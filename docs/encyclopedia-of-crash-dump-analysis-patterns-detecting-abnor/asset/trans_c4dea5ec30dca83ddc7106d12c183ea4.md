

让我们来看看这样的一个条目（第一个和最后一个 qword 值是指针）：

```
0:000> dq 000000db`56a57da0 L3
000000db`56a57da0 ffffff901`440deaf0 400a6d0a`00002c30
000000db`56a57db0 000000db`56a4f3b00

0:000> dw 000000db`56a57da0 L3*4
000000db`56a57da0 eaf0 440d f901 ffff 2c30 0000 6d0a 400a
000000db`56a57db0 3b00 564f 00db 0000
```

将 7f 应用到 wType 字 400a 上，得到 0xa 或 10，这是一个字体句柄：

```
0:000> ? 400a & 7f
Evaluate expression: 10 = 00000000`0000000a
```

由于此表中包含同一会话中其他进程的条目，直观评估句柄泄漏比较困难，因此我们编写了一个 WinDbg 脚本，该脚本从第一个非零 pKernelAddress ($t0) 遍历到第一个零条目，并针对给定的 wProcessId ($tpid) 统计条目数量 ($t1) 以及针对给定 wType ($t2) 的条目数量 ($t3)。该脚本还会统计直到第一个零条目之前的总条目数 ($t4)：

```
.while (qwo(@$t0)) { .if (wo(@$t0+8) == @$tpid) {r $t1 = @$t1+1; .if (((qwo(@$t0+8) >> 0n48) & 7f) == @$t2) {r $t3 = @$t3+1}; r $t0 = @$t0+3*8; r $t4 = @$t4+1}
```

要执行它，我们准备变量：

```
0:000> r $t0=000000db`56a500f0

0:000> r $t1=0

0:000> r $t2=a

0:000> r $t3=0

0:000> r $t4=0
```

```
0:000> .while (qwo(@$t0)) { .if (wo(@$t0+8) == @$tpid) {r $t1 = @$t1+1; .if (((qwo(@$t0+8) >> 0n48) & 7f) == @$t2) {r $t3 = @$t3+1}; r $t0 = @$t0+3*8; r $t4 = @$t4+1}
```

执行后，我们得到修改后的变量，它们显示连续非零句柄表条目的总数为 21464，当前进程的条目总数为 9990，字体总数为 9982：

```
0:000> ? $t0
Evaluate expression: 942052007216 = 000000db`56acdd30

0:000> ? $t1
Evaluate expression: 9990 = 00000000`00002706

0:000> ? $t2
Evaluate expression: 10 = 00000000`0000000a

0:000> ? $t3
Evaluate expression: 9982 = 00000000`000026fe

0:000> ? $t4
Evaluate expression: 21464 = 00000000`000053d8
```

如果我们对设备上下文（wType 为 1）重复运行同一脚本，则仅为我们的 PID 得到 2 个条目：

```
0:000> r $t0=000000db`56a500f0
0:000> r $t1=0
0:000> r $t2=1
0:000> r $t3=0
0:000> r $t4=0
0:000> .while (qwo(@$t0)) .if (wo(@$t0+8) == @$tpid) {r $t1 = @$t1+1; .if (((qwo(@$t0+8) >> 0n48) & 7f) == @$t2) {r $t3 = @$t3+1}; r $t0 = @$t0+3*8; r $t4 = @$t4+1}
0:000> ? $t3
Evaluate expression: 2 = 00000000`00000002
```

当然，此脚本可以进一步改进，例如，处理所有可能的 wType 值并打印其统计信息。它还可以作为带参数的文本 WinDbg 脚本过程来实现。

## 已处理异常

## .NET CLR

类似于非托管用户空间 Handled Exceptions（第 434 页）残留，我们可以在 .NET CLR 线程的原始堆栈上看到类似的残留。以下是一些典型片段（x86，CLR 4 也有类似残留）：

```
[...]
09c8e1e0 79ef2dee mscorwks!ExInfo::Init+0x41
09c8e1e4 00004000
09c8e1e8 79f088cc mscorwks!`string'
09c8e1ec 79f088c2 mscorwks!ExInfo::UnwindExInfo+0x14d
09c8e1f0 08f68728
09c8e1f4 95f5b898
09c8e1f8 09c8e1a4
09c8e1fc 09c8e92c
09c8e200 7a34d0d8 mscorwks!GetManagedNameForTypeInfo+0x22b02
09c8e204 79f091ee mscorwks!COMPlusCheckForAbort+0x15
09c8e208 00000000
09c8e20c aada664
09c8e210 0aaabff4
09c8e214 00000000
09c8e218 09c8eeec
09c8e21c 074c1f23
09c8e220 09c8ef0c
09c8e224 79f091cb mscorwks!JIT_EndCatch+0x16
09c8e228 09c8ef0c
09c8e22c 09c8eec
09c8e230 074c1f23
09c8e234 09c8e25c
09c8e238 0009c108
09c8e23c 09c8e460
09c8e240 09c8e5c4
09c8e244 00071d88
09c8e248 08f68728
09c8e24c 79e734c4 mscorwks!ClrFlsSetValue+0x57
09c8e250 95f5b8e4
09c8e254 aada634
09c8e258 08f68728
09c8e25c aada90c
09c8e260 aabfff4
09c8e264 00000002
09c8e268 09c8e304
09c8e26c aada664
09c8e270 00000000
09c8e274 09c8ef0c
09c8e278 09c8e234
09c8e27c 074c1f13
09c8e280 00000000
09c8e284 08f688a0
09c8e288 09c8e234
09c8e28c 79f00c0b mscorwks!Thread::ReturnToContext+0x4e2
09c8e290 aada90c
09c8e294 09c8eef4
09c8e298 09c8e2bc
09c8e29c 79f08eb8 mscorwks!EEJitManager::ResumeAtJitEH+0x28
09c8e2a0 09c8e460
09c8e2a4 074c1ed8
09c8e2a8 074b41a8
09c8e2ac 00000000
09c8e2b0 08f68728
09c8e2b4 00000000
09c8e2b8 09c8e410
09c8e2bc 09c8e3c8
09c8e2c0 79f08df5 mscorwks!COMPplusUnwindCallback+0x7c3
09c8e2c4 09c8e460
09c8e2c8 074b41a8
09c8e2cc 00000000
09c8e2d0 08f68728
09c8e2d4 00000000
09c8e2d8 0009c108
09c8e2dc 09c8e410
09c8e2e0 09c8e5c4
09c8e2e4 074b41a8
09c8e2e8 09c8e3a4
09c8e2ec 79e734c4 mscorwks!ClrFlsSetValue+0x57
09c8e2f0 95f5b984
09c8e2f4 0009c128
09c8e2f8 09c8e3a4
09c8e2fc 00000000
09c8e300 00000000
09c8e304 00000002
[...]
09c8e4e4 00000000
09c8e4e8 79f09160 mscorwks!_CT??_R0H+0x34b4
09c8e4ec ffffffff
09c8e4f0 73792e2f msvcr80!_getptd+0x6
09c8e4f4 ffffffff
09c8e4f8 737b7a78 msvcr80!__FrameUnwindToState+0xd9
09c8e4fc 737b7a5e msvcr80!__FrameUnwindToState+0xbf
09c8e500 95f5bc05
09c8e504 e06d7363
09c8e508 1fffffff
09c8e50c 19930522
09c8e510 ffffffff
09c8e514 ffffffff
09c8e518 09c8e500
09c8e51c 09c8e554
09c8e520 09c8e5a8
09c8e524 73798cd9 msvcr80!_except_handler4
09c8e528 efbc0d3d
09c8e52c ffffffff
09c8e530 737b7a5e msvcr80!__FrameUnwindToState+0xbf
09c8e534 737b89cb msvcr80!_InternalCxxFrameHandler+0x6d
09c8e538 09c8eab0
09c8e53c 09c8e6a0
09c8e540 79f09160 mscorwks!_CT??_R0H+0x34b4
09c8e544 ffffffff
09c8e548 00000000
09c8e54c 00000000
09c8e550 00000000
09c8e554 09c8e590
09c8e558 737b8af1 msvcr80!__CxxFrameHandler3+0x26
09c8e55c 09c8e600
09c8e560 09c8eab0
09c8e564 01010101
09c8e568 09000000
09c8e56c 09c8f160
09c8e570 07540c00
09c8e574 00071d88
09c8e578 08e65d48
09c8e57c 09c8e5ec
09c8e580 074c1ec8
09c8e584 00000024
09c8e588 00000001
09c8e58c 0009c108
09c8e590 08f68728
09c8e594 00000000
09c8e598 00000000
09c8e59c 09c8eb38
09c8e5a0 00000000
09c8e5a4 09c8e6a0
09c8e5a8 09c8f15c
09c8e5ac 09c8f15c
09c8e5b0 09c8eb38
09c8e5b4 95f5bf28
09c8e5b8 09c8e8f4
09c8e5bc 798e4bf2 mscorwks!Thread::StackWalkFrames+0xb8
09c8e5c0 08f68728
09c8e5c4 09c8ea40
09c8e5c8 79e84bf2 mscorwks!Thread::StackWalkFrames+0xb8
09c8e5cc 09c8e5ec
09c8e5d0 79f07d64 mscorwks!COMPlusUnwindCallback
09c8e5d4 09c8ea40
09c8e5d8 00000005
09c8e5dc 00000000
09c8e5e0 08f68728
09c8e5e4 08f688a0
09c8e5e8 08f68728
09c8e5ec 09c8ec20
09c8e5f0 00000000
09c8e5f4 09c8ebcc
09c8e5f8 09c8ecc0
09c8e5fc 09c8ecc4
09c8e600 09c8ecc8
09c8e604 09c8eccc
09c8e608 09c8ecd0
09c8e60c 09c8ecd4
09c8e610 09c8eeec
09c8e614 09c8ecd8
09c8e618 09c8ecd8
09c8e61c 00000024
09c8e620 00000000
09c8e624 0009c108
09c8e628 08f68728
09c8e62c 00000000
09c8e630 00000000
09c8e634 79e71ba4 mscorwks!Thread::CatchAtSafePoint
09c8e638 00000000
09c8e63c 79e71ba4 mscorwks!Thread::CatchAtSafePoint
09c8e640 09c8f15c
09c8e644 09c8f15c
09c8e648 00000000
09c8e64c 95f5bcc0
09c8e650 09c8e988
09c8e654 79e84bf2 mscorwks!Thread::StackWalkFrames+0xb8
09c8e658 09c8ea40
09c8e65c 79e84bf2 mscorwks!Thread::StackWalkFrames+0xb8
09c8e660 09c8e680
09c8e664 79f07957 mscorwks!COMPlusThrowCallback
09c8e668 09c8ea40
09c8e66c 00000000
09c8e670 00000000
09c8e674 0aada90c
09c8e678 09c8ea40
09c8e67c 79e84bff mscorwks!Thread::StackWalkFrames+0xc5
09c8e680 09c8ec20
09c8e684 00000000
09c8e688 09c8ecbc
09c8e68c 09c8ecc0
09c8e690 09c8ecc4
09c8e694 09c8ecc8
[...]
09c8e8f0 95f5b264
09c8e8f4 09c8e914
09c8e8f8 79f07d5e mscorwks!UnwindFrames+0x62
09c8e8fc 79f07d64 mscorwks!COMPlusUnwindCallback
09c8e900 09c8ea40
09c8e904 00000005
09c8e908 00000000
09c8e90c 09c8e6fc
09c8e910 08f68728
09c8e914 09c8e9a4
09c8e918 79f089cc mscorwks!COMPlusAfterUnwind+0x97
09c8e91c 08f68728
09c8e920 09c8ea40
09c8e924 00000001
09c8e928 00000000
09c8e92c 09c8ef6c
09c8e930 79f0a3d9 mscorwks!COMPlusNestedExceptionHandler
09c8e934 09c8f160
09c8e938 00000000
09c8e93c 00000000
09c8e940 cccccccc
[...]
```

有时如果未被覆盖，我们可以看到 ‘ExecuteHandler’ 调用：

```
[...]
09d2e6e0 00000000
09d2e6e4 00000720
09d2e6e8 77c41039 ntdll!ExecuteHandler2+0x26
09d2e6ec 09d2e7c8
09d2e6f0 0d2eb60
09d2e6f4 09d2e7c4
09d2e6f8 09d2e7a4
09d2e6fc 09d2eb60
09d2e700 77c4104d ntdll!ExecuteHandler2+0x3a
09d2e704 09d2eb60
09d2e708 09d2e7b0
09d2e70c 77c4100b ntdll!ExecuteHandler+0x24
09d2e710 09d2e7c8
09d2e714 00000001
09d2e718 09d2e6b0
09d2e71c 09d2e7a4
09d2e720 09d2e784
09d2e724 76545ac9 kernel32!except_handler4
[...]
```

如果存在此类痕迹，它们可以表现为 Caller-n-Callee（第 111 页）模式：

```
0:011> !DumpStack
OS Thread Id: 0x3cc (11)
Current frame: ntdll!KiFastSystemCallRet
ChildEBP RetAddr  Caller, Callee
09d2e690 77c40690 ntdll!ZwWaitForMultipleObjects+0xc
09d2e694 76577e09 kernel32!WaitForMultipleObjectsEx+0x11d, calling ntdll!NtWaitForMultipleObjects
09d2e6d8 76578101 kernel32!WaitForMultipleObjectsEx+0x33, calling ntdll!
09d2e6e4 77c41039 ntdll!ExecuteHandler2+0x26
09d2e708 77c4100b ntdll!ExecuteHandler+0x24, calling ntdll!ExecuteHandler2
09d2e730 6ba516a clr!WaitForMultipleObjectsEx_SO_TOLERANT+0x56, calling RtlActivateActivationContextUnsafeFast
kernel32!WaitForMultipleObjectsEx
09d2e794 6baa4f98 clr!Thread::DoAppropriateAptStateWait+0x4d, calling clr!WaitForMultipleObjectsEx_SO_TOLERANT
09d2e7b4 6baa4dd8 clr!Thread::DoAppropriateWaitWorker+0x17d, calling clr!Thread::DoAppropriateAptStateWait
09d2e848 6baa4e99 clr!Thread::DoAppropriateWait+0x60, calling clr!Thread::DoAppropriateWaitWorker
09d2e8b4 6baa4f17 clr!CLREvent::WaitEx+0x106, calling clr!Thread::DoAppropriateWait
09d2e8e0 6baa48b4 clr!CLREvtTickCount64+0x6b, calling clr!_allmul
09d2e908 6ba44d09 clr!CLREvent::Wait+0x19, calling clr!CLREvent::WaitEx
[...]

