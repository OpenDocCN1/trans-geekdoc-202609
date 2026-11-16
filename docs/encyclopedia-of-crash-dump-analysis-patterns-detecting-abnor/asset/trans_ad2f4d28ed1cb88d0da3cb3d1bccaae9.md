
这种分析模式在比较堆栈跟踪差异时非常有用，或者在某些问题版本没有符号、但希望将线程映射到其他先前正常运行（其中符号文件可用）的版本时也非常有用。任何不一致都可能指向进一步诊断分析的方向。例如，我们得到了堆栈跟踪集合（第 943 页）的这段片段：

```
4.000188 fffffa800d3d3b50 ffd0780f Blocked ModuleA+0x1ac1
4.00018c fffffa800d3f9950 ffd07b53 Blocked ModuleA+0xd802
4.000190 fffffa800d4161b0 fffffda6 Blocked ModuleA+0x9ce4
4.000194 fffffa800d418b50 fffffda6 Blocked ModuleA+0x9ce4
4.000198 fffffa800d418660 fffffda6 Blocked ModuleA+0x9ce4
4.0001ac fffffa800d41eb50 ffd078d2 Blocked ModuleA+0x7cf
4.0001b0 fffffa800d41e660 ffd0780f Blocked ModuleA+0x9ce4
4.0001c0 fffffa800d48f300 ffd0e5c0 Blocked ModuleA+0x7ee5
```

我们没有符号，因此不知道这些线程是否存在任何问题。幸运的是，我们从先前的 32 位版本中拥有了可用符号文件的线程部分序：

```
4.0000ec 85d8dc58 000068c Blocked ModuleA!FuncA+0x9b
4.0000f0 85d9fc78 001375a Blocked ModuleA!FuncB+0x67
**4.0000fc 85db8a58 000068c Blocked ModuleA!WorkerThread+0xa2**
**4.000104 85cdbdb4 000ff44 Blocked ModuleA!WorkerThread+0xa2**
**4.000108 85da2788 000ff47 Blocked ModuleA!WorkerThread+0xa2**
4.000110 857862e0 0013758 Blocked ModuleA!FuncC+0xe4
4.000114 85dda250 000ff44 Blocked ModuleA!FuncD+0xf2
```

如果将工作线程映射到 x64 版本的中间部分，我们会发现只是多了一个工作线程，但整体顺序相同：

```
4.000188 fffffa800d3d3b50 ffd0780f Blocked ModuleA+0x1ac1
4.00018c fffffa800d3f9950 ffd07b53 Blocked ModuleA+0xd802
4.000190 fffffa800d4161b0 fffffda6 Blocked ModuleA+0x9ce4
4.000194 fffffa800d418b50 fffffda6 Blocked ModuleA+0x9ce4
4.000198 fffffa800d418660 fffffda6 Blocked ModuleA+0x9ce4
4.0001ac fffffa800d41eb50 ffd078d2 Blocked ModuleA+0x7cf
4.0001b0 fffffa800d41e660 ffd0780f Blocked ModuleA+0x9ce4
4.0001c0 fffffa800d48f300 ffd0e5c0 Blocked ModuleA+0x7ee5
```

如果 x86 线程部分序也正常，那么我们可以认为 x64 线程部分序是正常的。当然，这仅是初步判断，随后需要继续寻找其他异常行为模式。如果有必要，我们可能需要更深入地检查堆栈跟踪，因为两个线程部分序中各个线程的堆栈跟踪深度、子跟踪以及对其他组件的使用可能有所不同。尽管顺序相同，但某些线程实际上可能是异常的。

## 线程饥饿

### 正常优先级

这里展示了经典线程饥饿的可能迹象。假设我们有两个优先级为 8 的运行线程：

```
0: kd> !running

System Processors 3 (affinity mask)
Idle Processors 0

PRCBs Current Next
0 ffdff120 89a92020 O..............
1 f7737120 89275020 W..............

0: kd> !thread 89a92020
THREAD 89a92020 Cid 11d8.27d8 Teb: 7ffd9000 Win32Thread: bc1e6860 RUNNING on processor 0
[...]
Priority 8 BasePriority 8 PriorityDecrement 0

0: kd> !thread 89275020
THREAD 89275020 Cid 1cd0.2510 Teb: 7ffa9000 Win32Thread: bc343180 RUNNING on processor 1
[...]
Priority 8 BasePriority 8 PriorityDecrement 0
```

如果有其他具有相同优先级且竞争相同处理器（高竞争，第 480 页）的就绪线程，优先级较低的其他线程可能会饥饿（以粗体斜体显示）：

```
0: kd> !ready
Processor 0: Ready Threads at priority 8
THREAD 894a1db0 Cid 1a98.25c0 Teb: 7ffde000 Win32Thread: bc19cea8 READY
THREAD 897c4818 Cid 11d8.1c5c Teb: 7ffa2000 Win32Thread: bc2c5ba8 READY
THREAD 8911fdf18 Cid 2730.03f4 Teb: 7ffd9000 Win32Thread: bc305830 READY
Processor 0: Ready Threads at priority 7
THREAD 8a9e5ab0 Cid 0250.0470 Teb: 7fff9f000 Win32Thread: 00000000 READY
THREAD 8a086838 Cid 0250.0654 Teb: 7ff93000 Win32Thread: 00000000 READY
THREAD 8984b8b8 Cid 0250.1dc4 Teb: 7fff99000 Win32Thread: 00000000 READY
THREAD 8912a4c0 Cid 0f4c.2410 Teb: 7ff81000 Win32Thread: 00000000 READY
THREAD 89e5c570 Cid 0f4c.01c8 Teb: 00000000 Win32Thread: 00000000 READY
Processor 0: Ready Threads at priority 6
THREAD 8a9353b0 Cid 1584.1598 Teb: 7ffb8000 Win32Thread: bc057698 READY
THREAD 8aba2020 Cid 1584.15f0 Teb: 7ff9f000 Win32Thread: bc20aea8 READY
THREAD 8aab17a0 Cid 1584.01a8 Teb: 7ff92000 Win32Thread: bc316ea8 READY
THREAD 8a457020 Cid 1584.0634 Teb: 7ff8d000 Win32Thread: bc30fea8 READY
THREAD 8a3d4020 Cid 1584.1510 Teb: 7ff8f000 Win32Thread: bc15b8a0 READY
THREAD 8a5f5db0 Cid 1584.165c Teb: 7ff9d000 Win32Thread: bc171e8 READY
THREAD 8a297020 Cid 0f4c.0f54 Teb: 7ffde000 Win32Thread: bc20fda0 READY
THREAD 8a126020 Cid 1584.175c Teb: 7ffa9000 Win32Thread: 00000000 READY
THREAD 8a548478 Cid 0250.07b0 Teb: 7ff9a000 Win32Thread: 00000000 READY
THREAD 8a478020 Cid 0944.0988 Teb: 7ffd9000 Win32Thread: 00000000 READY
THREAD 8986ad08   Cid 1d2c.1cf0    Teb: 7ffa8000 Win32Thread: bc285800 READY
THREAD 897f4db0   Cid 1d2c.2554    Teb: 7ffbd000 Win32Thread: bc238e80 READY
THREAD 89a2e618   Cid 1d2c.1de4    Teb: 7ffdd000 Win32Thread: bc203908 READY
Processor 0: Ready Threads at priority 0
THREAD 8b184db0   Cid 0004.0008    Teb: 00000000 Win32Thread: 00000000 READY
Processor 1: Ready Threads at priority 8
THREAD 89d89db0   Cid 1b10.20ac    Teb: 7ffd7000 Win32Thread: bc16e680 READY
THREAD 891f24a8   Cid 1e2c.20d0    Teb: 7ffda000 Win32Thread: bc1b9ea8 READY
THREAD 89214db0   Cid 1e2c.24d4    Teb: 7ffd7000 Win32Thread: bc24ed48 READY
THREAD 89a28020   Cid 1b10.21b4    Teb: 7ffa7000 Win32Thread: bc253b8 READY
THREAD 891e03b0   Cid 1a98.05c4    Teb: 7ffbd000 Win32Thread: bc228bb0 READY
THREAD 891b0020   Cid 1cd0.0144    Teb: 7ffde000 Win32Thread: bc205e8 READY
Processor 8: Ready Threads at priority 7
THREAD 898367a0   Cid 0f4c.1cd4    Teb: 00000000 Win32Thread: 00000000 READY
THREAD 8a1ac020   Cid 0f4c.1450    Teb: 00000000 Win32Thread: 00000000 READY
THREAD 8aa1ab90   Cid 0f4c.11b0    Teb: 00000000 Win32Thread: 00000000 READY
THREAD 89cc9e0    Cid 0f4c.1b34    Teb: 00000000 Win32Thread: 00000000 READY
THREAD 89579020   Cid 0f4c.2220    Teb: 00000000 Win32Thread: 00000000 READY
Processor 1: Ready Threads at priority 6
THREAD 8a487db0   Cid 1584.14bc    Teb: 7ffa2000 Win32Thread: bc304ea8 READY
THREAD 8a43ce20   Cid 1584.0630    Teb: 7ff8e000 Win32Thread: bc293c20 READY
THREAD 8a1b6db0   Cid 1584.1590    Teb: 7ff8c000 Win32Thread: bc310ea8 READY
THREAD 8a1fe6e0   Cid 1584.15ec    Teb: 7ffa1000 Win32Thread: bc15bea8 READY
THREAD 8ac0adb0   Cid 1584.156c    Teb: 7ff8a000 Win32Thread: bc153be8 READY
THREAD 8b1e35a0   Cid 1584.15f4    Teb: 7ff9e000 Win32Thread: bc0567e8 READY
THREAD 8a3288e8   Cid 1584.14b8    Teb: 7ff9a000 Win32Thread: bc2fbea8 READY
THREAD 8a5055a0   Cid 1584.1518    Teb: 7ff91000 Win32Thread: bc337ea8 READY
THREAD 891afdb0   Cid 1d2c.27e8    Teb: 7ffaf000 Win32Thread: bc217c18 READY
THREAD 8a07d308   Cid 1d2c.2548    Teb: 7ffae000 Win32Thread: bc235750 READY
THREAD 8a055d18   Cid 1584.17d0    Teb: 7ffd5000 Win32Thread: 00000000 READY
THREAD 8ac0b770   Cid 0250.0268    Teb: 7ffde000 Win32Thread: bc349d8 READY
THREAD 8a0eeb40   Cid 1584.1560    Teb: 7ffdc000 Win32Thread: 00000000 READY
```

这里我们还应分析优先级为 8 的运行线程和就绪线程的堆栈跟踪（第 926 页），并检查内核时间和用户时间（飙升线程，第 888 页）。如果在它们之间发现任何共同点，还应检查优先级较低的就绪线程，以查看这种共同性是否仅存在于优先级为 8 的线程中。另请参见类似模式“繁忙系统”（第 99 页），以及由实时优先级线程导致的类似饥饿模式（第 1008 页）。

### 实时优先级

当某些线程或进程具有更高优先级并受到操作系统线程调度器的青睐，从而实际导致其他线程饥饿时，就会出现这种模式。如果优先级线程是 CPU 密集型的，我们也会看到 CPU 飙升（飙升线程模式，第 888 页）。但是，如果它们的线程优先级是正常的，它们会被其他线程抢占，而后者线程就不会饥饿。以下是一个示例：来自两个不同应用程序但同一用户会话的两个线程在两个处理器上飙升（运行在其他处理器上的线程具有高于正常和正常优先级）：

```
System Uptime: 0 days 6:40:41.143

0: kd> !running

System Processors f (affinity mask)
Idle Processors None

        Prcb      Current     Next
0   f773a120  89864c86 ............
1   f773d120  89f243d2 ............
2   f7737120  89f61398 ............
3   f773f120  897228a0 ............

0: kd> .thread /r /p 89f61398
Implicit thread is now 89f61398
Implicit process is now 88bcc2e0
Loading User Symbols

0: kd> !thread 89f61398 1f
THREAD 89f61398  Cid 16f8.2058  Teb: 7ffdf000 Win32Thread: bc41aea8 RUNNING on processor 2
Not impersonating
DeviceMap            e48a6508
Owning Process       88bcc2e0       Image:         application.exe
Wait Start TickCount 1569737       Ticks: 0
Context Switch Count 7201654        LargeStack
UserTime             01:24:06.687
KernelTime           00:14:53.828
Win32 Start Address application (0x0040a52c)
Start Address kernel32!BaseProcessStartThunk (0x77e617f8)
Stack Init ba336000 Current ba335d00 Base ba336000 Limit ba330000 Call 0
Priority 24 BasePriority 24 PriorityDecrement 0
ChildEBP RetAddr
0012e09c 762c3b7d USER32!IsWindowVisible
0012e0c4 762d61bb MSVBMV50!RbyCountVisibleDesks+0x3c
0012e0d0 004831f6 MSVBMV50!rtcDoEvents+0x7
0012e348 0046daae application+0x831f6
0012e3a0 762c5ea9 application+0x6d1ae
0012e3dc 762c583 MSVBMV50!CallProcWithArgs+0x20
0012e3f8 762d8781 MSVBMV50!InvokeVtblEvent+0x33
0012e434 762cfbc2 MSVBMV50!InvokeEvent+0x32
0012e514 762cfa4a MSVBMV50!EvtdErrFireWorker+0x175
0012e55c 762b1aa MSVBMV50!EvtdErrFire+0x18
0012e5ac 7739bffa MSVBMV50!CThreadPool::GetThreadData+0xf
0012e58c 762cd13b USER32!CallHookWithSEH+0x21
0012e5ac 7739bffa MSVBMV50!VBDefControlProc_2787+0xad
