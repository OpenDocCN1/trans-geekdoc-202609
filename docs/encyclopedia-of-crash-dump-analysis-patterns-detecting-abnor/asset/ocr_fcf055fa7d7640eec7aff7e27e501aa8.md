```
f1cc2c50 80833465 nt!KiSwapContext+0x26
f1cc2c7c 8082b60f nt!KiSwapThread+0x2e5
f1cc2cc4 808bed60 nt!KeRemoveQueue+0x417
f1cc2d48 8088978c nt!NtRemoveIoCompletion+0xdc
f1cc2d48 7c8285ec nt!KiFastCallEntry+0xfc (TrapFrame @ f1cc2d64)
06ceff70 7c8277bd ntdll!KiFastSystemCallRet
06ceff74 7c839f38 ntdll!ZwRemoveIoCompletion+0xc
06ceffb8 77e64829 ntdll!RtlpWorkerThread+0x3d
06ceffec 00000000 kernel32!BaseThreadStart+0x34
```

```
THREAD a3612020 Cid 1980.1a48 Teb: 7ffd9000 Win32Thread: 00000000 WAIT: (Unknown) UserMode Alertable
a3612098 NotificationTimer

Not impersonating
DeviceMap                 e689f298
Owning Process            a342d3a0       Image:         explorer.exe
Wait Start TickCount      1346718        Ticks: 103729 (0:00:27.00.765)
Context Switch Count      4
UserTime                  00:00:00.000
KernelTime                00:00:00.000
Win32 Start Address ntdll!RtlpTimerStart (0x7c83d3dd)
Start Address kernel32!BaseThreadStartThunk (0x77e617ec)
Stack Init f2453000 Current f2452c80 Base f2453000 Limit f2450000 Call 0
Priority 10 BasePriority 10 PriorityDecrement 0
Kernel stack not resident.

ChildEBP RetAddr
f2452c98 80833465 nt!KiSwapContext+0x26
f2452cc4 80828f0b nt!KiSwapThread+0x2e5
f2452d0c 80994812 nt!KeDelayExecutionThread+0x2ab
f2452d54 8088978c nt!NtDelayExecution+0x84
f2452d54 7c8285ec nt!KiFastCallEntry+0xfc (TrapFrame @ f2452d64)
0149ff9c 7c8264fb ntdll!KiFastSystemCallRet
0149ffa0 7c83d424 ntdll!NtDelayExecution+0xc
0149ffb8 77e64829 ntdll!RtlpTimerThread+0x47
0149ffec 00000000 kernel32!BaseThreadStart+0x34
```

Explicit waits in the kernel can be originated from GUI threads and their message loops, for example, Main Thread (page 614). Blocked GUI thread, Message Box pattern (page 660) can be seen as an example of a genuine Blocked Thread. Some “blocked” threads are just really Passive Threads (page 793).