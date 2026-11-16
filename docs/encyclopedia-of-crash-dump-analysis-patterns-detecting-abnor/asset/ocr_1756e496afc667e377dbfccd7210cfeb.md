```
0013f8a4 7e450617 USER32!MessageBoxTimeoutA+0x9c
0013f8c4 7e4505cf USER32!MessageBoxExA+0x1b
0013f8e0 088098a9 USER32!MessageBoxA+0x45
...
...
...
0: kd> .process /r /p 888ffb60
Implicit process is now 888ffb60
Loading User Symbols
0: kd> !thread 88b14da8
...
...
...
ChildEBP RetAddr Args to Child
...
...
...
0013f8e0 088098a9 00000000 0013f944 088708f0 USER32!MessageBoxA+0x45
...
...
...
0: kd> dA 0013f944
0013f944 "Cannot contact database, Retry"
```

This immediately raised suspicion and looking at other threads in the same application revealed that many of them were trying to open a network connection, for example:

```
THREAD 87a70da8 Cid 0a04.0cc0 Teb: 7ff83000 Win32Thread: 00000000 WAIT: (UserRequest) UserMode Non-Alertable
87d690b0 NotificationEvent
87a70e98 NotificationTimer
IRP List:
87af7bc8: (0006,0244) Flags: 00000000 Mdl: 00000000
Not impersonating
DeviceMap e14bec28
Owning Process 888ffb60 Image: OUTLOOK.EXE
Wait Start TickCount 1267130 Ticks: 8515 (0:00:02:13.046)
Context Switch Count 18
UserTime 00:00:00.000
KernelTime 00:00:00.000
Win32 Start Address msmapi32!OpenThreadImpersonationToken (0x35f76963)
Start Address kernel32!BaseThreadStartThunk (0x7c810659)
Stack Init 9fbc5000 Current 9fbc4ca0 Base 9fbc5000 Limit 9fbc2000 Call 0
Priority 8 BasePriority 8 PriorityDecrement 0 DecrementCount 16
Kernel stack not resident.
ChildEBP RetAddr
9fbc4cb8 804e1bd2 nt!KiSwapContext+0x2f
9fbc4cc4 804e1c1e nt!KiSwapThread+0x8a
9fbc4ce8 8056d2f9 nt!KeWaitForSingleObject+0x1c2
9fbc4d50 804dd99f nt!NtWaitForSingleObject+0x9a
9fbc4d50 7c90eb94 nt!KiFastCallEntry+0xfc
1bd8f52c 7c90e9c0 ntdll!KiFastSystemCallRet
1bd8f530 7c8025cb ntdll!ZwWaitForSingleObject+0xc
```