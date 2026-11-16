```
1 Id: 1344.1ab0 Suspend: 1 Teb: 000007ff`fffdb000 Unfrozen
# Call Site
00 ntdll!NtWaitForMultipleObjects
01 ntdll!TppWaiterpThread
02 kernel32!BaseThreadInitThunk
03 ntdll!RtlUserThreadStart
```

```
2 Id: 1344.1638 Suspend: 1 Teb: 000007ff`fffdf9000 Unfrozen
# Call Site
00 ntdll!RtlUserThreadStart
```

// 3rd dump: we see 2 threads start at the same time

```
. 0 Id: 1344.1ca4 Suspend: 1 Teb: 000007ff`fffdd000 Unfrozen
# Call Site
00 ntdll!RtlCompareMemoryUlong
01 ntdll!RtlpAllocateHeap
02 ntdll!RtlAllocateHeap
03 ntdll!RtlDebugAllocateHeap
04 ntdll! ?? ::FNODOBFM:::`string'
05 ntdll!RtlAllocateHeap
06 ole32!CRpcResolver::GetThreadWinstaDesktop
07 ole32!CRpcResolver::GetConnection
08 ole32!CoInitializeSecurity
09 ole32!InitializeSecurity
0a ole32!ChannelProcessInitialize
0b ole32!ComApartment::InitRemoting
0c ole32!CGIPTable::RegisterInterfaceInGlobalHlp
0d ole32!CGIPTable::RegisterInterfaceInGlobal
0e shell32!MarshallToGIT
0f shell32!CBrowserProgressAggregator::BeginSession
10 shell32!IUnknown_BeginBrowserProgressSession
11 shell32!CDefView::CreateViewWindow3
12 shell32!CExplorerBrowser::CreateViewWindow
13 shell32!CExplorerBrowser::_SwitchView
14 shell32!CExplorerBrowser::_BrowseToView
15 shell32!CExplorerBrowser::_BrowseObjectInternal
16 shell32!CExplorerBrowser::_OnBrowseObject
17 shell32!CExplorerBrowser::_BrowseObject
18 comdlg32!CPrintDlg::CreatePrintBrowser
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
```