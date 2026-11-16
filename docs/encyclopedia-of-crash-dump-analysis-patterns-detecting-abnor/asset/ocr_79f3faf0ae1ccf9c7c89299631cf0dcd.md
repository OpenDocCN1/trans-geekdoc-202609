```
...
...
2709ff84 77b9b530 26658fb0 00000000 00000000 ComponentC!foo+0x18d
2709ffb8 7c82608b 26d9af70 00000000 00000000 msvcrt!_endthreadex+0xa3
2709ffec 00000000 77b9b4bc 26d9af70 00000000 kernel32!BaseThreadStart+0x34
```

We see that the thread C makes another LPC call (MessageId 000135e) and waiting for a reply. Let's find the server thread processing the message (thread D):

```
1: kd> !lpc message 000135ea
Searching message 135ea in threads ...
Client thread 89d08bb8 waiting a reply from 135ea
Server thread 89010020 is working on message 135ea
...
...
...
1: kd> !thread 89010020 16
THREAD 89010020 Cid 09b4.1530 Teb: 7ff93000 Win32Thread: 00000000 WAIT: (Unknown) UserMode Non-Alertable
8903ba28 Mutant - owning thread 89143020
Not impersonating
DeviceMap d64028f0
Owning Process 891b8b80 Image: svchost.exe
Wait Start TickCount 237641 Ticks: 1657 (0:00:00:25.890)
Context Switch Count 8
UserTime 00:00:00.000
KernelTime 00:00:00.000
Win32 Start Address 0x000135ea
LPC Server thread working on message Id 135ea
Start Address kernel32!BaseThreadStartThunk (0x7c82b5f3)
Stack Init b9455000 Current b9454c60 Base b9455000 Limit b9452000 Call 0
Priority 9 BasePriority 8 PriorityDecrement 0
ChildEBP RetAddr Args to Child
b9454c78 8083e6a2 89010098 89010020 890100c8 nt!KiSwapContext+0x26
b9454ca4 8083f164 00000000 00000000 00000000 nt!KiSwapThread+0x284
b9454cec 8092d7b0 8903ba28 00000006 00000001 nt!KeWaitForSingleObject+0x346
b9454d50 80834d3f 0000514 00000000 00000000 nt!NtWaitForSingleObject+0x9a
b9454d50 7c94ed54 00000514 00000000 00000000 nt!KiFastCallEntry+0fc
02b5f720 7c942124 75fdbe44 00000514 00000000 ntdll!KiFastSystemCallRet
02b5f724 75fdbe44 00000514 00000000 00000000 ntdll!NtWaitForSingleObject+0xc
02b5f744 75fdc57f 000e6014 000da62c 02b5fc0a ComponentD!bar+0x42
...
...
...
02b5f8c8 77c40f3b 0000da48 02b5fc90 00000001 ComponentD!foo+0x49
02b5f8f8 77cb23f7 75fdf8f2 02b5fae0 00000007 RPCRT4!Invoke+0x30
02b5fc8f 77cb26ed 00000000 00000000 00d4f24 RPCRT4!NdrStubCall2+0x299
02b5fd14 77c409be 00004f24 000b5d70 0000d4f24 RPCRT4!NdrServerCall11+0x19
02b5fd48 77c4093f 75fff834 000d4f24 02b5fdec RPCRT4!DispatchToStubInCNoAvrf+0x38
02b5fd9c 77c40865 00000005 00000000 7600589c RPCRT4!RPC_INTERFACE::DispatchToStubWorker+0x117
02b5fd0c 77c434b1 000d4f24 00000000 7600589c RPCRT4!RPC_INTERFACE::DispatchToStub+0xa3
02b5fdff 77c41bb3 000d3550 000a7800 0105d4b8 RPCRT4!LRPC_SCALL::DealWithRequestMessage+0x42c
02b5fe20 77c45458 000a7908 02b5fe38 000d3550 RPCRT4!LRPC_ADDRESS::DealWithLRPCRequest+0x127
02b5ff84 77c27788 02b5ffac 77c2f7dd 000a78d0 RPCRT4!LRPC_ADDRESS::ReceiveLotsaCalls+0x430
```