# User Space

This pattern occurs frequently. It manifests itself when we run !analyze -v command, and we don’t see an exception, or we see only a breakpoint hit. In this case, manual analysis is required. Sometimes this happens because of another pattern: **Multiple Exceptions** (page 714). In other cases an exception happens, and it is handled by an exception handler dismissing it, and a process continues its execution slowly accumulating corruption inside its data leading to a new crash or hang. Sometimes we see a process hanging during its termination like the case shown below.

We have a process dump with only one thread:

```
0:000> kv
ChildEBP RetAddr
0096fcdc 7c822124 ntdll!KiFastSystemCallRet
0096fce0 77e6baa8 ntdll!NtWaitForSingleObject+0xc
0096fd50 77e6ba12 kernel32!WaitForSingleObjectEx+0xac
0096fd64 67f016ce kernel32!WaitForSingleObject+0x12
0096fd78 7c82257a component!DllInitialize+0xc2
0096fd98 7c81b80b ntdll!LdrpCallInitRoutine+0x14
0096fe34 77e522fe ntdll!LdrShutdownProcess+0x130
0096ff20 77e5304d kernel32!_ExitProcess+0x43
0096ff34 77bcade4 kernel32!ExitProcess+0x14
0096ff40 77bcaefb msvcrt!_crtExitProcess+0x32
0096ff70 77bcaf6d msvcrt!_cinit+0xd2
0096ff84 77bcb555 msvcrt!_exit+0x11
0096ffb8 77e66063 msvcrt!endthreadex+0xc8
0096ffec 00000000 kernel32!BaseThreadStart+0x34
```

We can look at its raw stack and try to find the symbol address for KiUserExceptionDispatcher. This function calls RtlDispatchException:

```
0:000> !teb
TEB at 7ffdc000
ExceptionList: 0096fd40
StackBase: 00970000
StackLimit: 0096a000
SubSystemTib: 00000000
FiberData: 00001e00
ArbitraryUserPointer: 00000000
Self: 7ffdc000
EnvironmentPointer: 00000000
ClientId: 00000858 . 000008c0
RpcHandle: 00000000
Tls Storage: 00000000
PEB Address: 7ffdd000
LastErrorValue: 0
LastStatusValue: c0000135
Count Owned Locks: 0
HardErrorMode: 0
```