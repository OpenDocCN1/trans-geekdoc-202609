```
29 comctl32!_CreatePageDialog
2a comctl32!_CreatePage
2b comctl32!PageChange
2c comctl32!InitPropSheetDlg
2d comctl32!PropSheetDlgProc
2e user32!UserCallDlgProcCheckWow
2f user32!DefDlgProcWorker
30 user32!InternalCreateDialog
31 user32!CreateDialogIndirectParamAorW
32 user32!CreateDialogIndirectParamW
33 comctl32!_RealPropertySheet
34 comctl32!_PropertySheet
35 comdlg32!Print_InvokePropertySheets
36 comdlg32!PrintDlgExX
37 comdlg32!PrintDlgExW
38 notepad!GetPrinterDCviaDialog
39 notepad!PrintIt
3a notepad!NPCommand
3b notepad!NPWndProc
3c user32!UserCallWinProcCheckWow
3d user32!DispatchMessageWorker
3e notepad!WinMain
3f notepad!DisplayNonGenuineDlgWorker
40 kernel32!BaseThreadInitThunk
41 ntdll!RtlUserThreadStart
```

```
1 Id: 1344.1ab0 Suspend: 1 Teb: 000007ff`fffd000 Unfrozen
# Call Site
00 ntdll!NtWaitForMultipleObjects
01 ntdll!TppWaiterpThread
02 kernel32!BaseThreadInitThunk
03 ntdll!RtlUserThreadStart
```

```
2 Id: 1344.1638 Suspend: 1 Teb: 000007ff`fffd9000 Unfrozen
# Call Site
00 ntdll!ZwAlpcSendWaitReceivePort
01 rpcrt4!LRPC_CCALL::SendReceive
02 rpcrt4!NdrpClientCall3
03 rpcrt4!NdrClientCall3
04 winspool!RpcSpoolOpenPrinter
05 winspool!OpenPrinterRPC
06 winspool!OpenPrinterW
07 prncache!PrintCache::Listeners::Listener::Start
08 prncache!PrintCache::Listeners::Listener::StartCB
09 ntdll!TppWorkpExecuteCallback
0a ntdll!TppWorkerThread
0b kernel32!BaseThreadInitThunk
0c ntdll!RtlUserThreadStart
```

```
3 Id: 1344.830 Suspend: 1 Teb: 000007ff`fffd7000 Unfrozen
# Call Site
00 ntdll!NtWaitForMultipleObjects
01 KERNELBASE!WaitForMultipleObjectsEx
02 kernel32!WaitForMultipleObjects
03 prncache!PrintCache::Store::CacheStore::RegistryMonitor::MonitorRegistryChanges
04 prncache!PrintCache::Store::CacheStore::RegistryMonitor::MonitorRegistryChangesThreadProc
```