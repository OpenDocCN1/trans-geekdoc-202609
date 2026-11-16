
## Windows

If we have a process dump with many threads, it is sometimes difficult to see which thread there was spiking CPU.
This is why it is always good to have some screenshots or notes from QSlice or Process Explorer showing spiking
thread ID and process ID. The latter ID is to make sure that the process dump was from the correct process. New
process dumpers and tools from Microsoft (userdump.exe, procdump) save thread time information so we can
open the dump and see the time spent in kernel and user mode for any thread by entering !runaway command.
However, if that command shows many threads with similar CPU consumption, it will not highlight the particular
thread that was spiking at the time the crash dump was saved, so screenshots are still useful in some cases.

What to do if we don't have the spiking thread ID? We need to look at all threads and find those that are
not waiting. Almost all threads are waiting most of the time. So the chances to dump the normal process and see
some active threads are very low. If the thread is waiting, the top function on its stack is usually:

```
ntdll!KiFastSystemCallRet
```

and below that we can see some blocking calls waiting on some synchronization object, Sleep API call, IO
completion or for LPC reply:

```
0:085> ~*kv
...
...
...
64 Id: 1b0.120c Suspend: -1 Teb: 7ff69000 Unfrozen
ChildEBP RetAddr  Args to Child
02defe18 7c90e399 ntdll!KiFastSystemCallRet
02defe1c 77e76703 ntdll!NtReplyWaitReceivePortEx+0xc
02defff0 77e76c22 rpcrt4!LRPC_ADDRESS::ReceiveLotsaCalls+0xf4
02defff8 77e76a3b rpcrt4!RecvLotsaCallsWrapper+0x8
02defff8 77e76c0a rpcrt4!BaseCachedThreadRoutine+0x79
02defff4 7c80b683 rpcrt4!ThreadStartRoutine+0x1a
02defff0 00000000 kernel32!BaseThreadStart+0x37

65 Id: 1b0.740 Suspend: -1 Teb: 7ff67000 Unfrozen
ChildEBP RetAddr  Args to Child
02defff4 7c90d5c ntdll!KiFastSystemCallRet
02defff48 7c8023ed ntdll!NtDelayExecution+0xc
02deffa0 57cde2dd kernel32!SleepEx+0x61
02defff4 7c80b683 component!foo+0x35
02defff0 00000000 kernel32!BaseThreadStart+0x37

66 Id: 1b0.131c Suspend: -1 Teb: 7ff66000 Unfrozen
ChildEBP RetAddr  Args to Child
02f4ff38 7c90e90c ntdll!KiFastSystemCallRet
02f4ff3c 7c8025cb ntdll!ZwWaitForSingleObject+0xc
02f4ffa0 72001f65 kernel32!WaitForSingleObjectEx+0xa8
02f4ffb4 7c80b683 component!WorkerThread+0x15
02f4ffec 00000000 kernel32!BaseThreadStart+0x37

67 Id: 1b0.1320 Suspend: -1 Teb: 7ff65000 Unfrozen
ChildEBP RetAddr  Args to Child
02f8fe1c 7c90e9ab ntdll!KiFastSystemCallRet
02f8fe20 7c8094e2 ntdll!ZwWaitForMultipleObjects+0xc
02f8febc 7e4195f9 kernel32!WaitForMultipleObjectsEx+0x12c
02f8ff18 7e4196a8 user32!RealMsgWaitForMultipleObjectsEx+0x13e
02f8ff34 720019f6 user32!MsgWaitForMultipleObjects+0x1f
02f8ffa0 72001a29 component!bar+0xd9
02f8ffb4 7c80b683 component!MonitorWorkerThread+0x11
02f8ffec 00000000 kernel32!BaseThreadStart+0x37

68 Id: 1b0.1340 Suspend: -1 Teb: 7ff63000 Unfrozen
ChildEBP RetAddr  Args to Child
0301ff1c 7c90e31b ntdll!KiFastSystemCallRet
0301ff20 7c80a746 ntdll!ZwRemoveIoCompletion+0xc
0301ff4c 57d46e65 kernel32!GetQueuedCompletionStatus+0x29
0301ffb4 7c80b683 component!AsyncEventsThread+0x91
0301ffec 00000000 kernel32!BaseThreadStart+0x37
...
...
...

85 Id: 1b0.17b4 Suspend: -1 Teb: 7ffd4000 Unfrozen
ChildEBP RetAddr  Args to Child
00daffc8 7c9507a8 ntdll!DbgBreakPoint
00dafff0 00000000 ntdll!DbgUiRemoteBreakin+0x2d
```

Therefore, if we have a different thread like this one below the chances that it was spiking are bigger:

```
58 Id: 1b0.9f4 Suspend: -1 Teb: 7ff75000 Unfrozen
ChildEBP RetAddr  Args to Child
0280f64c 500af723 componentB!DoSomething+32
0280f85c 500b5391 componentB!CheckSomething+231
0280f884 500b7a3f componentB!ProcessWorkItem+9f
0301ffec 00000000 kernel32!BaseThreadStart+0x37
```

There is no KiFastSystemCallRet on top, and if we look at the currently executing instruction we see that it does some copy operation:

```
0:085> ~58r
eax=00000000 ebx=0280fdd4 ecx=0000005f edx=00000000 esi=03d30444 edi=0280f6dc
eip=500a4024 esp=0280f644 ebp=0280f64c iopl=0 nv up ei pl nz na po nc
cs=001b ss=0023 ds=0023 es=0023 fs=003b gs=0000 efl=00010202
component!DoSomething+32:
500a4024 f3a5 rep movs dword ptr es:[edi],dword ptr [esi] es:0023:0280f6dc=00004009
ds:0023:03d30444=00004009
```

In a kernel or a complete memory dump we can see CPU spikes by checking KernelTime and UserTime:

```
0: kd> !thread 88b66768
THREAD 88b66768 Cid 01fc.1550 Teb: 7ffad000 Win32Thread: bc18f240 RUNNING on processor 1
IRP List:
89716008: (0006,0094) Flags: 00000a00 Mdl: 00000000
Impersonation token: e423a030 (Level Impersonation)
DeviceMap e3712480
Owning Process 8a0a56a0 Image: SomeSvc.exe
Wait Start TickCount 1782229 Ticks: 0
Context Switch Count 877610 LargeStack
UserTime 00:00:01.0078
KernelTime 02:23:21.0718
```

By default !runaway command shows only user mode time. By specifying additional flags, it is possible to see both kernel and user times:

```
0:000> !runaway 3
User Mode Time
Thread Time
8:15a4 0 days 0:12:32.812
0:1c00 0 days 0:00:00.312
9:1b50 0 days 0:00:00.296
22:2698 0 days 0:00:00.046
17:22b8 0 days 0:00:00.031
14:2034 0 days 0:00:00.031
21:21b4 0 days 0:00:00.000
20:27b0 0 days 0:00:00.000
19:278c 0 days 0:00:00.000
18:2788 0 days 0:00:00.000
16:2194 0 days 0:00:00.000
15:2064 0 days 0:00:00.000
13:2014 0 days 0:00:00.000
12:1e38 0 days 0:00:00.000
11:1c54 0 days 0:00:00.000
10:1d40 0 days 0:00:00.000
7:1994 0 days 0:00:00.000
6:1740 0 days 0:00:00.000
5:1c18 0 days 0:00:00.000
4:c10 0 days 0:00:00.000
3:1774 0 days 0:00:00.000
2:1a08 0 days 0:00:00.000
1:fb8 0 days 0:00:00.000

Kernel Mode Time
Thread Time
9:1b50 0 days 1:21:54.125
8:15a4 0 days 0:02:48.390
0:1c00 0 days 0:00:00.328
14:2034 0 days 0:00:00.234
22:2698 0 days 0:00:00.156
17:22b0 0 days 0:00:00.015
21:21b4 0 days 0:00:00.000
20:27b0 0 days 0:00:00.000
19:278c 0 days 0:00:00.000
18:2788 0 days 0:00:00.000
16:2194 0 days 0:00:00.000
15:2064 0 days 0:00:00.000
13:2014 0 days 0:00:00.000
12:1e38 0 days 0:00:00.000
11:1c54 0 days 0:00:00.000
10:1d40 0 days 0:00:00.000
7:1994 0 days 0:00:00.000
6:1740 0 days 0:00:00.000
5:1c18 0 days 0:00:00.000
4:c10 0 days 0:00:00.000
3:1774 0 days 0:00:00.000
2:1a08 0 days 0:00:00.000
1:fb8 0 days 0:00:00.000
```

We see that the thread 15a4 spikes mostly in user mode but the thread 1b50 spikes mostly in kernel mode.

In the kernel and complete memory dumps we can scan all threads with Ticks: 0 or Elapsed Ticks: 0 to check their kernel and user times:

```
PROCESS 8782cd60 SessionId: 52 Cid: 4a58 Peb: 7ffdf000 ParentCid: 1ea4
DirBase: 0a260c00 ObjectTable: 88ab33a8 TableSize: 486.
Image: IEXPLORE.EXE
VadRoot 87f59ea8 Clone 0 Private 2077. Modified 123. Locked 0.
DeviceMap 880f6828
Token e8217cd0
ElapsedTime 0:03:09.0765
UserTime 0:00:00.0890
KernelTime 0:00:10.0171
QuotaPoolUsage[PagedPool] 100320
QuotaPoolUsage[NonPagedPool] 58100
Working Set Sizes (now,min,max) (4944, 50, 345) (19776KB, 200KB, 1380KB)
PeakWorkingSetSize 4974
VirtualSize 83 Mb
PeakVirtualSize 83 Mb
PageFaultCount 8544
MemoryPriority FOREGROUND
BasePriority 8
CommitCharge 2262

THREAD 87836580 Cid 4a58.57cc Teb: 7ffde000 Win32Thread: a224f1d8 WAIT: (Executive) KernelMode Non-Alertable
89dee788 Semaphore Limit 0x7fffffff
87836668 NotificationTimer
Not impersonating
Owning Process 8782cd60
Wait Start TickCount 123758 Elapsed Ticks: 0
Context Switch Count 97636 LargeStack
UserTime 0:00:00.0593
KernelTime 0:00:08.0359
Start Address 0x7c57b78c
Win32 Start Address 0x00401ee6
Stack Init ac154770 Current ac154320 Base ac155000 Limit ac14d000 Call ac15477c
Priority 11 BasePriority 8 PriorityDecrement 0 DecrementCount 0

ChildEBP RetAddr  Args to Child
ac154338 8042d8d7 00000000 8047bd00 00000001 nt!KiSwapThread+0x1b1
ac154360 80415d61 89dee788 00000000 00000000 nt!KeWaitForSingleObject+0x1a3
ac15439c 8041547c 00000000 00000001 8051c501 nt!ExpWaitForResource+0x2d
ac1543b4 8046997a 8047bd00 00000001 805225e9 nt!ExAcquireResourceSharedLite+0xc6
ac1543c0 805225e9 00000000 00000001 8051c501 nt!CmpLockRegistry+0x18
ac154430 8051c718 e7C5fd08 ac15448c 00000001 nt!CmSetValueKey+0x31
ac1544b4 8046b2a9 00000798 00125c04 00000000 nt!NtSetValueKey+0x196
ac1544b4 77f88de7 00000798 00125c04 00000000 nt!KiSystemService+0xc9
00125bb0 00000000 00000000 00000000 00000000 +0x77f88de7
```

For complete and kernel dumps we can also pay attention to the output of !running command and to
the output of !stacks command (Ticks and ThreadState columns).
