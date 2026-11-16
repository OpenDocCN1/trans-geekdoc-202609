# Thread Starvation

# Normal Priority

Here we show the possible signs of the classical Thread Starvation. Suppose we have two running threads with a priority 8:

```
0: kd> !running

System Processors 3 (affinity mask)
Idle Processors 0

Prccbs Current Next
0 ffdff120 89a92020 O..............
1 f7737120 89275020 W..............

0: kd> !thread 89a92020
THREAD 89a92020 Cid 11d8.27d8 Teb: 7ffd9000 Win32Thread: bc1e6860 RUNNING on processor 0
[...]
Priority 8 BasePriority 8 PriorityDecrement 0

0: kd> !thread 89275020
THREAD 89275020 Cid 1cd0.2510 Teb: 7ffa9000 Win32Thread: bc343180 RUNNING on processor 1
[...]
Priority 8 BasePriority 8 PriorityDecrement 0
```

If we have other threads ready with the same priority contending for the same processors (High Contention, page 480) other threads with less priority might starve (shown in bold italics):

```
0: kd> !ready
Processor 0: Ready Threads at priority 8
THREAD 894a1db0 Cid 1a98.25c0 Teb: 7ffde000 Win32Thread: bc19cea8 READY
THREAD 897c4818 Cid 11d8.1c5c Teb: 7ffa2000 Win32Thread: bc2c5ba8 READY
THREAD 8911fdf18 Cid 2730.03f4 Teb: 7ffd9000 Win32Thread: bc305830 READY
Processor 0: Ready Threads at priority 7
THREAD 8a9e5ab0 Cid 0250.0470 Teb: 7fff9f000 Win32Thread: 00000000 READY
THREAD 8a086838 Cid 0250.0654 Teb: 7ff93000 Win32Thread: 00000000 READY
THREAD 8984b8b8 Cid 0250.1dc4 Teb: 7fff99000 Win32Thread: 00000000 READY
THREAD 8912a4c0 Cid 0f4c.2410 Teb: 7ff81000 Win32Thread: 00000000 READY
THREAD 89e5c570 Cid 0f4c.01c8 Teb: 00000000 Win32Thread: 00000000 READY
Processor 0: Ready Threads at priority 6
THREAD 8a9353b0 Cid 1584.1598 Teb: 7ffb8000 Win32Thread: bc057698 READY
THREAD 8aba2020 Cid 1584.15f0 Teb: 7ff9f000 Win32Thread: bc20aea8 READY
THREAD 8aab17a0 Cid 1584.01a8 Teb: 7ff92000 Win32Thread: bc316ea8 READY
THREAD 8a457020 Cid 1584.0634 Teb: 7ff8d000 Win32Thread: bc30fea8 READY
THREAD 8a3d4020 Cid 1584.1510 Teb: 7ff8f000 Win32Thread: bc15b8a0 READY
THREAD 8a5f5db0 Cid 1584.165c Teb: 7ff9d000 Win32Thread: bc171e8 READY
THREAD 8a297020 Cid 0f4c.0f54 Teb: 7ffde000 Win32Thread: bc20fda0 READY
THREAD 8a126020 Cid 1584.175c Teb: 7ffa9000 Win32Thread: 00000000 READY
THREAD 8a548478 Cid 0250.07b0 Teb: 7ff9a000 Win32Thread: 00000000 READY
THREAD 8a478020 Cid 0944.0988 Teb: 7ffd9000 Win32Thread: 00000000 READY
```