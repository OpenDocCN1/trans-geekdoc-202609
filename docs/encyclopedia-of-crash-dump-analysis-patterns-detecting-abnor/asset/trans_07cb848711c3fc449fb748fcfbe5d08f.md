

## 自我诊断

### 内核模式

此模式是用户模式中 **自我诊断**（第 847 页）的内核模式对应物。它只是一组 bugcheck 代码集合，通常在损坏导致故障、异常或陷阱之前检测到问题。典型的示例是检测到失败的断言或 **损坏的结构**（第 144 页），例如：

```
BAD_POOL_HEADER (19)
The pool is already corrupt at the time of the current request.
This may or may not be due to the caller.
The internal pool links must be walked to figure out a possible cause of the problem, and then special pool applied to the suspect tags or the driver verifier to a suspect driver.
Arguments:
Arg1: 00000020, a pool block header size is corrupt.
Arg2: 8b79d078, The pool entry we were looking for within the page.
Arg3: 8b79d158, The next pool entry.
Arg4: 8a1c0004, (reserved)
```

### 注释

另一个示例是这个 bugcheck：

```
CRITICAL_STRUCTURE_CORRUPTION (109)
This bugcheck is generated when the kernel detects that critical kernel code or
data have been corrupted. There are generally three causes for a corruption:
- A driver has inadvertently or deliberately modified critical kernel code
or data. See http://www.microsoft.com/whdc/driver/kernel/64bitPatching.mspx
- A developer attempted to set a normal kernel breakpoint using a kernel
debugger that was not attached when the system was booted. Normal breakpoints,
“bp”, can only be set if the debugger is attached at boot time. Hardware
breakpoints, “ba”, can be set at any time.
- A hardware corruption occurred, e.g. failing RAM holding kernel code or data.
Arguments:
Arg1: [...], Reserved
Arg2: [...], Reserved
Arg3: [...], Failure type dependent information
Arg4: 0000000000000002, Type of corrupted region, can be
    - 0 : A generic data region
    - 1 : Modification of a function or .pdata
    - 2 : A processor IDT
    - 3 : A processor GDT
    - 4 : Type 1 process list corruption
    - 6 : Debug routine modification
    - 5 : Type 2 process list corruption
    - 7 : Critical MSR modification
```

### 注册表

这是针对系统配置数据库（注册表）的 **自我诊断**（内核模式）模式的变体。
有时可以看到是它的哪个部分（配置单元）导致了问题。下面是一个涉及可能损坏用户配置文件的示例：

```
REGISTRY_ERROR (51)
Something has gone badly wrong with the registry. If a kernel debugger is available, get a stack trace.
It can also indicate that the registry got an I/O error while trying to read one of its files, so it can
be caused by hardware problems or filesystem corruption. It may occur due to a failure in a refresh
operation, which is used only in by the security system, and then only when resource limits are
encountered.

Arguments:
Arg1: 00000003, (reserved)
Arg2: 00000004, (reserved)
Arg3: e82372f8, depends on where Windows bugchecked, *may be pointer to hive*
Arg4: 00000000, depends on where Windows bugchecked, may be return code of HvCheckHive if the hive is
corrupt.
```

```
0: kd> !reg hivelist
```

| 蜂窝地址 | 稳定长度 | 稳定映射 | 易失长度 | 易失映射 | 映射视图 | 固定视图 | U(计数) | 基块 | 文件名 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| e1008a68 | 13000 | e1008ac8 | 1000 | e1008c84 | 0 | 0 | 0 | e1015000 | \NONAME |
| e1014e60 | 901000 | e1023800 | 40000 | e101a67c | 202 | 0 | 0 | e1016000 | SYSTEM |
| e1938188 | d000 | e19381e8 | 4000 | e1938324 | 0 | 0 | 0 | e193a000 | \NONAME |
| e1968290 | 8000 | e19682f0 | 0 | 00000000 | 3 | 0 | 0 | e1d39000 | \SystemRoot\System32\Config\SAM |
| e1cab270 | 3d000 | e1cab2d0 | 1000 | e1cab44c | 16 | 0 | 0 | e1d32000 | \SystemRoot\System32\Config\SECURITY |
| e1c9f448 | 3f70000 | e1e37000 | 1000 | e1c9f5e4 | 256 | 0 | 0 | e1d71000 | \SystemRoot\System32\Config\DEFAULT |
| e1d75a80 | 7d50000 | e1ee3000 | 23000 | e1d75c1c | 254 | 12 | 0 | e1d37000 | \SystemRoot\System32\Config\SOFTWARE |
| e1ba30d0 | 37000 | e1ba3130 | 1000 | e1ba326c | 17 | 0 | 0 | e19e0000 | \ings\NetworkService\ntuser.dat |
| e1ba8060 | 1000 | e1ba80c0 | 0 | 00000000 | 1 | 0 | 0 | e1d8e000 | \Microsoft\Windows\UsrClass.dat |
| e1afc068 | 3b000 | e1afc0c8 | 1000 | e1afc204 | 17 | 0 | 0 | e1b3d000 | \ettings\LocalService\ntuser.dat |
| e1de62a0 | 1000 | e1de6300 | 0 | 00000000 | 1 | 0 | 0 | e1d39000 | \Microsoft\Windows\UsrClass.dat |
| [...] | [...] | [...] | [...] | [...] | [...] | [...] | [...] | [...] | [...] |
| e82372f8 | 106000 | e8237358 | 0 | 00000000 | 55 | 4 | 0 | e514c000 | \ings\User123\NTUSER.DAT |
| [...] | [...] | [...] | [...] | [...] | [...] | [...] | [...] | [...] | [...] |

```
0: kd> dt _CMHIVE e82372f8
nt!_CMHIVE
+0x000 Hive : _HHIVE
+0x2d0 FileHandles : [3] 0x80002234 Void
+0x2dc NotifyList : _LIST_ENTRY [ 0x0 - 0x0 ]
+0x2e4 HiveList : _LIST_ENTRY [ 0xe7a38d64 - 0xe4d9fc9c ]
+0x2ec HiveLock : _EX_PUSH_LOCK
+0x2f0 ViewLock : 0x8778b020 _KGUARDED_MUTEX
+0x2f4 WriterLock : _EX_PUSH_LOCK
+0x2f8 FlusherLock : _EX_PUSH_LOCK
+0x2fc SecurityLock : _EX_PUSH_LOCK
+0x300 LRUViewListHead : _LIST_ENTRY [ 0xe6160170 - 0xe3d71978 ]
+0x308 PinViewListHead : _LIST_ENTRY [ 0xe2714fe0 - 0xe108d9e0 ]
+0x310 FileObject : 0x89ecf310 _FILE_OBJECT
+0x314 FileFullPath : _UNICODE_STRING "\Device\HarddiskVolumeX\Documents and Settings\User123\NTUSER.DAT"
+0x31c FileUserName : _UNICODE_STRING "^?\E:\Documents and Settings\User123\NTUSER.DAT"
+0x324 MappedViews : 0x37
+0x326 PinnedViews : 4
+0x328 UseCount : 0
+0x32c SecurityCount : 9
+0x330 SecurityCacheSize : 9
+0x334 SecurityHitHint : 0n0
+0x338 SecurityCache : 0xe74d5008 _CM_KEY_SECURITY_CACHE_ENTRY
+0x33c SecurityHash : [64] _LIST_ENTRY [ 0xe3f80228 - 0xe5901ef0 ]
+0x53c UnloadEvent : (null)
+0x540 RootKcb : (null)
+0x544 Frozen : 0
+0x548 UnloadWorkItem : (null)
+0x54c GrowOnlyMode : 0
+0x550 GrowOffset : 0
+0x554 KcbConvertListHead : _LIST_ENTRY [ 0xe823784c - 0xe823784c ]
+0x55c KnodeConvertListHead : _LIST_ENTRY [ 0xe8237854 - 0xe8237854 ]
+0x564 CellRemapArray : (null)
+0x568 Flags : 1
+0x56c TrustClassEntry : _LIST_ENTRY [ 0xe8237864 - 0xe8237864 ]
+0x574 FlushCount : 0
+0x578 CreatorOwner : (null)
```

有时，**消息框**（第 660 页）和 **堆栈跟踪** 语义（第 926 页）等模式会揭示另一种我们称之为 **自我诊断** 的模式，该模式可能会也可能不会导致 **自我转储**（第 850 页）。诊断消息可能会揭示运行时环境内部检测到的问题。

请参阅以下堆栈跟踪（为清晰起见，以较小字体显示）：

```
0:000> kv
ChildEBP RetAddr   Args to Child
0012e8c0 77f4bf53 77f4610a 00000000 00000000 ntdll!KiFastSystemCallRet
0012e8f8 77f3965e 000101a2 00000000 00000001 user32!NtUserWaitMessage+0xc
0012e920 77f4f762 777f3000 00151768 00000000 user32!InternalDialogBox+0xd0
0012ebe0 77f4f047 0012ed3c 00000000 ffffffff user32!SoftModalMessageBox+0xf94b
0012ed30 77f4eec9 0012ed3c 00000028 00000000 user32!MessageBoxWorker+0x2ba
0012ed88 77f87fd0 00000000 001511a8 0014ef50 user32!MessageBoxTimeoutW+0x7a
0012edbc 77f742c8 00000000 0012ee70 1001d7d4 user32!MessageBoxTimeoutA+0x9c
0012edcc 77f742a4 00000000 0012ee70 1001d7d4 user32!MessageBoxExA+0x1b
0012edf8 10014c9a 00000000 0012ee70 1001d744 user32!MessageBoxA+0x45
WARNING: Stack unwind information not available. Following frames may be wrong.
0012ee2c 10010221 0012ee70 1001d7d4 00012010 component!Error+0x7e2a
...
```

转储消息框消息及其标题显示，Visual C++ 运行时检测到了缓冲区溢出条件：

```
0:000> da 0012ee70
0012ee70  "Buffer overrun detected!.Progra"
0012ee90  "m: E:\W\program.exe..A buffer ov"
0012eeb0  "errun has been detected which ha"
0012eed0  "'s corrupted the program''s.intern"
0012eef0  "al state. The program cannot sa"
0012ef10  "fely continue execution and must"
0012ef30  ".now be terminated.."

0:000> da 1001d7d4
1001d7d4  "Microsoft Visual C++ Runtime Lib"
1001d7f4  "rary"
```

### 注释

提出的问题之一：

Q. 当程序崩溃时，我们有时会看到类似“Microsoft Visual C++ 运行时错误”的对话框。该对话框之后不会创建 drwtsn32.log 文件。我们该如何处理？

A. 在这里，我们可以手动保存转储文件，方法是使用 MS userdump、procdump，或在 Vista/W2K8 中使用任务管理器。

另一个示例来自 IE：

```
0:000> kc

user32!NtUserMessageCall
user32!SendMessageWorker
user32!SendMessageW
ieframe!CTabWindow::_MakeBlockingCallToHungTabToTriggerNtUserHangDetection
ieframe!CTabWindow::MarkTabAsHung
ieframe!FrameTabWndProc
user32!InternalCallWinProc
user32!UserCallWinProcCheckWow
user32!DispatchMessageWorker
user32!DispatchMessageW
ieframe!CBrowserFrame::FrameMessagePump
ieframe!BrowserThreadProc
ieframe!BrowserNewThreadProc
ieframe!SHOpenFolderWindow
ieframe!IEWinMainEx
ieframe!IEWinMain
ieframe!LCIEsStartAsFrame
explore!WinMain
explore!_initterm_e
kernel32!BaseThreadInitThunk
ntdll_77dc0000!_RtlUserThreadStart
ntdll_77dc0000!_RtlUserThreadStart
```

另一个示例：运行时库 abort()：

```
# 2 Id: acc.13b0 Suspend: 0 Teb: 7efa9000 Unfrozen
ChildEBP RetAddr
0333f4cc 768c15f7 ntdll!NtWaitForMultipleObjects+0x15
0333f568 762c19f8 KERNELBASE!WaitForMultipleObjectsEx+0x100
0333f5b0 762c4200 kernel32!WaitForMultipleObjectsExImplementation+0xe0
0333f5cc 762e80a4 kernel32!WaitForMultipleObjects+0x18
0333f638 762e7f63 kernel32!WerpReportFaultInternal+0x186
0333f64c 762e7858 kernel32!WerpReportFault+0x70
```

