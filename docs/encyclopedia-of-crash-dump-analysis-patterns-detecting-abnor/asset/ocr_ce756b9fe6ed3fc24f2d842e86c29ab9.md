Multiple Exceptions captures the known fact that there could be as many exceptions (“crashes”) as many threads in a process. The following UML diagram depicts the relationship between Process, Thread, and Exception entities:

![](bbox=[0.24, 0.19, 0.76, 0.24])

Every process in Windows has at least one execution thread so there could be at least one exception per thread (like invalid memory reference) if things go wrong. There could be a second exception in that thread if exception handling code experiences another exception or the first exception was handled.

The general solution is to look at all threads and their stacks and do not rely on what tools say.

Here is a concrete example from one of the dumps. Internet Explorer crashed, and we opened it in WinDbg and run !analyze -v command. This is what we got in WinDbg output:

```
ExceptionAddress: 7c822583 (ntdll!DbgBreakPoint)
    ExceptionCode: 80000003 (Break instruction exception)
  ExceptionFlags: 00000000
NumberParameters: 3
    Parameter[0]: 00000000
    Parameter[1]: 8fb834b8
    Parameter[2]: 00000003
```

Break instruction, we might think, shows that the dump was taken manually from the running application, and there was no crash - the customer sent the wrong dump or misunderstood troubleshooting instructions. However, we looked at all threads, and noticed the following two stacks (threads 15 and 16):

```
0:016>~*kL
...
15 Id: 1734.8f4 Suspend: 1 Teb: 7ffab000 Unfrozen
ntdll!KiFastSystemCallRet
ntdll!NtRaiseHardError+0xc
kernel32!UnhandledExceptionFilter+0x54b
kernel32!BaseThreadStart+0x4a
kernel32!_except_handler3+0x61
ntdll!ExecuteHandler+0x26
ntdll!ExecuteHandler+0x24
ntdll!KiUserExceptionDispatcher+0xee
componentA!xxx
componentB!xxx
mshtml!xxx
kernel32!BaseThreadStart+0x34

# 16 Id: 1734.11a4 Suspend: 1 Teb: 7ffaa000 Unfrozen
ntdll!DbgBreakPoint
ntdll!DbgUiRemoteBreakin+0x36
```