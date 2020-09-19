# Virtualization



## Fundamentals
Paper - 1974 - **[Formal requirements for virtualizable third generation architectures](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.141.4815&rep=rep1&type=pdf)** - Define a set of conditions sufficient for a computer architecture to support system virtualization efficiently, the short version can be viewed on [wikipedia](https://en.wikipedia.org/wiki/Popek_and_Goldberg_virtualization_requirements).



## Architecture Related

Official Doc - **[Armv8-A Virtualization](https://developer.arm.com/architectures/learn-the-architecture/armv8-a-virtualization/single-page)** - describes the virtualization support in Armv8-A AArch64. Topics covered include stage 2 translation, virtual exceptions, and trapping.

Web Article - **[An in-depth look into the ARM virtualization extensions](https://genode.org/documentation/articles/arm_virtualization)** - From a practical way to inspect the extended ARM v7 architecture which supports virtualization, like how can we integrate virtualization into OS without increasing the trusted computing base (TCB) of applications that run beside virtual machines? Moreover, how can we make the virtual machine monitor (VMM) of one virtual machine (VM) independent of others.



# Vulnerability Discovery



## Fuzzing

Web Article - **[Fuzzing战争：从刀剑弓斧到星球大战](https://www.secrss.com/articles/19781)** - 该文从历史演变的角度，阐述了 Fuzzing 进步和演变的过程，并特别对 Coverage-based greybox fuzzing(CGF) 和对应的改进进行了简单说明，最后展望了Fuzzing的发展方向：覆盖全类软件、CGF 依然主流、结合虚拟化机制的黑盒 Fuzzing 。（作者是前 Pwn2Own 冠军 Flanker Edward）

Paper - 2017 - **[Coverage-based Greybox Fuzzing as Markov Chain](https://mboehme.github.io/paper/TSE18.pdf)** - 

# VirtVul

Paper - 2017 - **[Digtool: A Virtualization-Based Framework for Detecting Kernel Vulnerabilities](https://www.usenix.org/system/files/conference/usenixsecurity17/sec17-pan.pdf)** - 

Paper - 2020 - **[Agamotto: Accelerating Kernel Driver Fuzzing with Lightweight Virtual Machine Checkpoints](https://www.usenix.org/system/files/sec20-song.pdf)** - 

Paper - 2020 - **[USBFuzz: A Framework for Fuzzing USB Drivers by Device Emulation](https://www.usenix.org/system/files/sec20-peng_0.pdf)** - 

