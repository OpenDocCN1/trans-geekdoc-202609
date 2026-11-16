

## x86:

BugCheck D1, {f001, 2, 0, f001}

### DRIVER_IRQL_NOT_LESS_OR_EQUAL (d1)

尝试在中断请求级别（IRQL）过高时访问可分页（或完全无效）的地址。这通常是由驱动程序使用不当地址引起的。

如果可用内核调试器，获取堆栈回溯。

- 参数：
  - Arg1: 0000f001, 引用的内存
  - Arg2: 00000002, IRQL
  - Arg3: 00000000, 值 0 = 读取操作，1 = 写入操作
  - Arg4: 0000f001, 引用内存的地址

```
STACK_TEXT:
805573c0 0000f001 nt!KiTrap0E+0x238
80557430 ffdffc70 0xf001
80557450 804dcbef 0xffdffc70
80557454 00000000 nt!KiIdleLoop+0x10
```

## x64:

BugCheck 1E, {ffffffffc0000005, f001, 8, f001}

### KMODE_EXCEPTION_NOT_HANDLED (1e)

这是一个非常常见的 BugCheck。通常异常地址会指向导致问题的驱动程序/函数。始终要记下此地址，以及包含该地址的驱动程序/映像的链接日期。

- 参数：
  - Arg1: ffffffffc0000005, 未处理的异常代码
  - Arg2: 000000000000f001, 发生异常的地址
  - Arg3: 0000000000000008, 异常的参数 0
  - Arg4: 000000000000f001, 异常的参数 1

```
STACK_TEXT:
fffff800`062b8358 fffff800`01896747 : nt!KeBugCheckEx
fffff800`062b8360 fffff800`018b1ce9 : nt! ?? ::FNODOBFM::`string'+0x250e7
fffff800`062b8960 fffff800`018bae5 : nt!KiExceptionDispatch+0xa9
fffff800`062b8b40 00000000`0000f001 : nt!KiPageFault+0x1e5
fffff800`062b8cd8 fffffa60`02a7e685 : 0xf001
fffff800`062b8ce0 fffff800`018b6583 : intelppm!C1Idle+0x9
fffff800`062b8d10 fffff800`018b62a1 : nt!PoIdle+0x183
fffff800`062b8d80 fffff800`01a88860 : nt!KiIdleLoop+0x21
fffff800`062b8db0 00000000`fffff800 : nt!zzz_AsmCodeRange_End+0x4
fffff800`062b2b0 00000000`00000000 : 0xfffff800
```

还可以在以下线程堆栈中看到代码 f001：

```
DRIVER_VERIFIER_DETECTED_VIOLATION (c4)
A device driver attempting to corrupt the system has been caught. This is
because the driver was specified in the registry as being suspect (by the
administrator) and the kernel has enabled substantial checking of this driver.
If the driver attempts to corrupt the system, bugchecks 0xC4, 0xC1 and 0xA will
be among the most commonly seen crashes.
Arguments:
Arg1: 0000000000000091, A driver switched stacks using a method that is not supported by
the operating system. The only supported way to extend a kernel
mode stack is by using KeExpandKernelStackAndCallout.
Arg2: 0000000000000000
Arg3: fffff8800185bc40
Arg4: 0000000000000000

0: kd> k1 100
Child-SP RetAddr Call Site
fffff880`0891f8c8 fffff800`01729c8a nt!KeBugCheckEx
fffff880`0891f8d0 fffff800`01700573 nt! ?? ::FNODOBFM::`string'+0x4904
fffff880`0891f910 fffff800`0170d8df nt!RtlDispatchException+0x33
fffff880`0891f1f0 fffff800`016d2c42 nt!KiDispatchException+0x16f
fffff880`08920680 fffff800`016d17ba nt!KiExceptionDispatch+0xcx2
fffff880`08920860 fffff800`016ca533 nt!KiPageFault+0x23a
fffff880`089209f8 fffff800`016a88c0 nt!memcpy+0x223
fffff880`08920a00 fffff800`016a8638 nt!KiOpFetchBytes+0x30
fffff880`08920a30 fffff800`017d0d6f nt!KiOpDecode+0x68
fffff880`08920a80 fffff800`017d0896 nt!KiPreprocessFault+0x53
fffff880`08920b10 fffff800`016d2c42 nt!KiDispatchException+0x126
fffff880`089211a0 fffff800`016d17ba nt!KiExceptionDispatch+0xcx2
fffff880`08921380 00000000`0000f001 nt!KiPageFault+0x23a
fffff880`08921518 fffff800`016d9b4b 0xf001
fffff880`08921520 fffff800`016d94da nt!EnlightenedSwapContext_PatchXSave+0xa8
fffff880`08921560 fffff800`016da752 nt!KiSwapContext+0x7a
fffff880`089216a0 fffff800`016dc8af nt!KiCommitThreadWait+0x1d2
fffff880`08921730 fffff800`0169c1de nt!KeWaitForSingleObject+0x19f
fffff880`089217d0 fffff800`016db8bc nt!ExpWaitForResource+0xae
fffff880`08921840 fffff880`042fcd91 nt!ExAcquireResourceExclusiveLite+0x14f
[...]
fffff880`08921a10 fffff800`019eff16 nt!IopXxxControlFile+0x607
fffff880`08921b40 fffff800`016d2853 nt!NtDeviceIoControlFile+0x56
fffff880`08921bb0 00000000`7755ff2a nt!KiSystemServiceCopyEnd+0x13
00000000`0343f708 00000000`00000000 0x7755ff2a
```

硬件手动转储的另一个示例是 BugCheck 8E, {c0000005, ...

```
BUCKET_ID: IP_MISALIGNED

0: kd> .trap 0xffffffff99189ce4
ErrCode = 00000002
eax=00000115 ebx=8092596a ecx=00000000 edx=00cbff30 esi=00cbff38 edi=99189d64
eip=8092596c esp=99189d58 ebp=99189d64 iopl=0 nv up ei ng nz na pe cy
cs=0008 ss=0010 ds=0023 es=0023 fs=0030 gs=0000 efl=00010287
nt!NtUnmapViewOfSection+0x2:
8092596c 8c28 mov word ptr [eax],gs ds:0023:00000115=????????
```

```
0: kd> u nt!NtUnmapViewOfSection
nt!NtUnmapViewOfSection:
8092596a e9cd8c2777 jmp driverA+0x4263c (f7bae63c)
8092596f 51 push ecx
80925970 64a124010000 mov eax,dword ptr fs:[00000124h]
80925976 8a80d7000000 mov al,byte ptr [eax+0D7h]
8092597c 3c01 cmp al,1
8092597e 56 push esi
8092597f 8b750c mov esi,dword ptr [ebp+0Ch]
80925982 8845fc mov byte ptr [ebp-4],al
```

服务器被报告已挂起，所有 CPU 都繁忙。

内存转储 API 功能在 Windows 8.1 [129] 中可用。

## 进程

现在我们讨论进程内存转储中常见的 **手动转储** 模式。此处无法可靠识别手动转储，因为调试器或其他进程转储工具可能以非侵入方式附加到进程，且不会留下干预痕迹，因此我们只能依赖以下信息：

### 注释字段

```
Loading Dump File [C:\kktools\userdump8.1\x64\notepad.dmp]
User Mini Dump File with Full Memory: Only application data is available

Comment: 'Userdump generated complete user-mode minidump with Standalone function on COMPUTER-NAME'
```

### 无异常

```
Loading Dump File [C:\UserDumps\notepad.dmp]
User Mini Dump File with Full Memory: Only application data is available

Symbol search path is: srv*c:\mss*http://msdl.microsoft.com/download/symbols
Executable search path is:
Windows Vista Version 6000 MP (2 procs) Free x64
Product: WinNt, suite: SingleUserTS
Debug session time: Mon Dec 17 16:31:31.000 2007 (GMT+0)
System Uptime: 0 days 0:45:11.148
Process Uptime: 0 days 0:00:36.000
.......
user32!ZwUserGetMessage+0xa:
00000000`76c8e6aa c3            ret
0:000> ~*kL
.  0  Id: 1b8.ed4 Suspend: 1 Teb: 000007ff`fffdc000 Unfrozen
Child-SP          RetAddr           Call Site
00000000`0029f618 00000000`76c8e6ea user32!ZwUserGetMessage+0xa
00000000`0029f620 00000000`ff2b6eca user32!GetMessageW+0x34
00000000`0029f650 00000000`ff2bcf8b notepad!WinMain+0x176
00000000`0029f6d0 00000000`76d7cdcd notepad!IsTextUTF8+0x24f
00000000`0029f790 00000000`76ecc6e1 kernel32!BaseThreadInitThunk+0xd
00000000`0029f7c0 00000000`00000000 ntdll!RtlUserThreadStart+0x1d
```

### 唤醒调试器异常

```
Loading Dump File [C:\\UserDumps\\notepad2.dmp]
User Mini Dump File with Full Memory: Only application data is available

Symbol search path is: srv*c:\\mss*http://msdl.microsoft.com/download/symbols
Executable search path is:
Windows Vista Version 6000 MP (2 procs) Free x64
Product: WinNt, suite: SingleUserTS
Debug session time: Mon Dec 17 16:35:37.000 2007 (GMT+0)
System Uptime: 0 days 0:49:13.806
Process Uptime: 0 days 0:02:54.000
......................
This dump file has an exception of interest stored in it.
The stored exception information can be accessed via .ecxr.
(314.1b4): Wake debugger - code 80000007 (first/second chance not available) user32!ZwUserGetMessage+0xa:
00000000`76c8e6ea c3              ret
```

### 中断指令异常

```
Loading Dump File [C:\\UserDumps\\notepad3.dmp]
User Mini Dump File with Full Memory: Only application data is available

Symbol search path is: srv*c:\\mss*http://msdl.microsoft.com/download/symbols
Executable search path is:
Windows Vista Version 6000 MP (2 procs) Free x64
Product: WinNt, suite: SingleUserTS
Debug session time: Mon Dec 17 16:45:15.000 2007 (GMT+0)
System Uptime: 0 days 0:58:52.699
Process Uptime: 0 days 0:14:20.000
......................
This dump file has an exception of interest stored in it.
The stored exception information can be accessed via .ecxr.
ntdll!DbgBreakPoint:
00000000`76ecfdf0 cc              int     3

0:001> ~*kL

     Id: 1b8.ed4 Suspend: 1 Teb: 000007ff`fffdc000 Unfrozen
Child-SP          RetAddr           Call Site
00000000`0029f618 00000000`76c8e6ea user32!ZwUserGetMessage+0xa
00029f620 00000000`ff2b6eca user32!GetMessageW+0x34
00029f650 00000000`ff2bcf8b notepad!WinMain+0x176
00029f6d0 00000000`76d7cdcd notepad!IsTextUTF8+0x24f
00029f790 00000000`76ecc6e1 kernel32!BaseThreadInitThunk+0xd
00029f7c0 00000000`00000000 ntdll!RtlUserThreadStart+0x1d
```

