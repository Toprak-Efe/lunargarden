# Introduction to OS Systems
## OS Market
> [!Information] Modern Computers ($1T Market)
> - Processors: **$130 Billion Market** (2024)
> 	- Intel (i7), AMD (Ryzen 7), Apple (M3)
> 	- ARM (Private-Consortium): Samsung (Exynos), Broadcomm (Snapdragon),
> 	- RISC-V (Open): TR (Çakıl),
> 	- NVIDIA, Google, Mediatek
> - CPU, GPU, APU (Hybrid), TPU, NPU, VPU, LPU, FPGA, ASIC: **$300B**
> - Main Memory: **$220B Market (2024)**
> 	- DDR: Double Data Rate / Low-Pwer LPDDR SDRAM
> - I/O Devices: **$800B**
> 	- Storage (SSD, NVMe, Disk): **$200B (2024)**
> 	- Network Int. Cards (NIC): Wired (Eth,. Fiber), Wireless (WiFi, Cellular) **$300B**
> 	- Keyboard, Mouse, Display, Printers (2D/3D) **$400B**

Some esimates:
- 1.2 Billion smart phones sold in 2024
- 8 Billion smart phones worldwide
- 18 Billion mobile devices of which 60% are laptop-desktops (10B)
How about the others?
- Servers - Cloud
- SBC (Single Board Computers) - Edge
- IOT (Internet of Things)
## Components of Modern Computer
### Processors
The "brain" of the computer is the CPU. It fetches instructions from memory and executes them. The basic cycle of every CPU is to fetch the first instruction from memory, decode it to determine its type and operands, execute it, and then fetch, decode, and execute subsequent instructions. The cycle is repeated until the program finishes. In this way, programs are carried out.

> [!IMPORTANT] Pipelining
> To improve performance, CPU designers have long abandoned the simple model of fetching, decoding, and executing one instruction at a time. Many modern CPUs have facilities for executing more than one instruction at the same time. For example, a CPU might have separate fetch, decode, and execute units, so that while it is executing instruction n, it could also be decoding instruction n + 1 and fetching instruction n + 2. Such an organization is called a **pipeline**.
> 
> Pipelines cause compiler writers and operating system writers great headaches because they expose the complexities of the underlying machine to them and they have to deal with them.

> [!IMPORTANT] Superscalar CPU
> Even more advanced than a pipeline design is a superscalar CPU. In this design, multiple execution units are present, for example, one for integer arithmetic, one for floating-point arithmetic, and one for Boolean operations. Two or more instructions are fetched at once, decoded, and dumped into a holding buffer until they can be executed.

> [!INFO] Multithreading
> - Multithreading allows the CPU to hold the state of two different threads and then switch back and forth on a nanosecond time scale.
> - For example, if one of the processes needs to read a word from memory (which takes many clock cycles), a multithreaded CPU can just switch to another thread.
> - Multithreading does not offer true parallelism. Only one process at a time is running, but thread-switching time is reduced to the order of a nanosecond.

> [!INFO] Multiprocessing
> - Many CPU chips now have four, eight, or more complete processors or cores on them. The multicore chips in Fig 2. effectively carry four minichips on them, each with its own independent CPU.
> - Some processors, like Intel Xeon Phi and the Tilera TilePro, already sport more than 60 cores on a single chip.
> - Making use of such a multicore chip will definitely require a multiprocessor operating system.

> [!IMPORTANT] Hyperthreading
> Officially known as Hyper-Threading Technology (HTT) by Intel, is a proprietary implementation of Simultaneous MUltithreading (SMT). It allows a single core to appear as two or more logical cores to the operating system. This architecture takes advantage of the **superscalar** architecture.

### Memory
The second major component in any computer is the memory. Ideally, a memory should be extremely fast (faster than executing an instruction so that the CPU is not held up by the memory), abundantly large, and dirt cheap. No current technology satisfies all of these goals, so a different approach is taken. The memory system is constructed as a hierarchy of layers as shown in Fig 3. The top layers have higher speed, smaller capacity, and greater cost per bit than the lower ones, often by factors of a billion or more.

> [!IMPORTANT] Registers
> The top layer consists of the registers internal to the CPU. They are made of the same material as the CPU and are thus just as fast as the CPU. Consequently, there is no delay in accessing them. The storage capacity available in them is typically 32 × 32 bits on a 32-bit CPU and 64 × 64 bits on a 64-bit CPU. Less than 1 KB in both cases. Programs must manage the registers (i.e., decide what to keep in them) themselves, in software.

> [!IMPORTANT] Cache Memory
> - The second layer is the **cache memory**, which is controlled by the hardware itself. The main memory is divided into **cache lines**, typically 64 bytes, with addresses starting from 0.
> - The most used cache lines are kept physically close to the CPU in order to make their usage almost instantenous.
> - When the program needs to read a memory word, the hardware checks if that word is cached; if it is, a **cache hit** occurs and the data in the cache is used.
> - Cache hits normally take about two clock cycles.
> - Cache memory is limited in size due to its high cost. Some machines have two or even three levels of cache, each one slower and bigger than the one before it.

> [!INFORMATION] Caching Problem
> 1. When to put a new item into the cache.
> 2. Which cache line to put the new item in.
> 3. Which item to remove from the cache when a slot is needed.
> 4. Where to put a newly evicted item in the larger memory.
### I/O Devices
The CPU and memory are not the only resources that the operating system must manage. I/O devices also interact heavily with the operating system.

I/O devices generally consist of two parts:
- The Controller:
	- The controller is a chip or a set of chips that physically controls the device. It accepts commands from the operating system, for example, to read data from the device, and carries them out.
- The Device
	- The I/O device itself, an electronic or an electromechanical apparatus that is useful in some way. For example, disks, serial communication peripherals, more complex hardware systems, etc.
### Buses

> [!IMPORTANT] Industry Standard Architecture Bus (ISA)
> **Industry Standard Architecture** (**ISA**) is the [16-bit](https://en.wikipedia.org/wiki/16-bit "16-bit") internal [bus](https://en.wikipedia.org/wiki/Bus_\(computing\) "Bus (computing)") of [IBM PC/AT](https://en.wikipedia.org/wiki/IBM_PC/AT "IBM PC/AT") and similar computers based on the [Intel 80286](https://en.wikipedia.org/wiki/Intel_80286 "Intel 80286") and its immediate successors during the 1980s.
> - It is considered archeic and exceptionally slow.

> [!IMPORTANT] Peripheral Component Interconnect Bus (PCI)
> PCI is a local computer bus for attaching hardware devices in a computer and is a part of the PCI Local Bus standard.
> - Master - Slave
> - Parallel bus, synchronous to a singular bus clock.
> - Attached devices can be integrated into the motherboard (planar devices), or be expansion cards that fit into a slot.

> [!IMPORTANT] Peripheral Component Interconnect Express Bus (PCIE)
> PCIe is a point-to-point connection between two PCIe compatible devices, typically a motherboard and an expansion card or storage device such as an SSD or hard drive. The connection uses differential signaling to transmit data over separate pairs of copper wires, allowing for speeds up to 16 GT/s.
> 
> To ensure optimal performance and compatibility across multiple devices, the PCIe standard uses different lane sizes which can link together two or more components at once depending on their speed requirements. For instance, larger lanes such as x16 are typically used for graphics cards that require lots of bandwidth for high resolution content; while smaller lanes like x1 are reserved for lower speed peripherals like USB ports or SATA ports.

> [!IMPORTANT] Direct Media Interface Bus (DMI)
> DMI is essentially [PCI Express](https://en.wikipedia.org/wiki/PCI_Express "PCI Express"), using multiple lanes and [differential signaling](https://en.wikipedia.org/wiki/Differential_signaling "Differential signaling") to form a point-to-point link. Most implementations use a ×8 or ×4 link, while some mobile systems (e.g. 915GMS, 945GMS/GSE/GU and the [Atom](https://en.wikipedia.org/wiki/Intel_Atom "Intel Atom") N450) use a ×2 link, halving the bandwidth. The original implementation provides 10 Gbit/s (1 GB/s) in each direction using a ×4 link. The DMI provides support for concurrent traffic and [isochronous data transfer](https://en.wikipedia.org/wiki/Isochronous_timing "Isochronous timing") capabilities.

To run in an environment with various peripheral I/O devices, the operating system has to know the devices that are connected to the computer and configure them appropriately. This requirement led Intel and Microsoft to design a PC system called **plug and play**.

Before plug and play, each I/O card has a fixed interrupt request level and fixed addresses for it's I/O registers. The keyboard was interrupt 1, and the floppy disk was 6; with respective addresses 0x60 to 0x64 and 0x3F0 to 0x3F7.

This system quickly lead to conflicts and clashes which made handling peripherals in a computer system a nightmare.

What plug and play does is have the system automatically collect information about the I/O devices, centrally assign interrupt levels and I/O addresses, and then tell each card what its numbers are. This work is closely related to booting the computer.
### Motherboard
A motherboard is the main printed circuit board (PCB) in a computer. The motherboard is a computer's central communications backbone connectivity point, through which all components and external computer hardware connect.
### Booting

> [!IMPORTANT] Booting The Computer
> Very briefly, the boot process is as follows. Every PC contains a motherboard. On the motherboard is a program called the system BIOS (Basic Input Output System). The BIOS contains low-level I/O software, including procedures to read the keyboard, write to the screen, and do disk I/O, among other things.
> - When the computer is booted, the BIOS is started.
> - The BIOS checks for available RAM, and connected input devices.
> - It scans PCIe and PCI buses to detect attached devices.
> - Newly detected devices are configured.
> - The BIOS determines the boot device by trying a list of devices stored in CMOS memory.
> - An attempt is made to boot from a CD-ROM/USB Drive.
> - Otherwise, the system boots from hard disk.
> - The first sector of the boot device is read into memory and executed.
> - This sector contains a program that normally examines the partition table at the end of the boot sector to determine active partitions.
> - A secondary bootl oader is read in from that partition.
> - The loader reads in the operating system from the active partition and starts it.
> - The operating system then queries the BIOS to get the configuration information. ,
> - For each device, it checks to see if it has the device driver. If not, it asks the user to insert a CD-ROM containing the driver (supplied by the device’s manufacturer) or to download it from the Internet.
> - Once it has all the device drivers, the operating system loads them into the kernel.
> - Then it initializes its tables, creates whatever background processes are needed, and starts up a login program or GUI.
## The Operating System Zoo
> [!IMPORTANT] Operating System Types
> - Mainframe Operating Systems
> - Server Operating Systems
> - Multiprocessor Operating Systems
> ---
> - PC Operating Systems
> - Mobile Operating Systems
> - Embedded Operating Systems
> ---
> - Sensor Node Operating Systems
> - Real-Time Operating Systems (RTOS)
> - Smart Card Operating Systems
## Operating System Concepts
### Processes
> [!DEFINITION] Process
> Processes are a key concept in all operating systems. They are defined as programs in execution.
> - A process is associated with an address space.
> - A process is associated also with a set of resources.
> - The process is like a container that holds all the information required to run a program.

> [!IMPORTANT] Forking
> Forking is a process in which a program duplicates itself (with the state, counters, registers, etc.) and runs concurrently with it's copy as a two separate programs.
> 
> In C, the function `fork()` is used in order to fork the program. The function returns 0 for the forked process, and returns the positive PID of the forked process for the main program.
> 
> The exact same software is executed in forks, except for the return value of the proposed `fork()` being zero.

Processes can create child processes that operate as separate but softly bound child programs.
### Files


### Architectures of Virtual Machines
#virtualmachines #architecture #computers #windows #linux 
Virtualization can take place in two forms:
- Runtimes (e.g. Java Runtime Env.) shielding OS
	-  Process VM: Virtualization for a single process.
- Virtual Machine Monitors (VMM) shielding HW
	- VMM Interface offered to different programs (therefore it is possible to run multiple & different OS), e.g. Xen and VmWare
### Hypervisors
Hypervisors are Virtual Machine Monitors, they are virtualization software that come in two types.

> [!Defintion] Type 1
> The hardware directly runs the embedded hypervisor firmware. The operating systems are loaded and run consequently as individual processes after the bootloader enters into the hypervisor.

> [!DEFINITION] Type 2
> A host OS runs the Hypervisor in the application space, which creates a virtual environment to run the guest OS's in.
# Processes

## Process Management
## Threads
## Scheduling
## Virtualization
## Files
## System Calls
## Interrupts
## Process Synchronization
## MUTEX
## Locks
## Dreadlock
## Dining Philosophers Problem
## Memory Management
## Reliability
The reliability of a system has different metrics to measure with, and in these basic terms the system can either be **up** or **down**.

> [!DEFINITION] Availability
> The availability of a system is defined as the ratio between the **uptime** and the total operational lifespan.
> $$
> \text{Availability} = \frac{\text{Uptime}}{\text{Total Time}}
> $$

Reliability on the other hand is expressed by several terms such as  Mean Time to Failure (**MTTF**), Mean Time to Recover MTTR, Mean Time to Data Loss (**MTTDL**). The calculation of these terms are done for the graph below.
Where the first period of failure and succession is $x_1, y_1$ respectively, and the following terms being $x_2, y_2$: 
> [!DEFINITION] Mean Time to Failure
> $$
> \text{MTTF}: \frac{y_1 + y_2}{2}
> $$

> [!DEFINITION] Mean Time to Recover
> $$
> \text{MTTR} = \frac{x_1 + x_2}{2}
> $$


> [!DEFINITION] Mean Time to Data Loss
> 


## RAID Levels

# Virtual Memory
# OS Memory Management
# Caching
# Linux Memory Management
# File and Storage Systems
# Other I/O Systems
# OS Security
