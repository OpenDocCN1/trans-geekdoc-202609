
This can also be seen from the output of !lm1 command:

```
0:000> !lm1 7fef8cb0000
Loaded Module Info: [7fef8cb0000]
Module winspool
Base Address: 000007fef8cb0000
Image Name: winspool.drv
Machine Type: 34404 (X64)
Time Stamp: 50de1bb2 Fri Dec 28 22:22:42 2012
Size: 17000
CheckSum: 0
Characteristics: 2022
Debug Data Dirs: Type Size VA Pointer
CODEVIEW 49, e2c0, cac0 RSDS - GUID: {29D85193-1C9D-4997-95BA-DD190FA3C1BF}
Age: 1, Pdb: C:\Work\AWMA\FakeModule\x64\Release\winspool.pdb
?? 10, e30c, cb0c [Data not mapped]
Symbol Type: DEFERRED - No error - symbol load deferred
Load Report: no symbols loaded
```

## False Effective Address

When calculating effective addresses such as [r10+10h] or [rax+rcx*12h+40h] to show their value in the output of some commands such as .trap or .cxr a debugger uses CPU register values from a saved trap frame or context structure. If such information is invalid, the reported effective address doesn’t correspond to the real one during code execution. This analysis pattern is similar to False Function Parameters (page 390). Therefore, if a fault address is saved during bugcheck or exception processing, it may not correspond to the output of some commands where such calculation is necessary. For example, in a bugcheck parameter we have this referenced memory address:

```
Arg1: fffffadda17d001d, memory referenced
```

But the output of .trap command shows NULL Pointer (page 752) address:

```
NOTE: The trap frame does not contain all registers.
Some register values may be zeroed or incorrect.
rax=0000000000000000 rbx=0000000000000000 rcx=0000000000000000
[...]
movzx eax,word ptr [rax+10h] 0010=????
```

Usually, we are lucky, and an effective address is correct despite a warning such as in a pattern example on page 169 and a pattern interaction case study 79.

## False Function Parameters

Beginner users of WinDbg sometimes confuse the first 3 parameters (or 4 for x64) displayed by kb or kv commands with real function parameters:

```
0:000> kbnL
 # ChildEBP RetAddr  Args to Child
00 002df5f4 0041167b 0002df9c 00000000 7efdf000 ntdll!DbgBreakPoint
01 002df6d4 004115c9 00000000 40000000 00000001 CallingConventions!A::thiscallFunction+0x2b
02 002df97c 004114f9 00000001 40001000 00000002 CallingConventions!fastcallFunction+0x69
03 002dfbf8 0041142b 00000000 40000000 00000001 CallingConventions!cdeclFunction+0x59
04 002dfe7c 004116e8 00000000 40000000 00000001 CallingConventions!stdcallFunction+0x5b
05 002dfff68 00411c76 00000001 005a2820 005a28c8 CallingConventions!wmain+0x38
06 002dfffb8 00411abd 002dfff0 7d4e7d2a 00000000 CallingConventions!__tmainCRTStartup+0x1a6
07 002dfffc0 7d4e7d2a 00000000 00000000 7efdf000 CallingConventions!wmainCRTStartup+0xd
08 002dfff0 00000000 00411082 00000000 000000c8 kernel32!BaseProcessStart+0x28
```

The calling sequence for it is:

```
stdcallFunction(0, 0x40000000, 1, 0x40001000, 2, 0x40002000) ->
cdeclFunction(0, 0x40000000, 1, 0x40001000, 2, 0x40002000) ->
fastcallFunction(0, 0x40000000, 1, 0x40001000, 2, 0x40002000) ->
A::thiscallFunction(0, 0x40000000, 1, 0x40001000, 2, 0x40002000)
```

and we see that only in the case of **fastcall** calling convention we have a discrepancy due to the fact that the first two parameters are passed not via the stack but through ECX and EDX:

```
0:000> ub 004114f9
CallingConventions!cdeclFunction+0x45
004114e5 push        ecx
004114e6 mov         edx,dword ptr [ebp+14h]
004114e9 push        edx
004114ea mov         eax,dword ptr [ebp+10h]
004114ed push        eax
004114ee mov         edx,dword ptr [ebp+0Ch]
004114f1 mov         ecx,dword ptr [ebp+8]
004114f4 call        CallingConventions!?ILT+475(?fastcallFunctionYIXHHHHHZ) (004111e0)
```

However, if we have full symbols we can see all parameters:

```
0:000> .frame 2
02 002df97c 004114f9 CallingConventions!fastcallFunction+0x69

0:000> dv /i /V
prv param 002df974 @ebp-0x08       a = 0
prv param 002df968 @ebp-0x14       b = 1073741824
prv param 002df984 @ebp+0x08       c = 1
prv param 002df988 @ebp+0x0c       d = 1073745920
prv param 002df98c @ebp+0x10       e = 2
prv param 002df990 @ebp+0x14       f = 1073750016
prv local 002df7c7 @ebp-0x1b5      obj = class A
prv local 002df7d0 @ebp-0x1ac      dummy = int [100]
```

How does dv command know about values in ECX and EDX which were definitely overwritten by later code? This is because the called function prolog saved them as local variables which you can notice as negative offsets for EBP register in dv output above:

```
0:000> uf CallingConventions!fastcallFunction
CallingConventions!fastcallFunction
32 00411560 push ebp
32 00411561 mov ebp,esp
32 00411563 sub esp,27Ch
32 00411569 push ebx
32 0041156a push esi
32 0041156b push edi
32 0041156c push ecx
32 0041156d lea edi,[ebp-27Ch]
32 00411573 mov ecx,9Fh
32 00411578 mov eax,0CCCCCCCCh
32 0041157d rep stos dword ptr es:[edi]
32 0041157f pop ecx
32 00411580 mov dword ptr [ebp-14h],edx
32 00411583 mov dword ptr [ebp-8],ecx
...
```

In order to spot the occurrences of this pattern, double checks and knowledge of calling conventions are required. Sometimes this pattern is a consequence of Optimized Code pattern (page 767).

x64 stack traces don't show any discrepancies except the fact that thiscall function parameters are shifted to the right:

```
0:000> kbl
RetAddr : Args to Child : Call Site
00000001`40001397 : cccccccc`cccccccc cccccccc`cccccccc cccccccc`cccccccc cccccccc`cccccccc : ntdll!DbgBreakPoint
00000001`40001233 : 00000000`0012fa94 cccccccc`cccccccc cccccccc`40000000 cccccccc`00000001 : CallingConventions!Ldr::thiscallFunction+0x37
00000001`40001177 : cccccccc`00000000 cccccccc`40000000 cccccccc`00000001 cccccccc`40001000 : CallingConventions!fastcallFunction+0x93
00000001`400010c7 : cccccccc`00000000 cccccccc`40000000 cccccccc`00000001 cccccccc`40001000 : CallingConventions!cdeclFunction+0x87
00000001`400012ae : cccccccc`00000000 cccccccc`40000000 cccccccc`00000001 cccccccc`40001000 : CallingConventions!stdcallFunction+0x87
00000001`400018ec : 00000001`00000001 00000000`00481a80 00000000`00000000 00000001`40002eee : CallingConventions!wmain+0x4e
00000001`4000173e : 00000000`00000000 00000000`00000000 00000000`00000000 00000000`0012ffa8 : CallingConventions!__tmainCRTStartup+0x19c
00000000`77d5964c : 00000000`77d59628 00000000`00000000 00000000`00000000 00000000`0012ffa8 : kernel32!BaseProcessStart+0xe
00000000`00000000 : 00000000`40001730 00000000`00000000 00000000`00000000 00000000`00000000 : kernel32!BaseProcessStart+0x29
```

How can this happen if the standard x64 calling convention passes the first 4 parameters via ECX, EDX, R8, and R9? This is because the called function prolog saved them on the stack (this might not be true in the case of optimized code):

```
0:000> uf CallingConventions!fastcallFunction
CallingConventions!fastcallFunction
32 00000001`400011a0 44894c2420 mov dword ptr [rsp+20h],r9d
32 00000001`400011a5 4489442418 mov dword ptr [rsp+18h],r8d
32 00000001`400011aa 89542410 mov dword ptr [rsp+10h],edx
32 00000001`400011ae 894c2408 mov dword ptr [rsp+8],ecx
...
```

A::thiscallFunction function passes this pointer via ECX too, and this explains the right shift of parameters.

Here is the C++ code we used for experimentation:

```cpp
#include "stdafx.h"
#include <windows.h>

void __stdcall stdcallFunction (int, int, int, int, int, int);
void __cdecl cdeclFunction (int, int, int, int, int, int);
void __fastcall fastcallFunction (int, int, int, int, int, int);

class A
{
public:
	void thiscallFunction (int, int, int, int, int, int) { DebugBreak(); }
};

void __stdcall stdcallFunction (int a, int b, int c, int d, int e, int f)
{
	int dummy[100] = {0};

	cdeclFunction (a, b, c, d, e, f);
}

void __cdecl cdeclFunction (int a, int b, int c, int d, int e, int f)
{
	int dummy[100] = {0};

	fastcallFunction (a, b, c, d, e, f);
}

void __fastcall fastcallFunction (int a, int b, int c, int d, int e, int f)
{
	int dummy[100] = {0};

	A obj;

	obj.thiscallFunction (a, b, c, d, e, f);
}

int _tmain(int argc, _TCHAR* argv[])
{
	stdcallFunction (0, 0x40000000, 1, 0x40001000, 2, 0x40002000);

	return 0;
}
```
