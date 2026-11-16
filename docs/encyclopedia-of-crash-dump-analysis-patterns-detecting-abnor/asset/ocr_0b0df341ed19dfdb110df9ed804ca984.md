# Crash Signature

This is one of the most common patterns. It consists of a set of attributes derivable from saved execution context for exceptions, faults, and traps. For example, on x64 Windows, it is usually RIP and RSP addresses. For x86, it is usually EIP, ESP, and EBP. It can also include the application module name.

```
0:009> !analyze -v

[...]

FAILURE_BUCKET_ID: SOFTWARE_NX_FAULT_c0000005_ApplicationA.exe!Unknown

BUCKET_ID: APPLICATION_FAULT_SOFTWARE_NX_FAULT_STACK_CORRUPTION_BAD_IP_ApplicationA+2d560

[...]

0:009> kl
ChildEBP RetAddr
0354f270 75bc0962 ntdll!NtWaitForMultipleObjects+0x15
0354f30c 76511662 KERNELBASE!WaitForMultipleObjectsEx+0x100
0354f354 76511921 kernel32!WaitForMultipleObjectsExImplementation+0xe0
0354f370 76539b0d kernel32!WaitForMultipleObjects+0x18
0354f3dc 76539baa kernel32!WerpReportFaultInternal+0x186
0354f3f0 765398d8 kernel32!WerpReportFault+0x70
0354f400 76539855 kernel32!BasepReportFault+0x20
0354f48c 77750727 kernel32!UnhandledExceptionFilter+0x1af
0354f494 77750604 ntdll!_RtlUserThreadStart+0x62
0354f4a8 777504a9 ntdll!_Eh4_CallFilterFunc+0x12
0354f4d0 777387b9 ntdll!_except_handler4+0x8e
0354f4f4 7773878b ntdll!ExecuteHandler2+0x26
0354f544 776f010f ntdll!ExecuteHandler+0x24
0354f54a 0354f958 ntdll!KiUserExceptionDispatcher+0xf
WARNING: Frame IP not in any known module. Following frames may be wrong.
0354f908 02ff0340 0x354f958
00000000 00000000 0x2ff0340

0:009> kv
ChildEBP RetAddr Args to Child
[...]
0354f54a 0354f958 0154f5bc 0354f60c 0354f5bc ntdll!KiUserExceptionDispatcher+0xf (CONTEXT @ 0354f60c)
WARNING: Frame IP not in any known module. Following frames may be wrong.
0354f908 02ff0340 00000000 00000000 00000000 0x354f958
00000000 00000000 00000000 00000000 00000000 0x2ff0340

0:009> .cxr 0354f60c
eax=80010105 ebx=0354f924 ecx=00000003 edx=0000ffff esi=00d7dce0 edi=00d7e0c8
eip=0354f958 esp=0354f8f4 ebp=0354f908 iopl=0 nv up ei pl zr na pe nc
cs=0023 ss=002b ds=002b es=002b fs=0053 gs=002b efl=00010246
0354f958 64f9 stc
```