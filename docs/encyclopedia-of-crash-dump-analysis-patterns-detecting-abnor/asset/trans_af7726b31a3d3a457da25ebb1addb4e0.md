


```
WARNING: Stack unwind information not available. Following frames may be wrong.
8d1c0ce4 89007938 85a5a000 00000000 85a5a000 DriverA+0x7e52
8d1c0cf8 8900ae9a 85a5a000 00000000 00000000 DriverA+0x7938
8d1c0d50 82a23056 85a32008 a9492f18 00000000 DriverA+0xae9a
8d1c0d90 828cb1a9 8900ab4e 85a5a000 00000000 nt!PspSystemThreadStartup+0x9e
00000000 00000000 00000000 00000000 00000000 nt!KiThreadStartup+0x19
```

```
kd> !ready
Processor 0: Ready Threads at priority 15
THREAD 861a2590 Cid 0460.0464 Teb: 7ffdf000 Win32Thread: fe9dbb18 ?????
THREAD 853cac98 Cid 0460.0670 Teb: 7ffd6000 Win32Thread: 00000000 ?????
THREAD 852fda88 Cid 0004.0084 Teb: 00000000 Win32Thread: 00000000 ?????
THREAD 8534ad48 Cid 0004.0090 Teb: 00000000 Win32Thread: 00000000 ?????
THREAD 852f1d48 Cid 0004.0080 Teb: 00000000 Win32Thread: 00000000 ?????
THREAD 852fd4f0 Cid 0004.0088 Teb: 00000000 Win32Thread: 00000000 ?????
THREAD 85340020 Cid 0004.008c Teb: 00000000 Win32Thread: 00000000 ?????
THREAD 852e67c8 Cid 0004.0078 Teb: 00000000 Win32Thread: 00000000 ?????
THREAD 85de77a8 Cid 01e4.026c Teb: 7ffda000 Win32Thread: ffb2c008 ?????
THREAD 85da7d48 Cid 01e4.0234 Teb: 7ffdf000 Win32Thread: fdadb38 ?????
THREAD 85a7c678 Cid 0004.00f0 Teb: 00000000 Win32Thread: 00000000 ?????
[...]
```

## 超时

这是 **阻塞线程** 模式的一个特殊变体，其中具有超时值：线程被暂时阻塞。例如，此 **主线程** (第 614 页) 在等待蜂鸣声结束一分钟后被阻塞：

```
0:000> kvL
ChildEBP RetAddr  Args to Child
0291f354 7c90d21a 7c8023f1 00000001 0291f388 ntdll!KiFastSystemCallRet
0291f358 7c8023f1 00000001 0291f388 7c90d27e ntdll!NtDelayExecution+0xc
0291f3b0 7c837beb 0000ea60 00000001 00000004 kernel32!SleepEx+0x61
0291f404 004952a2 00000370 0000ea60 004d6ae2 kernel32!Beep+0x1b3
0291f410 004d6ae2 00000370 0000ea60 004d6ed4 Application!DoBeep+0x16
[...]
0291ffec 00000000 0045aad0 00e470a0 00000000 kernel32!BaseThreadStart+0x37

0:000> ? ea60/0n1000
Evaluate expression: 60 = 0000003c
```

此模式常见于（但不限于）漫游配置文件场景。除了阻塞线程（第 82 页）、等待链模式的端点线程（第 1092 页）和阻塞模块（第 96 页）之外。例如，有报告称某应用程序挂起，在完整内存转储中我们可以看到堆栈跟踪集合（第 943 页）中的一个线程：

```
THREAD fffffa8005eca060 Cid 14b0.1fec Teb: 000000007ef84000 Win32Thread: fffffff900c26c2c30 WAIT: (Executive) KernelMode Non-Alertable
fffffa80048e6758 NotificationEvent
IRP List:
fffffa8005a6c160: (0006,03e8) Flags: 00060000 Mdl: 00000000
Not impersonating
DeviceMap fffff8a0055b6620
Owning Process fffffa80063dd970 Image: Application.exe
Attached Process N/A Image: N/A
Wait Start TickCount 171988390 Ticks: 26963639 (4:21:01:46.859)
Context Switch Count 226 LargeStack
UserTime 00:00:00.015
KernelTime 00:00:00.015
Win32 Start Address 0x000000006d851f62
Stack Init fffffff880075a9db0 Current fffffff880075a9770
Base fffffff880075aa000 Limit fffffff880075a4000 Call 0
Priority 10 BasePriority 8 UnusualBoost 0 ForegroundBoost 2 IoPriority 2 PagePriority 5
Child-SP RetAddr Call Site
fffff880`075a97b0 fffff800`0167f752 nt!KiSwapContext+0x7a
fffff880`075a98f0 fffff800`016818af nt!KiCommitThreadWait+0x1d2
fffff880`075a9980 fffff800`019b612a nt!KeWaitForSingleObject+0x19f
fffff880`075a9a20 fffff800`0198feaa nt! ?? ::NNGAKEGL::`string'+0x1d61a
fffff880`075a9a60 fffff800`018ed0e3 nt!IopSynchronousServiceTail+0x35a
fffff880`075a9ad0 fffff800`01677853 nt!NtLockFile+0x514
fffff880`075a9bb0 00000000`77840cea nt!KiSystemServiceCopyEnd+0x13 (TrapFrame @ fffff880`075a9c20)
00000000`0798e488 00000000`7543293b ntdll!ZwLockFile+0xa
00000000`0798e490 00000000`7541cf87 wow64!whNtLockFile+0x7f
00000000`0798e510 00000000`7536276d wow64!Wow64SystemServiceEx+0xd7
00000000`0798edd0 00000000`7541d07e wow64cpu!TurboDispatchJumpAddressEnd+0x24
00000000`0798ee90 00000000`7541c549 wow64!RunCpuSimulation+0xa
00000000`0798eee0 00000000`7786d177 wow64!Wow64LdrpInitialize+0x429
00000000`0798f430 00000000`7782308e ntdll! ?? ::FNODOBFM::`string'+0x2bfe4
00000000`0798f4a0 00000000`00000000 ntdll!LdrInitializeThunk+0xe
```

我们立即发现锁定文件尝试的异常，并查看其 IRP：

```
0: kd> !irp fffffa8005a6c160
Irp is active with 7 stacks 7 is current (= 0xfffffa8005a6c3e0)
No Mdl: No System Buffer: Thread fffffa8005eca060: Irp stack trace.
cmd flg cl Device File Completion-Context
[ 0, 0] 0 2 00000000 00000000 00000000-00000000

Args: 00000000 00000000 00000000 fffffffc00020c
[ 0, 0] 0 0 00000000 00000000 00000000-00000000
```

```
Args: 00000000 00000000 00000000 00000000
[ 0, 0] 0 0 00000000 00000000 00000000-00000000

Args: 00000000 00000000 00000000 00000000
[ 0, 0] 0 0 00000000 00000000 00000000-00000000

Args: 00000000 00000000 00000000 00000000
[ 0, 0] 0 0 00000000 00000000 00000000-00000000

Args: 00000000 00000000 00000000 00000000
[ 11, 0] 0 2 fffffa8004ada620 00000000 fffff880177d9cc-fffffa800710e580
\FileSystem\mrxsmb mu!Mup!UncProviderCompletion
Args: 00000000 00000000 00000000 00000000
>[ 11, 1] 0 0 fffffa8004066400 fffffa80048e66c0 00000000-00000000
\FileSystem\Mup
Args: fffffa8004a98120 00000001 00000000 00000000
```

从该 IRP 中我们看到一个文件名：

```
0: kd> !fileobj fffffa80048e66c0

[...]\AppData\Roaming\Vendor\Product\Recent\index.dat

LockOperation Set Device Object: 0xfffffa8004066400 \FileSystem\Mup
Vpb is NULL
Access: Read SharedRead SharedWrite SharedDelete

Flags: 0x40002
Synchronous IO
Handle Created

File Object is currently busy and has 0 waiters.

FsContext: 0xfffff8a00e8d9010 FsContext2: 0xfffff8a0012e4d688
CurrentByteOffset: 0
Cache Data:
Section Object Pointers: fffffa8006086928
Shared Cache Map: 00000000
File object extension is at fffffa8005c8cbe0:
```

或者，我们从虚拟化进程（第 1068 页）获取 32 位堆栈跟踪：

```
0: kd> .process /r /p fffffa80063dd970
Implicit process is now fffffa80`063dd970
Loading User Symbols

0: kd> .thread /w fffffa8005eca060
Implicit thread is now fffffa80`05eca060
The context is partially valid. Only x86 user-mode context is available.
x86 context set
```

```
0: kd:x86> .reload
Loading Kernel Symbols
Loading User Symbols
Loading unloaded module list
Loading Wow64 Symbols
```

```
0: kd:x86> kv
*** Stack trace for last set context - .thread/.cxr resets it
ChildEBP RetAddr  Args to Child
07ac8510 7744f033 00000390 00000000 00000000 ntdll_779d0000!ZwLockFile+0x12
07ac8590 774f0fd3 061b2b68 ada9964d c0000016 kernel32!BaseDllOpenIniFileOnDisk+0x246
07ac85d0 774efae2 061b2b68 00001000 6d352f20 kernel32!BaseDllReadWriteIniFileOnDisk+0x2d
07ac85e8 775001bf 00000001 00000000 061b2b68 kernel32!BaseDllReadWriteIniFile+0xed
07ac861c 6d928401 07aca1c 00000000 00001000 kernel32!GetPrivateProfileStringW+0x35
WARNING: Stack unwind information not available. Following frames may be wrong.
07ac8640 6d9282f5 07aca71c 00000000 00000000 DLL+0x618401
[...]
07acfb14 774e3677 06757d20 07acfb60 77a09d72 DLL+0x541f6d
07acfb20 77a09d72 06757d20 eca51e43 00000000 kernel32!BaseThreadInitThunk+0xe
07acfb60 77a09d45 6d851f62 06757d20 ffffffff ntdll_779d0000!_RtlUserThreadStart+0x70
07acfb78 00000000 6d851f62 06757d20 00000000 ntdll_779d0000!_RtlUserThreadStart+0x1b
```

我们从文件句柄中得到相同的文件名：

```
0: kd> !handle 00000390
processor number 0, process fffffa80063dd970
PROCESS fffffa80063dd970
SessionId: 5 Cid: 14b0 Peb: 7efd000 ParentCid: 1fac
DirBase: 48293000 ObjectTable: fffffff8a010515f90 HandleCount: 342.
Image: Application.exe
Handle table at fffffff8a0083e9000 with 444 Entries in use
0390: Object: fffffa80048e66c0 GrantedAccess: 00120089 Entry: fffffff8a00866fe40
Object: fffffa80048e66c0 Type: (fffffa8003cfb040) File
ObjectHeader: fffffa80048e6690 (new version)
HandleCount: 1 PointerCount: 3
Directory Object: 00000000 Name: [...]\\AppData\\Roaming\\Vendor\\Product\\Recent\\index.dat {Mup}
```

此外，我们在原始堆栈中发现错误代码 c0000016 并对其进行检查：

```
0: kd> !error c0000016
Error code: (NTSTATUS) 0xc0000016 (3221225494) - {Still Busy} The specified I/O request packet (IRP)
cannot be disposed of because the I/O operation is not complete.
```

