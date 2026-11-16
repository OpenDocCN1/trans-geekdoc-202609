

## 调度级自旋

飙升线程模式（第 900 页）包括在 PASSIVE_LEVEL 或 APC_LEVEL IRQL 下运行的普通线程，这些线程可能会被任何其他优先级更高的线程抢占。因此，飙升线程在保存内存转储时不一定处于 RUNNING 状态。它们消耗了大量 CPU，这一点体现在其用户时间和内核时间值中。该模式还包括在 DISPATCH_LEVEL 和更高 IRQL 下运行的线程。这些线程不能被其他线程抢占，因此除非降低 IRQL，否则通常始终处于 RUNNING 状态。其中一些线程可能正在尝试获取自旋锁，因此我们需要针对它们的更专门的模式。当某些数据结构的自旋锁未被释放或已损坏，并且某个线程尝试获取它并进入无限自旋循环，除非被更高 IRQL 中断打断，否则我们会看到这种情况。这些无限循环也可能由于在调度级或更高 IRQL 下运行的代码中存在软件缺陷而发生。

让我们看一个示例。以下运行线程显然被键盘中断打断，以保存手动转储（第 625 页）。我们看到它在内核中花费了近 11 分钟：

```
0: kd> !thread
THREAD 830c07c0 Cid 0588.0528 Teb: 7ffa3000 Win32Thread: e29546a8 RUNNING on processor 0
Not impersonating
DeviceMap    e257b7c8
Owning Process    831ec608    Image:    MyApp.EXE
Wait Start TickCount    122850    Ticks: 40796 (0:00:10:37.437)
Context Switch Count    191    LargeStack
UserTime    00:00:00.000
KernelTime    00:10:37.406
Win32 Start Address MyApp!ThreadImpersonation (0x35f76821)
Start Address kernel32!BaseThreadStartThunk (0x7c810659)
Stack Init a07bf000 Current a07beca0 Base a07bf000 Limit a07bb000 Call 0
Priority 11 BasePriority 8 PriorityDecrement 2 DecrementCount 16
ChildEBP RetAddr
a07be0f8 f77777fa nt!KeBugCheckEx+0x1b
a07be114 f7777032 i8042prt!I8xProcessCrashDump+0x237
a07be15c 805448e5 i8042prt!I8042KeyboardInterruptService+0x21c
a07be15c 806e4a37 nt!KiInterruptDispatch+0x45 (FPO: [0,2] TrapFrame @ a07be180)
a07be220 a1342755 hal!KeAcquireInStackQueuedSpinLock+0x47
a07be220 a1342755 MyDriver!RcvData+0x98
```

要查看代码和上下文，我们切换到陷阱帧⁴⁴并反汇编被中断的函数：

```
1: kd> .trap a07be180
ErrCode = 00000000
eax=a07be200 ebx=a07be228 ecx=831dabf5 edx=a07beb94 esi=831d02a8 edi=831dabd8
eip=806e4a37 esp=a07be1f4 ebp=a07be220 iopl=0 nv up ei pl nz na po nc
cs=0008 ss=0010 ds=0000 es=0000 fs=0000 gs=0000 efl=00000202
hal!KeAcquireInStackQueuedSpinLock+0x47:
806e4a37 ebf3    jmp    hal!KeAcquireInStackQueuedSpinLock+0x3c (806e4a2c)
```

44 中断帧和堆栈重建，内存转储分析文选，第 1 卷，第 83 页

```
1: kd> uf hal!KeAcquireInStackQueuedSpinLock
hal!KeAcquireInStackQueuedSpinLock:
806e49f0 mov     eax,word ptr ds:[FFFE0080h]
806e49f5 shr     eax,4
806e49f8 mov     al,byte ptr hal!HalpVectorToIRQL (806ef218)[eax]
806e49fe mov     dword ptr ds:[0FFFE0080h],41h
806e4a08 mov     byte ptr [edx+8],al
806e4a0b mov     dword ptr [edx+4],ecx
806e4a0e mov     dword ptr [edx],0
806e4a14 mov     eax,edx
806e4a16 xchg    edx,dword ptr [ecx]
806e4a18 cmp     edx,0
806e4a1b jne     hal!KeAcquireInStackQueuedSpinLock+0x34 (806e4a24)

[...]

hal!KeAcquireInStackQueuedSpinLock+0x34:
806e4a24 or      ecx,1
806e4a27 mov     dword ptr [eax+4],ecx
806e4a2a mov     dword ptr [edx],eax

hal!KeAcquireInStackQueuedSpinLock+0x3c:
806e4a2c test    dword ptr [eax+4],1
806e4a33 je      hal!KeAcquireInStackQueuedSpinLock+0x33 (806e4a23)

hal!KeAcquireInStackQueuedSpinLock+0x45:
806e4a35 pause
806e4a37 jmp     hal!KeAcquireInStackQueuedSpinLock+0x3c (806e4a2c)
```

JMP 指令将执行传递到测试 [EAX+4] 地址处第一个位的代码。如果未设置该位，代码会顺序执行到同一条 JMP 指令。我们从陷阱帧中知道 EAX 的值，因此可以解引用该地址：

```
1: kd> dyd eax+4 11
    3       2       1       0
    3
10987654 32109876 54321098 76543210
------------- ------------- -------------
a07be204 10000001 00011101 10101011 11110101 831dabf5
```

该值为奇数：最左边的第一位已设置。因此，除非另一个处理器上运行的其他线程清除该位，否则代码会无限循环。然而，第二个处理器处于空闲状态：

```
0: kd> ~0s

0: kd> k
ChildEBP RetAddr
f794cd54 00000000 nt!KiIdleLoop+0x14
```

看来我们遇到了问题。我们需要检查 MyDriver.sys 代码，以了解它如何使用排队自旋锁。

**注**：除了用户定义的自旋锁外，还有内部系统排队自旋锁，可以使用 !qlocks WinDbg 命令进行检查。

## 分布式异常

### 托管代码

托管代码嵌套异常（第 723 页）为我们提供了进程虚拟空间绑定的堆栈跟踪。但是，异常对象可能会被跨进程甚至跨计算机封送。远程堆栈跟踪返回地址在不同进程上下文中不具有相同的有效性。幸运的是，异常对象中有一个 __remoteStackTraceString 字段，它包含原始堆栈跟踪。默认分析命令有时会使用它：

```
0:013> !analyze -v

[...]

EXCEPTION_OBJECT: !pe 25203b0
Exception object: 00000000025203b0
Exception type: System.Reflection.TargetInvocationException
Message: Exception has been thrown by the target of an invocation.
InnerException: System.Management.Instrumentation.WmiProviderInstallationException, Use !PrintException 000000002522cf0 to see more.
Stack Trace (generated):
SP IP Function
000000001D39E720 0000000000000001 Component!Proxy.Start()+0x20
000000001D39E720 000007FEFF503D0B mscorlib_ni!System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object, Boolean)+0x286
000000001D39E880 000007FEFF503E1A mscorlib_ni!System.Threading.ExecutionContext.Run(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object, Boolean)+0xa
000000001D39E880 000007FEFF503CD8 mscorlib_ni!System.Threading.ExecutionContext.Run(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object)+0x58
000000001D39E900 000007FEFF4FB002 mscorlib_ni!System.Threading.ThreadHelper.ThreadStart()+0x52

[...]

MANAGED_STACK_COMMAND: ** Check field _remoteStackTraceString **;!do 2522cf0;!do 2521900

[...]

0:013> !DumpObj 2522cf0

[...]
000007fef51b77f0 4000054 2c System.String 0 instance 2521900 _remoteStackTraceString

[...]

0:013> !DumpObj 2521900
Name: System.String
[...]
String: at System.Management.Instrumentation.InstrumentationManager.RegisterType(Type managementType) at Component.Provider..ctor() at Component.Start()
```

检查此字段对于来自托管空间执行残留（第 369 页）的感兴趣异常也是必要的。我们称此模式为分布式异常。基本思想在以下图表中说明，使用了借用的 UML 表示法（不仅限于两台计算机）：

![](img/d6dfefc8f9ab7106c77a723ff84aaa6d_243_0.png)

异常 CPU 消耗检测通常在进程级别进行，例如使用任务管理器检测时。有时该进程中许多线程中只有一个**飙升线程**（第 888 页），但也有 CPU 消耗分布在许多线程中的情况。我们称此模式为**分布式飙升**。这种行为可能是弱**耦合进程**（第 151 页）的结果，例如，在这两个服务中（为简化起见，我们将粗体显示用户模式下 CPU 时间超过 1 秒的线程）：

0:000> !runaway

用户模式时间

| 线程 | 时间 |
|--------|------|
| 120:4e518 | 0 days 0:05:09.937 |
| 126:531bc | 0 days 0:03:56.546 |
| 44:334c | 0 days 0:03:40.765 |
| 133:4fe1c | 0 days 0:03:31.156 |
| 45:42b4 | 0 days 0:03:27.328 |
| 107:25ae0 | 0 days 0:03:19.921 |
| 49:627c | 0 days 0:02:48.250 |
| 147:6b90c | 0 days 0:02:33.046 |
| 136:6620c | 0 days 0:02:05.109 |
| 127:4f2d0 | 0 days 0:02:04.046 |
| 129:5bc30 | 0 days 0:02:02.171 |
| 48:623c | 0 days 0:02:01.796 |
| 119:41f00 | 0 days 0:02:00.562 |
| 74:cd18 | 0 days 0:01:59.453 |
| 51:7a4c | 0 days 0:01:54.234 |
| 35:21d4 | 0 days 0:01:47.390 |
| 148:326dc | 0 days 0:01:32.640 |
| 123:43c8c | 0 days 0:01:32.515 |
| 135:67b08 | 0 days 0:01:32.296 |
| 11:aa8 | 0 days 0:01:30.906 |
| 118:4f28c | 0 days 0:01:20.265 |
| 42:3a3c | 0 days 0:01:20.000 |
| 77:d024 | 0 days 0:01:19.734 |
| 115:3a4b0 | 0 days 0:01:15.625 |
| 89:145f4 | 0 days 0:01:10.500 |
| 157:4e310 | 0 days 0:01:07.625 |
| 80:d07c | 0 days 0:01:07.468 |
| 33:1ab0 | 0 days 0:01:00.593 |
| 117:10bd4 | 0 days 0:00:59.421 |
| 151:1aaa0 | 0 days 0:00:59.015 |
| 28:17bc | 0 days 0:00:58.796 |
| 83:f3a4 | 0 days 0:00:55.828 |
| 122:41964 | 0 days 0:00:55.578 |
| 149:4101c | 0 days 0:00:55.234 |
| 10:aa4 | 0 days 0:00:52.453 |
| 106:21b80 | 0 days 0:00:51.187 |
| 132:62e5c | 0 days 0:00:49.437 |
| 160:3a3a8 | 0 days 0:00:48.875 |
| 137:6bf90 | 0 days 0:00:48.687 |
| 145:6f594 | 0 days 0:00:47.968 |
| 143:58d60 | 0 days 0:00:45.703 |
| 72:ba64 | 0 days 0:00:44.515 |

