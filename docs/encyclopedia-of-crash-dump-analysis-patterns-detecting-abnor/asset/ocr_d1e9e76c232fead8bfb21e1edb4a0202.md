# Ghost Thread

Sometimes **Wait Chains** (page 1092) such as involving critical sections (page 1086) may have **Missing Thread** (page 683) endpoint. However, in some cases, we might see **Ghost Thread** whose TID was reused by subsequent thread creation in a different process. For example, critical section structure may refer to such TID as in the example below.

```
// Critical section from LSASS process

THREAD fffffa803431cb0 Cid 03e8.2718 Teb: 000007ffff80000 Win32Thread: 0000000000000000 WAIT: (UserRequest) UserMode Non-Alertable
fffffa80330e0500 SynchronizationEvent
Impersonation token: fffff8a00b807060 (Level Impersonation)
Owning Process fffffa8032354c40 Image: lsass.exe
Attached Process N/A Image: N/A
Wait Start TickCount 107175 Ticks: 19677 (0:00:05:06.963)
Context Switch Count 2303 IdealProcessor: 1
UserTime 00:00:00.218
KernelTime 00:00:00.109
Win32 Start address nt!l!TppWorkerThread (0x0000000076e1f2e0)
Stack Init fffff8800800e5db0 Current fffff88008e5f900
Base fffff88008e06000 Limit fffff88008e5a000 Call 0
Priority 10 BasePriority 10 UnusualBoost 0 ForegroundBoost 0 IoPriority 2 PagePriority 5
Kernel stack not resident.

Child-SP RetAddr Call Site
fffff880`08e5f940 fffff800`01c7cf72 nt!KiSwapContext+0x7a
fffff880`08e5fa80 fffff800`01c8e39f nt!KiCommitThreadWait+0x1d2
fffff880`08e5fb10 fffff800`01f7fe3e nt!KeWaitForSingleObject+0x19f
fffff880`08e5fbb0 fffff800`01c867d3 nt!NtWaitForSingleObject+0xde
fffff880`08e5fc20 00000000`76e5067a nt!KiSystemServiceCopyEnd+0x13 (TrapFrame @ fffff880`08e5fc20)
00000000`0427cc a 00000000`76e4d808 ntdll!NtWaitForSingleObject+0xa
00000000`0427c b0 00000000`76e4d6fb ntdll!RtlpWaitOnCriticalSection+0xe8
00000000`0427cd 60 000007fe`f464a4fe ntdll!RtlEnterCriticalSection+0xd1
[...]

1: kd> .process /r /p fffffa8032354c40
Implicit process is now fffffa80`32353b30
Loading User Symbols
```