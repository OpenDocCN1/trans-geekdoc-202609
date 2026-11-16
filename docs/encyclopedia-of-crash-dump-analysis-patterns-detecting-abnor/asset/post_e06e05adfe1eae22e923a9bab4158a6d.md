

```
0333f65c 762e77d7 kernel32!BasepReportFault+0x20
0333f6e8 733f267a kernel32!UnhandledExceptionFilter+0x1af
0333fa20 747371ed msvcr90!abort+0x10f
WARNING: Stack unwind information not available. Following frames may be wrong.
0333fab8 77a938aa DispatcherProxy!Singleton<_dispatcherproxyreceiver>::instance+0x5ed
0333fbcc 77a99f45 ntdll!RtlpFreeHeap+0xb7a
0333fbe4 00000000 ntdll!_RtlUserThreadStart+0x1b
```

Another example is Windows 8-style security interrupts:

```
0:112> .exr -1
ExceptionAddress: 00007ffffdb82513 (eModel!wil::details::ReportFailure+0x00000000000000ab)
ExceptionCode: c0000409 (Security check failure or stack buffer overrun)
ExceptionFlags: 00000001
NumberParameters: 1
Parameter[0]: 0000000000000007
Subcode: 0x7 FAST_FAIL_FATAL_APP_EXIT

0:112> kc 4
# Call Site
00 eModel!wil::details::ReportFailure
01 eModel!wil::details::ReportFailure_Hr
02 eModel!wil::details::in1diag3::FailFast_Hr
03 eModel!SpartanCore::LayerOwner::ConnectToLayerStateSystem

0:112> r
Last set context:
rax=0000000000000000 rbx=0000000000000000 rcx=0000000000000007
rdx=0000004d31b8421c rsi=000000000000331c rdi=0000000000000004
rip=00007ffffdb82513 rsp=0000004d32c4bff0 rbp=000000000000331c
r8=0000000000000003 r9=0000004d31b8421c r10=0000004d31b841a8
r11=0000004d32c4bf60 r12=0000000000000000 r13=0000000000000000
r14=0000000000000000 r15=0000000000000000
iopl=0 nv up ei pl zr na po nc
cs=0033 ss=002b ds=002b es=002b fs=0053 gs=002b efl=00000246
eModel!wil::details::ReportFailure+0xab:
00007fff`fdb82513 cd29 int 29h
```

## Self-Dump

Sometimes processes dump themselves using Microsoft DbgHelp API when they encounter internal errors or for other debugging purposes. We separate that from unhandled exceptions which usually cause an external postmortem debugger process to dump memory contents as explained in “Who Calls the Postmortem Debugger?”182 and “Inside Vista Error Reporting”183 articles.

It is important to understand that a process can dump itself not only as a reaction to hardware and **Software Exceptions** (page 875) but for any reasons that came to mind of an application designer. In any case, it is useful to look at raw stack dump of all threads184 and search for the first chance exceptions like c0000005 and **Custom Exception Handlers** (page 169).

We can consider this pattern as a specialized version of **Special Stack Trace** pattern (page 882). The typical thread stack might look like and might be **Incorrect Stack Trace** (page 499) that requires manual reconstruction185:

```
0:012> kL
ChildEBP RetAddr
0151f0c4 77e61f0c ntdll!KiFastSystemCallRet
0151f0d4 08000000 kernel32!CreateFileMappingW+0xc8
WARNING: Frame IP not in any known module. Following frames may be wrong.
0151f0f0 7c82728b 0x8000000
0151f0f4 77e63e41 ntdll!NtMapViewOfSection+0xc
0151f12c 77e6440c kernel32!MapViewOfFileEx+0x71
0151f14c 7c8262b kernel32!MapViewOfFile+0x1b
0151f1d4 028ca67c ntdll!ZwClose+0xc
0151f2a4 028cc2f1 dbghelp!GenGetClrMemory+0xec
0151f2b4 028c8e55 dbghelp!Win32LiveSystemProvider::CloseMapping+0x11
0151f414 00000000 dbghelp!GenAllocateModuleObject+0x3c5
```

Raw stack data should reveal DbgHelp API calls:

```
0151f944 00000000
0151f948 00000000
0151f94c 0151f9c0
0151f950 028c7662 dbghelp!MiniDumpWriteDump+0x1b2
0151f954 ffffffff
0151f958 0000c0b0
0151f95c 00c21ea8
0151f960 00c21f88
0151f964 00c21e90
0151f968 00c21fa0
0151f96c 00000002
0151f970 00000000
0151f974 00000000
0151f978 00000000
0151f97c 7c829f60 ntdll!CheckHeapFillPattern+0x64
0151f980 ffffffff
0151f984 7c829f59 ntdll!RtlFreeHeap+0x70f
0151f988 7c34218a msvcr71!free+0xc3
0151f98c 00000000
0151f990 00000000
0151f994 00c21e90
0151f998 00c21fa0
0151f99c 00c21ea8
0151f9a0 00c21f88
0151f9a4 00000002
0151f9a8 021a0da
0151f9ac 001875d8
0151f9b0 7c3416db msvcr71!_nh_malloc+0x10
0151f9b4 0151f998
0151f9b8 001875d8
0151f9bc 00000000
0151f9c0 0151fbe4
0151f9c4 57b77d01 application!write_problem_report+0x18d1
0151f9c8 ffffffff
0151f9cc 0000c0b0
0151f9d0 00000718
0151f9d4 00000002
0151f9d8 00000000
0151f9dc 00000000
0151f9e0 00000000
0151f9e4 00029722
0151f9e8 0151fc20
```

Partially reconstructed stack trace may look like this:

```
0:012> k L=0151f94c
ChildEBP RetAddr
0151f0c4 77e61f0c ntdll!KiFastSystemCallRet
0151f94c 028c7662 kernel32!CreateFileMappingW+0xc8
0151f9c0 57b77d01 dbghelp!MiniDumpWriteDump+0x1b2
0151fbe4 57b77956 application!write_problem_report+0x18d1
0151fc30 579c83af application!TerminateThread+0x18
```

## Comments

Sometimes, Truncated Stack Traces (page 1017) hide Self-Dump processing:

```
4 Id: 10e4.2838 Suspend: 0 Teb: 7efa6000 Unfrozen
ChildEBP RetAddr
026beb1c 00000000 ntdll!NtGetContextThread+0x12
```

We need to examine raw stack Execution Residue (page 371) to see the presence of DbgHelp API.

## Semantic Split

Semantic Split is the partitioning of anomalous debugger output from debugging commands into several disjoint or weakly linked classes. It is better characterized as the partition of a memory analysis pattern, for example, Blocked Thread pattern (page 80), into classes with different semantics, for example, blocked display threads and blocked remote share threads. Here is one short example of it found in the output of !locks and !process 0 3f WinDbg commands from a complete memory dump forced on a hanging server. The output shows several blocked threads and Wait Chains (page 1089) of executive resources (some shared locks have been removed for clarity):

```
0: kd> !locks
**** DUMP OF ALL RESOURCE OBJECTS ****

Resource @ 0x88eeaf0  Exclusively owned
    Contention Count = 809254
    NumberOfExclusiveWaiters = 4
    Threads: 88a26db0-01<*>
    Threads Waiting On Exclusive Access:
    88c6b6d0   8877b020   88a7e020   88938db0

Resource @ 0x88badb20  Exclusively owned
    Contention Count = 9195
    NumberOfExclusiveWaiters = 4
    Threads: 88842020-02<*>
    Threads Waiting On Exclusive Access:
    88a8b170   89069450   88c4d020   88a26db0

Resource @ 0x88859cc0  Exclusively owned
    Contention Count = 51021
    NumberOfExclusiveWaiters = 8
    Threads: 886f1c50-01<*>
    Threads Waiting On Exclusive Access:
    88e04db0   886785c0   8851edb0   896ee890
    8869fb50   886d6498   889aa918   88c2da38

Resource @ 0x8881cc38  Exclusively owned
    Contention Count = 173698
    NumberOfExclusiveWaiters = 4
    Threads: 87e72598-01<*>
    Threads Waiting On Exclusive Access:
    88392020   8918c8d8   88423020   880eba50

Resource @ 0x884ffab0  Exclusively owned
    Contention Count = 3363
    NumberOfExclusiveWaiters = 2
    Threads: 8807c5b8-02<*>
    Threads Waiting On Exclusive Access:
    87e72598   881c12a8

Resource @ 0x87cd6d48  Exclusively owned
Contention Count = 242361
NumberOfExclusiveWaiters = 5
Threads: 87540718-01<*>
Threads Waiting On Exclusive Access:
878ceaf0   8785ac50   8884a7b8   87c4ca28
89ab5db0

Resource @ 0x87c44d08  Exclusively owned
Contention Count = 2560
NumberOfExclusiveWaiters = 1
Threads: 87540718-01<*>
Threads Waiting On Exclusive Access:
87c4e468

Resource @ 0x87b5f1d8  Exclusively owned
Contention Count = 3
NumberOfSharedWaiters = 3
Threads: 89e76db0-01<*> 8739ac50-01   86f5d1c8-01   870f4db0-01

Resource @ 0x888bfc38  Exclusively owned
Contention Count = 3
NumberOfSharedWaiters = 3
Threads: 88a10db0-01<*> 86c94198-01   86dac598-01   86d85c50-01
```

The first group of locks (bold above) shows various problems with ComponentA module:

```
0: kd> !thread 88842020 1f
THREAD 88842020 Cid 1cf8.1b28 Teb: 7ffdb000 Win32Thread: bc25e8c0 WAIT: (Unknown) KernelMode Non-Alertable
88842098 NotificationTimer
Not impersonating
DeviceMap      e3813fd0
Owning Process 888c5d88   Image:     ApplicationA.exe
Attached Process N/A      Image:     N/A
Wait Start TickCount   1163714   Ticks: 0
Context Switch Count   35781   LargeStack
UserTime    00:00:00.453
KernelTime   00:00:01.109
Win32 Start Address 0x77ec3ea5
Start Address kernel32!BaseThreadStartThunk (0x7c8217ec)
Stack Init b5cc4db0 Current b5cc4614 Base b5cc5000 Limit b5cbf000 Call b5cc4bd8
Priority 9 BasePriority 9 PriorityDecrement 0
ChildEBP RetAddr
b5cc462c 80833ec5 nt!KiSwapContext+0x26
b5cc4658 80829069 nt!KiSwapThread+0x2e5
b5cc46a0 bf8981b3 nt!KeDelayExecutionThread+0x2ab
b5cc46c4 bf898422 ComponentA!LockGUIHandle+0x6d
[...]
b5cc49e8 80a63456 nt!KiFastCallEntry+0xecd
[...]
```

