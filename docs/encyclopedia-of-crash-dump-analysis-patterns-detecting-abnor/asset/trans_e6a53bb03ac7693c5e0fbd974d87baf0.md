

| 按使用量划分的最大区域 | 基址 | 区域大小 |
| :--- | :--- | :--- |
| 空闲 | 3f0c0000 | 33050000 ( 816.313 Mb) |
| <未分类> | 158a1000 | fcf000 ( 15.809 Mb) |
| 映像 | 1083000 | 3d1000 ( 3.816 Mb) |
| 堆栈 | 2000000 | fd000 (1012.000 kb) |
| 内存映射文件 | 7efe5000 | fb000 (1004.000 kb) |
| TEB | 7efda000 | 1000 ( 4.000 kb) |
| PEB | 7efde000 | 1000 ( 4.000 kb) |

我们看到可用于分配的空闲内存仅为 816 Mb。

## 会话池

虽然我们在“内存不足（内核池）”模式（第 535 页）中简要提及过会话池，但我们将其单独列为一个（子）模式，以提供用于分析可能泄漏的 WinDbg 命令。以下输出显示了一组命令序列，可大致了解情况，尽管示例本身来自于一个健康的转储，因此没有加粗的高亮内容（我们之前发现会话池中的泄漏主要发生在 32 位情况中）：

```
1: kd> !vm 4

Terminal Server Memory Usage By Session:

Session ID 0 @ ffffff8800324d000:
Paged Pool Usage:      4128K
Commit Usage:          7488K

Session ID 1 @ ffffff88002f65000:
Paged Pool Usage:      32852K
Commit Usage:         36488K
```

```
1: kd> !session
Sessions on machine: 2
Valid Sessions: 0 1
Error in reading current session
```

```
1: kd> !session -s 1
Sessions on machine: 2
Implicit process is now ffffffa80`07d79730
Using session 1
```

```
1: kd> !pooled 8
Sorting by Session Tag

Pool Used:
NonPaged       Paged
Tag  Allocs   Used   Allocs   Used
TOTAL          4      4208   9500   33475120
[...]
```

## 堆栈跟踪数据库

我们曾看到一组进程内存转储，其中最大的几乎有 4GB。它们全部来自内存消耗最初为 200MB 且持续增长的进程。起初，我们怀疑是进程堆 内存泄漏（第 650 页）。然而，堆统计信息（!heap -s）是正常的。甚至没有大块分配 119。转储还附带了 UMDH 日志，但它们的差异只显示了内存波动（第 634 页），而非增长。堆栈跟踪收集（第 933 页）揭示了一个飙升线程（第 885 页）正在将堆分配记录到用户模式堆栈跟踪数据库中。我们还可以看到这是分布式飙升（第 243 页）。对地址空间的检查显示，有大量相同大小的连续区域，其中包含堆栈跟踪数据库（第 919 页）条目。因此，我们得出结论，这是堆栈跟踪日志记录 插装副作用（第 520 页），并建议在 gflags.exe 中限制堆栈回溯大小。

为确保我们正确理解了该问题，我们决定对其进行建模。由于日志记录实现不同，我们可能未得到相同的结果，但内存转储清楚地显示了内存不足模式变体的可能性。以下是源代码：

```
void foo20 (int size)
{
    free(malloc(size));
}

#define FOO(x,y) void foo##x (int size) { foo##y(size); }

FOO(19,20)
FOO(18,19)
FOO(17,18)
FOO(16,17)
FOO(15,16)
FOO(14,15)
FOO(13,14)
FOO(12,13)
FOO(11,12)
FOO(10,11)
FOO(9,10)
FOO(8,9)
FOO(7,8)
FOO(6,7)
FOO(5,6)
FOO(4,5)
FOO(3,4)
FOO(2,3)
FOO(1,2)

typedef void (*PFN) (int);

#define ARRSZ 20
```

119 软件行为模型，内存泄漏（进程堆）模式，内存转储分析文集，第 5 卷，第 315 页

```
PFN pfnArr[ARRSZ] = {foo1, foo2, foo3, foo4, foo5, foo6, foo7,
    foo8, foo9, foo10, foo11, foo12, foo13, foo14,
    foo15, foo16, foo17, foo18, foo19, foo20};

int __tmain(int argc, _TCHAR* argv[])
{
    int i;
    for (i = 1; i < 1000000000; ++i)
    {
        pfnArr[i%ARRSZ](i);
    }

    Sleep(-1);
    return 0;
}
```

它分配然后释放大小从 1 字节到 1,000,000,000 字节的不同堆条目，所有条目都有 20 种可能的不同堆栈跟踪。我们选择不同的堆栈跟踪，以增加不同 {大小，堆栈回溯} 对的数量，因为大小相似且具有相同堆栈跟踪的多次分配在数据库中可能只记录一次。我们通过调用 pfnArr 中的不同条目来模拟不同的堆栈跟踪。每次调用随后都会导致 foo20，但生成的堆栈跟踪深度不同。我们还为名为 AlloCFree.exe 的应用程序在 gflags.exe 中启用了“创建用户模式堆栈跟踪数据库”复选框。

然后我们看到 **堆栈跟踪数据库** 区域的扩展（地址不同，因为内存转储来自不同的应用程序运行）：

```
0:000> !address
[...]
    : Start      End        Size
+ 0'00240000 0'00312000 0'000d2000 MEM_PRIVATE MEM_COMMIT PAGE_READWRITE Other [Stack Trace Database]
0'00312000 0'01a37000 0'01725000 MEM_PRIVATE MEM_RESERVE Other [Stack Trace Database]
0'01a37000 0'01a40000 0'00009000 MEM_PRIVATE MEM_COMMIT PAGE_READWRITE Other [Stack Trace Database]
```

```
0:000> !address
[...]
+ 0'001b0000 0'0188c000 0'016dc000 MEM_PRIVATE MEM_COMMIT PAGE_READWRITE Other [Stack Trace Database]
0'0188c000 0'0188d000 0'00001000 MEM_PRIVATE MEM_RESERVE Other [Stack Trace Database]
0'0188d000 0'019b0000 0'00123000 MEM_PRIVATE MEM_COMMIT PAGE_READWRITE Other [Stack Trace Database]
```

堆保持不变：

```
0:000> !heap -s
NtGlobalFlag enables following debugging aids for new heaps:
    stack back traces
LFH Key                   : 0x000000f841c4f9c0
Termination on corruption : ENABLED
      Heap     Flags   Reserve   Commit   Virt   Free   List   UCR   Virt   Lock   Fast
                        (k)     (k)     (k)     (k)   length      blocks cont. heap
-------------------------------------------------------------------------------------
0000000001a40000 00000002    4096    1444    4096    1164     4     3     0     0   LFH
  External fragmentation  80 % (4 free blocks)
0000000000010000 00008000       64       4      64       1     1     1     0     0
0000000000020000 00008000       64      64      64      61     1     1     0     0
-------------------------------------------------------------------------------------
```

```
0:000> !heap -s
NtGlobalFlag enables following debugging aids for new heaps:
    stack back traces
LFH Key                   : 0x0000000473a639107
Termination on corruption : ENABLED
      Heap     Flags   Reserve   Commit   Virt   Free   List   UCR   Virt   Lock   Fast
                        (k)     (k)     (k)     (k)   length      blocks cont. heap
-------------------------------------------------------------------------------------
00000000019c0000 00000002    4096    1444    4096    1164     4     3     0     0
LFH
  External fragmentation  80 % (4 free blocks)
0000000000010000 00008000       64       4      64       1     1     1     0     0
0000000000020000 00008000       64      64      64      61     1     1     0     0
-------------------------------------------------------------------------------------
```

然而，我们看到该线程占用大量 CPU（**飙升线程**，第 888 页），并且它在记录堆栈回溯时被捕获：

```
0:000> kc
Call Site
ntdll!RtlpStdLogCapturedStackTrace
ntdll!RtlStdLogStackTrace
ntdll!RtlLogStackBackTraceEx
ntdll!RtlpAllocateHeap
ntdll!RtlAllocateHeap
AllocFree!heap_alloc
AllocFree!malloc
AllocFree!foo20
AllocFree!foo19
AllocFree!foo18
AllocFree!foo17
AllocFree!foo16
AllocFree!foo15
AllocFree!foo14
AllocFree!foo13
AllocFree!foo12
AllocFree!foo11
AllocFree!foo10
AllocFree!foo9
AllocFree!foo8
AllocFree!foo7
AllocFree!foo6
AllocFree!foo5
AllocFree!foo4
AllocFree!foo3
AllocFree!foo2
AllocFree!foo1
AllocFree!wmain
AllocFree!_tmainCRTStartup
kernel32!BaseThreadInitThunk
ntdll!RtlUserThreadStart
```

```
0:000> !runaway f
 User Mode Time
  Thread    Time
  0:53b8    0 days 3:22:02.354
 Kernel Mode Time
  Thread    Time
  0:53b8    0 days 0:20:39.022
 Elapsed Time
  Thread    Time
  0:53b8    0 days 10:11:23.596
```

如果转储区域的一部分，我们可以看到记录的堆栈回溯：

```
0:000> dps 0`0188c000-200 L200/8
00000000`0188be00 00000000`77891142 ntdll!RtlpAllocateHeap+0x33bd
00000000`0188be08 00000000`778834d8 ntdll!RtlAllocateHeap+0x16c
00000000`0188be10 00000001`3fc13cb4 AllocFree!malloc+0x5b
00000000`0188be18 00000001`3ffc1015 AllocFree!foo20+0x15
00000000`0188be20 00000001`3ffc1041 AllocFree!foo19+0x11
00000000`0188be28 00000001`3ffc1061 AllocFree!foo18+0x11
00000000`0188be30 00000001`3ffc12e3 AllocFree!wmain+0x53
00000000`0188be38 00000001`3ffc156c AllocFree!__tmainCRTStartup+0x144
00000000`0188be40 00000000`777259ed kernel32!BaseThreadInitThunk+0xd
00000000`0188be48 00000000`7785c541 ntdll!RtlUserThreadStart+0x1d
00000000`0188be50 00000000`0188b1d0
00000000`0188be58 0009457d`00024fff
00000000`0188be60 00000000`77891142 ntdll!RtlpAllocateHeap+0x33bd
00000000`0188be68 00000000`778834d8 ntdll!RtlAllocateHeap+0x16c
00000000`0188be70 00000001`3ffc13cb AllocFree!malloc+0x5b
00000000`0188be78 00000001`3ffc1015 AllocFree!foo20+0x15
00000000`0188be80 00000001`3ffc1041 AllocFree!foo19+0x11
00000000`0188be88 00000001`3ffc12e3 AllocFree!wmain+0x53
00000000`0188be90 00000001`3ffc156c AllocFree!__tmainCRTStartup+0x144
00000000`0188be98 00000000`777259ed kernel32!BaseThreadInitThunk+0xd
00000000`0188bea0 00000000`7785c541 ntdll!RtlUserThreadStart+0x1d
00000000`0188bea8 00000000`00000000
00000000`0188beb0 00000000`0188b230
00000000`0188beb8 0008457e`00023fff
00000000`0188bec0 00000000`77891142 ntdll!RtlpAllocateHeap+0x33bd
00000000`0188bec8 00000000`778834d8 ntdll!RtlAllocateHeap+0x16c
00000000`0188bed0 00000001`3ffc13cb AllocFree!malloc+0x5b
00000000`0188bed8 00000001`3ffc1015 AllocFree!foo20+0x15
00000000`0188beee 00000001`3ffc12e3 AllocFree!wmain+0x53
```

