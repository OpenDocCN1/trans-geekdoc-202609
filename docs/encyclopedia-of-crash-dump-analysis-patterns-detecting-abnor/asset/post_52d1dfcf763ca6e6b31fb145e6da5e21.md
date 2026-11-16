
```
0:014> !CLRStack
OS Thread Id: 0x11ec (14)
ESP         EIP
075af4fc 016bfd9a Ironring.Management.MMC.SnapinBase+MmcWindow.Invoke(System.Delegate, System.Object[])
...
...
...
075af740 793d87af System.Threading._ThreadPoolWaitCallback.WaitCallback_Context(System.Object)
075af748 793608fd System.Threading.ExecutionContext.Run(System.Threading.ExecutionContext,
System.Threading.ContextCallback, System.Object)
075af760 79388898 System.Threading._ThreadPoolWaitCallback.PerformWaitCallback(System.Object)
075af8f0 79e7be1b [GCFrame: 075af8f0]
```

!help command gives the list of other available SOS extension commands:

```
0:014> !help
```

Object Inspection
- DumpObj (do)
- DumpArray (da)
- DumpStackObjects (dso)
- DumpHeap
- DumpVC
- GCRoot
- ObjSize
- FinalizeQueue
- PrintException (pe)
- TraverseHeap

Examining code and stacks
- Threads
- CLRStack
- IP2MD
- U
- DumpStack
- EEStack
- GCInfo
- EHInfo
- COMState
- BPMD

Examining CLR data structures
- DumpDomain
- EEHeap
- Name2EE
- SyncBlk
- DumpMT
- DumpClass
- DumpMD
- Token2EE
- EEVersion
- DumpModule
- ThreadPool
- DumpAssembly
- DumpMethodSig
- DumpRuntimeTypes
- DumpSig
- DumpCleanupList
- RCWCleanupList
- DumpIL

### Diagnostic Utilities
- VerifyHeap
- DumpLog
- FindAppDomain
- SaveModule
- GCHandles
- GCHandleLeaks
- VMMap
- VMStat
- ProcInfo
- StopOnException (soe)
- MinidumpMode

### Other
- FAQ

In the case where .NET CLR runtime is version 1.x we might get messages pointing to some .NET DLL and this could be the indication that some threads have managed code:

```
*** WARNING: Unable to verify checksum for mscorlib.dll
*** ERROR: Module load completed but symbols could not be loaded for mscorlib.dll
```

In some cases we cannot load the appropriate SOS extension automatically:

```
0:000> .loadby sos mscorwks
Unable to find module “mscorwks”
```

Then we can try SOS version 1.0

```
0:000> !clr10\sos.EEStack
Loaded Son of Strike data table version 5 from
"C:\WINDOWS\Microsoft.NET\Framework\v1.1.4322\mscorsvr.dll"
```

The following message means that the server version of CLR is used:

```
0:000> .loadby sos mscorwks
Unable to find module “mscorwks”
0:000> .loadby sos mscorsvr
```

```
0:000> !help
SOS : Help
```

For some crash dumps we get the following message saying that sos.dll cannot be found:

```
0:000> .loadby sos mscorwks
The call to LoadLibrary(C:\WIN_N0_SP\Microsoft.NET\Framework\v2.0.50727\sos) failed, Win32 error 0n126
"The specified module could not be found."
Please check your debugger configuration and/or network access
```

Here we need to check where Microsoft.NET\Framework\v2.0.50727\sos.dll is installed on our crash dump analysis host and use .load command:

```
0:000> .load C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\sos.dll
```

The version of WinDbg since 6.8.4.0 and !analyze -v command show both native and managed stack traces from .NET 64-bit application memory dump so there is no need to load SOS manually there.

## Managed Stack Trace

Typical examples of this pattern are stack traces from !CLRStack and !pe extension commands or subtraces from !DumpStack and !EEStack extension commands:

```
0:000> !pe
Exception object: 0000000005a976b8
Exception type: System.FormatException
Message: Index (zero based) must be greater than or equal to zero and less than the size of the argument
list.
InnerException: <none>
StackTrace (generated):
SP IP Function
00000000000BE4A0 000007FEEC2153B0
mscorlib_ni!System.Text.StringBuilder.AppendFormat(System.IFormatProvider, System.String,
System.Object[])+0x999280
0000000000DBEE00 000007FEEB87C0FA mscorlib_ni!System.String.Format(System.IFormatProvider, System.String,
System.Object[])+0x5a
0000000000DBF30 000007FF00AB336B ModuleA!ClassB.get()+0xeb

0:010> !DumpStack
OS Thread Id: 0x8dc (15)
Child-SP RetAddr Call Site
00000001f69e8808 00000000774babc4 user32!ZwUserWaitMessage+0xa
00000001f69e810 00000000774b4edd user32!DialogBox2+0x274
00000001f69e8a0 0000000077520290 user32!InternalDialogBox+0x135
00000001f69e900 0000000077501c15 user32!SoftModalMessageBox+0x9b4
00000001f69ea30 000000007750146b user32!MessageBoxWorker+0x31d
00000001f69ebf0 0000000077501362 user32!MessageBoxTimeoutW+0xb3
00000001f69ecc0 000007fef1590ce7 user32!MessageBoxW+0x4e
00000001f69ed00 000007feeb0f5c59 mscorwks!DoNDirectCall__PatchGetThreadCall+0x7b
[...]
00000001f69e030 000007ff00a9ba1c ModuleA!ClassA.foo()+0x47
[...]
00000001f69fe30 00000007781c521 kernel32!BaseThreadInitThunk+0xd
00000001f69fe60 0000000000000000 ntdll!RtlUserThreadStart+0x1d
```

## Kernel

Some memory dumps are generated on purpose to troubleshoot process and system hangs. They are usually called **Manual Dumps**, manual crash dumps or manual memory dumps. Kernel, complete and kernel minidumps can be generated using the famous keyboard method described in the Microsoft article 127.

The crash dump will show E2 bugcheck:

```
MANUALLY_INITIATED_CRASH (e2)
The user manually initiated this crash dump.
Arguments:
Arg1: 00000000
Arg2: 00000000
Arg3: 00000000
Arg4: 00000000
```

Various tools including Citrix SystemDump reuse E2 bug check code and its arguments. There are many other 3rd-party tools used to bugcheck Windows OS such as BANG! from OSR or NotMyFault from Sysinternals. The old one is crash.exe that loads crashdrv.sys and uses the following bugcheck:

```
Unknown bugcheck code (69696969)
Unknown bugcheck description
Arguments:
Arg1: 00000000
Arg2: 00000000
Arg3: 00000000
Arg4: 00000000
```

In a memory dump, we would see its characteristic **Stack Trace** (page 926) pointing to crashdrv module:

```
STACK_TEXT:
b53ebe0 6f15888d nt!KeBugCheck+0xf
WARNING: Stack unwind information not available. Following frames may be wrong.
b53ebec 6f1584e3 crashdrv+0x88d
b53ec00 8041eec9 crashdrv+0x4e3
b53ec14 804b328a nt!IopCallDriver+0x35
b53ec28 804b40de nt!IopSynchronousServiceTail+0x60
b53ed00 804abd0a nt!IopXxxControlFile+0x5d6
b53ed34 80468379 nt!NtDeviceIoControlFile+0x28
b53ed34 77f82ca0 nt!KiSystemService+0xc9
0006fed4 7c5794fa ntdll!NtDeviceIoControlFile+0xb
0006ff38 01001a74 KERNEL32!DeviceIoControl+0xf8
0006ff70 01001981 crash+0x1a74
0006ff80 01001f93 crash+0x1981
0006ffc0 7c5989a5 crash+0x1f93
0006fff0 00000000 KERNEL32!BaseProcessStart+0x3d
```

Sometimes various hardware buttons are used to trigger NMI and generate a crash dump when the keyboard is not available. The bugcheck will be:

```
NMI_HARDWARE_FAILURE (80)
This is typically due to a hardware malfunction. The hardware supplier should be called.
Arguments:
Arg1: 004f4454
Arg2: 00000000
Arg3: 00000000
Arg4: 00000000
```

Critical process termination such as session 0 csrss.exe is also used to force a memory dump:

```
CRITICAL_OBJECT_TERMINATION (f4)
A process or thread crucial to system operation has unexpectedly exited or been terminated.
Several processes and threads are necessary for the operation of the system; when they are terminated
(for any reason), the system can no longer function.
Arguments:
Arg1: 00000003, Process
Arg2: 8a090d88, Terminating object
Arg3: 8a090eec, Process image file name
Arg4: 80967b74, Explanatory message (ascii)
```

## Comments

If you see myfault module on the stack then the dump was generated by NotMyFault Sysinternals tool:

```
1: kd> k
Child-SP RetAddr Call Site
fffffa60`06bf7558 fffff800`0165712e nt!KeBugCheckEx
fffffa60`06bf7560 fffff800`0165600b nt!KiBugCheckDispatch+0x6e
fffffa60`06bf76a0 fffffa60`053da17a nt!KiPageFault+0x20b
fffffa60`06bf7830 fffffa60`053da397 myfault+0x117a
fffffa60`06bf7990 fffff800`018dd25a myfault+0x1397
fffffa60`06bf79f0 fffff800`018f5f76 nt!IopXxxControlFile+0x5da
fffffa60`06bf7b40 fffff800`01656e33 nt!NtDeviceIoControlFile+0x56
fffffa60`06bf7bb0 00000000`77525aea nt!KiSystemServiceCopyEnd+0x13
```

Some virtualized environments (Virtualized System, page 1075) may have their own methods to trigger a crash dump. For example, on XenServer 128 we can see these bugchecks:
