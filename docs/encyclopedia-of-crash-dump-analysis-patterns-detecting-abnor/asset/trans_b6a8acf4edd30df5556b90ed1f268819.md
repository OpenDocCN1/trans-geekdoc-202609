

## 位置痕迹

内存转储中大多数执行残留（第365页）痕迹并非显式的时间性（参见《特殊和一般痕迹与日志分析》第170页），但可能按某些空间坐标排序，例如内存地址或页面帧编号。此外，虚拟空间可进一步细分为模块等位置，物理空间可重新结构化为进程等位置。可使用值引用（第1057页）分析模式构建某些数据值的简单空间痕迹。这些及更高级结构空间痕迹构造可命名为通用位置痕迹分析模式，如本图所示：

![](img/d6dfefc8f9ab7106c77a723ff84aaa6d_803_0.png)

内存属性（如页面保护）或从内存内容派生的属性也可视为位置痕迹数据。有时，通过查看位置容器的时间信息（例如，经过的进程时间或进程列表中的顺序，或堆栈区域线程所有者的线程顺序和时间），可以重建时间顺序。

## 注释

数据也可跨不同线程堆栈区域进行位置痕迹分析。

## 平台特定调试器

分析 .NET 托管代码需要特定于处理器架构平台的 SOS 扩展。例如，x64 WinDbg 无法分析 32 位进程中托管代码异常（第617页）的托管堆栈：

```
0:010> !analyze -v

[...]

FAULTING_IP:
kernel32!RaiseException+53
77e4bee7 5e              pop     esi

EXCEPTION_RECORD:  ffffffff -- (.exr 0xffffffffffffffff)
ExceptionAddress: 77e4bee7 (kernel32!RaiseException+0x00000053)
  ExceptionCode: e0434f4d (CLR exception)
ExceptionFlags: 00000001
NumberParameters: 1
  Parameter[0]: 80131509

[...]

MANAGED_STACK: !dumpstack -EE
No export dumpstack found

MANAGED_BITNESS_MISMATCH:
Managed code needs matching platform of sos.dll for proper analysis. Use 'x86' debugger.

[...]
```

```
0:010> kl 100
ChildEBP RetAddr
0573f0a4 79f071ac kernel32!RaiseException+0x53
0573f104 79f07a80 mscorwks!RaiseTheExceptionInternalOnly+0x2a8
0573f1a8 058ed3b3 mscorwks!JIT_Retthrow+0xbf
WARNING: Frame IP not in any known module. Following frames may be wrong.
0573f33c 793b0d1f <Unloaded_dllA.dll>+0x58ed3b2
0573f344 79373ec3 mscorlib_ni+0x2f0d1f
0573f358 793b0c68 mscorlib_ni+0x2b3ecd
0573f370 79e7c74b mscorlib_ni+0x2f0c68
0573f380 79e7c6cc mscorwks!CallDescrWorker+0x33
0573f400 79e7c8e1 mscorwks!CallDescrWorkerWithHandler+0xa3
0573f53c 79e7c783 mscorwks!MethodDesc::CallDescr+0x19c
0573f558 79e7c90d mscorwks!MethodDesc::CallTargetWorker+0x1f
0573f56c 79fc58cd mscorwks!ThreadNative::KickOffThread_Worker+0x190
0573f754 79ef3207 mscorwks!Thread::DoADCallBack+0x32a
0573f7fc 79ef30c3 mscorwks!Thread::ShouldChangeAbortToUnload+0xe3
0573f838 79ef4826 mscorwks!Thread::ShouldChangeAbortToUnload+0x30a
0573f860 79fc57b1 mscorwks!Thread::ShouldChangeAbortToUnload+0x33e
0573f878 79fc56ac mscorwks!ManagedThreadBase::KickOff+0x13
0573f914 79f95a2e mscorwks!ThreadNative::KickOffThread+0x269
```

```
0573ffb8 77e64829 mscorwks!Thread::intermediateThreadProc+0x49
0573ffec 00000000 kernel32!BaseThreadStart+0x34
```

因此我们运行 x86 WinDbg，获得 **嵌套异常** (第723页) 的更清晰视图：

```
0:010> !analyze -v

[...]

MANAGED_STACK: !dumpstack -EE
OS Thread Id: 0xc68 (15)
Current frame:
ChildEBP RetAddr  Caller,Callee

EXCEPTION_OBJECT: !pe 16584f0
Exception object: 016584f0
Exception type: System.InvalidOperationException
Message: There is an error in XML document (12, 12182).
InnerException: System.IO.IOException, use !PrintException 0164f6dc to see more
[...]

StackTraceString: <none>
HResult: 80131509
There are nested exceptions on this thread. Run with -nested for details

EXCEPTION_OBJECT: !pe 164f6dc
Exception object: 0164f6dc
Exception type: System.IO.IOException
Message: Unable to read data from the transport connection: The connection was closed.
InnerException: <none>
[...]

StackTraceString: <none>
HResult: 80131620
There are nested exceptions on this thread. Run with -nested for details

MANAGED_OBJECT: !dumpobj 1655a38
Name: System.String
MethodTable: 790fd8c4
EEClass: 790fd824
Size: 270(0x10e) bytes
(C:\WINDOWS\assembly\GAC_32\mscorlib\2.0.0.0__[...]\mscorlib.dll)
String: Unable to read data from the transport connection: The connection was closed.

EXCEPTION_MESSAGE: Unable to read data from the transport connection: The connection was closed.

MANAGED_OBJECT_NAME: System.IO.IOException
```

当我们需要 **平台特定调试器** 时，还有此类模式的其他实例，例如，在 x64 机器上对 x86 进程进行实时调试（我们需要 x64 调试器）或为事后分析加载旧的 32 位 DLL 扩展（我们需要 x86 调试器）。

## 普列阿得斯

这是 lm WinDbg 命令输出中服务于类似功能的模块簇，例如打印缓冲区中的打印驱动程序或 Citrix 打印服务。通常，我们知道其中任何一个都可能出错。另一个示例是完整内存转储中在独立终端服务会话中服务于相同功能的一组进程模块。

## 混淆前残留

此模式与 **打包** (第775页) 和混淆代码密切相关。根据混淆和打包的程度，一些初始代码和数据结构以及包括字符串片段在内的模式可能会在混淆后的数据中泄露，从而揭示预期的软件行为：

```
0:000> s-sa 00000000`00fd4000 L6000
[...]
00000000`00fd943d  "o__"
00000000`00fd9449  "91!We"
00000000`00fd945d  "H5!"
00000000`00fd94d2  "z@!"
00000000`00fd94d4  "commandS"
00000000`00fd94f4  "IsDeb"
00000000`00fd94fd  "uggerP"
00000000`00fd9507  "Enc"
00000000`00fd950c  "v)3Po4t"
00000000`00fd9515  "DeXU"
00000000`00fd9520  "xFe"
00000000`00fd952a  "5Eb"
00000000`00fd9533  "SI=18kev"
00000000`00fd953e  "Z_1m"
00000000`00fd9547  "@IF"
[...]
```

## 问题异常处理程序

此模式通常出现于未按规定规则编写的自定义异常处理程序（例如，针对不可继续异常的处理程序（第171页））或具有常规代码中常见的其他缺陷。请参阅对前者建模的案例研究（第172页）。

在下面示例中，针对类似问题的堆栈跟踪结尾不同，显示了与自定义异常处理程序（第171页）的关系：

```
0:000> kv 1000
ChildEBP RetAddr  Args to Child
0003300c 77af9904 77b8929c 792ea99b 00000000 ntdll!RtlAcquireSRWLockShared+0x1a
00033058 77af9867 00406ef8 00033098 000330a0 ntdll!RtlLookupFunctionTable+0x2a
000330a8 77af97f9 00406ef8 00000000 00000000 ntdll!RtlIsValidHandler+0x26
00033128 77b25dd7 01033140 00033154 00033140 ntdll!RtlDispatchException+0x10b
00033128 77b40726 01033140 00033154 00033140 ntdll!KiUserExceptionDispatcher+0xf (CONTEXT @ 00033154)
00033490 77b25dd7 010334a8 000334bc 000334a8 ntdll!RtlDispatchException+0x18a
00033490 77b40726 010334a8 000334bc 000334a8 ntdll!KiUserExceptionDispatcher+0xf (CONTEXT @ 000334bc)
000337f8 77b25dd7 01033810 00033824 00033810 ntdll!RtlDispatchException+0x18a
[...]
0012f228 77b40726 0112f240 0012f254 0012f240 ntdll!KiUserExceptionDispatcher+0xf (CONTEXT @ 0012f254)
0012f590 77b8fbae 0112f5a8 0012f5d8 0012f5a8 ntdll!RtlDispatchException+0x18a
0012f590 768bfbae 0112f5a8 0012f5d8 0012f5a8 ntdll!KiUserExceptionDispatcher+0xf (CONTEXT @ 0012f5d8)
0012f8f4 0059ecad 0eedfade 00000001 00000007 kernel32!RaiseException+0x58
WARNING: Stack unwind information not available. Following frames may be wrong.
0012f918 74737599 0eedfade 00000001 00000007 Application+0x19ecad
[...]
0012ff88 768cd0e9 7ffdf000 0012ffd4 77b019bb Application+0x70f8
0012ff94 77b019bb 7ffdf000 793f6617 00000000 kernel32!BaseThreadInitThunk+0xe
0012ffd4 77b0198e 011263c0 7ffdf000 ffffffff ntdll!__RtlUserThreadStart+0x23
0012ffec 00000000 011263c0 7ffdf000 00000000 ntdll!_RtlUserThreadStart+0x1b

0:000> !exchain
00033048: ntdll!_except_handler4+0 (77ac99fa)
0012ff78: Application+6ef8 (00406ef8)
0012ffc4: ntdll!_except_handler4+0 (77ac99fa)
0012ffe4: ntdll!FinalExceptionHandler+0 (77b66f9b)
Invalid exception stack at ffffffff
```

