
## Well-Tested Function

When looking at stack traces software engineers immediately spot the right function to dig into its source code:

```
STACK_TEXT:
05b3f514 66ed52d3 08d72fee 08da6fc4 05b3f540 msvcrt!wcscpy+0xe
05b3f53c 77c50193 07516fc8 06637fc4 00000006 ModuleA!Add+0xd8
05b3f568 77cb33e1 66ed51fb 05b3f750 00000006 rpcrt4!Invoke+0x30
05b3f968 77cb1968 08d6afe0 0774cf4c 0660af28 rpcrt4!NdrStubCall2+0x299
[...]
```

Most will start with `ModuleA!Add` and examine parameters to `wcscpy` function. This is because `wcscpy` (UNICODE version of `strcpy`) is considered **Well-Tested**. For the purposes of default analysis via `!analyse -v` command it is possible to configure WinDbg to ignore our own functions and modules as well if we are sure they were **Well-Tested** or **Pass Through** (page 787). For details, please see minidump analysis case study <sup>235</sup>.

## Well-Tested Module

We introduce this pattern by analogy with **Well-Tested Function** (page 1145). **Well-Tested Module** is a module we usually skip when analyzing **Stack Trace** (page 926) because we suspect it the least. WinDbg can also be customized to skip such modules for the default analysis command as shown in component identification minidump analysis example 236.

## Wild Code

The case when a function pointer or a return address becomes **Wild Pointer** (page 1150) and EIP or RIP value lies in a valid region of memory the execution path may continue through a region called **Wild Code**. This might loop on itself or eventually reach non-executable or invalid pages and produce an exception. **Local Buffer Overflow** (page 611) might lead to this behavior and also data corruption that overwrites function pointers with valid memory addresses.

Our favorite example is when a function pointer points to zeroed pages with EXECUTE page attribute. What will happen next when we dereference it? All zeroes are the perfect x86/x64 code:

```
0:001> dd 00000000`771afdf0
00000000`771afdf0 00000000 00000000 00000000 00000000
00000000`771afe00 00000000 00000000 00000000 00000000
00000000`771afe10 00000000 00000000 00000000 00000000
00000000`771afe20 00000000 00000000 00000000 00000000
00000000`771afe30 00000000 00000000 00000000 00000000
00000000`771afe40 00000000 00000000 00000000 00000000
00000000`771afe50 00000000 00000000 00000000 00000000
00000000`771afe60 00000000 00000000 00000000 00000000
0:001> u
ntdll!DbgUserBreakPoint:
00000000`771afe00 0000 add byte ptr [rax],al
00000000`771afe02 0000 add byte ptr [rax],al
00000000`771afe04 0000 add byte ptr [rax],al
00000000`771afe06 0000 add byte ptr [rax],al
00000000`771afe08 0000 add byte ptr [rax],al
00000000`771afe0a 0000 add byte ptr [rax],al
00000000`771afe0c 0000 add byte ptr [rax],al
00000000`771afe0e 0000 add byte ptr [rax],al
```

Now if RAX points to a valid memory page with WRITE attribute the code will modify the first byte at that address:

```
0:001> dq @rax
000007ff`fffdcc00 00000000`00000000 00000000`00000000 035a0000
000007ff`fffdcc10 00000000`0359c000 00000000`00000000
000007ff`fffdcc20 00000000`00001e00 00000000`00000000
000007ff`fffdcc30 000007ff`fffdcc00 00000000`00000000
000007ff`fffdcc40 00000000`0000142c 00000000`00000000
000007ff`fffdcc50 00000000`00000000 00000000`00000000
000007ff`fffdcc60 000007ff`fffd8000 00000000`00000000
000007ff`fffdcc70 00000000`00000000 00000000`00000000
```

Therefore the code will be perfectly executed:

```
0:001> t
ntdll!DbgBreakPoint+0x2:
00000000`771afdf2 0000 add byte ptr [rax],al ds:000007ff`fffdcc00=00

0:001> t
ntdll!DbgBreakPoint+0x4:
00000000`771afdf4 0000      add     byte ptr [rax],al ds:000007ff`fffdc000=00

0:001> t
ntdll!DbgBreakPoint+0x6:
00000000`771afdf6 0000      add     byte ptr [rax],al ds:000007ff`fffdc000=00

0:001> t
ntdll!DbgBreakPoint+0x8:
00000000`771afdf8 0000      add     byte ptr [rax],al ds:000007ff`fffdc000=00

0:001> t
ntdll!DbgBreakPoint+0xa:
00000000`771afdfa 0000      add     byte ptr [rax],al ds:000007ff`fffdc000=00
```

## Comments

Sometimes we see Incorrect Stack Trace (page 499) pattern since it doesn’t make sense that waiting functions call GDI and other modules:

```
0:000> k
ChildEBP RetAddr
03ced1b0 771d6aec ntdll!KiFastSystemCallRet
03ced1b4 75406a8e ntdll!NtWaitForMultipleObjects+0xc
03ced250 7734be76 KERNELBASE!WaitForMultipleObjectsEx+0x100
03ced298 7734be4e kernel32!WaitForMultipleObjectsExImplementation+0xe0
03ced2b4 7736072f kernel32!WaitForMultipleObjects+0x18
03ced320 773609ca kernel32!WerpReportFaultInternal+0x186
03ced334 77360978 kernel32!WerpReportFault+0x70
03ced344 773608f3 kernel32!BasepReportFault+0x20
03ced3d0 7720820a kernel32!UnhandledExceptionFilter+0x1af
03ced3d8 771ae364 ntdll!__RtlUserThreadStart+0x62
03ced3ec 771ae1fc ntdll!_Eh4CallFilterFunc+0x12
03ced414 771d72b9 ntdll!_except_handler4+0x8e
03ced438 771d728b ntdll!ExecuteHandler2+0x26
03ced45c 771af9d7 ntdll!ExecuteHandler+0x24
03ced4e8 771d7117 ntdll!RtlDispatchException+0x127
03ced4e8 63050001 ntdll!KiUserExceptionDispatcher+0xf
03ceda64 771e73e2 ModuleA!FunctionA+0xc1
03ceda84 0141b848 ntdll!_SEH_epilog4_GS+0xa
03cedcb4 767cbbf4 ModuleB!FunctionB+0x188
03cedcc8 767cbcb5 gdi32!NTGdiDopenDCw+0xc
03cedf70 013cb7df gdi32!hdcCreateDcW+0x517
03cee0c8 7734c413 ModuleB!FunctionC+0xff
03cee0e0 7734c3c2 kernel32!WaitForSingleObjectExImplementation+0x75
03cee0f4 65e66c9c kernel32!WaitForSingleObject+0x12
WARNING: Frame IP not in any known module. Following frames may be wrong.
00000000 00000000 0x65e66c9c
```

Also the return address for ModuleA!FunctionA looks coincidental: 63050001. Although we are able to see code we are not able to disassemble it backwards:

```
0:000> u 63050001
ModuleA!FunctionA+0xc1:
63050001 a105638c34 mov eax,dword ptr ds:[C4836305h]
63050006 108d4c241051 adc byte ptr [ebp+5110244Ch],cl
6305000c ff15b4a00563 call dword ptr [ModuleA!_imp__OutputDebugStringA (6305a0b4)]
63050012 84e14 mov ecx,dword ptr [esi+14h]
63050015 85c9 test ecx,ecx
63050017 740e je ModuleA!FunctionA+0xe7 (63050027)
63050019 8b11 mov edx,dword ptr [ecx]
6305001b 8b4204 mov eax,dword ptr [edx+4]

0:000> ub 63050001
^ Unable to find valid previous instruction for 'ub 63050001'

0:000> ub 63050001-1
^ Unable to find valid previous instruction for 'ub 63050001-1'

0:000> ub 63050001-2
^ Unable to find valid previous instruction for 'ub 63050001-2'

0:000> ub 63050001-3
ModuleA!FunctionA+0xa4:
6304ffe4 ffd2 call edx
6304ffe6 84c0 test al,al
6304ffe8 7541 jne ModuleA!FunctionA+0xeb (6305002b)
6304ffea 6818c20563 push offset ModuleA!`string' (6305c218)
6304ffef 68bcc10563 push offset ModuleA!`string' (6305c1bc)
6304fff4 8d442418 lea eax,[esp+18h]
6304fff8 6800010000 push 100h
6304fffd 50 push eax
```

## Wild Pointer

This pattern was briefly mentioned in Local Buffer Overflow (page 611) which shows examples of pointers having UNICODE structure in their values. We can also observe pointers with ASCII structure as .formats WinDbg command indicates:

```
FAILED_INSTRUCTION_ADDRESS:
 65747379`735c5357  ??
          ???
IP_ON_HEAP:  65747379735c5357
0:012> .formats rip
Evaluate expression:
  Hex:     65747379`735c5357
  Decimal: 7310595060592825175
  Octal:   0625643467456327051527
  Binary:  01100101 01110100 01110011 01110011 01110111 00110100 01011100 01010111
  Chars:   etsys\Sw
  Time:    Wed May 10 22:00:59.282 24767 (GMT+1)
  Float:   low 1.7456e+031 high 7.21492e+022
  Double:  5.30388e+180
```

Here is another example of a pointer having UNICODE structure:

```
FAILED_INSTRUCTION_ADDRESS:
 0045004c`00490046  ??
          ???
0:014> .formats rip
Evaluate expression:
  Hex:     0045004c`00490046
  Decimal: 19422099815333958
  Octal:   0010505004600022200106
  Binary:  00000000 01000101 00000000 01001100 00000000 01001001 00000000 01000110
  Chars:   ..E.L.I.F
  Time:    Wed Jul 19 07:46:21.533 1662 (GMT+1)
  Float:   low 6.70409e-039 high 6.33676e-039
  Double:  2.33646e-307
```

When we have EIP or RIP pointers, we have another pattern to name when the value coincidentally lies inside some valid region of memory: Wild Code (page 1148). Here is one example of the latter pattern:

```
IP_ON_STACK:
 +e11ffa8
STACK_TEXT:
 0e11ff7c 098eefe2 0xe11ffa8
 0e11ff84 77b6b530 dll1!StartWorking+0xcab
 0e11ffb8 7c826063 msvcrt!_endthreadex+0xa3
 0e11ffec 00000000 kernel32!BaseThreadStart+0x34
```
