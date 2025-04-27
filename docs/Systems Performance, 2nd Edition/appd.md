---
sidebar_position: 31
---

# Appendix D

Solutions to Selected Exercises

The following are suggested solutions to selected exercises.[1](appd.md)

[1](appd.md)If you manage a training course where students receive a copy of this text, contact either the publisher or myself for a full list of exercise solutions.

### Chapter 2—Methodology

Q. What is latency?

A. A measure of time, usually time waiting for something to be done. In the IT industry, the term may be used differently depending on context.

### Chapter 3—Operating Systems

Q. List the reasons why a thread would leave the CPU.

A. Blocked on I/O, blocked on a lock, call to yield, expired time slice, preempted by another thread, device interrupt, exiting.

### Chapter 6—CPUs

Q. Calculate the load average . . .

A. 34

### Chapter 7—Memory

Q. Using Linux terminology, what is the difference between paging and swapping?

A. Paging is the movement of memory pages; swapping is the movement of pages to and from swap devices/files.

Q. Describe memory utilization and saturation.

A. For memory capacity, utilization is the amount that is in use and not available, measured against the total usable memory. This can be presented as a percentage, similar to file system capacity. Saturation is a measure of the demand for available memory beyond the size of memory, which usually invokes a kernel routine to free memory to satisfy this demand.

### Chapter 8—File Systems

Q. What is the difference between logical I/O and physical I/O?

A. Logical I/O is to the file system interface; physical I/O is to the storage devices (disks).

Q. Explain how file system copy-on-write can improve performance.

A. Since random writes can be written to a new location, they can be grouped (by increasing I/O size) and written out sequentially. Both of these factors usually improve performance, depending on the storage device type.

### Chapter 9—Disks

Q. Describe what happens when disks are overloaded with work, including the effect on application performance.

A. The disks run at a continual high utilization rate (up to 100%) with a high degree of saturation (queueing). Their I/O latency is increased due to the likelihood of queueing (which can be modeled). If the application is performing file system or disk I/O, the increased latency *may* hurt application performance, provided it is a synchronous I/O type: reads, or synchronous writes. It must also occur during a critical application code path, such as while a request is serviced, and not an asynchronous background task (which may only *indirectly* cause poor application performance). Usually back pressure from the increased I/O latency will keep the rate of I/O requests in check and not cause an unbounded increase in latency.

### Chapter 11—Cloud Computing

Q. Describe physical system observability from an OS-virtualized guest.

A. Depending on the host kernel implementation, the guest can see high-level metrics of all physical resources, including CPUs and disks, and notice when they are utilized by other tenants. Metrics that leak user data should be blocked by the kernel. For example, utilization for a CPU may be observable (say, 50%), but not the process IDs and process names from other tenants that are causing it.
