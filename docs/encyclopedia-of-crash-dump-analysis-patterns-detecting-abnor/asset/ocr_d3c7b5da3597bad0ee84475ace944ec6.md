# Dialog Box

Similar to **Message Box** (page 660) and **String Parameter** (page 962) patterns we also have **Dialog Box** pattern where we can see dialog window caption and contents when we examine function parameters. Although in the examples below we know the dialog purpose from the friendly call stack function names, for many 3rd-party applications we either don’t have symbols or such helper functions, but we want to know what was on the screen when screenshots were not collected.

The first two examples are from *Notepad* application, and the third is from IE:

```
0:000> kv
ChildEBP RetAddr  Args to Child
0017f5c4 777b073f 777c3c9f 000d023c 00000001 ntdll!KiFastSystemCallRet
0017f5c8 777c3c9f 000d023c 00000001 00000000 user32!NtUserWaitMessage+0xc
0017f5fc 777c2dc0 00310778 000023c 00000001 user32!DialogBox+0x202
0017f624 777c2cee 76460000 02a6bc60 000d023c user32!InternalDialogBox+0xd0
0017f644 76489a65 76460000 02a6bc60 000d023c user32!DialogBoxIndirectParamAorW+0x37
0017f680 76489ccf 0017f68c 00000001 0017f644 comdlg32!ChooseFont+0x1ba
0017f6bc 06741c7 0017f6d4 00000111 00000000 comdlg32!ChooseFont+0x2e
0017f734 0067164a 000d023c 00000021 00000000 notepad!NPCommand+0x4c7
0017f758 777afd72 000d023c 00000111 00000021 notepad!NPWndProc+0x4cf
0017f784 777a4ea 0067146c 000d023c 00000111 user32!InternalCallWinProc+0x23
0017f7fc 777b018d 00000000 067146c 000d023c user32!UserCallWinProcCheckWow+0x14b
0017f860 777b022b 067146c 00000000 0017f8a4 user32!DispatchMessageWorker+0x322
0017f870 0671465 0017f888 00000000 067a21c user32!DispatchMessage+0xf
0017f8a4 067195d 0677000 00000000 00231cfa notepad!WinMain+0xe3
0017f934 76520de9 7dfd9000 0017f980 77b019bf notepad!_initterm+0x1a1
0017f940 77b019bf 7ffd9000 78fb7908 00000000 kernel32!BaseThreadInitThunk+0xe
0017f980 77b0198e 006731ed 7ffd9000 00000000 ntdll!_RtlUserThreadStart+0x23
0017f998 00000000 006731ed 7ffd9000 00000000 ntdll!_RtlUserThreadStart+0x1b
```

```
0:000> dc 02a6bc60 150
02a6bc60 8c880c4 00000000 000d0014 011f0036 ...........6...
02a6bc70 00000c4 00460000 006e006f 00000074 .....F.o.n.t...
02a6bc80 004d0008 00200053 00680053 006c0065 ..M.S. .S.h.e.l.
02a6bc90 0020006c 006c0044 00000067 50020000 l. .D.l.g....P
02a6bca0 00000000 00700007 0090028 ffffa440 .......(@...
02a6bcb0 00260082 00670046 0074006e 0000003a ...&.F.n.t...
02a6bcc0 00000000 50210b51 00000000 00100007 ....Q!P.......
02a6bcd0 004c0062 ffff0470 00000085 00000000 b.L.p.......
02a6bce0 50020000 00000000 0070006e 0090002c .P....n.,...
02a6bcf0 fff0441 00460082 006e006f 00200074 A...F.o.n.t.
02a6bd00 00740073 00790062 006e0069 0030003a s.t.&y.l.e.i...
02a6bd10 00000000 50210041 00000000 001000e ...A!P...n...
02a6bd20 004c0044 ffff0471 00000085 00000000 J.L.q.......
02a6bd30 50020000 00000000 007000bd 0009001e ...P.......
02a6bd40 ffff0442 00260082 00690053 0055007a B...&S.i.z.e.
02a6bd50 0000000a 00000000 50210b51 00000000 .....Q!P....
02a6bd60 001000be 004c0024 fff0472 00000085 ...$.L.r...
02a6bd70 00000000 50020007 00000000 00610007 ....P....a.
02a6bd80 00480062 fff0430 00450080 00660066 b.H.0....E.f.f.
02a6bd90 00630065 00730074 00000000 50010003 e.c.t.s......P
```