
```
ntdll!_RtlUserThreadStart
ntdll!_RtlUserThreadStart
103 Id: 136c.17a0 Suspend: 0 Teb: 7ff2d000 Unfrozen
ntdll!KiFastSystemCallRet
ntdll!ZwRemoveIoCompletion
kernel32!GetQueuedCompletionStatus
dtrans!TMThreadProc
kernel32!BaseThreadInitThunk
ntdll!_RtlUserThreadStart
ntdll!_RtlUserThreadStart

104 Id: 136c.17c4 Suspend: 0 Teb: 7ff2c000 Unfrozen
ntdll!KiFastSystemCallRet
ntdll!ZwRemoveIoCompletion
kernel32!GetQueuedCompletionStatus
dtrans!TMThreadProc
kernel32!BaseThreadInitThunk
ntdll!_RtlUserThreadStart
ntdll!_RtlUserThreadStart

105 Id: 136c.f08 Suspend: 0 Teb: 7ffa0000 Unfrozen
ntdll!KiFastSystemCallRet
ntdll!ZwRemoveIoCompletion
kernel32!GetQueuedCompletionStatus
dtrans!TMThreadProc
kernel32!BaseThreadInitThunk
ntdll!_RtlUserThreadStart
ntdll!_RtlUserThreadStart

106 Id: 136c.1268 Suspend: 0 Teb: 7ff28000 Unfrozen
ntdll!KiFastSystemCallRet
ntdll!ZwRemoveIoCompletion
kernel32!GetQueuedCompletionStatus
dtrans!TMThreadProc
kernel32!BaseThreadInitThunk
ntdll!_RtlUserThreadStart
ntdll!_RtlUserThreadStart

107 Id: 136c.12c8 Suspend: 0 Teb: 7ff27000 Unfrozen
ntdll!KiFastSystemCallRet
ntdll!ZwRemoveIoCompletion
kernel32!GetQueuedCompletionStatus
dtrans!TMThreadProc
kernel32!BaseThreadInitThunk
ntdll!_RtlUserThreadStart
ntdll!_RtlUserThreadStart

108 Id: 136c.1634 Suspend: 0 Teb: 7ff26000 Unfrozen
ntdll!KiFastSystemCallRet
ntdll!ZwRemoveIoCompletion
kernel32!GetQueuedCompletionStatus
dtrans!TMThreadProc

kernel32!BaseThreadInitThunk
ntdll!_RtlUserThreadStart
ntdll!_RtlUserThreadStart
109 Id: 136c.120c Suspend: 0 Teb: 7ff21000 Unfrozen
ntdll!KiFastSystemCallRet
ntdll!ZwRemoveIoCompletion
kernel32!GetQueuedCompletionStatus
dtrans!TMThreadProc
kernel32!BaseThreadInitThunk
ntdll!_RtlUserThreadStart
ntdll!_RtlUserThreadStart

110 Id: 136c.13f4 Suspend: 0 Teb: 7ff20000 Unfrozen
ntdll!KiFastSystemCallRet
ntdll!ZwRemoveIoCompletion
kernel32!GetQueuedCompletionStatus
dtrans!TMThreadProc
kernel32!BaseThreadInitThunk
ntdll!_RtlUserThreadStart
ntdll!_RtlUserThreadStart

111 Id: 136c.1494 Suspend: 0 Teb: 7ff1f000 Unfrozen
ntdll!KiFastSystemCallRet
ntdll!ZwRemoveIoCompletion
kernel32!GetQueuedCompletionStatus
dtrans!TMThreadProc
kernel32!BaseThreadInitThunk
ntdll!_RtlUserThreadStart
ntdll!_RtlUserThreadStart

112 Id: 136c.16ec Suspend: 0 Teb: 7ff1e000 Unfrozen
ntdll!KiFastSystemCallRet
ntdll!ZwRemoveIoCompletion
kernel32!GetQueuedCompletionStatus
dtrans!TMThreadProc
kernel32!BaseThreadInitThunk
ntdll!_RtlUserThreadStart
ntdll!_RtlUserThreadStart

113 Id: 136c.d68 Suspend: 0 Teb: 7ff4a000 Unfrozen
ntdll!KiFastSystemCallRet
ntdll!ZwRemoveIoCompletion
kernel32!GetQueuedCompletionStatus
rpcrt4!COMMON_ProcesCalls
rpcrt4!LOADABLE_TRANSPORT::ProcessIOEvents
rpcrt4!ProcessIOEventsWrapper
rpcrt4!BaseCachedThreadRoutine
rpcrt4!ThreadStartRoutine
kernel32!BaseThreadInitThunk
ntdll!_RtlUserThreadStart
ntdll!_RtlUserThreadStart

114 Id: 136c.5fc Suspend: 0 Teb: 7fffd000 Unfrozen
ntdll!KiFastSystemCallRet
ntdll!ZwWaitForWorkViaWorkerFactory
ntdll!TppWorkerThread
kernel32!BaseThreadInitThunk
ntdll!_RtlUserThreadStart
ntdll!_RtlUserThreadStart
```

In contrast, Flash10b module (shown in bold italics above) is not ubiquitous; it is present on just two threads (#31 and #32).

We got the idea of **Unified Stack Trace** analysis pattern from Flame Graphs<sup>213</sup>. Like the latter, we combine **Stack Trace Collection** (page 933) into one aggregate trace, but we may use the same length for repeated frames and may use different color intensities to present multiplicities. Different frame height may also be used to unify top frames such as waiting API. Different collections may be used in addition to database-like (page 919) stack traces (**Unmanaged Space**, page 943, **Managed Space**, page 940, **Predicate**, page 943, **I/O Requests**, page 936, **CPUs**, page 933). The collections may be composed of different varieties of stack traces, such as **General**, page 926, **Managed**, page 624, **Module**, page 699, **Quotient**, page 824, **Filters**, page 924).

```
0:003> ~*kc

 0  Id: 984.994 Suspend: 1 Teb: 00007ff6`f411d000 Unfrozen
 # Call Site
00 USER32!NtUserGetMessage
01 USER32!GetMessageW
02 notepad!WinMain
03 notepad!WinMainCRTStartup
04 KERNEL32!BaseThreadInitThunk
05 ntdll!RtlUserThreadStart

 1  Id: 984.eb8 Suspend: 1 Teb: 00007ff6`f411b000 Unfrozen
 # Call Site
00 ntdll!NtWaitForWorkViaWorkerFactory
01 ntdll!TppWorkerThread
02 KERNEL32!BaseThreadInitThunk
03 ntdll!RtlUserThreadStart

 2  Id: 984.1a8c Suspend: 1 Teb: 00007ff6`f4119000 Unfrozen
 # Call Site
00 ntdll!NtWaitForWorkViaWorkerFactory
01 ntdll!TppWorkerThread
02 KERNEL32!BaseThreadInitThunk
03 ntdll!RtlUserThreadStart

 # 3  Id: 984.11b0 Suspend: 1 Teb: 00007ff6`f4117000 Unfrozen
 # Call Site
00 ntdll!DbgBreakPoint
01 ntdll!DbgUiRemoteBreakin
02 KERNEL32!BaseThreadInitThunk
03 ntdll!RtlUserThreadStart
```

The collection can be represented in a more compact form with multiplicities:

```
USER32!NtUserGetMessage
USER32!GetMessageW
notepad!WinMain | 2* ntdll!NtWaitForWorkViaWorkerFactory | ntdll!DbgBreakPoint
notepad!WinMainCRTStartup | 2* ntdll!TppWorkerThread | ntdll!DbgUiRemoteBreakin
4* KERNEL32!BaseThreadInitThunk
4* ntdll!RtlUserThreadStart
```

It can also be illustrated in the following diagram:

![](img/d6dfefc8f9ab7106c77a723ff84aaa6d_1035_0.png)

Such diagrams may help to spot Ubiquitous Components (page 1020) quickly.

**Unified Stack Trace** is also a generalization of **Stack Trace Set** (page 952) where the latter only excludes fully duplicated stack traces, but the former takes into account **Constant Subtraces** (page 141).

## Unknown Component

Sometimes we suspect that a problem was caused by some module but WinDbg lmv command doesn't show the company name and other verbose information for it, and Google search has no results for the file name. We call this pattern Unknown Component.

In such cases, additional information can be obtained by dumping the module resource section or the whole module address range and looking for ASCII and UNICODE strings. For example (byte values in db output are omitted for clarity):

```
2: kd> lmv m driver
start end module name
f5022000 f503e400 driver (deferred)
Image path: \SystemRoot\System32\drivers\driver.sys
Image name: driver.sys
Timestamp: Tue Jun 12 11:33:16 2007 (466E766C)
CheckSum: 00021A2C
ImageSize: 0001C400
Translations: 0000.04b0 0000.04e0 0409.04b0 0409.04e0
2: kd> db f5022000 f503e400
f5022000 MZ.......
f5022010 .......@.....
f5022020 .............
f5022030 ............!
f5022040 !.L!Th
f5022050 is program canno
f5022060 t be run in DOS
f5022070 mode....$....
f5022080 .g.._B.._B.._B.
f5022090 _C.=B..%Q.X.B.
f50220a0 _B.B].B.Y%H..|.B.
f50220b0 ..D^.B.Rich..B.
f50220c0 ......PE..L...
f50220d0 lvnF.......
...
f503ce30 .............
f503ce40 .............
f503ce50 .............
f503ce60 .......0...
f503ce70 .............
f503ce80 ....H......
f503ce90 ......4...V.
f503cea0 S_.V.E.R.S.I.O.
f503ceb0 N_..I.N.F.O....
f503cec0 .............
f503ced0 ......?......
f503cee0 .............
f503cef0 ....P....S.tr.
f503cf00 i.n.g.File.I.
f503cf10 n.f.o.......0.
f503cf20 4.0.9.0.4.b.0...
f503cf30 4...C.o.m.p.p.a
f503cf40 n.y.N.a.m.e...
f503cf50 M.y.C.o.m.p. .A.
f503cf60 G...p.$...F.i.l
f503cf70 e.D.e.s.c.r.i.p.
f503cf80 t.i.o.n...M.y
f503cf90 .B.i.g. .P.r.o.
f503cfa0 d.u.c.t .H.o.o.o
f503cfb0 k..........
f503cfc0 ............
f503cfd0 ....4...F.i.l
f503cfe0 e.V.e.r.s.i.o.n
f503cff0 ...5...1.0...
f503d000 ???????????????
f503d010 ????????????????
f503d020 ???????????????
f503d030 ???????????????
...
...
...
```

We see that CompanyName is MyComp AG, FileDescription is My Big Product Hook, and FileVersion is 5.0.1.

In our example the same information can be retrieved by dumping the image file header and then finding and dumping the resource section:

```
2: kd> lmv m driver
start end module name
f5022000 f503e400 driver (deferred)
Image path: \SystemRoot\System32\drivers\driver.sys
Image name: driver.sys
Timestamp: Tue Jun 12 11:33:16 2007 (466E766C)
CheckSum: 00021A2C
ImageSize: 0001C400
Translations: 0000.04b0 0000.04e0 0409.04b0 0409.04e0

2: kd> !dh f5022000 -f
File Type: EXECUTABLE IMAGE
FILE HEADER VALUES
14C machine (i386)
6 number of sections
466E766C time date stamp Tue Jun 12 11:33:16 2007
0 file pointer to symbol table
0 number of symbols
E0 size of optional header
10E characteristics
Executable
Line numbers stripped
Symbols stripped
32 bit word machine
```
