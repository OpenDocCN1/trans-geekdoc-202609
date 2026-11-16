# Idle socket and network protocol threads:

```
5 Id: ecc.920 Suspend: 1 Teb: 7efa3000 Unfrozen
ChildEBP RetAddr
0412f534 751b3b28 ntdll!ZwWaitForSingleObject+0x15
0412f574 751b2690 mswsock!SockWaitForSingleObject+0x19f
0412f660 771d3781 mswsock!WSPSelect+0x38c
0412f6d0 760f6fd0 ws2_32!select+0x456
0412fa34 760f2a78 WININET!ICASyncThread::SelectThread+0x242
0412fa3c 76ea19f1 WININET!ICASyncThread::SelectThreadWrapper+0xd
0412fa48 7797d109 kernel32!BaseThreadInitThunk+0xe
0412fa88 00000000 ntdll!_RtlUserThreadStart+0x23

6 Id: ecc.b1c Suspend: 1 Teb: 7ef9d000 Unfrozen
ChildEBP RetAddr
047afa6c 751b1b25 ntdll!NtRemoveIoCompletion+0x15
047afa44 76ea19f1 mswsock!SockAsyncThread+0x69
047afab0 7797d109 kernel32!BaseThreadInitThunk+0xe
047afaf0 00000000 ntdll!_RtlUserThreadStart+0x23

7 Id: 820.f90 Suspend: 1 Teb: 7ffd9000 Unfrozen
ChildEBP RetAddr
018dff84 7c93e9ab ntdll!KiFastSystemCallRet
018dff88 60620e6c ntdll!ZwWaitForMultipleObjects+0xc
018dffb4 7c80b683 NETAPI32!NetbiosWaiter+0x73
018dffec 00000000 kernel32!BaseThreadStart+0x37
```

# Function names showing passive nature of threads:

```
8 Id: 65c.b40 Suspend: 1 Teb: 000007ff`fffa6000 Unfrozen
Child-SP RetAddr Call Site
00000000`0259fdc0 00000000`76d9d820 ntdll!NtWaitForSingleObject+0xa
00000000`0259fdd0 0000007e`f8258084 kernel32!WaitForSingleObjectEx+0x9c
00000000`0259fe90 0000007e`fee994e7 wsnmp32!**thrNotify**+0x9c
00000000`0259fef0 0000007e`fee9967d msvcrt!endthreadex+0x47
00000000`0259ff20 00000000`76d9ccd msvcrt!endthreadex+0x100
00000000`0259ff50 00000000`76eec6e1 kernel32!BaseThreadInitThunk+0xd
00000000`0259ff80 00000000`00000000 ntdll!RtlUserThreadStart+0x1d

12 Id: 65c.908 Suspend: 1 Teb: 000007ff`fff9e000 Unfrozen
Child-SP RetAddr Call Site
00000000`0368fd48 00000000`76d9d820 ntdll!NtWaitForSingleObject+0xa
00000000`0368fd50 0000007e`fa49afd0 kernel32!WaitForSingleObjectEx+0x9c
00000000`0368fe10 00000000`76d9cdcd FuncDisc!**CNotificationQueue**::ThreadProc+0x2ec
00000000`0368fe70 00000000`76eec6e1 kernel32!BaseThreadInitThunk+0xd
00000000`0368fea0 00000000`00000000 ntdll!RtlUserThreadStart+0x1d
```