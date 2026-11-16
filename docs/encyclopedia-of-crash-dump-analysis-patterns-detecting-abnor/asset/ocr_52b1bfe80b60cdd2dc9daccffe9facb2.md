Therefore [RBX+28] contains SharedSemaphore field that is assigned to RCX as a first parameter to NtWaitForSingleObject. The similar fragment of RtlAcquireResourceExclusive has [RBX+38] which 0x10 further than 0x28 and corresponds to ExclusiveSemaphore handle field:

```
ntdll!RtlAcquireResourceExclusive+0xd2:
00000000`770c2a12 488b4b38        mov     rcx,qword ptr [rbx+38h]
00000000`770c2a16 4c8bc6          mov     r8,rsi
00000000`770c2a19 33d2            xor     edx,edx
00000000`770c2a1b e8d0e84000      call    ntdll!NtWaitForSingleObject (00000000`771112f0)
00000000`770c2a20 3d02010000      cmp     eax,102h
00000000`770c2a25 0f8401c60600      je      ntdll ?? ::FNODOBFM::`string'+0x12591 (00000000`7712f02c)
```

So we just need to know the value of RBX and dump the structure to find OwningThread field. We can either calculate it from RSP or use /c switch with .frame command:

```
0: kd> kn
*** Stack trace for last set context - .thread/.cxr resets it
# Child-SP          RetAddr           Call Site
00 ffffff800`0e870940 ffffff800`01c76972 nt!KiSwapContext+0x7a
01 ffffff800`0e870a80 ffffff800`01c8d748 nt!KiCommitThreadWait+0x1d2
02 ffffff800`0e870b10 ffffff800`01f7b2be nt!KeWaitForSingleObject+0x19f
03 ffffff800`0e870bb0 ffffff800`01c801d3 nt!NtWaitForSingleObject+0xde
04 fffffff800`0e870c20 00000000`773912fa nt!KiSystemServiceCopyEnd+0x13
05 00000000`22ae6c8 00000000`773470b4 ntdll!NtWaitForSingleObject+0xa
06 00000000`022ae6d0 00000000`ff4013a3 ntdll!RtlAcquireResourceShared+0xd0
07 00000000`022ae710 00000000`ff401675 lsm!CAutoSharedLock::<AutoSharedLock+0x61
08 00000000`022ae7e0 00000000`ff402c68 lsm!CTSSession::getTerminal+0x21
09 00000000`022ae820 0000007fe`fd8bff85 lsm!RpcGetEnumResult+0x202
0a 00000000`022ae980 0000007fe`fd8b4de2 RPCRT4!Invoke+0x65
0b 00000000`022ae9e0 0000007fe`fd8b17bd RPCRT4!NdrStubCall2+0x32a
0c 00000000`022aef00 0000007fe`fd8b3254 RPCRT4!NdrServerCall2+0x1d
0d 00000000`022af030 0000007fe`fd8b33b6 RPCRT4!DispatchToStubInCNoAvrf+0x14
0e 00000000`022af060 0000007fe`fd8b3aa RPCRT4!RPC_INTERFACE::DispatchToStubWorker+0x146
0f 00000000`022af180 0000007fe`fd8b375d RPCRT4!LRPC_SCALL::DispatchRequest+0x149
10 00000000`022af260 0000007fe`fd8d09ff RPCRT4!LRPC_SCALL::HandleRequest+0x20d
11 00000000`022af390 0000007fe`fd8b05b5 RPCRT4!LRPC_ADDRESS::ProcessIO+0x3bf
12 00000000`022af4d0 00000000`7735b6bb RPCRT4!LrpIoComplete+0xa5
13 00000000`022af560 00000000`7735ff2f ntdll!TppAlpcpExecuteCallback+0x26b
14 00000000`022af5f0 00000000`7713652d ntdll!TppWorkerThread+0x3f8
15 00000000`022af8f0 00000000`7736c541 kernel32!BaseThreadInitThunk+0xd
16 00000000`022af920 00000000`00000000 ntdll!RtlUserThreadStart+0x1d
```

```
0: kd> .frame /c 6
06 00000000`022ae6d0 00000000`ff4013a3 ntdll!RtlAcquireResourceShared+0xd0
rax=0000000000000000 rbx=00000000023ac128 rcx=0000000000000000
rdx=0000000000000000 rsi=0000000077472410 rdi=0000000000000001
rip=00000000773470b4 rsp=00000000022ae6d0 rbp=0000000000000000
r8=0000000000000000 r9=0000000000000000 r10=0000000000000000
r11=0000000000000000 r12=29406b2a1a85bd43 r13=0000000000000009
r14=000000000000000c r15=00000000022aef20
iopl=0         nv up di pl nz na po nc
cs=0000  ss=0000  ds=0000  es=0000  fs=0000  gs=0000             efl=00000000
ntdll!RtlAcquireResourceShared+0xd0:
00000000`773470b4 3d02010000      cmp     eax,102h
```