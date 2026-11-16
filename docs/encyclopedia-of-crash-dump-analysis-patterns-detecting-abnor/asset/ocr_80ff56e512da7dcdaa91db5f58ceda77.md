```
Process Uptime: 0 days 0:00:10.000

3: kd> !process 8a389d88
PROCESS 8a389d88  SessionId: 0  Cid: 020c    Peb: 7ffdf000  ParentCid: 01bc
    DirBase: 7fbe6080  ObjectTable: e1721008  HandleCount:  455.
    Image: winlogon.exe

VadRoot 8a650d70 Vads 194 Clone 0 Private 1166. Modified 45. Locked 0.
DeviceMap e10030f8
    Token                             e139be0
    ElapsedTime                       00:00:01.062
    UserTime                          00:00:00.046
    KernelTime                        00:00:00.015
    QuotaPoolUsage[PagedPool]         71228
    QuotaPoolUsage[NonPagedPool]      72232
    Working Set Sizes (now,min,max) (2265, 50, 345) (9060KB, 200KB, 1380KB)
    PeakWorkingSetSize                2267
    VirtualSize                       41 Mb
    PeakVirtualSize                   42 Mb
    PageFaultCount                    2605
    MemoryPriority                    BACKGROUND
    BasePriority                      13
    CommitCharge                      1468
```

# Comments

Another example of no sessions:

```
0: kd> !session
There are ZERO session on machine.

0: kd> !process 0 0
***** NT ACTIVE PROCESS DUMP *****
PROCESS fffffa8003c77b10
    SessionId: none Cid: 0004 Peb: 00000000 ParentCid: 0000
    DirBase: 00187e00  ObjectTable: fffffa80000012f0  HandleCount:  231.
    Image: System

PROCESS fffffa80050afb10
    SessionId: none Cid: 0198 Peb: 7fffffdf000 ParentCid: 0004
    DirBase: a9cf0000  ObjectTable: fffffa8000525970 HandleCount:  22.
    Image: smss.exe
```