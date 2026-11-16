

## 注释

在某些缺少 !runaway 信息的旧版转储中，如果线程执行某种窥探消息循环，我们可以推测出飙升线程：

```
0:012> !runaway
ERROR: !runaway: extension exception 0x80004002.
"Unable to get thread times - dumps may not have time information"

6 Id: 136c.13bc Suspend: 1 Teb: 7ffd8000 Unfrozen
ChildEBP RetAddr  Args to Child
0198f914 5b2d887c 0198f938 00000000 00000000 USER32!PeekMessageA+0xfb
0198fa20 5b2d3b87 059d6704 00000000 00000000 ModuleA!Choose+0x177
[...]

0:012> ~6s
eax=0000abbb ebx=00000400 ecx=00000200 edx=00000abb esi=7ffd8000 edi=0066b3e0
eip=7e42ae35 esp=0198f908 ebp=0198f914 iopl=0 nv up ei pl nz na pe nc
cs=001b ss=0023 ds=0023 es=0023 fs=003b gs=0000 efl=00040206
USER32!PeekMessageA+0xfb:
7e42a3e5 2b470c sub eax,dword ptr [edi+0Ch] ds:0023:0066b3ec=000abbbd
```

将其与“线程年龄”模式（第 1001 页）结合使用也很有用，以查看飙升的幅度：

```
Process Uptime: 0 days 17:35:06.000
```

如果我们查看线程 CPU 消耗，与整个进程运行时间相比，飙升值相对较小：

```
0:000> !runaway f
User Mode Time
Thread Time
4:1560   0 days 0:00:08.034
7:7e0   0 days 0:00:03.338
11:1244 0 days 0:00:03.213
8:1510   0 days 0:00:02.324
3:86c   0 days 0:00:00.015
[...]
```

然而，与“线程年龄”相比，它们要大得多：

```
Elapsed Time
Thread Time
[...]
3:86c   0 days 17:35:05.213
4:1560  0 days 0:02:12.350
[...]
7:7e0  0 days 0:00:22.429
11:1244  0 days 0:00:17.655
```

如何使用 WinDbg 脚本从内核和完整内存转储中获取飙升线程（第 190 页）。

在内核转储中，我们可以使用此命令查看所有运行线程的堆栈：

```
!running -t
```

在完整内存转储中执行该命令时，如果线程进程上下文与当前 CPU 上的当前进程不同，则用户部分无效，因此建议通过 !thread 1f 进行手动线程检查。

## Stack Overflow

### Linux

这是以前针对 Mac OS X（第 897 页）和 Windows（第 912 页）平台描述过的 **栈溢出**（用户模式）模式的 Linux 变体：

```
(gdb) bt
#0 0x00000000004004fb in procF ()
#1 0x000000000040054b in procF ()
#2 0x000000000040054b in procF ()
#3 0x000000000040054b in procF ()
#4 0x000000000040054b in procF ()
#5 0x000000000040054b in procF ()
#6 0x000000000040054b in procF ()
#7 0x000000000040054b in procF ()
#8 0x000000000040054b in procF ()
#9 0x000000000040054b in procF ()
#10 0x000000000040054b in procF ()
#11 0x000000000040054b in procF ()
#12 0x000000000040054b in procF ()
[...]
```

```
(gdb) bt -10
#15409 0x000000000040054b in procF ()
#15410 0x000000000040054b in procF ()
#15411 0x000000000040054b in procF ()
#15412 0x000000000040055b in procF ()
#15413 0x0000000000400575 in bar_one ()
#15414 0x0000000000400585 in foo_one ()
#15415 0x000000000040059d in thread_one ()
#15416 0x0000000000401690 in start_thread (arg=<optimized out>)
 at pthread_create.c:304
#15417 0x0000000000432549 in clone ()
#15418 0x0000000000000000 in ?? ()
```

在栈溢出的情况下，栈指针会递减超出栈区域边界进入不可访问区域，因此任何栈内存访问都会触发访问违例：

```
(gdb) x $rsp
0x7eff46109ec0: 0x0

(gdb) frame 1
#1 0x000000000040054b in procF ()

(gdb) x $rsp
0x7eff4610a0e0: 0x0
(gdb) maintenance info sections
[...]
Core file:
[...]
0x7eff46109000->0x7eff4610a000 at 0x02034000: Load13 ALLOC LOAD READONLY HAS_CONTENTS
0x7eff4610a000->0x7eff461090a000 at 0x02035000: load14 ALLOC LOAD HAS_CONTENTS
[...]
```

### Mac OS X

这是 Mac OS X / GDB 中对应于栈溢出（用户模式）模式的示例：

```
(gdb) bt 10
#0 0x0000000105dafea8 in bar (i=0)
#1 0x0000000105dafe9 in bar (i=262102)
#2 0x0000000105dafe9 in bar (i=262101)
#3 0x0000000105dafe9 in bar (i=262100)
#4 0x0000000105dafe9 in bar (i=262099)
#5 0x0000000105dafe9 in bar (i=262098)
#6 0x0000000105dafe9 in bar (i=262097)
#7 0x0000000105dafe9 in bar (i=262096)
#8 0x0000000105dafe9 in bar (i=262095)
#9 0x0000000105dafe9 in bar (i=262094)
(More stack frames follow...)

```

至少有 262,102 个帧，因此我们不尝试全部列出。我们想做的是根据当前栈指针地址从节列表中获取堆栈跟踪边界，并转储其上半部分（栈从高地址向低地址增长），以获取底部初始堆栈跟踪：

```
(gdb) x $rsp
0x7fff651aeff0: 0x00000000
```

由于这是栈溢出，我们预期 RSP 已超出页边界，并且预期最低地址为 0x7fff651af000。

```
(gdb) maint info sections
[...]
Core file:
`/cores/core.2763', file type mach-o-le.
[...]
0x0000000105e00000->0x0000000105f00000 at 0x00035000: LC_SEGMENT. ALLOC LOAD CODE HAS_CONTENTS
0x00007fff651af000->0x00007fff651af000 at 0x00135000: LC_SEGMENT. ALLOC LOAD CODE HAS_CONTENTS
0x00007fff651af000->0x00007fff651af000 at 0x03935000: LC_SEGMENT. ALLOC LOAD CODE HAS_CONTENTS
0x00007fff659af000->0x00007fff6599e400 at 0x04135000: LC_SEGMENT. ALLOC LOAD CODE HAS_CONTENTS
0x00007fff6599e400->0x00007fff6599e6000 at 0x0416a000: LC_SEGMENT. ALLOC LOAD CODE HAS_CONTENTS
[...]

```

```
(gdb) x/250a 0x00007fff659a0000-2000
0x7fff659a830: 0x0 0x150000000
0x7fff659a840: 0x7fff659ae860 0x105dafe9 <bar+25>
0x7fff659a850: 0x0 0x140000000
0x7fff659a860: 0x7fff659ae880 0x105dafe9 <bar+25>
0x7fff659a870: 0x0 0x130000000
0x7fff659a880: 0x7fff659ae8a0 0x105dafe9 <bar+25>
0x7fff659a890: 0x0 0x120000000
0x7fff659a8a0: 0x7fff659ae8c0 0x105dafe9 <bar+25>
0x7fff659a8b0: 0x0 0x110000000
0x7fff659a8c0: 0x7fff659ae8e0 0x105dafe9 <bar+25>
0x7fff659a8d0: 0x0 0x100000000
0x7fff659a8e0: 0x7fff659ae900 0x105dafe9 <bar+25>
0x7fff659ae8f0: 0x0 0xf000000000
0x7fff659ae900: 0x7fff659ae920 0x105dafeb9 <bar+25>
0x7fff659ae910: 0x0 0xe000000000
0x7fff659ae920: 0x7fff659ae940 0x105dafeb9 <bar+25>
0x7fff659ae930: 0x0 0xd000000000
0x7fff659ae940: 0x7fff659ae960 0x105dafeb9 <bar+25>
0x7fff659ae950: 0x0 0xc000000000
0x7fff659ae960: 0x7fff659ae980 0x105dafeb9 <bar+25>
0x7fff659ae970: 0x0 0xb000000000
0x7fff659ae980: 0x7fff659ae9a0 0x105dafeb9 <bar+25>
0x7fff659ae990: 0x0 0xa000000000
0x7fff659ae9a0: 0x7fff659ae9c0 0x105dafeb9 <bar+25>
0x7fff659ae9b0: 0x0 0x9000000000
0x7fff659ae9c0: 0x7fff659ae9e0 0x105dafeb9 <bar+25>
0x7fff659ae9d0: 0x0 0x8000000000
0x7fff659ae9e0: 0x7fff659aea00 0x105dafeb9 <bar+25>
0x7fff659ae9f0: 0x0 0x7000000000
0x7fff659aea00: 0x7fff659aea20 0x105dafeb9 <bar+25>
0x7fff659aea10: 0x0 0x6000000000
0x7fff659aea20: 0x7fff659aea40 0x105dafeb9 <bar+25>
0x7fff659aea30: 0x0 0x565b9fe0
0x7fff659aea40: 0x7fff659aea60 0x105dafeb9 <bar+25>
0x7fff659aea50: 0x7fff659aea70 0x4659bd31f
0x7fff659aea60: 0x7fff659aea80 0x105dafeb9 <bar+25>
0x7fff659aea70: 0x7fff659aeaf0 0x3659b031a
0x7fff659aea80: 0x7fff659aeaa0 0x105dafeb9 <bar+25>
0x7fff659aea90: 0x7fff659af5c0 0x2000000000
0x7fff659aeaa0: 0x7fff659aeac0 0x105dafeb9 <bar+25>
0x7fff659aeab0: 0x100000000 0x1659aeb18
0x7fff659aeac0: 0x7fff659aead0 0x105dafefe <foo+14>
0x7fff659aead0: 0x7fff659aeaf0 0x105dafefeb <main+27>
0x7fff659aeae0: 0x7fff659aeb18 0x1
-Type to continue, or q to quit--
0x7fff659aeaf0: 0x7fff659aeb08 0x105daf94 <start+52>
0x7fff659aeb00: 0x0 0x0
[...]
0x7fff659aefff: 0x3139336561303363 0x3162235
```

有趣的是，如果我们将最低帧设置下来，并尝试在 GDB 核心转储中获取寄存器信息：

```
(gdb) frame 262102
#262102 0x0000000105dafeb9 in bar (i=1)
13 bar(i+1);
(gdb) info r
Segmentation fault: 11 (core dumped)
```

查看其核心转储显示它也经历了栈溢出：

```
(gdb) bt
#0 0x00007ff8c1bacf0 in __sfvwrite ()
#1 0x00007ffff8c189947 in __vfprintf ()
#2 0x00007fff8c184edb in vsnprintf_l ()
#3 0x00007ff8c1566be in __sprint_chk ()
#4 0x00000001bd14d515 in print_displacement ()
#5 0x00000001bd010ddf in OP_E ()
#6 0x00000001bd13f9b in print_insn ()
#7 0x00000001bc164ce in length_of_this_instruction ()
#8 0x00000001bc9e296 in x86_analyze_prologue ()
#9 0x00000001bc9f1f3 in x86_frame_prev_register ()
#10 0x00000001bc91d70 in frame_register_unwind ()
#11 0x00000001bc92015 in frame_unwind_register ()
#12 0x00000001bc91d70 in frame_register_unwind ()
#13 0x00000001bc92015 in frame_unwind_register ()
#14 0x00000001bc91d70 in frame_register_unwind ()
#15 0x00000001bc92015 in frame_unwind_register ()
#16 0x00000001bc91d70 in frame_register_unwind ()
#17 0x00000001bc92015 in frame_unwind_register ()
#18 0x00000001bc91d70 in frame_register_unwind ()
#19 0x00000001bc92015 in frame_unwind_register ()
#20 0x00000001bc91d70 in frame_register_unwind ()
#21 0x00000001bc92015 in frame_unwind_register ()
#22 0x00000001bc91d70 in frame_register_unwind ()
#23 0x00000001bc92015 in frame_unwind_register ()
#24 0x00000001bc91d70 in frame_register_unwind ()
#25 0x00000001bc92015 in frame_unwind_register ()
#26 0x00000001bc91d70 in frame_register_unwind ()
#27 0x00000001bc92015 in frame_unwind_register ()
#28 0x00000001bc91d70 in frame_register_unwind ()
#29 0x00000001bc92015 in frame_unwind_register ()
#30 0x00000001bc91d70 in frame_register_unwind ()
#31 0x00000001bc92015 in frame_unwind_register ()
[...]
```

我们建模应用程序的源代码：

```
void bar(int i)
{
    bar(i+1);
}

void foo()
{
    bar(1);
}

int main(int argc, const char * argv[])
{
    foo();
    return 0;
}
```

