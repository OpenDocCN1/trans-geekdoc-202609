# Process Objects

Here we show an example of Wait Chain (page 1092) involving process objects. This variation is similar to threads waiting for thread objects (page 1128). When looking at Stack Trace Collection (page 943) from a complete memory dump file, we see that several threads in a set of processes are blocked in ALPC Wait Chain (page 1097):

```
THREAD fffffa8010b8700 Cid 12f8.1328 Teb: 000000007ef9a000 Win32Thread: 0000000000000000 WAIT:
(WrLpcReply) UserMode Non-Alertable
fffffa8010b8a90 Semaphore Limit 0x1
Waiting for reply to ALPC Message fffffa8801c7096e0 : queued at port fffffa8010c9d9a0 : owned by process fffffa80109cbcl0
Not impersonating
DeviceMap fffffa80097ce5e0
Owning Process fffffa80110ad510 Image: ProcessA.exe
Attached Process N/A Image: N/A
Wait Start TickCount 14004580 Ticks: 62149 (0:00:16:09.530)
Context Switch Count 25100
UserTime 00:00:00.421
KernelTime 00:00:00.218
Win32 Start Address 0x0000000074ca29e1
Stack Init fffffa6003bc4db0 Current fffffa6003bc4670
Base fffffa6003bc5000 Limit fffffa6003bbf000 Call 0
Priority 8 BasePriority 8 PriorityDecrement 0 IoPriority 2 PagePriority 5
Child-SP RetAddr Call Site
fffffa60`03bc46b0 fffff800`01cba0fa nt!KiSwapContext+0x7f
fffffa60`03bc47b0 fffff800`01caebad nt!KiSwapThread+0x13a
fffffa60`03bc4860 fffff800`01ce4e72 nt!KeWaitForSingleObject+0x2cb
fffffa60`03bc48f0 fffff800`01f32f34 nt!AlpcpSignalAndWait+0x92
fffffa60`03bc4980 fffff800`01f2f9c6 nt!AlpcpReceiveSynchroniousReply+0x44
fffffa60`03bc49e0 fffff800`01f1f52f nt!AlpcpProcessSynchronousRequest+0x24f
fffffa60`03bc4b00 fffff800`01cb7973 nt!NtAlpcSendWaitReceivePort+0x19f
fffffa60`03bc4bb0 00000000`771375a6 nt!KiSystemServiceCopyEnd+0x13 (TrapFrame @ fffffa60`03bc4c20)
00000000`016e5eb8 00000000`74f9993f ntdll!ZwAlpcSendWaitReceivePort+0xa
00000000`016e5c00 00000000`74f8a996 wow64!whNtAlpcSendWaitReceivePort+0x5f
00000000`016e6e10 00000000`75183688 wow64!Wow64SystemServiceEx+0xca
00000000`016eecc0 00000000`74f8ab46 wow64!cpu!ServiceNoTurbo+0x28
00000000`016eef50 00000000`74f8a14c wow64!RunCpuSimulation+0xa
00000000`016eef80 00000000`771605a8 wow64!Wow64LdrpInitialize+0x4b4
00000000`016efe40 00000000`771168d6 ntdll! ?? ::FNODOBFM::`string'+0x20aa1
00000000`016ef590 00000000`00000000 ntdll!LdrInitializeThunk+0xe
```

```
1: kd> !alpc /m fffffa801c7096e0

Message @ fffffa8801c7096e0
MessageID : 0x263C (9788)
CallbackID : 0x29F2A02 (43985410)
SequenceNumber : 0x000009FE (2558)
Type : LPC_REQUEST
DataLength : 0x0058 (88)
TotalLength : 0x0080 (128)
Canceled : No
Released : No
ReplyWaitReply : No
Continuation : Yes
```