---
sidebar_position: 28
---

# Appendix A

USE Method: Linux

This appendix contains a checklist for Linux derived from the USE method [\[Gregg 13d\]](appa.md). This is a method for checking system health, and identifying common resource bottlenecks and errors, introduced in [Chapter 2](ch02.md), [Methodologies](ch02.md), [Section 2.5.9](ch02.md), [The USE Method](ch02.md). Later chapters ([5](ch05.md), [6](ch06.md), [7](ch07.md), [9](ch09.md), [10](ch10.md)) described it in specific contexts and introduced tools to support its use.

Performance tools are often enhanced, and new ones are developed, so you should treat this as a starting point that will need updates. New observability frameworks and tools can also be developed to specifically make following the USE method easier.

### Physical Resources

**Component**

**Type**

**Metric**

CPU

Utilization

Per CPU: `mpstat -P ALL 1`, sum of CPU-consuming columns (`%usr`, `%nice`, `%sys`, `%irq`, `%soft`, `%guest`, `%gnice`) or inverse of idle columns (`%iowait`, `%steal`, `%idle`); `sar -P ALL`, sum of CPU-consuming columns (`%user`, `%nice`, `%system`) or inverse of idle columns (`%iowait`, `%steal`, `%idle`)

System-wide: `vmstat 1`, `us` + `sy`; `sar -u`, `%user` + `%nice` + `%system`

Per process: `top`, `%CPU`; `htop`, `CPU%`; `ps -o pcpu`; `pidstat 1`, `%CPU`

Per kernel thread: `top/htop` (`K` to toggle), where VIRT == 0 (heuristic)

CPU

Saturation

System-wide: `vmstat 1`, `r` &gt; CPU count[1](appa.md); `sar -q`, `runq-sz` &gt; CPU count; `runqlat`; `runqlen`

Per process: /proc/PID/schedstat 2nd field (sched\_info.run\_delay); getdelays.c, `CPU`[2](appa.md); `perf sched latency` (shows average and maximum delay per schedule)[3](appa.md)

CPU

Errors

Machine Check Exceptions (MCEs) seen in `dmesg` or rasdaemon and `ras-mc-ctl --summary`; perf(1) if processor-specific error events (PMCs) are available; e.g., AMD64’s “04Ah Single-bit ECC Errors Recorded by Scrubber”[4](appa.md) (which can also be classified as a memory device error); `ipmtool sel list`; `ipmitool sdr list`

Memory capacity

Utilization

System-wide: `free -m`, `Mem:` (main memory), `Swap:` (virtual memory); `vmstat 1`, `free` (main memory), `swap` (virtual memory); `sar -r`, `%memused`; `slabtop -s c` for kmem slab usage

Per process: `top`/`htop`, `RES` (resident main memory), `VIRT` (virtual memory), `Mem` for system-wide summary

Memory capacity

Saturation

System-wide: `vmstat 1`, `si`/`so` (swapping); `sar -B`, `pgscank` + `pgscand` (scanning); `sar -W`

Per process: getdelays.c, `SWAP`2; 10th field (min\_flt) from /proc/PID/stat for minor fault rate, or dynamic instrumentation[5](appa.md); `dmesg | grep killed` (OOM killer)

Memory capacity

Errors

`dmesg` for physical failures or rasdaemon and `ras-mc-ctl --summary` or `edac-util`; `dmidecode` may also show physical failures; `ipmtool sel list`; `ipmitool sdr list`; dynamic instrumentation, e.g., uretprobes for failed malloc()s (bpftrace)

Network interfaces

Utilization

`ip -s link`, RX/TX tput / max bandwidth; `sar -n DEV`, rx/tx kB/s / max bandwidth; /proc/net/dev, `bytes` RX/TX tput/max

Network interfaces

Saturation

`nstat`, `TcpRetransSegs`; `sar -n EDEV`, `*drop/s`, `*fifo/s`[6](appa.md); /proc/net/dev, RX/TX `drop`; dynamic instrumentation of other TCP/IP stack queueing (bpftrace)

Network interfaces

Errors

`ip -s link`, `errors`; `sar -n EDEV` all; /proc/net/dev, `errs`, `drop6`; extra counters may be under /sys/class/net/\*/statistics/\*error\*; dynamic instrumentation of driver function returns

Storage device I/O

Utilization

System-wide: `iostat -xz 1`, `%util`; `sar -d`, `%util`; per process: `iotop`, `biotop`; /proc/PID/sched `se.statistics.iowait_sum`

Storage device I/O

Saturation

`iostat -xnz 1`, `avgqu-sz` &gt; 1, or high `await`; `sar -d` same; perf(1) block tracepoints for queue length/latency; `biolatency`

Storage device I/O

Errors

/sys/devices/ . . . /ioerr\_cnt; `smartctl`; `bioerr`; dynamic/static instrumentation of I/O subsystem response codes[7](appa.md)

Storage capacity

Utilization

Swap: `swapon -s`; `free`; /proc/meminfo `SwapFree`/`SwapTotal`; file systems: `df -h`

Storage capacity

Saturation

Not sure this one makes sense—once it’s full, ENOSPC (although when close to full, performance may be degraded depending on the file system free block algorithm)

Storage capacity

File systems: errors

`strace` for ENOSPC; dynamic instrumentation for ENOSPC; /var/log/messages errs, depending on FS; application log errors

Storage controller

Utilization

`iostat -sxz 1`, sum devices and compare to known IOPS/tput limits per card

Storage controller

Saturation

See storage device saturation, . . .

Storage controller

Errors

See storage device errors, . . .

Network controller

Utilization

Infer from `ip –s link` (or `sar`, or /proc/net/dev) and known controller max tput for its interfaces

Network controller

Saturation

See network interfaces, saturation, . . .

Network controller

Errors

See network interfaces, errors, . . .

CPU interconnect

Utilization

`perf stat` with PMCs for CPU interconnect ports, tput/max

CPU interconnect

Saturation

`perf stat` with PMCs for stall cycles

CPU interconnect

Errors

`perf stat` with PMCs for whatever is available

Memory interconnect

Utilization

`perf stat` with PMCs for memory buses, tput/max; e.g. Intel uncore\_imc/data\_reads/,uncore\_imc/data\_writes/; or IPC less than, say, 0.2; PMCs may also have local versus remote counters

Memory interconnect

Saturation

`perf stat` with PMCs for stall cycles

Memory interconnect

Errors

`perf stat` with PMCs for whatever is available; `dmidecode` might have something

I/O interconnect

Utilization

`perf stat` with PMCs for tput/max if available; inference via known tput from iostat/ip/ . . .

I/O interconnect

Saturation

`perf stat` with PMCs for stall cycles

I/O interconnect

Errors

`perf stat` with PMCs for whatever is available

General notes: `uptime` “load average” (or /proc/loadavg) wasn’t included for CPU metrics since Linux load averages include tasks in the uninterruptible I/O state.

perf(1): is a powerful observability toolkit that reads PMCs and can also use dynamic and static instrumentation. Its interface is the perf(1) command. See [Chapter 13](ch13.md), [perf](ch13.md).

PMCs: Performance monitoring counters. See [Chapter 6](ch06.md), [CPUs](ch06.md), and their usage with perf(1).

I/O interconnect: This includes the CPU-to-I/O controller buses, the I/O controller(s), and device buses (e.g., PCIe).

Dynamic instrumentation: allows custom metrics to be developed. See [Chapter 4](ch04.md), [Observability Tools](ch04.md), and the examples in later chapters. Dynamic tracing tools for Linux include perf(1) ([Chapter 13](ch13.md)), Ftrace ([Chapter 14](ch14.md)), BCC and bpftrace ([Chapter 15](ch15.md)).

For any environment that imposes resource controls (e.g., cloud computing), check USE for each resource control. These may be encountered—and limit usage—before the hardware resource is fully utilized.

[1](appa.md)The `r` column reports those threads that are waiting *and* threads that are running on-CPU. See the `vmstat(1)` description in [Chapter 6](ch06.md), [CPUs](ch06.md).

[2](appa.md)Uses delay accounting; see [Chapter 4](ch04.md), [Observability Tools](ch04.md).

[3](appa.md)There is also the sched:sched\_process\_wait tracepoint for perf(1); be careful about overheads when tracing, as scheduler events are frequent.

[4](appa.md)There aren’t many error-related events in the recent Intel and AMD processor manuals.

[5](appa.md)This can be used to show what is consuming memory and leading to saturation, by seeing what is causing minor faults. This should be available in htop(1) as MINFLT.

[6](appa.md)Dropped packets are included as both saturation and error indicators, since they can occur due to both types of events.

[7](appa.md)This includes tracing functions from different layers of the I/O subsystem: block device, SCSI, SATA, IDE... Some static probes are available (perf(1) scsi and block tracepoint events); otherwise, use dynamic tracing.

### Software Resources

**Component**

**Type**

**Metric**

Kernel mutex

Utilization

With CONFIG\_LOCK\_STATS=y, /proc/lock\_stat `holdtime-total` / `acquisitions` (also see `holdtime-min`, `holdtime-max`)[8](appa.md); dynamic instrumentation of lock functions or instructions (maybe)

Kernel mutex

Saturation

With CONFIG\_LOCK\_STATS=y, /proc/lock\_stat `waittime-total` / `contentions` (also see `waittime-min`, `waittime-max`); dynamic instrumentation of lock functions, e.g., `mlock.bt` \[Gregg 19]; spinning shows up with profiling `perf record -a -g -F 99` ...

Kernel mutex

Errors

Dynamic instrumentation (e.g., recursive mutex enter); other errors can cause kernel lockup/panic, debug with kdump/`crash`

User mutex

Utilization

`valgrind --tool=drd --exclusive-threshold=` ... (held time); dynamic instrumentation of lock-to-unlock function time[9](appa.md)

User mutex

Saturation

`valgrind --tool=drd` to infer contention from held time; dynamic instrumentation of synchronization functions for wait time, e.g., `pmlock.bt`; profiling (perf(1)) user stacks for spins

User mutex

Errors

`valgrind --tool=drd` various errors; dynamic instrumentation of pthread\_mutex\_lock() for EAGAIN, EINVAL, EPERM, EDEADLK, ENOMEM, EOWNERDEAD, . . .

Task capacity

Utilization

`top`/`htop`, `Tasks` (current); `sysctl kernel.threads-max`, /proc/sys/kernel/threads-max (max)

Task capacity

Saturation

Threads blocking on memory allocation; at this point the page scanner should be running (`sar -B`, `pgscan*`), else examine using dynamic tracing

Task capacity

Errors

“can’t fork()” errors; user-level threads: pthread\_create() failures with EAGAIN, EINVAL, . . . ; kernel: dynamic tracing of kernel\_thread() ENOMEM

File descriptors

Utilization

System-wide: `sar -v`, `file-nr` versus /proc/sys/fs/file-max; or just /proc/sys/fs/file-nr

Per process: `echo /proc/PID/fd/* | wc -w` versus `ulimit -n`

File descriptors

Saturation

This one may not make sense

File descriptors

Errors

`strace` errno == EMFILE on syscalls returning file descriptors (e.g., open(2), accept(2), ...); `opensnoop -x`

[8](appa.md)Kernel lock analysis used to be via lockmeter, which had an interface called lockstat.

[9](appa.md)Since these functions can be very frequent, beware of the performance overhead of tracing every call: an application could slow by 2x or more.

### A.1 References

**\[Gregg 13d]** Gregg, B., “USE Method: Linux Performance Checklist,” [http://www.brendangregg.com/USEmethod/use-linux.html](http://www.brendangregg.com/USEmethod/use-linux.html), first published 2013.
