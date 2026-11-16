```
0c user32!AddEllipsisAndDrawLine
0d user32!DrawTextExWorker
0e user32!DrawTextW
0f comctl32!CLVView::_ComputeLabelSizeWorker
10 comctl32!CLVView::v_RecomputeLabelSize
11 comctl32!CLVListView::v_DrawItem
12 comctl32!CLVDrawItemManager::DrawItem
13 comctl32!CLVDrawManager::_PaintItems
14 comctl32!CLVDrawManager::_PaintWorkArea
15 comctl32!CLVDrawManager::_OnPaintWorkAreas
16 comctl32!CLVDrawManager::_OnPaint
17 comctl32!CListView::WndProc
18 comctl32!CListView::s_WndProc
19 user32!UserCallWinProcCheckWow
1a user32!CallWindowProcAorW
1b user32!CallWindowProcW
1c comctl32!CallOriginalWndProc
1d comctl32!CallNextSubclassProc
1e comctl32!DefSubclassProc
1f shell32!DefSubclassProc
20 shell32!CListViewHost::_ListViewSubclassWndProc
21 comctl32!CallNextSubclassProc
22 comctl32!MasterSubclassProc
23 user32!UserCallWinProcCheckWow
24 user32!DispatchClientMessage
25 user32!_fnDOWORD
26 ntdll!KiUserCallbackDispatcherContinue
27 user32!NtUserDispatchMessage
28 user32!DispatchMessageWorker
29 user32!IsDialogMessageW
2a comctl32!Prop_IsDialogMessage
2b comctl32!_RealPropertySheet
2c comctl32!_PropertySheet
2d comdlg32!Print_InvokePropertySheets
2e comdlg32!PrintDlgEx
2f comdlg32!PrintDlgExW
30 notepad!GetPrinterDCviaDialog
31 notepad!PrintIt
32 notepad!NPCommand
33 notepad!NPWndProc
34 user32!UserCallWinProcCheckWow
35 user32!DispatchMessageWorker
36 notepad!WinMain
37 notepad!DisplayNonGenuineDlgWorker
38 kernel32!BaseThreadInitThunk
39 ntdll!RtlUserThreadStart
```

```
1 Id: 1344.1ab0 Suspend: 1 Teb: 000007ff`fffd000 Unfrozen
# Call Site
00 ntdll!NtWaitForMultipleObjects
01 ntdll!TppWaiterpThread
02 kernel32!BaseThreadInitThunk
03 ntdll!RtlUserThreadStart
```