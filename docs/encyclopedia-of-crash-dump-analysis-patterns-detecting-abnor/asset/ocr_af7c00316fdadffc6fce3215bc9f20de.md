```
19000 [   2B0] address [size] of Import Address Table Directory
    0 [     0] address [size] of Delay Import Directory
    0 [     0] address [size] of COR20 Header Directory
    0 [     0] address [size] of Reserved Directory
...
...
...
0:000> dds 60000000+19000 60000000+19000+2B0
60019064 7c82b0dc ntdll!RtlReAllocateHeap
60019068 77e4ec39 kernel32!HeapDestroy
6001906c 77e41fba kernel32!GetSystemTimeAsFileTime
60019070 77e619d1 kernel32!GetTickCount
60019074 77e69577 kernel32!QueryPerformanceCounter
60019078 7c82a9be ntdll!RtlSizeHeap
6001907c 77e82060 kernel32!SetUnhandledExceptionFilter
60019080 77e7690d kernel32!UnhandledExceptionFilter
60019084 77e42004 kernel32!TerminateProcess
60019088 7c82a136 ntdll!RtlRestoreLastWin32Error
6001908c 77e77a5f kernel32!SuspendThread
60019090 77e76a26 kernel32!SetThreadContext
60019094 77e77ae3 kernel32!GetThreadContext
60019098 77e73347 kernel32!FlushInstructionCache
6001909c 77e5f38b kernel32!ResumeThread
600190a0 77e61648 kernel32!InterlockedCompareExchange
600190a4 77e645a9 kernel32!VirtualAlloc
600190a8 77e41fe3 kernel32!VirtualProtect
600190ac 77e66ed1 kernel32!VirtualQuery
600190b0 77e44960 kernel32!GetLogicalDriveStringsA
600190b4 77eab481 kernel32!GetVolumeNameForVolumeMountPointA
600190b8 77e6794d kernel32!GetACP
600190bc 77e6f3cf kernel32!GetLocaleInfoA
600190c0 77e622b7 kernel32!GetThreadLocale
600190c4 77e69d74 kernel32!GetVersionExA
600190c8 77e4beab kernel32!RaiseException
600190cc 77e60037 kernel32!GetSystemDirectoryA
600190d0 77e52b74 kernel32!GetWindowsDirectoryA
600190d4 77e5c7a8 kernel32!lstrcmpA
600190d8 77e46c99 kernel32!OutputDebugStringA
600190dc 77e5bd7d kernel32!CreateEventA
600190e0 77e62311 kernel32!SetEvent
600190e4 77e51281 kernel32!ExpandEnvironmentStringsA
600190e8 77e9f365 kernel32!MoveFileA
600190ec 77e5da00 kernel32!IsDebuggerPresent
600190f0 77e9e4b1 kernel32!QueryDosDeviceA
600190f4 7c829e08 ntdll!RtlGetLastWin32Error
600190f8 77e63d7a kernel32!GetProcAddress
600190fc 77e41dc6 kernel32!LoadLibraryA
60019100 7c829e17 ntdll!RtlFreeHeap
60019104 77e62419 kernel32!LocalFree
60019108 7c829fd6 ntdll!RtlAllocateHeap
6001910c 77e63ec7 kernel32!GetProcessHeap
60019110 77ea2186 kernel32!VerifyVersionInfoA
60019114 7c81379f ntdll!VerSetConditionMask
60019118 77e63143 kernel32!WideCharToMultiByte
6001911c 77e70550 kernel32!SizeofResource
```