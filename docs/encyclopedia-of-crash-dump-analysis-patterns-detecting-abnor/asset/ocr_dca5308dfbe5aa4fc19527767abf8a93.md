```
```
WARNING: Stack unwind information not available. Following frames may be wrong.
f4924830 f6002996 SomeDrv+0x48bee

5: kd! >thread 86ffe700 1f
THREAD 86ffe700 Cid 1ba4.1ba8 Teb: 7ffdf000 Win32Thread: bc23cea8 RUNNING on processor 4
Not impersonating
DeviceMap e44e9a40
Owning Process 87005708 Image: WINWORD.EXE
Wait Start TickCount 1415535 Ticks: 0
Context Switch Count 1547251 LargeStack
UserTime 00:00:00.750
KernelTime 00:00:45.265
Win32 Start Address WINWORD (0x300019b0)
Start Address kernel32!BaseProcessStartThunk (0x77e617f8)
Stack Init f3465000 Current f3464c48 Base f3465000 Limit f345e000 Call 0
Priority 8 BasePriority 8 PriorityDecrement 0
ChildEBP RetAddr
f3464d64 7c8285eb nt!KiFastCallEntry+0x91
f3464d68 badb0000 ntdll!KiFastSystemCall+0x3
```
```

```
```
5: kd! >thread 86803a90 1f
THREAD 86803a90 Cid 3c20.29f8 Teb: 7ffdf000 Win32Thread: bc295480 RUNNING on processor 5
Not impersonating
DeviceMap e518c6b8
Owning Process 857d5500 Image: SystemDump.exe
Wait Start TickCount 1415535 Ticks: 0
Context Switch Count 310 LargeStack
UserTime 00:00:00.015
KernelTime 00:00:00.046
*** ERROR: Module load completed but symbols could not be loaded for SystemDump.exe
Win32 Start Address SystemDump_400000 (0x0040ef92)
Start Address kernel32!BaseProcessStartThunk (0x77e617f8)
Stack Init b38a4000 Current b38a3c08 Base b38a4000 Limit b389f000 Call 0
Priority 11 BasePriority 8 PriorityDecrement 2
ChildEBP RetAddr
b38a3bf0 f79e3743 000000e2 cccccccc 866962b0 nt!KeBugCheckEx+0x1b
WARNING: Stack unwind information not available. Following frames may be wrong.
b38a3c3c 8081df65 SystemDump+0x743
b38a3c50 808f5437 nt!IofCallDriver+0x45
b38a3c64 808f61bf nt!IopSynchronousServiceTail+0x10b
b38a3d00 808eeed0 nt!IopXxxControlFile+0x5e5
b38a3d34 8088978c nt!NtDeviceIoControlFile+0x2a
b38a3d34 7c8285ec nt!KiFastCallEntry+0xfc
0012efc4 7c826fcb ntdll!KiFastSystemCallRet
0012efc8 77e416f5 ntdll!NtDeviceIoControlFile+0xc
0012f02c 00402208 kernel32!DeviceIoControl+0x137
0012f884 00404f8e SystemDump_400000+0x2208
```
```