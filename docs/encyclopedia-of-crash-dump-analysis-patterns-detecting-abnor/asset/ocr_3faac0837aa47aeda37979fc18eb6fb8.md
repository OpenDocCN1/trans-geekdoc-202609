# Software

We often say that particular thread is blocked and/or it blocks other threads. At the same time, we know that almost all threads are “blocked” to some degree except those currently running on processors. They are either preempted and in the ready lists, voluntarily yielded their execution, or they are waiting for some synchronization object. Therefore the notion of Blocked Thread is highly context and problem dependent and usually we notice them when comparing current thread stack traces with their expected normal stack traces. Here reference guides (Appendix A) are indispensable especially those created for troubleshooting concrete products.

To show the diversity of “blocked” threads, we can propose the following thread classification:

# Running threads

Their EIP (RIP) points to some function different from KiSwapContext:

```
3: kd> !running

System Processors f (affinity mask)
Idle Processors 0

 Prcb              Current           Next
 0 ffdff120        a30a9350          ................
 1 ff727120        a3186448          ................
 2 f772f120        a59a1b40          ................
 3 f7737120        a3085888          ................
3: kd> !thread a59a1b40
THREAD a59a1b40  Cid 0004.00b8  Teb: 00000000 Win32Thread: 00000000 RUNNING on processor 2
 Not impersonating
DeviceMap            e10028b0
 Owning Process     a59aa648       Image:         System
 Wait Start TickCount   1450446       Ticks: 1 (0:00:00:00.015)
 Context Switch Count   308765
 UserTime             00:00:00.000
 KernelTime           00:00:01.250
 Start Address nt!ExpWorkerThread (0x80880356)
 Stack Init f7055000 Current f7054cec Base f7055000 Limit f7052000 Call 0
 Priority 12 BasePriority 12 PriorityDecrement 0
 ChildEBP RetAddr
 f7054cb4 8093c55c nt!ObReferenceObject+0x1c
 f7054ca0 8093d2ae nt!ObpQueryNameString+0x2ba
 f7054cbc 8087f0df nt!ObQueryNameString+0x18
 f7054d80 80880441 nt!IopErrorLogThread+0x197
 f7054dac 80949b7c nt!ExpWorkerThread+0xeb
 f7054ddc 8088e062 nt!PspSystemThreadStartup+0x2e
 00000000 00000000 nt!KiThreadStartup+0x16
3: kd> .thread a59a1b40
Implicit thread is now a59a1b40
```