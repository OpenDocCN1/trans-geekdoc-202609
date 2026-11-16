```
0: kd> lmv m ModuleA
start   end         module name
01320000 013bb000   ModuleA   (deferred)
Image path: C:\Program Files\VendorA\ModuleA.dll
Image name: ModuleA.dll
Timestamp:        Thu Aug 11 21:42:08 2011 (4E4484F0)
CheckSum:         000A9C8B
ImageSize:        0009B000
Translations:     0000.04b0 0000.04e4 0409.04b0 0409.04e4
```

```
0: kd> !lmi ModuleA
Loaded Module Info: [ModuleA]
    Module: ModuleA
Base Address: 01320000
Image Name: ModuleA.dll
Machine Type: 332 (I386)
Time Stamp: 4e4484f0 Thu Aug 11 21:42:08 2011
Size: 9b000
CheckSum: a9c8b
Characteristics: 2102
Debug Data Dirs: Type Size VA Pointer
CODEVIEW 5e, 830a0, 830a0 [Debug data not mapped] - can't validate symbols, if present.
Symbol Type: DEFERRED - No error - symbol load deferred
Load Report: no symbols loaded
```

However, in Stack Trace Collection (page 943, !process 0 3f WinDbg command) we find another stack trace from a different process but with loaded symbol files for ModuleA:

```
THREAD 89703020 Cid 1068.1430 Teb: 7ffdf000 Win32Thread: e34d43a8 WAIT: (UserRequest) UserMode Non-Alertable
89a3ac58 NotificationEvent
89703110 NotificationTimer
IRP List:
899ab488: (0006,0094) Flags: 00000900 Mdl: 00000000
Not impersonating
DeviceMap e10086c8
Owning Process 0 Image: <Unknown>
Attached Process 89825020 Image: ApplicationB.exe
Wait Start TickCount 8164457 Ticks: 2821 (0:00:00:44.078)
Context Switch Count 552 LargeStack
UserTime 00:00:00.296
KernelTime 00:00:00.890
Start Address 0x0103e5e1
Stack Init b8796000 Current b8795ca0 Base b8796000 Limit b8791000 Call 0
Priority 15 BasePriority 15 PriorityDecrement 0 DecrementCount 0
ChildEBP RetAddr
b8795cb8 80503836 nt!KiSwapContext+0x2f
b8795cc4 804fb068 nt!KiSwapThread+0x8a
b879cec 805c0750 nt!KeWaitForSingleObject+0x1c2
b8795d50 8054161c nt!NtWaitForSingleObject+0x9a
b8795d50 7c90e4f4 nt!KiFastCallEntry+0x8fc (TrapFrame @ b8795d64)
0006fa1c 7c90d3f3 ntdll!KiFastSystemCallRet
0006fa20 7c8025db ntdll!NtWaitForSingleObject+0xc
0006fa84 010ae96a kernel32!WaitForSingleObjectEx+0xa8
0006fafc 010aeaf ModuleA!Wait+0xaab
```