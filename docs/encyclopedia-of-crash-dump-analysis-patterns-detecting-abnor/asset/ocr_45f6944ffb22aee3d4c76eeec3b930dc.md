```
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

It is a path to a DLL that was probably missing:

```
0:000> du 0017f33c
0017f33c  "C:\\Program Files (x86)\\Common Fi"
0017f37c  "les\\Roxio Shared\\DLLShared\\KERNE"
0017f3bc  "L32.dll"
```

We think the loader was trying to find KERNEL32.dll following the DLL search order, and this was the last path element:

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
```