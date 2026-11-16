

However, dumping raw stack data around corresponding frames gives us pipe name clue and possible service name to look further:

```
0: kd> dpnu 00000000`11f4da70
00000000`11f4da70  00000000`11f4dba8  "\\.\PIPE\ServiceArpc"
00000000`11f4da78  00000000`00000000
00000000`11f4da80  00000000`00000000
00000000`11f4da88  00000000`000003e8
00000000`11f4da90  00000000`11f4db30
00000000`11f4da98  00000000`00110018
00000000`11f4daa0  00000000`0d9001a0
00000000`11f4daa8  00000000`0000001a
00000000`11f4dab0  00000000`00000000
00000000`11f4dab8  00000000`00000000
00000000`11f4dac0  00000000`0020000c
00000000`11f4dac8  00000000`0d9001e2  "ServiceArpc"
00000000`11f4dad0  00000000`00000000
00000000`11f4dad8  00000000`00000000
00000000`11f4dae0  00000000`00240022
```

## Hidden Process

Not all processes are linked into a list that some commands traverse such as !process 0 0. A process may unlink itself or be in an initialization stage. However, a process structure is allocated from the nonpaged pool, and such pool can be searched for "Proc" pool tag (unless a process changes that in memory). For example:

```
0: kd> !poolfind Proc

Searching NonPaged pool (83c3c000 : 8bc00000) for Tag: Proc

*87b15000 size: 298 previous size: 0 (Free) Proc
*87b18370 size: 298 previous size: 98 (Allocated) Proc (Protected)
[...]
*8a35e900 size: 298 previous size: 30 (Allocated) Proc (Protected)
*8a484000 size: 298 previous size: 0 (Allocated) Proc (Protected)
*8a4a2d68 size: 298 previous size: 28 (Allocated) Proc (Protected)
[...]
```

One such structure is missing from the active process linked list (note that it has a parent PID):

```
0: kd> !process 8a484000+20
PROCESS 8a484020 SessionId: 0 Cid: 05a0 Peb: 00000000 ParentCid: 0244
DirBase: bffc2200 ObjectTable: e17e6a78 HandleCount: 0
Image: AppChild.exe
VadRoot 8a574f80 Vads 4 Clone 0 Private 3 Modified 0 Locked 0
DeviceMap e1002898
Token e1a36030
ElapsedTime 00:00:00.000
UserTime 00:00:00.000
KernelTime 419 Days 13:24:16.625
QuotaPoolUsage[PagedPool] 7580
QuotaPoolUsage[NonPagedPool] 160
Working Set Sizes (now,min,max) (12, 50, 345) (48KB, 200KB, 1380KB)
PeakWorkingSetSize 12
VirtualSize 1 Mb
PeakVirtualSize 1 Mb
PageFaultCount 5
MemoryPriority BACKGROUND
BasePriority 8
CommitCharge 156

No active threads
```

We may think that this process is a zombie (note that unlike terminated processes it has a non-zero data such as VAD and object table and zero PEB and elapsed time) but inspection of its parent process thread stacks reveals that it was in the process of creation (note an attached process field):

```
THREAD 8a35dad8 Cid 0244.0248 Teb: 7ffdd000 Win32Thread: bc3aa688 WAIT: (Unknown) KernelMode Non-Alertable
ba971608 NotificationEvent
Impersonation token: e2285030 (Level Impersonation)
DeviceMap e1a31a58
Owning Process 8a35e920 Image: AppParent.exe
Attached Process 8a484020 Image: AppChild.exe
Wait Start TickCount 2099 Ticks: 1 (0:00:00:00.015)
Context Switch Count 279 LargeStack
UserTime 00:00:00.046
KernelTime 00:00:00.046
Win32 Start Address AppParent!mainCRTStartup (0x0100d303)
Start Address kernel32!BaseProcessStartThunk (0x77e617f8)
Stack Init ba972000 Current ba971364 Base ba972000 Limit ba96e000 Call 0
Priority 8 BasePriority 8 PriorityDecrement 0
ChildEBP RetAddr
ba97137c 80833f2d nt!KiSwapContext+0x26
ba9713a8 80829c72 nt!KiSwapThread+0x2e5
ba9713f0 bad3c9db nt!KeWaitForSingleObject+0x346
[...]
ba971b94 8094cfc3 nt!MmCreatePeb+0x2cc
ba971ce4 8094d42d nt!PspCreateProcess+0x5a9
ba971d38 8088b4ac nt!NtCreateProcessEx+0xf77
ba971d38 7c82845c nt!KiFastCallEntry+0x0fc (TrapFrame @ ba971d64)
0006f498 7c826d09 ntdll!KiFastSystemCallRet
0006f49c 77e6cf95 ntdll!ZwCreateProcessEx+0xc
0006fc00 7d1ec670 kernel32!CreateProcessInternalW+0x15e5
0006fd0c 01008bcf ADVAPI32!CreateProcessAsUserW+0x108
[...]
```

## Hidden Stack Trace

Sometimes, a stack trace from **Stack Trace Collection** (page 943) may look well-formed at first sight, for example, having an expected start frames:

```
0:000> ~*k

[...]
# 19 Id: 16a4.21f4 Suspend: 0 Teb: 7e95b000 Unfrozen
ChildEBP RetAddr
0c2de6b0 74eb112f ntdll!NtWaitForMultipleObjects+0xc
0c2de83c 76ca7b89 KERNELBASE!WaitForMultipleObjectsEx+0xcc
0c2de858 76d0b7bf kernel32!WaitForMultipleObjects+0x19
0c2dec98 76d00295 kernel32!WerpReportFaultInternal+0x50b
0c2deca8 76ce1709 kernel32!WerpReportFault+0x74
0c2decb4 74f5f705 kernel32!BasepReportFault+0x19
0c2ded3c 76fb4f84 KERNELBASE!UnhandledExceptionFilter+0x1f4
0c2ded54 76fb5728 ntdll!TppExceptionFilter+0x30
0c2ded64 76fc595a ntdll!TppWorkerpInnerExceptionFilter+0xe
0c2df914 76fc7c04 ntdll!TppWorkerThread+0x87f5a
0c2df928 76f1ad1f kernel32!BaseThreadInitThunk+0x24
0c2df970 76f1acea ntdll!_RtlUserThreadStart+0x2f
0c2df980 00000000 ntdll!_RtlUserThreadStart+0x1b
[...]
```

So, we may think something wrong happened in `ntdll!TppWorkerThread` code (although 0x87f5a offset looks suspicious). However, in reality, in this case, due to exception filter logic (or some other reason in different cases), we have **Hidden Stack Trace**. When looking at `UnhandledExceptionFilter` parameters (or raw stack as in the case of **Hidden Exceptions**, page 455), we find an exception context:

```
0:019> kv
ChildEBP RetAddr Args to Child
0c2de6b0 74eb112f 00000003 0c2de880 00000001 ntdll!NtWaitForMultipleObjects+0xc
0c2de83c 76ca7b89 00000003 0c2de880 00000000 KERNELBASE!WaitForMultipleObjectsEx+0xcc
0c2de858 76d0b7bf 00000003 0c2de880 00000000 kernel32!WaitForMultipleObjects+0x19
0c2dec98 76d00295 00000000 00000001 00000000 kernel32!WerpReportFaultInternal+0x50b
0c2deca8 76ce1709 0c2ded3c 74f5f705 0c2ded94 kernel32!WerpReportFault+0x74
0c2decb4 74f5f705 0c2ded94 00000001 a79b7895 kernel32!BasepReportFault+0x19
0c2ded3c 76fb4f84 0c2ded94 0c2ded94 00000000 KERNELBASE!UnhandledExceptionFilter+0x1f4
0c2ded54 76fb5728 00000000 00000000 0c2df914 ntdll!TppExceptionFilter+0x30
0c2ded64 76fc595a 0c2df8d0 76f0a070 0c2df914 ntdll!TppWorkerpInnerExceptionFilter+0xe
0c2df914 76fc7c04 0f79e380 76ca7be0 0ab54024 ntdll!TppWorkerThread+0x87f5a
0c2df928 76f1ad1f 0f79e380 a59141d7 00000000 kernel32!BaseThreadInitThunk+0x24
0c2df970 76f1acea ffffffff 76f00233 00000000 ntdll!_RtlUserThreadStart+0x2f
0c2df980 00000000 76e4a00 0f79e380 00000000 ntdll!_RtlUserThreadStart+0x1b
0:019> dd 0c2ded94 L2
0c2ded94 0c2deef8 0c2def48
```

```
0:019> .cxr 0c2def48
eax=15f237e5 ebx=15f235e9 ecx=15f237e1 edx=7e95b000 esi=15f237e1 edi=09724b10
eip=76f00fb2 esp=0c2df3ac ebp=0c2df3ac iopl=0 nv up ei pl nz na po nc
cs=0023 ss=002b ds=002b es=002b fs=0053 gs=002b efl=00010202
ntdll!RtlEnterCriticalSection+0x12:
76f00fb2 f00fba3000 lock btr dword ptr [eax],0 ds:002b:15f237e5=????????
```

```
0:019> k
*** Stack trace for last set context - .thread/.cxr resets it
ChildEBP RetAddr
0c2df3ac 7407999c ntdll!RtlEnterCriticalSection+0x12
0c2df3cc 7407acd6 ModuleA!DoWork+0x1b
[...]
0c2df73c 76ee3aa7 ModuleA!ThreadPoolWorkCallback+0xa9
0c2df77c 76ee1291 ntdll!TppWorkpExecuteCallback+0x137
0c2df914 76ca7c04 ntdll!TppWorkerThread+0x48e
0c2df928 76f1ad1f kernel32!BaseThreadInitThunk+0x24
0c2df970 76f1acea ntdll!__RtlUserThreadStart+0x2f
0c2df980 00000000 ntdll!_RtlUserThreadStart+0x1b
```

We consider this a different pattern than Hidden Call (page 450) because an entire stack (sub)trace is missing between UnhandledExceptionFilter and thread start frames:

```
ntdll!NtWaitForMultipleObjects
KERNELBASE!WaitForMultipleObjectsEx
kernel32!WaitForMultipleObjects
kernel32!WerpReportFaultInternal
kernel32!WerpReportFault
kernel32!BasepReportFault
KERNELBASE!UnhandledExceptionFilter
[...]
ntdll!TppWorkerThread
kernel32!BaseThreadInitThunk
ntdll!__RtlUserThreadStart
ntdll!_RtlUserThreadStart
```

This pattern is also different from Past Stack Trace (page 800) pattern because Hidden Stack Trace belongs to PRESENT time zone. Our example is also different from Hidden Exception (page 455) analysis pattern and its recovered stack trace because exception processing is not hidden and shows Exception Stack Trace (page 363) albeit with a hidden part.

We were also fortunate to have Stored Exception (page 959, accessible by !analyze -v command):

```
0:019> .exr -1
ExceptionAddress: 76f00fb2 (ntdll!RtlEnterCriticalSection+0x00000012)
ExceptionCode: c0000005 (Access violation)
ExceptionFlags: 00000000
NumberParameters: 2
Parameter[0]: 00000001
Parameter[1]: 15f237e5
Attempt to write to address 15f237e5
```

