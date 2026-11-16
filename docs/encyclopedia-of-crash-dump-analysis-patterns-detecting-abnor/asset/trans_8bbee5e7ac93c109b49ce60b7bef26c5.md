

## Comments

异常处理程序可能属于已卸载模块（第 1041 页），从而导致栈溢出（第 912 页）：

```
[...]
00000000`018cd4e0 00000000`772b96c5 ntdll!RtlpCallVectoredHandlers+0xac
00000000`018cd550 00000000`772c722a ntdll!RtlDispatchException+0x25
00000000`018cdbf0 000007fe`f992acc0 ntdll!KiUserExceptionDispatcher+0x2e
00000000`018cc188 00000000`772a38bb <Unloaded_ModuleA.dll>+0x3acc0
00000000`018ce190 00000000`772b96c5 ntdll!RtlpCallVectoredHandlers+0xac
00000000`018ce200 00000000`772c722a ntdll!RtlDispatchException+0x25
00000000`018ce8a0 00000000`772b3738 ntdll!KiUserExceptionDispatcher+0x2e
00000000`018cee40 00000000`772b3c64 ntdll!LdrpSearchResourceSection_U+0x16e
00000000`018cef70 00000000`7716e8b0 ntdll!LdrFindResource_U+0x44
00000000`018cefb0 00000000`6eadac42 kernel32!FindResourceExW+0x84
[...]
00000000`018cfef0 00000000`772a6991 kernel32!BaseThreadInitThunk+0xd
00000000`018cfff0 00000000`00000000 ntdll!RtlUserThreadStart+0x1d
```

## Problem Module

有时此模式可帮助进行故障排除。问题模块（包括进程名）是那些由于其增值行为可能会破坏正常软件行为的组件，因此需要采取从轻微配置更改到完全移除等各种故障排除变通方法。典型示例包括终端服务环境中的内存优化服务 173 或 Hooksware（第 1175 页）。我们可以在 !lmv 或 !process 0 0 WinDbg 命令的输出中查看主进程模块。lm 命令将列出进程内存转储中的模块名（例如 DLL），lmk 命令可从内核和完整内存转储中提供内核空间模块（例如驱动程序）列表，而以下命令列出完整内存转储中每个进程的所有用户空间模块：

```
!for_each_process ".process /r /p @#Process; lmu"
```

当然，如果我们对时间戳和模块信息感兴趣，也可以尝试各种 lm 命令变体。

### Comments

我们还可以在堆栈跟踪集合（第 944 页）中搜索问题模块名，例如，在完整内存转储或调试器日志中使用 !stacks 2 ModuleName。

## Problem Vocabulary

快速检查内存转储中是否存在可疑内容的一种方法是将其转换为调试器日志 174，例如堆栈跟踪集合，（第 943 页），并搜索诸如“等待中”、“终止”、“停止”、“互斥体”、“异常”、“临界”、“消息框”和“挂起计数”等文本字符串。当然，词汇表取决于操作系统，可能存在误报，并且会随时间变化。此模式类似于词汇索引软件跟踪分析模式 175。

例如，最近在一个涉及大量 ALPC 等待链（第 1097 页）且存在潜在进程间死锁的完整内存转储中，我们发现了以下具有长等待线程时间（第 1137 页，超出 ALPC 线程等待时间）的线程，指向一个待进一步检查的进程对象：

```
THREAD fffffffa801338b950 Cid 02a0.7498 Teb: 000007ffffd8000 Win32Thread: 0000000000000000 WAIT: (UserRequest) UserMode Non-Alertable
fffffa8012a39b30 ProcessObject
Not impersonating
DeviceMap fffffff8a000080a70
Owning Process fffffff8a0a31d040 Image: smss.exe
Attached Process N/A Image: N/A
Wait Start TickCount 9752080 Ticks: 5334204 (0:23:09:06.937)
Context Switch Count 38
UserTime 00:00:00.000
KernelTime 00:00:00.000
Win32 Start Address ntdll!TppWorkerThread (0x000000007722fcb0)
Stack Init fffffff8020259db0 Current fffffff8020259900
Base fffffff8802025a000 Limit fffffff88020254000 Call 0
Priority 11 BasePriority 11 UnusualBoost 0 ForegroundBoost 0 IoPriority 2 PagePriority 5
Kernel stack not resident.
Child-SP RetAddr Call Site
fffff880`20259492 fffff800`01693f92 nt!KiSwapContext+0x7a
fffff880`20259a80 fffff800`016967af nt!KiCommitThreadWait+0x1d2
fffff880`20259b10 fffff800`01984b2e nt!KeWaitForSingleObject+0x19f
fffff880`20259bb0 fffff800`0168df93 nt!NtWaitForSingleObject+0xde
fffff880`20259c20 00000000`7726135a nt!KiSystemServiceCopyEnd+0x13 (TrapFrame @ fffff880`20259c20)
00000000`048f648 00000000`48026517 ntdll!NtWaitForSingleObject+0xa
00000000`048f650 00000000`480269c4 smss!SmpTerminateCSR+0xa3
00000000`048f6a0 00000000`48023670 smss!SmpStopCsr+0x44
00000000`048f6d0 00000000`77288137 smss!SmpApiCallback+0x338
00000000`048f900 00000000`7722feff ntdll! ?? ::FNODOBFM::`string'+0x1f718
00000000`048f990 00000000`77274a00 ntdll!TppWorkerThread+0x3f8
00000000`048fc90 00000000`00000000 ntdll!RtlUserThreadStart+0x25
```

在此进程中，我们可以看到阻塞模块（第 96 页），并建议联系其供应商。

## Process Factory

在 PDP-11 系统编程的旧日子里，我们学习了生成进程的系统调用，并用汇编语言编写了一个会自行生成自身的程序。这种递归生成导致运行任务呈几何级数增长，并迅速使 RSX-11M 系统陷入停顿。最近，我们在一个内存转储中观察到了类似的非递归 **进程工厂** 模式：资源管理器不断地创建 *application.exe* 进程，等到有人注意到某种影响时，已有超过 5,000 个此类进程：

```
1: kd> !vm
[...]
5d20 application.exe 212 ( 848 Kb)
5d08 application.exe 212 ( 848 Kb)
5d04 application.exe 212 ( 848 Kb)
5cf8 application.exe 212 ( 848 Kb)
5cf0 application.exe 212 ( 848 Kb)
5ce8 application.exe 212 ( 848 Kb)
5cdc application.exe 212 ( 848 Kb)
5ccc application.exe 212 ( 848 Kb)
5cc8 application.exe 212 ( 848 Kb)
5cc0 application.exe 212 ( 848 Kb)
5ca8 application.exe 212 ( 848 Kb)
5c9c application.exe 212 ( 848 Kb)
5c98 application.exe 212 ( 848 Kb)
5c90 application.exe 212 ( 848 Kb)
5c88 application.exe 212 ( 848 Kb)
5c7c application.exe 212 ( 848 Kb)
5c70 application.exe 212 ( 848 Kb)
5c68 application.exe 212 ( 848 Kb)
5c64 application.exe 212 ( 848 Kb)
5c60 application.exe 212 ( 848 Kb)
5c50 application.exe 212 ( 848 Kb)
5c4c application.exe 212 ( 848 Kb)
5c44 application.exe 212 ( 848 Kb)
5c3c application.exe 212 ( 848 Kb)
5c34 application.exe 212 ( 848 Kb)
5c2c application.exe 212 ( 848 Kb)
5c24 application.exe 212 ( 848 Kb)
5c1c application.exe 212 ( 848 Kb)
5bf8 application.exe 212 ( 848 Kb)
5be0 application.exe 212 ( 848 Kb)
5bd4 application.exe 212 ( 848 Kb)
5bd0 application.exe 212 ( 848 Kb)
5ba4 application.exe 212 ( 848 Kb)
5b58 application.exe 212 ( 848 Kb)
5b50 application.exe 212 ( 848 Kb)
5b44 application.exe 212 ( 848 Kb)
5b38 application.exe 212 ( 848 Kb)
5b30 application.exe 212 ( 848 Kb)
5b04 application.exe 212 ( 848 Kb)
5af4 application.exe 212 ( 848 Kb)
5ad8 application.exe 212 ( 848 Kb)
5ad4 application.exe 212 ( 848 Kb)
5ac8 application.exe 212 ( 848 Kb)
5ac4 application.exe 212 ( 848 Kb)
5ab4 application.exe 212 ( 848 Kb)
5aa4 application.exe 212 ( 848 Kb)
5a9c application.exe 212 ( 848 Kb)
5a94 application.exe 212 ( 848 Kb)
5a8c application.exe 212 ( 848 Kb)
5a88 application.exe 212 ( 848 Kb)
5a74 application.exe 212 ( 848 Kb)
[...]

1: kd> !process 0 0
**** NT ACTIVE PROCESS DUMP ****
PROCESS 8b57f020 SessionId: none Cid: 0004 Peb: 00000000 ParentCid: 0000
    DirBase: cffb3020 ObjectTable: e1003da0 HandleCount: 3932.
    Image: System

PROCESS 8a9fd888 SessionId: none Cid: 01b8 Peb: 7ffdf000 ParentCid: 0004
    DirBase: cffb3040 ObjectTable: e13e3f68 HandleCount: 111.
    Image: smss.exe

PROCESS 89f0d508 SessionId: 0 Cid: 01f0 Peb: 7ffd8000 ParentCid: 01b8
    DirBase: cffb3060 ObjectTable: e16bc370 HandleCount: 1292.
    Image: csrss.exe

PROCESS 89eea7c8 SessionId: 0 Cid: 0208 Peb: 7ffde000 ParentCid: 01b8
    DirBase: cffb3080 ObjectTable: e14b4160 HandleCount: 564.
    Image: winlogon.exe

[...]

PROCESS 8607c020 SessionId: 1 Cid: 44c8 Peb: 7ffdc000 ParentCid: 4cf8
    DirBase: cffb7080 ObjectTable: e3c9fd38 HandleCount: 25407.
    Image: explorer.exe

[...]

PROCESS 85e1d020 SessionId: 1 Cid: 538c Peb: 7ffda000 ParentCid: 44c8
    DirBase: cffb8980 ObjectTable: e8065b20 HandleCount: 39.
    Image: application.exe

PROCESS 85c74610 SessionId: 1 Cid: 5394 Peb: 7ffd9000 ParentCid: 44c8
    DirBase: cffb89a0 ObjectTable: e6951878 HandleCount: 39.
    Image: application.exe

PROCESS 85c81020 SessionId: 1 Cid: 53a4 Peb: 7ffd7000 ParentCid: 44c8
    DirBase: cffb89c0 ObjectTable: e6d2f600 HandleCount: 39.
    Image: application.exe

PROCESS 85c6fb18 SessionId: 1 Cid: 53a8 Peb: 7ffd7000 ParentCid: 44c8
    DirBase: cffb89e0 ObjectTable: e54df078 HandleCount: 39.
    Image: application.exe
```

