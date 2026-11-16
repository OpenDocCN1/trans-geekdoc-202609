

- RTL_CRITICAL_SECTION 锁
- HANDLE 共享信号量
- ULONG 共享等待者
- HANDLE 独占信号量
- ULONG 独占等待者
- LONG 活跃数量
- HANDLE 拥有线程
- ULONG 超时提升
- PVOID 调试信息

为双重检查，我们反汇编 RtlAcquireResourceShared 并检查来自 NtWaitForSingleObject 调用的返回地址 (00000000`773470b4)：

```
0: kd> .thread /r /p fffffa8052d66000
Implicit thread is now fffffa80`52d66060
Implicit process is now fffffa80`4a16b260
Loading User Symbols
................
0: kd> uf ntdll!RtlAcquireResourceShared
[...]
ntdll!RtlAcquireResourceShared+0xc2:
00000000`773470a6 4888b428 mov rcx,qword ptr [rbx+28h]
00000000`773470aa 4c8bc6 mov r8,rsi
00000000`773470ad 33d2 xor edx,edx
00000000`773470af e83ca20400 call ntdll!NtWaitForSingleObject (00000000`773912f0)
00000000`773470b4 3d02010000 cmp eax,102h
00000000`773470b9 0f8402080600 je ntdll! ?? ::FNODOBFM::`string'+0x12629 (00000000`773af0c1)
[...]
ntdll!RtlAcquireResourceShared:
00000000`77352af0 48895c2420 mov qword ptr [rsp+20h],rbx
00000000`77352af4 57 push rdi
00000000`77352af5 4883ec30 sub rsp,30h
00000000`77352afa 448b4944 mov r9d,dword ptr [rcx+44h]
00000000`77352afe 0fb6fa movzx edi,dl
00000000`77352b01 488bd9 mov rbx,rcx
00000000`77352b04 4585c9 test r9d,r9d
00000000`77352b07 0f88a7000000 js ntdll!RtlAcquireResourceShared+0x65 (00000000`77352bb4)
[...]
```

我们可以看到句柄从 [RBX+28] 获取，并且可以看到 RBX 在函数序言中被保存，然后 RCX 的值被赋给了 RBX。RCX 作为调用约定的第一个参数，应该是指向 RTL_RESOURCE 的指针，该结构体以 RTL_CRITICAL_SECTION 作为第一个成员，其大小为 0x28：

0: kd> dt ntdll!_RTL_CRITICAL_SECTION

| 偏移 | 字段 | 类型 |
|------|------|------|
| +0x000 | 调试信息 | Ptr64 _RTL_CRITICAL_SECTION_DEBUG |
| +0x008 | 锁计数 | Int4B |
| +0x00c | 递归计数 | Int4B |
| +0x010 | 拥有线程 | Ptr64 Void |
| +0x018 | 锁信号量 | Ptr64 Void |
| +0x020 | 自旋计数 | Uint8B |

因此 [RBX+28] 包含共享信号量字段，该字段作为第一个参数赋给 RCX 传递给 NtWaitForSingleObject。RtlAcquireResourceExclusive 的类似片段具有 [RBX+38]，它比 0x28 多 0x10，对应独占信号量句柄字段：

```
ntdll!RtlAcquireResourceExclusive+0xd2:
00000000`770c2a12 488b4b38        mov     rcx,qword ptr [rbx+38h]
00000000`770c2a16 4c8bc6          mov     r8,rsi
00000000`770c2a19 33d2            xor     edx,edx
00000000`770c2a1b e8d0e84000      call    ntdll!NtWaitForSingleObject (00000000`771112f0)
00000000`770c2a20 3d02010000      cmp     eax,102h
00000000`770c2a25 0f8401c60600      je      ntdll ?? ::FNODOBFM::`string'+0x12591 (00000000`7712f02c)
```

因此，我们只需要知道 RBX 的值并转储结构体以查找拥有线程字段。我们可以从 RSP 计算它，或者使用 .frame 命令的 /c 开关：

```
0: kd> kn
*** Stack trace for last set context - .thread/.cxr resets it
# Child-SP          RetAddr           Call Site
00 fffff800`0e870940 fffff800`01c76972 nt!KiSwapContext+0x7a
01 fffff800`0e870a80 fffff800`01c8d748 nt!KiCommitThreadWait+0x1d2
02 fffff800`0e870b10 fffff800`01f7b2be nt!KeWaitForSingleObject+0x19f
03 fffff800`0e870bb0 fffff800`01c801d3 nt!NtWaitForSingleObject+0xde
04 fffff800`0e870c20 00000000`773912fa nt!KiSystemServiceCopyEnd+0x13
05 00000000`022ae6c8 00000000`773470b4 ntdll!NtWaitForSingleObject+0xa
06 00000000`022ae6d0 00000000`ff4013a3 ntdll!RtlAcquireResourceShared+0xd0
07 00000000`022ae710 00000000`ff401675 lsm!CAutoSharedLock::<AutoSharedLock+0x61
08 00000000`022ae7e0 00000000`ff402c68 lsm!CTSSession::getTerminal+0x21
09 00000000`022ae820 0000007fe`fd8bff85 lsm!RpcGetEnumResult+0x202
0a 00000000`022ae980 0000007fe`fd8b4de2 RPCRT4!Invoke+0x65
0b 00000000`022ae9e0 0000007fe`fd8b17bd RPCRT4!NdrStubCall2+0x32a
0c 00000000`022aef00 0000007fe`fd8b3254 RPCRT4!NdrServerCall2+0x1d
0d 00000000`022af030 0000007fe`fd8b33b6 RPCRT4!DispatchToStubInCNoAvrf+0x14
0e 00000000`022af060 0000007fe`fd8b3aa9 RPCRT4!RPC_INTERFACE::DispatchToStubWorker+0x146
0f 00000000`022af180 0000007fe`fd8b375d RPCRT4!LRPC_SCALL::DispatchRequest+0x149
10 00000000`022af260 0000007fe`fd8d09ff RPCRT4!LRPC_SCALL::HandleRequest+0x20d
11 00000000`022af390 00000000`7735b6bb RPCRT4!LrpIoComplete+0xa5
12 00000000`022af560 00000000`7735ff2f ntdll!TppAlpcpExecuteCallback+0x26b
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
r8=0000000000000000 r9=0000000000000000 r10=00000000`00000000
r11=0000000000000000 r12=29406b2a1a85bd43 r13=0000000000000009
r14=000000000000000c r15=00000000022aef20
iopl=0         nv up di pl nz na po nc
cs=0000  ss=0000  ds=0000  es=0000  fs=0000  gs=0000             efl=00000000
ntdll!RtlAcquireResourceShared+0xd0:
00000000`773470b4 3d02010000      cmp     eax,102h
```

```
0: kd> dp rbx+28 L10
00000000`023ac150 00000000`00001244 00000000`000001b5
00000000`023ac160 00000000`0000f3fc ffffffff`00000000
00000000`023ac170 00000000`000021ac 00000000`00000000
00000000`023ac180 00000000`02735fc0 00000000`00000001
00000000`023ac190 00000000`00000000 01cf07ac`9fa06d27
00000000`023ac1a0 00000000`00000000 00000000`00000000
00000000`023ac1b0 ffffffff`ffffffff 00000000`00000000
00000000`023ac1c0 00000000`00000000 00000000`00000000
```

我们检查所有这些句柄（拥有线程似乎更早出现，且缺少活跃数量字段，但这可能只是 ReactOS 中旧 x86 结构与 x64 Windows 之间的差异）：

```
0: kd> !handle 00000000`00001244

PROCESS fffff8a04a16b260
SessionId: 0 Cid: 03c0    Peb: 7fffffdc000  ParentCid: 0350
DirBase: 195950000  ObjectTable: fffff8a0032424e0  HandleCount: 5252.
Image: lsm.exe

Handle table at fffff8a0032424e0 with 5252 entries in use

1244: Object: fffff8a04a79ad50  GrantedAccess: 00100003 Entry: fffff8a022b39910
Object: fffff8a04a79ad50  Type: (fffff8a048fc8790) Semaphore
ObjectHeader: fffff8a04a79ad20 (new version)
HandleCount: 1  PointerCount: 438
```

```
0: kd> !handle 00000000`00000f3c

PROCESS fffff8a04a16b260
SessionId: 0 Cid: 03c0    Peb: 7fffffdc000  ParentCid: 0350
DirBase: 195950000  ObjectTable: fffff8a0032424e0  HandleCount: 5252.
Image: lsm.exe

Handle table at fffff8a0032424e0 with 5252 entries in use

0f3c: Object: fffff8a04fa81f60  GrantedAccess: 00100003 Entry: fffff8a02cd3ecf0
Object: fffff8a04fa81f60  Type: (fffff8a048fc8790) Semaphore
ObjectHeader: fffff8a04fa81f30 (new version)
HandleCount: 1  PointerCount: 1
```

```
0: kd> !thread -t 00000000`000021a0 1f
THREAD fffff8a04d5d1b0 Cid 03c0.21a0 Teb: 000007fffff9c000 Win32Thread: 0000000000000000 WAIT: (WrLpcReply) UserMode Non-Alertable
fffff8a04d5d5578 Semaphore Limit 0x1
Waiting for reply to ALPC Message fffff8a02c9a9500 : queued at port fffff8a04ac4e7d0 : owned by process fffff8a04acd8730
Not impersonating
DeviceMap fffffa0000088c0
Owning Process fffff8a04a1b6260 Image: lsm.exe
Attached Process N/A Image: N/A
Wait Start TickCount 73337319 Ticks: 1466453 (0:06:21:53.328)
Context Switch Count 69 IdealProcessor: 1
UserTime 00:00:00.000
KernelTime 00:00:00.000
Win32 Start Address ntdll!TppWorkerThread (0x000000007735fbf0)
Stack Init fffff8a00aa1fdb0 Current fffff8a00aa1f600
Base fffff8a00aa20000 Limit fffff8a00aa1a000 Call 0
Priority 9 BasePriority 8 UnusualBoost 0 ForegroundBoost 0 IoPriority 2 PagePriority 5
Kernel stack not resident.

Child-SP RetAddr Call Site
fffff880`0aalf640 fffff800`01c76972 nt!KiSwapContext+0x7a
fffff880`0aalf780 fffff800`01c87d8f nt!KiCommitThreadWait+0x1d2
fffff880`0aalf810 fffff800`01ca25af nt!KeWaitForSingleObject+0x19f
fffff880`0aalf8b0 fffff800`01f96b6b nt!AlpcpSignalAndWait+0x8f
fffff880`0aalf960 fffff800`01f95fb0 nt!AlpcpReceiveSynchronousReply+0x46
fffff880`0aalf9c0 fffff800`01f93dab nt!AlpcpProcessSynchronousRequest+0x33d
fffff880`0aalfb00 fffff800`01c801d3 nt!NtAlpcSendWaitReceivePort+0x1ab
fffff880`0aalfbb0 00000000`77391bda nt!KiSystemServiceCopyEnd+0x13 (TrapFrame @ fffff880`0aalfc20)
00000000`01dddb48 000007fe`fd8c8306 ntdll!ZwAlpcSendWaitReceivePort+0xa
00000000`01dddb50 000007fe`fd8c2a02 RPCRT4!RPC_CCALL::SendReceive+0x156
00000000`01dddc10 000007fe`fd5b28c0 RPCRT4!_RpcSendReceive+0x42
00000000`01dddc40 000007fe`ff5b282f ole32!ThreadSendReceive+0x40
[d: w7rtm\com\ole32\com\dcomrem\channelb.cxx @ 5003]
00000000`01dddc90 000007fe`ff5b265b ole32!CRpcChannelBuffer::SwitchAptAndDispatchCall+0xa3
[d: w7rtm\com\ole32\com\dcomrem\channelb.cxx @ 4454]
00000000`01dddd30 000007fe`ff46daaa ole32!CRpcChannelBuffer::SendReceive2+0x11b
[d: w7rtm\com\ole32\com\dcomrem\channelb.cxx @ 4074]
00000000`01dddef0 000007fe`ff46da0c ole32!CAptRpcChnl1::SendReceive+0x52
[d: w7rtm\com\rpc\ndrole\proxy.cxx @ 1932]
00000000`01dddfc0 000007fe`ff5b205d ole32!CCtxComChnl::SendReceive+0x68
[d: w7rtm\com\rpc\ndrole\ctxchnl.cxx @ 734]
00000000`01dde070 000007fe`fd96b949 ole32!NdrExtpProxySendReceive+0x45 [d: w7rtm\com\rpc\ndrole\proxy.cxx @ 1932]
00000000`01dde0a0 000007fe`ff5b21d0 RPCRT4!NdrpClientCall3+0x2e2
00000000`01dde360 000007fe`ff46d8a2 ole32!ObjectStublessClient+0x11d
[d: w7rtm\com\rpc\ndrole\amd64\stblsclt.cxx @ 621]
00000000`01dde6f0 00000000`ff417d26 ole32!ObjectStubless+0x42 [d: w7rtm\com\rpc\ndrole\amd64\stubless.asm @ 117]
00000000`01dde740 00000000`ff4186ba lsm!CTSSession::Disconnect+0x3a5
00000000`01dde810 0000007fe`fd8bff85 lsm!RpcDisconnect+0x15e
00000000`01dde850 0000007fe`fd96b68e RPCRT4!Invoke+0x65
00000000`01dde8a0 0000007fe`fd8a92e0 RPCRT4!Ndr64StubWorker+0x61b
00000000`01ddee60 0000007fe`fd8b3254 RPCRT4!NdrServerCallAll+0x40
00000000`01ddeeb0 0000007fe`fd8b33b6 RPCRT4!DispatchToStubInCNoAvrf+0x14
00000000`01ddeee0 0000007fe`fd8b3aa9 RPCRT4!RPC_INTERFACE::DispatchToStubWorker+0x146

