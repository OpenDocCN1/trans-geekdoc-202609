Gluing them together, we get this approx. stack trace:

```
97543b6c 85adf579 nt!KiTrap0E+0x2ac
WARNING: Stack unwind information not available. Following frames may be wrong.
97543be8 85adf770 myfault+0x579
97543bf4 85adf7fc myfault+0x770
97543c2c 81827ecf myfault+0x7fc
97543c44 81988f65 nt!IopCallDriver+0x63
97543c64 81989F25 nt!IoSynchoronousServiceTail+0x1e0
97543d00 8198ee8d nt!IopXxxControlFile+0x6b7
97543d34 8188c96a nt!NtDeviceIoControlFile+0x2a
97543d34 77510f34 ntl!KiFastCallEntry+0x12a
0012f9a0 7750f850 ntdll!KiFastSystemCallRet
0012f9a4 77417c92 ntdll!NtDeviceIoControlFile+0xc
0012fa04 00401a5b kernel32!DeviceIoControl+0x14a
0012fa94 7700becf NotMyFault+0x1a5b
0012fc0c 7700286a USER32!UserCallWinProcCheckWow+0x14b
0012fc4c 77002bba USER32!SendMessageWorker+0x4b7
0012fc6c 7700c6ba USER32!SendMessageW+0x7c
0012fc84 7700c7c9 USER32!xxxButtonNotifyParent+0x41
0012fca0 7700c7e8 USER32!xxxBNReleaseCapture+0xf7
0012fd24 7701632e USER32!ButtonWndProcWorker+0x910
0012fd44 77001a10 USER32!ButtonWndProcA+0x4c
0012fd70 77001ae8 USER32!InternalCallWinProc+0x23
0012fde8 77002a47 USER32!UserCallWinProcCheckWow+0x14b
0012fe4c 77002a98 USER32!DispatchMessageWorker+0x322
0012fe5c 7ff11fc USER32!DispatchMessageW+0xf
0012fe80 76fe98d2 USER32!IsDialogMessageW+0x586
0012fea0 00401cc9 USER32!IsDialogMessageA+0xff
0012ff10 004022ec NotMyFault+0x1cc9
0012ffac 774ea9bd kernel32!BaseThreadInitThunk+0xe
0012ffec 00000000 ntdll!_RtlUserThreadStart+0x23
```