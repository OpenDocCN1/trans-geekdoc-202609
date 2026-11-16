```
Kernel stack not resident.
ChildEBP RetAddr   Args to Child
f60dfc78 8083d5b1 89815db0 89815e58 00000006 nt!KiSwapContext+0x26
f60dfca4 8083df9e 00000000 00000000 00000000 nt!KiSwapThread+0x2e5
f60dfcec 8092ae57 88603e40 00000006 00000001 nt!KeWaitForSingleObject+0x346
f60dfd50 80833bef 000004fc 00000000 00000000 nt!NtWaitForSingleObject+0x9a
f60dfd50 7c8285ec 000004fc 00000000 00000000 nt!KiFastCallEntry+0xfc
```

We see that it is blocked waiting for a synchronization object (mutant, shown in bold italics above), and we check the thread 884d7db0 that owns it:

```
7: kd> !thread 884d7db0
THREAD 884d7db0 Cid 1218.1ec2 Teb: 7ffdd000 Win32Thread: 00000000 WAIT: (Unknown) UserMode Non-
Alertable
884d7f9c Semaphore Limit 0x1
Waiting for reply to LPC MessageId 0000fa9e:
Current LPC port e121fdb8
Not impersonating
DeviceMap e10018b8
Owning Process 887d32d0 Image: svchost.exe
Wait Start TickCount 11800 Ticks: 432925 (0:01:52:44.453)
Context Switch Count 111
UserTime 00:00:00.000
KernelTime 00:00:00.000
Win32 Start Address 0x0000fa9b
LPC Server thread working on message Id fa9b
Start Address 0x77e617ec
Stack Init f4598000 Current f4597c08 Base f4598000 Limit f4595000 Call 0
Priority 9 BasePriority 8 PriorityDecrement 0
Kernel stack not resident.
ChildEBP RetAddr Args to Child
f4597c20 8083d5b1 884d7db0 884d7e58 00000007 nt!KiSwapContext+0x26
f4597c4c 8083f9e 884d7f9c 884d7f70 884d7db0 nt!KiSwapThread+0x2e5
f4597c94 8093eda1 884d7f9c 00000011 80939091 nt!KeWaitForSingleObject+0x346
f4597d50 80833bef 00000560 0000ebfe 0000ebfe nt!NtRequestWaitReplyPort+0x776
f4597d50 7c8285ec 00000560 0000ebfe 0000ebfe nt!KiFastCallEntry+0xfc
```

The thread is waiting for the LPC message 0000fa9e, and we look for a server thread processing it:

```
7: kd> !thread 898c6db0
THREAD 898c6db0 Cid 0b38.188c Teb: 7ff4d000 Win32Thread: 00000000 WAIT: (Unknown) UserMode Non-
Alertable
884362c8 SynchronizationEvent
Not impersonating
DeviceMap e11399e8
Owning Process 88340758 Image: AppB.exe
Wait Start TickCount 11801 Ticks: 432924 (0:01:52:44.437)
Context Switch Count 7
UserTime 00:00:00.000
KernelTime 00:00:00.000
Win32 Start Address 0x0000fa9e
LPC Server thread working on message Id fa9e
Start Address 0x77e617ec
Stack Init f5138000 Current f5137c60 Base f5138000 Limit f5135000 Call 0
```