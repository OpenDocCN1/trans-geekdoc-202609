```
0:000> dd 01115018 L4
01115018 011150fc 0012ffb4 0011512c 001150d0
```

So we use the valid context pointer now:

```
0:000> .cxr 0011512c
eax=001153fc ebx=0eedfade ecx=00000000 edx=001537a8 esi=001154a4 edi=00000007
eip=7c7e2afb esp=001153f8 ebp=0011544c iopl=0         nv up ei pl nz na po nc
cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=00200202
kernel32!RaiseException+0x53:
7c7e2afb 5e              pop     esi
0:000> kv
*** Stack trace for last set context - .thread/.cxr resets it
ChildEBP RetAddr  Args to Child
0011544c 0057ac37 0eedfade 00000001 00000007 kernel32!RaiseException+0x53
WARNING: Stack unwind information not available. Following frames may be wrong.
00115470 0098fa49 0eedfade 00000001 00000007 Application+0x17ac37
[...]
0012268c 7e398816 017d0f87 000607e8 0000001a USER32!InternalCallWinProc+0x28
001226f4 7e3a8ea0 00000000 017d0f87 000607e8 USER32!UserCallWinProcCheckWow+0x150
00122748 7e3aacd1 00fd2ad0 0000001a 00000000 USER32!DispatchClientMessage+0xa3
00122778 7c90e473 00122788 00000030 00000030 USER32!__fnINSTRING+0x37
001227b4 7e3993e9 7e3993a8 00122840 00000000 ntdll!KiUserCallbackDispatcher+0x13
001227e0 7e3aa43b 00122840 00000000 00000000 USER32!NtUserPeekMessage+0xc
0012280c 004794d9 00122840 00000000 00000000 USER32!PeekMessageA+0xeb
001228bc 00461667 0012ff7c 00461680 001228e0 Application+0x794d9
[...]
```