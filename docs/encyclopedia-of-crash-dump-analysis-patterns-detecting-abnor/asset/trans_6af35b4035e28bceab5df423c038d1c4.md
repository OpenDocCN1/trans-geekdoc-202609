

```
EXCEPTION_RECORD:  ffffffff -- (.exr 0xffffffffffffffff)
ExceptionAddress: 74d4e366 (kernel32!RaiseException+0x00000053)
  ExceptionCode: c0000008 (Invalid handle)
  ExceptionFlags: 00000000
NumberParameters: 0
Thread tried to close a handle that was invalid or illegal to close

DEFAULT_BUCKET_ID:  STATUS_INVALID_HANDLE

PROCESS_NAME:  BadHandle.exe

ERROR_CODE: (NTSTATUS) 0xc0000008 - An invalid HANDLE was specified.

STACK_TEXT:
0012ff64 00401043 c0000008 00000000 00000000 kernel32!RaiseException+0x53
WARNING: Stack unwind information not available. Following frames may be wrong.
0012ffc0 74d4e72d 00000000 00000000 7efde000 BadHandle+0x1043
0012fff0 00000000 004010f9 00000000 00000000 kernel32!BaseProcessStart+0x28

FAULTING_THREAD:  00000b64

PRIMARY_PROBLEM_CLASS:  STATUS_INVALID_HANDLE

BUGCHECK_STR:  APPLICATION_FAULT_STATUS_INVALID_HANDLE
```

由于 WinDbg 关于堆栈展开的警告，我们可以双重检查 RaiseException 返回地址的反汇编：

```
0:000> ub 00401043
BadHandle+0x1029:
00401029 push    offset BadHandle+0x212c (0040212c)
0040102e push    0
00401030 call    esi
00401032 push    0
00401034 push    0
00401036 push    0
00401038 push    0C0000008h
0040103d call    dword ptr [BadHandle+0x2004 (00402004)]

0:000> dps 00402004 l1
00402004  7d4e2318 kernel32!RaiseException
```

在这种情况下，真正的问题可能是内存损坏覆盖了存储的有效句柄值。

## 注释

我们还可以检查句柄值是否有效：

```
STACK_TEXT:
0fbef7f8 7581c455 00000aa4 00000aa4 0fbef818 ntdll!ZwClose+0x12
0fbef808 76051438 00000aa4 0000000d 00000000 KERNELBASE!CloseHandle+0x2d
0fbef818 5fa2632a 00000aa4 5fa24b9c 00000000 kernel32!CloseHandleImplementation+0x3f
[...]

0:017> !handle 00000aa4
Handle 00000aa4
Type

0:017> !handle 00000aa0
Handle 00000aa0
Type Thread

0:017> !handle 00000aa8
Handle 00000aa8
Type Event
```

在 gflags.exe 中启用应用程序验证器以捕获句柄关闭堆栈跟踪，也可能揭示在出现第二次无效句柄关闭之前最初是谁关闭了句柄。请在那里使用 !trace 命令。

## 托管空间

我们最近在 .NET 程序执行的上下文中遇到了 **无效句柄** 模式。我们决定对其进行建模，并编写了一个小型 C# 程序：

```
namespace SafeHandle
{
    class Program
    {
        static void Main(string[] args)
        {
            SafeFileHandle hFile =
                new SafeFileHandle(new IntPtr(0xDEAD), true);
            Console.WriteLine("About to close");
            Console.ReadKey();
        }
    }
}
```

当然，当我们执行它时什么都不会发生。默认情况下，无效句柄会被忽略。但是，为了改变行为，我们在 gflags.exe 中启用了“启用关闭异常”：

![](img/d6dfefc8f9ab7106c77a723ff84aaa6d_577_0.png)

此外，如果我们运行它，我们会得到这个托管堆栈跟踪（第 624 页）：

![](img/d6dfefc8f9ab7106c77a723ff84aaa6d_578_0.png)

如果我们启用了 *应用程序验证器*，本可以检测到无效句柄，但那样我们就不会有 **托管代码异常**（第 617 页）。

因此，我们加载一个崩溃转储（因为我们启用了 LocalDumps[^121] 而保存），并加载 SOS 扩展：

```
0:002> lm m clr
start end module name
000007fe8d880000 000007feee1eb000 clr (pdb symbols)
Loaded symbol image file: clr.dll
Image path: C:\Windows\Microsoft.NET\Framework64\v4.0.30319\clr.dll
[...]

0:002> .load C:\Windows\Microsoft.NET\Framework64\v4.0.30319\sos

0:002> !pe
Exception object: 0000000002ab5fe8
Exception type: System.Runtime.InteropServices.SEHException
Message: External component has thrown an exception.
InnerException:
StackTrace (generated):
| SP | IP | Function |
|---|---|---|
| 0000000018A0FED0 | 0000000000000000 | mscorlib_ni!Microsoft.Win32.Win32Native.CloseHandle(IntPtr)+0x1 |
| 0000000018A0F2F0 | 0000000000000000 | mscorlib_ni!System.Runtime.InteropServices.SafeHandle.InternalFinalize()+0x1 |
| 0000000018A0F2F0 | 000007FEE6C2F7A6 | mscorlib_ni!System.Runtime.InteropServices.SafeHandle.Finalize()+0x26 |

StackTraceString:
HResult: 80004005
```

我们的非托管 CLR 线程（第 124 页）异常堆栈跟踪（第 363 页）非常简单：

```
0:002> k
000000001b40d6e8 000007fefd651430 ntdll!NtWaitForMultipleObjects+0xa
000000001b40d6f0 0000000077621723 KERNELBASE!WaitForMultipleObjectsEx+0xe8
000000001b40d7f0 000000007769b5e5 kernel32!WaitForMultipleObjectsExImplementation+0xb3
000000001b40d880 000000007769b767 kernel32!WerpReportFaultInternal+0x215
000000001b40d920 000000007769b7bf kernel32!WerpReportFault+0x77
000000001b40d950 000000007769b9dc kernel32!BasepReportFault+0x1f
000000001b40d980 00000000778b3398 kernel32!UnhandledExceptionFilter+0x1fc
000000001b40da60 00000000778385c8 ntdll! ?? ::FNODOBFM::`string'+0x2365
000000001b40da90 00000000778492d2 ntdll!_C_specific_handler+0x8c
000000001b40db00 00000000778391cf ntdll!RtlpExecuteHandlerForException+0xd
000000001b40db30 00000000778397c8 ntdll!RtlDispatchException+0x85a
000000001b40e210 00000000778712c7 ntdll!RtlRaiseException+0x22f
000000001b40ebc0 000007fefd651873 ntdll!KiRaiseUserExceptionDispatcher+0x3a
000000001b40ec90 0000000077621991 KERNELBASE!CloseHandle+0x13
000000001b40ecc0 000007feec720418 kernel32!CloseHandleImplementation+0x3d
000000001b40edc0 000007feed8e9e03 mscorlib_ni+0x580418
000000001b40eea0 000007feed8e9e7e clr!CallDescrWorkerInternal+0x83
000000001b40eee0 000007feed8ec860 clr!CallDescrWorkerWithHandler+0x4a
000000001b40ef20 000007feed8f1ald clr!DispatchCallSimple+0x85
000000001b40efb0 000007feed8f19ac clr!SafeHandle::RunReleaseMethod+0x69
000000001b40f050 000007feed8f180a clr!SafeHandle::Release+0x122
000000001b40f120 000007feed4863e clr!SafeHandle::Dispose+0x36
000000001b40f190 000007feec2f74a6 clr!SafeHandle::Finalize+0xa2
000000001b40f2f0 000007feed8e9d56 mscorlib_ni+0x48f7a6
000000001b40f330 000007feed83c4e clr!FastCallFinalizeWorker+0x6
000000001b40f360 000007feed83c3 clr!MethodDesc::RequiresFullSlotNumber+0x72
000000001b40f3a0 000007feed83b0f clr!MethodTable::CallFinalizer+0xa3
000000001b40f3e0 000007feed9fe46 clr!SVR::CallFinalizer+0x5f
000000001b40f420 000007feed9aac5b clr!SVR::CallFinalizer+0x102
000000001b40f4e0 000007feed8f458c clr!WKS::GCHeap::IsPromoted+0xeee
000000001b40f520 000007feed8f451a clr!Frame::Pop+0x50
000000001b40f560 000007feed8449c1 clr!COMCustomAttribute::PopSecurityContextFrame+0x192
000000001b40f660 000007feed9d1bfe clr!COMCustomAttribute::PopSecurityContextFrame+0xbd
000000001b40f6f0 000007feed9d1e59 clr!ManagedThreadBase_NoADTransition+0x3f
000000001b40f750 000007feed9533de clr!WKS::GCHeap::FinalizerThreadStart+0x193
000000001b40f790 00000000776159ed clr!Thread::IntermediateThreadProc+0x7d
000000001b40f850 000000007784c541 kernel32!BaseThreadInitThunk+0xd
000000001b40f880 0000000000000000 ntdll!RtlUserThreadStart+0x1d
```

我们看到异常处理发生在对象终结期间。如果可能，我们可以通过反汇编推断句柄的值（可能是小值，第 873 页）：

```
0:002> kn
# Child-SP RetAddr Call Site
00 000000001b40d6e8 000007fefd651430 ntdll!NtWaitForMultipleObjects+0xa
01 000000001b40d6f0 0000000077621723 KERNELBASE!WaitForMultipleObjectsEx+0xe8
02 000000001b40d7f0 000000007769b5e5 kernel32!WaitForMultipleObjectsExImplementation+0xb3
03 000000001b40d880 000000007769b767 kernel32!WerpReportFaultInternal+0x215
04 000000001b40d920 000000007769b7bf kernel32!WerpReportFault+0x77
05 000000001b40d950 000000007769b9dc kernel32!BasepReportFault+0x1f
06 000000001b40d980 0000000077b83398 kernel32!UnhandledExceptionFilter+0x1fc
07 000000001b40da60 00000000778385c8 ntdll! ?? ::FNODOBFM::`string'+0x2365
08 000000001b40da90 00000000778492d0 ntdll!_C_specific_handler+0x8c
09 000000001b40db00 00000000778391cf ntdll!RtlpExecuteHandlerForException+0xd
0a 000000001b40db30 00000000778397c8 ntdll!RtlDispatchException+0x45a
0b 000000001b40e210 00000000778712c7 ntdll!RtlRaiseException+0x22
0c 000000001b40e4bc 000007fefd651873 ntdll!KiRaiseUserExceptionDispatcher+0x3a
0d 000000001b40ec90 0000000077621991 KERNELBASE!CloseHandle+0x13
0e 000000001b40ecc0 000007feec720418 kernel32!CloseHandleImplementation+0x3d
0f 000000001b40edd0 000007feed8e9e03 mscorlib_ni+0x580418
10 000000001b40eea0 000007feed8e9e7e clr!CallDescrWorkerInternal+0x83
11 000000001b40eee0 000007feed8e8c60 clr!CallDescrWorkerWithHandler+0x4a
12 000000001b40ef20 000007feed8f1a1d clr!DispatchCallSimple+0x85
13 000000001b40efb0 000007feed8f19ac clr!SafeHandle::RunReleaseMethod+0x69
14 000000001b40f050 000007feed8f180a clr!SafeHandle::Release+0x122
15 000000001b40f120 000007feed4863e clr!SafeHandle::Dispose+0x36
16 000000001b40f190 000007feec62f76a clr!SafeHandle::Finalize+0xa2
17 000000001b40f2f0 000007feed8e9d56 mscorlib_ni+0x48f746
18 000000001b40f330 000007feed83c4e clr!FinalCallFinalizerWorker+0x6
19 000000001b40f360 000007feed83bc3 clr!MethodDesc::RequiresFullSlotNumber+0x72
1a 000000001b40f3a0 000007feed83b0f clr!MethodTable::CallFinalizer+0xa3
1b 000000001b40f3e0 000007feed9fe4e clr!SVR::CallFinalizer+0x5f
1c 000000001b40f420 000007feed9aa55b clr!SVR::CallFinalizer+0x102
1d 000000001b40f4e0 000007feed8f458c clr!WKS::GCHeap::IsPromoted+0xeee
1e 000000001b40f520 000007feed8f451a clr!Frame::Pop+0x50
1f 000000001b40f560 000007feed8f449f clr!COMCustomAttribute::PopSecurityContextFrame+0x192
20 000000001b40f660 000007feed9d1be4 clr!COMCustomAttribute::PopSecurityContextFrame+0xbd
21 000000001b40f6f0 000007feed9d1e59 clr!ManagedThreadBase_NoADTransition+0x3f
22 000000001b40f750 000007feed9533de clr!WKS::GCHeap::FinalizerThreadStart+0x193
23 000000001b40f790 00000000776159ed clr!Thread::intermediateThreadProc+0x7d
24 000000001b40f850 000000007784c541 kernel32!BaseThreadInitThunk+0xd
25 000000001b40f880 0000000000000000 ntdll!RtlUserThreadStart+0x1d
```

```
0:002> .frame /c d
0d 000000001b40ec90 0000000077621991 KERNELBASE!CloseHandle+0x13
rax=00000000c0000001 rbx=0000000000000000 rcx=00000000009a0000
rdx=0000000000000001 rsi=000000001b40efd0 rdi=000000001b40eff8
rip=000007fefd651873 rsp=000000001b40ec90 rbp=000000001b40edf0
r8=000000001b40ce08 r9=000000001b40cf70 r10=0000000000000000
r11=0000000000000246 r12=0000000000000001 r13=0000000040000000
r14=000000001b40ef40 r15=0000000000000000
iopl=0 nv up ei pl zr na po nc
cs=0033 ss=002b ds=002b es=002b fs=0053 gs=002b efl=00000246
KERNELBASE!CloseHandle+0x13:
000007fefd651873 85c0 test eax,eax
```

[^121]: http://msdn.microsoft.com/en-us/library/bb787181.aspx

