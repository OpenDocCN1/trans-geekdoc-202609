

```
Key: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\kernel
Value: ObTracePoolTags
Type: REG_SZ
Data: Proc
```

排查或调试后我们需要禁用跟踪，因为它会消耗池内存（另一种**插桩副作用**模式的变体（第 520 页），并且可能导致类似的**内存不足**模式，用于堆栈跟踪数据库，第 563 页）：

| Tag | 非分页分配 | 非分页释放 | 非分页差值 | 非分页已用 | 分页分配 | 分页释放 | 分页差值 | 分页已用 | 描述 |
|-----|-------------|-------------|-------------|-------------|-----------|-----------|-----------|-----------|-------------|
| ObRt | 5688634 | 5676109 | 12525 | 4817288240 | 0 | 0 | 0 | | 对象引用堆栈跟踪，二进制: nt!ob |
| Proc | 22120 | 101 | 22019 | 25961168 | 0 | 0 | 0 | | 进程对象，二进制: nt!ps |

启用跟踪后，我们会收集完整的内存转储（在事后调试的情况下），以使用 **!obtrace** WinDbg 命令分析另一种**堆栈跟踪**模式的变体（第 919 页）：

```
0: kd> obtrace fffffffa800af9e220
Object: fffffffa800af9e220
Image: Appd.exe
Sequence (+/-) Tag Stack
--------------------------- -------------------
ad377858 +1 Dflt nt! ?? ::NNGAKEGL::`string'+21577
nt!PsPAllocateProcess+185
nt!NtCreateUserProcess+4a3
nt!KiSystemServiceCopyEnd+13

ad377882 +1 Dflt nt! ?? ::NNGAKEGL::`string'+1f9d8
nt!NtProtectVirtualMemory+119
nt!KiSystemServiceCopyEnd+13
nt!KiServiceLinkage+0
nt!RtlCreateUserStack+1e4
nt!PsAllocateThread+299
nt!NtCreateUserProcess+65d
nt!KiSystemServiceCopyEnd+13

ad377884 -1 Dflt nt! ?? ::FNODOBFM::`string'+4886e
nt!NtProtectVirtualMemory+161
nt!KiSystemServiceCopyEnd+13
nt!KiServiceLinkage+0
nt!RtlCreateUserStack+1e4
[...]
```

分析此类跟踪可能会因**堆栈跟踪截断**（第 1015 页）而变得复杂。**源模块**（第 771 页）在某些情况下可能简化计数。

## 常规数据

此模式将内存中发现的 ASCII 和 UNICODE 类型 (00xx00yy) 数据推广到特定领域的数据格式，例如位图和矢量数据。后者的示例可能是 ...0xx0yy... 序列（xxx 是十六进制数字三元组）。此模式的典型用法是分析损坏的动态内存块（进程堆、内核池），其中跨块边界的常规数据连续性指向可能的**共享缓冲区覆盖**（第 868 页）。

## 相对内存泄漏

在进程堆（第 650 页）和 .NET 堆（第 636 页，或通常有多个动态内存分配器）的并行**内存泄漏**情况下，我们关注相对增长，以查看它们是否相互依赖，即托管堆对象是否指向进程堆条目。当我们有一组连续的内存转储时，可以构建堆大小表并绘制图表，其中坐标轴表示内存快照编号和总堆大小（字节）：

![](img/d6dfefc8f9ab7106c77a723ff84aaa6d_833_0.png)

不幸的是，如上图所示，相对增长大小可能不成比例。为克服此问题，我们可以通过最低相应堆大小对大小进行归一化，即 S_n/S_1：

![](img/d6dfefc8f9ab7106c77a723ff84aaa6d_834_0.png)

尽管如此，如果不存在相关性，这仍然无法显示没有相关性。我们可以绘制相对增长，即 S_n/S_{n-1}，n > 1：

![](img/d6dfefc8f9ab7106c77a723ff84aaa6d_835_0.png)

图表显示**相对堆泄漏**之间没有明显相关性。类似的图表可以针对相对对象分布（.NET 堆上的**对象分布异常**，第 756 页）构建。

## RIP 堆栈跟踪

注入代码的地址可能不在加载模块的地址范围内。在这种情况下，在执行调用历史记录中，我们会在堆栈跟踪上看到纯 EIP 和 RIP 返回地址。我们称此模式为**RIP 堆栈跟踪**，部分原因是我们在出错并导致进程崩溃后见过这些地址：

```
0:005> k
ChildEBP RetAddr
02aec974 77655620 ntdll!KiFastSystemCallRet
02aec978 77683c62 ntdll!NtWaitForSingleObject+0xc
02aec9fc 77683d4b ntdll!RtlReportExceptionEx+0x14b
02aeca3c 7769fa87 ntdll!RtlReportException+0x3c
02aeca50 7769fbd0 ntdll!RtlpTerminateFailureFilter+0x14
02aeca5c 775f9bdc ntdll!RtlReportCriticalFailure+0x6b
02aeca70 775f4f67 ntdll!_EH4_CallFilterFunc+0x12
02aeca98 77655f79 ntdll!_except_handler4+0x8e
02aecabc 77655f4b ntdll!ExecuteHandler2+0x26
02aecb6c 77655dd7 ntdll!ExecuteHandler+0x24
02aecb6c 7769fa8f ntdll!KiUserExceptionDispatcher+0xf
02aecce0 776a0704 ntdll!RtlReportCriticalFailure+0x5b
02aecef0 776a07f2 ntdll!RtlpReportHeapFailure+0x21
02aecf24 7766b1a5 ntdll!RtlpLogHeapFailure+0xa1
02aecfc6 7765730a ntdll!RtlpCoalesceFreeBlocks+0x4b9
02aecd64 77657545 ntdll!RtlpFreeHeap+0x1e2
02aed080 75e47e4b ntdll!RtlFreeHeap+0x14e
02aed0c8 77037277 kernel32!GlobalFree+0x47
02aed0dc 774b4a1f ole32!ReleaseStgMedium+0x124
02aed0ff 77517feb urlmon!ReleaseBindInfo+0x4c
02aed100 774d9a87 urlmon!CINet::ReleaseCNetObjects+0x3d
02aed118 774d93f0 urlmon!CINetHttp::OnWininetRequestHandleClosing+0x60
02aed12c 76432078 urlmon!CINet::CINetCallback+0x2de
02aed274 76438f5d wininet!InternetIndicateStatus+0xfc
02aed2a4 7643937a wininet!HANDLE_OBJECT::~HANDLE_OBJECT+0xc9
02aed2c0 7643916b wininet!INTERNET_CONNECT_HANDLE_OBJECT::~INTERNET_CONNECT_HANDLE_OBJECT+0x209
02aed2cc 76438d5e wininet!HTTP_REQUEST_HANDLE_OBJECT::`vector deleting destructor'+0xd
02aed2dc 76434e72 wininet!HANDLE_OBJECT::Dereference+0x22
02aed2e8 76439419 wininet!DereferenceObject+0x21
02aed310 76439114 wininet!InternetCloseHandle+0x9d
02aed330 0000aaff wininet!InternetCloseHandle+0x11e
WARNING: Frame IP not in any known module. Following frames may be wrong.
02aed33c 774c5d25 0x4aaaf
02aed358 774c5d95 urlmon!CINet::TerminateRequest+0x82
02aed364 774c5d7c urlmon!CINet::MyUnlockRequest+0x10
02aed370 774c5d63 urlmon!CINetProtImpl::UnlockRequest+0x10
02aed37c 774c5d49 urlmon!CINetEmbFilter::UnlockRequest+0x11
02aed388 774b743d urlmon!CINet::UnlockRequest+0x13
02aed394 774b73e1 urlmon!COInetProt::UnlockRequest+0x11
02aed3a8 774b7530 urlmon!CTransaction::UnlockRequest+0x36
02aed3b4 774b74e0 urlmon!CTransData::~CTransData+0x3a
02aed3c0 774b74c9 urlmon!CTransData::~`scalar deleting destructor'+0xd
02aed3d8 774e221f urlmon!CTransData::Release+0x25
02aed3e0 774b6d0a urlmon!CReadOnlyStreamDirect::~CReadOnlyStreamDirect+0x1a
02aed3ec 774b7319 urlmon!CReadOnlyStreamDirect::`vector deleting destructor'+0xd
02aed404 774b72be urlmon!CReadOnlyStreamDirect::Release+0x25
02aed410 774b71f4 urlmon!CBinding::~CBinding+0xb9
02aed41c 774b71dd urlmon!CBinding::`scalar deleting destructor'+0xd
02aed434 6b20b0e8 urlmon!CBinding::Release+0x25
02aed448 6b20b0ba mshtml!ATL::AtlComPtrAssign+0x2b
02aed458 6b20b8de mshtml!ATL::CComPtr<IBindCallbackInternal>::operator=+0x15
02aed464 6b20b8aa mshtml!CBindingXSSFilter::TearDown+0x2b
02aed46c 6b20b8a7 mshtml!BindingXSSFilter_TearDown+0x19
02aed478 6b0da61a mshtml!CStreamProxy::Passivate+0x12
02aed484 6b0ddf3a mshtml!CBaseFT::Release+0x1d
02aed4ac 6b0eb070 mshtml!CDwnBindData::TerminateBind+0x11d
02aed4b8 6b11a2a9 mshtml!CDwnBindData::TerminateOnApt+0x14
02aed4ec 6b105096 mshtml!GlobalWndOnMethodCall+0xfb
02aed50c 7742fd72 mshtml!GlobalWndProc+0x183
02aed538 7742fe4a user32!InternalCallWinProc+0x23
02aed5b0 7743018d user32!UserCallWinProcCheckWow+0x14b
02aed614 7743022b user32!DispatchMessageWorker+0x322
02aed624 6ecac1d5 user32!DispatchMessageW+0xf
02aef72c 6ec5337e ieframe!CTabWindow::_TabWindowThreadProc+0x54c
02aef7e4 760f426d ieframe!LCIETab_ThreadProc+0x2c1
02aef7f4 75e4d0e9 iertutil!CisoScope::RegisterThread+0xab
02aef800 776319bb kernel32!BaseThreadInitThunk+0xe
02aef840 7763198e ntdll!__RtlUserThreadStart+0x23
02aef858 00000000 ntdll!_RtlUserThreadStart+0x1b
```

但是，需要检查此类地址是否属于 .NET CLR JIT 代码（第 591 页）。

## 粗糙堆栈跟踪

此模式是更通用的**执行残留**（第 371 页）模式或托管空间中的**调用方-被调用方**（第 111 页）的示例。它只是来自线程堆栈区域或其片段的符号引用集合（也可能包含**巧合符号信息**，第 137 页）。在 WINDbg 中，我们可以通过使用 **dpS** 命令获取它：

```
0:003> !teb
TEB at 000007fffffd6000
    ExceptionList:        0000000000000000
    StackBase:            0000000024500000
    StackLimit:           00000000244b0000
    SubSystemTib:         0000000000000000
    FiberData:            000000000001e0e0
    ArbitraryUserPointer: 0000000000000000
    Self:                 000007fffffd6000
    EnvironmentPointer:   0000000000000000
    ClientId:             0000000000047fc .   000000000004824
    RpcHandle:            0000000000000000
    Tls Storage:          000007fffffd6058
    PEB Address:          000007fffffd000
    LastErrorValue:       0
    LastStatusValue:      c0000302
    Count Owned Locks:    0
    HardErrorMode:        0

0:003> dpS 000000000244b000 0000000002450000
000007fe`fd4a8a2e ole32!InternalVerifyStackAvailable+0x44 [d:\w7main\minio\safealloca\alloca.c @ 317]
000007fe`fd4a8a2e ole32!InternalVerifyStackAvailable+0x44 [d:\w7main\minio\safealloca\alloca.c @ 317]
000007fe`fd4a8a2e ole32!InternalVerifyStackAvailable+0x44 [d:\w7main\minio\safealloca\alloca.c @ 317]
00000000`771d5430 ntdll!RtlpInterceptorRoutines
00000000`771d134d ntdll!RtlAllocateHeap+0x16c
00000000`770ec9c3 ntdll!RtlAppendUnicodeStringToString+0x53
00000000`76eaebe5 kernel32!Wow64RedirectKeyPathInternal+0x2b7
00000000`770ec9c3 ntdll!RtlAppendUnicodeStringToString+0x53
00000000`7711f4fd ntdll!RtlFreeHeap+0x1a6
00000000`76eaec01 kernel32!ConstructKernelKeyPath+0x15f
00000000`76eaedd3 kernel32!Wow64NtOpenKey+0xee
00000000`7711f4fd ntdll!RtlFreeHeap+0x1a6
00000000`76ebc8aa kernel32!BaseRegOpenClassKeyFromLocation+0x3ba
00000000`76f3edf0 kernel32!'string'
00000000`771d5430 ntdll!RtlpInterceptorRoutines
00000000`76ebcb99 kernel32!BaseRegGetUserPrefixLength+0xea
00000000`76f3ee38 kernel32!'string'
00000000`76f3edc8 kernel32!'string'
00000000`76ebc3a8 kernel32!BaseRegGetKeySemantics+0x1b8
00000000`771150d3 ntdll!RtlNtStatusToDosError+0x27
00000000`76eb36b7 kernel32!LocalBaseRegOpenKey+0x276
0007fe`fd4b6c79 ole32!GetUnquotedPath+0x29 [d:\w7rtm\com\ole32\com\objbase\dlcache.cxx @ 2256]
000007fe`fd4b7019 ole32!CClassCache::CDllPathEntry::NegotiateDllInstantiationProperties+0x145 [d:\w7rtm\com\ole32\com\objbase\dlcache.cxx @ 3092]
00000000`771d5430 ntdll!RtlpInterceptorRoutines
00000000`7711d34d ntdll!RtlAllocateHeap+0x16c
00000000`77115cc4 ntdll!RtlpAllocateHeap+0xc12
0007fe`fd1c0359 usp10!USpShapingClient::AllocMem+0x49
```

