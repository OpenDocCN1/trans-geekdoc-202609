

```
0012fcc4 00020003
0012fcc8 001d0001
0012fccc 00000000
0012fcd0 01e04f7
0012fcd4 0012fcc0
0012fcd8 00000000
0012fcdc 0012fd4c
0012fce0 7475f1a6
0012fce4 74730850
0012fce8 ffffffff
0012fcec 0012fd20
0012fcf0 7e431923 user32!DispatchHookA+0x101
0012fcf4 00000003
0012fcf8 00000011
0012fcfc 001d0001
0012fd00 00000000
0012fd04 0012fe94
0012fd08 00000102
0012fd0c 7ffde000
0012fd10 00000000
0012fd14 00000001
0012fd18 00000003
0012fd1c 7e42b326 user32!CallHookWithSEH+0x44
0012fd20 0012fd5c
0012fd24 7e42b317 user32!CallHookWithSEH+0x21
0012fd28 00020003
0012fd2c 00000011
0012fd30 001d0001
0012fd34 747307c3
0012fd38 00000000
0012fd3c 0012fe94
0012fd40 00000102
[...]
0:000> ub 74730844
DllA!ThreadKeyboardProc+0x5e:
7473082b jne DllA!ThreadKeyboardProc+0x77 (74730844)
7473082d cmp dword ptr [ebp-1Ch],esi
74730830 je DllA!ThreadKeyboardProc+0x77 (74730844)
74730832 push dword ptr [ebp+10h]
74730835 push dword ptr [ebp+0Ch]
74730838 push dword ptr [ebp+8]
7473083b push dword ptr [ebp-1Ch]
7473083e call dword ptr [DllA!_imp_CallNextHookEx (74721248)]
```

有时我们甚至可以重构显示消息挂钩调用堆栈的堆栈跟踪片段¹³⁴。当线程在消息挂钩过程中激增或阻塞时，我们可以看到挂钩模块：

```
0:000> kL
ChildEBP RetAddr
0012fc80 7e43e1ad ntdll!KiFastSystemCallRet
0012fca8 74730844 user32!NtUserCallNextHookEx+0xc
0012fcce 7e431923 DllA!ThreadKeyboardProc+0x77
0012fd20 7e42b317 user32!DispatchHookA+0x101
0012fd5c 7e430238 user32!CallHookWithSEH+0x21
0012fd80 7c90e473 user32!_fnHKINDWORD+0x24
0012fda4 7e4193e9 ntdll!KiUserCallbackDispatcher+0x13
0012fdd0 7e419402 user32!NtUserPeekMessage+0xc
0012fdfc 747528ee user32!PeekMessageW+0xbc
[...]
0012fff0 00000000 kernel32!BaseProcessStart+0x23
```

## 注释

## 另一个示例：

```
002afcd0 765614ab ntdll!ZwWaitForSingleObject+0x15
002afdc3 768b1194 KERNELBASE!WaitForSingleObjectEx+0x98
002afd54 768b1148 kernel32!WaitForSingleObjectExImplementation+0x75
002afd68 002e95de kernel32!WaitForSingleObject+0x12
WARNING: Stack unwind information not available. Following frames may be wrong.
002afd9c 767c8336 HookA+0x95de
002afdcc 767b0a09 USER32!DispatchHook+0x10e
002afe0c 767c2bfd USER32!CallHookWithSEH+0x21
002afec3 775b010a USER32!__fnHkINLPMOUSEHOOKSTRUCTEX+0x29
002afed4 00471c64 ntdll!KiUserCallbackDispatcher+0x2e
002afefc 00471d1f ProcessA+0x62d00
[...]
002aff94 775d9f72 kernel32!BaseThreadInitThunk+0xe
002affd4 775d9f45 ntdll!_RtlUserThreadStart+0x70
002affec 00000000 ntdll!_RtlUserThreadStart+0x1b
```

## 镜像转储集

如果操作系统不在虚拟机中，则很难获取物理内存的一致性实时快照（请参阅不一致转储分析模式，第 498 页）。LiveKd¹³⁵ 中的镜像转储选项可以保存一致的内核内存转储。然后，我们可以使用 Fiber Bundle¹³⁶ 技术保存单个进程内存转储，或使用 LiveKd 创建不一致的完整内存转储，或两者兼用。我们称此模式为镜像转储集。

![](img/d6dfefc8f9ab7106c77a723ff84aaa6d_665_0.png)

我们可以使用以下当前堆栈跟踪来识别镜像转储：

```
0: kd> version
...
64-bit Kernel bitmap dump: ...
...
```

```
0: kd> k
 # Child-SP RetAddr Call Site
00 ffffd000`26121700 fffff803`c5f55ee3 nt!IopLiveDumpEndMirroringCallback+0x7f
01 ffffd000`26121750 fffff803`c6f0561b nt!MmDuplicateMemory+0x807
02 ffffd000`26121830 fffff803`cF851c60 nt!IopLiveDumpCaptureMemoryPages+0x53
03 ffffd000`26121890 fffff803`cf44744d nt!IoCaptureLiveDump+0xf8
04 ffffd000`261218e0 fffff803`cF8ce0bd nt!DbgkCaptureLiveKernelDump+0x2e7
05 ffffd000`26121970 fffff803`cf3deb3b nt!NtSystemDebugControl+0x3f5
06 ffffd000`26121a90 00007ffa`2925205a nt!KiSystemServiceCopyEnd+0x13
07 000000a3`5bcddb48 00000000`00000000 0x00007ffa`2925205a
```

在一个分析案例中，我们得到了这样一组数据，在完整内存中分析了端点在筛选器驱动程序（第 924 页）中阻塞的用户空间堆栈跟踪中的 ALPC 等待链（第 1097 页）。但由于不一致性，查找帧中包含筛选器管理器的堆栈跟踪失败：

```
0: kd> version
...
64-bit Full kernel dump: ...
...
```

```
0: kd> !stacks 2 FltMgr
...
TYPE mismatch for thread object at ffffe001b804d638
4.----- NO ETHREAD DATA
TYPE mismatch for thread object at ffffe001b804d638
4.----- NO ETHREAD DATA
TYPE mismatch for thread object at ffffe001b804d638
4.----- NO ETHREAD DATA
TYPE mismatch for thread object at ffffe001b804d638
4.----- NO ETHREAD DATA
TYPE mismatch for thread object at ffffe001b804d638
4.----- NO ETHREAD DATA
...
```

因此，我们从一致的镜像转储中找到了这样的内核空间堆栈跟踪。

## 缺失组件

### 常规

当某个 DLL 缺失时，代码有时会引发异常。如果没有符号和源代码，我们需要猜测该组件名称。这可以通过检查异常 ESP/RSP 值附近的原始堆栈数据来完成。

考虑 App.exe 的以下不完整非托管堆栈跟踪的崩溃转储：

```
EXCEPTION_RECORD: ffffffff -- (.exr 0xffffffffffffffff)
ExceptionAddress: 76f442eb (kernel32!RaiseException+0x00000058)
  ExceptionCode: c06d007f
  ExceptionFlags: 00000000
NumberParameters: 1
  Parameter[0]: 0024f21c

0:000> kL
ChildEBP RetAddr
0024f1f8 6eb1081e kernel32!RaiseException+0x58
WARNING: Stack unwind information not available. Following frames may be wrong.
0024f260 6eac2fbb AppNativeLib!AppLibraryExports::InteropNotifyUnAdvise+0x6aa9
0024f2ac 6ea9e269 AppNativeLib!AppLibraryExports::Phase2Initialization+0x24c9
0024f32c 79e74d79 AppNativeLib!AppLibraryExports::QueryDatabase+0x99da
0024f3d4 664bd6af mscorwks!MethodTable::IsValueType+0x35
0024f3e8 319ce9e AppShell_ni+0x2d6af
0024f3f4 31a15d19 UIX_ni+0x1ec9e
0024f3f8 00000000 UIX_ni+0x65d19
```

我们可以尝试将此崩溃解释为托管代码异常（第 617 页），但首先让我们检查异常代码。Google 搜索显示，错误代码 c06d007f 表示“延迟加载导出缺失”，这肯定与某个缺失的 DLL 有关。无法从堆栈跟踪输出中得知缺失的是哪一个。需要进一步挖掘。

让我们查看原始堆栈。首先，我们可以尝试查看线程原始堆栈数据中是否有对 LoadLibrary 的调用：

```
0:000> !teb
TEB at 7ffdf000
    ExceptionList:        0024f8c4
    StackBase:            00250000
    StackLimit:           00249000
    SubSystemTib:         00000000
    FiberData:            0001e000
    ArbitraryUserPointer: 00000000
    Self:                 7ffdf000
    EnvironmentPointer:   00000000
    ClientId:             000012f4 . 0001080
    RpcHandle:            00000000
    Tls Storage:          004e8a18
    PEB Address:          7ffde000
```

LastErrorValue: 126
LastStatusValue: c0000135
Count Owned Locks: 0
HardErrorMode: 0

0:000> dds 00249000 00250000
00249000 00000000
00249004 00000000
...
0024f1a0 00000000
0024f1a4 00000000
0024f1a8 c0d007f
0024f1ac 00000000
0024f1b0 00000000
0024f1b4 76f442eb kernel32!RaiseException+0x58
0024f1b8 00000001
0024f1bc 0024f21c
0024f1c0 00000000
0024f1c4 00000000
0024f1c8 00000000
0024f1cc 00000000
0024f1d0 76f00000 kernel32!_imp__aullrem (kernel32+0x0)
0024f1d4 7fbd2a5d
0024f1d8 0024f1e8
0024f1dc 76fb8e8f kernel32!LookupHandler+0x10
0024f1e0 6ecb9b40 AppNativeLib!ShutdownSingletonMgr+0x15b024
0024f1e4 0024f21c
0024f1e8 0024f200
0024f1ec 6ec74e2a AppNativeLib!ShutdownSingletonMgr+0x11630e
0024f1f0 6ecb9b40 AppNativeLib!ShutdownSingletonMgr+0x15b024
0024f1f4 6ecb9ff0 AppNativeLib!ShutdownSingletonMgr+0x15b4d4
0024f1f8 0024f260
0024f1fc 6eb1081e AppNativeLib!AppLibraryExports::InteropNotifyUnAdvise+0x6aa9
0024f200 c6d007f
0024f204 00000000
0024f208 00000001
...

我们的崩溃转储中没有这样的调用。然后，我们可以尝试将原始堆栈数据解释为字节流，以查看 “.dll” 字符串：

```
0:000> db 00249000 00250000
00249000 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00249010 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00249020 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00249030 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
...
```

除了 “user32.dll” 外，没有这样的字符串。

