```
0: kd> !running

System Processors f (affinity mask)
Idle Processors e

    Prcb     Current     Next
0 ffdff120 808a68c0 86841588 ..........
```

```
0: kd> !thread 808a68c0 1f
THREAD 808a68c0  Cid 0000.0000  Teb: 00000000 Win32Thread: 00000000 RUNNING on processor 0
Not impersonating
Owning Process      808a6b40      Image:      Idle
Wait Start TickCount      0     Ticks: 15423499 (2:18:56:32.171)
Context Switch Count      100782385
UserTime      00:00:00.000
KernelTime      2 Days 12:18:49.343
Stack Init 808a38b0 Current 808a35fc Base 808a38b0 Limit 808a08b0 Call 0
Priority 0 BasePriority 0 PriorityDecrement 0
ChildEBP RetAddr
808a07bc 808a4d4f nt!KeBugCheckEx+0x1b
808a080c 80834b83 hal!HalHandleNMI+0x1a5
808a080c 808a0853 nt!KiTrap02+0x136 (TrapFrame @ 808a0820)
808a3570 f7659ca2 hal!HalpClockInterrupt+0xff (TrapFrame @ 808a3570)
808a3600 80839b12 intelppm!AcpiC1Idle+0x12
808a3604 00000000 nt!KiIdleLoop+0xa
```

```
0: kd> !ready
Processor 0: No threads in READY state
Processor 1: No threads in READY state
Processor 2: No threads in READY state
Processor 3: No threads in READY state
```