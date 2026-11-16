
```
60019120 77e6b11b kernel32!SetHandleCount
60019124 77e69bf9 kernel32!LoadResource
60019128 77e511e1 kernel32!FindResourceA
6001912c 77e7388c kernel32!FindResourceExA
60019130 77e5be30 kernel32!lstrlenA
60019134 77e424de kernel32!Sleep
60019138 77e4a2cb kernel32!WaitNamedPipeA
6001913c 77e63e6f kernel32!CloseHandle
60019140 77e5e123 kernel32!OpenEventA
60019144 77e622c9 kernel32!lstrlenW
60019148 77e62fc7 kernel32!GetCurrentThreadId
6001914c 77e5fdd4 kernel32!OpenProcess
60019150 77e63c78 kernel32!GetCurrentProcessId
60019154 7c81a3ab ntdll!RtlLeaveCriticalSection
60019158 7c81a360 ntdll!RtlEnterCriticalSection
6001915c 77e4cabf kernel32!GetComputerNameA
60019160 77e6f032 kernel32!ProcessIdToSessionId
60019164 77e645ff kernel32!GetModuleFileNameA
60019168 77e6474a kernel32!GetModuleHandleA
6001916c 77e62fd9 kernel32!GetCurrentProcess
60019170 77e49968 kernel32!GetCurrentDirectoryA
60019174 77e61c7b kernel32!WaitForSingleObject
60019178 77e63868 kernel32!GetCurrentThread
6001917c 7c82c988 ntdll!RtlDeleteCriticalSection
60019180 77e67861 kernel32!InitializeCriticalSection
60019184 77e6b1a1 kernel32!FreeLibrary
60019188 77e63f41 kernel32!UnmapViewOfFile
6001918c 77e643f1 kernel32!MapViewOfFile
60019190 77e6b65f kernel32!OpenFileMappingA
60019194 77e61694 kernel32!InterlockedExchange
60019198 77e4d2fb kernel32!DeleteFileA
...
...
...
60019294 00000000
**60019298 61e81000 detoured!Detoured**
6001929c 00000000
...
...
...
```

这引起了怀疑，即 _3rdPartyHook_ 以某种方式为其自身目的优化了虚拟地址空间，这导致虚拟地址空间变得更加碎片化。

## 注释

!address -summary WinDbg 命令还会给出关于区域类型使用情况以及每种区域类型中最大可用块的各种输出。

## 物理内存

有时物理内存不足，系统会经历所谓的**磁盘**或**页文件抖动**，试图解决页面错误。这可以从某些来自冻结环境的内存转储中看到，显示运行线程中存在双重陷阱的迹象，第一个陷阱是正常的内存访问错误（以粗体显示）和第二个是强制 NMI bugcheck 115 以保存内存转储（以粗斜体显示）：

```
1: kd> .bugcheck
Bugcheck code 00000080
Arguments 004f4454 00000000 00000000 00000000

1: kd> !thread
THREAD 88939b20  Cid 360.378  Teb: 7ffdb000 Win32Thread: a20a7ac8 RUNNING
IRP List:
86be9e68: (0006,0100) Flags: 00000070 Mdl: 00000000
88939e68: (0006,0100) Flags: 00000070 Mdl: 00000000
88939128: (0006,0100) Flags: 00000070 Mdl: 00000000

Not impersonating
Owning Process 889456e0
Wait Start TickCount      2357431    Elapsed Ticks: 9
Context Switch Count      18267         LargeStack
UserTime     0:00:08.0218
KernelTime   0:12:28.0109
Start Address KERNEL32!BaseThreadStartThunk (0x7c57b740)
Win32 Start Address msafd!SockAsyncThread (0x74fd3113)
Stack Init bef9e000 Current bef9db60 Base bef9e000 Limit bef9b000 Call 0
Priority 11 BasePriority 11 PriorityDecrement 0 DecrementCount 0

ChildEBP RetAddr
8904aff0 80469211 hal!HalHandleNMI+0x193
8904aff0 80438621 nt!KiTrap02+0x41
bef9dc10 8043799a nt!MiTrimWorkingSet+0xa7
bef9dc38 80437bec nt!MiDoReplacement+0x2e
bef9dc50 804453cf nt!MiLocateAndReserveWsle+0x1e
bef9dc68 804444e0 nt!MiAddValidPageToWorkingSet+0x89
bef9dc8c 8044434a nt!MiCompleteProtoPteFault+0xf6
bef9dcb8 804436e8 nt!MiResolveProtoPteFault+0x160
bef9dcfc 8044ccd0 nt!MiDispatchFault+0x8fc
bef9dd4c 8046b963 nt!MmAccessFault+0xd1c
bef9dd4c 74fd31e0 nt!KiTrap0E+0xc7
016effb4 7c57b3bc msafd!SockAsyncThread+0xcd
016effcc 00000000 KERNEL32!BaseThreadStart+0x52
```

如果我们检查虚拟内存统计信息，可以看到可用页面数量很低：

```
1: kd> !vm

*** Virtual Memory Usage ****
Physical Memory: 524165 ( 2096660 Kb)
Page File: \??\C:\pagefile.sys
Current: 4190208Kb Free Space: 3298704Kb
Minimum: 4190208Kb Maximum: 4190208Kb
Page File: \??\E:\pagefile.sys
Current: 4190208Kb Free Space: 3339860Kb
Minimum: 4190208Kb Maximum: 4190208Kb
Available Pages: 1098 ( 4392 Kb)
ResAvail Pages: 410646 ( 1642584 Kb)
Modified Pages: 282384 ( 1129536 Kb)
NonPagedPool Usage: 10046 ( 40184 Kb)
NonPagedPool Max: 68609 ( 274436 Kb)
PagedPool 0 Usage: 15391 ( 61564 Kb)
PagedPool 1 Usage: 1906 ( 7624 Kb)
PagedPool 2 Usage: 1925 ( 7700 Kb)
PagedPool 3 Usage: 1937 ( 7748 Kb)
PagedPool 4 Usage: 1892 ( 7568 Kb)
PagedPool Usage: 23051 ( 92204 Kb)
PagedPool Maximum: 87040 ( 348160 Kb)
Shared Commit: 16867 ( 67468 Kb)
Special Pool: 0 ( 0 Kb)
Free System PTEs: 65288 ( 261152 Kb)
Shared Process: 38655 ( 154620 Kb)
PagedPool Commit: 23051 ( 92204 Kb)
Driver Commit: 1060 ( 4240 Kb)
Committed pages: 1049592 ( 4198368 Kb)
Commit limit: 2580155 ( 10320620 Kb)
[...]
```

在 W2K 转储中，我们还可以看到对工作集资源的锁定（此处名称是从 **Ws** 简写推测得出的）：

```
1: kd> !locks
**** DUMP OF ALL RESOURCE OBJECTS ****

Resource @ nt!MmSystemWsLock (0x804869c0) Exclusively owned
Contention Count = 33083
NumberOfExclusiveWaiters = 237
[...]
```

并且，每个线程优先级的就绪状态线程数量巨大。

查看拥有运行线程的当前进程显示，与用户模式下花费的时间相比，页面错误数量庞大，内核 CPU 时间增加：

```
1: kd> !process 889456e0
PROCESS 889456e0 SessionId: 0 Cid: 0360 Peb: 7ffdf000 ParentCid: 01a8
    DirBase: 102af000 ObjectTable: 88945c08 TableSize: 622.
    Image: Application.EXE
    VadRoot 88944468 Clone 0 Private 838. Modified 30691412. Locked 188.
    DeviceMap 89049288
    Token                             e28db550
    ElapsedTime                       10:13:30.0684
    UserTime                          0:00:12.0578
    KernelTime                        0:12:38.0625
    QuotaPoolUsage[PagedPool]         31568
    QuotaPoolUsage[NonPagedPool]      68266
    Working Set Sizes (now,min,max)  (49, 50, 345) (196KB, 200KB, 1380KB)
    PeakWorkingSetSize                1956
    VirtualSize                       131 Mb
    PeakVirtualSize                   131 Mb
    PageFaultCount                    46180598
    MemoryPriority                    BACKGROUND
    BasePriority                      10
    CommitCharge                      1247
```

## PTE

为了维持虚拟地址到物理地址的转换，操作系统需要页表。这些表也占用内存。如果内存不足以创建新表，系统将无法创建进程、分配 I/O 缓冲区以及从池中分配内存。

我们可能会从 WinDbg 中看到以下诊断消息：

```
4: kd> !vm

*** Virtual Memory Usage ***
Physical Memory:    851422 (  3405688 Kb)
Page File: \\?\C:\pagefile.sys
  Current: 2095104 Kb  Free Space: 2081452 Kb
  Minimum: 2095104 Kb  Maximum: 4190208 Kb
Available Pages:     683464 (  2733856 Kb)
ResAvail Pages:      800927 (  3203708 Kb)
Locked IO Pages:           145 (       580 Kb)
Free System PTEs:     23980 (     95920 Kb)

***************** 356363 system PTE allocations have failed ***************
Free NP PTEs:         6238 (     24952 Kb)
Free Special NP:           0 (         0 Kb)
Modified Pages:         482 (      1928 Kb)
Modified PF Pages:      482 (      1928 Kb)
NonPagedPool Usage:   18509 (     74036 Kb)
NonPagedPool Max:     31970 (    127880 Kb)
PagedPool 0 Usage:    8091 (     32364 Kb)
PagedPool 1 Usage:    2495 (       9980 Kb)
PagedPool 2 Usage:    2580 (     10320 Kb)
PagedPool 3 Usage:    2552 (     10208 Kb)
PagedPool 4 Usage:    2584 (     10336 Kb)
PagedPool Usage:      18302 (     73208 Kb)
PagedPool Maximum:    39936 (    159744 Kb)

********************* 48530 pool allocations have failed *********************
Shared Commit:         5422 (     21688 Kb)
Special Pool:             0 (         0 Kb)
Shared Process:         5762 (     23048 Kb)
PagedPool Commit:      18365 (     73460 Kb)
Driver Commit:          2347 (      9388 Kb)
Committed pages:       129014 (    516056 Kb)
Commit limit:        1342979 (   5371916 Kb)
```

我们还可以看到关于池分配失败的另一条诊断消息，这可能是 PTE 分配失败的后果。
