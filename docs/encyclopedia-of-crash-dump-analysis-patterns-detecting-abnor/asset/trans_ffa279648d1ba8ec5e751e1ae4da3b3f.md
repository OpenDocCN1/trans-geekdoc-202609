

## 第二版前言

距上一版出版已过去两年，在发布《内存转储分析选集》第8b、9a和9b卷（包含包括Linux变体在内的新内存分析模式）后，我们决定出版更新版。新版现包含超过50个新模式和模式变体，其中包括撰写本文时即将出版的第10a卷中的5个分析模式，以及超过70条新注释。WinDbg输出和代码部分已重新格式化，以便于屏幕和平装书阅读。部分笔误已更正，标点符号也已改进。

除第一版前言中提供的联系方式外，我们还建议关注以下Facebook页面和群组：

- http://www.facebook.com/DumpAnalysis
- http://www.facebook.com/groups/dumpanalysis

## 致谢

特别感谢Igor Dzyubenko为第二版提出修正和改进建议，感谢João Roque，以及Malcolm McCaffery在首版发布后提供了鼓励性支持，感谢软件诊断库用户为评论部分做出贡献，感谢软件诊断服务培训课程和参考资料的客户为延续本项目提供了资助。

## 关于作者

![](img/d6dfefc8f9ab7106c77a723ff84aaa6d_47_0.png)

Dmitry Vostokov是一位国际公认的专家、演讲者、教育家、科学家和作者。他是面向模式的软件诊断、取证和预测学科以及软件诊断研究所（DA+TA：DumpAnalysis.org + TraceAnalysis.org）的创始人。Vostokov还撰写了30多本关于软件诊断、取证和问题解决、内存转储分析、调试、软件跟踪和日志分析、逆向工程以及恶意软件分析的书籍。他在包括领导、技术和人员管理角色在内的多个行业拥有超过20年的软件架构、设计、开发和维护经验。

Dmitry还创立了DiaThings、Logtell ect、OpenTask迭代与增量出版（OpenTask.com）、软件诊断服务（原内存转储分析服务PatternDiagnostics.com和Software Prognostics）。在业余时间，他会在Debugging.TV上介绍各种主题，并探索他所开创的软件叙事学（Software Narratology，一种软件故事的应用科学）及其进一步发展——事物叙事学（Narratology of Things）和事物诊断（Diagnostics of Things，DoT）。他目前的研究兴趣是理论软件诊断。

## 缩写转储

有时我们会得到难以完整分析的内存转储，因为保存时省略了部分（甚至大部分）信息。这些通常是小内存转储（与内核转储和完整转储相对）以及用户进程小型转储。当我们打开转储文件时，可以轻松识别出这种情况：

```
User Mini Dump File: Only registers, stack and portions of memory are available
Mini Kernel Dump File: Only registers and stack trace are available
```

同样适用于省略线程时间信息的用户转储（无法使用!runaway WinDbg命令），或使用.dump命令的各种选项（包括privacy-aware1）而不是/ma或已弃用的/f选项保存的转储。相反，崩溃转储中被手动擦除的数据2更像是另一种称为Lateral Damage（第602页）模式的示例。

缩写转储的类似情况在Wrong Dump3和Missing Space4反模式中有所讨论。

无论如何，我们不应该忽略此类转储文件，而应尝试分析它们。例如，一些方法（包括使用镜像二进制文件）在内核小型转储分析系列5中有列出。在寻找执行残留（第371页）时，我们甚至可以看到部分原始堆栈数据：

```
0: kd> !thread
GetPointerFromAddress: unable to read from 81d315b0
THREAD 82f49020 Cid 0004.0034 Teb: 00000000 Win32Thread: 00000000 RUNNING on processor 0
IRP List:
Unable to read nt!_IRP @ 8391e008
Not impersonating
GetUlongFromAddress: unable to read from 81d0ad90
Owning Process 82f00ab0 Image: System
Attached Process N/A Image: N/A
ffff0000: Unable to get shared data
Wait Start TickCount 4000214
Context Switch Count 21886
ReadMemory error: Cannot get nt!KeMaximumIncrement value.
UserTime                    00:00:00.000
KernelTime                  00:00:00.000
Win32 Start Address nt!ExpWorkerThread (0x81c78ea3)
Stack Init 85be0000 Current 85bdf7c0 Base 85be0000 Limit 85bdd000 Call 0
Priority 14 BasePriority 12 PriorityDecrement 0 IoPriority 2 PagePriority 5
[...]

0: kd> dps 85bdd000 85be0000
85bdd000 ????????
85bdd004 ????????
85bdd008 ????????
85bdd00c ????????
85bdd010 ????????
85bdd014 ????????
85bdd018 ????????
85bdd01c ????????
[...]
85bdfc4 ????????
85bdfc8 ????????
85bdfcc ????????
85bdfd0 0000000a
85bdfd4 a112883e
85bdfd8 0000001b
85bdfdc 00000000
85bdfe0 81c28750 nt!KeSetEvent+0x4d
85bdfe4 85bdf8e8
85bdfe8 85bdf970
85bdfe8 81c28750 nt!KeSetEvent+0x4d
85bdff0 badb0d00
85bdff4 00000000
85bdff8 00000000
85bdffc 81cf4820 nt!KiInitialPCR+0x120
85bdf00 00000000
85bdf04 85bdf938
85bdf08 81cf4820 nt!KiInitialPCR+0x120
85bdf0c 00000000
85bdf10 81d32300 nt!OpTimerLock
85bdf14 00000000
85bdf18 81fa0000 nt!_NULL_IMPORT_DESCRIPTOR <PERF> (nt+0x3a0000)
85bdf1c 85bd0023
85bdf20 00000023
85bdf24 00000000
85bdf28 81d323c0 nt!KiDispatcherLock
85bdf2c a1128828
85bdf30 85bdf9b4
85bdf34 85bdfdb0
85bdf38 00000030
85bdf3c 84ca6f40
85bdf40 84ca6f38
85bdf44 00000001
85bdf48 85bdf970
85bdf4c 00000000
85bdf50 81c28750 nt!KeSetEvent+0x4d
85bdf54 00000008
85bdf58 00010246
85bdf5c 00000000
85bdf960 84ca68a0
[...]
85bdfd2c 82f49020
85bdfd30 835ca4d0
85bdfd34 a6684538
85bdfd38 81cfde7c nt!ExWorkerQueue+0x3c
85bdfd3c 00000001
85bdfd40 00000000
85bdfd44 85bdfd7c
85bdfd48 81c78fa0 nt!ExpWorkerThread+0xfd
85bdfd4c 835ca4d0
85bdfd50 00000000
85bdfd54 82f49020
85bdfd58 00000000
85bdfd5c 00000000
85bdfd60 0069000b
85bdfd64 00000000
85bdfd68 00000001
85bdfd6c 00000000
85bdfd70 835ca4d0
85bdfd74 81da9542 nt!PnpDeviceEventWorker
85bdfd78 00000000
85bdfd7c 85bdfd0c
85bdfd80 81e254e0 nt!PspSystemThreadStartup+0x9d
85bdfd84 835ca4d0
85bdfd88 85bdf4680
85bdfd8c 00000000
85bdfd90 00000000
85bdfd94 00000000
85bdfd98 00000002
85bdfd9c 00000000
85bdfda0 00000000
85bdfda4 00000001
85bdfda8 85bdfd88
85bdfdac 85bdfdbc
85bdfdb0 ffffffff
85bdfdb4 81c8aa5d nt!_except_handler4
85bdfdb8 81c9ddb8 nt!'string'+0x4
85bdfdbc 00000000
85bdfdc0 00000000
85bdfdc4 81c9159e nt!KiThreadStartup+0x16
85bdfdc8 81c78ea3 nt!ExpWorkerThread
85bdfdcc 00000001
85bdfdd0 00000000
85bdfdd4 00000000
85bdfdd8 002e0069
85bdfddc 006c0064
85bdfde0 004c006c
85bdfde4 00000000
85bdfde8 000007f0
85bdfdec 00010000
85bdfdf0 0000027f
85bdfdf4 00000000
85bdfdf8 00000000
85bdfdfc 00000000
85bdfe00 00000000
85bdfe04 00000000
85bdfe08 00001f80
85bdfe0c 0000ffff
85bdfe10 00000000
85bdfe14 00000000
85bdfe18 00000000
[...]
85bdffec 00000000
85bdfff0 00000000
85bdfff4 00000000
85bdfff8 00000000
85bdfffc 00000000
85be0000 ????????
```

- 1 WinDbg是隐私感知型，《内存转储分析选集》第1卷，第600页
- 2 崩溃转储中的数据隐藏，《内存转储分析选集》第2卷，第397页
- 3 错误转储，《内存转储分析选集》第1卷，第496页
- 4 缺失空间，《内存转储分析选集》第3卷，第138页
- 5 小型转储分析，《内存转储分析选集》第1卷，第43页

用户小型转储在此处类似：

```
0:001> k
ChildEBP RetAddr
099bfe14 7c90daaa ntdll!KiFastSystemCallRet
099bfe18 77e765e3 ntdll!NtReplyWaitReceivePortEx+0xc
099bff80 77e76caf rpcrt4!LRPC_ADDRESS::ReceiveLotsaCalls+0x12a
099bff88 77e76ad1 rpcrt4!RecvLotsaCallsWrapper+0x8
099bffa8 77e76c97 rpcrt4!BaseCachedThreadRoutine+0x79
099bfff4 7c80b729 rpcrt4!ThreadStartRoutine+0x1a
099bfffec 00000000 kernel32!BaseThreadStart+0x37
```

```
0:001> dd 099bfe14
099bfe14 099bfe24 7c90daaa 77e765e3 00000224
099bfe24 099bff74 00000000 2d87a8e 099bff48
099bfe34 fbf58e18 00000400 fd629338 b279dbbc
099bfe44 fd59288b fb58ebc b279dbbc 0c1e002
099bfe54 00000000 00000006 00000001 00000000
099bfe64 e637d218 00000000 00000006 00000006
099bfe74 00000006 e1f76998 e39b8b60 00000000
099bfe84 fbe33c40 00000001 e5ce12f8 b279db9c
```

```
0:001> dd 099bfe14-20
099bfdf4 ???????? ???????? ???????? ????????
099bfe04 ???????? ???????? ???????? ????????
099bfe14 099bfe24 7c90daaa 77e765e3 00000224
099bfe24 099bff74 00000000 2d87a8e 099bff48
099bfe34 fbf58e18 00000040 fd629338 b279dbbc
099bfe44 fd59288b fb58ebc b279dbbc 0c1e002
099bfe54 00000000 00000006 00000001 00000000
099bfe64 e637d218 00000000 00000006 00000006
```

此处作为警告，可以得出结论：小型转储也可能泄露私人信息，特别是在原始堆栈数据中出现ASCII或Unicode缓冲区时。

我们以缩写书为类比，命名了此模式。

