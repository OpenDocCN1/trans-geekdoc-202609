# Idle main service thread and service dispatch threads:

```
. 0 Id: 65c.660 Suspend: 1 Teb: 000007ff`fffdc000 Unfrozen
Child-SP RetAddr Call Site
00000000`0011f2c8 00000000`76d926da ntdll!NtReadFile+0xa
00000000`0011f2d0 000007fe`fd6665aa kernel32!ReadFile+0x8a
00000000`0011f360 000007fe`fd6662e3 ADVAPI32!ScGetPipeInput+0x4a
00000000`0011f440 000007fe`fd65f0f3 ADVAPI32!ScDispatcherLoop+0x9a
00000000`0011f540 00000000`ff4234a3 ADVAPI32!StartServiceCtrlDispatcherW+0x176
00000000`0011f7e0 00000000`ff042e66 spoolsv!main+0x23
00000000`0011f850 00000000`76eec6e1 kernel32!BaseThreadInitThunk+0xd
00000000`0011f880 00000000`00000000 ntdll!RtlUserThreadStart+0x1d
```

```
1 Id: 65c.664 Suspend: 1 Teb: 000007ff`fffda000 Unfrozen
Child-SP RetAddr Call Site
00000000`009f9c88 00000000`76d9d820 ntdll!NtWaitForSingleObject+0xa
00000000`009f9d00 00000000`ff4307f kernel32!WaitForSingleObjectEx+0x9c
00000000`009f9fa0 000007fe`fd64bf5 spoolsv!SPOOLER_main+0x80
00000000`009fac0 00000000`76d9ccd ADVAPI32!ScSvcctrlThreadW+0x25
00000000`009fafa0 00000000`76eec6e1 kernel32!BaseThreadInitThunk+0xd
00000000`009ffb20 00000000`00000000 ntdll!RtlUserThreadStart+0x1d
```

# Idle window message loops:

```
10 Id: 65c.514 Suspend: 1 Teb: 000007ff`fffa2000 Unfrozen
Child-SP RetAddr Call Site
00000000`02c5fc18 00000000`76cae6ea USER32!ZwUserGetMessage+0xa
00000000`02c5fc20 000007fe`f88523f0 USER32!GetMessageW+0x34
00000000`02c5fc50 00000000`76d9cdcd usermon!CPNPNotifications::WindowMessageThread+0x1a0
00000000`02c5fd20 00000000`76eec6e1 kernel32!BaseThreadInitThunk+0xd
00000000`02c5fd50 00000000`00000000 ntdll!RtlUserThreadStart+0x1d
```

```
11 Id: 65c.9bc Suspend: 1 Teb: 000007ff`fffa0000 Unfrozen
Child-SP RetAddr Call Site
00000000`037cf798 00000000`76cae6ea USER32!ZwUserGetMessage+0xa
00000000`037cf7a0 000007fe`f7ea0d3a USER32!GetMessageW+0x34
00000000`037cf7d0 00000000`76d9dcdd WSDMon!Ncd::TPower::WindowMessageThread+0xe6
00000000`037cf870 00000000`76eec6e1 kernel32!BaseThreadInitThunk+0xd
00000000`037cf8a0 00000000`00000000 ntdll!RtlUserThreadStart+0x1d
```

```
13 Id: ecc.b34 Suspend: 1 Teb: 7ef85000 Unfrozen
ChildEBP RetAddr
0621fc18 75b8b458 USER32!NtUserGetMessage+0x15
0621fc3c 74aa1404 USER32!GetMessageA+0xa2
0621fc74 76ea19f1 WINMM!mcicwindow+0x102
0621fc80 7797d109 kernel32!BaseThreadInitThunk+0xe
0621fcc0 00000000 ntdll!_RtlUserThreadStart+0x23
```