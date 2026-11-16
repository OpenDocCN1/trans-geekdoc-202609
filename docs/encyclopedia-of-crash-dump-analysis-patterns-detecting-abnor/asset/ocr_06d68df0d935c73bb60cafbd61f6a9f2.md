```
nt!KiIdleLoop+0x7d:
8088d32f sti
8088d330 lea ecx,[ebx+120h]
8088d336 call nt!KiIdleSchedule (808343e6)
8088d33b test eax,eax
8088d33d mov esi,eax
8088d33f mov edi,dword ptr [ebx+12Ch]
8088d345 jne nt!KiIdleLoop+0x99 (8088d2f1)

nt!KiIdleLoop+0xef:
8088d347 jmp nt!KiIdleLoop+0xa (8088d262)
```

In some memory dumps taken when systems or sessions were hanging or very slow for some time we might see Busy System pattern where all processors execute non-idle threads, and there are threads in ready queues waiting to be scheduled:

```
3: kd> !running

System Processors f (affinity mask)
Idle Processors 0

Prcb Current Next
0 fffdf120 88cef850 ..........
1 f7727120 8940b7a0 ..........
2 f772f120 8776f020 ..........
3 f7737120 87b25360 ..........

3: kd> !ready
Processor 0: Ready Threads at priority 8
THREAD 88161668 Cid 3d58.43a0 Teb: 7ffdf000 Win32Thread: bc1eba48 READY
THREAD 882d0020 Cid 3d58.43a0 Teb: 7ffdf000 Win32Thread: bc208338 READY
THREAD 88716b40 Cid 2034.241c Teb: 7ffdf000 Win32Thread: bc11b388 READY
THREAD 886f7978 Cid 2444.2564 Teb: 7ffde000 Win32Thread: bc1ccc18 READY
THREAD 87b6f2a8 Cid 2308.4bfc Teb: 7ffdf000 Win32Thread: bc1f7b98 READY
Processor 0: Ready Threads at priority 0
THREAD 8a3925a8 Cid 0004.0008 Teb: 00000000 Win32Thread: 00000000 READY
Processor 1: Ready Threads at priority 9
THREAD 87e69db0 Cid 067c.3930 Teb: 7ffdb000 Win32Thread: bc180990 READY
Processor 1: Ready Threads at priority 8
THREAD 88398c70 Cid 27cc.15b4 Teb: 7ffde000 Win32Thread: bc159ea8 READY
Processor 2: Ready Threads at priority 8
THREAD 8873cdd0 Cid 4c24.4384 Teb: 7ffdd000 Win32Thread: bc1c9838 READY
THREAD 89f331e0 Cid 453c.4c68 Teb: 7ffdf000 Win32Thread: bc21dbd0 READY
THREAD 889a03f0 Cid 339c.2fcc Teb: 7ffdf000 Win32Thread: bc1cde8 READY
THREAD 87aacdb0 Cid 3b89.4ed0 Teb: 7ffde000 Win32Thread: bc1c5d10 READY
Processor 3: No threads in READY state
```

Here is another example from a busy 8-processor system where only one processor was idle at the time of the bugcheck: