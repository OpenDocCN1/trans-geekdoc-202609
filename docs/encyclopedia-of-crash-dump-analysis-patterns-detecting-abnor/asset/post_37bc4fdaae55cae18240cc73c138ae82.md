
![](img/d6dfefc8f9ab7106c77a723ff84aaa6d_726_0.png)

Consider the following C++ code with two exception handlers:

```
__try
{
  __try
  {
    *(int *)NULL = 0; // Exception 1
    // Dump1 1st chance
  }
  __except (EXCEPTION_EXECUTE_HANDLER)
  {
    std::cout << "Inner" << std::endl;
    *(int *)NULL = 0; // Exception 2
    // Dump2 1st chance
  }
}
__except (EXCEPTION_EXECUTE_HANDLER)
{
    std::cout << "Outer" << std::endl;
    *(int *)NULL = 0;   // Exception 3
                // Dump3 1st chance
                // Dump4 2nd chance
}
```

If we run the actual program, and we have set a default postmortem debugger 149, we get a second-chance exception dump (Dump4). The program first outputs “Inner” and then “Outer” on a console and then crashes. When we look at the dump we see second-chance exception processing code where the exception record for NtRaiseException is the same and points to Exception 3 context (shown in bold underlined):

> This dump file has an exception of interest stored in it.
> The stored exception information can be accessed via .ecxr.
> ((1dc.f94): Access violation - code c0000005 (first/second chance not available)
> *** ERROR: Module load completed but symbols could not be loaded for NestedException.exe
> NestedException+0x1a72:
> 00000001`40001a72 c7042500000000000000 mov dword ptr [0],0 ds:00000000`00000000=????????
> 
> 0:000> !teb
> TEB at 000007fffffd0000
>     ExceptionList:        0000000000000000
>     StackBase:            0000000000130000
>     StackLimit:           000000000012d000
>     SubSystemTib:         0000000000000000
>     FiberData:            0000000000001e00
>     ArbitraryUserPointer: 0000000000000000
>     Self:                 000007ffffffe000
>     EnvironmentPointer:   0000000000000000
>     ClientId:             00000000000011dc . 0000000000000f94
>     RpcHandle:            0000000000000000
>     Tls Storage:          000007ffffffe058
>     PEB Address:          000007fffffff5000
>     LastErrorValue:       0
>     LastStatusValue:      c000000d
>     Count Owned Locks:    0
>     HardErrorMode:        0
> 
> 0:000> dqs 000000000012d000 0000000000130000
> ...
> 00000000`0012f918 00000000`00000006
> 00000000`0012f920 00000000`00000000
> 00000000`0012f928 00000000`775a208d ntdll!KiUserExceptionDispatch+0x53
> 00000000`0012f930 00000000`00000000
> 00000000`0012f938 00000000`0012f930 ; exception context
> 00000000`0012f940 01c8d5f0`00000000
> 00000000`0012f948 00000000`00000000
> ...

```
0:000> ub ntdll!KiUserExceptionDispatch+0x53
ntdll!KiUserExceptionDispatch+0x35:
00000000`775a206f xor     edx,edx
00000000`775a2071 call    ntdll!RtlRestoreContext (00000000`775a2255)
00000000`775a2076 jmp     ntdll!KiUserExceptionDispatch+0x53 (00000000`775a208d)
[...]
00000000`775a2082 mov     rdx,rsp
00000000`775a2085 xor     r8,r8b
00000000`775a2088 call    ntdll!NtRaiseException (00000000`775a1550)
0:000> .cxr 00000000`0012f930
rax=000000001400223d rbx=0000000000000000 rcx=00000000140022128
rdx=0000000000000001 rsi=0000000000000006 rdi=00000000140022120
rip=00000000140001a72 rsp=000000000012fed0 rbp=0000000000000000
r8=000007ffffffe000  r9=0000000000000001 r10=0000000000000000
r11=0000000000000246 r12=0000000000000000 r13=0000000000000002
r14=0000000000000000 r15=0000000000000000
iopl=0         nv up ei pl zr ac po nc
cs=0033  ss=002b  ds=002b  es=002b  fs=0053  gs=002b             efl=00010256
NestedException+0x1a72:
00000001`40001a72 c7042500000000000000 mov dword ptr [0],0 ds:00000000`00000000=????????
```

However, if we have a first-chance exception Dump3 from some exception monitoring program (Early Crash Dump pattern, page 312) we see that NtRaiseException parameter points to "Inner" Exception 2 context (a different and earlier address, shown in italics underlined):

```
This dump file has an exception of interest stored in it.
The stored exception information can be accessed via .ecxr.
((1dc.f94): Access violation - code c0000005 (first/second chance not available)
*** ERROR: Module load completed but symbols could not be loaded for NestedException.exe
NestedException+0x1a72:
00000001`40001a72 c7042500000000000000 mov dword ptr [0],0 ds:00000000`00000000=????????
0:000> dqs 00000000`0012d000 00000000`00130000
...
00000000`0012f928 00000000`775a2068 ntdll!KiUserExceptionDispatch+0x2e
00000000`0012f930 00000000`00000000
00000000`0012f938 00000000`0012f930 ; exception context
0:000> .cxr 00000000`0012f930
[...]
NestedException+0x19fa:
00000001`400019fa c7042500000000000000 mov dword ptr [0],0 ds:00000000`00000000=????????
```

Similar can be said about Dump2 where NtRaiseException parameter points to Exception 1 context. But Dump1 doesn't have any traces of exception processing as expected. All 4 dump files can be downloaded from FTP to play with 150.

## Nested Offender

Sometimes we suspect one component, but there is another, **Nested Offender**, which raised an exception. That exception propagated through exception filters and handlers and prompted the suspected component to respond with a diagnostic message. Here is an example of a thread showing the runtime error message box:

![](img/d6dfefc8f9ab7106c77a723ff84aaa6d_729_0.png)

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

However, when looking at the raw stack data, we see exception processing residue (**Hidden Exception** pattern, page 457) that points to *ComponentA* that tried to allocate more memory than was available (*bad_alloc* C++ Exception, page 108):

```
0:087> !teb
TEB at 7ffb4000
    ExceptionList:        5546e4e8
    StackBase:            55470000
    StackLimit:           55457000
    SubSystemTib:         00000000
    FiberData:            00001e00
    ArbitraryUserPointer: 00000000
    Self:                 7ffb4000
    EnvironmentPointer:   00000000
    ClientId:             0000136c . 00001714
    RpcHandle:            00000000
    Tls Storage:          5826eef0
    PEB Address:          7ffd7000
    LastErrorValue:       0
    LastStatusValue:      0
    Count Owned Locks:    0
    HardErrorMode:        0
```

```
0:087> dds 55457000 55470000
55457000 00000000
[...]
5546e694 55470000
5546e698 55457000
5546e69c 00274cb0
5546e6a0 5546e9f4
5546e6a4 772899f7 ntdll!KiUserExceptionDispatcher+0xf
5546e6a8 0046e6b8
5546e6ac 5546e6d8
5546e6b0 5546e6b8
[...]
```

```
0:087> .cxr 5546ed8
eax=5546e94a ebx=00001000 ecx=00000003 edx=00000000 esi=689a9c54 edi=6b330000
eip=771942eb esp=5546e94a ebp=5546e9f4 iopl=0 nv up ei pl nz ac po nc
cs=001b ss=0023 ds=0023 es=0023 fs=003b gs=0000 efl=00240212
kernel32!RaiseException+0x58:
771942eb c9              leave
```

```
0:087> .exr 5546e6b8
ExceptionAddress: 771942eb (kernel32!RaiseException+0x00000058)
ExceptionCode: e06d7363 (C++ EH exception)
ExceptionFlags: 00000001
NumberParameters: 3
Parameter[0]: 19930520
Parameter[1]: 5546ea3c
Parameter[2]: 688b7954
pExceptionObject: 5546ea3c
__s_ThrowInfo : 688b7954
Type : class std::bad_alloc
Type : class std::exception
```

```
0:087> kl
*** Stack trace for last set context - .thread/.cxr resets it
ChildEBP RetAddr
5546e9f4 6882dead kernel32!RaiseException+0x58
WARNING: Stack unwind information not available. Following frames may be wrong.
5546ea2c 6882a59d ComponentA!DllUnregisterServer+0x1adbe0
5546ea48 6868157b ComponentA!DllUnregisterServer+0x1aa2d0
5546ea74 6869d2c6 ComponentA!DllUnregisterServer+0x12ae
5546ea88 6868a415 ComponentA!DllUnregisterServer+0x1cfff9
5546eaa0 685a165e ComponentA!DllUnregisterServer+0xa148
5546eac8 685a9828 ComponentA+0x5165e
5546ebc8 68605fdd ComponentA+0x59828
5546ebf0 6a807aba ComponentA+0xb5fdd
5546ec08 6a807a77 mshtml!CViewDispClient::Invalidate+0x59
5546ec20 00000000 mshtml!CDispRoot::InvalidateRoot+0x1d
0:087> ub 6882dead
ComponentA!DllUnregisterServer+0x1adbc4:
6882de91 je ComponentA!DllUnregisterServer+0x1adbcd (6882de9a)
6882de93 mov dword ptr [ebp-0Ch],1994000h
6882de9a lea eax,[ebp-0Ch]
6882de9d push eax
6882de9e push dword ptr [ebp-10h]
6882dea1 push dword ptr [ebp-1Ch]
6882dea4 push dword ptr [ebp-20h]
6882dea7 call dword ptr [ComponentA!DllUnregisterServer+0x1ba0a3 (6883a370)]
```

It happens that ComponentB has an exception filter that shows the runtime error:

```
0:087> !exchain
5546e4e8: ComponentB!DllUnregisterServer+18df (0c83a0d0)
5546e578: kernel32!ExceptHandler4+0 (7715e289)
5546e5e4: ntdll!ExecuteHandler+23a (77289bad)
5546faa8: user32!except_handler4+0 (76f951ba)
5546fb0c: user32!except_handler4+0 (76f951ba)
5546fbd0: ntdll!_except_handler4+0 (77239834)
Invalid exception stack at ffffffff
```

Nested Offender is different from Nested Exception pattern (page 726). The latter is about an exception handler that experiences or throws another exception.
