
```
0: kd> .sympath+ c:\sym\ModuleA.pdb\C14E734A367F4DD0974DFA47C1194F281
Symbol search path is: SRV*c:\mss*http://msdl.microsoft.com/download/symbols;
c:\sym\ModuleA.pdb\C14E734A367F4DD0974DFA47C1194F281
[...]

0: kd> .reload
Loading Kernel Symbols
Loading User Symbols
Loading unloaded module list

0: kd> kL
*** Stack trace for last set context - .thread/.cxr resets it
ChildEBP RetAddr
ba38fcb8 80503836 nt!KiSwapContext+0x2f
ba38fcc4 804fb068 nt!KiSwapThread+0x8a
ba38fcec 805c0750 nt!KeWaitForSingleObject+0x1c2
ba38fd50 8054161c nt!NtWaitForSingleObject+0x9a
ba38fd50 7c90e4f4 nt!KiFastCallEntry+0xfc
0006f648 7c90df3c ntdll!KiFastSystemCallRet
0006f64c 7c91b22b ntdll!NtWaitForSingleObject+0xc
0006fd4 7c901046 ntdll!RtlpWaitForCriticalSection+0x132
0006f6dc 01373d7f ntdll!RtlEnterCriticalSection+0x46
0006f64e 0132b22e ModuleA!CSLock+0x7
0006f7a4 0132b785 ModuleA!SignalEvent+0x5e
[...]

0006f848 7e418734 ModuleA!WindowProc+0x136
0006f874 7e418816 USER32!InternalCallWinProc+0x28
0006f8dc 7e4189cd USER32!UserCallWinProcCheckWow+0x150
0006f93c 7e418a10 USER32!DispatchMessageWorker+0x306
0006f94c 0084367e USER32!DispatchMessageW+0xf
[...]
```

## 非同步转储

分析来自**耦合进程**（第 149 页）或一般情况下来自纤维束内存空间的内存纤维²¹⁴时，我们需要了解其创建时间（称为调试会话时间）。在某些情况下，我们需要知道它们的时间顺序：哪个进程内存转储先被保存，以及在第二个进程内存转储被保存之前过了多长时间。除了打开转储时的初始输出外，**.time** 和 **version** WinDbg 命令可在分析过程中的任何时候用于检查此信息。

在一个涉及打印的示例中，我们看到**阻塞线程**（82）正尝试使用 LPC 联系打印机后台处理程序服务。其**线程年龄**（第 1001 页）不超过 3 秒。我们还有打印机后台处理程序服务进程的内存转储，据称是同时获取的。但是，检查时发现，它是在 2 分钟前保存的。此外，*PrintIsolationHost.exe* 进程内存转储的保存时间更早。因此，整个序列被颠倒了，因为打印应用程序调用后台处理程序，而后者调用相应的驱动程序，而不是反过来。

## 用户空间证据

提出的一个问题是：如果我们得到的是内核内存转储，而不是请求的完整内存转储，该怎么办？它有用吗？当然，如果在分析内核内存转储后请求了完整内存转储，那么第二个内核转储可能有助于双重验证。因此，我们假设这是第一次获得内核内存转储，而问题与性能或系统冻结有关，而不是 bugcheck。如果存在 bugcheck，大多数情况下内核内存转储就足够了，因此我们不考虑此模式中的内核转储。

这样的内核内存转储仍然有用，因为用户空间诊断指标指向用户空间或“进程间空间”中的可能模式。我们将此模式称为**用户空间证据**。它是一个集合型超模式，类似**历史信息**（第 483 页）。

在内核内存转储中，我们可以看到诸如**等待链**（例如，**ALPC**，第 1097 页，或**进程对象**，第 1108 页）、**死锁**（例如 ALPC，第 197 页）、与特定**双重栈跟踪**（第 282 页，例如，异常处理）对应的内核栈跟踪、**句柄泄漏**（第 416 页）、**缺失线程**（第 683 页）、**模块产品进程**（第 698 页）、**单线程进程**（第 765 页）、**飙升线程**（第 885 页）、**进程工厂**（第 814 页，例如，**僵尸进程**的父 PID，第 1158 页）等模式。

发现的证据可能指向特定进程和进程组（**耦合进程**，第 148 页，以及会话进程），并建议收集进程内存转储（尤其是强制获取进一步的完整内存转储存在问题）或针对已诊断进程的故障排除步骤。

## 增值进程

这是终端服务环境中常见的模式：在每个会话中都列出了一个或多个进程名称，但并非必然需要。这些进程通常运行以提供用户体验增强。在这种情况下，如果观察到的功能问题与运行附加进程的目的相符，我们可能希望出于测试和故障排除目的将其消除。

```
0: kd> !sprocess 12
Dumping Session 12

__MM_SESSION_SPACE fffff880e5d5000
__MMSESSION fffff880e5d5b40
PROCESS fffffa800d50b30
SessionId: 12 Cid: 0b04 Peb: 7ffffffdc000 ParentCid: 1478
DirBase: 6bb77000 ObjectTable: fffff8a003f280b0 HandleCount: 158.
Image: csrss.exe

PROCESS fffffa80030c7060
SessionId: 12 Cid: 1a48 Peb: 7fffffd8000 ParentCid: 1478
DirBase: 0a33c000 ObjectTable: fffff8a003c46c00 HandleCount: 179.
Image: winlogon.exe

PROCESS fffffa8008250b30
SessionId: 12 Cid: 18c8 Peb: 7fffffd000 ParentCid: 1a48
DirBase: 0350d000 ObjectTable: fffff8a0025b6840 HandleCount: 226.
Image: LogonUI.exe

PROCESS fffffa8008b00530
SessionId: 12 Cid: 1508 Peb: 7fffffd000 ParentCid: 02f0
DirBase: 02f65000 ObjectTable: fffff8a003b7e530 HandleCount: 197.
Image: ExcitingFeatureX.exe

[...]
```

## 值偏差

### 栈跟踪

内存转储分析关乎偏差，其中一种就是**值偏差**（一种超模式），无论是打开句柄数量（**内存不足**，第 526 页）、堆大小（**内存泄漏**，第 650 页）、竞争锁数量（**共享锁蜂拥**，第 966 页）、在内核中花费的时间（**飙升线程**，第 888 页）等，还有许多其他指标。每个系统或进程属性都有其平均值和均值，大的偏差会表现为所谓的异常。下面我们提供一个栈跟踪大小（深度）偏差的示例。大多数栈跟踪的平均帧数取决于内存转储的类型：用户、内核和完整，但明显更长或更短的栈跟踪在**栈跟踪集合**（第 943 页）中清晰可见。我们最初计划将此模式称为**黑天鹅**，但稍加思考后放弃了这个想法，因为此类偏差毕竟并不真正罕见。以下是来自 CPU 飙升进程的**栈跟踪集合**示例，其中包含大量仅有三个帧的相同栈跟踪：

```
0:000> ~*kL

[...]

  19 Id: 1054.1430 Suspend: 1 Teb: 7ff9c000 Unfrozen
ChildEBP RetAddr
1ac6ff50 7739bf53 ntdll!KiFastSystemCallRet
1ac6ffb8 77e6482f user32!NtUserWaitMessage+0xc
1ac6ffec 00000000 kernel32!BaseThreadStart+0x34

  20 Id: 1054.c90 Suspend: 1 Teb: 7ffaf000 Unfrozen
ChildEBP RetAddr
1b30ff50 7739bf53 ntdll!KiFastSystemCallRet
1b30ffb8 77e6482f user32!NtUserWaitMessage+0xc
1b30ffec 00000000 kernel32!BaseThreadStart+0x34

  21 Id: 1054.a34 Suspend: 1 Teb: 7ff9a000 Unfrozen
ChildEBP RetAddr
1b63ff50 7739bf53 ntdll!KiFastSystemCallRet
1b63ffb8 77e6482f user32!NtUserWaitMessage+0xc
1b63ffec 00000000 kernel32!BaseThreadStart+0x34

  22 Id: 1054.1584 Suspend: 1 Teb: 7ff99000 Unfrozen
ChildEBP RetAddr
1ba9ff50 7739bf53 ntdll!KiFastSystemCallRet
1ba9ffb8 77e6482f user32!NtUserWaitMessage+0xc
1ba9ffec 00000000 kernel32!BaseThreadStart+0x34

[...]
```

这些栈跟踪从 RetAddr 分析角度来看是正确的：

```
0:000> ub 7739bf53
user32!PeekMessageW+0x11e:
7739bf42 nop
7739bf43 nop
7739bf44 nop
7739bf45 nop
7739bf46 nop
user32!NtUserWaitMessage:
7739bf47 mov eax,1244h
7739bf4c mov edx,offset SharedUserData!SystemCallStub (7ffe0300)
7739bf51 call dword ptr [edx]
```

```
0:000> ub 77e6482f
kernel32!BaseThreadStart+0x10:
77e6480b mov eax,dword ptr fs:[00000018h]
77e64811 cmp dword ptr [eax+10h],1E00h
77e64818 jne kernel32!BaseThreadStart+0x2e (77e64829)
77e6481a cmp byte ptr [kernel32!BaseRunningInServerProcess (77ecb008)],0
77e64821 jne kernel32!BaseThreadStart+0x2e (77e64829)
77e64823 call dword ptr [kernel32!_imp__CsrNewThread (77e4132c)]
77e64829 push dword ptr [ebp+0Ch]
77e6482c call dword ptr [ebp+8]
```

查看它们的线程时间表明它们是最主要的飙升者：

```
0:000> !runaway
User Mode Time
Thread Time
19:1430 0 days 0:01:34.109
22:1584 0 days 0:01:28.140
21:a34 0 days 0:01:26.765
20:c90 0 days 0:01:24.218
0:e78 0 days 0:00:01.687
10:398 0 days 0:00:01.062
7:14e8 0 days 0:00:00.250
4:1258 0 days 0:00:00.093
6:2e8 0 days 0:00:00.015
1:11c0 0 days 0:00:00.015
26:1328 0 days 0:00:00.000
25:7ec 0 days 0:00:00.000
[ ... ]
```

为了推测可能的罪魁祸首组件，我们查看其原始堆栈数据上留下的执行残留（第 371 页）。确实，我们看到大量指向 3rdPartyExtension 模块的非巧合符号信息引用（第 137 页）：
