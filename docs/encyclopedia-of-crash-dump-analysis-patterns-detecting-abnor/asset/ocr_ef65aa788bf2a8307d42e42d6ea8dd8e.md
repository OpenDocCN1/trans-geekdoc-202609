# # Data

This is a special version of the more general Invalid Pointer pattern (page 589) like NULL Code Pointer (page 750). The effective address is below 0xFFFF, and it is usually a register with 0 value and a small offset, for example:

```
0: kd> r
Last set context:
eax=8923b008 ebx=00000000 ecx=00000000 edx=8923b008 esi=891312d0 edi=89f0b300
eip=8081c7c4 esp=f1b5d744 ebp=f1b5d744 iopl=0 nv up ei ng nz ac pe nc
cs=0008 ss=0010 ds=0023 es=0023 fs=0030 gs=0000 efl=00010296
nt!IopIoOperationSynchronous+0x2e:
8081c7c4 f6412c02 test byte ptr [ecx+2Ch],2 ds:0023:0000002c=?
```

Here, after disassembling the function backward, we see the succession of dereferences starting from [EBP+8] and this means that a pointer to a structure (an IRP here) was passed to the function, and it had a data pointer in it, pointing to another structure and the latter contained a NULL pointer:

```
0: kd> ub 8081c7c4
nt!IopIoOperationSynchronous:
8081c7b6 8bff mov edi,edi
8081c7b8 55 push ebp
8081c7b9 8bec mov ebp,esp
8081c7bb 8b4508 mov eax,dword ptr [ebp+8]
8081c7be 8b4860 mov ecx,dword ptr [eax+60h]
8081c7c1 8b4918 mov ecx,dword ptr [ecx+18h]
```

# # Comments

x64 example that also shows .cxr command in x64 context:

```
0:006> k
# Child-SP RetAddr Call Site
00 000000a9`be019378 00007ffe`1b1198f8 ntdll!NtWaitForMultipleObjects+0xa
01 000000a9`be019380 00007ffe`1b11908e KERNELBASE!WaitForMultipleObjectsEx+0xef
02 000000a9`be019680 00007ffe`1b92155c KERNELBASE!WaitForMultipleObjects+0xe
03 000000a9`be0196c0 00007ffe`1b921088 kernel32!BasepReportFault+0x54c
04 000000a9`be019c30 00007ffe`1b1403cd kernel32!BasepReportFault+0x78
05 000000a9`be019c60 00007ffe`1dd8df6f KERNELBASE!UnhandledExceptionFilter+0x1fd
06 000000a9`be019d60 00007ffe`1dd65680 ntdll!LdrpLogFatalUserCallbackException+0x56
07 000000a9`be019e90 00007ffe`1dd6666d ntdll!KiUserCallbackDispatcherHandler+0x20
08 000000a9`be019ed0 00007ffe`1dde3c00 ntdll!RtlpExecuteHandlerForException+0xd
09 000000a9`be019f00 00007ffe`1dd6577a ntdll!RtlDispatchException+0x370
0a 000000a9`be01a600 00007ffd`f98e8f69 ntdll!KiUserExceptionDispatch+0x3a
0b 000000a9`be01ad00 00007ffd`f985c944 edgehtml!CWebPlatformTridentHost::LoadNewWindowContent+0x35
0c 000000a9`be01ad90 00007ffe`1b84b0b3 edgehtml!CWebPlatform::LoadNewWindowContent+0x64
0d 000000a9`be01ae10 00007ffe`1b80521e rpcrt4!Invoke+0x73
0e 000000a9`be01aea0 00007ffe`1b83aaba rpcrt4!NdrStubCall2+0x34e
0f 000000a9`be01b4f0 00007ffe`1d414b1b rpcrt4!NdrStubCall3+0xea
10 000000a9`be01b560 00007ffe`1d4c25b2 combase!CStdStubBuffer_Invoke+0x6b
```