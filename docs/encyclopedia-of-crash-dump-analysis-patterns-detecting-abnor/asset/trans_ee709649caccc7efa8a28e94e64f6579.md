
```
1a ole32!CCClassCache::GetClassObject
1b ole32!CServerContextActivator::CreateInstance
1c ole32!ActivationPropertiesIn::DelegateCreateInstance
1d ole32!CApartmentActivator::CreateInstance
1e ole32!CProcessActivator::CCICallback
1f ole32!CProcessActivator::AttemptActivation
20 ole32!CProcessActivator::ActivateByContext
21 ole32!CProcessActivator::CreateInstance
22 ole32!ActivationPropertiesIn::DelegateCreateInstance
23 ole32!CClientContextActivator::CreateInstance
24 ole32!ActivationPropertiesIn::DelegateCreateInstance
25 ole32!ICoCreateInstanceEx
26 ole32!CoCreateInstance
27 shell32!_SHCoCreateInstance
28 shell32!SHExtCoCreateInstance
29 shell32!DCA_SHExtCoCreateInstance
2a shell32!CFSIconOverlayManager::_s_LoadIconOverlayIdentifiers
2b shell32!CFSIconOverlayManager::CreateInstance
2c shell32!IconOverlayManagerInit
2d shell32!GetIconOverlayManager
2e shell32!FileIconInit
2f shell32!Shell_GetImageLists
30 comdlg32!PrintDlgDialog::CPrintDialog
31 comdlg32!Print_GeneralDlgProc
32 user32!UserCallDlgProcCheckWow
33 user32!DefDlgProcWorker
34 user32!InternalCreateDialog
35 user32!CreateDialogIndirectParamAorW
36 user32!CreateDialogIndirectParamW
37 comctl32!_CreatePageDialog
38 comctl32!_CreatePage
39 comctl32!PageChange
3a comctl32!InitPropSheetDlg
3b comctl32!PropSheetDlgProc
3c user32!UserCallDlgProcCheckWow
3d user32!DefDlgProcWorker
3e user32!InternalCreateDialog
3f user32!CreateDialogIndirectParamAorW
40 user32!CreateDialogIndirectParamW
41 comctl32!_RealPropertySheet
42 comctl32!PropertySheet
43 comdlg32!Print_InvokePropertySheets
44 comdlg32!PrintDlgEx
45 comdlg32!PrintDlgExW
46 notepad!GetPrinterDCviaDialog
47 notepad!PrintIt
48 notepad!NPCommand
49 notepad!NPWndProc
4a user32!UserCallWinProcCheckWow
4b user32!DispatchMessageWorker
4c notepad!WinMain
4d notepad!DisplayNonGenuineDlgWorker
4e kernel32!BaseThreadInitThunk
4f ntdll!RtlUserThreadStart
```

```
1 Id: 1344.1ab0 Suspend: 1 Teb: 000007ff`fffdb000 Unfrozen
# Call Site
00 ntdll!NtWaitForMultipleObjects
01 ntdll!TppWaiterThread
02 kernel32!BaseThreadInitThunk
03 ntdll!RtlUserThreadStart
```

```
2 Id: 1344.1638 Suspend: 1 Teb: 000007ff`fffdf9000 Unfrozen
# Call Site
00 ntdll!RtlUserThreadStart
```

### 第 3 个转储：我们看到 2 个线程同时启动

```
. 0 Id: 1344.1ca4 Suspend: 1 Teb: 000007ff`fffdd000 Unfrozen
# Call Site
00 ntdll!RtlCompareMemoryUlong
01 ntdll!RtlpAllocateHeap
02 ntdll!RtlAllocateHeap
03 ntdll!RtlDebugAllocateHeap
04 ntdll! ?? ::FNODOBFM::`string'
05 ntdll!RtlAllocateHeap
06 ole32!CRpcResolver::GetThreadWinstaDesktop
07 ole32!CRpcResolver::GetConnection
08 ole32!CoInitializeSecurity
09 ole32!InitializeSecurity
0a ole32!ChannelProcessInitialize
0b ole32!CComApartment::InitRemoting
0c ole32!CGIPTable::RegisterInterfaceInGlobalHlp
0d ole32!CGIPTable::RegisterInterfaceInGlobal
0e shell32!MarshallToGIT
0f shell32!CBrowserProgressAggregator::BeginSession
10 shell32!IUnknown_BeginBrowserProgressSession
11 shell32!CDefView::CreateViewWindow3
12 shell32!CExplorerBrowser::_CreateViewWindow
13 shell32!CExplorerBrowser::_SwitchView
14 shell32!CExplorerBrowser::_BrowseToView
15 shell32!CExplorerBrowser::_BrowseObjectInternal
16 shell32!CExplorerBrowser::_OnBrowseObject
17 shell32!CExplorerBrowser::_BrowseObject
18 comdlg32!CPrintDialog::CreatePrintBrowser
19 comdlg32!CPrintDialog::OnInitDialog
1a comdlg32!Print_GeneralDlgProc
1b user32!UserCallDlgProcCheckWow
1c user32!DefDlgProcWorker
1d user32!InternalCreateDialog
1e user32!CreateDialogIndirectParamAorW
1f user32!CreateDialogIndirectParamW
20 comctl32!CreatePageDialog
21 comctl32!_CreatePage
22 comctl32!PageChange
23 comctl32!InitPropSheetDlg
24 comctl32!PropSheetDlgProc
25 user32!UserCallDlgProcCheckWow
26 user32!DefDlgProcWorker
27 user32!InternalCreateDialog
28 user32!CreateDialogIndirectParamAorW
29 user32!CreateDialogIndirectParamW
2a comctl32!_RealPropertySheet
2b comctl32!_PropertySheet
2c comdlg32!Print_InvokePropertySheets
2d comdlg32!PrintDlgEx
2e comdlg32!PrintDlgExW
2f notepad!GetPrinterDCviaDialog
30 notepad!PrintIt
31 notepad!NPCommand
32 notepad!NPWndProc
33 user32!UserCallWinProcCheckWow
34 user32!DispatchMessageWorker
35 notepad!WinMain
36 notepad!DisplayNonGenuineDlgWorker
37 kernel32!BaseThreadInitThunk
38 ntdll!RtlUserThreadStart
```

```
1 Id: 1344.1ab0 Suspend: 1 Teb: 000007ff`fffdb000 Unfrozen
# Call Site
00 ntdll!NtWaitForMultipleObjects
01 ntdll!TppWaiterThread
02 kernel32!BaseThreadInitThunk
03 ntdll!RtlUserThreadStart
```

```
2 Id: 1344.1638 Suspend: 1 Teb: 000007ff`fffd9000 Unfrozen
# Call Site
00 ntdll!ZwAlpcSendWaitReceivePort
01 rpcrt4!LRPC_CCALL::SendReceive
02 rpcrt4!NdrpcClientCall13
03 rpcrt4!NdrClientCall13
04 sechost!LsLookupOpenLocalPolicy
05 sechost!LookupAccountNameInternal
06 sechost!LookupAccountNameLocalW
07 rpcrt4!RpcpLookupAccountNameDirect
08 rpcrt4!RpcpLookupAccountName
09 rpcrt4!LRPC_BASE_BINDING_HANDLE::SetAuthInformation
0a rpcrt4!LRPC_BINDING_HANDLE::SetAuthInformation
0b rpcrt4!RpcBindingSetAuthInfoExW
0c winspool!STRING_HANDLE_bind
0d rpcrt4!GenericHandleMgr
0e rpcrt4!ExplicitBindingHandleMgr
0f rpcrt4!Ndr64pClientSetupTransferSyntax
10 rpcrt4!NdrpcClientCall13
11 rpcrt4!NdrClientCall13
12 winspool!RpcSplOpenPrinter
13 winspool!OpenPrinterRPC
14 winspool!OpenPrinter2W
15 prncache!PrintCache::Listeners::Listener::Start
16 prncache!PrintCache::Listeners::Listener::StartCB
17 ntdll!TppWorkpExecuteCallback
18 ntdll!TppWorkerThread
19 kernel32!BaseThreadInitThunk
1a ntdll!RtlUserThreadStart
```

```
3 Id: 1344.830 Suspend: 1 Teb: 000007ff`fffd7000 Unfrozen
# Call Site
00 ntdll!RtlUserThreadStart

4 Id: 1344.1edc Suspend: 0 Teb: 000007ff`fffd5000 Unfrozen
# Call Site
00 ntdll!RtlUserThreadStart
```

### 第 4 个转储

```
. 0 Id: 1344.1ca4 Suspend: 1 Teb: 000007ff`fffd0000 Unfrozen
# Call Site
00 ntdll!RtlCompareMemoryUlong
01 ntdll!RtlpAllocateHeap
02 ntdll!RtlAllocateHeap
03 ntdll!RtlDebugAllocateHeap
04 ntdll! ?? ::FNODOBFM::`string'
05 ntdll!RtlAllocateHeap
06 ole32!CRpcResolver::GetThreadWinstaDesktop
07 ole32!CRpcResolver::GetConnection
08 ole32!CoInitializeSecurity
09 ole32!InitializeSecurity
0a ole32!ChannelProcessInitialize
0b ole32!CComApartment::InitRemoting
0c ole32!CGIPTable::RegisterInterfaceInGlobalHlp
0d ole32!CGIPTable::RegisterInterfaceInGlobal
0e shell32!MarshallToGIT
0f shell32!CBrowserProgressAggregator::BeginSession
10 shell32!IUnknown_BeginBrowserProgressSession
11 shell32!CDefView::CreateViewWindow3
12 shell32!CExplorerBrowser::_CreateViewWindow
13 shell32!CExplorerBrowser::_SwitchView
14 shell32!CExplorerBrowser::_BrowseToView
15 shell32!CExplorerBrowser::_BrowseObjectInternal
16 shell32!CExplorerBrowser::_OnBrowseObject
17 shell32!CExplorerBrowser::_BrowseObject
18 comdlg32!CPrintDialog::CreatePrintBrowser
19 comdlg32!CPrintDialog::OnInitDialog
1a comdlg32!Print_GeneralDlgProc
1b user32!UserCallDlgProcCheckWow
1c user32!DefDlgProcWorker
1d user32!InternalCreateDialog
1e user32!CreateDialogIndirectParamAorW
1f user32!CreateDialogIndirectParamW
20 comctl32!CreatePageDialog
21 comctl32!_CreatePage
22 comctl32!PageChange
23 comctl32!InitPropSheetDlg
24 comctl32!PropSheetDlgProc
25 user32!UserCallDlgProcCheckWow
26 user32!DefDlgProcWorker
27 user32!InternalCreateDialog
28 user32!CreateDialogIndirectParamAorW
29 user32!CreateDialogIndirectParamW
2a comctl32!_RealPropertySheet
2b comctl32!_PropertySheet
2c comdlg32!Print_InvokePropertySheets
2d comdlg32!PrintDlgEx
2e comdlg32!PrintDlgExW
2f notepad!GetPrinterDCviaDialog
30 notepad!PrintIt
31 notepad!NPCommand
32 notepad!NPWndProc
33 user32!UserCallWinProcCheckWow
34 user32!DispatchMessageWorker
35 notepad!WinMain
36 notepad!DisplayNonGenuineDlgWorker
37 kernel32!BaseThreadInitThunk
38 ntdll!RtlUserThreadStart
```

```
1 Id: 1344.1ab0 Suspend: 1 Teb: 000007ff`fffdb000 Unfrozen
# Call Site
00 ntdll!NtWaitForMultipleObjects
01 ntdll!TppWaiterThread
02 kernel32!BaseThreadInitThunk
03 ntdll!RtlUserThreadStart
```

```
2 Id: 1344.1638 Suspend: 1 Teb: 000007ff`fffd9000 Unfrozen
# Call Site
00 ntdll!ZwAlpcSendWaitReceivePort
01 rpcrt4!LRPC_CCALL::SendReceive
02 rpcrt4!NdrpcClientCall13
03 rpcrt4!NdrClientCall13
04 sechost!LsLookupOpenLocalPolicy
05 sechost!LookupAccountNameInternal
06 sechost!LookupAccountNameLocalW
07 rpcrt4!RpcpLookupAccountNameDirect
08 rpcrt4!RpcpLookupAccountName
09 rpcrt4!LRPC_BASE_BINDING_HANDLE::SetAuthInformation
0a rpcrt4!LRPC_BINDING_HANDLE::SetAuthInformation
0b rpcrt4!RpcBindingSetAuthInfoExW
0c winspool!STRING_HANDLE_bind
0d rpcrt4!GenericHandleMgr
0e rpcrt4!ExplicitBindingHandleMgr
0f rpcrt4!Ndr64pClientSetupTransferSyntax
10 rpcrt4!NdrpcClientCall13
11 rpcrt4!NdrClientCall13
12 winspool!RpcSplOpenPrinter
13 winspool!OpenPrinterRPC
14 winspool!OpenPrinter2W
15 prncache!PrintCache::Listeners::Listener::Start
16 prncache!PrintCache::Listeners::Listener::StartCB
17 ntdll!TppWorkpExecuteCallback
18 ntdll!TppWorkerThread
19 kernel32!BaseThreadInitThunk
1a ntdll!RtlUserThreadStart
```
