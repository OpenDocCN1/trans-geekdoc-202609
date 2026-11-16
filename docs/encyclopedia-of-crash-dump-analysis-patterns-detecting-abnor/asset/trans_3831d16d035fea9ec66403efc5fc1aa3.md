

```
00118d14  00118d34
...
...
...
0:020> lm
```

| 起始 | 结束 | 模块名称 |
| --- | --- | --- |
| 00400000 | 00ba8000 | AppSql |
| ... | ... | ... |
| 10000000 | 100e0000 | myhook |

地址 10008e00 看起来非常“整齐”，它可能是一组位标志，而且，如果我们反向反汇编该地址处的代码，我们看不到通常将该地址保存到堆栈上的 call 指令：

```
0:000> ub 10008e00
myhook!notify_me+0x211
10008de5 81c180000000   add     ecx,80h
10008deb 899578ffffff   mov     dword ptr [ebp-88h],edx
10008df1 89458c         mov     dword ptr [ebp-74h],eax
10008df4 894d98         mov     dword ptr [ebp-68h],ecx
10008df7 6a01           push    1
10008df9 8d45ec         lea     eax,[ebp-14h]
10008dfc 50             push    eax
10008dfd ff75e0         push    dword ptr [ebp-20h]
```

相比之下，其他两个地址是保存在堆栈上的返回地址：

```
0:000> ub 0066a831
AppSql+0x26a81e:
0066a81e 8fbf           mov     edi,ebx
0066a820 f3a5           rep movs dword ptr es:[edi],dword ptr [esi]
0066a822 8bca           mov     ecx,edx
0066a824 83e103         and     ecx,3
0066a827 f3a4           rep movs byte ptr es:[edi],byte ptr [esi]
0066a829 8b00           mov     eax,dword ptr [eax]
0066a82b 50             push    eax
0066a82c e8affeffff     call    AppSql+0x26a6e0 (0066a6e0)
```

```
0:000> ub 0049e180
AppSql+0x9e16f:
0049e16f cc             int     3
0049e170 55             push    ebp
0049e171 8bec           mov     ebp,esp
0049e173 8b4510         mov     eax,dword ptr [ebp+10h]
0049e176 8b4d0c         mov     ecx,dword ptr [ebp+0Ch]
0049e179 50             push    eax
0049e17a 51             push    ecx
0049e17b e840c61c00     call    AppSql+0x26a7c0 (0066a7c0)
```

因此，myhook!notify_me+0x22c 的出现可能只是巧合，除非它是指向函数的指针。不过，如果它是函数指针地址，那么它就不会指向压入参数的函数调用序列的中间部分：

```
0:000> ub 10008e00
myhook!notify_me+0x211
10008de5 81c180000000 add ecx,80h
10008deb 899578ffffff mov dword ptr [ebp-88h],edx
10008df1 89458c mov dword ptr [ebp-74h],eax
10008df4 894d98 mov dword ptr [ebp-68h],ecx
10008df7 6a01 push 1
10008df9 8d45ec lea eax,[ebp-14h]
10008dfc 50 push eax
10008dfd ff75e0 push dword ptr [ebp-20h]
0:000> u 10008e00
myhook!notify_me+0x22c
10008e00 e82ff1ffff call myhook!copy_data (10007f34)
10008e05 8b578fffffff mov eax,dword ptr [ebp-88h]
10008e0b 3945ac cmp dword ptr [ebp-88h],eax
10008e0e 731f jae myhook!notify_me+0x25b (10008e2f)
10008e10 8b4598 mov eax,dword ptr [ebp-68h]
10008e13 0fbff00 movsx eax,word ptr [eax]
10008e16 8945a8 mov dword ptr [ebp-58h],eax
10008e19 8b45e0 mov eax,dword ptr [ebp-20h]
```

此外，因为我们有源代码和私有符号，我们知道如果它是函数指针，那么它应该是 myhook!notify_me 地址，而不是 notify_me+0x22c 地址。

所有这些证据都支持这样的假设：myhook 在问题堆栈上的出现只是巧合，应该被忽略。

补充一点，我们在一个崩溃转储中迄今发现的最巧合的符号信息，是导出的 _DebuggerHookData 与事后调试器 NTSD 位置之间的偶然对应关系：

```
002dd434 003a0043
002dd438 0057005c
002dd43c 004e0049 LegacyApp!_DebuggerHookData+0xc4a5
002dd440 004f0044 LegacyApp!_DebuggerHookData+0x1c4a0
002dd444 00530057
002dd448 0073005c
002dd44c 00730079
002dd450 00650074
002dd454 0033006d
002dd458 005c0032
002dd45c 0074006e
002dd460 00640073
002dd464 0065002e
002dd468 00650078
0:000> du 002dd434
002dd434 "C:\WINDOWS\system32\ntsd.exe"
```

引入“变量减法”（Variable Subtract，第 1058 页）分析模式，是为了对仅涉及一个线程的内存快照间 CPU 峰值进行互相关（Inter-Correlation18）分析。相比之下，我们发现“常量减法”（Constant Subtract）模式在仅涉及一个内存快照的多线程等待链（Wait Chain，第 1082 页）分析（即内相关分析，Intra-Correlation19）中很有用。这里，常量减法将来自堆栈跟踪收集（Stack Trace Collection，第 943 页）的堆栈跟踪与分叉堆栈跟踪帧（类似于分叉点跟踪分析模式20）分组，以提供一些等待链关系提示。这些跟踪最初可能通过前面的等待链分析或技术特定的子跟踪（如 ALPC/RPC 服务器线程帧，如 COM 接口调用的示例堆栈所示，技术特定子跟踪，第 988 页）发现。下面是一个极简堆栈跟踪图（类似于加速 Windows 软件跟踪分析培训21 中介绍的极简跟踪图），用于说明该模式（它还显示了从完整内存转储中看到的用户空间中的峰值线程模式，第 888 页）：

![](img/d6dfefc8f9ab7106c77a723ff84aaa6d_140_0.png)

- 18 《内存转储分析文选》第 4 卷，第 350 页
- 19 同上，第 3 卷，第 347 页
- 20 同上，第 4 卷，第 343 页
- 21 http://www.patterndiagnostics.com/Training/Accelerated-Windows-Software-Trace-Analysis-Public.pdf

## 损坏的转储

这是一个相当常见的模式，通常是截断转储（Truncated Dump，第 1015 页）模式的后果。当我们打开此类崩溃转储时，通常会在 WinDbg 输出中立即注意到错误。我们可以区分两类损坏的内存转储：完全损坏和部分损坏。完全损坏较少见，由无效文件头引起，并以错误消息框的形式表现出来，显示以下 Win32 错误：

```
Loading Dump File [C:\Documents and Settings\All Users\Application Data\Microsoft\Dr
Watson\user_corrupted.dmp]
ERROR: Directory not present in dump (RVA 0x20202020)
Could not open dump file [C:\Documents and Settings\All Users\Application Data\Microsoft\Dr
Watson\user_corrupted.dmp], Win32 error 1392
"The file or directory is corrupted and unreadable."
```

部分损坏的文件可以加载，但缺少一些关键信息，例如已加载模块的列表以及所有或某些处理器的上下文。我们可以在 WinDbg 输出中看到大量类似以下的消息：

```
GetContextState failed, 0x80070026
Unable to get current machine context, Win32 error 0n38
```

```
GetContextState failed, 0x80004005
```

```
GetContextState failed, 0xD0000147
```

它们表示：

```
?: kd> !error 0x80070026
Error code: (HRESULT) 0x80070026 (2147942438) - Reached the end of the file.
?: kd> !error 0x80004005
Error code: (HRESULT) 0x80004005 (2147500037) - Unspecified error
?: kd> !error 0xD0000147
Error code: (NTSTATUS) 0xd0000147 (3489661255) - {No Paging File Specified} No paging file was specified
in the system configuration.
```

不过，在许多此类情况下，我们仍然可以看到系统信息和 bugcheck 参数：

```
********************
THIS DUMP FILE IS PARTIALLY CORRUPT.
KdDebuggerDataBlock is not present or unreadable.
********************
Unable to read PsLoadedModuleList
KdDebuggerData.KernBase < SystemRangeStart
Windows Server 2003 Kernel Version 3790 MP (4 procs) Free x86 compatible
Product: Server, suite: TerminalServer
Kernel base = 0x00000000 PsLoadedModuleList = 0x808af9c8
Debug session time: Wed Nov 21 20:29:31.373 2007 (GMT+0)
System Uptime: 0 days 0:45:02.312
Unable to read PsLoadedModuleList
KDebuggerData.KernBase < SystemRangeStart
Loading Kernel Symbols
Unable to read PsLoadedModuleList
GetContextState failed, 0x80070026
GetContextState failed, 0x80070026
CS descriptor lookup failed
GetContextState failed, 0x80070026
GetContextState failed, 0x80070026
GetContextState failed, 0x80070026
GetContextState failed, 0x80070026
Unable to get program counter
GetContextState failed, 0x80070026
Unable to get current machine context, Win32 error 0n38
GetContextState failed, 0x80070026
GetContextState failed, 0x80070026
Use !analyze -v to get detailed debugging information.
```

```
BugCheck 20, {0, ffff, 0, 1}
***** Debugger could not find nt in module list, module list might be corrupt, error 0x80070057.
GetContextState failed, 0x80070026
Unable to read selector for PCR for processor 0
GetContextState failed, 0x80070026
Unable to read selector for PCR for processor 0
GetContextState failed, 0x80070026
Unable to read selector for PCR for processor 0
GetContextState failed, 0x80070026
GetContextState failed, 0x80070026
Unable to get current machine context, Win32 error 0n38
GetContextState failed, 0x80070026
Unable to get current machine context, Win32 error 0n38
GetContextState failed, 0x80070026
```

查看 bugcheck 编号和参数，我们可以形成一些签名并在我们的崩溃数据库中检查。我们还可以请求与调试会话时间相对应的内核 minidump。

## 评论

主要观点是，如果你有一个损坏的转储，你仍然可能识别出问题。此外，系统管理员和支持工程师可以更早识别出损坏的转储并请求新的转储。

