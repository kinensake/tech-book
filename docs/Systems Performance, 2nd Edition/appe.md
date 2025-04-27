---
sidebar_position: 32
---

# Appendix E

Systems Performance Who’s Who

It can be useful to know who created the technologies that we use. This is a list of who’s who in the field of systems performance, based on the technologies in this book. This was inspired by the Unix who’s who list in [\[Libes 89\]](appe.md). Apologies to those who are missing or misappropriated. If you wish to dig further into the people and history, see the chapter references and the names listed in the Linux source, both the Linux repository history and the MAINTAINERS file in the Linux source code. The Acknowledgments section of my BPF book [\[Gregg 19\]](appe.md) also lists various technologies, in particular extended BPF, BCC, bpftrace, kprobes, and uprobes, and the people behind them.

**John Allspaw**: Capacity planning [\[Allspaw 08\]](appe.md).

**Gene M. Amdahl**: Early work on computer scalability [\[Amdahl 67\]](appe.md).

**Jens Axboe**: CFQ I/O Scheduler, fio, blktrace, io\_uring.

**Brenden Blanco**: BCC.

**Jeff Bonwick**: Invented kernel slab allocation, co-invented user-level slab allocation, co-invented ZFS, kstat, first developed mpstat.

**Daniel Borkmann**: Co-creator and maintainer of extended BPF.

**Roch Bourbonnais**: Sun Microsystems systems performance expert.

**Tim Bray**: Authored the Bonnie disk I/O micro-benchmark, known for XML.

**Bryan Cantrill**: Co-created DTrace; Oracle ZFS Storage Appliance Analytics.

**Rémy Card**: Primary developer for the ext2 and ext3 file systems.

**Nadia Yvette Chambers**: Linux hugetlbfs.

**Guillaume Chazarain**: iotop(1) for Linux.

**Adrian Cockcroft**: Performance books [\[Cockcroft 95\]](appe.md)[\[Cockcroft 98\]](appe.md), Virtual Adrian (SE Toolkit).

**Tim Cook**: nicstat(1) for Linux, and enhancements.

**Alan Cox**: Linux network stack performance.

**Mathieu Desnoyers**: Linux Trace Toolkit (LTTng), kernel tracepoints, main author of userspace RCU.

**Frank Ch. Eigler**: Lead developer for SystemTap.

**Richard Elling**: Static performance tuning methodology.

**Julia Evans**: Performance and debugging documentation and tools.

**Kevin Robert Elz**: DNLC.

**Roger Faulkner**: Wrote /proc for UNIX System V, thread implementation for Solaris, and the truss(1) system call tracer.

**Thomas Gleixner**: Various Linux kernel performance work including hrtimers.

**Sebastian Godard**: sysstat package for Linux, which contains numerous performance tools including iostat(1), mpstat(1), pidstat(1), nfsiostat(1), cifsiostat(1), and an enhanced version of sar(1), sadc(8), sadf(1) (see the metrics in [Appendix B](appb.md)).

**Sasha Goldshtein**: BPF tools (argdist(8), trace(8), etc.), BCC contributions.

**Brendan Gregg**: nicstat(1), DTraceToolkit, ZFS L2ARC, BPF tools (execsnoop, biosnoop, ext4slower, tcptop, etc.), BCC/bpftrace contributions, USE method, heat maps (latency, utilization, subsecond-offset), flame graphs, flame scope, this book and previous ones [\[Gregg 11a\]](appe.md)[\[Gregg 19\]](appe.md), other perf work.

**Dr. Neil Gunther**: Universal Scalability Law, ternary plots for CPU utilization, performance books \[Gunther 97].

**Jeffrey Hollingsworth**: Dynamic instrumentation [\[Hollingsworth 94\]](appe.md).

**Van Jacobson**: traceroute(8), pathchar, TCP/IP performance.

**Raj Jain**: Systems performance theory \[Jain 91].

**Jerry Jelinek**: Solaris Zones.

**Bill Joy**: vmstat(1), BSD virtual memory work, TCP/IP performance, FFS.

**Andi Kleen**: Intel performance, numerous contributions to Linux.

**Christoph Lameter**: SLUB allocator.

**William LeFebvre**: Wrote the first version of top(1), inspiring many other tools.

**David Levinthal**: Intel processor performance expert.

**John Levon**: OProfile.

**Mike Loukides**: First book on Unix systems performance [\[Loukides 90\]](appe.md), which either began or encouraged the tradition of resource-based analysis: CPU, memory, disk, network.

**Robert Love**: Linux kernel performance work, including for preemption.

**Mary Marchini**: libstapsdt: dynamic USDT for various languages.

**Jim Mauro**: Co-author of Solaris Performance and Tools [\[McDougall 06a\]](appe.md), DTrace: Dynamic Tracing in Oracle Solaris, Mac OS X, and FreeBSD \[Gregg 11].

**Richard McDougall**: Solaris microstate accounting, co-author of Solaris Performance and Tools \[McDougall 06a].

**Marshall Kirk McKusick**: FFS, work on BSD.

**Arnaldo Carvalho de Melo**: Linux perf(1) maintainer.

**Barton Miller**: Dynamic instrumentation \[Hollingsworth 94].

**David S. Miller**: Linux networking maintainer and SPARC maintainer. Numerous performance improvements, and support for extended BPF.

**Cary Millsap**: Method R.

**Ingo Molnar**: O(1) scheduler, completely fair scheduler, voluntary kernel preemption, ftrace, perf, and work on real-time preemption, mutexes, futexes, scheduler profiling, work queues.

**Richard J. Moore**: DProbes, kprobes.

**Andrew Morton**: fadvise, read-ahead.

**Gian-Paolo D. Musumeci**: *System Performance Tuning*, 2nd Ed. [\[Musumeci 02\]](appe.md).

**Mike Muuss**: ping(8).

**Shailabh Nagar**: Delay accounting, taskstats.

**Rich Pettit**: SE Toolkit.

**Nick Piggin**: Linux scheduler domains.

**Bill Pijewski**: Solaris vfsstat(1M), ZFS I/O throttling.

**Dennis Ritchie**: Unix, and its original performance features: process priorities, swapping, buffer cache, etc.

**Alastair Robertson**: Created bpftrace.

**Steven Rostedt**: Ftrace, KernelShark, real-time Linux, adaptive spinning mutexes, Linux tracing support.

**Rusty Russell**: Original futexes, various Linux kernel work.

**Michael Shapiro**: Co-created DTrace.

**Aleksey Shipilëv**: Java performance expert.

**Balbir Singh**: Linux memory resource controller, delay accounting, taskstats, cgroupstats, CPU accounting.

**Yonghong Song**: BTF, and extended BPF and BCC work.

**Alexei Starovoitov**: Co-creator and maintainer of extended BPF.

**Ken Thompson**: Unix, and its original performance features: process priorities, swapping, buffer cache, etc.

**Martin Thompson**: Mechanical sympathy.

**Linus Torvalds**: The Linux kernel and numerous core components necessary for systems performance, Linux I/O scheduler, Git.

**Arjan van de Ven**: latencytop, PowerTOP, irqbalance, work on Linux scheduler profiling.

**Nitsan Wakart**: Java performance expert.

**Tobias Waldekranz**: ply (first high-level BPF tracer).

**Dag Wieers**: dstat.

**Karim Yaghmour**: LTT, push for tracing in Linux.

**Jovi Zhangwei**: ktap.

**Tom Zanussi**: Ftrace hist triggers.

**Peter Zijlstra**: Adaptive spinning mutex implementation, hardirq callbacks framework, other Linux performance work.

### E.1 References

**\[Amdahl 67]** Amdahl, G., “Validity of the Single Processor Approach to Achieving Large Scale Computing Capabilities,” *AFIPS*, 1967.

**\[Libes 89]** Libes, D., and Ressler, S., *Life with UNIX: A Guide for Everyone*, Prentice Hall, 1989.

**\[Loukides 90]** Loukides, M., *System Performance Tuning*, O’Reilly, 1990.

**\[Hollingsworth 94]** Hollingsworth, J., Miller, B., and Cargille, J., “Dynamic Program Instrumentation for Scalable Performance Tools,” *Scalable High-Performance Computing Conference (SHPCC)*, May 1994.

**\[Cockcroft 95]** Cockcroft, A., *Sun Performance and Tuning*, Prentice Hall, 1995.

**\[Cockcroft 98]** Cockcroft, A., and Pettit, R., *Sun Performance and Tuning: Java and the Internet*, Prentice Hall, 1998.

**\[Musumeci 02]** Musumeci, G. D., and Loukidas, M., *System Performance Tuning*, 2nd Edition, O’Reilly, 2002.

**\[McDougall 06a]** McDougall, R., Mauro, J., and Gregg, B., *Solaris Performance and Tools: DTrace and MDB Techniques for Solaris 10 and OpenSolaris*, Prentice Hall, 2006.

**\[Gunther 07]** Gunther, N., *Guerrilla Capacity Planning*, Springer, 2007.

**\[Allspaw 08]** Allspaw, J., *The Art of Capacity Planning*, O’Reilly, 2008.

**\[Gregg 11a]** Gregg, B., and Mauro, J., *DTrace: Dynamic Tracing in Oracle Solaris, Mac OS X and FreeBSD*, Prentice Hall, 2011.

**\[Gregg 19]** Gregg, B., *BPF Performance Tools: Linux System and Application Observability*, Addison-Wesley, 2019.
