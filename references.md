*Format: category - year - title - (abstract or review)*



# Virtualization



## Fundamentals
Paper - 1974 - **[Formal requirements for virtualizable third generation architectures](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.141.4815&rep=rep1&type=pdf)** - Define a set of conditions sufficient for a computer architecture to support system virtualization efficiently, the short version can be viewed on [wikipedia](https://en.wikipedia.org/wiki/Popek_and_Goldberg_virtualization_requirements).



## Architecture Related

Doc - Updating - **[Armv8-A Virtualization](https://developer.arm.com/architectures/learn-the-architecture/armv8-a-virtualization/single-page)** - describes the virtualization support in Armv8-A AArch64. Topics covered include stage 2 translation, virtual exceptions, and trapping. 



Article - 2015 - **[An in-depth look into the ARM virtualization extensions](https://genode.org/documentation/articles/arm_virtualization)** - From a practical way to inspect the extended ARM v7 architecture which supports virtualization, like how can we integrate virtualization into OS without increasing the trusted computing base (TCB) of applications that run beside virtual machines? Moreover, how can we make the virtual machine monitor (VMM) of one virtual machine (VM) independent of others.



Series - 2008 - **[Hardware Virtualization: the Nuts and Bolts](https://www.anandtech.com/show/2480/10)** - Explains the impact of x86 hardware virtualization performance. Topics include:
> A Matter of Privileges, Virtualization Challenges, Binary Translation, System Calls, I/O Virtualization, Memory ManagementParavirtualization, Intel VT-x and AMD SVM, Intel's EPT and AMD's NPT, Standardization Please!, The Benchmarks, Conclusion and Bibliography, 



Series/Code - Updating - **[Hypervisor-From-Scratch](https://github.com/SinaKarvandi/Hypervisor-From-Scratch)** - Course contains technical details to create a basic Virtual Machine based on x86 hardware virtualization.. Topics include:
> Basic Concepts & Configure Testing Environment, Entering VMX Operation, Setting up Our First Virtual Machine, Address Translation Using Extended Page Table (EPT), Setting up VMCS & Running Guest Code, Virtualizing An Already Running System, Using EPT & Page-Level Monitoring Features, How To Do Magic With Hypervisor!



Doc - 2009 - **[Performance Evaluation of Intel EPT Hardware Assist](https://www.vmware.com/pdf/Perf_ESX_Intel-EPT-eval.pdf)** - Vmware's introduction about Extended Page Tables (EPT, Intel's implementation of [Second Level Address Translation (SLAT), also known as nested paging](http://en.wikipedia.org/wiki/Second_Level_Address_Translation), which is used to more efficiently virtualize the memory of guest VMs) and shadow page table technique, and they designed a experience to evaluated their performance.



# Vulnerability Discovery



## Fuzzing

Article - 2020 - **[Fuzzing战争：从刀剑弓斧到星球大战](https://www.secrss.com/articles/19781)** - 该文从历史演变的角度，阐述了 Fuzzing 进步和演变的过程，并特别对 Coverage-based greybox fuzzing(CGF) 和对应的改进进行了简单说明，最后展望了Fuzzing的发展方向：覆盖全类软件、CGF 依然主流、结合虚拟化机制的黑盒 Fuzzing 。（作者是前 Pwn2Own 冠军 Flanker Edward）



Paper - 2017 - **[Coverage-based Greybox Fuzzing as Markov Chain](https://mboehme.github.io/paper/TSE18.pdf)** - 



Paper - 2017 - **[Designing New Operating Primitives to Improve Fuzzing Performance](https://iisp.gatech.edu/sites/default/files/images/designing_new_operating_primitives_to_improve_fuzzing_performance_vt.pdf)** - 



# VirtVul

Paper - 2020 - **[Agamotto: Accelerating Kernel Driver Fuzzing with Lightweight Virtual Machine Checkpoints](https://www.usenix.org/system/files/sec20-song.pdf)** - 



Paper - 2020 - **[USBFuzz: A Framework for Fuzzing USB Drivers by Device Emulation](https://www.usenix.org/system/files/sec20-peng_0.pdf)** - 



Paper - 2017 - **[Digtool: A Virtualization-Based Framework for Detecting Kernel Vulnerabilities](https://www.usenix.org/system/files/conference/usenixsecurity17/sec17-pan.pdf)** - 



# Miscellaneous

Blog - 2017 - **[SecDr](http://secdr.github.io/)** - 

