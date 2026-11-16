```
24 comctl32!CallNextSubclassProc
25 comctl32!MasterSubclassProc
26 user32!UserCallWinProcCheckWow
27 user32!DispatchClientMessage
28 user32!_fnDOWORD
29 ntdll!KiUserCallbackDispatcherContinue
2a user32!NtUserDispatchMessage
2b user32!DispatchMessageWorker
2c user32!IsDialogMessageW
2d comctl32!Prop_IsDialogMessage
2e comctl32!RealPropertySheet
2f comctl32!_PropertySheet
30 comdlg32!Print_InvokePropertySheets
31 comdlg32!PrintDlgExX
32 comdlg32!PrintDlgExW
33 notepad!GetPrinterDCviaDialog
34 notepad!PrintIt
35 notepad!NPCommand
36 notepad!NPWndProc
37 user32!UserCallWinProcCheckWow
38 user32!DispatchMessageWorker
39 notepad!WinMain
3a notepad!DisplayNonGenuineDlgWorker
3b kernel32!BaseThreadInitThunk
3c ntdll!RtlUserThreadStart
```

```
1 Id: 1344.1ab0 Suspend: 1 Teb: 000007ff`fffdb000 Unfrozen
# Call Site
00 ntdll!NtWaitForMultipleObjects
01 ntdll!TppWaiterpThread
02 kernel32!BaseThreadInitThunk
03 ntdll!RtlUserThreadStart
```

```
2 Id: 1344.1638 Suspend: 1 Teb: 000007ff`ffff9000 Unfrozen
# Call Site
00 ntdll!NtUnmapViewOfSection
01 KERNELBASE!FreeLibrary
02 user32!PrivateExtractIconsW
03 shell32!SHPrivateExtractIcons
04 shell32!SHDefExtractIconW
05 shell32!CExtractIcon::_ExtractW
06 shell32!CExtractIconBase::Extract
07 shell32!IExtractIcon_Extract
08 shell32!GetIIIndexGivenPIIcon
09 shell32!GetIIIndexFromItem
0a shell32!SHGetIconIndexFromPIDL
0b shell32!MapIDListToIconIIndex
0c shell32!CLoadSystemIconTask::InternalResumeRT
0d shell32!CRunnableTask::Run
0e shell32!CShellTask::TT_Run
0f shell32!CShellTaskThread::ThreadProc
10 shell32!CShellTaskThread::s_ThreadProc
11 shlwapi!ExecuteWorkItemThreadProc
12 ntdll!RtlpTpWorkCallback
13 ntdll!TppWorkerThread
```