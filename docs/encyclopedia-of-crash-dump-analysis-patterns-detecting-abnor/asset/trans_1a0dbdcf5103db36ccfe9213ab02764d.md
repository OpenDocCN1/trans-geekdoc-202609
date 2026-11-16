

## x64 的另一个示例：

```
0:004> r
rax=0000000000000000 rbx=000000dd5253ce30 rcx=000000d515923a00
rdx=0000000000000000 rsi=0000000000000002 rdi=000000dd5253c940
rip=00007ffd1fbc98cc rsp=000000dd5253d660 rbp=000000dd5253d220
r8=000000dd515923a0 r9=000000000fffffff r10=0000000000000000
r11=000000dd5253d3c8 r12=00007ffd20002460 r13=000000dd636a3101
r14=000000dd51738000 r15=0000000000000c00
iopl=0 nv up ei pl nz na pe nc
cs=0033 ss=002b ds=002b es=002b fs=0053 gs=002b efl=00010200
edghtml!CComWindowProxy::PrivateAddRef+0x3c:
00007ffd`1fbc98cc 488b7868 mov rdi,qword ptr [rax+68h] ds:00000000`00000068=????????????????
```

```
0:004> k
# Child-SP RetAddr Call Site
00 000000dd`5253d060 00007ffd`1fbc9850 edghtml!CComWindowProxy::PrivateAddRef+0x3c
01 000000dd`5253d090 00007ffd`1fbc97eb edghtml!CEventPathBuilder::SetProxy+0x20
02 000000dd`5253d0c0 00007ffd`1fbcb79b edghtml!CEventPathBuilder::AppendWindowTarget+0x47
03 000000dd`5253d0f0 00007ffd`1fbc5189 edghtml!CWindow::BuildEventPath+0x1b
04 000000dd`5253d120 00007ffd`1faec7f1 edghtml!CEventMgr::Dispatch+0x5c9
05 000000dd`5253d3d0 00007ffd`1faeb7cc edghtml!CMessagePort::HandlePostMessage+0x10d
06 000000dd`5253d450 00007ffd`1fc4b667 edghtml!CMessageDispatcher::ProcessNotification+0x5c
07 000000dd`5253d480 00007ffd`1f9d21d1 edghtml!GlobalWndOnPaintPriorityMethodCall+0x457
08 000000dd`5253d570 00007ffd`43a900dc edghtml!GlobalWndProc+0x101
09 000000dd`5253d5f0 00007ffd`43a8fe52 user32!UserCallWinProcCheckWow+0x1fc
0a 000000dd`5253d6e0 00007ffd`43a9d3fe user32!DispatchClientMessage+0xa2
0b 000000dd`5253d740 00007ffd`462f5714 user32!_fnDWORD+0x3e
0c 000000dd`5253d7a0 00007ffd`43aaffba ntdll!KiUserCallbackDispatcherContinue
0d 000000dd`5253d828 00007ffd`43a8fca7 user32!NtUserDispatchMessage+0xa
0e 000000dd`5253d830 00007ffd`19c6ee8e user32!DispatchMessageWorker+0x247
0f 000000dd`5253d8b0 00007ffd`19cd0b8b eModel!CTabWindow::_TabWindowThreadProc+0x5b8
10 000000dd`5253fb10 00007ffd`3630864f eModel!LCIETab_ThreadProc+0x2bb
11 000000dd`5253fc40 00007ffd`45f42d92 iertutil!_IsoThreadProc_WrapperToReleaseScope+0x1f
12 000000dd`5253fc70 00007ffd`46269f64 kernel32!BaseThreadInitThunk+0x22
13 000000dd`5253fc0a 00000000`00000000 ntdll!RtlUserThreadStart+0x34
```

## 对象分布异常

### .NET 堆

有时我们会注意到堆和池（IRP，第 759 页）中对象分布的异常。如果存在大型对象，内存消耗可能会很高。此类异常可能指向可能的内存（第 526 页）、句柄（第 416 页）和对象泄漏。但也可能是临时状况（**内存波动**，第 634 页），由大量排队或推迟的工作引起，可通过适当的软件配置来解决。如果诊断出的异常围绕某些组件或特定功能集中，也可指导故障排除工作。可通过总内存消耗和特定类对象的总数来评估分布情况。

以下是来自 .NET 堆的 **对象分布异常** 分析模式示例。**!DumpHeap -stat** WinDbg SOS 扩展命令的输出显示了与 SQL 数据查询相关的对象的异常分布：

| 计数 | 总大小 | 类型 |
|------|--------|------|
| [...] | | |
| 2342 | 281040 | System.Reflection.RuntimeParameterInfo |
| 3868 | 309440 | System.Data.Metadata.Edm.TypeUsage |
| 13218 | 317232 | System.Object |
| 3484 | 390208 | System.Reflection.RuntimeMethodInfo |
| 6092 | 508044 | System.Int32[] |
| 2756 | 617344 | System.Data.SqlClient._SqlMetaData |
| 2770 | 822870 | System.Char[] |
| 24560 | 1375360 | System.RuntimeType |
| 18 | 4195296 | System.Int64[] |
| 449691 | 10792584 | System.Data.SqlClient.SqlGen.SqlBuilder |
| 449961 | 10799064 | System.Int64 |
| 449691 | 14390112 | System.Data.Query.InternalTrees.ComparisonOp |
| 449695 | 14390240 | System.Data.Query.InternalTrees.ConditionalOp |
| 6360 | 15509435 | System.Byte[] |
| 449690 | 17987600 | System.Data.Query.InternalTrees.ConstantOp |
| 449938 | 17997520 | System.Data.Query.InternalTrees.VarRefOp |
| 450898 | 21643104 | System.Data.Common.CommandTrees.DbPropertyExpression |
| [...] | | |

分布的异常特征也在以下图表中说明：

### 对象数量

![](img/d6dfefc8f9ab7106c77a723ff84aaa6d_756_0.png)

### 对象总大小

![](img/d6dfefc8f9ab7106c77a723ff84aaa6d_757_0.png)

来自挂起或运行缓慢的工作站和服务器的内核或完整内存转储中，!irpfind WinDbg 命令可能会显示 IRP 对象分布异常模式，当某些驱动程序在正常情况下未观察到的大量活动 IRP 时。我们通过使用 Visual Studio 键盘宏预处理命令输出以消除已完成的 IRP，然后使用 Excel，从两个问题内核转储中创建了两个 IRP 分布图。在一个案例中，来自第三方防病毒筛选驱动程序的大量 I/O 请求数据包：

```
\Driver\3rdPartyAvFilter
```

![](img/d6dfefc8f9ab7106c77a723ff84aaa6d_758_0.png)

在第二个案例中，是针对内核套接字辅助功能驱动程序的大量活动 IRP：

\Driver\AFD

![](img/d6dfefc8f9ab7106c77a723ff84aaa6d_759_0.png)

两个图表中的另外两个峰值与 NTPS 和 NTFS、管道和文件系统相关，通常是正常的。

以下是我们在首次撰写此模式时从 Vista 工作站捕获的 IRP 分布图：

![](img/d6dfefc8f9ab7106c77a723ff84aaa6d_759_1.png)

### 注释

此模式以前称为 IRP 分布异常。

## OMAP 代码优化

**OMAP 代码优化**用于缩小需要驻留在内存中的代码大小。因此，对于编译后的函数，不是采用平坦地址空间，而是将其碎片散落在各处。当我们尝试在其地址反汇编 OMAP 代码时，这会导致歧义，因为 WinDbg 不知道是应将地址范围视为函数偏移（从函数源代码开始计算）还是仅视为内存布局偏移（从该函数的地址开始计算）。我们使用 `IoCreateDevice` 函数代码来说明此模式。

让我们首先计算从函数第一个地址开始的随机地址（内存布局偏移）：

```
kd> ? nt!IoCreateDevice
Evaluate expression: -8796073668256 = fffffff800`01275160

kd> ? nt!IoCreateDevice+0x144
Evaluate expression: -8796073667932 = fffffff800`012752a4

kd> ? fffffff800`012752a4-fffff800`01275160
Evaluate expression: 324 = 00000000`00000144
```

如果我们尝试反汇编同一地址处的代码，该表达式也将被评估为内存布局偏移：

```
kd> u nt!IoCreateDevice+0x144
nt!IoCreateDevice+0x1a3:
fffff800`012752a4 or             eax,10h
fffff800`012752a7 mov            dword ptr [rsp+0B0h],eax
fffff800`012752ae test           ebp,ebp
fffff800`012752b0 mov            ebx,ebp
fffff800`012752b2 jne            nt!IoCreateDevice+0x1b3
fffff800`012752b8 add            ebx,dword ptr [rsp+54h]
fffff800`012752bc mov            rdx,qword ptr [nt!IoCreateDeviceObjectType]
fffff800`012752c3 lea            rcx,[rsp+88h]
```

我们可以看到差异：我们给出了 +0x144 偏移，但显示的代码是从 +0x1a3 开始的！这是因为 OMAP 优化将函数偏移 +0x1a3 处的代码移动到从 +0x144 开始的内存位置。下图说明了这一点：

![](img/d6dfefc8f9ab7106c77a723ff84aaa6d_761_0.png)

如果在从线程堆栈跟踪反汇编 *函数名+偏移* 地址时看到这种情况，可以改用原始地址：

```
kd> k
Child-SP RetAddr Call Site
fffffad`e3a18d30 fffff800`012b331e component!function+0x72
fffffad`e3a18d70 fffff800`01044196 nt!PspSystemThreadStartup+0x3e
fffffad`e3a18dd0 00000000`00000000 nt!KxStartSystemThread+0x16

kd> u fffff800`012b331e
nt!PspSystemThreadStartup+0x3e:
fffff800`012b331e nop
fffff800`012b331f test byte ptr [rbx+3FCh],40h
fffff800`012b3326 jne nt!PspSystemThreadStartup+0x4c
fffff800`012b332c mov rax,qword ptr gs:[188h]
fffff800`012b3335 cmp rbx,rax
fffff800`012b3338 jne nt!PspSystemThreadStartup+0x10c
fffff800`012b333e or dword ptr [rbx+3FCh],1
fffff800`012b3345 xor ecx,ecx
```

