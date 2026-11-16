

## 截断转储

Mac OS X

这是 Mac OS X / GDB 中对应于截断转储模式的情况：

```
(gdb) info threads
Cannot access memory at address 0x7fff885e9e42
4 0x00007fff885e9e42 in ?? ()
3 0x00007fff885e9e42 in ?? ()
2 0x00007fff885e9e42 in ?? ()
* 1 0x00007fff885e9e42 in ?? ()
warning: Couldn't restore frame in current thread, at frame 0
0x00007fff885e9e42 in ?? ()

(gdb) disass 0x00007fff885e9e42
No function contains specified address.

(gdb) info r rsp
rsp 0x7fff67fe8a18 0x7fff67fe8a18

(gdb) x/100a 0x7fff67fe8a18
0x7fff67fe8a18: Cannot access memory at address 0x7fff67fe8a18
```

这通常发生在没有足够空间保存完整核心转储时。

## Windows

有时候页面文件大小小于物理内存大小。如果出现这种情况，并且我们在控制面板的“启动和恢复”设置中配置了“完整内存转储”，则会得到 **截断内存转储**。当我们打开此类转储文件时，WinDbg 会打印一条警告：

```
***********************************************************************
WARNING: Dump file has been truncated.  Data may be missing.
***********************************************************************
```

我们可以使用 !vm 命令再次确认：

```
kd> !vm

*** Virtual Memory Usage ***
        Physical Memory:    511859  (  2047436 Kb)
        Paging File Name paged out
        Current:    1536000 Kb  Free Space:   1522732 Kb
        Minimum:    1536000 Kb  Maximum:      1536000 Kb
```

我们看到页面文件大小为 1.5 GB，但物理内存大小为 2 GB。发生蓝屏（BSOD）时，物理内存内容将保存到页面文件中，转储文件大小实际不超过 1.5 GB，从而有效截断了崩溃转储分析所需的数据。

有时我们仍然可以访问截断转储中的一些数据，但需要注意 WinDbg 的提示。例如，在上面所示的 **截断转储** 中，堆栈和驱动程序代码不可用：

```
kd> kv
ChildEBP RetAddr  Args to Child
WARNING: Stack unwind information not available. Following frames may be wrong.
f408b004  00000000 00000000 00000000 00000000 driver+0x19237

kd> r
Last set context:
eax=89d5230 ebx=89d21130 ecx=89d21130 edx=89c8cc20 esi=89e24ac0 edi=89c8cc20
eip=f7242237 esp=f408afec ebp=f408b004 iopl=0 nv up ei ng nz ac po nc
cs=0008  ss=0010  ds=0023  es=0023  fs=0030  gs=0000             efl=00010292
driver+0x19237:
f7242237 ??              ???

kd> dds esp
f408afec  ????????
f408aff0  ????????
f408aff4  ????????
f408aff8  ????????
f408affc  ????????
f408b000  ????????
f408b004  ????????
f408b008  ????????
f408b00c  ????????
f408b010 ????????
f408b014 ????????
f408b018 ????????
f408b01c ????????
f408b020 ????????
f408b024 ????????
f408b028 ????????
f408b02c ????????
f408b030 ????????
f408b034 ????????
f408b038 ????????
f408b03c ????????
f408b040 ????????
f408b044 ????????
f408b048 ????????
f408b04c ????????
f408b050 ????????
f408b054 ????????
f408b058 ????????
f408b05c ????????
f408b060 ????????
f408b064 ????????
f408b068 ????????
```

```
kd> lmv m driver
start            end                module name
f7229000 f725f000   driver   T (no symbols)
    Loaded symbol image file: driver.sys
    Image path: driver.sys
    Image name: driver.sys
    Timestamp:        unavailable (FFFFFFFE)
    CheckSum:         missing
    ImageSize:        00036000
```

```
kd> dd f7229000
f7229000 ???????? ???????? ???????? ????????
f7229010 ???????? ???????? ???????? ????????
f7229020 ???????? ???????? ???????? ????????
f7229030 ???????? ???????? ???????? ????????
f7229040 ???????? ???????? ???????? ????????
f7229050 ???????? ???????? ???????? ????????
f7229060 ???????? ???????? ???????? ????????
f7229070 ???????? ???????? ???????? ????????
```

如果出于某种原因无法增加页面文件大小，我们应该在“启动和恢复”中配置“内核内存转储”。对于大多数错误检查，内核内存转储已经足够，除非是 **手动转储**（第 625 页），此时我们需要检查用户进程空间。

## 截断堆栈跟踪

有时我们会看到带有缺失堆栈帧的这种模式。例如，在一次事件中，为 **内存泄漏**（第 650 页）应用程序启用用户模式堆栈跟踪数据库后，我们从增长的堆段中得到了这些条目（其他段具有未截断的保存堆栈跟踪）：

```
0bdc1350: 40010 . 40010 [101] - busy (3fff8) Internal

7702fbd2: ntdll!RtlAllocateHeap+0x0000021d
77005eef: ntdll!RtlpAllocateUserBlock+0x000000a2
77026a65: ntdll!RtlpLowFragHeapAllocFromContext+0x00000785
7702661f: ntdll!RtlAllocateHeap+0x00000017c
```

```
0be01360: 40010 . 40010 [101] - busy (3fff8) Internal

7702fbd2: ntdll!RtlAllocateHeap+0x0000021d
77005eef: ntdll!RtlpAllocateUserBlock+0x000000a2
77026a65: ntdll!RtlpLowFragHeapAllocFromContext+0x00000785
7702661f: ntdll!RtlAllocateHeap+0x00000017c
```

```
0be41370: 40010 . 40010 [101] - busy (3fff8) Internal

7702fbd2: ntdll!RtlAllocateHeap+0x0000021d
77005eef: ntdll!RtlpAllocateUserBlock+0x000000a2
77026a65: ntdll!RtlpLowFragHeapAllocFromContext+0x00000785
7702661f: ntdll!RtlAllocateHeap+0x00000017c
```

**截断堆栈跟踪**与**不正确堆栈跟踪**（第 499 页）不同，因为其幸存部分是正确的。我们如何找到此类堆栈跟踪的其余部分？这里我们可以建议查看其他堆段并查看相同大小的分配。如果 **截断堆栈跟踪** 来自 **堆栈跟踪收集**（第 943 页），我们可以将其与另一进程实例中具有相同线程位置的非截断线程堆栈进行比较。

### 注释

另一个示例是调试器截断输出的情况。在 WinDbg 中，有一个名为 .kframes 的命令，用于设置堆栈跟踪帧的默认数量。

以下是来自 x64 Windows 10 的另一个 **截断堆栈跟踪** 示例，该示例发生在调用了 **NULL 代码指针**（第 750 页）之后。

```
0:003> kL
# Child-SP RetAddr Call Site
00 0000005b`056ae1f8 00007ffa`e2f2916f ntdll!NtWaitForMultipleObjects+0xa
01 0000005b`056ae200 00007ffa`e2f2906e KERNELBASE!WaitForMultipleObjectsEx+0xef
02 0000005b`056ae500 00007ffa`e3b5155c KERNELBASE!WaitForMultipleObjects+0xe
03 0000005b`056ae540 00007ffa`e3b51088 kernel32!WerpReportFaultInternal+0x494
04 0000005b`056aeab0 00007ffa`e2f503ad kernel32!WerpReportFault+0x48
05 0000005b`056aeae0 00007ffa`e5c58cd2 KERNELBASE!UnhandledExceptionFilter+0x1fd
06 0000005b`056aebe0 00007ffa`e5c44296 ntdll!RtlUserThreadStart$filt$0+0x3e
07 0000005b`056aec20 00007ffa`e5c5666d ntdll!_C_specific_handler+0x96
08 0000005b`056aec90 00007ffa`e5bd3c00 ntdll!RtlpExecuteHandlerForException+0xd
09 0000005b`056aecc0 00007ffa`e5c5577a ntdll!RtlDispatchException+0x370
0a 0000005b`056af3c0 00000000`00000000 ntdll!KiUserExceptionDispatch+0x3a
```

我们可以查看陷阱帧 RSP 地址并恢复返回地址：

```
0:003> dt _KTRAP_FRAME RSP 0000005b`056af7e8
ntdll!_KTRAP_FRAME
+0x180 Rsp : 0x0000005b`056afad8
0:003> dps 0x0000005b`056afad8 L1
0000005b`056afad8  00007ff7`f6381266 ApplicationM!thread_two+0x16
0:003> ub 00007ff7`f6381266
[...]
ApplicationM!thread_two:
00007ff7`f6381250 48894c2408        mov qword ptr [rsp+8],rcx
00007ff7`f6381255 4883ec38          sub rsp,38h
00007ff7`f6381259 48c744242000000000 mov qword ptr [rsp+20h],0
00007ff7`f6381262 ff542420          call qword ptr [rsp+20h]
```

并重建堆栈跟踪的底部：

```
0:003> k L=0x0000005b`056afad8
# Child-SP RetAddr Call Site
00 0000005b`056afad8  00007ff7`f6381266 ntdll!NtWaitForMultipleObjects+0xa
01 0000005b`056afae0  00007ff7`f6382bd1 ApplicationM!thread_two+0x16
02 (Inline Function) -------- ApplicationM!invoke_thread_procedure+0xe
03 0000005b`056afb20 00007ffa`e3b42d92 ApplicationM!thread_start+0x5d
04 0000005b`056afb50 00007ffa`e5bc9f64 kernel32!BaseThreadInitThunk+0x22
05 0000005b`056afb80 00000000`00000000 ntdll!RtlUserThreadStart+0x34
```

然后构建粘合堆栈跟踪（第 413 页）：

```
0000005b`056ae1f8 00007ffa`e2f2916f ntdll!NtWaitForMultipleObjects+0xa
0000005b`056ae200 00007ffa`e2f2906e KERNELBASE!WaitForMultipleObjectsEx+0xef
0000005b`056ae500 00007ffa`e3b5155c KERNELBASE!WaitForMultipleObjects+0xe
0000005b`056ae540 00007ffa`e3b51088 kernel32!WerpReportFaultInternal+0x494
0000005b`056aeab0 00007ffa`e2f503ad kernel32!WerpReportFault+0x48
0000005b`056aeae0 00007ffa`e5c58cd2 KERNELBASE!UnhandledExceptionFilter+0x1fd
0000005b`056aebe0 00007ffa`e5c44296 ntdll!RtlUserThreadStart$filt$0+0x3e
0000005b`056aec20 00007ffa`e5c5666d ntdll!_C_specific_handler+0x96
0000005b`056aec90 00007ffa`e5bd3c00 ntdll!RtlpExecuteHandlerForException+0xd
0000005b`056aecc0 00007ffa`e5c5577a ntdll!RtlDispatchException+0x370
```

