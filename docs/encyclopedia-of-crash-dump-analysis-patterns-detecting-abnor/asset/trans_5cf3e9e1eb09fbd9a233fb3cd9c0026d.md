
### 调用站点
- 02 kernel32!BaseRegGetUserAndMachineClass
- 03 kernel32!LocalBaseRegQueryValue
- 04 kernel32!RegQueryValueExW
- 05 shlwapi!SHRegQueryValueW
- 06 shlwapi!SHRegGetValueW
- 07 shlwapi!SHQueryValueExW
- 08 shell32!_GetServerInfo
- 09 shell32!_SHCoCreateInstance
- 0a shell32!CRegFolder::_CreateCachedRegFolder
- 0b shell32!CRegFolder::_BindToItem
- 0c shell32!CRegFolder::_BindToObject
- 0d shell32!CRegFolder::_BindToItem
- 0e shell32!CRegFolder::_BindToObject
- 0f shell32!SHBindToObject
- 10 shell32!CIconOverlayTask::InternalResumeRT
- 11 shell32!CRunnableTask::Run
- 12 shell32!CShellTask::_TT_Run
- 13 shell32!CShellTaskThread::ThreadProc
- 14 shell32!CShellTaskThread::s_ThreadProc
- 15 shlwapi!ExecuteWorkItemThreadProc
- 16 ntdll!RtlpTpWorkCallback
- 17 ntdll!TppWorkerThread
- 18 kernel32!BaseThreadInitThunk
- 19 ntdll!RtlUserThreadStart

### 线程 8
Id: 1344.1b80, 挂起: 1, Teb: 000007ff`fffaa000, 未冻结

#### 调用站点
- 00 ntdll!ZwDelayExecution
- 01 KERNELBASE!SleepEx
- 02 ole32!CROIDTable::WorkerThreadLoop
- 03 ole32!CRpcThread::WorkerLoop
- 04 ole32!CRpcThreadCache::RpcWorkerThreadEntry
- 05 kernel32!BaseThreadInitThunk
- 06 ntdll!RtlUserThreadStart

### 线程 9
Id: 1344.eb8, 挂起: 1, Teb: 000007ff`fffa8000, 未冻结

#### 调用站点
- 00 ntdll!RtlUserThreadStart

### 第 11 转储

### 线程 0
Id: 1344.1ca4, 挂起: 1, Teb: 000007ff`fffdd000, 未冻结

#### 调用站点
- 00 usp10!GenericEngineGetGlyphs
- 01 usp10!ShlShape
- 02 usp10!ScriptShape
- 03 usp10!RenderItemNoFallback
- 04 usp10!RenderItemWithFallback
- 05 usp10!RenderItem
- 06 usp10!ScriptStringAnalyzeGlyphs
- 07 usp10!ScriptStringAnalyse
- 08 lpk!LpkCharsetDraw
- 09 lpk!LpkDrawTextEx
- 0a user32!DT_GetExtentMinusPrefixes
- 0b user32!NeedsEndEllipsis
- 0c user32!AddEllipsisAndDrawLine
- 0d user32!DrawTextExWorker
- 0e user32!DrawTextW
- 0f comctl32!CLVView::_ComputeLabelSizeWorker
- 10 comctl32!CLVView::v_RecomputeLabelSize
- 11 comctl32!CLVListView::v_DrawItem
- 12 comctl32!CLVDrawItemManager::DrawItem
- 13 comctl32!CLVDrawManager::_PaintItems
- 14 comctl32!CLVDrawManager::_PaintWorkArea
- 15 comctl32!CLVDrawManager::_OnPaintWorkAreas
- 16 comctl32!CLVDrawManager::_OnPaint
- 17 comctl32!CListView::WndProc
- 18 comctl32!CListView::s_WndProc
- 19 user32!UserCallWinProcCheckWow
- 1a user32!CallWindowProcAorW
- 1b user32!CallWindowProcW
- 1c comctl32!CallOriginalWndProc
- 1d comctl32!CallNextSubclassProc
- 1e comctl32!DefSubclassProc
- 1f shell32!DefSubclassProc
- 20 shell32!CListViewHost::_ListViewSubclassWndProc
- 21 comctl32!CallNextSubclassProc
- 22 comctl32!MasterSubclassProc
- 23 user32!UserCallWinProcCheckWow
- 24 user32!DispatchClientMessage
- 25 user32!_fnDOWORD
- 26 ntdll!KiUserCallbackDispatcherContinue
- 27 user32!NtUserDispatchMessage
- 28 user32!DispatchMessageWorker
- 29 user32!IsDialogMessageW
- 2a comctl32!Prop_IsDialogMessage
- 2b comctl32!_RealPropertySheet
- 2c comctl32!_PropertySheet
- 2d comdlg32!Print_InvokePropertySheets
- 2e comdlg32!PrintDlgEx
- 2f comdlg32!PrintDlgExW
- 30 notepad!GetPrinterDCviaDialog
- 31 notepad!PrintIt
- 32 notepad!NPCommand
- 33 notepad!NPWndProc
- 34 user32!UserCallWinProcCheckWow
- 35 user32!DispatchMessageWorker
- 36 notepad!WinMain
- 37 notepad!DisplayNonGenuineDlgWorker
- 38 kernel32!BaseThreadInitThunk
- 39 ntdll!RtlUserThreadStart

### 线程 1
Id: 1344.1ab0, 挂起: 1, Teb: 000007ff`fffd000, 未冻结

#### 调用站点
- 00 ntdll!NtWaitForMultipleObjects
- 01 ntdll!TppWaiterThread
- 02 kernel32!BaseThreadInitThunk
- 03 ntdll!RtlUserThreadStart

### 线程 2
Id: 1344.1638, 挂起: 1, Teb: 000007ff`fffd9000, 未冻结

#### 调用站点
- 00 ntdll!NtWaitForSingleObject
- 01 ntdll!RtlpWaitOnCriticalSection
- 02 ntdll!RtlEnterCriticalSection
- 03 user32!BitmapFromDIB
- 04 user32!ConvertDIBBitmap
- 05 user32!ConvertDIBIcon
- 06 user32!CreateIconFromResourceEx
- 07 user32!PrivateEnumProc
- 08 kernel32!EnumResourceNamesInternal
- 09 kernel32!EnumResourceNamesExW
- 0a user32!PrivateExtractIconsW
- 0b shell32!SHPrivateExtractIcons
- 0c shell32!SHDefExtractIconW
- 0d shell32!CExtractIcon::_ExtractW
- 0e shell32!CExtractIconBase::Extract
- 0f shell32!IExtractIcon_Extract
- 10 shell32!_GetIIndexGivenPXIcon
- 11 shell32!_GetIIndexFromItem
- 12 shell32!SHGetIconIndexFromPIDL
- 13 shell32!MapIDListToIconIndex
- 14 shell32!CLoadSystemIconTask::InternalResumeRT
- 15 shell32!CRunnableTask::Run
- 16 shell32!CShellTask::_TT_Run
- 17 shell32!CShellTaskThread::ThreadProc
- 18 shell32!CShellTaskThread::s_ThreadProc
- 19 shlwapi!ExecuteWorkItemThreadProc
- 1a ntdll!RtlpTpWorkCallback
- 1b ntdll!TppWorkerThread
- 1c kernel32!BaseThreadInitThunk
- 1d ntdll!RtlUserThreadStart

### 线程 3
Id: 1344.830, 挂起: 1, Teb: 000007ff`fffd7000, 未冻结

#### 调用站点
- 00 ntdll!NtWaitForMultipleObjects
- 01 KERNELBASE!WaitForMultipleObjectsEx
- 02 kernel32!WaitForMultipleObjectsEx
- 03 prncache!PrintCache::Store::CacheStore::RegistryMonitor::MonitorRegistryChanges
- 04 prncache!PrintCache::Store::CacheStore::RegistryMonitor::MonitorRegistryChangesThreadProc
- 05 kernel32!BaseThreadInitThunk
- 06 ntdll!RtlUserThreadStart

### 线程 4
Id: 1344.1edc, 挂起: 1, Teb: 000007ff`fffd5000, 未冻结

#### 调用站点
- 00 ntdll!NtWaitForSingleObject
- 01 ntdll!RtlpWaitOnCriticalSection
- 02 ntdll!RtlEnterCriticalSection
- 03 user32!BitmapFromDIB
- 04 user32!ConvertDIBBitmap
- 05 user32!ConvertDIBIcon
- 06 user32!CreateIconFromResourceEx
- 07 user32!PrivateEnumProc
- 08 kernel32!EnumResourceNamesInternal
- 09 kernel32!EnumResourceNamesExW
- 0a user32!PrivateExtractIconsW
- 0b shell32!SHPrivateExtractIcons
- 0c shell32!SHDefExtractIconW
- 0d shell32!CExtractIcon::ExtractW
- 0e shell32!CExtractIconBase::Extract
- 0f shell32!IExtractIcon_Extract
- 10 shell32!_GetIIndexGivenPXIcon
- 11 shell32!_GetIIndexFromItem
- 12 shell32!SHGetIconIndexFromPIDL
- 13 shell32!MapIDListToIconIndex
- 14 shell32!CLoadSystemIconTask::InternalResumeRT
- 15 shell32!CRunnableTask::Run
- 16 shell32!CShellTask::_TT_Run
- 17 shell32!CShellTaskThread::ThreadProc
- 18 shell32!CShellTaskThread::s_ThreadProc
- 19 shlwapi!ExecuteWorkItemThreadProc
- 1a ntdll!RtlpTpWorkCallback
- 1b ntdll!TppWorkerThread
- 1c kernel32!BaseThreadInitThunk
- 1d ntdll!RtlUserThreadStart

### 线程 5
Id: 1344.1b44, 挂起: 1, Teb: 000007ff`fffd3000, 未冻结

#### 调用站点
- 00 user32!NtUserGetIconInfo
- 01 user32!CopyIconCur
- 02 user32!InternalCopyImage
- 03 user32!CopyImage
- 04 comctl32!CImageList::_ReplaceIcon
- 05 comctl32!CImageList::ReplaceIcon
- 06 comctl32!CSparseImageList::ReplaceIcon
- 07 shell32!CIconCache::AddToBackIconTable
- 08 shell32!AddToBackIconTable
- 09 shell32!SHAddIconsToCache
- 0a shell32!_GetIIndexGivenPXIcon
- 0b shell32!_GetIIndexFromItem
- 0c shell32!SHGetIconIndexFromPIDL
- 0d shell32!MapIDListToIconIndex
- 0e shell32!CLoadSystemIconTask::InternalResumeRT
- 0f shell32!CRunnableTask::Run
- 10 shell32!CShellTask::_TT_Run
- 11 shell32!CShellTaskThread::ThreadProc
- 12 shell32!CShellTaskThread::s_ThreadProc
- 13 shlwapi!ExecuteWorkItemThreadProc
- 14 ntdll!RtlpTpWorkCallback
- 15 ntdll!TppWorkerThread
- 16 kernel32!BaseThreadInitThunk
- 17 ntdll!RtlUserThreadStart

### 线程 6
Id: 1344.1d9c, 挂起: 1, Teb: 000007ff`fffae000, 未冻结

#### 调用站点
- 00 gdi32!NtUserSelectPalette
- 01 gdi32!SelectPalette
- 02 gdi32!SetDIBits
- 03 user32!BitmapFromDIB
- 04 user32!ConvertDIBBitmap
- 05 user32!ConvertDIBIcon
- 06 user32!CreateIconFromResourceEx
- 07 user32!PrivateEnumProc
- 08 kernel32!EnumResourceNamesInternal
- 09 kernel32!EnumResourceNamesExW
- 0a user32!PrivateExtractIconsW
- 0b shell32!SHPrivateExtractIcons
- 0c shell32!SHDefExtractIconW
- 0d shell32!CExtractIcon::ExtractW
- 0e shell32!CExtractIconBase::Extract
- 0f shell32!IExtractIcon_Extract
- 10 shell32!_GetIIndexGivenPXIcon
- 11 shell32!_GetIIndexFromItem
- 12 shell32!SHGetIconIndexFromPIDL
- 13 shell32!MapIDListToIconIndex
- 14 shell32!CLoadSystemIconTask::InternalResumeRT
- 15 shell32!CRunnableTask::Run
- 16 shell32!CShellTask::_TT_Run
- 17 shell32!CShellTaskThread::ThreadProc
- 18 shell32!CShellTaskThread::s_ThreadProc
- 19 shlwapi!ExecuteWorkItemThreadProc
- 1a ntdll!RtlpTpWorkCallback
- 1b ntdll!TppWorkerThread
- 1c kernel32!BaseThreadInitThunk
- 1d ntdll!RtlUserThreadStart

### 线程 7
Id: 1344.139c, 挂起: 1, Teb: 000007ff`fffac000, 未冻结

#### 调用站点
- 00 ntdll!NtWaitForMultipleObjects
- 01 KERNELBASE!WaitForMultipleObjectsEx
- 02 kernel32!WaitForMultipleObjectsExImplementation
- 03 user32!RealMsgWaitForMultipleObjectsEx
- 04 user32!MsgWaitForMultipleObjectsEx
- 05 user32!MsgWaitForMultipleObjects
- 06 shell32!CShellTaskScheduler::TT_MsgWaitForMultipleObjects
- 07 shell32!CShellTaskScheduler::TT_TransitionThreadToRunningOrTerminating
- 08 shell32!CShellTaskThread::ThreadProc
- 09 shell32!CShellTaskThread::s_ThreadProc
- 0a shlwapi!ExecuteWorkItemThreadProc
- 0b ntdll!RtlpTpWorkCallback
- 0c ntdll!TppWorkerThread
- 0d kernel32!BaseThreadInitThunk
- 0e ntdll!RtlUserThreadStart

### 线程 8
Id: 1344.1b80, 挂起: 1, Teb: 000007ff`fffac000, 未冻结

#### 调用站点
- 00 ntdll!ZwDelayExecution
- 01 KERNELBASE!SleepEx
- 02 ole32!CROIDTable::WorkerThreadLoop
- 03 ole32!CRpcThread::WorkerLoop
- 04 ole32!CRpcThreadCache::RpcWorkerThreadEntry
- 05 kernel32!BaseThreadInitThunk
- 06 ntdll!RtlUserThreadStart

### 线程 9
Id: 1344.eb8, 挂起: 1, Teb: 000007ff`fffac000, 未冻结

#### 调用站点
- 00 ntdll!ZwAlpcSendWaitReceivePort
- 01 rpcrt4!LRPC_SCALL::SendReceive
