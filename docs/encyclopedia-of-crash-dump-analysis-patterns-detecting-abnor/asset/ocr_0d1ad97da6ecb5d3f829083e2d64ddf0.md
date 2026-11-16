```
04 user32!ConvertDIBitmap
05 user32!ConvertDIBIcon
06 user32!CreateIconFromResourceEx
07 user32!PrivateEnumProc
08 kernel32!EnumResourceNamesInternal
09 kernel32!EnumResourceNamesExW
0a user32!PrivateExtractIconsW
0b shell32!SHPrivateExtractIcons
0c shell32!SHDefExtractIconW
0d shell32!CExtractIcon::ExtractW
0e shell32!CExtractIconBase::Extract
0f shell32!IExtractIcon_Extract
10 shell32!_GetIIIndexGivenPXIcon
11 shell32!_GetIIIndexFromItem
12 shell32!SHGetIconIndexFromPIDL
13 shell32!MapIDListToIconILIndex
14 shell32!CCloudSystemIconTask::InternalResumeRT
15 shell32!CRunnableTask::Run
16 shell32!CShellTask::TT_Run
17 shell32!CShellTaskThread::ThreadProc
18 shell32!CShellTaskThread::s_ThreadProc
19 shlwapi!ExecuteWorkItemThreadProc
1a ntdll!RtlpTpWorkCallback
1b ntdll!TppWorkerThread
1c kernel32!BaseThreadInitThunk
1d ntdll!RtlUserThreadStart
```

```
7 Id: 1344.139c Suspend: 1 Teb: 000007ff`fffac000 Unfrozen
# Call Site
00 ntdll!ZwMapViewOfSection
01 KERNELBASE!BasePloadLibraryAsDataFileInternal
02 KERNELBASE!LoadLibraryExW
03 user32!PrivateExtractIconsW
04 shell32!SHPrivateExtractIcons
05 shell32!SHDefExtractIconW
06 shell32!CExtractIcon::ExtractW
07 shell32!CExtractIconBase::Extract
08 shell32!IExtractIcon_Extract
09 shell32!_GetIIIndexGivenPXIcon
0a shell32!_GetIIIndexFromItem
0b shell32!SHGetIconIndexFromPIDL
0c shell32!MapIDListToIconILIndex
0d shell32!CCloudSystemIconTask::InternalResumeRT
0e shell32!CRunnableTask::Run
0f shell32!CShellTask::TT_Run
10 shell32!CShellTaskThread::ThreadProc
11 shell32!CShellTaskThread::s_ThreadProc
12 shlwapi!ExecuteWorkItemThreadProc
13 ntdll!RtlpTpWorkCallback
14 ntdll!TppWorkerThread
15 kernel32!BaseThreadInitThunk
16 ntdll!RtlUserThreadStart
```