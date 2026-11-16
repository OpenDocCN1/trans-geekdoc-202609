

```
6: 00170000
Segment at 00170000 to 00180000 (00008000 bytes committed)
7: 013b0000
Segment at 013b0000 to 013c0000 (00003000 bytes committed)
```

但 GC 堆以及其中 Leak 和 System.Byte[][] 对象的数量显著增长：

```
Process Uptime: 0 days 0:00:04.000

0:000> !eeheap -gc
Number of GC Heaps: 1
generation 0 starts at 0x013c1018
generation 1 starts at 0x013c100c
generation 2 starts at 0x013c1000
ephemeral segment allocation context: (0x013cd804, 0x013cdff4)
segment begin allocated size
0055ee08 790d7ae4 790f7064 0x0001f580(128384)
013c0000 013c1000 013cdff4 0x0000cff4(53236)
Large object heap starts at 0x023c1000
segment begin allocated size
023c0000 023c1000 023c3250 0x00002250(8784)
Total Size 0x2e7c4(190404)
------------------------
GC Heap Size 0x2e7c4(190404)
```

```
0:000> !dumpheap -stat
total 2176 objects
Statistics:
              Count    TotalSize Class Name
...
...
...
             46      736 CLRHeapLeak.Leak
              5      8816 System.Object[]
             46    47656  System.Byte[]
           2035   129604  System.String
Total 2176 objects
```

```
Process Uptime: 0 days 0:09:56.000

0:000> !eeheap -gc
Number of GC Heaps: 1
generation 0 starts at 0x018cddbc
generation 1 starts at 0x01541ec4
generation 2 starts at 0x013c1000
ephemeral segment allocation context: (0x0192d668, 0x0192ddc8)
segment begin allocated size
0055ee08 790d7ae4 790f7064 0x0001f580(128384)
013c0000 013c1000 0192ddc8 0x0056cdc8(5688776)
Large object heap starts at 0x023c1000
segment begin allocated size
023c0000 023c1000 023c3240 0x00002240(8768)
Total Size 0x58e588(5825928)
-----------------
GC Heap Size 0x58e588(5825928)

0:000> !dumpheap -stat
total 12887 objects
Statistics:
Count   TotalSize Class Name
...
...
5       8816 System.Object[]
5403    86448 CLRHeapLeak.Leak
2026    128632 System.String
5403    5597508 System.Byte[]
Total 12887 objects
```

进程运行时间：0 天 0:16:33.000

```
0:000> !eeheap -gc
Number of GC Heaps: 1
generation 0 starts at 0x01c59cb4
generation 1 starts at 0x0194fd20
generation 2 starts at 0x01c13f000
ephemeral segment allocation context: (0x01cd3050, 0x01cd3cc0)
  segment   begin allocated  size
0055ee08 790d7ae4  790f7064  0x0001f580(128384)
013c0000 013c1000  01cd3cc0  0x0091f2cc0(9514176)
Large object heap starts at 0x023c1000
  segment   begin allocated  size
023c0000 023c1000  023c3240  0x00002240(8768)
Total Size  0x934480(9651328)
-----------------
GC Heap Size  0x934480(9651328)

0:000> !dumpheap -stat
total 20164 objects
Statistics:
Count   TotalSize Class Name
5       8816 System.Object[]
2026    128632 System.String
9038    144608 CLRHeapLeak.Leak
9038    9363368 System.Byte[]
Total 20164 objects
```

这不是传统的内存泄漏，因为我们有引用链。但是，不受控制的内存增长也可以被视为内存泄漏，原因可能是应用程序设计不良、输入验证不当或错误处理等问题。

有些情况下客户认为存在内存泄漏，但实际上并非如此。其中一种情况是在多处理器服务器上运行时进程大小异常巨大。如果托管典型 .NET 程序集 DLL 的 dllhost.exe 在本地工作站上占用少于 100Mb，而在 4 处理器服务器上开始占用超过 300Mb，那么很可能是服务器版本的 CLR 使用了按处理器划分的 GC 堆：

```
0:000> .loadby sos mscorsvr

0:000> !EEHeap -gc
generation 0 starts at 0x05c80154
generation 1 starts at 0x05c7720c
generation 2 starts at 0x102d0030
generation 0 starts at 0x179a0444
generation 1 starts at 0x1799b7a4
generation 2 starts at 0x142d0030
generation 0 starts at 0x0999ac88
generation 1 starts at 0x09990cc4
generation 2 starts at 0x182d0030
generation 0 starts at 0x242eccb0
generation 1 starts at 0x242d0030
generation 2 starts at 0x1c2d0030
...
...
...
GC Heap Size 0x109702ec(278332140)
```

或者如果是 CLR 1.x，旧扩展也会告诉我们同样的情况：

```
0:000> !.\clr10\sos.eeheap -gc
Loaded Son of Strike data table version 5 from
"C:\WINDOWS\Microsoft.NET\Framework\v1.1.4322\mscorsvr.dll"
Number of GC Heaps: 4
--------------------------------
Heap 0 (0x000f9af0)
generation 0 starts at 0x05c80154
generation 1 starts at 0x05c7720c
generation 2 starts at 0x102d0030
...
...
...
Heap Size 0x515ed60(85,323,104)
--------------------------------
Heap 1 (0x000fa070)
generation 0 starts at 0x179a0444
generation 1 starts at 0x1799b7a4
generation 2 starts at 0x142d0030
...
...
...
Heap Size 0x37c7bf0(58,489,840)
--------------------------------
Heap 2 (0x000ffab80)
generation 0 starts at 0x0999ac88
generation 1 starts at 0x09990cc4
generation 2 starts at 0x182d0030
...
...
...
Heap Size 0x485de34(75,882,036)
--------------------------------
Heap 3 (0x000fb448)
generation 0 starts at 0x242eccb0
generation 1 starts at 0x242d0030
generation 2 starts at 0x1c2d0030
...
...
...
Heap Size 0x41ea570(69,117,296)
------------------------
Reserved segments:
------------------------
GC Heap Size 0x1136ecf4(288,812,276)
```

处理器越多，对总 VM 大小贡献的堆就越多。虽然进程占用将近 400Mb，但如果之后不持续超过该值地随时间增长，则属于正常现象。

## 注释

我们也可以通过 !DumpHeap -mt 获取特定对象，然后通过 !gcroot 获取其在特定堆栈上的可能根。

有时候，并非泄漏，只是某种分布异常（参见“对象分布异常”，第 756 页）。

## I/O 完成包

这是“内存不足（内核池）”模式的一个专用形式（第 535 页）。与其他内核池标记相比，该模式目前提供的独特诊断是：池分配条目显示了泄漏进程：

```
0: kd> !poolused 3
Sorting by NonPaged Pool Consumed

Pool Used:
NonPaged
        Paged
Tag  Allocs  Frees  Diff   Used   Allocs  Frees  Diff   Used
Icp  1294074 42875  1251199 96642976 0      0      0      0    I/O completion packets queue
on a completion ports
[...]
```

```
0: kd> !poolfind Icp

Scanning large pool allocation table for Tag: Icp (fffffa8013e00000 : fffffa8014100000)

*fffffa800e188260 size: 50 previous size: 40 (Allocated) Icp Process: fffffa800899dc40
*fffffa800e1882e0 size: 50 previous size: 30 (Allocated) Icp Process: fffffa800899dc40
*fffffa800e188330 size: 50 previous size: 50 (Allocated) Icp Process: fffffa800899dc40
*fffffa800e188380 size: 50 previous size: 50 (Allocated) Icp Process: fffffa800899dc40
*fffffa800e1883d0 size: 50 previous size: 50 (Allocated) Icp Process: fffffa800899dc40
*fffffa800e188420 size: 50 previous size: 50 (Allocated) Icp Process: fffffa800899dc40
*fffffa800e188470 size: 50 previous size: 50 (Allocated) Icp Process: fffffa800899dc40
*fffffa800e1884c0 size: 50 previous size: 50 (Allocated) Icp Process: fffffa800899dc40
```

```
0: kd> !process fffffa800899dc40 1
PROCESS fffffa800899dc40
SessionId: 0 Cid: 434 Peb: 7efdf000 ParentCid: 0412
DirBase: 09d6b000 ObjectTable: fffffff8a0046c8c10 HandleCount: 1068.
Image: ServiceA.exe
[...]
```

## 页表

有时我们会遇到与页表数量增长相关的内存泄漏。其中一个原因可能是**僵尸进程**数量的增加，当它们达到数以万计时会很明显。

```
1: kd> !process 0 0
[...]
PROCESS fffffff8026bd6f0
SessionId: 0 Cid: 0a6c Peb: 7fffffdc000 ParentCid: 03ac
    DirBase: 9d35a000 ObjectTable: fffffff8a00170ac80 HandleCount: 152.
Image: svchost.exe
[...]
PROCESS ffffffa8027de9b30
SessionId: 0 Cid: 21d0 Peb: 7fffffdfd000 ParentCid: 02e0
    DirBase: 37881000 ObjectTable: 00000000 HandleCount: 0.
Image: conhost.exe
[...]
PROCESS ffffffa8028eb0600
SessionId: 0 Cid: ab88 Peb: 7fffffdfd000 ParentCid: 02e0
    DirBase: 27a2f000 ObjectTable: 00000000 HandleCount: 0.
Image: conhost.exe
[...]
```

即使是僵尸进程，也至少保留了一个来自其虚拟到物理内存映射之前的页表的页面（页目录）（!dd 与 dd WinDbg 命令相同，但用于物理内存）：

```
1: kd> !dd 9d35a000
#9d35a000 9d62867 03c00000 00000000 00000000
#9d35a010 00000000 00000000 00000000 00000000
#9d35a020 00000000 00000000 00000000 00000000
#9d35a030 00000000 00000000 00000000 00000000
#9d35a040 00000000 00000000 00000000 00000000
#9d35a050 00000000 00000000 00000000 00000000
#9d35a060 00000000 00000000 00000000 00000000
#9d35a070 00000000 00000000 9d45e867 49500000
```

```
1: kd> !dd 37881000
#37881000 00000000 00000000 00000000 00000000
#37881010 00000000 00000000 00000000 00000000
#37881020 00000000 00000000 00000000 00000000
#37881030 00000000 00000000 00000000 00000000
#37881040 00000000 00000000 00000000 00000000
#37881050 00000000 00000000 00000000 00000000
#37881060 00000000 00000000 00000000 00000000
#37881070 00000000 00000000 00000000 00000000
```

```
1: kd> !dd 27a2f000
#27a2f000 00000000 00000000 00000000 00000000
#27a2f010 00000000 00000000 00000000 00000000
#27a2f020 00000000 00000000 00000000 00000000
#27a2f030 00000000 00000000 00000000 00000000
#27a2f040 00000000 00000000 00000000 00000000
#27a2f050 00000000 00000000 00000000 00000000
```

