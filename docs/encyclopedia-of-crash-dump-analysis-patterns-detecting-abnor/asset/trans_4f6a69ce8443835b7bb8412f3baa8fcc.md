

0679f958 76f08bcc ntdll!NtSetEvent+0xc
0679f95c 748e3b0b KERNELBASE!SetEvent+0x10
0679f960 000004ac
0679f964 00000000
0679f968 0679f984
0679f96c 5f5fcbe6 msvcr120!Concurrency::details::ExternalContextBase::Unblock+0x3f
0679f970 0000004ac
0679f974 03a6f750
0679f978 03a6f750
0679f97c 0679f9b4
0679f980 5f5fb70d msvcr120!Concurrency::details::_Condition_variable::notify_all+0x3f
0679f984 0679f9b4
0679f988 5f5fb722 msvcr120!Concurrency::details::_Condition_variable::notify_all+0x54
0679f98c 07481380
0679f990 05ba6f60
0679f994 071cf9ac
[...]

Both methods point to the same possible owner thread which is also blocked in reading a file.

## CLR Monitors

This is a variation of a general **等待链** (第 1092 页) 模式，与 **CLR 线程** (第 124 页) 相关。在查看完整内存转储中的 **堆栈跟踪收集** (第 943 页) 时，我们可能会发现使用监视器同步机制的线程：

```
[... 32-bit ...]
09d2e908 6bda4d409 clr!CLREvent::WaitEx+0x106
09d2e91c 6bb90160 clr!CLREvent::Wait+0x19
09d2e9ac 6bb90256 clr!AwareLock::EnterEpilogHelper+0xa8
09d2e9ec 6bb9029b clr!AwareLock::EnterEpilog+0x42
09d2ea0c 6b9a0f78 clr!AwareLock::Enter+0x5f
09d2eaa8 05952499 clr!JIT_MonEnterWorker_Portable+0xf8
[...]
```

or

```
[... 64-bit ...]
00000000`2094e230 000007fe`eecd3e3a clr!CLREvent::WaitEx+0xc1
00000000`2094e2d0 000007fe`eecd3d43 clr!AwareLock::EnterEpilogHelper+0xca
00000000`2094e3a0 000007fe`eee3e613 clr!AwareLock::EnterEpilog+0x63
00000000`2094e400 000007ff`007f4c38 clr!JIT_MonEnterWorker_Portable+0x14f
[...]
```

看到此类线程时，我们可以请求进程内存转储，以使用 SOS 或其他 WinDbg 扩展（例如 **死锁** (第 202 页) 模式示例中针对 CLR 2 (mscorwks) 的示例）进行 .NET 内存转储分析。

## Critical Sections

这里是另一个一般等待链模式 (第 1092 页) 的示例，其中对象是临界区。

如果我们使用 **!analyze -v -hang** 命令，WinDbg 可以检测到它们，但在存在多个等待链的情况下，它只检测一个，不一定是最长或最宽的链：

| DL | Eid | Cid | WaitType |
|---|---|---|---|
| 2 | 8d8.90c | 临界区 | --> |
| 4 | 8d8.914 | 临界区 | --> |
| 66 | 8d8.f9c | 未知 | |

查看线程时，我们可以看到此链，并且还可以看到最终线程正在阻塞等待套接字。

```
0:167> ~~[90c]kvL
ChildEBP RetAddr Args to Child
00bffd9c 7c942124 7c95970f 00000ea0 00000000 ntdll!KiFastSystemCallRet
00bbfda0 7c95970f 00000ea0 00000000 00000000 ntdll!NtWaitForSingleObject+0xc
00bbfdcc 7c959620 00000000 00000004 00000000 ntdll!RtlpWaitOnCriticalSection+0x19c
00bbfdfc 6748d2f9 06018b50 00000000 00000000 ntdll!RtlEnterCriticalSection+0xa8
...
00bbffb8 7c82680b 00315218 00000000 00000000 msvcrt!_endthreadex+0xa3
00bbffec 00000000 77b9b4bc 00315218 00000000 kernel32!BaseThreadStart+0x34

0:167> ~~[914]kvL 100
ChildEBP RetAddr Args to Child
00dbf1cc 7c942124 7c95970f 000004b0 00000000 ntdll!KiFastSystemCallRet
00dbf1d0 7c95970f 000004b0 00000000 00000000 ntdll!NtWaitForSingleObject+0xc
00dbf20c 7c959620 00000000 00000004 0031abcc ntdll!RtlpWaitOnCriticalSection+0x19c
00dbf22c 6748d244 0031abd8 003174e0 00dbf254 ntdll!RtlEnterCriticalSection+0xa8
...
00dbfbf8 7c82680b 00315218 00000000 00000000 msvcrt!_endthreadex+0xa3
00dbffec 00000000 77b9b4bc 00315218 00000000 kernel32!BaseThreadStart+0x34

0:167> ~~[f9c]kvL 100
ChildEBP RetAddr Args to Child
0fe2a09c 7c942124 71933a89 00000b50 00000001 ntdll!KiFastSystemCallRet
0fe2a0a0 71933a89 00000b50 00000001 0fe2a0c8 ntdll!NtWaitForSingleObject+0xc
0fe2a0dc 7194576e 00000b50 00000234 00000000 mswsock!SockWaitForSingleObject+0x19d
0fe2a154 71a12679 00000234 0fe2a1b4 00000001 WS2_32!WSARecv+0x77
0fe2a190 62985408 00000234 0fe2a1b4 00000001 WS2_32!WSARecv+0x77
0fe2a1d0 6298326b 00000234 0274ebc6 00000810 component!wait+0x338
...
0fe2ffb8 7c82680b 060cfc70 00000000 00000000 msvcrt!_endthreadex+0xa3
0fe2ffec 00000000 77b9b4bc 060cfc70 00000000 kernel32!BaseThreadStart+0x34
```

如果我们查看所有持有的临界区，可以看到另一个阻塞了超过 125 个其他线程的线程：

```
0:167> !locks

CritSec +31abd8 at 0031abd8
WaiterWoken   No
LockCount     6
RecursionCount 1
OwningThread  f9c
EntryCount    0
ContentionCount 17
*** Locked

CritSec +51e4bd8 at 051e4bd8
WaiterWoken   No
LockCount     125
RecursionCount 1
OwningThread  830
EntryCount    0
ContentionCount 7d
*** Locked

CritSec +5f40620 at 05f40620
WaiterWoken   No
LockCount     0
RecursionCount 1
OwningThread  920
EntryCount    0
ContentionCount 0
*** Locked

CritSec +60b6320 at 060b6320
WaiterWoken   No
LockCount     1
RecursionCount 1
OwningThread  8a8
EntryCount    0
ContentionCount 1
*** Locked

CritSec +6017c60 at 06017c60
WaiterWoken   No
LockCount     0
RecursionCount 1
OwningThread  914
EntryCount    0
ContentionCount 0
*** Locked
```

```
CritSec +6018b50 at 06018b50
WaiterWoken No
LockCount 3
RecursionCount 1
OwningThread 914
EntryCount 0
ContentionCount 3
*** Locked
```

```
CritSec +6014658 at 06014658
WaiterWoken No
LockCount 2
RecursionCount 1
OwningThread 928
EntryCount 0
ContentionCount 2
*** Locked
```

```
0:167> ~~[830]kvL 100
ChildEBP RetAddr Args to Child
0ff2f300 7c942124 7c95970f 000004b0 00000000 ntdll!KiFastSystemCallRet
0ff2f304 7c95970f 000004b0 00000000 00000000 ntdll!NtWaitForSingleObject+0xc
0ff2f340 7c959620 00000000 00000000 0031abcc ntdll!RtlpWaitOnCriticalSection+0x19c
0ff2f360 6748d244 0031abd8 003174e0 0ff2f388 ntdll!RtlEnterCriticalSection+0xa8
...
0ff2ffb8 7c82680b 060cf9a0 00000000 00000000 msvcrt!_endthreadex+0xa3
0ff2ffec 00000000 77b9b4bc 060cf9a0 00000000 kernel32!BaseThreadStart+0x34
```

搜索任何正在等待临界区 051e4bd8 的线程，得到：

```
8 Id: 8d8.924 Suspend: 1 Teb: 7ffd5000 Unfrozen
ChildEBP RetAddr Args to Child
011efe80 7c942124 7c95970f 00000770 00000000 ntdll!KiFastSystemCallRet
011efe84 7c95970f 00000770 00000000 00000000 ntdll!NtWaitForSingleObject+0xc
011efe90 7c959620 00000000 00000000 00000000 ntdll!RtlpWaitOnCriticalSection+0x19c
011ef940 677b209d 051e4bd8 011efa8c 057bd36c ntdll!RtlEnterCriticalSection+0xa8
...
011effb8 7c82680b 00315510 00000000 00000000 msvcrt!_endthreadex+0xa3
011effec 00000000 77b9b4bc 00315510 00000000 kernel32!BaseThreadStart+0x34
```

并且我们可以构建另一个等待链：

| 8 | 8d8.924 | 临界区 | --> |
| 67 | 8d8.830 | 临界区 | --> |
| 66 | 8d8.f9c | 未知 | |

## Executive Resources

在内核和完整内存转储中，**等待链** (第 1092 页) 模式最常见且最容易检测的示例是对象为执行资源（**死锁**，第 194 页）时。在某些复杂情况下，我们甚至可以有多个等待链。例如，在下面 **!locks** WinDbg 命令的输出中，我们可以找到至少三个用粗体、斜体和粗斜体标记的等待链：

```
883db310 -> 8967d020 -> 889fa230
89a74228 -> 883dad4e0 -> 88d7a3e0
88e13990 -> 899da538 -> 8805fac8
```

手动查找链的过程很简单。选取标记为 <*> 的线程。这是当前持有该资源的线程。查看哪些线程正在等待对该资源的独占访问。然后搜索 <*> 线程的其他出现，以查看它是否正在独占等待被其他线程阻塞的另一个资源，以此类推。

```
1: kd> !locks
**** DUMP OF ALL RESOURCE OBJECTS ****

Resource @ 0x8b4425c8  Shared 1 owning threads
Contention Count = 45
NumberOfSharedWaiters = 43
NumberOfExclusiveWaiters = 2
Threads: **8967d020-01-<*>** 88748b10-01 88b8b020-01 8b779ca0-01
88673248-01 8b7797c0-01 889c8358-01 8b777b40-01
8b7763f0-01 8b776b40-01 8b778040-01 8841b020-01
8b7788d0-01 88c7b000-01 8b776020-01 8b775020-01

[...]

8b778020-01 8b779a30-01 8b778660-01 8943a020-01
88758020-01 8b777bd0-01 88ee3590-01 896f3020-01
89fc4b98-01 89317938-01 8867f1e0-01 89414118-01
88e899a8-01 88de5b70-01 88c4b588-01 8907dd48-01

Threads Waiting On Exclusive Access:
**883db310**       8907d280

Resource @ 0x899e27ac  Exclusively owned
Contention Count = 1
NumberOfExclusiveWaiters = 1
Threads: **889fa230-01-<*>**
Threads Waiting On Exclusive Access:
**8967d020**

Resource @ 0x881a38f8  Exclusively owned
Contention Count = 915554
NumberOfExclusiveWaiters = 18
Threads: 883dad4e0-01-<*>
Threads Waiting On Exclusive Access:
89a74228   8844c630   8955e020   891aa440
894a6270   889b7ab0   8947d020   881e5760
8b594af8   88dc0e20   899df328   8aa86900
897ff020   8920adb0   8972b1c0   89657c70
88bcc868   88cb0cb0
```

