```
ApplicationK!_callthreadstart
ApplicationK!_threadstart
kernel32!BaseThreadInitThunk
ntdll!_RtlUserThreadStart
ntdll!_RtlUserThreadStart

2 Id: f00.f1c Suspend: 1 Teb: 7efd7000 Unfrozen

ntdll!NtDelayExecution
KERNELBASE!SleepEx
KERNELBASE!Sleep
kernel32!WerpReportFault
kernel32!BasepReportFault
kernel32!UnhandledExceptionFilter
ntdll!_RtlUserThreadStart
ntdll!_EH4_CallFilterFunc
ntdll!_except_handler4
ntdll!ExecuteHandler2
ntdll!ExecuteHandler
ntdll!KiUserExceptionDispatcher
ApplicationK!thread_two
ApplicationK!_callthreadstart
ApplicationK!_threadstart
kernel32!BaseThreadInitThunk
ntdll!_RtlUserThreadStart
ntdll!_RtlUserThreadStart

0:000> !uniqstack
Processing 3 threads, please wait

. 0 Id: f00.f04 Suspend: 0 Teb: 7efdd000 Unfrozen
Start: ApplicationK!mainCRTStartup (013a137c)
Priority: 0 Priority class: 32 Affinity: 3
ChildEBP RetAddr
0037f1a4 77d0bdd6 ntdll!NtWaitForMultipleObjects+0x15
0037f240 7529162d KERNELBASE!WaitForMultipleObjectsEx+0x100
0037f288 75291921 kernel32!WaitForMultipleObjectsExImplementation+0xe0
0037f2a4 7529b92d kernel32!WaitForMultipleObjects+0x18
0037f310 752b9bca kernel32!WerpReportFaultInternal+0x186
0037f324 752b98f8 kernel32!WerpReportFault+0x70
0037f334 7529875 kernel32!BasepReportFault+0x20
0037f3c0 77b10df7 kernel32!UnhandledExceptionFilter+0x1af
0037f3c8 77b10cd4 ntdll!_RtlUserThreadStart+0x62
0037f3dc 77b10b71 ntdll!_EH4_CallFilterFunc+0x12
0037f404 77a6ac6 ntdll!_except_handler4+0x8e
0037f428 77ae6a9b ntdll!ExecuteHandler2+0x26
0037f4d8 77ab010f ntdll!ExecuteHandler+0x24
0037f4d8 77d0280c ntdll!KiUserExceptionDispatcher+0xf
0037f824 013a1035 KERNELBASE!DebugBreak+0x2
0037f828 013a1325 ApplicationK!main+0x25
0037f870 75293677 ApplicationK!__tmainCRTStartup+0xfb
0037f87c 77ad9f02 kernel32!BaseThreadInitThunk+0xe
0037f8bc 77ad9ed5 ntdll!__RtlUserThreadStart+0x70
0037f8d 00000000 ntdll!_RtlUserThreadStart+0x1b
```