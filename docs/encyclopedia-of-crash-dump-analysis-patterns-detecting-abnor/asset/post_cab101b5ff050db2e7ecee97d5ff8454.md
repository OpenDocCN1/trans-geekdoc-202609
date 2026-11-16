
```
0:002> ub 00000000`77621991
kernel32!CloseHandleImplementation+0x1e:
00000000`7762196e 83f9f4        cmp     ecx,0FFFFFFFFh
00000000`77621971 0f83952e0100  jae     kernel32!TlsGetValue+0x3ef0 (00000000`7763480c)
00000000`77621977 488bc3        mov     rax,rbx
00000000`7762197a 2500300000    and     eax,100000003h
00000000`7762197f 4883f803      cmp     rax,3
00000000`77621983 0f847f8dfeff  je      kernel32!CloseHandleImplementation+0x56 (00000000`7760a708)
00000000`77621989 488bcb        mov     rcx,rbx
00000000`7762198c e81f000000    call    kernel32!CloseHandle (00000000`776219b0)
```

Here we also check the value from the managed stack trace or **Execution Residue** (page 369):

```
0:002> !CLRStack -a
OS Thread Id: 0x1390 (2)
Child SP IP       Call Site
00000001b40fedf8 000000007787186a [InlinedCallFrame: 00000001b40fedf8]
Microsoft.Win32.Win32Native.CloseHandle(IntPtr)
00000001b40fef80 000007fec720418 [InlinedCallFrame: 00000001b40fef80]
Microsoft.Win32.Win32Native.CloseHandle(IntPtr)
00000001b40fed00 000007fec720418 DomainNeutralILStubClass.IL_STUB_PInvoke(IntPtr)
PARAMETERS:
<no data>

00000001b40feff8 000007feed8e9e03 [GCFrame: 00000001b40feff8]
00000001b40ff148 000007feed8e9e03 [GCFrame: 00000001b40ff148]
00000001b40ff1f8 000007feed8e9e03 [HelperMethodFrame_PROD: 00000001b40ff1f8] System.Runtime.InteropServices.SafeHandle.InternalFinalize()
00000001b40ff2f0 000007feec62f7a6 System.Runtime.InteropServices.SafeHandle.Finalize()

PARAMETERS:
this (0x0000000001b40f330) = 0x0000000002ab2d78
```

```
0:002> !dso
OS Thread Id: 0x1390 (2)
RSP/REG   Object Name
00000001b40fea00 0000000002ab2d78 Microsoft.Win32.SafeHandles.SafeFileHandle
00000001b40fefd0 0000000002ab2d78 Microsoft.Win32.SafeHandles.SafeFileHandle
00000001b40ff038 0000000002ab2d78 Microsoft.Win32.SafeHandles.SafeFileHandle
00000001b40ff050 0000000002ab2d78 Microsoft.Win32.SafeHandles.SafeFileHandle
00000001b40ff090 0000000002ab2d78 Microsoft.Win32.SafeHandles.SafeFileHandle
00000001b40ff120 0000000002ab2d78 Microsoft.Win32.SafeHandles.SafeFileHandle
00000001b40ff190 0000000002ab2d78 Microsoft.Win32.SafeHandles.SafeFileHandle
00000001b40ff188 0000000002ab2d78 Microsoft.Win32.SafeHandles.SafeFileHandle
00000001b40ff240 0000000002ab2d78 Microsoft.Win32.SafeHandles.SafeFileHandle
00000001b40ff2f8 0000000002ab2d78 Microsoft.Win32.SafeHandles.SafeFileHandle
00000001b40ff330 0000000002ab2d78 Microsoft.Win32.SafeHandles.SafeFileHandle
00000001b40ff360 0000000002ab5e10 System.Threading.Thread
00000001b40ff390 0000000002ab2d78 Microsoft.Win32.SafeHandles.SafeFileHandle
00000001b40ff3e0 0000000002ab2d78 Microsoft.Win32.SafeHandles.SafeFileHandle
00000001b40ff3f0 0000000002ab2d78 Microsoft.Win32.SafeHandles.SafeFileHandle
00000001b40ff430 0000000002ab58a8 Microsoft.Win32.SafeHandles.SafeViewOfFileHandle
00000001b40ff4e0 0000000002ab2d78 Microsoft.Win32.SafeHandles.SafeFileHandle
```

Please note that we do not have global application flags:

```
0:002> !do 000000002ab2d78
Name: Microsoft.Win32.SafeHandles.SafeFileHandle
MethodTable: 00007feec88a260
EEClass: 00007feec34d340
Size: 32(0x20) bytes
File: C:\windows\Microsoft.Net\assembly\GAC_64\mscorlib\v4.0_4.0.0.0__b77a5c561934e089\mscorlib.dll
Fields:
MT Field Offset Type VT Attr Value Name
000007feec88a338 400060d 8 System.IntPtr 1 instance dead handle
000007feec8892b8 400060e 10 System.Int32 1 instance 3 _state
000007feec887de0 400060f 14 System.Boolean 1 instance 1 _ownsHandle
000007feec887de0 4000610 15 System.Boolean 1 instance 1 _fullyInitialized
```

```
0:002> !gflag
Current NtGlobalFlag contents: 0x00000000
```

Here is the exception stack trace from a different crash dump when we enable Application Verifier:

```
0:002> !gflag
Current NtGlobalFlag contents: 0x02000100
vrf - Enable application verifier
hpa - Place heap allocations at ends of pages

0:002> k
Child-SP RetAddr Call Site
00000000`24bac4a8 00000000`77cd3072 ntdll!NtWaitForSingleObject+0xa
00000000`24bac4b0 00000000`77cd32b5 ntdll!RtlReportExceptionEx+0x1d2
00000000`24bac5a0 000007fe`fa2c26fb ntdll!RtlReportException+0xb5
00000000`24bac620 00000000`77c2a5db verifier!AVrfpVectoredExceptionHandler+0x26b
00000000`24bac6b0 00000000`77c28e62 ntdll!RtlpCallVectoredHandlers+0xa8
00000000`24bac720 00000000`77c61248 ntdll!RtlDispatchException+0x22
00000000`24bace00 000007fe`fa2bae03 ntdll!KiUserExceptionDispatch+0x2e
00000000`24bad500 000007fe`fa2c268a verifier!VerifierStopMessageEx+0x6fb
00000000`24bad850 00000000`77c2a5db verifier!AVrfpVectoredExceptionHandler+0x1fa
00000000`24bad8e0 00000000`77c28e62 ntdll!RtlpCallVectoredHandlers+0xa8
00000000`24bad950 00000000`77c297c8 ntdll!RtlDispatchException+0x22
00000000`24bae030 00000000`77c612c7 ntdll!KiRaiseException+0x22f
00000000`24bae9e0 000007fe`fa2d2386 ntdll!KiRaiseUserExceptionDispatcher+0x3a
00000000`24baeab0 000007fe`fddb1873 verifier!AVrfpNtClose+0xbe
00000000`24baeae0 000007fe`fa2d4031 KERNELBASE!CloseHandle+0x13
00000000`24baeb10 000007fe`fa2d40cb verifier!AVrfpCloseHandleCommon+0x95
00000000`24baeb40 000007fe`77a11991 verifier!AVrfpKernelbaseCloseHandle+0x23
00000000`24baeb80 000007fe`fa2d4031 kernel32!CloseHandleImplementation+0x3d
00000000`24baeb90 000007fe`fa2d409c verifier!AVrfpCloseHandleCommon+0x95
*** WARNING: Unable to verify checksum for mscorlib.ni.dll
00000000`24baecc0 000007fe`e6a04418 verifier!AVrfpKernel32CloseHandle+0x2c
00000000`24baed00 000007fe`e0e9e03 mscorlib_ni+0x580418
00000000`24baedd0 000007fe`ec09e7e clr!CallDescrWorkerInternal+0x83
00000000`24baee10 000007fe`ec0ec860 clr!CallDescrWorkerWithHandler+0x4a
00000000`24baee50 000007fe`ec0f1a1d clr!DispatchCallSimple+0x85
00000000`24baeee0 000007fe`ec0f19ac clr!SafeHandle::RunReleaseMethod+0x69
00000000`24baef80 000007fe`ec0f180a clr!SafeHandle::Release+0x122
00000000`24baf050 000007fe`ec24863e clr!SafeHandle::Dispose+0x36
00000000`24baf0c0 000007fe`e694f7a6 clr!SafeHandle::Finalize+0xa2
00000000`24baf220 000007fe`ec0e9d56 mscorlib_ni+0x48f7a6
00000000`24baf260 000007fe`ec283c4e clr!FastCallFinalizeWorker+0x6
00000000`24baf290 000007fe`ec283bc3 clr!MethodDesc::RequiresFullSlotNumber+0x72
00000000`24baf2d0 000007fe`ec283bcf clr!MethodTable::CallFinalizer+0xa3
00000000`24baf310 000007fe`ec1fee46 clr!SVR::CallFinalizer+0x5f
00000000`24baf350 000007fe`ec1aac5b clr!SVR::CallFinalizer+0x102
00000000`24baf410 000007fe`ec0f458c clr!WKS::GCHeap::IsPromoted+0xee
00000000`24baf450 000007fe`ec0f451a clr!Frame::Pop+0x50
00000000`24baf490 000007fe`ec0f49f1 clr!COMCustomAttribute::PopSecurityContextFrame+0x192
00000000`24baf590 000007fe`ec1d1bfc clr!COMCustomAttribute::PopSecurityContextFrame+0xbd
00000000`24baf620 000007fe`ec1d1e59 clr!ManagedThreadBase_NoADTransition+0x3f
00000000`24baf680 000007fe`ec1533de clr!WKS::GCHeap::FinalizerThreadStart+0x193
00000000`24baf6c0 000007fe`fa2d4b87 clr!Thread::intermediateThreadProc+0x7d
00000000`24baf780 00000000`77a059ed verifier!AVrfpStandardThreadFunction+0x2b
00000000`24baf7c0 00000000`77c3c541 kernel32!BaseThreadInitThunk+0xd
00000000`24baf7f0 00000000`00000000 ntdll!RtlUserThreadStart+0x1d
```

```
0:002> !pe
There is no current managed exception on this thread
```

```
0:002> !CLRStack
OS Thread Id: 0x51e4 (2)
Child SP IP Call Site
0000000024baed28 0000000077c612fa [InlinedCallFrame: 0000000024baed28]
Microsoft.Win32.Win32Native.CloseHandle(IntPtr)
0000000024baed28 000007fe6a040148 [InlinedCallFrame: 0000000024baed28]
Microsoft.Win32.Win32Native.CloseHandle(IntPtr)
0000000024baed00 000007fe6a040418 DomainNeutralILStubClass.IL_STUB_PInvoke(IntPtr)
0000000024baef28 000007feec0e9e03 [GCFrame: 0000000024baef28]
0000000024baf078 000007feec0e9e03 [GCFrame: 0000000024baf078]
0000000024baf128 000007feec0e9e03 [HelperMethodFrame_1OBJ: 0000000024baf128]
System.Runtime.InteropServices.SafeHandle.InternalFinalize()
0000000024baf220 000007fe6e94f7a6 System.Runtime.InteropServices.SafeHandle.Finalize()
0000000024baf5d8 000007feec0e9d56 [DebuggerU2MCatchHandlerFrame: 0000000024baf5d8]
```

```
0:002> !dso
OS Thread Id: 0x51e4 (2)
RSP/REG Object Name
0000000024BAEDD0 000000000c282d78 Microsoft.Win32.SafeHandles.SafeFileHandle
0000000024BAEEF0 000000000c282d78 Microsoft.Win32.SafeHandles.SafeFileHandle
0000000024BAEF68 000000000c282d78 Microsoft.Win32.SafeHandles.SafeFileHandle
0000000024BAEF80 000000000c282d78 Microsoft.Win32.SafeHandles.SafeFileHandle
0000000024BAEFC0 000000000c282d78 Microsoft.Win32.SafeHandles.SafeFileHandle
0000000024BAF050 000000000c282d78 Microsoft.Win32.SafeHandles.SafeFileHandle
0000000024BAF0C0 000000000c282d78 Microsoft.Win32.SafeHandles.SafeFileHandle
0000000024BAF0E8 000000000c282d78 Microsoft.Win32.SafeHandles.SafeFileHandle
0000000024BAF170 000000000c282d78 Microsoft.Win32.SafeHandles.SafeFileHandle
0000000024BAF228 000000000c282d78 Microsoft.Win32.SafeHandles.SafeFileHandle
0000000024BAF260 000000000c282d78 Microsoft.Win32.SafeHandles.SafeFileHandle
0000000024BAF290 000000000c285e10 System.Threading.Thread
0000000024BAF2C0 000000000c282d78 Microsoft.Win32.SafeHandles.SafeFileHandle
0000000024BAF310 000000000c282d78 Microsoft.Win32.SafeHandles.SafeFileHandle
0000000024BAF320 000000000c282d78 Microsoft.Win32.SafeHandles.SafeFileHandle
```
