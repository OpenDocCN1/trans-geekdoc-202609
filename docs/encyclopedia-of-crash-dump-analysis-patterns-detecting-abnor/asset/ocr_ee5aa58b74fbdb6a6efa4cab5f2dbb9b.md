```
0:003> kL
# Child-SP RetAddr Call Site
00 0000005b`056ae1f8 00007ffa`e2f2916f ntdll!NtWaitForMultipleObjects+0xa
01 0000005b`056ae200 00007ffa`e2f2906e KERNELBASE!WaitForMultipleObjectsEx+0xef
02 0000005b`056ae500 00007ffa`e3b5155c KERNELBASE!WaitForMultipleObjects+0xe
03 0000005b`056ae540 00007ffa`e3b51088 kernel32!WerpReportFaultInternal+0x494
04 0000005b`056aeab0 00007ffa`e2f503ad kernel32!WerpReportFault+0x48
05 0000005b`056aeae0 00007ffa`e5c58cd2 KERNELBASE!UnhandledExceptionFilter+0x1fd
06 0000005b`056aebe0 00007ffa`e5c44296 ntdll!RtlUserThreadStart$filt$0+0x3e
07 0000005b`056aec20 00007ffa`e5c5666d ntdll!_C_specific_handler+0x96
08 0000005b`056aec90 00007ffa`e5bd3c00 ntdll!RtlpExecuteHandlerForException+0xd
09 0000005b`056aecc0 00007ffa`e5c5577a ntdll!RtlDispatchException+0x370
0a 0000005b`056af3c0 00000000`00000000 ntdll!KiUserExceptionDispatch+0x3a
```

We can look at the trap frame RSP address and recover the return address:

```
0:003> dt _KTRAP_FRAME RSP 0000005b`056af7e8
ntdll!_KTRAP_FRAME
+0x180 Rsp : 0x0000005b`056afad8
0:003> dps 0x0000005b`056afad8 L1
0000005b`056afad8  00007ff7`f6381266 ApplicationM!thread_two+0x16
0:003> ub 00007ff7`f6381266
[...]
ApplicationM!thread_two:
00007ff7`f6381250 48894c2408        mov qword ptr [rsp+8],rcx
00007ff7`f6381255 4883ec38          sub rsp,38h
00007ff7`f6381259 48c744242000000000 mov qword ptr [rsp+20h],0
00007ff7`f6381262 ff542420          call qword ptr [rsp+20h]
```

and reconstruct the bottom of the stack trace:

```
0:003> k L=0x0000005b`056afad8
# Child-SP RetAddr Call Site
00 0000005b`056afad8  00007ff7`f6381266 ntdll!NtWaitForMultipleObjects+0xa
01 0000005b`056afae0  00007ff7`f6382bd1 ApplicationM!thread_two+0x16
02 (Inline Function) -------- ApplicationM!invoke_thread_procedure+0xe
03 0000005b`056afb20 00007ffa`e3b42d92 ApplicationM!thread_start+0x5d
04 0000005b`056afb50 00007ffa`e5bc9f64 kernel32!BaseThreadInitThunk+0x22
05 0000005b`056afb80 00000000`00000000 ntdll!RtlUserThreadStart+0x34
```

and then construct Glued Stack Trace (page 413):

```
0000005b`056ae1f8 00007ffa`e2f2916f ntdll!NtWaitForMultipleObjects+0xa
0000005b`056ae200 00007ffa`e2f2906e KERNELBASE!WaitForMultipleObjectsEx+0xef
0000005b`056ae500 00007ffa`e3b5155c KERNELBASE!WaitForMultipleObjects+0xe
0000005b`056ae540 00007ffa`e3b51088 kernel32!WerpReportFaultInternal+0x494
0000005b`056aeab0 00007ffa`e2f503ad kernel32!WerpReportFault+0x48
0000005b`056aeae0 00007ffa`e5c58cd2 KERNELBASE!UnhandledExceptionFilter+0x1fd
0000005b`056aebe0 00007ffa`e5c44296 ntdll!RtlUserThreadStart$filt$0+0x3e
0000005b`056aec20 00007ffa`e5c5666d ntdll!_C_specific_handler+0x96
0000005b`056aec90 00007ffa`e5bd3c00 ntdll!RtlpExecuteHandlerForException+0xd
0000005b`056aecc0 00007ffa`e5c5577a ntdll!RtlDispatchException+0x370
```