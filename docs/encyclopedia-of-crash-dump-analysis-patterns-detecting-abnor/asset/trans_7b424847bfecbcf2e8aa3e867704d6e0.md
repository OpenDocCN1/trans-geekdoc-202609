
特殊堆栈跟踪模式（第 882 页）是关于不存在于正常崩溃转储中的堆栈跟踪。特殊进程是类似模式，指不在正常操作期间运行或高度特定领域的进程，它们是特定软件环境的标志，例如，在 VMWare 或 VirtualPC 188 中运行的操作系统。这里我们将看到一个示例：识别特定进程如何有助于在完整内存转储中成功定位问题。

检查运行中的进程显示 Dr. Watson 的存在：

```
5: kd> !process 0 0
**** NT ACTIVE PROCESS DUMP ****
PROCESS 89d9b648 SessionId: none Cid: 0004 Peb: 00000000 ParentCid: 0000
DirBase: 54d5d020 ObjectTable: e1000e20 HandleCount: 1711.
Image: System

PROCESS 8979b758 SessionId: none Cid: 01b0 Peb: 7ffdd000 ParentCid: 0004
DirBase: 54d5d040 ObjectTable: e181d8b0 HandleCount: 29.
Image: smss.exe

PROCESS 89793cf0 SessionId: 0 Cid: 01e0 Peb: 7ffde000 ParentCid: 01b0
DirBase: 54d5d060 ObjectTable: e13eea10 HandleCount: 1090.
Image: csrss.exe
...
...
...
PROCESS 8797a600 SessionId: 1 Cid: 17d0 Peb: 7ffdc000 ParentCid: 1720
DirBase: 54d5d8c0 ObjectTable: e2870af8 HandleCount: 243.
Image: explorer.exe

PROCESS 87966d88 SessionId: 2 Cid: 0df0 Peb: 7ffd4000 ParentCid: 01b0
DirBase: 54d5d860 ObjectTable: e284cd48 HandleCount: 53.
Image: csrss.exe

PROCESS 879767c8 SessionId: 0 Cid: 0578 Peb: 7ffde000 ParentCid: 0ca8
DirBase: 54d5d8a0 ObjectTable: e2c05268 HandleCount: 180.
Image: drwtsn32.exe
```

检查堆栈跟踪显示 drwtsn32.exe 正在等待调试器事件，因此必定存在调试目标（被调试程序）：

```
5: kd> .process /r /p 879767c8
Implicit process is now 879767c8
Loading User Symbols
```

```
5: kd> !process 879767c8
PROCESS 879767c8 SessionId: 0 Cid: 0578 Peb: 7ffde000 ParentCid: 0ca8
    DirBase: 54d58da0 ObjectTable: e2c05268 HandleCount: 180.
    Image: drwtsn32.exe
VadRoot 88a33cd0 Vads 59 Clone 0 Private 1737. Modified 10792. Locked 0.
DeviceMap e10028e8
    Token                             e2e2330
    ElapsedTime                       00:01:12.703
    UserTime                          00:00:00.203
    KernelTime                        00:00:00.031
    QuotaPoolUsage[PagedPool]         52092
    QuotaPoolUsage[NonPagedPool]      2360
    Working Set Sizes (now,min,max)   (2488, 50, 345) (9952KB, 200KB, 1380KB)
    PeakWorkingSetSize                2534
    VirtualSize                       34 Mb
    PeakVirtualSize                   38 Mb
    PageFaultCount                    13685
    MemoryPriority                    BACKGROUND
    BasePriority                      6
    CommitCharge                      1927

THREAD 87976250 Cid 0578.04bc Teb: 7ffdd000 Win32Thread: bc14a008 WAIT: (Unknown) UserMode Non-
Alertable
87976558 Thread
Not impersonating
DeviceMap      e10028e8
Owning Process   879767c8       Image:         drwtsn32.exe
Wait Start TickCount      13460       Ticks: 4651 (0:00:01:12.671)
Context Switch Count      15          LargeStack
UserTime               00:00:00.000
KernelTime             00:00:00.000
Win32 Start Address drwtsn32!mainCRTStartup (0x01007c1d)
Start Address kernel32!BaseProcessStartThunk (0x7c8217f8)
Stack Init f433b000 Current f433ac60 Base f433b000 Limit f4337000 Call 0
Priority 6 BasePriority 6 Decrement 0
ChildEBP RetAddr
f433ac78 80833465 nt!KiSwapContext+0x26
f433aca4 80829a62 nt!KiSwapThread+0x2e5
f433acec 80938dc0 nt!KeWaitForSingleObject+0x346
f433ad50 8088978c nt!NtWaitForSingleObject+0x9a
f433ad50 7c9485ec nt!KiFastCallEntry+0xfc
0007fe98 7c821c8d ntdll!KiFastSystemCallRet
0007feac 01005557 kernel32!WaitForSingleObject+0x12
0007ff0c 01007ff8 drwtsn32!NotifyWinMain+0x1ba
0007fff4 01007d4c drwtsn32!main+0x31
0007fffc 7c82f23b drwtsn32!mainCRTStartup+0x12f
0007fff0 00000000 kernel32!BaseProcessStart+0x23
THREAD 87976558 Cid 0578.0454 Teb: 7ffdc000 Win32Thread: 00000000 WAIT: (Unknown) UserMode Non-
Alertable
	89de2e50 NotificationEvent
	879765d0 NotificationTimer
Not impersonating
DeviceMap                 e10028e8
Owning Process            879767c8       Image:         drwtsn32.exe
Wait Start TickCount      18102          Ticks: 9 (0:00:00:00.140)
Context Switch Count      1163
UserTime                  00:00:00.203
KernelTime                00:00:00.031
Win32 Start Address drwtsn32!DispatchDebugEventThread (0x01003d6d)
Start Address kernel32!BaseThreadStartThunk (0x7c8217ec)
Stack Init f4e26000 Current f4e25be8 Base f4e26000 Limit f4e23000 Call 0
Priority 6 BasePriority 6 PriorityDecrement 0
ChildEBP RetAddr
f4e25c00 80833465 nt!KiSwapContext+0x26
f4e25c2c 80829a62 nt!KiSwapThread+0x2e5
f4e25c74 809a06ab nt!KeWaitForSingleObject+0x346
f4e25d4c 80889798 nt!NtWaitForDebugEvent+0xd5
f4e25d4c 7c9485ec nt!KiFastCallEntry+0xfc
0095ed20 60846f8f ntdll!KiFastSystemCallRet
0095ee6c 60816ecf dbgeng!LiveUserTargetInfo::WaitForEvent+0x1fa
0095ee88 60817d03 dbgeng!WaitForAnyTarget+0x45
0095eecc 60817270 dbgeng!RawWaitForEvent+0x15f
0095fee4 01003f8d dbgeng!DebugClient::WaitForEvent+0x80
0095ffb8 7c824829 drwtsn32!DispatchDebugEventThread+0x220
0095ffec 00000000 kernel32!BaseThreadStart+0x34
```

了解到调试器会挂起被调试程序中的线程（挂起线程模式，第 964 页），我们确实看到了问题进程：

```
5: kd> !process 0 2
**** NT ACTIVE PROCESS DUMP ****
...
...
...
PROCESS 898285b0 SessionId: 0 Cid: 0ca8 Peb: 7ffda000 ParentCid: 022c
	DirBase: 54d5d500 ObjectTable: e2776880 HandleCount:  2.
	Image: svchost.exe
THREAD 888b8668 Cid 0ca8.1448 Teb: 00000000 Win32Thread: 00000000 WAIT: (Unknown) KernelMode Non-
Alertable
SuspendCount 2
	888b87f8 Semaphore Limit 0x2
```

转储其线程堆栈仅显示一个系统线程，而我们通常期望来自用户空间的大量线程。还存在调试端口：

```
5: kd> .process /r /p 898285b0
Implicit process is now 898285b0
Loading User Symbols
```

```
5: kd> !process 898285b0
PROCESS 898285b0 SessionId: 0 Cid: 0ca8 Peb: 7ffda000 ParentCid: 022c

DirBase: 54d5d000 ObjectTable: e2776880 HandleCount: 2.
Image: svchost.exe
VadRoot 88953220 Vads 209 Clone 0 Private 901. Modified 3. Locked 0.
DeviceMap e10028e8
Token e27395b8
ElapsedTime 00:03:25.640
UserTime 00:00:00.0156
KernelTime 00:00:00.234
QuotaPoolUsage[PagedPool] 82988
QuotaPoolUsage[NonPagedPool] 8824
Working Set Sizes (now,min,max) (2745, 50, 345) (10980KB, 200KB, 1380KB)
PeakWorkingSetSize 2819
VirtualSize 82 Mb
PeakVirtualSize 83 Mb
PageFaultCount 4519
MemoryPriority BACKGROUND
BasePriority 6
CommitCharge 1380
DebugPort 89de2e50

THREAD 888B8668 Cid 0ca8.1448 Teb: 00000000 Win32Thread: 00000000 WAIT: (Unknown) KernelMode Non-
Alertable
SuspendCount 2
888B87F8 Semaphore Limit 0x2
Not impersonating
DeviceMap e10028e8
Owning Process 898285b0 Image: svchost.exe
Wait Start TickCount 13456 Ticks: 4655 (0:00:01:12.734)
Context Switch Count 408
UserTime 00:00:00.000
KernelTime 00:00:00.000

Start Address driverA! (0xf6fb8218)
Stack Init f455b000 Current f455a3ac Base f455b000 Limit f4558000 Call 0
Priority 6 BasePriority 6 PriorityDecrement 0
ChildEBP RetAddr
f455a4c4 80833465 nt!KiSwapContext+0x26
f455a3f0 80829a62 nt!KiSwapThread+0x2e5
f455a438 80833178 nt!KeWaitForSingleObject+0x346
f455a450 8082e01f nt!KiSuspendThread+0x18
f455a498 80833480 nt!KiDeliverApc+0x117
f455a4d0 80829a62 nt!KiSwapThread+0x300
f455a518 f6fb7f13 nt!KeWaitForSingleObject+0x346
f455a548 f4edd457 driverA!WaitForSingleObject+0x75
f455a55c f4edcdd8 driverB!DeviceWaitForRead+0x19
f455ad90 f6fb8265 driverB!InputThread+0x17e
f455adac 80949b7c driverA!DriverThread+0x4d
f455adcc 8088e062 nt!PspSystemThreadStartup+0x2e
00000000 00000000 nt!KiThreadStartup+0x16
```

最可能的情景是 *svchost.exe* 遇到了未处理的异常，触发了启动事后调试器 189，例如 Dr. Watson。

此模式的其他类似示例可能包括 Vista 上存在 *WerFault.exe*，以及 NTSD 和其他 JIT 调试器在运行。

## 注释

某些进程会短暂出现以执行专门任务，并且通常不存在于内存中。它们在内存转储中的存在可以指向异常情况，例如 **等待链**（第 1082 页）、**阻塞线程**（第 80 页）等许多其他情况。例如，在 W2K8 终端会话环境中存在多个 *LogonUI* 进程。

另一个错误报告示例是存在 *DW20.exe*。
