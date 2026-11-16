```
3: kd> r
Last set context:
eax=00000028 ebx=e1000228 ecx=e1002b30 edx=e1000234 esi=e1002b18 edi=0000001a
eip=8086c73e esp=f7054bc4 ebp=f7054ca4 iopl=0 nv up ei pl nz na po nc
cs=0008 ss=0010 ds=0023 es=0023 fs=0030 gs=0000 efl=00000202
nt!ObReferenceObject+0x1c:
8086c73e 40 inc eax
```

These threads can also be identified by RUNNING attribute in the output of !process 0 3f command
applied for complete and kernel memory dumps.

# Ready threads

These threads can be seen in the output of !ready command or identified by READY attribute in the
output of !process 0 3f command:

```
3: kd> !ready
Processor 0: No threads in READY state
Processor 1: Ready Threads at priority 11
 THREAD a3790790 Cid 0234.1108 Teb: 7ffab000 Win32Thread: 00000000 READY
 THREAD a32799a8 Cid 0234.061c Teb: 7ff83000 Win32Thread: 00000000 READY
 THREAD a3961798 Cid 0c04.0c68 Teb: 7fffab000 Win32Thread: bc204ea8 READY
Processor 1: Ready Threads at priority 10
 THREAD a32bedb0 Cid 1fc8.1a30 Teb: 7ffad000 Win32Thread: bc804468 READY
Processor 1: Ready Threads at priority 9
 THREAD a52cdc48 Cid 0004.0d44 Teb: 00000000 Win32Thread: 00000000 READY
Processor 2: Ready Threads at priority 11
 THREAD a37fedb0 Cid 0c04.11f8 Teb: 7ff8e000 Win32Thread: 00000000 READY
Processor 3: Ready Threads at priority 11
 THREAD a5683db0 Cid 0234.0274 Teb: 7ffd6000 Win32Thread: 00000000 READY
 THREAD a3151d48 Cid 0234.2088 Teb: 7ff88000 Win32Thread: 00000000 READY
 THREAD a5099d80 Cid 0ecc.0d60 Teb: 7ffd4000 Win32Thread: 00000000 READY
 THREAD a3039498 Cid 0c04.275c Teb: 7ff7d000 Win32Thread: 00000000 READY
```

If we look at these threads we see that they were either scheduled to run because of a signaled object
they were waiting for:

```
3: kd> !thread a3039498
THREAD a3039498 Cid 0c04.275c Teb: 7ff7d000 Win32Thread: 00000000 READY
IRP List:
a2feb008: (0006,0094) Flags: 00000870 Mdl: 00000000
Not impersonating
DeviceMap e10028b0
Owning Process a399a770 Image: svchost.exe
Wait Start TickCount 1450447 Ticks: 0
Context Switch Count 1069
UserTime 00:00:00.000
KernelTime 00:00:00.000
Win32 Start Address 0x001e4f22
LPC Server thread working on message Id 1e4f22
Start Address KERNEL32!BaseThreadStartThunk (0x77e617ec)
Stack Init f171b000 Current f171ac60 Base f171b000 Limit f1718000 Call 0
Priority 11 BasePriority 10 PriorityDecrement 0
```