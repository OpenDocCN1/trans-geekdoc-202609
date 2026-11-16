# Accidental Lock

When a system is unresponsive or sluggish, we usually check _ERESOURCE locks in the kernel or complete memory dumps to see **Deadlock** (page 193) or **High Contention** (page 477) patterns. However, there is some chance that reported locks are purely accidental and appear in a crash dump because they just happened at that time. We need to look at _Contention Count_, _Ticks_ and _KernelTime_ in both blocking and blocked threads to recognize an **Accidental Lock**. Also, WinDbg may not distinguish between prolonged and accidental locks when we use `!analyze -v -hang` command, and merely reports some lock chain it finds among equal alternatives.

Here is an example. The system was reported hung, and kernel memory dump was saved. WinDbg analysis command reports one thread blocking 3 other threads and the driver on top of the blocking thread stack is _AVDriver.sys_. The algorithm WinDbg uses to point to specific image name is described in minidump analysis article⁶ and in our case it chooses _AVDriver_ module:

```
BLOCKED_THREAD: 8089d8c0

BLOCKING_THREAD: 8aab4700

LOCK_ADDRESS: 8859a570 -- (!locks 8859a570)

Resource @ 0x8859a570 Exclusively owned
 Contention Count = 3
 NumberOfExclusiveWaiters = 3
 Threads: 8aab4700-01<*>
 Threads Waiting On Exclusive Access:
 885d0020 88a7c020 8aafc7d8

1 total locks, 1 locks currently held

BUGCHECK_STR: LOCK_HELD

FAULTING_THREAD: 8aab4700

STACK_TEXT:
f592f698 80832f7a nt!KiSwapContext+0x26
f592f6c4 80828705 nt!KiSwapThread+0x284
f592f70c 7f22a394 nt!KeDelayExecutionThread+0x2ab
WARNING: Stack unwind information not available. Following frames may be wrong.
f592f734 f720ae35 AVDriver+0x1394
f592f750 f720b208 AVDriver+0x1e35
f592f794 f721945a AVDriver+0x2208
f592f7cc 8081dcdf AVDriver+0x1045a
f592f7e0 f5b9f76a nt!IoCallDriver+0x45
f592f7f0 f5b9c621 Driver!FS_Dispatch+0xa4
```