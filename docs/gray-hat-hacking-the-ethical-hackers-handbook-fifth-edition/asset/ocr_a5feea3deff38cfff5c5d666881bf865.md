checking the HookType parameter in the stack, which is 2 (for WH_KEYBOARD):

```
0012F964 00000002 |HookType
0012F968 00410078 |Hookproc = locker.00410078
0012F96C 00400000 |hModule = 00400000 (locker)
0012F970 00000000 \ThreadID = 0
```

![](bbox=[0.133, 0.206, 0.262, 0.288])

NOTE Many other actions are performed by the malware. We are just listing the more relevant ones to keep the chapter’s length reasonable.

Moving forward, we find a loop whose only purpose is to find and minimize all the windows on the Desktop:

```
00410D47 PUSH 0FF
00410D4C LEA EAX,DWORD PTR SS:[ESP+4]
00410D50 PUSH EAX
00410D51 PUSH EBX
00410D52 CALL locker.004051BC ; JMP to USER32.GetWindowTextA
00410D57 PUSH ESP
00410D58 PUSH 0
00410D5A CALL locker.00405194 ; JMP to USER32.FindWindowA
00410D5F MOV ESI,EAX
00410D61 PUSH ESI
00410D62 CALL locker.00404EEC ; JMP to USER32.IsWindowVisible
00410D67 TEST EAX,EAX
00410D69 JE SHORT locker.00410D7D
00410D6B PUSH 0
00410D6D PUSH 0F020
00410D72 PUSH 112
00410D77 PUSH ESI
00410D78 CALL locker.004051EC ; JMP to USER32.PostMessageA
00410D7D PUSH 2
00410D7F PUSH EBX
00410D80 CALL locker.00404EB4 ; JMP to USER32.GetWindow
00410D85 MOV EBX,EAX
00410D87 TEST EBX,EBX
00410D89 JNZ SHORT locker.00410D47
```

This check is self-explanatory. It gets the title of the current window displayed via GetWindowTextA and finds that window. If the window is visible, it is minimized via a PostMessage with the following parameters:

```
0012F964 hWnd = 180174
0012F968 Message = WM_SYSCOMMAND
0012F96C Type = SC_MINIMIZE
```