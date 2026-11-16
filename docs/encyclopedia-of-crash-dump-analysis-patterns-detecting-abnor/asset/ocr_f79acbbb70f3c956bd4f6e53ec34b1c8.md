```
```c
CloseHandle(hThread);
                return (INT_PTR)TRUE;
            }
            break;
        }
        return (INT_PTR)FALSE;
}
```
```

When we open the crash dump we see these threads:

```
```
0:002> ~*kL

  0  Id: cb0.9ac Suspend: 1 Teb: 7efdd000 Unfrozen
ChildEBP RetAddr
0012fdf4 00411554 user32!NtUserGetMessage+0x15
0012fdf8 00412329 NullThread!WinMain+0x44
0012fff8 0041208d NullThread!_tmainCRTStartup+0x289
0012fff0 7d4e7d2a NullThread!WinMainCRTStartup+0xd
0012fff0 00000000 kernel32!BaseProcessStart+0x28

  1  Id: cb0.8b4 Suspend: 1 Teb: 7efda000 Unfrozen
ChildEBP RetAddr
01eafec4 7d63f501 ntdll!NtWaitForMultipleObjects+0x15
01eaff48 7d63f988 ntdll!EtwWaitForMultipleObjectsEx+0xf7
01eaff88 7d4dfe21 ntdll!EtwEventPump+0x27f
01eaffec 00000000 kernel32!BaseThreadStart+0x34

  2  Id: cb0.ca8 Suspend: 1 Teb: 7efd7000 Unfrozen
ChildEBP RetAddr
0222fff8 7d4dfe21 NullThread!ThreadProc+0x34
0222ffec 00000000 kernel32!BaseThreadStart+0x34

#  3  Id: cb0.5bc Suspend: 1 Teb: 7efaf000 Unfrozen
ChildEBP RetAddr
WARNING: Frame IP not in any known module. Following frames may be wrong.
0236fff8 7d4dfe21 0x0
0236ffec 00000000 kernel32!BaseThreadStart+0x34

  4  Id: cb0.468 Suspend: -1 Teb: 7efac000 Unfrozen
ChildEBP RetAddr
01f7fff4 7d674807 ntdll!NtTerminateThread+0x12
01f7ffc4 7d65509f ntdll!RtlExitUserThread+0x26
01f7fff4 00000000 ntdll!DbgUiRemoteBreakin+0x41
```
```

We see our first created thread looping:

```
```
0:003> ~2s
eax=cbfc04b5 ebx=00000000 ecx=00000000 edx=00000000 esi=00000000 edi=0222ffb8
eip=00411aa4 esp=0222fee0 ebp=0222ffb8 iopl=0 nv up ei ng nz na po nc
cs=0023 ss=002b ds=002b es=002b fs=0053 gs=002b efl=00000282
NullThread!ThreadProc+0x34:
00411aa4 7402          je      NullThread!ThreadProc+0x38 (00411aa8)  [br=0]
```
```