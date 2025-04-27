---
sidebar_position: 33
---

# Glossary

**ABI** Application binary interface.

**ACK** TCP acknowledgment.

**adaptive** mutex A mutex (mutual exclusion) synchronization lock type. See [Chapter 5](ch05.md), [Applications](ch05.md), [Section 5.2.5](ch05.md), [Concurrency and Parallelism](ch05.md).

**address** A memory location.

**address space** A virtual memory context. See [Chapter 7](ch07.md), [Memory](ch07.md).

**AMD** A processor vendor.

**API** Application programming interface.

**application** A program, typically user-level.

**ARM** A processor vendor.

**ARP** Address resolution protocol.

**array** A set of values. This is a data type for programming languages. Low-level languages typically store arrays in a contiguous range of memory, and value index refers to their offset.

**ASIC** Application-specific integrated circuit.

**associative array** A data type for programming languages where values are referenced by an arbitrary key or multiple keys.

**AT&amp;T** The American Telephone and Telegraph Company, which included Bell Laboratories, where Unix was developed.

**back end** Refers to data storage and infrastructure components. A web server is back-end software. See [front end](gloss.md).

**balanced system** A system without a bottleneck.

**bandwidth** The frequency range for a communication channel, measured in Hertz. In computing, bandwidth is used to describe the maximum transfer rate for a communication channel. It is also frequently *misused* to describe the current throughput (which is wrong).

**BCC** BPF compiler collection. BCC is a project that includes a BPF compiler framework, as well as many BPF performance tools. See [Chapter 15](ch15.md).

**benchmark** In computing, a benchmark is a tool that performs a workload experiment and measures its performance: the benchmark result. These are commonly used for evaluating the performance of different options.

**BIOS** Basic Input/Output System: firmware used to initialize computer hardware and manage the booting process.

**bottleneck** Something that limits performance.

**BPF** Berkeley Packet Filter: a lightweight in-kernel technology from 1992 created to improve the performance of packet filtering. Since 2014 it has been extended to become a general-purpose execution environment (see [eBPF](gloss.md)).

**BSD** Berkeley Software Distribution, a derivative of Unix.

**buffer** A region of memory used for temporary data.

**byte** A unit of digital data. This book follows the industry standard where one byte equals eight bits, where a bit is a zero or a one.

**C** The C programming language.

**cache hit** A request for data that can be returned from the contents of the cache.

**cache miss** A request for data that was not found in the cache.

**cache warmth** See Hot, Cold, and Warm Caches in [Section 2.3.14](ch02.md), [Caching](ch02.md), in [Chapter 2](ch02.md), [Methodologies](ch02.md).

**CDN** Content delivery network.

**client** A consumer of a network service, referring to either the client host or the client application.

**command** A program executed at the shell.

**concurrency** See [Section 5.2.5](ch05.md), [Concurrency and Parallelism](ch05.md), in [Chapter 5](ch05.md), [Applications](ch05.md).

**contention** Competition for a resource.

**core** An execution pipeline on a processor. These may be exposed on an OS as single CPUs, or via hyperthreads as multiple CPUs.

**CPI** Cycles per instruction. See [Chapter 6](ch06.md), [CPUs](ch06.md).

**CPU** Central processing unit. This term refers to the set of functional units that execute instructions, including the registers and arithmetic logic unit (ALU). It is now often used to refer to either the processor or a virtual CPU.

**CPU cross call** A call by a CPU to request work from others on a multi-CPU system. Cross calls may be made for system-wide events such as CPU cache coherency calls. See [Chapter 6](ch06.md), [CPUs](ch06.md). Linux terms these “SMP calls.”

**CPU cycle** A unit of time based on the clock rate of the processor: for 2 GHz, each cycle is 0.5 ns. A cycle itself is an electrical signal, the rising or falling of voltage, used to trigger digital logic.

**cross call** See [CPU](gloss.md) cross call.

**CSV** The Comma Separated Values file type.

**CTSS** Compatible Time-Sharing System, one of the first time-sharing systems.

**daemon** A system program that continually runs to provide a service.

**datagram** See [segment](gloss.md).

**debuginfo file** A symbol and debug information file, used by debuggers and profilers.

**DEC** Digital Equipment Corporation.

**disk** A physical storage device. Also see [HDD](gloss.md) and [SSD](gloss.md).

**disk controller** A component that manages directly attached disks, making them accessible to the system, either directly or mapped as virtual disks. Disk controllers may be built into the system main board, included as expansion cards, or built into storage arrays. They support one or more storage interface types (e.g., SCSI, SATA, SAS) and are also commonly called *host bus adaptors* (HBAs), along with the interface type, for example, *SAS HBA*.

**DNS** Domain Name Service.

**DRAM** Dynamic random-access memory, a type of volatile memory in common use as main memory.

**duplex** Simultaneous bi-directional communication.

**dynamic instrumentation** Dynamic instrumentation or dynamic tracing is a technology that can instrument any software event, including function calls and returns, by live modification of instruction text and the insertion of temporary tracing instructions.

**dynamic tracing** This can refer to the software that implements dynamic instrumentation.

**eBPF** Extended BPF (see [BPF](gloss.md)). The eBPF abbreviation originally described the extended BPF from 2014, which updated the register size, instruction set, added map storage, and limited kernel calls. By 2015, it was decided to call eBPF just BPF.

**ECC** Error-correcting code. An algorithm for detecting errors and fixing some types of errors (usually single-bit errors).

**ELF** Executable and Linkable Format: a common file format for executable programs.

**errno** A variable containing the last error as a number following a standard (POSIX.1-2001).

**Ethernet** A set of standards for networking at the physical and data link layers.

**expander card** A physical device (card) connected to the system, usually to provide an additional I/O controller.

**file descriptor** An identifier for a program to use in referencing an open file.

**firmware** Embedded device software.

**flame graph** A visualization for a set of stack traces. See [Chapter 2](ch02.md), [Methodologies](ch02.md).

**FPGA** Field-programmable gate array. A reprogrammable integrated circuit used in computing to typically accelerate a specific operation.

**frame** A message at the data link layer of the OSI networking model (see [Section 10.2.3](ch10.md), [Protocol Stack](ch10.md)).

**FreeBSD** An open source, Unix-like, operating system.

**front end** Refers to end-user interface and presentation software. A web application is front-end software. See [back end](gloss.md).

**fsck** The file system check command is used to repair file systems after system failure, such as due to a power outage or kernel panic. This process can take hours.

**Gbps** Gigabits per second.

**GPU** Graphics processing unit. These can be used for other workloads as well, such as machine learning.

**GUI** Graphical user interface.

**HDD** Hard disk drive, a rotational magnetic storage device. See [Chapter 9](ch09.md), [Disks](ch09.md).

**Hertz (Hz)** Cycles per second.

**hit ratio** Often used to describe cache performance: the ratio of cache hits versus hits plus misses, usually expressed as a percentage. Higher is better.

**host** A system connected to the network. Also called a network *node*.

**HTTP** Hyper Text Transfer Protocol.

**hyperthread** Intel’s implementation of SMT. This is a technology for scaling CPUs, allowing the OS to create multiple virtual CPUs for one core and schedule work on them, which the processor attempts to process in parallel.

**ICMP** Internet Control Message Protocol. Used by ping(1) (ICMP echo request/reply).

**I/O** Input/output.

**IO Visor** The Linux Foundation project that hosts the bcc and bpftrace repositories on GitHub, and facilitates collaboration among BPF developers at different companies.

**IOPS** I/O operations per second, a measure of the rate of I/O.

**Intel** A processor vendor.

**instance** A virtual server. Cloud computing provides server instances.

**IP** Internet Protocol. Main versions are IPv4 and IPv6. See [Chapter 10](ch10.md), [Network](ch10.md).

**IPC** Either means: instructions per cycle, a low-level CPU performance metric, or inter-process communication, a means for processes to exchange data. Sockets are an inter-process communication mechanism.

**IRIX** A Unix-derived operating system by Silicon Graphics, Inc. (SGI).

**IRQ** Interrupt request, a hardware signal to the processor to request work. See [Chapter 3](ch03.md), [Operating Systems](ch03.md).

**Kbytes** Kilobytes. The International System of Units (SI) defines a kilobyte as 1000 bytes, but in computing a kilobyte is typically 1024 bytes (which SI terms a kibibyte). Throughout this book, tools that report Kbytes are usually using the definition of 1024 (210) bytes.

**kernel** The core program on a system that runs in privileged mode to manage resources and user-level processes.

**kernel-land** Kernel software.

**kernel-level** The processor privilege mode that kernel execution uses.

**kernel-space** The address space of the kernel.

**kprobes** A Linux kernel technology for kernel-level dynamic instrumentation.

**latency** Time spent waiting. In computing performance it is often used to describe resource I/O time. Latency is important for performance analysis, because it is often the most effective measure of a performance issue. Where exactly it is measured can be ambiguous without further qualifiers. For example, “disk latency” could mean time spent waiting on a disk driver queue only or, from an application, it could mean the entire time waiting for disk I/O to complete, both queued and service time. Latency is limited by a lower bound, bandwidth by an upper bound.

**local disks** Disks that are connected directly to the server and are managed by the server. These include disks inside the server case and those attached directly via a storage transport.

**logical processor** Another name for a *virtual CPU*. See [Chapter 6](ch06.md), [CPUs](ch06.md).

**LRU** Least recently used. See [Section 2.3.14](ch02.md), [Caching](ch02.md), in [Chapter 2](ch02.md), [Methodologies](ch02.md).

**main board** The circuit board that houses the processors and system interconnect; also called the *system board*.

**main memory** The primary memory storage of a system, usually implemented as DRAM.

**major fault** A memory access fault that was serviced from storage devices (disks). See [Chapter 3](ch03.md), [Operating Systems](ch03.md).

**malloc** Memory allocate. This usually refers to the function performing allocation.

**Mbps** Megabits per second.

**Mbytes** Megabytes. The International System of Units (SI) defines a megabyte as 1000000 bytes, but in computing a megabyte is typically 1048576 bytes (which SI terms a mebibyte). Throughout this book, tools that report Mbytes are usually using the definition of 1048576 (220) bytes.

**memory** See [main memory](gloss.md).

**micro-benchmark** A benchmark for measuring single or simple operations.

**minor fault** A memory access fault that was serviced from main memory. See [Chapter 3](ch03.md), [Operating Systems](ch03.md).

**MMU** Memory management unit. This is responsible for presenting memory to a CPU and for performing virtual-to-physical address translation.

**mutex** A mutual exclusion lock. They can become a source of performance bottlenecks, and are often investigated for performance problems. See [Chapter 5](ch05.md), [Applications](ch05.md).

**mysqld** The daemon for the MySQL database.

**NVMe** Non-Volatile Memory express: a PCIe bus specification for storage devices.

**observability** The ability for a computing system to be observed. This includes the practice and tools used to analyze the state of computing systems.

**off-CPU** This term refers to a thread that is not currently running on a CPU, and so is “off-CPU,” due to either having blocked on I/O, a lock, a voluntary sleep, or other event.

**on-CPU** This term refers to a thread that is currently running on a CPU.

**operation rate** Operations per interval (e.g., operations per second), which may include non-I/O operations.

**OS** Operating System. The collection of software including the kernel for managing resources and user-level processes.

**packet** A network message at the network layer of the OSI networking model (see [Section 10.2.3](ch10.md)).

**page** A chunk of memory managed by the kernel and processor. All memory used by the system is broken up into pages for reference and management. Typical page sizes include 4 Kbytes and 2 Mbytes (depending on the processor).

**pagefault** A system trap that occurs when a program references a memory location where the virtual memory is not currently mapped to a physical backing page. This is a normal consequence of an on-demand allocation memory model.

**pagein/pageout** Functions performed by an operating system (kernel) to move chunks of memory (pages) to and from external storage devices.

**parallel** See [Section 5.2.5](ch05.md), [Concurrency and Parallelism](ch05.md), in [Chapter 5](ch05.md), [Applications](ch05.md).

**PC** Program counter, a CPU register that points to the currently executing instruction.

**PCID** Process-context ID, a processor/MMU feature to tag virtual address entries with the process ID to avoid flushing on context switches.

**PCIe** Peripheral Component Interconnect Express: a bus standard commonly used for storage and network controllers.

**PDP** Programmed Data Processor, a minicomputer series made by Digital Equipment Corporation (DEC).

**PEBS** Precise event-based sampling (aka *processor* event-based sampling), an Intel processor technology for use with PMCs to provide more precise recording of CPU state during events.

**Performance engineer** A technical staff member who works primarily on computer performance: planning, evaluations, analysis, and improvements. See [Chapter 1](ch01.md), [Introduction](ch01.md), [Section 1.3](ch01.md), [Activities](ch01.md).

**PID** Process identifier. The operating system unique numeric identifier for a process.

**PMCs** Performance Monitoring Counters: special hardware registers on the processor that can be programmed to instrument low-level CPU events: cycles, stall cycles, instructions, memory loads/stores, etc.

**POSIX** Portable Operating System Interface, a family of related standards managed by the IEEE to define a Unix API. This includes a file system interface as used by applications, provided via system calls or system libraries built upon system calls.

**process** A running instance of a program. Multi-tasked operating systems can execute multiple processes concurrently, and can run multiple instances of the same program as different processes. A process contains one or more threads for execution on CPUs.

**processor ring** A protection mode for the CPU.

**production** A term used in technology to describe the workload of real customer requests, and the environment that processes it. Many companies also have a “test” environment with synthetic workloads for testing things before production deployment.

**profiling** A technique to collect data that characterizes the performance of a target. A common profiling technique is timed sampling (see [sampling](gloss.md)).

**PSI** Linux pressure stall information, used for identifying performance issues caused by resources.

**RCU** Read-copy-update: a Linux synchronization mechanism.

**real-time workload** One that has fixed latency requirements, usually low latency.

**registers** Small storage locations on a CPU, used directly from CPU instructions for data processing.

**remote disks** Disks (including virtual disks) that are used by a server but are connected to a remote system.

**RFC** Request For Comments: a public document by the Internet Engineering Task Force (IETF) to share networking standards and best practices. RFCs are used to define networking protocols: RFC 793 defines the TCP protocol.

**RSS** Resident set size: a measure of main memory.

**ROI** Return on investment, a business metric.

**run queue** A CPU scheduler queue of tasks waiting their turn to run on a CPU. In reality the queue may be implemented as a tree structure, but the term run queue is still used.

**RX** Receive (used in networking).

**sampling** An observability method for understanding a target by taking a subset of measurements: a sample.

**script** In computing, an executable program, usually short and in a high-level language.

**SCSI** Small Computer System Interface. An interface standard for storage devices.

**sector** A data unit size for storage devices, commonly 512 bytes or 4 Kbytes. See [Chapter 9](ch09.md), [Disks](ch09.md).

**segment** A message at the transport layer of the OSI networking model (see [Section 10.2.3](ch10.md), [Protocol Stack](ch10.md)).

**server** In networking, a network host that provides a service for network clients, such as an HTTP or database server. The term *server* can also refer to a physical system.

**shell** A command-line interpreter and scripting language.

**SLA** Service level agreement.

**SMP** Symmetric multiprocessing, a multiprocessor architecture where multiple similar CPUs share the same main memory.

**SMT** Simultaneous multithreading, a processor feature to run multiple threads on cores. See [hyperthread](gloss.md).

**SNMP** Simple Network Management Protocol.

**socket** A software abstraction representing a network endpoint for communication.

**Solaris** A Unix-derived operating system originally developed by Sun Microsystems, it was known for scalability and reliability, and was popular in enterprise environments. Since the acquisition of Sun by Oracle Corporation, it has been renamed Oracle Solaris.

**SONET** Synchronous optical networking, a physical layer protocol for optical fibers.

**SPARC** A processor architecture (from *s*calable *p*rocessor *arc*hitecture).

**SRE** Site reliability engineer: a technical staff member focused on infrastructure and reliability. SREs work on performance as part of incident response, under short time constraints.

**SSD** Solid-state drive, a storage device typically based on flash memory. See [Chapter 9](ch09.md), [Disks](ch09.md).

**SSH** Secure Shell. An encrypted remote shell protocol.

**stack** In the context of observability tools, stack is usually short for “stack trace.”

**stack frame** A data structure containing function state information, including the return address and function arguments.

**stack trace** A call stack composed of multiple stack frames spanning the code path ancestry. These are often inspected as part of performance analysis, particularly CPU profiling.

**static instrumentation/tracing** Instrumentation of software with precompiled probe points. See [Chapter 4](ch04.md), [Observability Tools](ch04.md).

**storage array** A collection of disks housed in an enclosure, which can then be attached to a system. Storage arrays typically provide various features to improve disk reliability and performance.

**struct** A structured object, usually from the C programming language.

**SunOS** Sun Microsystems Operating System. This was later rebranded as Solaris.

**SUT** System under test.

**SVG** The Scalable Vector Graphs file format.

**SYN** TCP synchronize.

**syscall** See [system call](gloss.md).

**system call** The interface for processes to request privileged actions from the kernel. See [Chapter 3](ch03.md), [Operating Systems](ch03.md).

**task** A Linux runnable entity, which may be a process, a thread from a multithreaded process, or a kernel thread. See [Chapter 3](ch03.md), [Operating Systems](ch03.md).

**TCP** Transmission Control Protocol. Originally defined in RFC 793. See [Chapter 10](ch10.md), [Network](ch10.md).

**TENEX** TEN-EXtended operating system, based on TOPS-10 for the PDP-10.

**thread** A software abstraction for an instance of program execution, which can be scheduled to run on a CPU. The kernel has multiple threads, and a process contains one or more. See [Chapter 3](ch03.md), [Operating Systems](ch03.md).

**throughput** For network communication devices, throughput commonly refers to the data transfer rate in either bits per second or bytes per second. Throughput may also refer to I/O completions per second (IOPS) when used with statistical analysis, especially for targets of study.

**TLB** Translation Lookaside Buffer. A cache for memory translation on virtual memory systems, used by the MMU (see [MMU](gloss.md)).

**TLS** Transport Layer Security: used to encrypt network requests.

**TPU** Tensor processing unit. An AI accelerator ASIC for machine learning developed by Google, and named after TensorFlow (a software platform for machine learning).

**tracepoints** A Linux kernel technology for providing static instrumentation.

**tracer** A tracing tool. See [tracing](gloss.md).

**tracing** Event-based observability.

**tunable** Short for tunable parameter.

**TX** Transmit (used in networking).

**UDP** User Datagram Protocol. Originally defined in RFC 768. See [Chapter 10](ch10.md), [Network](ch10.md).

**uprobes** A Linux kernel technology for user-level dynamic instrumentation.

**us** Microseconds. This should be abbreviated as μs; however, you will often see it as “us,” especially in the output of ASCII-based performance tools. (Note that vmstat(8)’s output, included many times in this book, includes a `us` column, short for user time.)

**μs** Microseconds. See [“us.”](gloss.md)

**USDT** User-land Statically Defined Tracing. This involves the placement of static instrumentation in application code by the programmer, at locations to provide useful probes.

**user-land** This refers to user-level software and files, including executable programs in /usr/bin, /lib, etc.

**user-level** The processor privilege mode that user-land execution uses. This is a lower privilege level than the kernel, and one that denies direct access to resources, forcing user-level software to request access to them via the kernel.

**user-space** The address space of the user-level processes.

**variable** A named storage object used by programming languages.

**vCPU** A virtual CPU. Modern processors can expose multiple virtual CPUs per core (e.g., Intel Hyper-Threading).

**VFS** Virtual file system. An abstraction used by the kernel to support different file system types.

**virtual memory** An abstraction of main memory that supports multitasking and over-subscription.

**VMS** Virtual Memory System, an operating system by DEC.

**workload** This describes the requests for a system or resource.

**x86** A processor architecture based on the Intel 8086.

**ZFS** A combined file system and volume manager created by Sun Microsystems.
