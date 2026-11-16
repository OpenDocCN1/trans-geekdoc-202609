# Random Object

Sometimes we observe rare events when abnormal conditions that usually result in a system crash result in a milder problem, for example, a service is unavailable and not affecting other services and users. It was reported that an application was freezing during user session logoff. A complete memory dump was saved at that time, and its Stack Trace Collection (!stacks command, 943) shows the following suspicious thread in a user process (all other threads were waiting as normal):

```
0: kd> !stacks
Proc.Thread .Thread Ticks ThreadState Blocker
[...]
[89cfa960 Application.exe]
ea0.001c4c 89a11db0 0499cd1 Blocked DriverA+0x69db
[...]

0: kd> !thread 89a11db0 16
THREAD 89a11db0 Cid 0ea0.1c4c Teb: 7ffdf000 Win32Thread: bc347a48 WAIT: (Unknown) KernelMode Non-Alertable
89b87770 Unknown
b97004ac NotificationEvent
IRP List:
899e2668: (0006,0244) Flags: 00000884 Mdl: 00000000
Not impersonating
DeviceMap daf62b28
Owning Process 89cfa960 Image: Application.exe
Attached Process N/A Image: N/A
Wait Start TickCount 909331 Ticks: 4824273 (0:20:56:19.265)
Context Switch Count 186 LargeStack
UserTime 00:00:00.015
KernelTime 00:00:00.093
*** ERROR: Module load completed but symbols could not be loaded for Application.exe
Win32 Start Address Application (0x00406b2a)
Start Address kernel32!BaseProcessStartThunk (0x77e617f8)
Stack Init b60ceb30 Current b60cdf10 Base b60cf000 Limit b60cb000 Call b60ceb34
Priority 10 BasePriority 10 PriorityDecrement 0
ChildEBP RetAddr Args to Child
b60cdf28 80833485 89a11db0 00000000 00000000 nt!KiSwapContext+0x26
b60cdf54 8082949b dc399008 89b87748 b60ce01c nt!KiSwapThread+0x2e5
b60cdf88 b96d69db 00000002 b60cdffc 00000001 nt!KeWaitForMultipleObjects+0x3d7
WARNING: Stack unwind information not available. Following frames may be wrong.
b60cdfe8 b96d719e 89b87748 dc399008 b60ce01c DriverA+0x69db
[...]
```

We notice "89b87770 Unknown" and double check what object the thread is waiting for:

```
0: kd> dp b60cdfbc L00000002
b60cdfbc 89b87770 b97004ac
```