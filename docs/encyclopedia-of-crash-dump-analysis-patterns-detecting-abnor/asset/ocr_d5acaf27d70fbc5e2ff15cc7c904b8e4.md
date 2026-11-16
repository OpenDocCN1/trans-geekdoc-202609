# Main Thread

When we look at a thread, and it is not in **Passive Thread** pattern list (page 793), and it looks more like **Blocked Thread** (see page 82) we may ask whether it is **Main Thread**. Every process has at least one thread of execution called main or primary thread. Most GUI applications have window message processing loop inside their main process thread. When a memory dump is saved, it is most likely that this thread is blocked waiting for window or user-defined messages to arrive and can be considered as **Passive Thread**. If we see it blocked on something else waiting for some time, we may consider the application is hanging. Here is an example of the normal iexplore.exe thread stack taken from a kernel dump:

```
PROCESS 88de4140  SessionId: 3  Cid: 15a8    Peb: 7ffdf000  ParentCid: 0e28
DirBase: 0a43d440  ObjectTable: 88efe008  TableSize: 852.
Image: IEXPLORE.EXE
VadRoot 88dbbca8 Clone 0 Private 6604. Modified 951. Locked 0.
DeviceMap 88de6408
Token                             e3f5ccf0
ElapsedTime                       0:10:52.0281
UserTime                          0:00:06.0250
KernelTime                        0:00:10.0421
QuotaPoolUsage[PagedPool]         126784
QuotaPoolUsage[NonPagedPool]      197704
Working Set Sizes (now,min,max)   (8347, 50, 345) (33388KB, 200KB, 1380KB)
PeakWorkingSetSize                10000
VirtualSize                       280 Mb
PeakVirtualSize                   291 Mb
PageFaultCount                    15627
MemoryPriority                    FOREGROUND
BasePriority                      8
CommitCharge                      7440

THREAD 88ee2b00  Cid 15a8.1654  Teb: 7ffde000 Win32Thread: a2242018 WAIT: (WrUserRequest) UserMode Non-Alertable
88f82e00  SynchronizationEvent
Not impersonating
Owning Process            88de4140
Wait Start TickCount      104916         Elapsed Ticks: 0
Context Switch Count      100208         LargeStack
UserTime                  0:00:04.0484
KernelTime                0:00:09.0859
Start Address KERNEL32!BaseProcessStartThunk (0x7c57b70c)
Stack Init be597000 Current be596cc8 Base be597000 Limit be58f000 Call 0
Priority 12 BasePriority 8 PriorityDecrement 0 DecrementCount 0
ChildEBP RetAddr
be596ce0 8042d87d nt!KiSwapThread+0x1b1
be596d08 a00019c2 nt!KeWaitForSingleObject+0x1a3
be596d44 a00138c5 win32k!xxxSleepThread+0x18a
be596d54 a00138d1 win32k!xxxWaitMessage+0xe
be596d5c 8046b2a9 win32k!NtUserWaitMessage+0xb
be596d5c 77e37ccd nt!KiSystemService+0xc9
```