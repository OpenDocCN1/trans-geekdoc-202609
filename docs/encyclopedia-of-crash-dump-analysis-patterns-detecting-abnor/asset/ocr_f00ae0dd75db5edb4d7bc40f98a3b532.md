# Waiting threads (wait originated from kernel space)

Examples include explicit wait as a result from calling potentially blocking API:

```
THREAD a33a9740 Cid 1980.1960 Teb: 7ffde000 Win32Thread: bc283ea8 WAIT: (Unknown) UserMode Non-Alertable
a35e3168 SynchronizationEvent
Not impersonating
DeviceMap e689f298
Owning Process a342d3a0 Image: explorer.exe
Wait Start TickCount 1369801 Ticks: 80646 (0:00:21:00.093)
Context Switch Count 1667 LargeStack
UserTime 00:00:00.015
KernelTime 00:00:00.093
Win32 Start Address Explorer!ModuleEntry (0x010148a4)
Start Address kernel32!BaseProcessStartThunk (0x77e617f8)
Stack Init f258b000 Current f258ac50 Base f258b000 Limit f2585000 Call 0
Priority 13 BasePriority 10 PriorityDecrement 1
Kernel stack not resident.
ChildEBP RetAddr
f258ac68 80833465 nt!KiSwapContext+0x26
f258ac94 80829a62 nt!KiSwapThread+0x2e5
f258acdc bf89adb3 nt!KeWaitForSingleObject+0x346
f258ad38 bf89da43 win32k!xxxSleepThread+0x1be
f258ad4c bf89e401 win32k!xxxRealWaitMessageEx+0x12
f258ad5c 8088978c win32k!NtUserWaitMessage+0x14
f258ad5c 7c8285ec nt!KiFastCallEntry+0xfc (TrapFrame @ f258ad64)
0007feeec 7739bf53 ntdll!KiFastSystemCallRet
0007ff08 7c8faddb USER32!NtUserWaitMessage+0xc
0007ff14 0100fff1 SHELL32!SHDesktopMessageLoop+0x24
0007ff5c 0101490c Explorer!ExplorerWinMain+0x2c4
0007ffc0 776ef23b Explorer!ModuleEntry+0x6d
0007fff0 00000000 kernel32!BaseProcessStart+0x23
```

and implicit wait when a thread yields execution to another thread voluntarily via explicit context swap:

```
THREAD a3072b68 Cid 1fc8.1d94 Teb: 7ffaf000 Win32Thread: bc1e3c20 WAIT: (Unknown) UserMode Non-Alertable
a37004d8 QueueObject
a3072be0 NotificationTimer
IRP List:
a322bee0: (0006,01fc) Flags: 00000000 Mdl: a30b8e30
a30bcc38: (0006,01fc) Flags: 00000000 Mdl: a35bf530
Not impersonating
DeviceMap e12256a0
Owning Process a3340a10 Image: IEXPLORE.EXE
Wait Start TickCount 1447963 Ticks: 2484 (0:00:00:38.812)
Context Switch Count 3972 LargeStack
UserTime 00:00:00.140
KernelTime 00:00:00.250
Win32 Start Address ntdll!TlpWorkerThread (0x7c839efb)
Start Address kernel32!BaseThreadStartThunk (0x77e617ec)
Stack Init f1cc3000 Current f1cc2c38 Base f1cc3000 Limit f1cbf000 Call 0
Priority 10 BasePriority 10 PriorityDecrement 0
ChildEBP RetAddr
```