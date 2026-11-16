# User Space

As discussed in **Early Crash Dump** pattern (page 312) saving crash dumps on first-chance exceptions helps to diagnose components that might have caused corruption and later crashes, hangs or CPU spikes by ignoring abnormal exceptions like access violation. In such cases, we need to know whether an application installs its own **Custom Exception Handler** or several of them. If it uses only default handlers provided by runtime or windows subsystem then most likely a first-chance access violation exception will result in a last-chance exception and a postmortem dump. To check a chain of exception handlers, we can use WinDbg **!exchain** extension command.

For example:

```
0:000> !exchain
0017f9d8: TestDefaultDebugger!AfxWinMain+3f5 (00420aa9)
0017fa60: TestDefaultDebugger!AfxWinMain+34c (00420a00)
0017fb20: user32!_except_handler4+0 (770780eb)
0017fcc0: user32!_except_handler4+0 (770780eb)
0017fd24: user32!_except_handler4+0 (770780eb)
0017fe40: TestDefaultDebugger!AfxWinMain+16e (00420822)
0017feec: TestDefaultDebugger!AfxWinMain+797 (00420e4b)
0017ff90: TestDefaultDebugger!_except_handler4+0 (00410e00)
0017ffdc: ntdll!_except_handler4+0 (77961c78)
```

We see that **TestDefaultDebugger** doesn't have its own exception handlers except ones provided by MFC and C/C++ runtime libraries which were linked statically. Here is another example. It was reported that a 3rd-party application was hanging and spiking CPU (**Spiking Thread** pattern, page 888), so a user dump was saved using command line **userdump.exe**:

```
0:000> vertarget
Windows Server 2003 Version 3790 (Service Pack 2) MP (4 procs) Free x86 compatible
Product: Server, suite: TerminalServer
kernel32.dll version: 5.2.3790.4062 (srv03_sp2_gtx.070417-0203)
Debug session time: Thu Nov 22 12:45:59.000 2007 (GMT+0)
System Uptime: 0 days 10:43:07.667
Process Uptime: 0 days 4:51:32.000
Kernel time: 0 days 0:08:04.000
User time: 0 days 0:23:09.000
0:000> !runaway 3
User Mode Time
Thread Time
0:1c1c 0 days 0:08:04.218
1:2e04 0 days 0:00:00.015
Kernel Mode Time
Thread Time
0:1c1c 0 days 0:23:09.156
1:2e04 0 days 0:00:00.031
```