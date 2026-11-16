```
0:020> u
0e11ffa8 dcff fdiv st(7),st
...
```

We see that EIP is very close to EBP/ESP, and this explains why !analyze -v reports IP_ON_STACK. Clearly
floating-point code is not what we should expect. This example shows that wild pointers sometimes are valid but
either through code chain or pointer chain the execution reaches Invalid Pointer (page 589) and a process or
system crashes.

# Comments

The following example shows UNICODE data in RCX register:

```
0:001> k
 # Child-SP RetAddr Call Site
00 00000000`8d71deb8 00007ffb`322b918f ntdll!NtWaitForMultipleObjects+0xa
01 00000000`8d71dec0 00007ffb`322b908e KERNELBASE!WaitForMultipleObjectsEx+0xef
02 00000000`8d71e1c0 00007ffb`32c2155c KERNELBASE!WaitForMultipleObjects+0xe
03 00000000`8d71e200 00007ffb`32c21088 kernel32!WerpReportFaultInternal+0x494
04 00000000`8d71e770 00007ffb`322e03cd kernel32!WerpReportFault+0x48
05 00000000`8d71e7a0 00007ffb`34e48cd2 KERNELBASE!UnhandledExceptionFilter+0x1fd
06 00000000`8d71e8a0 00007ffb`34e34296 ntdll!RtlUserThreadStart$filt$0+0x3e
07 00000000`8d71e8e0 00007ffb`34e46660 ntdll!_C_specific_handler+0x96
08 00000000`8d71e950 00007ffb`34dc3c00 ntdll!RtlpExecuteHandlerForException+0xd
09 00000000`8d71e980 00007ffb`34e4577a ntdll!RtlDispatchException+0x370
0a 00000000`8d71f080 00007ffb`2fb57749 ntdll!KiUserExceptionDispatch+0x3a
0b 00000000`8d71f790 00007ffb`2f2baf5a uWM!CBaseObject::~Release+0x15
0c 00000000`8d71f7c0 00007ffb`2fb9fd6c uDWM!CWindowData::SetIconicBitmap+0x21
0d 00000000`8d71f7f0 00007ffb`2fbaddde uDWM!`ScalingCompatLogging::Instance'::`2'::`dynamic atexit
destructor for 'wrapper''+0x1497c
0e 00000000`8d71f820 00007ffb`2fbae13b uDWM!CIconicBitmapRegistry::AcceptBitmap+0x56
0f 00000000`8d71f860 00007ffb`2fbb9d09 uDWM!CIconicBitmapRegistry::BitmapReceived+0x267
10 00000000`8d71fa50 00007ffb`2fb9d9b0 uDWM!CWindowList::SetIconicThumbnail+0x105
11 00000000`8d71fac0 00007ffb`2fb12c0f uDWM!`ScalingCompatLogging::Instance'::`2'::`dynamic atexit
destructor for 'wrapper''+0x12c50
12 00000000`8d71fc40 00007ffb`2fbb1d71 dwmredir!CSessionPort::ProcessCommand+0x34f
13 00000000`8d71fcf0 00007ffb`2fb1c889 dwmredir!CPortBase::PortThreadInternal+0x241
14 00000000`8d71fda0 00007ffb`32c12d92 dwmredir!CPortBase::PortThread+0x9
15 00000000`8d71fdd0 00007ffb`34d9f64e kernel32!BaseThreadInitThunk+0x22
16 00000000`8d71fe00 00000000`00000000 ntdll!RtlUserThreadStart+0x34

0:001> .cxr 00000005`8d71f080
rax=0000000000000001 rbx=00390035003a0039 rcx=00390035003a0039
rdx=0000000000000000 rsi=00000000ffffffff rdi=000000005919e6f0
rip=00007ffb2fb57749 rsp=000000008d71f790 rbp=0000000058d71f960
r8=000000000000002e3 r9=000000000000002e3 r10=0000000058bcc7630
r11=0000000059400fbd0 r12=0000000058bcc7620 r13=000000005920e0000
r14=0000000000000047 r15=000000000000006c
iopl=0         nv up ei ng nz na po nc
cs=0033  ss=002b  ds=002b  es=002b  fs=0053  gs=002b             efl=00010286
uDWM!CBaseObject::~Release+0x15:
00007ffb`2fb57749 f00fc1708       lock xadd dword ptr [rcx+8],esi ds:00390035`003a0041=????????
```