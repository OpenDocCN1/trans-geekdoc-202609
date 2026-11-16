Therefore, the appearance of myhook!notify_me+0x22c could be a coincidence unless it was a pointer to a function. However, if it was the function pointer address then it wouldn't have pointed to the middle of the function call sequence that pushes arguments:

```
0:000> ub 10008e00
myhook!notify_me+0x211
10008de5 81c180000000 add ecx,80h
10008deb 899578ffffff mov dword ptr [ebp-88h],edx
10008df1 89458c mov dword ptr [ebp-74h],eax
10008df4 894d98 mov dword ptr [ebp-68h],ecx
10008df7 6a01 push 1
10008df9 8d45ec lea eax,[ebp-14h]
10008dfc 50 push eax
10008dfd ff75e0 push dword ptr [ebp-20h]
0:000> u 10008e00
myhook!notify_me+0x22c
10008e00 e82ff1ffff call myhook!copy_data (10007f34)
10008e05 8b578fffffff mov eax,dword ptr [ebp-88h]
10008e0b 3945ac cmp dword ptr [ebp-54h],eax
10008e0e 731f jae myhook!notify_me+0x25b (10008e2f)
10008e10 8b4598 mov eax,dword ptr [ebp-68h]
10008e13 0fbff00 movsx eax,word ptr [eax]
10008e16 8945a8 mov dword ptr [ebp-58h],eax
10008e19 8b45e0 mov eax,dword ptr [ebp-20h]
```

Also, because we have a source code and private symbols, we know that if it was a function pointer, then it would have been myhook!notify_me address and not notify_me+0x22c address.

All this evidence supports the hypothesis that myhook occurrence on the problem stack is just the coincidence and should be ignored.

To add, the most coincidental symbolic information we have found so far in one crash dump is an accidental correspondence between exported _DebuggerHookData and the location of the postmortem debugger NTSD:

```
002dd434 003a0043
002dd438 0057005c
002dd43c 004e0049 LegacyApp!_DebuggerHookData+0xc4a5
002dd440 004f0044 LegacyApp!_DebuggerHookData+0x1c4a0
002dd444 00530057
002dd448 0073005c
002dd44c 00730079
002dd450 00650074
002dd454 0033006d
002dd458 005c0032
002dd45c 0074006e
002dd460 00640073
002dd464 0065002e
002dd468 00650078
0:000> du 002dd434
002dd434 "C:\WINDOWS\system32\ntsd.exe"
```