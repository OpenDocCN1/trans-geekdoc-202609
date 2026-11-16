

```
000007fe`fdc48942 usp10!COTlsClient::AllocMem+0x12
000007fe`fdc48942 usp10!COTlsClient::AllocMem+0x12
000007fe`fdc1d4f1 usp10!UspFreeMem+0x61
000007fe`fdc4896e usp10!COTlsClient::FreeMem+0xe
000007fe`fdc6e817 usp10!ApplyFeatures+0xa17
000007fe`fdc67f22 usp10!ApplyLookup+0x592
000007fe`fdc48901 usp10!COTlsClient::GetDefaultGlyphs+0x131
000007fe`fdc60100 usp10!HangulEngineGetGlyphs+0x2c0
000007fe`fdc10359 usp10!CuspShapingClient::AllocMem+0x49
000007fe`fdc48942 usp10!COTlsClient::AllocMem+0x12
000007fe`fdc10359 usp10!CuspShapingClient::AllocMem+0x49
000007fe`fdc1d4f1 usp10!UspFreeMem+0x61
000007fe`fdc48942 usp10!COTlsClient::AllocMem+0x12
000007fe`fdc1d4f1 usp10!UspFreeMem+0x61
000007fe`fdc4896e usp10!COTlsClient::FreeMem+0xe
000007fe`fdc6e817 usp10!ApplyFeatures+0xa17
000007fe`fdc6a8a8 usp10!RePositionOtlGlyphs+0x238
000007fe`fdc48901 usp10!COTlsClient::GetDefaultGlyphs+0x131
000007fe`fdc60100 usp10!HangulEngineGetGlyphs+0x2c0
000007fe`fdc48798 usp10!COTlsClient::ReleaseOtTable+0x78
000007fe`fdc6ae85 usp10!OtlReleaseMgr::detach+0xc5
00000000`7717c63e ntdll!EtwEventWriteNoRegistration+0xae
000007fe`fdc48999 usp10!COTlsClient::Release+0x49
00000000`771150d3 ntdll!RtlNtStatusToDosError+0x27
00000000`7716bd85 ntdll!WaitForWerSvc+0x85
00000000`7717b94e ntdll!WerpAllocateAndInitializeSid+0xbe
00000000`7716bd90 ntdll! ?? ::FNODOBFM::`string'
00000000`7717d5cf ntdll!WerpReportSect+0x3f
00000000`7718123d ntdll!SendMessageToWERService+0x22d
00000000`77181260 ntdll! ?? ::FNODOBFM::`string'
00000000`77182308 ntdll!ReportExceptionInternal+0xc8
000007fe`fd061430 KERNELBASE!WaitForMultipleObjectsEx+0xe8
00000000`76ec1723 kernel32!WaitForMultipleObjectsExImplementation+0xb3
00000000`76f3b5e5 kernel32!WerpReportFaultInternal+0x215
00000000`76f3b767 kernel32!WerpReportFault+0x77
00000000`76f3b7bf kernel32!BasepReportFault+0x1f
00000000`76f3b9dc kernel32!UnhandledExceptionFilter+0x1fc
00000000`77118d7e ntdll!RtlpFindUnicodeStringInSection+0x50e
00000000`771198fc ntdll!LdrpFindLoadedDll+0x10c
00000000`770e9caa ntdll!RtlDecodePointer+0x2a
00000000`770c0000 ntdll!RtlDeactivateActivationContext <PERF> (ntdll+0x0)
00000000`771e8180 ntdll!string'+0xc040
00000000`771e818c ntdll!string'+0xc04c
00000000`77153398 ntdll! ?? ::FNODOBFM::`string'+0x2365
00000000`770d85c8 ntdll!_C_specific_handler+0x8c
00000000`770c0000 ntdll!RtlDeactivateActivationContext <PERF> (ntdll+0x0)
00000000`770ec541 ntdll!RtlUserThreadStart+0x1d
00000000`770e9d2d ntdll!RtlpExecuteHandlerForException+0xd
00000000`77220dd2 ntdll!CsrPortMemoryRemoteDelta <PERF> (ntdll+0x142dd0)
00000000`770d91cf ntdll!RtlDispatchException+0x45a
00000000`76faddaa kernel32!_PchSym_ <PERF> (kernel32+0x10dda0)
00000000`7711920a ntdll!RtlDosApplyFileIsolationRedirection_Ustr+0x3da
00000000`77220dd2 ntdll!CsrPortMemoryRemoteDelta <PERF> (ntdll+0x142dd0)
00000000`771e8180 ntdll!string'+0xc040
00000000`770c0000 ntdll!RtlDeactivateActivationContext <PERF> (ntdll+0x0)
00000000`770ec541 ntdll!RtlUserThreadStart+0x1d
00000000`770c0000 ntdll!RtlDeactivateActivationContext <PERF> (ntdll+0x0)
00000000`7720d2dd ntdll!CsrPortMemoryRemoteDelta <PERF> (ntdll+0x142dd0)
00000000`771d7718 ntdll!LdrpDefaultExtension
00000000`770d852c ntdll!_C_specific_handler
00000000`771e8180 ntdll!string'+0xc040
000007fe`ff36250c mscorlib!_szComClassName
00000000`770e7a33 ntdll!LdrpFindOrMapDll+0x138
00000000`771192a8 ntdll!LdrpApplyFileNameRedirection+0x2d3
00000000`771d5430 ntdll!RtlpInterceptorRoutines
00000000`7711d448 ntdll!RtlAllocateHeap+0xe4
00000000`76df8b88 user32!GetPropW+0x4d
00000000`76fd7931 user32!IsWindow+0x9
00000000`770f41c8 ntdll!RtlpReAllocateHeap+0x178
000007fe`fb601381 uxtheme!CThemeWnd::_PreDefWindowProc+0x31
00000000`76eb59e0 kernel32!BaseThreadInitThunk
00000000`ffdbdb32 calc!CTimerCalc::Start+0xa9
00000000`ff9d0000 calc!CCalculatorController::<C>CalculatorController <PERF> (calc+0x0)
00000000`ffeca64 calc!_dyn_tls_init_callback <PERF> (calc+0x7ac64)
00000000`76ea0000 kernel32!TestResourceDataMatchEntry <PERF> (kernel32+0x0)
00000000`76fadada kernel32!__PchSym_ <PERF> (kernel32+0x10dda0)
00000000`770c0000 ntdll!RtlDeactivateActivationContext <PERF> (ntdll+0x0)
00000000`7720d2dd ntdll!CsrPortMemoryRemoteDelta <PERF> (ntdll+0x142dd0)
00000000`76fd760e user32!RealDefWindowProc+0x5a
000007fe`fb600037 uxtheme!operator delete <PERF> (uxtheme+0x37)
000007fe`77111248 ntdll!KiUserExceptionDispatcher+0x2e
000007fe`fb63fb40 uxtheme!$VProc_ImageExportDirectory
00000000`ffdbdb27 calc!CTimedCalc::WatchDogThread+0xb2
00000000`76fe76c2 user32!DefDlgProc+0x36
00000000`76fd9bef user32!UserCallWinProcCheckWow+0x1cb
00000000`76fd9b43 user32!UserCallWinProcCheckWow+0x99
00000000`76fd9bef user32!UserCallWinProcCheckWow+0x1cb
00000000`76fd72cb user32!DispatchClientMessage+0xc3
00000000`770e46b4 ntdll!NtdllDialogWndProc_W
00000000`ffdbdb27 calc!CTimedCalc::WatchDogThread+0xb2
00000000`77101530 ntdll!NtdllDispatchMessage_W
00000000`76fe505b user32!DialogBox2+0x2ec
00000000`ff9d0000 calc!CCalculatorController::<C>CalculatorController <PERF> (calc+0x0)
00000000`76fe4edd user32!InternalDialogBox+0x135
00000000`ffedceb0 calc!CTimerCalc::TimeOutDlgProc
00000000`ff9d0000 calc!CCalculatorController::<C>CalculatorController <PERF> (calc+0x0)
00000000`76fe4f52 user32!DialogBoxIndirectParamAorW+0x58
00000000`ffdcdeb0 calc!CTimerCalc::TimeOutDlgProc
00000000`ff9d0000 calc!CCalculatorController::<C>CalculatorController <PERF> (calc+0x0)
00000000`76fd476e user32!DialogBoxParamW+0x66
00000000`ffdcdeb0 calc!CTimerCalc::TimeOutDlgProc
00000000`ffdbdafa calc!CTimerCalc::WatchDogThread+0x72
00000000`76eb59ed kernel32!BaseThreadInitThunk+0xd
00000000`770ec541 ntdll!RtlUserThreadStart+0x1d
00000000`76fb7e0e kernel32!UnhandledExceptionFilter
```

The name for this pattern comes from rough sets 180 in mathematics.

## Same Vendor

Sometimes we have very similar abnormal software behavior dispositions (like crashes with similar stack traces) for different applications or services. In such cases, we should also check application or service vendor and copyright in the output of lmv command. Similar to Template Module (page 997) Same Vendor pattern can be useful to relate such different incidents. Usually, in the same company, code and people reuse tends to distribute code fragments and code construction styles across different product lines, and, therefore, software defects may surface in different images. For example:

```
0:000> lmv m ApplicationA
start end module name
00400000 00d99000 ApplicationA (deferred)
[...]
Image name: ApplicationA.exe
Timestamp: [...]
CheckSum: 00000000
[...]
CompanyName: CompanyA
ProductName: CompanyA Application
LegalCopyright: Copyright (c) CompanyA
[...]
0:000> lmv m ApplicationB
start end module name
00400000 019d0000 ApplicationB C (no symbols)
Image name: ApplicationB.exe
[...]
CompanyName: CompanyA
ProductName: ApplicationB
LegalCopyright: Copyright (c) CompanyA
[...]
```

## Screwbolt Wait Chain

Here we introduce another **Wait Chain** (page 1082) pattern where a client thread makes a request and a created server thread servicing the request makes another request to the client which creates a new client thread to service the server request. The new client thread makes a request to the server again, and a new server thread is created which makes a new client request, and so on. The additional signs here may be an abnormal number of threads and possibly **Handle Leak** (page 416) pattern although the latter may be present only in a client or server process only. **Thread Age** (page 1001), **Waiting Thread Time** (page 1137), and common **Blocking Module** (page 96) patterns may be used to unwind the chain and diagnose the possible problem module and corresponding **Module Product Process** (page 697). The pattern is illustrated in this diagram:

![](img/d6dfefc8f9ab7106c77a723ff84aaa6d_842_0.png)

Although we initially found this pattern related to LPC /ALPC IPC (page 1097) we think it is not limited to it and can occur in different client-server communication implementations.

