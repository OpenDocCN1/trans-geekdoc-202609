```
0:000> kv
ChildEBP RetAddr  Args to Child
WARNING: Frame IP not in any known module. Following frames may be wrong.
49ab5bba 00000000 00000000 00000000 00000000 0x60f1011a
0:000> r
eax=38084ff0 ebx=52303340 ecx=963f1416 edx=0000063d esi=baaff395 edi=678c5804
eip=60f1011a esp=5a9d0f48 ebp=49ab5bba iopl=0 nv up ei pl nz na pe nc
cs=001b ss=0023 ds=0023 es=0023 fs=003b gs=0000 efl=00210206
60f1011a cd01 int 1
0:000> u
60f1011a cd01 int 1
60f1011c cc int 3
60f1011d 8d ???
60f101e6 c8eb02 shr bl,2
60f10121 0f840f31cd01 je 62be3236
60f10127 8d ???
60f10128 c8cc0f ror ah,0Fh
60f1012b 0cce or ecx,esi
```

Looking at raw stack data, we notice the presence of a specific component that is known to patch the process import table. Applying techniques outlined in Hooked Functions pattern (page 488) we notice two different 3rd-party components that patched two different modules (kernel32 and user32):

```
0:000> !chkimg -lo 50 -d !kernel32 -v
Searching for module with expression: !kernel32
Will apply relocation fixups to file used for comparison
Will ignore NOP/LOCK errors
Will ignore patched instructions
Image specific ignores will be applied
Comparison image path: c:\mss\kernel32.dll\4626487F102000\kernel32.dll
No range specified
Scanning section: .text
Size: 564709
Range to scan: 77e41000-77ecade5
77e41ae5-77e41ae9 5 bytes - kernel32!LoadLibraryExW
[ 6a 34 68 48 78:e9 16 e5 f4 07 ]
77e44a8a-77e44a8e 5 bytes - kernel32!WaitNamedPipeW (+0x2fa5)
[ 8b ff 55 8b ec:e9 71 b5 f9 07 ]
77e5106a-77e5106e 5 bytes - kernel32!CreateProcessInternalW (+0xc5e0)
...
Total bytes compared: 564709(100%)
Number of errors: 49
49 errors : !kernel32 (77e41ae5-77e9aa16)
```