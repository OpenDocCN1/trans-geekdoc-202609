
```
0:005> !address 00040000
Usage:                   <unclassified>
Allocation Base:         00040000
Base Address:            00040000
End Address:             0005d000
Region Size:             0001d000
Type:                    00020000 MEM_PRIVATE
State:                   00001000 MEM_COMMIT
Protect:                 00000040 PAGE_EXECUTE_READWRITE
```

```
0:005> !address 10000000
Usage:                   <unclassified>
Allocation Base:         10000000
Base Address:            10000000
End Address:             10001000
Region Size:             00001000
Type:                    00020000 MEM_PRIVATE
State:                   00001000 MEM_COMMIT
Protect:                 00000004 PAGE_READWRITE
```

- suspicious text inside
- suspicious import table (for example, screen grabbing) or its absence (dynamic imports)

```
0:005> !dh 10000000
[...]
2330 [  50] address [size] of Export Directory
20E0 [  78] address [size] of Import Directory
0   [   0] address [size] of Resource Directory
0   [   0] address [size] of Exception Directory
0   [   0] address [size] of Security Directory
4000 [  34] address [size] of Base Relocation Directory
2060 [  1C] address [size] of Debug Directory
0   [   0] address [size] of Description Directory
0   [   0] address [size] of Special Directory
0   [   0] address [size] of Thread Storage Directory
0   [   0] address [size] of Load Configuration Directory
0   [   0] address [size] of Bound Import Directory
2000 [  58] address [size] of Import Address Table Directory
0   [   0] address [size] of Delay Import Directory
0   [   0] address [size] of COR20 Header Directory
0   [   0] address [size] of Reserved Directory
[...]
```

```
0:005> dps 10000000+2000 10000000+2000+58
10002000 76376101 gdi32!CreateCompatibleDC
10002004 763793d6 gdi32!StretchBlt
10002008 76377461 gdi32!CreateDIBSection
1000200c 763762a0 gdi32!SelectObject
10002010 00000000
10002014 754e4a11 kernel32!lstrcmpW
10002018 75e440aa kernel32!VirtualFree
1000201c 75e4ad55 kernel32!VirtualAlloc
10002020 00000000
10002024 77429ced user32!ReleaseDC
10002028 77423ba7 user32!NtUserGetWindowDC
1000202c 77430e21 user32!GetWindowRect
10002030 00000000
10002034 744a75e9 GdiPlus!GdiplusStartup
10002038 744976dd GdiPlus!GdipSaveImageToStream
1000203c 0744cd38 GdiPlus!GdipGetImageEncodersSize
10002040 744971cf GdiPlus!GdipDisposeImage
10002044 744a8591 GdiPlus!GdipCreateBitmapFromHBITMAP
10002048 744cdbae GdiPlus!GdipGetImageEncoders
1000204c 00000000
10002050 7707d51b ole32!CreateStreamOnHGlobal
10002054 00000000
10002058 00000000
```

```
0:000> !dh 012a0000
[...]
0   [   0] address [size] of Export Directory
0   [   0] address [size] of Import Directory
0   [   0] address [size] of Resource Directory
0   [   0] address [size] of Exception Directory
0   [   0] address [size] of Security Directory
8000 [ FC] address [size] of Base Relocation Directory
4000 [ 1C] address [size] of Debug Directory
0   [   0] address [size] of Description Directory
0   [   0] address [size] of Special Directory
0   [   0] address [size] of Thread Storage Directory
0   [   0] address [size] of Load Configuration Directory
0   [   0] address [size] of Bound Import Directory
0   [   0] address [size] of Import Address Table Directory
0   [   0] address [size] of Delay Import Directory
0   [   0] address [size] of COR20 Header Directory
0   [   0] address [size] of Reserved Directory
[...]
```

- suspicious path names

Age: 7, Pdb: d:\work\BekKonnekt\Client_src_code_New\Release\Blackjoe_new.pdb

Debug Directories(1)

| Type | Size | Address | Pointer |
|------|------|---------|---------|
| cv | 46 | 2094 | 894 |

Format: RSDS, guid, 1, C:\MyWork\screens_dll\Release\screens_dll.pdb

- suspicious image path (although could be just dynamic code generation for .NET assemblies)

- uninitialized image resources

```
0:002> lmv m C6DC
start    end        module name
012a0000 012a9000   C6DC    C (no symbols)
    Loaded symbol image file: C6DC.tmp
    Image path: C:\Users\User\AppData\Local\Temp\C6DC.tmp
    Image name: C6DC.tmp
    Timestamp:        Sun May 30 20:18:32 2010 (4C02BA08)
    CheckSum:         00000000
    ImageSize:        00009000
    File version:     0.0.0.0
    Product version:  0.0.0.0
    File flags:       0 (Mask 0)
    File OS:          0 Unknown Base
    File type:        0.0 Unknown
    File date:        00000000.00000000
    Translations:     0000.04b0 0000.04e4 0409.04b0 0409.04e4
```

## Comments

.imgscan might not be able to find all hidden modules (**Debugger Omission** pattern, page 220).

Timestamps might be suspicious too.

## Deviant Token

Sometimes we need to check what security principal or group we run a process under, or what privileges it has or whether it has impersonating threads. We may find an unexpected token with a different security identifier, for example, Network Service instead of Local System (SID: S-1-5-18):

```
PROCESS 8f218d88  SessionId: 0  Cid: 09c4    Peb: 7ffdf000  ParentCid: 0240
DirBase: bffd4260  ObjectTable: e10eae90  HandleCount:  93.
Image: ServiceA.exe
VadRoot 8f1f70e8 Vads 141 Clone 0 Private 477. Modified 2. Locked 0.
DeviceMap e10038d8
Token                             e10ff5d8
[...]
0: kd> !token e10ff5d8
_TOKEN e10ff5d8
TS Session ID: 0
User: S-1-5-20
[...]
```

Well-known SIDs can be found in MS KB article 243330³⁹.

## Diachronic Module

When we have a performance issue, we may request a set of consecutive memory dump saved after some interval. In such memory dumps we may see the same thread(s) having similar stack trace(s). In this simple diagnostic scenario we may diagnose several patterns based on the stack traces: Active Threads (page 66) that can be Spiking Threads (page 885) with Spike Intervals (page 884) or stable, not changing, Wait Chains (for example, critical sections, page 1086). Here we may easily identify Top (page 1012) active and Blocking (page 96) modules based on Module Wait Chain (page 1103).

The more complex case arises when we have different Active Threads and/or Wait Chains with different thread IDs at different times. However, if their Top Module is the same, we may have found it as a performance root cause component especially in the case of Active Threads since it is statistically probable that such threads were active for considerable time deltas around the snapshot times (since threads are usually waiting). Such hypothesis may also be confirmed by inter-correlational analysis (Inter-Correlation⁴⁰) with software traces and logs where we can see Thread of Activity⁴¹ Discontinuities⁴² and Time Deltas⁴³.

We call this analysis pattern Diachronic Module since we see the module component appears in different thread stack traces diachronically (at different times). The typical simplified scenario is illustrated in this diagram:

![](img/d6dfefc8f9ab7106c77a723ff84aaa6d_230_0.png)

## Memory Snapshots

This analysis pattern is different from synchronous module case (the module component appears in different thread stack traces at the same time) which was named Ubiquitous Component (page 1020).

## Dialog Box

Similar to **Message Box** (page 660) and **String Parameter** (page 962) patterns we also have **Dialog Box** pattern where we can see dialog window caption and contents when we examine function parameters. Although in the examples below we know the dialog purpose from the friendly call stack function names, for many 3rd-party applications we either don’t have symbols or such helper functions, but we want to know what was on the screen when screenshots were not collected.

The first two examples are from *Notepad* application, and the third is from IE:

```
0:000> kv
ChildEBP RetAddr  Args to Child
0017f5c4 777b073f 777c3c9f 000d023c 00000001 ntdll!KiFastSystemCallRet
0017f5c8 777c3c9f 000d023c 00000000 user32!NtUserWaitMessage+0xc
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
02a6bc60 08c880c4 00000000 000d0014 011f0036 ...........6...
02a6bc70 000000c4 00460000 006e006f 00000074 .....F.o.n.t...
02a6bc80 004d0008 00200053 00680053 006c0065 ..M.S. .S.h.e.l.
02a6bc90 0020006c 006c0044 00000067 50020000 l. .D.l.g....P
02a6bca0 00000000 00700007 00090028 0fffa440 .......(@...
02a6bcb0 00260082 00670046 0074006e 0000003a ...&.F.n.t...
02a6bcc0 00000000 50210b51 00000000 00100007 ....Q!P.......
02a6bcd0 004c0062 ffff0470 00000085 00000000 b.L.p.......
02a6bce0 50020000 00000000 0070006e 0090002c .P....n.,...
02a6bcf0 0fff0441 00460082 006e006f 00200074 A...F.o.n.t.
02a6bd00 00740073 00790062 006e0069 0030003a s.t.&y.l.e.i...
02a6bd10 00000000 50210041 00000000 0010000e ...A!P...n...
02a6bd20 004c0044 ffff0471 00000085 00000000 J.L.q.......
02a6bd30 50020000 00000000 007000bd 0009001e ...P.......
02a6bd40 ffff0442 00260082 00690053 0055007a B...&S.i.z.e.
02a6bd50 0000000a 00000000 50210b51 00000000 .....Q!P....
02a6bd60 001000be 004c0024 0fff0472 00000085 ...$.L.r...
02a6bd70 00000000 50020007 00000000 00610007 ....P....a.
02a6bd80 00480062 0fff0430 00450080 00660066 b.H.0....E.f.f.
02a6bd90 00630065 00730074 00000000 50010003 e.c.t.s......P
```
