

```
0bf10000 00001003 256 4 4
0bf50000 00001003 256 4 4
0bf90000 00001003 256 4 4
0b660000 00001002 64 20 20
00870000 00001002 64 20 20
0d760000 00001002 256 12 12
0dc60000 00001002 1088 220 220
0c3a0000 00001002 64 12 12
0c3d0000 00001002 1088 160 364
08420000 00001002 64 64 64
```

## 第 2 转储

```
0:000> !heap -s
Heap Flags Reserv Commit Virt
(k) (k) (k)
----------------------------------
00140000 00000002 8192 4600 4600
00240000 00008000 64 12 12
00310000 00001000 7232 4516 4600
00420000 00001002 1024 520 520
00340000 00001002 256 44 44
00720000 00001002 64 32 32
00760000 00001002 64 48 48
01020000 00001002 256 24 24
02060000 00001002 64 16 16
02070000 00001003 256 124 124
020b0000 00001003 256 4 4
020f0000 00001003 256 4 4
02130000 00001003 256 4 4
02170000 00001003 256 4 4
021f0000 00001002 1088 76 76
021e0000 00001002 64 16 16
02330000 00001002 1088 428 428
02340000 00011002 256 12 12
02380000 00001002 64 12 12
024c0000 00001003 64 8 8
028d0000 00001002 7232 3796 6768
02ce0000 00001003 64 8 8
07710000 00001002 64 20 20
07b20000 00001002 64 16 16
07f30000 00001002 64 16 16
09050000 00001002 256 12 12
09c80000 00001002 261376 221152 22928
007d0000 00001003 256 192 192
00810000 00001003 256 4 4
0bbd0000 00001003 256 4 4
0be10000 00001003 256 4 4
0be50000 00001003 256 4 4
0be90000 00001003 256 60 60
0bed0000 00001003 256 4 4
0bf10000 00001003 256 4 4
0bf50000 00001003 256 4 4
0bf90000 00001003 256 4 4
0b660000 00001002 64 20 20
00870000 00001002 64 20 20
```

| 0d760000 | 00001002 | 256 | 12 | 12 |
| 0dc60000 | 00001002 | 1088 | 228 | 228 |
| 0c3a0000 | 00001002 | 64 | 12 | 12 |
| 0c3d0000 | 00001002 | 1088 | 168 | 224 |
| 08450000 | 00001002 | 64 | 64 | 64 |

我们可以看到，唯一显著的堆增长出现在 09c80000 地址，从 130Mb 增长到 260Mb。然而，这并没有说明是哪段代码在使用它。为了找到这段代码，我们需要启用所谓的用户模式堆栈跟踪数据库。请参阅 Citrix 文章了解如何配置它130。文章中的示例是针对 Citrix IMA 服务的，但我们可以将 ImaSrv.exe 替换为任何其他可执行文件名。

假设在启用用户模式堆栈跟踪数据库并重新启动程序或服务后，我们观察到增长，并获得了带有以下加粗突出显示的可疑堆的内存转储：

```
0:000> !gflag
Current NtGlobalFlag contents: 0x00001000
ust - Create user mode stack trace database

0:000> !heap -s
NtGlobalFlag enables following debugging aids for new heaps:
stack back traces
LFH Key: 0x2687ed29
Heap      Flags   Reserv  Commit  Virt
          (k)     (k)     (k)
----------------------------------------
00140000 58000062 4096    488     676
00240000 58008060   64     12     12
00360000 58001062 3136   1152   1216
003b0000 58001062   64     32     32
01690000 58001062  256     32     32
016d0000 58001062 1024    520    520
003e0000 58001062   64     48     48
02310000 58001062  256     24     24
02b30000 58001062   64     16     16
02b40000 58001063  256     64     64
02b80000 58001063  256      4      4
02bc0000 58001063  256      4      4
02c00000 58001063  256      4      4
02c40000 58001063  256      4      4
02c80000 58001063  256      4      4
02cc0000 58001063  256      4      4
02d30000 58001063   64      4      4
03140000 58001062 7232   4160   4896
03550000 58001063   64      4      4
07f70000 58001062   64     12     12
08380000 58001062   64     12     12
08790000 58001062   64     12     12
091d0000 58011062  256     12     12
```

| | | | | |
|---|---|---|---|---|
| 09210000 | 58001062 | 64 | 16 | 16 |
| 09220000 | 58001062 | 64 | 12 | 12 |
| 092a0000 | 58001062 | 64 | 12 | 12 |
| 09740000 | 58001062 | 256 | 12 | 12 |
| 0b1a0000 | 58001062 | 64 | 12 | 12 |
| **0b670000** | **58001062** | **64768** | **39508** | **39700** |
| 0b7b0000 | 58001062 | 64 | 12 | 12 |
| 0c650000 | 58001062 | 1088 | 192 | 192 |

每个堆都细分为多个段，要查看哪些段增长最多，可以使用 !heap -m <堆地址> 命令：

```
0:000> !heap -m 0b670000
Index Address Name Debugging options enabled
29: 0b670000
Segment at 0b670000 to 0b6b0000 (00040000 bytes committed)
Segment at 0c760000 to 0c860000 (00100000 bytes committed)
Segment at 0c980000 to 0cb80000 (001fe000 bytes committed)
Segment at 0cb80000 to 0cf80000 (003cc000 bytes committed)
Segment at 0dc30000 to 0e430000 (00800000 bytes committed)
Segment at 12330000 to 13330000 (01000000 bytes committed)
Segment at 13330000 to 15330000 (0078b000 bytes committed)
...
...
...
```

如果使用 !heap -a <堆地址> 命令，除了堆段列表外，还会转储单个堆分配条目。这可能会产生非常大的输出，我们应该提前使用 .logopen <文件名> 命令打开日志文件。

输出可能如下所示（摘自另一个转储）：

```
0:000> !heap -a 000a0000
...
...
...
Segment00 at 000a0000:
Flags: 00000000
Base: 000a0000
First Entry: 000a0580
Last Entry: 000b0000
Total Pages: 00000010
Total UnCommit: 00000002
Largest UnCommit:00000000
UnCommitted Ranges: (1)

Heap entries for Segment00 in Heap 000a0000
000a0000: 00000 . 00580 [101] - busy (57f)
000a0580: 00580 . 00240 [101] - busy (23f)
000a07c0: 00240 . 00248 [101] - busy (22c)
000a0a08: 00248 . 00218 [101] - busy (200)
000a0c20: 00218 . 00ce0 [100]
000a1900: 00ce0 . 00f88 [101] - busy (f6a)
000a2888: 00f88 . 04418 [101] - busy (4400)
000a6ca0: 04418 . 05958 [101] - busy (5940)
000ac5f8: 05958 . 00928 [101] - busy (90c)
000acf20: 00928 . 010c0 [100]
000adfe0: 010c0 . 00020 [111] - busy (1d)
000ae000: 00002000 - uncommitted bytes.
```

然后，我们可以使用 !heap -p -a <堆条目地址> 命令检查单个条目，以查看分配它们的堆栈跟踪：

```
0:000> !heap -p -a 000a6ca0
address 000a6ca0 found in
_HEAP @ a0000
HEAP_ENTRY Size Prev Flags UserPtr UserSize - state
000a6ca0 0b2b 0000 [00] 000a6cb8 5940 - (busy)
Trace: 2156ac
7704dba4 ntdll!RtlAllocateHeap+0x0000021d
75c59b12 USP10!UspAllocCache+0x0000002b
75c62381 USP10!AllocSizeCache+0x00000048
75c61c74 USP10!FindOrCreateSizeCacheWithoutRealizationID+0x00000124
75c61bc0 USP10!FindOrCreateSizeCacheUsingRealizationID+0x00000070
75c59a97 USP10!UpdateCache+0x0000002b
75c59a61 USP10!ScriptCheckCache+0x0000005c
75c59d04 USP10!ScriptStringAnalyse+0x0000012a
7711140f LPK!LpkStringAnalyse+0x00000114
7711159e LPK!LpkCharsetDraw+0x00000302
77111488 LPK!LpkDrawTextEx+0x00000044
76a4beb3 USER32!DT_DrawStr+0x0000013a
76a4be45 USER32!DT_DrawJustifiedLine+0x000005f
76a49d68 USER32!AddEllipsisAndDrawLine+0x00000186
76a4bc31 USER32!DrawTextExWorker+0x00001b1
76a4bedc USER32!DrawTextExW+0x0000001e
746051d8 uxtheme!CTexDraw::GetTextExtent+0x00000be
7460515a uxtheme!GetTextTextExtent+0x0000065
74611ed4 uxtheme!CThemeMenuBar::MeasureItem+0x00000124
746119c1 uxtheme!CThemeMenu::OnMeasureItem+0x000003f
74611978 uxtheme!CThemeWnd::PreDefWindowProc+0x00000117
74601ea5 uxtheme!ThemeDefWindowProc+0x0000090
74601f61 uxtheme!ThemeDefWindowProcW+0x0000018
76a4a09e USER32!DefWindowProc+0x00000068
931406 notepad!NPWndProc+0x00000084
76a51a10 USER32!InternalCallWinProc+0x00000023
76a51ae8 USER32!UserCallWinProcCheckWow+0x0000014b
76a51c03 USER32!DispatchClientMessage+0x00000da
76a3bc24 USER32!_fnINTOUTLPUAHMESSAGEITEM+0x0000027
77040e6e ntdll!KiUserCallbackDispatcher+0x0000002e
76a51d87 USER32!RealDefWindowProcW+0x00000047
74601f2f uxtheme!_ThemeDefWindowProc+0x000001b8
```

如果要转储所有带有相应堆栈跟踪的堆条目，可以使用 !heap -k -h <堆地址> 命令。

有时所有这些命令都不起作用。在这种情况下，我们可以使用旧的 Windows 2000 扩展131。

有些人更喜欢使用 umdh.exe 获取文本日志文件，但将堆分配堆栈跟踪嵌入崩溃转储的优势在于，我们无需在客户现场发送和配置符号文件。

分析堆时，各种 pageheap 选项 !heap -p 非常有用，例如（摘自 WinDbg 帮助）：

> -t[c/s] [Traces]
> 
> “导致调试器显示重度堆用户收集的跟踪。Traces 指定要显示的跟踪数量；默认值为四个。如果跟踪数量多于指定数量，则显示最早的跟踪。如果使用 -t 或 -tc，则按计数用法对跟踪进行排序。如果使用 -ts，则按大小对跟踪进行排序。”

我们也可以使用 Microsoft Debug Diagnostics 工具132。

