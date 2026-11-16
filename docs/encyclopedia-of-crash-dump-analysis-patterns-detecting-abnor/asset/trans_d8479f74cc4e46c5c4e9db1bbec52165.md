

## 内核空间

这是内核空间中 **已处理异常** 模式的一个变体，类似于用户空间（第 434 页）和托管空间（第 428 页）。崩溃转储与内核空间中的 **隐藏异常** 模式（第 455 页）相同：

```
fffff880`0a83d910 00000000`00000000
fffff880`0a83d918 ffffffff`4005f4d8
fffff880`0a83d920 fffffff880`0a83dca0
fffff880`0a83d928 fffffff880`016bc1c1 nt!C_specific_handler+0xcc
fffff880`0a83d930 00000000`00000000
fffff880`0a83d938 00000000`00000000
fffff880`0a83d940 00000000`00000000
fffff880`0a83d948 00000000`00000000
fffff880`0a83d950 fffffff800`0189e938 nt!BTFBuffer <PERF> (nt+0x280e38)
fffff880`0a83d958 fffffff880`0a83e940
fffff880`0a83d960 fffffff880`016ad767 nt!IopCompleteRequest+0x147
fffff880`0a83d968 fffffff880`0a83de40
fffff880`0a83d970 fffffff800`01665e40 nt!GSHandlerCheck_SEH
fffff880`0a83d978 fffffff800`017e5338 nt!_imp_NtOpenSymbolicLinkObject+0xfe30
fffff880`0a83d980 fffffff880`0a83e310
fffff880`0a83d988 00000000`00000000
fffff880`0a83d990 00000000`00000000
fffff880`0a83d998 fffffff800`016b42dd nt!RtlpExecuteHandlerForException+0xd
fffff880`0a83d9a0 fffffff880`017d7d0c nt!_imp_NtOpenSymbolicLinkObject+0x2804
fffff880`0a83d9a8 fffffff880`0a83eab0
fffff880`0a83d9b0 00000000`00000000
```

```
0: kd> ub fffff800`016b42dd
nt!RtlpExecuteHandlerForException+0x24:
fffff800`016b42c4 cc              int 3
fffff800`016b42c5 cc              int 3
fffff880`016b42c6 cc              int 3
fffff880`016b42c7 cc              int 3
fffff880`016b42c8 0f1f840000000000 nop dword ptr [rax+rax]
nt!RtlpExecuteHandlerForException:
fffff880`016b42d0 4883ec28        sub rsp,28h
fffff880`016b42d4 4c89c42420      mov qword ptr [rsp+20h],r9
fffff880`016b42d9 41ff5130        call qword ptr [r9+30h]
```

## 用户空间

即使我们在检查原始堆栈数据时看不到异常代码，但在某些情况下，仍可能看到调用异常处理程序后留下的执行残留。例如，当我们启动 TestWER 工具并选中“已处理异常”复选框时，可以看到：

![](img/d6dfefc8f9ab7106c77a723ff84aaa6d_433_0.png)

如果然后点击按钮，并使用任务管理器保存进程内存转储，我们会在原始堆栈上找到以下痕迹：

```
0:000> !teb
TEB at 7efdd000
ExceptionList: 0018fe20
StackBase: 00190000
StackLimit: 0018d000
SubSystemTib: 00000000
FiberData: 00001e00
ArbitraryUserPointer: 00000000
Self: 7efdd000
EnvironmentPointer: 00000000
ClientId: 00000838 . 00000f98
RpcHandle: 00000000
Tls Storage: 7efdd02c
PEB Address: 7efde000
LastErrorValue: 0
LastStatusValue: c0000034
Count Owned Locks: 0
HardErrorMode: 0
```

```
0:000> dps 0018d000 00190000
[...]
0018f414 00000000
0018f418 0018f840
0018f41c 0018f4cc
0018f420 77726a9b ntdll!ExecuteHandler+0x24
0018f424 0018f4e4
0018f428 0018f840
0018f42c 0018f534
0018f430 0018f848
0018f434 00412600 TestWER!except_handler4
0018f438 00000001
0018f43c 00000000
[...]
```

```
0:000> ub 77726a9b
ntdll!ExecuteHandler+0x7:
77726a7e 33f0 xor esi,esi
77726a80 33ff xor edi,edi
77726a82 ff742420 push dword ptr [esp+20h]
77726a86 ff742420 push dword ptr [esp+20h]
77726a8a ff742420 push dword ptr [esp+20h]
77726a8e ff742420 push dword ptr [esp+20h]
77726a92 ff742420 push dword ptr [esp+20h]
77726a96 e808000000 call ntdll!ExecuteHandler2 (77726aa3)
```

如果将上述输出与二次机会异常内存转储中的原始堆栈片段进行比较（在重新启动 TestWER 后，不选中“已处理异常”复选框并单击大闪电按钮），我们会看到类似的调用片段：

```
[...]
0018f3f4 0ddd0aa7
0018f3f8 0018f41c
0018f3fc 77726ac9 ntdll!ExecuteHandler2+0x26
0018f400 fffffffe
0018f404 0fffffc4
0018f408 0018f534
0018f40c 0018f4b8
0018f410 0018f840
0018f414 77726add ntdll!ExecuteHandler2+0x3a
0018f418 0018ffc4
0018f41c 0018ffcc
0018f420 77726a9b ntdll!ExecuteHandler+0x24
0018f424 0018f4e4
0018f428 0018ffc4
0018f42c 0018f534
0018f430 0018f4b8
0018f434 77750ae5 ntdll!except_handler4
0018f438 00000000
0018f43c 0018f4e4
0018f440 0018ffc4
0018f444 77726a3d ntdll!RtlDispatchException+0x127
0018f448 0018f4e4
0018f44c 0018ffc4
0018f450 0018f534
0018f454 0018f4b8
0018f458 77750ae5 ntdll!_except_handler4
0018f45c 00000111
0018f460 0018f4e4
[...]
```

有时，我们还可以看到“Unwind”、“StackWalk”、“WalkFrames”、“EH”、“Catch”函数。有时我们看不到任何内容，因为在过去某个时间点发生 **已处理异常** 后，此类残留被后续函数调用覆盖了。

## 注释

如果我们为同一进程获得多个相同的首次机会异常转储，则说明该异常已被处理。否则，我们将看不到后续的转储。

## 硬件活动

有时，当报告大量中断，但内存转储文件中没有中断风暴或挂起 DPC 的迹象时，在运行和/或可疑线程中搜索此模式很有用。这可以通过检查线程原始堆栈上留下的执行残留来完成。尽管发现的驱动程序活动可能与报告的问题无关，但它可以作为检查可疑驱动程序是否有更新的一般建议的驱动程序排除程序的有用起点。以下是网卡执行“Scatter-Gather”DMA 的线程原始堆栈示例：

```
1: kd> !thread
THREAD f7732090 Cid 0000.0000 Teb: 00000000 Win32Thread: 00000000 RUNNING on processor 1
Not impersonating
Owning Process 8089db40 Image: Idle
Attached Process N/A Image: N/A
Wait Start TickCount 0 Ticks: 24437545 (4:10:03:56.640)
Context Switch Count 75624870
UserTime 00:00:00.000
KernelTime 4 Days 08:50:5.125
Stack Init f78b3000 Current f78b2d4c Base f78b3000 Limit f78b0000 Call 0
Priority 0 BasePriority 0 PriorityDecrement 0
ChildEBP RetAddr Args to Child
f7b30c5c 00000000 00000000 00000000 00000000 LiveKdD+0x1c07

1: kd> dds f78b0000 f78b3000
f78b0000 00000000
f78b0004 00000000
f78b0008 00000000
f78b000c 00000000
f78b0010 00000000
[...]
f78b2870 8b3de0d0
f78b2874 80887b75 nt!KiFlushTargetSingleTb+0xd
f78b2878 8b49032c
f78b287c 00000000
f78b2880 2d003202
f78b2884 00000000
f78b2888 00000000
f78b288c 2d003202
f78b2890 8b490302
f78b2894 f78b28a4
f78b2898 80a61456 hal!KfLowerIrql+0x62
f78b289c 2d00320a
f78b28a0 00000000
f78b28a4 8b3de0d0
f78b28a8 8b3e3730
f78b28ac 00341eb0
f78b28b0 f78b2918
f78b28b4 f63fbf78 NetworkAdapterA!SendWithScatterGather+0x318
f78b28b8 8b3de0d0
f78b28bc 8b341eb0
f78b28c0 f78b28d4
f78b28c4 00000000
f78b28c8 8a55f3c0 hal!KfAcquireSpinLock
f78b28cc 00000000
f78b28d0 8b3de0d0
f78b28d4 00000000
f78b28d8 8b3de0d0
f78b28dc 8b3eb730
f78b28e0 005a7340
f78b28e4 f78b294c
f78b28e8 f63fbf78 NetworkAdapterA!SendWithScatterGather+0x318
f78b28ec 8b3de0d0
f78b28f0 8a5a7340
f78b28f4 f78b2908
f78b28f8 00000000
f78b28fc 8b3de0d0
f78b2900 8b0f5158
f78b2904 001e2340
f78b2908 f78b2970
f78b290c f63fbf78 NetworkAdapterA!SendWithScatterGather+0x318
f78b2910 8b3de0d0
f78b2914 8b1e2340
f78b2918 f78b292c
f78b291c 00000000
f78b2920 8a55f3c0 hal!KfAcquireSpinLock
f78b2924 00000000
f78b2928 8b3de0d0
f78b292c 00000000
f78b2930 8b3eb700
f78b2934 00000000
f78b2938 00000000
f78b293c 00000000
f78b2940 00000000
f78b2944 00000000
f78b2948 00000000
f78b294c 0a446aa2
f78b2950 f78b29b8
f78b2954 8b0f5158
f78b2958 8b01ce10
f78b295c 00000001
f78b2960 8b3de0d0
f78b2964 80a5f302 hal!HalpPerfInterrupt+0x32
f78b2968 00000001
f78b296c 8b3de0d0
f78b2970 80a5f302 hal!HalpPerfInterrupt+0x32
f78b2974 8b3de302
f78b2978 f78b2988
f78b297c 80a61456 hal!KfLowerIrql+0x62
f78b2980 80a5f3c0 hal!KfAcquireSpinLock
f78b2984 8b3de302
f78b2988 f78b29a4
f78b298c 80a5f44b hal!KfReleaseSpinLock+0xb
f78b2990 f63fbbf NetworkAdapterA!SendPackets+0x1b3
f78b2994 8a446a90
f78b2998 8b0e8ab0
f78b299c 00000000
f78b29a0 008b29d0
f78b29a4 f78b29bc
f78b29a8 7163790 NDIS!ndisMProcessSGList+0x90
f78b29ac 8b3de388
f78b29b0 f78b29d0
f78b29b4 00000001
f78b29b8 00000000
f78b29bc f78b29e8
f78b29c0 80a60147 hal!HalBuildScatterGatherList+0x1c7
f78b29c4 8b0e89b0
f78b29c8 00000000
f78b29cc a4a4cde8
f78b29d0 8b1e2340
f78b29d4 8a446aa2
f78b29d8 8b026ca0
f78b29dc 8b1e2340
f78b29e0 8b0e8ab0
f78b29e4 8b0e8ab0
f78b29e8 f78b2a44
f78b29ec f716369f NDIS!ndisMAllocSGList+0xda
f78b29f0 8a44cde8
f78b29f4 8b0e89b0
f78b29f8 8a446a70
f78b29fc 00000000
f78b2a00 00000036
f78b2a04 f7163730 NDIS!ndisMProcessSGList
f78b2a08 8b1e2340
f78b2a0c 00000000
f78b2a10 8a44cde8
f78b2a14 00000218
f78b2a18 8b1e2308
[...]
f78b2a40 029a9e02
f78b2a44 f78b2a60
f78b2a48 f71402ff NDIS!ndisMSendX+0x1dd
f78b2a4c 8b490310
f78b2a50 8b1e2340
f78b2a54 8a446a70
f78b2a58 8a9a9e02
f78b2a5c 8a9a9e02
f78b2a60 f78b2a88
f78b2a64 f54c923 tcpip!ARPSendData+0x1a9
f78b2a68 8b3e76c8
f78b2a6c 8b1e2340
f78b2a70 8a9a9ea8
f78b2a74 8b490310
f78b2a78 80888b00 nt!RtlBackoff+0x68
f78b2a7c 8a446a70
f78b2a80 8a446aa2
f78b2a84 8a446a70
f78b2a88 f78b2ab4
f78b2a8c f546ba5d tcpip!ARPTransmit+0x112
f78b2a90 8b490310
```

