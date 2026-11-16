

```
0017f9a0  77b8dab8 ntdll!RtlpRunTable+0x218
0017f9a4  ffffffff
0017f9a8  77ba2515 ntdll!vDbgPrintExWithPrefixInternal+0x214
0017f9ac  77ba253b ntdll!DbgPrintEx+0x1e
0017f9b0  77b7f356 ntdll! ?? ::FNODOBFM::`string'
0017f9b4  00000055
0017f9b8  00000003
0017f9bc  77b809c2 ntdll! ?? ::FNODOBFM::`string'
0017f9c0  0017fc9c
0017f9c4  00000001
0017f9c8  0017fd00
0017f9cc  77bcf28e ntdll!_LdrpInitialize+0x12a
0017f9d0  00000055
0017f9d4  75ce3cf9
0017f9d8  0001003f
0017f9dc  00000000
0017f9e0  00000000
0017f9e4  00000000
0017f9e8  00000000
0017f9ec  00000000
...
```

我们在上面看到突出显示的异常分派调用（隐藏异常，第 457 页）。它们的一个参数是异常记录，我们尝试获取一个：

```
0:000> .exr 0017f988
ExceptionAddress: 77bcf1d1 (ntdll!_LdrpInitialize+0x0000006d)
  ExceptionCode: c0000135
ExceptionFlags: 00000001
NumberParameters: 0
```

错误 c0000135 表示加载程序无法定位某个组件。现在我们尝试检查相同的原始堆栈数据，查找任何字符串模式。例如，以下 UNICODE 模式清晰可见：

```
0017f2fc  00000000
0017f300  00088ec4
0017f304  77b910d7 ntdll!RtlpDosPathNameToRelativeNtPathName_Ustr+0x344
0017f308  00000000
0017f30c  43000043
0017f310  0042002a
0017f314  0017f33c
0017f318  00000000
0017f31c  00000002
0017f320  00000008
0017f324  00000000
0017f328  0000008c
0017f32c  000a0008
0017f330  77b91670 ntdll!`string'
0017f334  0b9b2bd6
0017f338  0017f5d4
0017f33c  003a0043
0017f340  0050005c
0017f344  006f0072
0017f348  00720067
0017f34c  006d0061
0017f350 00460020
0017f354 006c0069
0017f358 00730065
0017f35c 00280020
0017f360 00380078
0017f364 00290036
0017f368 00430005
0017f36c 006d006f
0017f370 00660064
0017f374 0020006e
0017f378 00690046
0017f37c 0055006e
0017f380 006c0003
0017f384 00f60052
0017f388 00690078
0017f38c 0020006f
0017f390 00680053
0017f394 00720061
0017f398 00640065
0017f39c 00440005
0017f3a0 0043004f
0017f3a4 00680053
0017f3a8 00720061
0017f3ac 00640065
0017f3b0 00420005
0017f3b4 00520045
0017f3b8 0045004c
0017f3bc 0033004c
0017f3c0 002e0032
0017f3c4 006c0064
0017f3c8 00000000
0017f3cc 00000000
```

这是指向一个可能丢失的 DLL 的路径：

```
0:000> du 0017f33c
0017f33c  "C:\\Program Files (x86)\\Common Fi"
0017f37c  "les\\Roxio Shared\\DLLShared\\KERNE"
0017f3bc  "L32.dll"
```

我们认为加载程序正在按照 DLL 搜索顺序查找 KERNEL32.dll，而这正是最后一个路径元素：

```
0:000> !peb
PEB at 7fde000
    InheritedAddressSpace:    No
    ReadImageFileExecOptions:  No
    BeingDebugged:            Yes
    ImageBaseAddress:         00400000
    Ldr                       77c40080
    Ldr.Initialized:          Yes
    Ldr.InInitializationOrderModuleList: 00881ad0 . 008831b8
    Ldr.InLoadOrderModuleList:           00881a50 . 00883dc8
    Ldr.InMemoryOrderModuleList:         00881a58 . 00883dd0
                     Base TimeStamp                     Module
... Environment: 00881de8
...
Path=C:\Windows\system32; C:\Windows; C:\Windows\System32\Wbem; C:\Program Files\ATI Technologies\ATI.ACE; c:\Program Files (x86)\Microsoft SQL Server\90\Tools\binn\; C:\Program Files (x86)\Common Files\Roxio Shared\DLLShared\
```

在类似情况下，**!dlls** 命令可能会有所帮助。它显示加载顺序（-l 开关）并指向最后处理的 DLL：

```
0:001> !dlls -l
0x004740e8: C:\Program Files\Application\Application.exe
	Base	0x012a0000	EntryPoint	0x012b0903	Size	0x00057000
	Flags	0x00004010	LoadCount	0x0000ffff	TlsIndex	0x00000000
		LDRP_ENTRY_PROCESSED

0x00474158: C:\Windows\SysWOW64\ntdll.dll
	Base	0x77d00000	EntryPoint	0x00000000	Size	0x00160000
	Flags	0x00004014	LoadCount	0x0000ffff	TlsIndex	0x00000000
		LDRP_IMAGE_DLL
		LDRP_ENTRY_PROCESSED

0x00474440: C:\Windows\syswow64\kernel32.dll
	Base	0x77590000	EntryPoint	0x775a1f3e	Size	0x00110000
	Flags	0x00008401	LoadCount	0x0000ffff	TlsIndex	0x00000000
		LDRP_IMAGE_DLL
		LDRP_ENTRY_PROCESSED
		LDRP_PROCESS_ATTACH_CALLED

...

0x00498ff8: C:\Windows\WinSxS\x86_microsoft.windows.common-controls_...\comctl32.dll
	Base	0x74d90000	EntryPoint	0x74dc43e5	Size	0x0019e000
	Flags	0x100c4014	LoadCount	0x00000003	TlsIndex	0x00000000
		LDRP_IMAGE_DLL
		LDRP_ENTRY_PROCESSED
		LDRP_DONT_CALL_FOR_THREADS
		LDRP_PROCESS_ATTACH_CALLED

0x004991b8: C:\Windows\WinSxS\x86_microsoft.windows.vc80.mfcloc_...\MFC80ENU.DLL
	Base	0x71b10000	EntryPoint	0x00000000	Size	0x0000e000
	Flags	0x10004014	LoadCount	0x00000001	TlsIndex	0x00000000
		LDRP_IMAGE_DLL
		LDRP_ENTRY_PROCESSED
```

如果在崩溃转储中难以确定实际发生了什么，可以使用 gflags 启用加载程序跟踪并在调试器下运行应用程序。例如，对于 notepad.exe 我们有：

![](img/d6dfefc8f9ab7106c77a723ff84aaa6d_678_0.png)

```
Microsoft (R) Windows Debugger Version 6.8.0004.0 AMD64
Copyright (c) Microsoft Corporation. All rights reserved.

CommandLine: C:\Windows\notepad.exe
Symbol search path is: srv*c:\mss*http://msdl.microsoft.com/download/symbols
Executable search path is:
ModLoad: 00000000`ffac0000 00000000`ffaef000   notepad.exe
ModLoad: 00000000`779b0000 00000000`77b2a000   ntdll.dll
LDR: NEW PROCESS
  Image Path: C:\Windows\notepad.exe (notepad.exe)
  Current Directory: C:\Program Files\Debugging Tools for Windows 64-bit\
  Search Path: C:\Windows; C:\Windows\system32; C:\Windows\system; C:\Windows;.; C:\Program Files\Debugging Tools for Windows 64-bit\winext\arcade; C:\Windows\system32;C:\Windows;
C:\Windows\System32\Wbem; C:\Program Files\ATI Technologies\ATI.ACE; c:\Program Files (x86)\Microsoft SQL Server\90\Tools\binn\; C:\Program Files (x86)\Common Files\Roxio Shared\DLLShared\
LDR: LdrLoadDll, loading kernel32.dll from
ModLoad: 00000000`777a0000 00000000`778d1000   C:\Windows\system32\kernel32.dll
LDR: kernel32.dll bound to ntdll.dll
LDR: kernel32.dll has stale binding to ntdll.dll
LDR: Stale Bind ntdll.dll from kernel32.dll

LDR: LdrGetProcedureAddress by NAME - BaseThreadInitThunk
[3d8,1278] LDR: Real INIT LIST for process C:\Windows\notepad.exe pid 984 0x3d8
[3d8,1278] C:\Windows\system32\kernel32.dll init routine 00000000777DC960
[3d8,1278] LDR: kernel32.dll loaded - Calling init routine at 00000000777DC960
LDR: notepad.exe bound to ADVAPI32.dll
ModLoad: 000007fe`fe520000 000007fe`fe61f000   C:\Windows\system32\ADVAPI32.dll
LDR: ADVAPI32.dll bound to ntdll.dll
LDR: ADVAPI32.dll has stale binding to ntdll.dll
LDR: Stale Bind ntdll.dll from ADVAPI32.dll
LDR: ADVAPI32.dll bound to KERNEL32.dll
LDR: ADVAPI32.dll has stale binding to KERNEL32.dll
LDR: ADVAPI32.dll bound to ntdll.dll via forwarder(s) from kernel32.dll
LDR: ADVAPI32.dll has stale binding to ntdll.dll
LDR: Stale Bind KERNEL32.dll from ADVAPI32.dll
LDR: LdrGetProcedureAddress by NAME - RtlAllocateHeap
LDR: LdrGetProcedureAddress by NAME - RtlReAllocateHeap
LDR: LdrGetProcedureAddress by NAME - RtlEncodePointer
LDR: LdrGetProcedureAddress by NAME - RtlDecodePointer
LDR: LdrGetProcedureAddress by NAME - RtlSizeHeap
LDR: LdrGetProcedureAddress by NAME - RtlDeleteCriticalSection
LDR: LdrGetProcedureAddress by NAME - RtlEnterCriticalSection
LDR: LdrGetProcedureAddress by NAME - RtlInitializeCriticalSection
LDR: LdrGetProcedureAddress by NAME - RtlLeaveCriticalSection
LDR: ADVAPI32.dll bound to RPCRT4.dll
...
```

此技术仅适用于本机平台加载程序跟踪。例如，它不会显示在 WOW64 下加载的 32 位模块的加载程序跟踪：

```
Microsoft (R) Windows Debugger Version 6.8.0004.0 X86
Copyright (c) Microsoft Corporation. All rights reserved.

CommandLine: C:\Apps\StackOverflow.exe
Symbol search path is: srv*c:\mss*http://msdl.microsoft.com/download/symbols
Executable search path is:
ModLoad: 00400000 00418000   StackOverflow.exe
ModLoad: 77b60000 77cb0000   ntdll.dll
LDR: NEW PROCESS
    Image Path: C:\Apps\StackOverflow.exe (StackOverflow.exe)
...
LDR: Loading (STATIC, NON_REDIRECTED) C:\Windows\system32\wow64cpu.dll
LDR: wow64cpu.dll bound to ntdll.dll
LDR: wow64cpu.dll has stale binding to ntdll.dll
LDR: Stale Bind ntdll.dll from wow64cpu.dll
LDR: wow64cpu.dll bound to wow64.dll
LDR: wow64cpu.dll has stale binding to wow64.dll
LDR: Stale Bind wow64.dll from wow64cpu.dll
LDR: wow64.dll has stale binding to wow64cpu.dll
LDR: Stale Bind wow64cpu.dll from wow64.dll
LDR: Refcount wow64cpu.dll (1)
LDR: Refcount wow64.dll (2)
LDR: Refcount wow64win.dll (1)
LDR: Refcount wow64.dll (3)
LDR: LdrGetProcedureAddress by NAME - Wow64LdrpInitialize
...
ModLoad: 77630000 77740000   C:\Windows\syswow64\kernel32.dll
ModLoad: 76030000 76100000   C:\Windows\syswow64\USER32.dll
```

