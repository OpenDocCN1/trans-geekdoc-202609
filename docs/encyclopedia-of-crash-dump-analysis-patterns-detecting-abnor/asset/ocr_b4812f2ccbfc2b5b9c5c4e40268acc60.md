```
1: kd> !cs -l -o -s
----------------------------------
DebugInfo           = 0x00000000003475220
Critical section    = 0x0000000000337740 (+0x3377740)
LOCKED
LockCount           = 0x10
WaiterWoken         = No
OwningThread        = 0x00000000000004e4
RecursionCount      = 0x0
LockSemaphore       = 0x0
SpinCount           = 0x0000000000000000
OwningThread        = .thread fffffa80344e4c00
[...]
```

```
// The "owner" thread is from winlogon.exe
```

```
1: kd> !thread fffffa80344e4c00 1f
THREAD fffffa80344e4c00 Cid 21d0.1e44 Teb: 000007fffffae000 Win32Thread: fffff900c0998c20 WAIT:
(WrUserRequest) UserMode Non-Alertable
fffffa80355817d0 SynchronizationEvent
Not impersonating
DeviceMap           fffffa80000088f0
Owning Process      fffffa80344ff77c0       Image: winLogon.exe
[...]
```

A PML (Process Monitor) log was recorded before the complete memory dump was forced, and it clearly shows **Glued Activity** trace analysis pattern⁸⁴. LSASS owned the thread but then the thread exited, and 2 other processes subsequently reused its TID.