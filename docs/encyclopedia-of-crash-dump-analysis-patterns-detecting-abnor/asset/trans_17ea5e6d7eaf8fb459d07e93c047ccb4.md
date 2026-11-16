

```
ModLoad: 775a0000 77630000   C:\Windows\syswow64\GDI32.dll
ModLoad: 76df0000 76dbf000   C:\Windows\syswow64\ADVAPI32.dll
ModLoad: 76df0000 76ee0000   C:\Windows\syswow64\RPCRT4.dll
ModLoad: 75d60000 75dc0000   C:\Windows\syswow64\Secur32.dll
(1ec.1290): Unknown exception - code c0000135 (first chance)
(1ec.1290): Unknown exception - code c0000135 (!!! second chance !!!)
eax=00000000 ebx=77c4a174 ecx=75ce3cf9 edx=00000000 esi=7fede028 edi=7efd0000
eip=77bcf1d1 esp=0017fca4 ebp=0017fd00 iopl=0         nv up ei pl zr na pe nc
cs=0023  ss=002b  ds=002b  es=002b  fs=0053  gs=002b             efl=00000246
ntdll!_LdrpInitialize+0x6d:
77bcf1d1 8b45b8            mov     eax,dword ptr [ebp-48h] ss:002b:0017fcb8=7efde000
```

The dump file that we used can be downloaded from FTP to play with^138.

## 注释

Sometimes, we may not see exceptions, but error and status codes in the output of !teb command, for example:

```
Error code: (Win32) 0x7e (126) - The specified module could not be found.
Error code: (NTSTATUS) 0xc0000135 (3221225781) - The program can't start because %hs is missing from your computer. Try reinstalling the program to fix this problem.
```

## 缺失进程

Sometimes the functionality of a system depends on a specific application or service process. For example, in a database server environment it might be a database process, in a printing environment, it is a print spooler process, or in a terminal services environment, it is a terminal services process (*termsvc*, hosted by *svchost.exe*). In system failure scenarios, we should check these processes for their presence (and also the presence of any **耦合进程**, page 149). However, if the vital process is present in the output we should check if it is exited but references to it exist, or whether there are any **缺失线程** (page 683) or **缺失组件** (page 666) inside it, any **挂起线程** (page 964) and **特殊进程** (page 875) like a postmortem debugger. We shouldn’t also forget about service dependencies and their relevant process startup order. For example, we know that our service is hosted by *svchost.exe* and we see one such process exited, but its object is still referenced somewhere:

```
0: kd> !vm

*** Virtual Memory Usage ***
[...]
        0ed8 svchost.exe       0 (        0 Kb)
[...]
```

However, another command shows that it could be a different service hosted by the same image, *svchost.exe* if we know that ServiceA depends on our service:

```
0: kd> !process 0 0

[...]

PROCESS 8aabed88  SessionId: 0  Cid: 0854    Peb: 7ffd6000  ParentCid: 0220
    DirBase: bff4d4a0  ObjectTable: e1c867a8  HandleCount:  778.
    Image: ServiceA.exe

[...]

PROCESS 8aaa6510  SessionId: 0  Cid: 0ed8    Peb: 7ffd4000  ParentCid: 0220
    DirBase: bff4d580  ObjectTable: 00000000  HandleCount:  0.
    Image: svchost.exe

[...]
```

Another alternative is that our service was restarted but then exited. If our process is not visible, it could be possible that it was either stopped or simply crashed before.

### 注释

Another example is a GUI message **等待链** (page 1132) directed to a window that once belonged to no longer running process.

## 缺失线程

Sometimes it is possible that a process crash dump doesn’t have all usual threads inside. For example, we expect at least 4 threads including the main process thread, but in the dump, we see only 3. If we know that some access violations were reported in the event log before (not necessarily for the same PID), we may suspect that one of the threads had been terminated due to some reason. We call this pattern **缺失线程**.

In order to simulate this problem, we created a small multithreaded program in Visual C++:

```
#include "stdafx.h"
#include <process.h>

void thread_request(void *param)
{
    while (true);
}

int _tmain(int argc, _TCHAR* argv[])
{
    _beginthread(thread_request, 0, NULL);

    try
    {
        if (argc == 2)
        {
            *(int *)NULL = 0;
        }
    }
    catch (...)
    {
        _endthread();
    }

    while (true);

    return 0;
}
```

If there is a command line argument, then the main thread simulates access violation and finishes in the exception handler. In order to use SEH exceptions with C++ try/catch blocks we have to enable /EHa option in C++ Code Generation properties:

| 启用字符串池 | 否 |
|---|---|
| 启用最小重新生成 | 否 |
| 启用 C++ 异常 | 是，带有 SEH 异常 (/EHa) |
| 较小类型检查 | 否 |
| 基本运行时检查 | 默认 |
| 运行时库 | 多线程 (/MT) |
| 结构成员对齐 | 默认 |
| 缓冲区安全检查 | 是 |
| 启用函数级链接 | 否 |
| 启用增强指令集 | 未设置 |
| 浮点模型 | 精确 (/fp:precise) |
| 启用浮点异常 | 否 |

If we run the program without command line parameter and take a manual dump from it, we see 2 threads:

```
0:000> ~*kL
 .  0  Id: 1208.fdc Suspend: 1 Teb: 7efdd000 Unfrozen
ChildEBP RetAddr
0012ff70 00401403 MissingThread!wmain+0x58
0012ffc0 7d4e7d2a MissingThread!_tmainCRTStartup+0x15e
0012fff0 00000000 kernel32!BaseProcessStart+0x28

 1  Id: 1208.102c Suspend: 1 Teb: 7efda000 Unfrozen
ChildEBP RetAddr
005dff7c 004010ef MissingThread!thread_request
005dffb4 00401188 MissingThread!_callthreadstart+0x1b
005dffb8 7d4dfe21 MissingThread!_threadstart+0x73
005dffec 00000000 kernel32!BaseThreadStart+0x34

0:000> ~
 .  0  Id: 1208.fdc Suspend: 1 Teb: 7efdd000 Unfrozen
   1  Id: 1208.102c Suspend: 1 Teb: 7efda000 Unfrozen

0:000> dd 7efdd000 14
7efdd000 0012ff64 00130000 0012e000 00000000
```

We also dumped TEB of the main thread. However, if we run the program with any command line parameter and look at its manual dump we would see only one thread with the main thread missing:

```
0:000> ~*kL
 .  0  Id: 1004.12e8 Suspend: 1 Teb: 7efda000 Unfrozen
ChildEBP RetAddr
005dff7c 004010ef MissingThread!thread_request
005dffb4 00401188 MissingThread!_callthreadstart+0x1b
005dffb8 7d4dfe21 MissingThread!_threadstart+0x73
005dffec 00000000 kernel32!BaseThreadStart+0x34

0:000> ~
 .  0  Id: 1004.12e8 Suspend: 1 Teb: 7efda000 Unfrozen
```

If we try to dump TEB address and stack data from the missing main thread we would see that the memory was already decommitted:

```
0:000> dd 7efdd000 14
7efdd000 ???????? ???????? ???????? ????????
0:000> dds 0012e000 00130000
0012e000 ????????
0012e004 ????????
0012e008 ????????
0012e00c ????????
0012e010 ????????
0012e014 ????????
0012e018 ????????
0012e01c ????????
0012e020 ????????
0012e024 ????????
```

The same effect can be achieved in the similar program that exits the thread in the custom unhandled exception filter:

```
#include "stdafx.h"
#include <process.h>
#include <windows.h>

LONG WINAPI CustomUnhandledExceptionFilter(struct _EXCEPTION_POINTERS* ExceptionInfo)
{
    ExitThread(-1);
}

void thread_request(void *param)
{
    while (true);
}

int _tmain(int argc, _TCHAR* argv[])
{
    _beginthread(thread_request, 0, NULL);
    SetUnhandledExceptionFilter(CustomUnhandledExceptionFilter);

    *(int *)NULL = 0;

    while (true);

    return 0;
}
```

The solution to catch an exception that results in a thread termination would be to run the program under WinDbg or any other debugger:

```
CommandLine: C:\MissingThread\MissingThread.exe 1
Symbol search path is: SRV*c:\websymbols*http://msdl.microsoft.com/download/symbols
Executable search path is:
ModLoad: 00400000 0040f000   MissingThread.exe
ModLoad: 7d4c0000 7d5f0000   NOT_AN_IMAGE
ModLoad: 7d6d0000 7d6f0000   C:\W2K3\SysWOW64\ntdll.dll
ModLoad: 7d4c0000 7d5f0000   C:\W2K3\syswow64\kernel32.dll
(df0.12f0): Break instruction exception - code 80000003 (first chance)
eax=7d600000 ebx=7fed000 ecx=00000005 edx=00000020 esi=7d6a01f4 edi=00221f38
eip=7d61002d esp=0012fb4c ebp=0012fcac iopl=0 nv up ei pl zr na po nc
cs=0023 ss=002b ds=002b es=002b fs=0053 gs=002b efl=00010202
ntdll!DbgBreakPoint:
7d61002d cc            int    3

0:000> g
ModLoad: 71c20000 71c32000   C:\W2K3\SysWOW64\tsappcmp.dll
ModLoad: 77ba0000 77bfa000   C:\W2K3\syswow64\msvcrt.dll
ModLoad: 00410000 004ab000   C:\W2K3\syswow64\ADVAPI32.dll
ModLoad: 7da20000 7db00000   C:\W2K3\syswow64\RPCRT4.dll
ModLoad: 7d8d0000 7d920000   C:\W2K3\syswow64\Secur32.dll
(df0.12f0): Access violation - code c0000005 (first chance)
First chance exceptions are reported before any exception handling.
This exception may be expected and handled.
eax=00000070 ebx=7d4d8df9 ecx=7b8d42d9 edx=00000000 esi=00000002 edi=0000ece
eip=00401057 esp=0012ff50 ebp=0012ff70 iopl=0 nv up ei pl zr na pe nc
cs=0023 ss=002b ds=002b es=002b fs=0053 gs=002b efl=00010246
MissingThread!wmain+0x47:
00401057 c7050000000000000000 mov dword ptr ds:[0],0 ds:002b:00000000=????????

0:000> kl
ChildEBP RetAddr
0012ff70 00401403 MissingThread!wmain+0x47
0012ffc0 7d4e7d2a MissingThread!_tmainCRTStartup+0x15e
0012fff0 00000000 kernel32!BaseProcessStart+0x28
```

If live debugging is not possible and we are interested in crash dumps saved upon a first chance exception before it is processed by an exception handler we can also use MS userdump tool after we install it and enable All Exceptions in the Process Monitoring Rules dialog box. Another tool can be used is ADPlus in crash mode from Debugging Tools for Windows.

