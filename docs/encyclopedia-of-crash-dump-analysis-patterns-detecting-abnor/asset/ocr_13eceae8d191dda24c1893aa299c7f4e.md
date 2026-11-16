The second processor is busy too:

```
0: kd> !running

System Processors 3 (affinity mask)
Idle Processors 0

Prcbs Current Next
0 8172c920 84e6c900 .........
1 805d8120 85138030 85a50d78 .........
0: kd> !thread 85138030
THREAD 85138030 Cid 0564.11c8 Teb: 7ff9f000 Win32Thread: 00000000 RUNNING on processor 1
IRP List:
85ab5d00: (0006,01fc) Flags: 00000884 Mdl: 00000000
85445ab8: (0006,0094) Flags: 00060000 Mdl: 00000000
Not impersonating
DeviceMap 98a7d558
Owning Process 84f0d938 Image: Application.exe
Attached Process N/A Image: N/A
Wait Start TickCount 695643 Ticks: 224 (0:00:00:03.500)
Context Switch Count 20
UserTime 00:00:00.000
KernelTime 00:00:00.000
Win32 Start Address 0x705e2679
Stack Init a1d13000 Current a1d10a70 Base a1d13000 Limit a1d10000 Call 0
Priority 9 BasePriority 8 PriorityDecrement 0 IoPriority 2 PagePriority 5
ChildEBP RetAddr Args to Child
00000000 00000000 00000000 00000000 0x0
```

Because we have (Limit, Current, Base) triple for our thread, we check its **Execution Residue** (page 371) on the kernel raw stack. We find traces of a hypercall too:

```
0: kd> dds a1d10000 a1d13000
[...]
a1d1215c 816fa6da nt!HvlEndSystemInterrupt+0x20
a1d12160 40000070
a1d12164 00000000
a1d12168 81608838 hal!HalEndSystemInterrupt+0x7a
a1d1216c 805d8000
a1d12170 a1d12180
a1d12174 81618c9 hal!HalpIpiHandler+0x189
a1d12178 84f4841b
a1d1217c 000000e1
a1d12180 a1d122cc
a1d12184 84617008
a1d12188 badb0d00
a1d1218c 00000000
a1d12190 81665699 nt!RtlWalkFrameChain+0x58
a1d12194 816659c4 nt!RtlWalkFrameChain+0x377
a1d12198 11c4649e
a1d1219c 00000002
a1d121a0 00000003
a1d121a4 85478444
```