We see that it was an access violation exception and check the thread with TID cfc:

```
0:000> kL
ChildEBP RetAddr
0012bd54 77d70dde ntdll!KiFastSystemCallRet
0012bd58 7b1d8e48 user32!NtUserWaitMessage+0xc
0012dbec 7b1d8937 System_Windows_Forms_ni+0x208e48
0012dc44 7b1d8781 System_Windows_Forms_ni+0x208937
0012dc74 7b6edd1f System_Windows_Forms_ni+0x208781
0012dc8c 7b72246b System_Windows_Forms_ni+0x71dd1f
0012dd18 7b722683 System_Windows_Forms_ni+0x75246b
0012dd58 7b6ff776 System_Windows_Forms_ni+0x752683
0012dd64 7b6fa27c System_Windows_Forms_ni+0x7277f6
0012f148 77d6fd82 System_Windows_Forms_ni+0x72a27c
0012f174 77d6f794 user32!InternalCallWinProc+0x23
0012flec 77d70008 user32!UserCallWinProcCheckWow+0x14b
0012f250 77d70060 user32!DispatchMessageWorker+0x322
0012f260 0a1412fa user32!DispatchMessageW+0xf
WARNING: Frame IP not in any known module. Following frames may be wrong.
0012f27c 578439f7 0xa1412fa
0012f2ec 578430c9 WindowsBase_ni+0x939f7
0012f2f8 5784306c WindowsBase_ni+0x930c9
0012f304 55bed46e WindowsBase_ni+0x9306c
0012f310 55bec76f PresentationFramework_ni+0x1cd46e
0012f334 55bd3aa6 PresentationFramework_ni+0x1cc76f
```

If there was an exception it must be Hidden Exception (page 457) so we inspect the thread raw stack:

```
0:000> !teb
TEB at 7ffdf000
    ExceptionList:        0012e470
    StackBase:            00130000
    StackLimit:           0011e000
    SubSystemTib:         00000000
    FiberData:            00001e00
    ArbitraryUserPointer: 00000000
    Self:                 7ffdf000
    EnvironmentPointer:   00000000
    ClientId:             00000b6c . 00000cfc
    RpcHandle:            00000000
    Tls Storage:          7ffdf02c
    PEB Address:          7ffd4000
    LastErrorValue:       0
    LastStatusValue:      c0000139
    Count Owned Locks:    0
    HardErrorMode:        0

0:000> dps 0011e000 00130000
0011e000  00000000
0011e004  00000000
0011e008  00000000
[...]
0012e72c  00130000
0012e730  0011e000
0012e734  00ee350d
```