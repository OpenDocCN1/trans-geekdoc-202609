we compiled the version of MyDLL that causes NULL pointer access violation when the same function is called from it. The DLL was placed into a separate folder, and the PATH variable was modified to reference that folder:

```
C:\>set PATH=C:\OLD;%PATH%
```

The application crashes and the installed default postmortem debugger⁴⁷ saves its crash dump. If we open it, we see that it crashed in MyDLL_1e60000 module which should trigger suspicion:

```
0:000> r
rax=0000000001e1010 rbx=0000000000000000 rcx=0000775dcac00000
rdx=0000000000000000 rsi=0000000000000006 rdi=0000000000001770
rip=0000000001e61010 rsp=000000000012fed8 rbp=0000000000000000
r8=0000000000000000 r9=000000000012fd58 r10=0000000000000001
r11=000000000012fcc0 r12=0000000000000000 r13=0000000000000002
r14=0000000000000000 r15=0000000000000000
iopl=0 nv up ei pl nz na po nc
cs=0033 ss=002b ds=002b es=002b fs=0053 gs=002b efl=00010200
MyDLL_1e60000!fnMyDLL:
00000000`01e61010 c704250000000000000000 mov dword ptr [0],0 ds:00000000`00000000=????????
0:000> kL
Child-SP          RetAddr           Call Site
00000000`0012fed8 00000001`40010193 MyDLL_1e60000!fnMyDLL
00000000`0012fee0 00000001`40013444 2DLls+0x1093
00000000`0012ff10 00000000`773acdcd 2DLls+0x1344
00000000`0012ff60 00000000`774fc6e1 kernel32!BaseThreadInitThunk+0xd
00000000`0012ff90 00000000`00000000 ntdll!RtlUserThreadStart+0x1d
```

Looking at the list of modules we see two versions of MyDLL loaded from two different folders:

```
0:000> lm
start             end                 module name
00000000`01e60000 00000000`01e71000   MyDLL_1e60000
00000000`772a0000 00000000`7736a000   user32
00000000`77370000 00000000`774a1000   kernel32
00000000`774b0000 00000000`7762a000   ntdll
00000001`40000000 00000001`40010000   2DLls
00000001`80000000 00000001`80011000   MyDLL
00007fe`fc9e0000 000007fe`fca32000   uxtheme
000007fe`fe870000 000007fe`fe9a9000   rpcrt4
000007fe`fe9b0000 000007fe`fe9bc000   lpk
000007fe`fea10000 000007fe`feae8000   oleaut32
000007fe`fec0000 000007fe`fed6a000   usp10
000007fe`fefb0000 000007fe`fefb0000   ole32
000007fe`fefb0000 000007fe`ff0af000   advapi32
000007fe`fff00000 000007fe`fff31000   gdi32
000007fe`ff2e0000 000007fe`ff381000   msvcrt
000007fe`ff390000 000007fe`ff3b8000   imm32
000007fe`ff4b0000 000007fe`ff5b4000   msctf
```