```
0006fb38 010b84ce ModuleA!Read+0x6f
[...]

0: kd> lmi ModuleA
Loaded Module Info: [ModuleA]
Module: ModuleA
Base Address: 01090000
Image Name: ModuleA.dll
Machine Type: 332 (I386)
Time Stamp: 4e4484f0 Thu Aug 11 21:42:08 2011
Size: 9b0000
CheckSum: a9c8b
Characteristics: 2102
Debug Data Dirs: Type Size VA Pointer
CODEVIEW: 5e, 830a0, 830a0 RSDS - GUID: {C14E734A-367F-4DD0-974D-FA47C1194F28}
Age: 1, Pdb: Y:\src\...\ModuleA.pdb
Symbol Type: DEFERRED - No error - symbol load deferred
Load Report: no symbols loaded
```

```
0: kd> lm v m ModuleA
start end module name
01090000 0112b000 ModuleA (deferred)
Image path: C:\Program Files\VendorA\ModuleA.dll
Image name: ModuleA.dll
Timestamp: Thu Aug 11 21:42:08 2011 (4E4484F0)
CheckSum: 000A9C8B
ImageSize: 0009B000
File version: 1.3.0.0
Product version: 1.3.0.0
File flags: 8 (Mask 3F) Private
File OS: 40004 NT Win32
File type: 2.0 DLL
File date: 00000000.00000000
Translations: 0409.04b0
CompanyName: VendorA
ProductName: VendorA
InternalName: ModuleA.dll
OriginalFilename: ModuleA.dll
ProductVersion: 1.3
FileVersion: 1.3.0.0
FileDescription: ModuleA GUI
LegalCopyright: Copyright VendorA
```

So we switch to that thread (with the new process context) to get the needed symbol path:

```
0: kd> .thread /r /p 89703020
Implicit thread is now 89703020
Implicit process is now 89825020
Loading User Symbols
```