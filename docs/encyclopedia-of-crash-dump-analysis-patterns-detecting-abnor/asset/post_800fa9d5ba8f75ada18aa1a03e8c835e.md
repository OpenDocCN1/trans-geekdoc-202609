
## Accidental Lock

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
f592f7fc 8081dcdf Driver!Kernel_dispatch+0x53
f592f810 8feb2856 nt!IofCallDriver+0x45
f592f874 8081dcdf nt!IofCallDriverQueryFullName+0x5c10
f592f888 f5e9eae3 nt!IofCallDriver+0x45
f592f8b8 f5e9eca4 DrvFilter!PassThrough+0x115
f592f8d4 8081dcdf DrvFilter!Create+0xda
f592f8e8 808f8275 nt!IofCallDriver+0x45
f592f9d0 808f8bc6 nt!IopParseDevice+0xa35
f592fa08 80936689 nt!IopParseFile+0x46
f592fa88 80932e04 nt!ObpLookupObjectName+0x11f
f592fadc 808ea331 nt!ObOpenObjectByName+0xea
f592fb58 808eeb4b nt!IopCreateFile+0x447
f592fbf4 f57c8efd nt!IoCreateFile+0xa3
f592fc24 f57c9f29 srv!SrvIoCreateFile+0x36d
f592fcf0 f57c5ae4 srv!SrvNtCreateFile+0x5cc
f592fd78 f57adbc6 srv!SrvSmbNtCreateAndX+0x15c
f592fd84 f57c3451 srv!SrvProcessSmb+0xb7
f592fdac 80948b80 srv!WorkerThread+0x138
f592fddc 8088d4e2 nt!PspSystemThreadStartup+0x2e
00000000 00000000 nt!KiThreadStartup+0x16

STACK_COMMAND: .thread 0xffffffff8aab4700 ; kb

FOLLOWUP_IP:
AVDriver+1394
f720a394 eb85      jmp     AVDriver+0x131b (f720a31b)

MODULE_NAME: AVDriver

IMAGE_NAME:  AVDriver.sys
```

### Motivated by this “discovery” we want to see all locks:

```
0: kd> !locks
**** DUMP OF ALL RESOURCE OBJECTS ****
KD: Scanning for held locks...

Resource @ 0x895a62d8    Shared 1 owning threads
   Threads: 89570520-01<*>

Resource @ 0x897ceba8    Shared 1 owning threads
   Threads: 89584020-01<*>

Resource @ 0x8958e020    Shared 1 owning threads
   Threads: 89555020-01<*>

Resource @ 0x89590608    Shared 1 owning threads
   Threads: 89666020-01<*>

Resource @ 0x89efc398    Shared 1 owning threads
   Threads: 89e277c0-01<*>

Resource @ 0x88d70820   Shared 1 owning threads
Threads: 88e43948-01<*>

Resource @ 0x89f2fb00   Shared 1 owning threads
Threads: 89674688-01<*>

Resource @ 0x89c80370   Shared 1 owning threads
Threads: 888496b8-01<*>

Resource @ 0x89bdfd08   Shared 1 owning threads
Threads: 88b62910-01<*>

Resource @ 0x888b5488   Shared 1 owning threads
Threads: 88536730-01<*>

Resource @ 0x89f2e348   Shared 1 owning threads
Threads: 89295930-01<*>

Resource @ 0x891a0838   Shared 1 owning threads
Threads: 88949020-01<*>

Resource @ 0x8825bf08   Shared 1 owning threads
Threads: 882b9a08-01<*>

Resource @ 0x881a6510   Shared 1 owning threads
Threads: 88a88338-01<*>

Resource @ 0x885c5890   Shared 1 owning threads
Threads: 881ab020-01<*>

Resource @ 0x886633a8   Shared 1 owning threads
Threads: 89b5f8b0-01<*>

Resource @ 0x88216390   Shared 1 owning threads
Threads: 88820020-01<*>

Resource @ 0x88524490   Shared 1 owning threads
Threads: 88073020-01<*>

Resource @ 0x88f6a020   Shared 1 owning threads
Threads: 88e547b0-01<*>

Resource @ 0x88cf2020   Shared 1 owning threads
Threads: 89af32d8-01<*>

Resource @ 0x889cea80   Shared 1 owning threads
Threads: 88d18b40-01<*>

Resource @ 0x88486298   Shared 1 owning threads
Threads: 88af7db0-01<*>

Resource @ 0x88b22270 Exclusively owned
Contention Count = 4
NumberOfExclusiveWaiters = 4
Threads: 8aad07d8-01<*>
Threads Waiting On Exclusive Access:
8ad78020 887abdb0 88eb39a8 8aa1f668

Resource @ 0x88748c20 Exclusively owned
Contention Count = 2
NumberOfExclusiveWaiters = 2
Threads: 8873c8d8-01<*>
Threads Waiting On Exclusive Access:
88477478 88db6020

Resource @ 0x8859a570 Exclusively owned
Contention Count = 3
NumberOfExclusiveWaiters = 3
Threads: 8aab4700-01<*>
Threads Waiting On Exclusive Access:
885d0020 88a7c020 8aafc7d8

KD: Scanning for held locks...
18911 total locks, 25 locks currently held
```

We can ignore shared locks and then concentrate on the last 3 exclusively owned resources. It looks suspicious that Contention Count has the same number as the number of threads waiting for exclusive access (NumberOfExclusiveWaiters). This means that these resources had never been used before. If we dump locks verbosely, we see that blocked threads had been waiting no more than 2 seconds, for example, for resource 0x8859a570:

```
0: kd> !thread 885d0020; !thread 88a7c020; !thread 8aafc7d8
THREAD 885d0020 Cid 0004.1c34 Teb: 00000000 Win32Thread: 00000000 WAIT: (Unknown) KernelMode Non-
Alertable
89908d50 SynchronizationEvent
885d0098 NotificationTimer
Not impersonating
DeviceMap e10022c8
Owning Process 8ad80648 Image: System
Wait Start TickCount 7689055 Ticks: 127 (0:00:00:01.984)
Context Switch Count 248
UserTime 00:00:00.000
KernelTime 00:00:00.000
Start Address srv!WorkerThread (0xf57c3394)
Stack Init b4136000 Current b4135b74 Base b4136000 Limit b4133000 Call 0
Priority 9 BasePriority 9 PriorityDecrement 0
ChildEBP RetAddr
b4135b8c 80832f7a nt!KiSwapContext+0x26
b4135b8b 8082925c nt!KiSwapThread+0x284
b4135c00 8087c1ad nt!KeWaitForSingleObject+0x346
b4135c3c 8087c3a1 nt!ExpWaitForResource+0xd5
b4135c5c f57c9e95 nt!ExAcquireResourceExclusiveLite+0x8d
b4135cf0 f57ca5e4 srv!SrvNtCreateFile+0x510
b4135d78 f57adbc6 srv!SrvSmbNtCreateAndX+0x15c
b4135d84 f57c3451 srv!SrvProcessSmb+0xb7
b4135dac 80948bd0 srv!WorkerThread+0x138
b4135dcb 888d4e2 nt!PspSystemThreadStartup+0x2e
00000000 00000000 nt!KiThreadStartup+0x16

THREAD 88a7c020 Cid 0004.3448 Teb: 00000000 Win32Thread: 00000000 WAIT: (Unknown) KernelMode Non-
Alertable
  89998d50 SynchronizationEvent
  88a7c098 NotificationTimer

Not impersonating
DeviceMap e10022c8
Owning Process 8ad80648 Image: System
Wait Start TickCount 7689112 Ticks: 70 (0:00:00:01.093)
Context Switch Count 210
UserTime 00:00:00.000
KernelTime 00:00:00.000
Start Address srv!WorkerThread (0xf57c3394)
Stack Init b55dd000 Current b55db47 Base b55dd000 Limit b55da000 Call 0
Priority 9 BasePriority 9 PriorityDecrement 0
ChildEBP RetAddr
b55dcb8 80832f7a nt!KiSwapContext+0x26
b55dcbb 8082925c nt!KiSwapThread+0x284
b55dcc0 8087c1ad nt!KeWaitForSingleObject+0x346
b55dcc3 8087c3a1 nt!ExpWaitForResource+0xd5
b55dcc5 f57ce995 nt!ExAcquireResourceExclusiveLite+0x8d
b55dccf f57c5ae4 srv!SrvNtCreateFile+0x510
b55dc78 f57adbc6 srv!SrvSmbNtCreateAndX+0x15c
b55dcc84 f57c3451 srv!SrvProcessSmb+0xb7
b55dcac 80948bd0 srv!WorkerThread+0x138
b55ddcc 8088d4e2 nt!PspSystemThreadStartup+0x2e
00000000 00000000 nt!KiThreadStartup+0x16

THREAD 8aafc7d8 Cid 0004.058c Teb: 00000000 Win32Thread: 00000000 WAIT: (Unknown) KernelMode Non-
Alertable
  89998d50 SynchronizationEvent
  8aafc850 NotificationTimer

Not impersonating
DeviceMap e10022c8
Owning Process 8ad80648 Image: System
Wait Start TickCount 7689171 Ticks: 11 (0:00:00:00.171)
Context Switch Count 310
UserTime 00:00:00.000
KernelTime 00:00:00.000
Start Address srv!WorkerThread (0xf57c3394)
Stack Init f592c000 Current f592bb18 Base f592c000 Limit f5929000 Call 0
Priority 9 BasePriority 9 PriorityDecrement 0
ChildEBP RetAddr
f592bb30 80832f7a nt!KiSwapContext+0x26
f592bb5c 8082925c nt!KiSwapThread+0x284
f592bba4 8087c1ad nt!KeWaitForSingleObject+0x346
f592bbe0 8087c3a1 nt!ExpWaitForResource+0xd5
f592bc0 f57c8267 nt!ExAcquireResourceExclusiveLite+0x8d
f592bc18 f57ff0ed srv!UnlinkRfcbFromLfcb+0x33
f592bc34 f57f2eea srv!SrvCompleteRfcbClose+0x1df
f592bc54 f57b5e8f srv!CloseRfcbInternal+0xb6
f592bc78 f57ce8a9 srv!SrvCloseRfcbsOnSessionORPid+0x74
```
