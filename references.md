*Format: category - year - title - (abstract or review)*

<br>

# Virtualization

<br>

## Fundamentals
Paper - 1974 - **[Formal requirements for virtualizable third generation architectures](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.141.4815&rep=rep1&type=pdf)** - Define a set of conditions sufficient for a computer architecture to support system virtualization efficiently, the short version can be viewed on [wikipedia](https://en.wikipedia.org/wiki/Popek_and_Goldberg_virtualization_requirements).

<br>

## Architecture Related

Doc - Updating - **[Armv8-A Virtualization](https://developer.arm.com/architectures/learn-the-architecture/armv8-a-virtualization/single-page)** - describes the virtualization support in Armv8-A AArch64. Topics covered include stage 2 translation, virtual exceptions, and trapping. 

<br>

Article - 2015 - **[An in-depth look into the ARM virtualization extensions](https://genode.org/documentation/articles/arm_virtualization)** - From a practical way to inspect the extended ARM v7 architecture which supports virtualization, like how can we integrate virtualization into OS without increasing the trusted computing base (TCB) of applications that run beside virtual machines? Moreover, how can we make the virtual machine monitor (VMM) of one virtual machine (VM) independent of others.

<br>

Doc - Updating - **[Intel® 64 and IA-32 Architectures Software Developer's Manual Volume 3C: System Programming Guide, Part 3](https://software.intel.com/content/www/us/en/develop/download/intel-64-and-ia-32-architectures-sdm-volume-3c-system-programming-guide-part-3.html)** - Volume 3C covers system management mode, virtual machine extensions (VMX) instructions, and Intel® Virtualization Technology (Intel® VT).

Doc - Updating - **[Intel® Virtualization Technology FlexMigration (Intel® VT FlexMigration) Application Note](https://software.intel.com/content/www/us/en/develop/download/intel-virtualization-technology-flexmigration-intel-vt-flexmigration-application-note.html)** - This application note discusses virtualization capabilities in Intel® processors that support Intel® VT FlexMigration which is a part of Intel VT that allows a virtual-machine monitor (VMM) to report a consistent set of available processor features to guest software running in a virtual machine (VM), thereby broadening the live-migration compatibility pool across generations of Intel® processors.

Doc - Updating - **[Intel® Virtualization Technology for Directed I/O Architecture Specification](https://software.intel.com/content/www/us/en/develop/download/intel-virtualization-technology-for-directed-io-architecture-specification.html)** - This document describes the Intel® Virtualization Technology for Directed I/O.

<br>

Paper - 2010 - **[The evolution of an x86 virtual machine monitor](http://course.ece.cmu.edu/~ece845/docs/vmware-evolution.pdf)** - 

<br>

Article - 2012 - **[Bringing Virtualization to the x86 Architecture with the Original VMware Workstation](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.423.4009&rep=rep1&type=pdf)** - 

<br>

Paper - 2006 - **[A Comparison of Software and Hardware Techniques for x86 Virtualization](https://www.vmware.com/pdf/asplos235_adams.pdf)** - 

<br>

Series - 2008 - **[Hardware Virtualization: the Nuts and Bolts](https://www.anandtech.com/show/2480/10)** - Explains the impact of **x86** hardware virtualization performance. Topics include: A Matter of Privileges, Virtualization Challenges, Binary Translation, System Calls, I/O Virtualization, Memory ManagementParavirtualization, Intel VT-x and AMD SVM, Intel's EPT and AMD's NPT, Standardization Please!, The Benchmarks, Conclusion and Bibliography.

<br>

Series/Code - Updating - **[Hypervisor-From-Scratch](https://github.com/SinaKarvandi/Hypervisor-From-Scratch)** - Course contains technical details to create a basic Virtual Machine based on **x86** hardware virtualization.. Topics include: Basic Concepts & Configure Testing Environment, Entering VMX Operation, Setting up Our First Virtual Machine, Address Translation Using Extended Page Table (EPT), Setting up VMCS & Running Guest Code, Virtualizing An Already Running System, Using EPT & Page-Level Monitoring Features, How To Do Magic With Hypervisor.

<br>

Doc - 2009 - **[Performance Evaluation of Intel EPT Hardware Assist](https://www.vmware.com/pdf/Perf_ESX_Intel-EPT-eval.pdf)** - Vmware's introduction about **x86** Extended Page Tables (EPT, Intel's implementation of [Second Level Address Translation (SLAT), also known as nested paging](http://en.wikipedia.org/wiki/Second_Level_Address_Translation), which is used to more efficiently virtualize the memory of guest VMs) and shadow page table technique, and they designed a experience to evaluated their performance.

<br>

# Vulnerability Discovery

<br>

## Fuzzing

Article - 2020 - **[Fuzzing战争：从刀剑弓斧到星球大战](https://www.secrss.com/articles/19781)** - 该文从历史演变的角度，阐述了 Fuzzing 进步和演变的过程，并特别对 Coverage-based greybox fuzzing(CGF) 和对应的改进进行了简单说明，最后展望了Fuzzing的发展方向：覆盖全类软件、CGF 依然主流、结合虚拟化机制的黑盒 Fuzzing 。（作者是前 Pwn2Own 冠军 Flanker Edward）

<br>

Paper - 2017 - **[Coverage-based Greybox Fuzzing as Markov Chain](https://mboehme.github.io/paper/TSE18.pdf)** - 

<br>

Paper - 2017 - **[Designing New Operating Primitives to Improve Fuzzing Performance](https://iisp.gatech.edu/sites/default/files/images/designing_new_operating_primitives_to_improve_fuzzing_performance_vt.pdf)** - 

<br>

# VirtVul

Paper - 2020 - **[Agamotto: Accelerating Kernel Driver Fuzzing with Lightweight Virtual Machine Checkpoints](https://www.usenix.org/system/files/sec20-song.pdf)** - 

<br>

Paper - 2020 - **[USBFuzz: A Framework for Fuzzing USB Drivers by Device Emulation](https://www.usenix.org/system/files/sec20-peng_0.pdf)** - 

<br>

Paper - 2017 - **[Digtool: A Virtualization-Based Framework for Detecting Kernel Vulnerabilities](https://www.usenix.org/system/files/conference/usenixsecurity17/sec17-pan.pdf)** - 

<br>

# Miscellaneous

Blog - 2017 - **[SecDr](http://secdr.github.io/)** - 


