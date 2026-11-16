

## 共享结构

有时我们查看栈轨迹收集（第 943 页）或其谓词子集（第 943 页），并识别出其中一个参数实际上是相同的结构地址或句柄。在 x64 情况下，我们可能通过返回地址的反向反汇编（**ub** WinDbg 命令）看到它，但在 x86 情况下，大多数时候我们可以直接从详细栈轨迹中发现，如下面的片段所示（除非参数内存槽被重复使用，请参阅**优化代码**，第 767 页）：

```
THREAD 830f9990 Cid 0428.0e94 Teb: 7ffdf000 Win32Thread: 00000000 WAIT: (UserRequest) UserMode Non-Alertable
[...]
ChildEBP RetAddr  Args to Child
0031f74c 7784b071 00000000 00000000 7ffdb000 ntdll!RtlpWaitOnCriticalSection+0x154
0031f774 0a911500 00a9b7a8 00000000 00a91452 ntdll!RtlEnterCriticalSection+0x152
WARNING: Stack unwind information not available. Following frames may be wrong.
0031f7c8 76113833 7ffdb000 0031f814 7784a9bd Application+0x1150
0031f7d4 7784a9bd 7ffdb000 003114bf 00000000 kernel32!BaseThreadInitThunk+0xe
0031f814 00000000 00a914a9 7ffdb000 00000000 ntdll!_RtlUserThreadStart+0x23

THREAD 886ee030 Cid 0428.0ef4 Teb: 7ffde000 Win32Thread: 00000000 WAIT: (UserRequest) UserMode Non-Alertable
[...]
ChildEBP RetAddr  Args to Child
0098fcb8 77f881b1 00000000 00000000 001614a0 ntdll!RtlpUnWaitCriticalSection+0x1b
0098fce0 0a9102e 00a9b7a8 00000000 00000000 ntdll!RtlEnterCriticalSection+0x152
WARNING: Stack unwind information not available. Following frames may be wrong.
0098fd28 00a91275 0098fd3c 76113833 001614a0 Application+0x102e
0098fd30 76113833 001614a0 0098fd7c 7784a9bd Application+0x1275
0098fd3c 7784a9bd 001614a0 009811d7 00000000 kernel32!BaseThreadInitThunk+0xe
0098fd7c 00000000 00a911ff 001614a0 00000000 ntdll!_RtlUserThreadStart+0x23
```

在**多个异常**（第 714 页）的情况下，甚至是单个线程上的单个异常涉及对结构字段的无效访问时，另一个线程上对同一结构的引用可能指向可能的同步问题。

## 小值

有时我们在内存（例如原始堆栈）或 CPU 寄存器中看到所谓的**小值**，它们可以是 ASCII 或 UNICODE 值、某个 ID，甚至是句柄。当它们聚集在一起时，可以形成某个**语义结构**（第 860 页），例如 PID.TID 示例，或**常规数据**（第 833 页）模式。这里我们举例说明一个句柄示例（也是用户空间中**等待链**分析的示例，第 1092 页）：

```
0:000> kv
           Child-SP          RetAddr           : Args to Child                                                           : Call Site
Child
00000000`0016de78 000007fe`fcf010dc : 00000000`02c79fa0 00000000`08c3faf0 00000000`021551f0
00000000`08c3fb00 : ntdll!NtWaitForSingleObject+0xa
00000000`0016de80 000007fe`f90e6d7f : 00000000`10b40010 00000000`10b40010 00000000`00000000
00000000`000070e0 : KERNELBASE!WaitForSingleObjectEx+0x79
[...]
```

```
0:000> !handle 00000000000070e0 ff
Handle 00000000000070d0
 Type             Thread
 Attributes       0
 GrantedAccess    0x1fffff:
     Delete,ReadControl,WriteDac,WriteOwner,Synch
     Terminate,Suspend,Alert,GetContext,SetContext,SetInfo,QueryInfo,SetToken,
 Impersonate,DirectImpersonate
 HandleCount      5
 PointerCount     9
 Name             <none>
 Object specific information
 Thread Id        278c.a58
 Priority         13
 Base Priority    0
```

```
0:000> ~~[a58]s
ntdll!NtWaitForMultipleObjects+0xa:
00000000`770c186a c3              ret
```

```
0:002> kv
           Child-SP          RetAddr           : Args to Child                                                           : Call Site
Child
00000000`0f6af758 000007fe`fcf01430 : 00000000`00000025 00000000`00000000 00000000`00000000
000007fe`e35a1fb0 : ntdll!NtWaitForMultipleObjects+0xa
00000000`0f6af760 00000000`76e61220 : 00000000`0f6af8a8 00000000`0f6af890 00000000`00000000
00000000`00000000 : KERNELBASE!WaitForMultipleObjectsEx+0xe8
[...]
```

```
0:002> dp 000000000f6af890 L4
00000000`0f6af890 00000000`00000dbc 00000000`000007c0
00000000`0f6af8a0 00000000`00000000 00000000`00000000
```

```
0:002> !handle dbc ff
Handle 0000000000000dbc
Type Thread
Attributes 0
GrantedAccess 0x1fffff:
 Delete,ReadControl,WriteDac,WriteOwner,Synch
 Terminate,Suspend,Alert,GetContext,SetContext,SetInfo,QueryInfo,SetToken,
 Impersonate,DirectImpersonate
HandleCount 2
PointerCount 4
Name <none>
Object specific information
 Thread Id 278c.24ac
 Priority 14
 Base Priority 0
```

```
0:002> !handle 7c0 ff
Handle 00000000000007c0
Type Thread
Attributes 0
GrantedAccess 0x1fffff:
 Delete,ReadControl,WriteDac,WriteOwner,Synch
 Terminate,Suspend,Alert,GetContext,SetContext,SetInfo,QueryInfo,SetToken,
 Impersonate,DirectImpersonate
HandleCount 2
PointerCount 4
Name <none>
Object specific information
 Thread Id 278c.628
 Priority 14
 Base Priority 0
```

### 注释

有时，小值可能巧合地是一个有效的句柄值，同时也是有效的线程 ID 或进程 ID。

## 软件异常

软件异常在激活上下文（第 60 页）、异常模块（第 328 页）、缺少组件（静态链接，第 672 页）、自转储（第 850 页）、栈溢出（软件实现，第 910 页）和转换异常（第 1013 页）模式中被提及。软件异常的典型示例是 C++ 异常（第 108 页）模式。

软件异常，例如*内存不足*，与所谓的*硬件异常*不同，因为它们可预测、同步，并由软件代码本身检测。相比之下，硬件异常（例如除以零、访问违例和内存保护）是不可预测的，并由硬件检测。当然，可以在代码执行前进行一些检查，然后为可能的硬件异常抛出软件异常或诊断消息。例如，请参阅用户模式的自我诊断模式（第 847 页）及其内核模式的相应等效项（第 844 页）。

在 Windows 内存转储中，我们可能在用户空间栈轨迹中看到 *RaiseException* 调用，例如来自数据相关性模式示例（第 180 页）：

```
0:000> kl
ChildEBP RetAddr
0012e950 78158e89 kernel32!RaiseException+0x53
0012e988 7830770c msvcr80!_CxxThrowException+0x46
0012e99c 783095bc mfc80u!AfxThrowMemoryException+0x19
0012e9b4 02afa8ca mfc80u!operator new+0x27
0012e9c8 02b0992f ModuleA!std::Allocator<...>::...+0x1a
0012e9e0 02b09e7c ModuleA!std::vector<double,std::allocator >::vector<double,std::allocator >+0x3f
[...]
```

### 注释

这里是软件异常的一个示例，这些异常被收集并随后由内部软件异常封装，有关更多参考信息，请参见**多个异常（封存）**分析模式，第 714 页。

```
0:008> kc
#
00 combase!RoFailFastWithErrorContextInternal2
01 combase!RoFailFastWithErrorContextInternal
02 Windows_UI_Xaml!DirectUI::ErrorHelper::ProcessUnhandledError
03 Windows_UI_Xaml!DirectUI::FinalUnhandledErrorDetectedRegistration::OnFinalUnhandledErrorDetected
04 Windows_UI_Xaml!Microsoft::WRL::Details::InvokeHelper, Windows::Foundation::IEventHandler,
Microsoft::WRL::FtmBase,Microsoft::WRL::Details::Nil,Microsoft::WRL::Details::Nil,
Microsoft::WRL::Details::Nil,Microsoft::WRL::Details::Nil,
Microsoft::WRL::Details::Nil,Microsoft::WRL::Details::Nil, Microsoft::WRL::Details::Nil>,long
(__stdcall*)(IInspectable *,Windows::ApplicationModel::Core::IUnhandledErrorDetectedEventArgs *,2>::Invoke
05 twinapi_appcore!Windows::Internal::Details::GitInvokeHelper,Windows::Internal::GitPtr,2>::Invoke
06 twinapi_appcore!Windows::ApplicationModel::Core::UnhandledErrorInvokeHelper::Invoke
07 twinapi_appcore!Microsoft::WRL::InvokeTraits<2>::InvokeDelegates< ,Windows::Foundation::IEventHandler >
08 twinapi_appcore!Microsoft::WRL::EventSource,Microsoft::WRL::InvokeModeOptions<2> >::DoInvoke < >
09 twinapi_appcore!Windows::ApplicationModel::Core::CoreApplication::ForwardLocalError
0a twinapi_appcore!Windows::ApplicationModel::Core::CoreApplicationFactory::ForwardLocalError
0b combase!CallErrorForwarder
0c combase!RoReportFailedDelegate
0d twinapi_appcore!wil::ErrorHandlingHelpers::Instance'::`2'::`dynamic atexit destructor for 'wrapper''
0e twinapi_appcore!Microsoft::WRL::EventSource,Microsoft::WRL::InvokeModeOptions< -2> >::DoInvoke < >
0f twinapi_appcore!Windows::ApplicationModel::Core::CoreApplicationView::Activate
10 rpcrt4!Invoke
11 rpcrt4!NdrStubCall2
12 combase!CStdStubBuffer_Invoke
13 rpcrt4!CStdStubBuffer_Invoke
14 combase!InvokeStubWithExceptionPolicyAndTracing:::-17::::operator()
15 combase!ObjectMethodExceptionHandlingAction< >
16 combase!InvokeStubWithExceptionPolicyAndTracing
17 combase!DefaultStubInvoke
18 combase!SyncStubCall::Invoke
19 combase!SyncServerCall::StubInvoke
1a combase!StubInvoke
1b combase!ServerCall::ContextInvoke
1c combase!CServerChannel::ContextInvoke
1d combase!DefaultInvokeInApartment
1e combase!ASTAInvokeInApartment
1f combase!AppInvoke
20 combase!ComInvokeWithLockAndIPID
21 combase!ComInvoke
22 combase!ThreadDispatch
23 combase!ComApartment::ASTAHandleMessage
24 combase!ASTAWaitContext::Wait
25 combase!ASTAWaitInNewContext
26 combase!ASTAThreadWaitForHandles
27 combase!CoWaitForMultipleHandles
28 twinapi_appcore!CSimpleArray,CSimpleArrayStandardCompareHelper,CSimpleArrayStandardMergeHelper
>::RemoveAt
29 SHCore!CSimpleArray,4294967294,CTPolicyCoTaskMem >,CSimpleArrayStandardCompareHelper
>,CSimpleArrayStandardMergeHelper > >:::_Add const &
2a kernel32!BaseThreadInitThunk
2b ntdll!_RtlUserThreadStart
2c ntdll!_RtlUserThreadStart

0:008> !error c000027b
Error code: (NTSTATUS) 0xc000027b (3221226107) - An application-internal exception has occurred.
```

