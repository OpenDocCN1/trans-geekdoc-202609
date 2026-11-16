# Software

**Not My Version** is another basic pattern of DLL Hell variety. It is when we look at component timestamps and paths and realize that one of the modules from the production environment is older than we had during development and testing. The **lmft** WinDbg command will produce the necessary output. If there are many modules, we may want to create a CAD graph (Component Age Diagram 158) to spot anomalies visually. Component version check is one of the basic troubleshooting and system administration activities. Here is one example (module start and end load addresses are removed for visual clarity):

```
```
0:000> kL
Child-SP          RetAddr           Call Site
00000000`0012fed8 00000001`40001093 MyDLL!fnMyDLL
00000000`0012fee0 00000001`40001344 2DLls+0x1093
00000000`0012ff10 00000000`773acdcd 2DLls+0x1344
00000000`0012fff0 00000000`774fc6e1 kernel32!BaseThreadInitThunk+0xd
00000000`0012ff90 00000000`00000000 ntdll!RtlUserThreadStart+0x1d
```
```

```
```
0:000> lmft
module name
MyDLL   C:\OLD\MyDLL.dll   Wed Jun 18 14:49:13 2004
user32   C:\Windows\System32\user32.dll   Thu Feb 15 05:22:33 2007
kernel32 C:\Windows\System32\kernel32.dll Thu Nov 02 11:14:48 2006
ntdll   C:\Windows\System32\ntdll.dll   Thu Nov 02 11:16:02 2006
2DLls   C:\2DLls\2DLls.exe   Thu Jun 19 10:46:44 2008 (485A2B04)
uxtheme C:\Windows\System32\uxtheme.dll Thu Nov 02 11:15:07 2006
rpcrt4 C:\Windows\System32\rpcrt4.dll Tue Jul 17 05:21:15 2007
lpk C:\Windows\System32\lpk.dll   Thu Nov 02 11:12:33 2006
oleaut32 C:\Windows\System32\oleaut32.dll Thu Dec 06 05:09:35 2007
usp10 C:\Windows\System32\usp10.dll   Thu Nov 02 11:15:03 2006
ole32   C:\Windows\System32\ole32.dll   Thu Nov 02 11:14:31 2006
advapi32 C:\Windows\System32\advapi32.dll Thu Nov 02 11:11:35 2006
gdi32   C:\Windows\System32\gdi32.dll   Thu Feb 21 04:40:51 2008
msvcrt C:\Windows\System32\msvcrt.dll   Thu Nov 02 11:13:37 2006
imm32   C:\Windows\System32\imm32.dll   Thu Nov 02 11:13:15 2006
msctf   C:\Windows\System32\msctf.dll   Thu Nov 02 11:13:42 2006
```
```

This pattern should be checked when we have instances of **Module Variety** (page 703) and, especially, **Duplicated Module** (page 287). Note that this pattern can also easily become an anti-pattern when applied to **Unknown Component** (page 1035) 159.