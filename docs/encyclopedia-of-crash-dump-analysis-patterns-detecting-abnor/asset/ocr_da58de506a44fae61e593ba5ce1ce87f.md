```
0:000> u 77e41ae5
kernel32!LoadLibraryExW:
77e41ae5 7fd90000
77e41aea out 77h,al
77e41aec call kernel32!_SEH_prolog (77e6b779)
77e41af1 xor edi,edi
77e41af3 mov dword ptr [ebp-28h],edi
77e41af6 mov dword ptr [ebp-2Ch],edi
77e41af9 mov dword ptr [ebp-20h],edi
77e41afc cmp dword ptr [ebp+8],edi

0:000> u 7fd90000
*** ERROR: Symbol file could not be found. Defaulted to export symbols for ComponentA.dll -
7fd90000 jmp ComponentA!DllUnregisterServer+0x2700 (678c4280)
7fd90005 push 34h
7fd90007 push offset kernel32!`string'+0xc (77e67b48)
7fd9000c jmp kernel32!LoadLibraryExW+0x7 (77e41aec)
7fd90011 add byte ptr [eax],al
7fd90013 add byte ptr [eax],al
7fd90015 add byte ptr [eax],al
7fd90017 add byte ptr [eax],al

0:000> !chkimg -lo 50 -d !user32 -v
Searching for module with expression: !user32
Will apply relocation fixups to file used for comparison
Will ignore NOP/LOCK errors
Will ignore patched instructions
Image specific ignores will be applied
Comparison image path: c:\mss\user32.dll\45E7BFD692000\user32.dll
No range specified

Scanning section: .text
Size: 396943
Range to scan: 77381000-773e1e8f
77383f38-77383f3c 5 bytes - user32!EnumDisplayDevicesW
[ 8b ff 55 8b ec:e9 c3 c0 82 08 ]
77384406-7738440a 5 bytes - user32!EnumDisplaySettingsExW (+0x4ce)
[ 8b ff 55 8b ec:e9 ff 5f 7e 08 ]
773844d9-773844dd 5 bytes - user32!EnumDisplaySettingsW (+0xd3)
[ 8b ff 55 8b ec:e9 22 bb 80 08 ]
7738619b-7738619f 5 bytes - user32!EnumDisplayDevicesA (+0x1cc2)
[ 8b ff 55 8b ec:e9 60 9e 83 08 ]
7738e985-7738e989 5 bytes - user32!CreateWindowExA (+0x87ea)
[ 8b ff 55 8b ec:e9 76 16 8c 08 ]
...
Total bytes compared: 396943(100%)
Number of errors: 119
119 errors : !user32 (7738f38-773c960c)
```