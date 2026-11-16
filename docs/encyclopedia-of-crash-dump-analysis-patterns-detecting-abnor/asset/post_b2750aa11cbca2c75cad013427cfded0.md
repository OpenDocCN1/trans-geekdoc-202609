
The first parameter is KAFFINITY mask, and 0x2 is 0b10 (binary) which is the second core. This thread had been already set to run on that core only:

```
0: kd> dt _KTHREAD 8b3b08b8
nt!_KTHREAD
    +0x000 Header             : _DISPATCHER_HEADER
    ...
    +0x124 Affinity           : 2
    ...
```

Let's look at our second core:

```
0: kd> ~1s
1: kd> kl 100
ChildEBP RetAddr
a8f00618 acd21947 hal!KeAcquireInStackQueuedSpinLock+0x43
a8f00618 acd21947 tcpip!IndicateData+0x98
a8f00684 acd173e5 tcpip!IndicateData+0x98
a8f0070c acd14e5 tcpip!TCPRcv+0xbb0
a8f0076c acd14b19 tcpip!DeliverToUser+0x18e
a8f007e8 acd14836 tcpip!DeliverToUserEx+0x95e
a8f008a0 acd13928 tcpip!IPRcvPacket+0x6cb
a8f008e0 acd13853 tcpip!ARPRcvIndicateNew+0x149
a8f0091c ba56be45 tcpip!ARPRcvPacket+0x68
a8f00970 b635801d NDIS!ethFilterDprIndicateReceivePacket+0x307
a8f00984 b63581b4 psched!PsFlushReceiveQueue+0x15
a8f009a8 b63585f9 psched!PsEnqueueReceivePacket+0xda
a8f009c0 ba56c8ed psched!ClReceiveComplete+0x13
a8f009d8 b7defdb8 NDIS!EthFilterDprIndicateReceiveComplete+0x7c
a8f00a08 b7df0f78 driverA+0x17db5
a8f00a64 ba55ec2c driverA+0x18f78
a8f00a88 bb09962c NDIS!ndisMSendCompleteX+0x8d
a8f00a9c b6b0a36d driverB+0x62c
a8f00aab ba55e88f driverB+0x13d6
a8f00ae0 b7de003c NDIS!NdisReturnPackets+0xe9
a8f00af0 ba55e88f driverA+0x803c
a8f00b18 b6358061 NDIS!NdisReturnPackets+0xe9
a8f00b30 ba55e88f psched!MpReturnPacket+0x3b
a8f00b58 acc877cc NDIS!NdisReturnPackets+0xe9
87749da0 00000000 afd!AfdReturnBuffer+0xe1
1: kd> r
eax=a8f005f8 ebx=a8f00624 ecx=8a9862ed edx=a8f00b94 esi=874e2ed0 edi=8a9862d0
eip=806e6a33 esp=a8f005ec ebp=a8f00618 iopl=0 nv up ei pl nz na po nc
cs=0008 ss=0010 ds=0023 es=0023 fs=0030 gs=0000 efl=00000202
hal!KeAcquireInStackQueuedSpinLock+0x43:
806e6a33 74ee je hal!KeAcquireInStackQueuedSpinLock+0x33 (806e6a23) [br=0]
```

1: kd> !running

System Processors 3 (affinity mask)
Idle Processors 1

PrCb Current Next
1 bab38120 8a0c8ae8 8b3a7318 .......
```

We see the thread 8a0c8ae8 had been spinning on the second core for more than 2 minutes:

```
1: kd> !thread 8a0c8ae8 1f
THREAD 8a0c8ae8 Cid 0660.0124 Teb: 7ffd7000 Win32Thread: e338c498 RUNNING on processor 1
IRP List:
8a960008: (0006,01b4) Flags: 00000900 Mdl: 87535908
Not impersonating
DeviceMap e2f155b8
Owning Process 87373020 Image: APPLICATION.EXE
Wait Start TickCount 43918 Ticks: 9245 (0:00:02:24.453)
Context Switch Count 690 LargeStack
UserTime 00:00:00.000
KernelTime 00:02:24.453
...
```

Its kernel time looks consistent with the starved thread waiting time:

```
0: kd> !thread 8b3b08b8 1f
THREAD 8b3b08b8 Cid 0004.002c Teb: 00000000 Win32Thread: 00000000 READY
Not impersonating
DeviceMap e1009248
Owning Process 8b3b2830 Image: System
Wait Start TickCount 44419 Ticks: 8744 (0:00:02:16.625)
...
```

For comparison, the spinning thread has affinity mask 0b11 (0x3) which means that it could be scheduled to run on both cores:

```
0: kd> dt _KTHREAD 8a0c8ae8
nt!_KTHREAD
+0x000 Header : _DISPATCHER_HEADER
...
+0x124 Affinity : 3
...
```

## Annotated Disassembly

## JIT .NET Code

When disassembling JIT code, it is good to see annotated function calls with full type and token information:

```
0:000> !CLRStack
OS Thread Id: 0xbf8 (0)
ESP         EIP
001fef90 003200a4 ClassMain.DoWork()
001fef94 00320082 ClassMain.Main(System.String[])
001ff1b0 79e7c74b [GCFrame: 001ff1b0]

0:000> !U 00320082
Normal JIT generated code
ClassMain.Main(System.String[])
Begin 00320070, size 13
00320070 b960300000   mov ecx,0D3060h (MT: ClassMain)
00320075 e8a21fdaff   call 000c201c (JitHelp: CORINFO_HELP_NEWSFAST)
0032007a 8bc8         mov ecx,eax
0032007c ff159c300d00 call dword ptr ds:[0D309Ch] (ClassMain.DoWork(), mdToken: 06000002)
>> 00320082 c3         ret
```

However, this doesn't work when we disable the output of raw bytes:

```
0:000> !U 00320082
Normal JIT generated code
ClassMain.Main(System.String[])
Begin 00320070, size 13
00320070 mov ecx,0D3060h
00320075 call 000c201c
0032007a mov ecx,eax
0032007c call dword ptr ds:[0D309Ch]
>> 00320082 ret
```

Here we can still double check JIT-ed function calls manually:

```
0:000> dd 0D309Ch 11
00d309c 00320098

0:000> !IP2MD 00320098
MethodDesc: 000d3048
Method Name: ClassMain.DoWork()
Class: 000d1180
MethodTable: 000d3060
mdToken: 06000002
Module: 000d2c3c
IsJitted: yes
m_CodeOrIL: 00320098
```

## Blocked DPC

In this pattern, we have blocked per-processor Deferred Procedure Call queues because of threads running on processors with IRQL > DISPATCH_LEVEL. For example, on the processor 11 (0x0b):

```
11: kd> !dpcs
CPU Type KDPC Function
3: Normal : 0x8accacec 0xf710567a DriverA

5: Normal : 0x89f449e4 0xf595b83a DriverB

7: Normal : 0x8a63664c 0xf59e3f04 USBPORT!USBPORT_IsrDpc

11: Normal : 0x8acb2cec 0xf710567a DriverA
11: Normal : 0x8b5e955c 0xf73484e6 ACPI!ACPIInterruptServiceRoutineDPC

11: kd> !thread
THREAD 89806428  Cid 0934.0944  Teb: 7ffdb000 Win32Thread: bc17dda0 RUNNING on processor b
Not impersonating
DeviceMap            e1002258
Owning Process       89972290       Image:         ApplicationA.exe
Attached Process     N/A            Image:         N/A
Wait Start TickCount 2863772       Ticks: 368995 (0:01:36:04.140)
Context Switch Count 145085         LargeStack
UserTime             00:00:00.015
KernelTime           01:36:04.203
Win32 Start Address MSVCR90!_threadstartex (0x7854345e)
Start Address kernel32!BaseThreadStartThunk (0x77e617ec)
Stack Init f3f63000 Current f3f62c4c Base f3f63000 Limit f3f5f000 Call 0
Priority 10 BasePriority 10 PriorityDecrement 0
ChildEBP RetAddr  Args to Child
f777d3b0 f3f62d28 00000010 00000000 00000000 hal!KeAcquireInStackQueuedSpinLockRaiseToSynch+0x36
WARNING: Frame IP not in any known module. Following frames may be wrong.
f777d3b4 00000000 00000000 00000000 00000000 0xf3f62d28
```

## Blocked Queue

## LPC/ALPC

We provide an example of an ALPC port here. If we see an LPC/ALPC wait chain (page 1097) endpoint or just have a message address (and optionally a port address), we can check the port queue length. For example, in a frozen system we have this WinDbg output:

```
THREAD fffffa8009db7160  Cid 03b0.2ec0  Teb: 000007fffffd5000 Win32Thread: 0000000000000000 WAIT:
    (WrLpcReply) UserMode Non-Alertable
    fffffa8009db7520  Semaphore Limit 0x1
Waiting for reply to ALPC Message fffffa800dbc6650 : queued at port fffffa800577ee60 : owned by process fffffa80055ddb30
Not impersonating
DeviceMap            fffff8a000008b30
Owning Process       fffffa8005691b30       Image:         ServiceA.exe
Attached Process     N/A                    Image:         N/A
Wait Start TickCount 39742808
Context Switch Count 9
UserTime             00:00:00.000
KernelTime           00:00:00.000
Win32 Start Address 0x0000000076cd8e70
Stack Init fffff8800bf60db0 Current fffff8800bf60620
Base fffff8800bf61000 Limit fffff8800bf5b000 Call 0
Priority 10 BasePriority 9 UnusualBoost 0 ForegroundBoost 0 IoPriority 2 PagePriority 5
Kernel stack not resident.
Child-SP RetAddr Call Site
fffff880`0bf60660 fffff800`016de992 nt!KiSwapContext+0x7a
fffff880`0bf607a0 fffff800`016e0cff nt!KiCommitThreadWait+0x1d2
fffff880`0bf60830 fffff800`016f5d1f nt!KeWaitForSingleObject+0x19f
fffff880`0bf608d0 fffff800`019ddac6 nt!AlpcpSignalAndWait+0x8f
fffff880`0bf60980 fffff800`019dba50 nt!AlpcpReceiveSynchronousReply+0x46
fffff880`0bf609e0 fffff800`019d8fcb nt!AlpcpProcessSynchronousRequest+0x33d
fffff880`0bf60b00 fffff800`016d6993 nt!NtAlpcSendWaitReceivePort+0x1ab
fffff880`0bf60bb0 00000000`76d105aa nt!KiSystemServiceCopyEnd+0x13 (TrapFrame @ fffff880`0bf60c20)
00000000`01fe6e38 000007fe`fec0aa76 ntdll!ZwAlpcSendWaitReceivePort+0xa
00000000`01fe6e40 000007fe`fecacb64 RPCRT4!LRPC_CCALL::SendReceive+0x156
00000000`01fe6e70 000007fe`fecacd55 RPCRT4!NdrpClientCall3+0x244
00000000`01fe6e90 000007fe`fcbf18a1 RPCRT4!NdrClientCall3+0xf2
[...]
```

```
0: kd> !alpc /m fffffa800dbc6650
Message @ fffffa800dbc6650
        MessageID     : 0x0720 (1824)
        CallbackID    : 0x257C575 (39306613)
        SequenceNumber: 0x00000002 (2)
        Type          : LPC_REQUEST
        DataLength    : 0x0044 (68)
        TotalLength   : 0x006C (108)
        Canceled      : No
        Release       : No
        ReplyWaitReply: No
        Continuation  : Yes
        OwnerPort     : fffffa8006a4bb10 [ALPC_CLIENT_COMMUNICATION_PORT]
        WaitingThread : fffffa8009db7160
        QueueType     : ALPC_MSGQUEUE_PENDING
        QueuePort     : fffffa800577ee60 [ALPC_CONNECTION_PORT]
        QueuePortOwnerProcess : fffffa80056db30 (ServiceB.exe)
        ServerThread  : fffffa8007ead4d0
        QuotaCharged  : No
        CancelQueuePort : 0000000000000000
        CancelSequencePort : 0000000000000000
        CancelSequenceNumber : 0x00000000 (0)
        ClientContext : 0000000002a60f40
        ServerContext : 0000000000000000
        PortContext   : 000000000227a370
        CancelPortContext : 0000000000000000
        SecurityData  : 0000000000000000
        View          : 0000000000000000
```

```
0: kd> !alpc /p fffffa800577ee60
Port @ fffffa800577ee60
        Type          : ALPC_CONNECTION_PORT
        CommunicationInfo : fffffa80022435d0
                ConnectionPort      : fffffa800577ee60
                ClientCommunicationPort : 0000000000000000
                ServerCommunicationPort : 0000000000000000
        OwnerProcess  : fffffa80056ddb30 (ServiceB.exe)
        SequenceNo    : 0x0000481A (18458)
        CompletionPort: fffffa8005728e80
        CompletionList: 0000000000000000
        MessageZone   : 0000000000000000
        ConnectionPending : No
        ConnectionRefused : No
        Disconnected  : No
        Closed        : No
        FlushOnClose  : Yes
        ReturnExtendedInfo : No
        Waitable      : No
        Security      : Static
        Wow64CompletionList : No
```

Main queue is empty.

Large message queue is empty.

Pending queue has 698 message(s)
