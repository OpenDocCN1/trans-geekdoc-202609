# F

# Fake Module

In **Fake Module** pattern, one of the loaded modules masquerades as a legitimate system DLL or a widely known value adding DLL from some popular 3rd-party product. To illustrate this pattern we modeled it as Victimware78: a process crashed after loading a malware module:

```
0:000> k
*** Stack trace for last set context - .thread/.cxr resets it
Child-SP            RetAddr           Call Site
00000000`0026f978  00000001`3f89103a 0x0
00000000`0026f980  00000001`3f8911c4 FakeModule!wmain+0x3a
00000000`0026f9c0  00000000`76e3652d FakeModule!__tmainCRTStartup+0x144
00000000`0026fa00  00000000`7752c521 kernel32!BaseThreadInitThunk+0xd
00000000`0026fa30  00000000`00000000 ntdll!RtlUserThreadStart+0x1d
```

When we inspected loaded modules we didn't find anything suspicious:

```
0:000> lm
start             end                 module name
00000000`76e20000 00000000`76f3f000   kernel32 <none>
00000000`77500000 00000000`776a9000   ntdll <none>
00000000`3f790000 00000000`3f8a6000   FakeModule <none>
000007fe`f8bc0000 000007fe`f8cc7000   winspool <none>
000007fe`fdb30000 000007fe`fdb9c000   KERNELBASE <none>
```

However, when checking module images for any modifications we find that *winspool* module was not compared with the corresponding existing binary from Microsoft symbol server:

```
0:000> !for_each_module "!chkimg -v -d @#ModuleName"
Searching for module with expression: kernel32
Will apply relocation fixups to file used for comparison
Will ignore NOP/LOCK errors
Will ignore patched instructions
Image specific ignores will be applied
Comparison image path: C:\WSDK8\Debuggers\x64\sym\kernel32.dll\503285C111f000\kernel32.dll
No range specified

Scanning section: .text
Size: 633485
Range to scan: 76e21000-76ebba8d
Total bytes compared: 633485(100%)
Number of errors: 0
0 errors : kernel32
```