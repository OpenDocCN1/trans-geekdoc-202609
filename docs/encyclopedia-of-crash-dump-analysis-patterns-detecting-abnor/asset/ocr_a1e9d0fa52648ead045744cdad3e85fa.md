# Nested Offender

Sometimes we suspect one component, but there is another, **Nested Offender**, which raised an exception. That exception propagated through exception filters and handlers and prompted the suspected component to respond with a diagnostic message. Here is an example of a thread showing the runtime error message box:

![](bbox=[0.222, 0.188, 0.789, 0.438])

The corresponding **Stack Trace** (page 926) points to *ComponentB* module:

```
0:087> kL
ChildEBP RetAddr
5546ddf0 76f50dde ntdll!KiFastSystemCallRet
5546ddf4 76f3b0b2 user32!NtUserWaitMessage+0xc
5546de28 76f3bca user32!DialogBox2+0x202
5546de50 76f8ccdc user32!InternalDialogBox+0xd0
5546de0f 76f8d25e user32!SoftModalMessageBox+0x69f
5546e040 76f8d394 user32!MessageBoxWorker+0x2c7
5546e098 76f8d43e user32!MessageBoxTimeoutW+0x7f
5546e0cc 76f8d5ec user32!MessageBoxTimeoutA+0xa1
5546e0ec 67f24ac7 user32!MessageBoxExA+0x1b
5546e10c 76f8d65e ieiframe!Detour_MessageBoxExA+0x2c
5546e128 0c841c28 user32!MessageBoxA+0x45
WARNING: Stack unwind information not available. Following frames may be wrong.
5546e16c 0c83d1b9 ComponentB!DllUnregisterServer+0x9437
5546e190 0c83c7f2 ComponentB!DllUnregisterServer+0x49c8
00000000 00000000 ComponentB!DllUnregisterServer+0x4781

0:087> .asm no_code_bytes
Assembly options: no_code_bytes
```