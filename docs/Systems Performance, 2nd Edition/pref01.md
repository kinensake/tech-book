---
sidebar_position: 9
---

# Preface

*“There are known knowns; there are things we know we know. We also know there are known unknowns; that is to say we know there are some things we do not know. But there are also unknown unknowns—there are things we do not know we don’t know.”*

—U.S. Secretary of Defense Donald Rumsfeld, February 12, 2002

While the previous statement was met with chuckles from those attending the press briefing, it summarizes an important principle that is as relevant in complex technical systems as it is in geopolitics: performance issues can originate from anywhere, including areas of the system that you know nothing about and you are therefore not checking (the unknown unknowns). This book may reveal many of these areas, while providing methodologies and tools for their analysis.

### About This Edition

I wrote the first edition eight years ago and designed it to have a long shelf life. Chapters are structured to first cover durable skills (models, architecture, and methodologies) and then faster-changing skills (tools and tuning) as example implementations. While the example tools and tuning will go out of date, the durable skills show you how to stay updated.

There has been a large addition to Linux in the past eight years: Extended BPF, a kernel technology that powers a new generation of performance analysis tools, which is used by companies including Netflix and Facebook. I have included a BPF chapter and BPF tools in this new edition, and I have also published a deeper reference on the topic [\[Gregg 19\]](pref01.md). The Linux perf and Ftrace tools have also seen many developments, and I have added separate chapters for them as well. The Linux kernel has gained many performance features and technologies, also covered. The hypervisors that drive cloud computing virtual machines, and container technologies, have also changed considerably; that content has been updated.

The first edition covered both Linux and Solaris equally. Solaris market share has shrunk considerably in the meantime [\[ITJobsWatch 20\]](pref01.md), so the Solaris content has been largely removed from this edition, making room for more Linux content to be included. However, your understanding of an operating system or kernel can be enhanced by considering an alternative, for perspective. For that reason, some mentions of Solaris and other operating systems are included in this edition.

For the past six years I have been a senior performance engineer at Netflix, applying the field of systems performance to the Netflix microservices environment. I’ve worked on the performance of hypervisors, containers, runtimes, kernels, databases, and applications. I’ve developed new methodologies and tools as needed, and worked with experts in cloud performance and Linux kernel engineering. These experiences have contributed to improving this edition.

### About This Book

Welcome to *Systems Performance: Enterprise and the Cloud*, 2nd Edition! This book is about the performance of operating systems and of applications from the operating system context, and it is written for both enterprise server and cloud computing environments. Much of the material in this book can also aid your analysis of client devices and desktop operating systems. My aim is to help you get the most out of your systems, whatever they are.

When working with application software that is under constant development, you may be tempted to think of operating system performance—where the kernel has been developed and tuned for decades—as a solved problem. It isn’t! The operating system is a complex body of software, managing a variety of ever-changing physical devices with new and different application workloads. The kernels are also in constant development, with features being added to improve the performance of particular workloads, and newly encountered bottlenecks being removed as systems continue to scale. Kernel changes such as the mitigations for the Meltdown vulnerability that were introduced in 2018 can also hurt performance. Analyzing and working to improve the performance of the operating system is an ongoing task that should lead to continual performance improvements. Application performance can also be analyzed from the operating system context to find more clues that might be missed using application-specific tools alone; I’ll cover that here as well.

#### Operating System Coverage

The main focus of this book is the study of systems performance, using Linux-based operating systems on Intel processors as the primary example. The content is structured to help you study other kernels and processors as well.

Unless otherwise noted, the specific Linux distribution is not important in the examples used. The examples are mostly from the Ubuntu distribution and, when necessary, notes are included to explain differences for other distributions. The examples are also taken from a variety of system types: bare metal and virtualized, production and test, servers and client devices.

Across my career I’ve worked with a variety of different operating systems and kernels, and this has deepened my understanding of their design. To deepen your understanding as well, this book includes some mentions of Unix, BSD, Solaris, and Windows.

#### Other Content

Example screenshots from performance tools are included, not just for the data shown, but also to illustrate the types of data available. The tools often present the data in intuitive and self-explanatory ways, many in the familiar style of earlier Unix tools. This means that screenshots can be a powerful way to convey the purpose of these tools, some requiring little additional description. (If a tool does require laborious explanation, that may be a failure of design!)

Where it provides useful insight to deepen your understanding, I touch upon the history of certain technologies. It is also useful to learn a bit about the key people in this industry: you’re likely to come across them or their work in performance and other contexts. A “who’s who” list has been provided in [Appendix E](appe.md).

A handful of topics in this book were also covered in my prior book, *BPF Performance Tools* [\[Gregg 19\]](pref01.md): in particular, BPF, BCC, bpftrace, tracepoints, kprobes, uprobes, and various BPF-based tools. You can refer to that book for more information. The summaries of these topics in this book are often based on that earlier book, and sometimes use the same text and examples.

#### What Isn’t Covered

This book focuses on performance. To undertake all the example tasks given will require, at times, some system administration activities, including the installation or compilation of software (which is not covered here).

The content also summarizes operating system internals, which are covered in more detail in separate dedicated texts. Advanced performance analysis topics are summarized so that you are aware of their existence and can study them as needed from additional sources. See the Supplemental Material section at the end of this Preface.

#### How This Book Is Structured

**[Chapter 1](ch01.md), [Introduction](ch01.md),** is an introduction to systems performance analysis, summarizing key concepts and providing examples of performance activities.

**[Chapter 2](ch02.md), [Methodologies](ch02.md),** provides the background for performance analysis and tuning, including terminology, concepts, models, methodologies for observation and experimentation, capacity planning, analysis, and statistics.

**[Chapter 3](ch03.md), [Operating Systems](ch03.md),** summarizes kernel internals for the performance analyst. This is necessary background for interpreting and understanding what the operating system is doing.

**[Chapter 4](ch04.md), [Observability Tools](ch04.md),** introduces the types of system observability tools available, and the interfaces and frameworks upon which they are built.

**[Chapter 5](ch05.md), [Applications](ch05.md),** discusses application performance topics and observing them from the operating system.

**[Chapter 6](ch06.md), [CPUs](ch06.md),** covers processors, cores, hardware threads, CPU caches, CPU interconnects, device interconnects, and kernel scheduling.

**[Chapter 7](ch07.md), [Memory](ch07.md),** is about virtual memory, paging, swapping, memory architectures, buses, address spaces, and allocators.

**[Chapter 8](ch08.md), [File Systems](ch08.md),** is about file system I/O performance, including the different caches involved.

**[Chapter 9](ch09.md), [Disks](ch09.md),** covers storage devices, disk I/O workloads, storage controllers, RAID, and the kernel I/O subsystem.

**[Chapter 10](ch10.md), [Network](ch10.md),** is about network protocols, sockets, interfaces, and physical connections.

**[Chapter 11](ch11.md), [Cloud Computing](ch11.md),** introduces operating system– and hardware-based virtualization methods in common use for cloud computing, along with their performance overhead, isolation, and observability characteristics. This chapter covers hypervisors and containers.

**[Chapter 12](ch12.md), [Benchmarking](ch12.md),** shows how to benchmark accurately, and how to interpret others’ benchmark results. This is a surprisingly tricky topic, and this chapter shows how you can avoid common mistakes and try to make sense of it.

**[Chapter 13](ch13.md), [perf](ch13.md),** summarizes the standard Linux profiler, perf(1), and its many capabilities. This is a reference to support perf(1)’s use throughout the book.

**[Chapter 14](ch14.md), [Ftrace](ch14.md),** summarizes the standard Linux tracer, Ftrace, which is especially suited for exploring kernel code execution.

**[Chapter 15](ch15.md), [BPF](ch15.md),** summarizes the standard BPF front ends: BCC and bpftrace.

**[Chapter 16](ch16.md), [Case Study](ch16.md),** contains a systems performance case study from Netflix, showing how a production performance puzzle was analyzed from beginning to end.

[Chapters 1](ch01.md) to [4](ch04.md) provide essential background. After reading them, you can reference the remainder of the book as needed, in particular [Chapters 5](ch05.md) to [12](ch12.md), which cover specific targets for analysis. [Chapters 13](ch13.md) to [15](ch15.md) cover advanced profiling and tracing, and are optional reading for those who wish to learn one or more tracers in more detail.

[Chapter 16](ch16.md) uses a storytelling approach to paint a bigger picture of a performance engineer’s work. If you’re new to performance analysis, you might want to read this first as an example of performance analysis using a variety of different tools, and then return to it when you’ve read the other chapters.

#### As a Future Reference

This book has been written to provide value for many years, by focusing on background and methodologies for the systems performance analyst.

To support this, many chapters have been separated into two parts. The first part consists of terms, concepts, and methodologies (often with those headings), which should stay relevant many years from now. The second provides examples of how the first part is implemented: architecture, analysis tools, and tunables, which, while they will become out-of-date, will still be useful as examples.

#### Tracing Examples

We frequently need to explore the operating system in depth, which can be done using tracing tools.

Since the first edition of this book, extended BPF has been developed and merged into the Linux kernel, powering a new generation of tracing tools that use the BCC and bpftrace front ends. This book focuses on BCC and bpftrace, and also the Linux kernel’s built-in Ftrace tracer. BPF, BCC, and bpftrace, are covered in more depth in my prior book [\[Gregg 19\]](pref01.md).

Linux perf is also included in this book and is another tool that can do tracing. However, perf is usually included in chapters for its sampling and PMC analysis capabilities, rather than for tracing.

You may need or wish to use different tracing tools, which is fine. The tracing tools in this book are used to show the questions that you can ask of the system. It is often these questions, and the methodologies that pose them, that are the most difficult to know.

#### Intended Audience

The intended audience for this book is primarily systems administrators and operators of enterprise and cloud computing environments. It is also a reference for developers, database administrators, and web server administrators who need to understand operating system and application performance.

As a performance engineer at a company with a large compute environment (Netflix), I frequently work with SREs (site reliability engineers) and developers who are under enormous time pressure to solve multiple simultaneous performance issues. I have also been on the Netflix CORE SRE on-call rotation and have experienced this pressure firsthand. For many people, performance is not their primary job, and they need to know just enough to solve the current issues. Knowing that your time may be limited has encouraged me to keep this book as short as possible, and structure it to facilitate jumping ahead to specific chapters.

Another intended audience is students: this book is also suitable as a supporting text for a systems performance course. I have taught these classes before and learned which types of material work best in leading students to solve performance problems; that has guided my choice of content for this book.

Whether or not you are a student, the chapter exercises give you an opportunity to review and apply the material. These include some optional advanced exercises, which you are not expected to solve. (They may be impossible; they should at least be thought-provoking.)

In terms of company size, this book should contain enough detail to satisfy environments from small to large, including those with dozens of dedicated performance staff. For many smaller companies, the book may serve as a reference when needed, with only some portions of it used day to day.

#### Typographic Conventions

The following typographical conventions are used throughout this book:

**Example**

**Description**

netif\_receive\_skb()

Function name

iostat(1)

A command referenced by [chapter 1](ch01.md) of its man page

read(2)

A system call referenced by its man page

malloc(3)

A C library function call referenced by its man page

vmstat(8)

An administration command referenced by its man page

Documentation/...

Linux documentation in the Linux kernel source tree

kernel/...

Linux kernel source code

fs/...

Linux kernel source code, file systems

CONFIG\_...

Linux kernel configuration option (Kconfig)

`r_await`

Command line input and output

`mpstat 1`

Highlighting of a typed command or key detail

`#`

Superuser (root) shell prompt

`$`

User (non-root) shell prompt

`^C`

A command was interrupted (Ctrl-C)

`[...]`

Truncation

#### Supplemental Material, References, and Bibliography

References are listed are at the end of each chapter rather than in a single bibliography, allowing you to browse references related to each chapter’s topic. The following selected texts can also be referenced for further background on operating systems and performance analysis:

**\[Jain 91]** Jain, R., *The Art of Computer Systems Performance Analysis: Techniques for Experimental Design, Measurement, Simulation, and Modeling*, Wiley, 1991.

**\[Vahalia 96]** Vahalia, U., *UNIX Internals: The New Frontiers*, Prentice Hall, 1996.

**\[Cockcroft 98]** Cockcroft, A., and Pettit, R., *Sun Performance and Tuning: Java and the Internet*, Prentice Hall, 1998.

**\[Musumeci 02]** Musumeci, G. D., and Loukides, M., *System Performance Tuning*, 2nd Edition, O’Reilly, 2002.

**\[Bovet 05]** Bovet, D., and Cesati, M., *Understanding the Linux Kernel,* 3rd Edition, O’Reilly, 2005.

**\[McDougall 06a]** McDougall, R., Mauro, J., and Gregg, B., *Solaris Performance and Tools: DTrace and MDB Techniques for Solaris 10 and OpenSolaris*, Prentice Hall, 2006.

**\[Gove 07]** Gove, D., *Solaris Application Programming*, Prentice Hall, 2007.

**\[Love 10]** Love, R., *Linux Kernel Development*, 3rd Edition, Addison-Wesley, 2010.

**\[Gregg 11a]** Gregg, B., and Mauro, J., *DTrace: Dynamic Tracing in Oracle Solaris, Mac OS X and FreeBSD*, Prentice Hall, 2011.

**\[Gregg 13a]** Gregg, B., *Systems Performance: Enterprise and the Cloud*, Prentice Hall, 2013 (first edition).

**\[Gregg 19]** Gregg, B., *BPF Performance Tools: Linux System and Application Observability*, Addison-Wesley, 2019.

**\[ITJobsWatch 20]** ITJobsWatch, “Solaris Jobs,” [https://www.itjobswatch.co.uk/jobs/uk/solaris.do#demand\_trend](https://www.itjobswatch.co.uk/jobs/uk/solaris.do#demand_trend), accessed 2020.
