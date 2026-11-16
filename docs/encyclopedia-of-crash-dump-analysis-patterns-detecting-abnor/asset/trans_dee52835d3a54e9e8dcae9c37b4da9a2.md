

```
managed thread. You can run !threads to get a list of managed threads in
the process
OS Thread Id: 0x36fc (2)
Child SP IP       Call Site
03c2fb78 779b0f34 [DebuggerU2MCatchHandlerFrame: 03c2fb78]
OS Thread Id: 0x3700 (3)
Child SP IP       Call Site
0470f0cc 779b0f34 [InlinedCallFrame: 0470f0cc]
0470f0c8 69938b07 DomainNeutralILStubClass.IL_STUB_PInvoke(Microsoft.Win32.SafeHandles.SafePipeHandle,
IntPtr)
0470f0cc 699cc07c [InlinedCallFrame: 0470f0cc]
Microsoft.Win32.UnsafeNativeMethods.ConnectNamedPipe(Microsoft.Win32.SafeHandles.SafePipeHandle, IntPtr)
0470f130 699c0c7c System.IO.Pipes.NamedPipeServerStream.WaitForConnection()
0470f140 003c31ed LINQPad.Program.Listener()
0470f1d8 6b64ae5b System.Threading.ThreadHelper.ThreadStart_Context(System.Object)
0470f1e8 6b5d7ff4 System.Threading.ExecutionContext.Run(System.Threading.ExecutionContext,
System.Threading.ContextCallback, System.Object, Boolean)
0470f20c 6b5d7f34 System.Threading.ExecutionContext.Run(System.Threading.ExecutionContext,
System.Threading.ContextCallback, System.Object)
0470f228 6b64ade8 System.Threading.ThreadHelper.ThreadStart()
0470f44c 6c1721db [GCFrame: 0470f44c]
0470f710 6c1721db [DebuggerU2MCatchHandlerFrame: 0470f710]

OS Thread Id: 0x3704 (4)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process

OS Thread Id: 0x3710 (5)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process

OS Thread Id: 0x3714 (6)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process

OS Thread Id: 0x3718 (7)
Child SP IP       Call Site
0596ee40 779b0f34 [GCFrame: 0596ee40]
0596ef34 779b0f34 [HelperMethodFrame_1OBJ: 0596ef34] System.Threading.Monitor.ObjWait(Boolean, Int32,
System.Object)
0596ef90 6b5d91d0 System.Threading.Monitor.Wait(System.Object, Int32, Boolean)
0596efa0 6bb9428a System.Threading.Monitor.Wait(System.Object)
0596fefa 003cb55a ActiproSoftware.SyntaxEditor.SemanticParserService.c()
0596f068 6b64ae5b System.Threading.ThreadHelper.ThreadStart_Context(System.Object)
0596f078 6b5d7ff4 System.Threading.ExecutionContext.Run(System.Threading.ExecutionContext,
System.Threading.ContextCallback, System.Object, Boolean)
0596f09c 6b5d7f34 System.Threading.ExecutionContext.Run(System.Threading.ExecutionContext,
System.Threading.ContextCallback, System.Object)
0596f08b 6b64ade8 System.Threading.ThreadHelper.ThreadStart()
0596f2dc 6c1721db [GCFrame: 0596f2dc]
0596f5a0 6c1721db [DebuggerU2MCatchHandlerFrame: 0596f5a0]
OS Thread Id: 0x3764 (8)
Child SP IP       Call Site
0564f148 779b0f34 [HelperMethodFrame_1OBJ: 0564f148]
System.Threading.WaitHandle.WaitOneNative(System.Runtime.InteropServices.SafeHandle, UInt32, Boolean,
Boolean)
0564f1f0 6b64b5ef System.Threading.WaitHandle.InternalWaitOne(System.Runtime.InteropServices.SafeHandle,
Int64, Boolean, Boolean)
0564f20c 6b64b5ad System.Threading.WaitHandle.WaitOne(Int32, Boolean)
0564f224 6b64b570 System.Threading.WaitHandle.WaitOne()
0564f22c 04b607d4 ActiproBridge.ReferenceManager+?15?.<StartAdvanceFeeder>b__4()
0564f268 6b64ae5b System.Threading.ThreadHelper.ThreadStart_Context(System.Object)
0564f278 6b5d7ff4 System.Threading.ExecutionContext.Run(System.Threading.ExecutionContext,
System.Threading.ContextCallback, System.Object, Boolean)
0564f29c 6b5d7f34 System.Threading.ExecutionContext.Run(System.Threading.ExecutionContext,
System.Threading.ContextCallback, System.Object)
0564f2b8 6b64ade8 System.Threading.ThreadHelper.ThreadStart()
0564f4dc 6c1721db [GCFrame: 0564f4dc]
0564f7a0 6c1721db [DebuggerU2MCatchHandlerFrame: 0564f7a0]
OS Thread Id: 0x3768 (9)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
OS Thread Id: 0x376c (10)
Child SP               Call Site
GetFrameContext failed: 1
OS Thread Id: 0x3798 (11)
Child SP               Call Site
GetFrameContext failed: 1
OS Thread Id: 0x37e0 (12)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
OS Thread Id: 0x37f8 (13)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
```

## 谓词

有时候，我们需要将常规堆栈跟踪收集范围缩小到满足某些谓词^198 的少数线程，例如，内核时间花费大于某个值的所有线程，或所有挂起的线程，或等待特定同步对象类型的所有线程。这可以使用 WinDbg 脚本^199 和调试器扩展来实现。

## 注释

这里的一个示例可以是 TEB.SubProcessTag 中的服务标记，用于识别 svchost.exe 中特定服务的线程。

要列出特定 WOW64 进程的 32 位堆栈跟踪：

```
!for_each_thread ".thread @#Thread; r $t0 = @#Thread; .if (@@c++(((nt!_KTHREAD *)@$t0)->Process) == ProcessAddress) {.thread /w @#Thread; .reload; kv 256; .effmach AMD64 }"
```

198 http://en.wikipedia.org/wiki/Predicate_(mathematical_logic)

199 Two WinDbg Scripts That Changed the World, Memory Dump Analysis Anthology, Volume 7, page 32

## 非托管空间

有时，问题不能仅从单个**堆栈跟踪**模式中识别，而需要从**堆栈跟踪集合**中识别。

这些包括**耦合进程**（第 149 页）、**过程调用链** 200 和**阻塞线程**（第 80 页）。此处我们仅讨论列出堆栈跟踪的各种方法。

- 包括各种进程小转储在内的进程转储：
  - ~*kv 命令列出所有进程线程。
  - !findstack module[!symbol] 2 命令筛选所有堆栈跟踪，仅显示包含模块或 module!symbol 的跟踪。
  - !uniqstack 命令。
- 内核小转储：
  - 只有一个问题线程。kv 命令或其变体足够。
- 内核和完整内存转储：
  - !process 0 3f 命令列出所有进程及其线程，包括完整内存转储的用户空间进程线程堆栈。此命令适用于 Windows XP 及更高版本。对于旧系统，可以使用 WinDbg 脚本。
  - !stacks 2 [module[!symbol]] 命令显示内核模式堆栈跟踪，我们可以根据模块或 module!symbol 筛选输出。筛选仅适用于 Windows XP 及更高版本系统的崩溃转储。
  - ~/ProcessorN|s;reload /user;kv 命令序列显示指定处理器上运行线程的堆栈跟踪。

处理器更改命令在此示例中演示：

```
0: kd> ~2s

2: kd> k
ChildEBP RetAddr
eb42bd58 00000000 nt!KiIdleLoop+0x14
```

```
2: kd> ~1s;.reload /user;k
Loading User Symbols
..
ChildEBP RetAddr
be4f8c30 eb091f43 i8042prt!I8xProcessCrashDump+0x53
be4f8c8c 8046bfe2 i8042prt!I8042KeyboardInterruptService+0x15d
be4f8c8c 8049470f nt!KiInterruptDispatch+0x32
be4f8d54 80468389 nt!NtSetEvent+0x71
be4f8d54 77f8290a nt!KiSystemService+0xc9
081cfcfc 77f88266 ntdll!ZwSetEvent+0xb
081cffc0 77f881b1 ntdll!RtlpUnWaitCriticalSection+0x1b
081cff14 1b00c7d1 ntdll!RtlLeaveCriticalSection+0x1d
081cff4c 1b0034da msjet40!Database::ReadPages+0x81
081cffb4 7c57b3bc msjet40!System::WorkerThread+0x115
081cffec 00000000 KERNEL32!BaseThreadStart+0x52
```

### !findstack 命令示例（进程转储）：

```
0:000> !findstack kernel32!RaiseException 2
Thread 000, 1 frame(s) match
* 00 0013b3f8 72e8d3ef kernel32!RaiseException+0x53
01 0013b418 72e9a26b msxml3!Exception::raiseException+0x5f
02 0013b424 72e8ff00 msxml3!Exception::_throwError+0x22
03 0013b46c 72e6abaa msxml3!COMSafeControlRoot::getBaseURL+0x3d
04 0013b4bc 72e6a888 msxml3!Document::loadXML+0x82
05 0013b510 64b73a9b msxml3!DOMDocumentWrapper::loadXML+0x5a
06 0013b538 64b7a4eb6 iepeers!CPersistUserData::initXMLCache+0xa6
07 0013b560 77d0516e iepeers!CPersistUserData::load+0xfc
08 0013b57c 77d14abf oleaut32!DispatchCallFunc+0x16a
...
...
...
66 0013fec8 0040243d shdocvw!IEWinMain+0x129
67 0013ff1c 00402744 iexplore!WinMain+0x316
68 0013ffc0 77e6f23b iexplore!WinMainCRTStartup+0x182
69 0013fff0 00000000 kernel32!BaseProcessStart+0x23
```

### !stacks 命令示例（内核转储）：

```
2: kd> !stacks 2 nt!PspExitThread
Proc.Thread .Thread Ticks ThreadState Blocker
[8a390818 System]
[8a1bbbf8 smss.exe]
[8a16cbf8 csrss.exe]
[89c14bf0 winlogon.exe]
[89dda630 services.exe]
[89c23af0 lsass.exe]
```

