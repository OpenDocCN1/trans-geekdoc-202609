# PTE

In order to maintain virtual to physical address translation, OS needs page tables. These tables occupy memory too. If memory is not enough for new tables the system will fail to create processes, allocate I/O buffers and memory from pools.

We might see the following diagnostic message from WinDbg:

```
4: kd> !vm

*** Virtual Memory Usage ***
Physical Memory:    851422 (  3405688 Kb)
Page File: \\?\C:\pagefile.sys
  Current: 2095104 Kb  Free Space: 2081452 Kb
  Minimum: 2095104 Kb  Maximum: 4190208 Kb
Available Pages:     683464 (  2733856 Kb)
ResAvail Pages:      800927 (  3203708 Kb)
Locked IO Pages:           145 (       580 Kb)
Free System PTEs:     23980 (     95920 Kb)

***************** 356363 system PTE allocations have failed ***************
Free NP PTEs:         6238 (     24952 Kb)
Free Special NP:           0 (         0 Kb)
Modified Pages:         482 (      1928 Kb)
Modified PF Pages:      482 (      1928 Kb)
NonPagedPool Usage:   18509 (     74036 Kb)
NonPagedPool Max:     31970 (    127880 Kb)
PagedPool 0 Usage:    8091 (     32364 Kb)
PagedPool 1 Usage:    2495 (       9980 Kb)
PagedPool 2 Usage:    2580 (     10320 Kb)
PagedPool 3 Usage:    2552 (     10208 Kb)
PagedPool 4 Usage:    2584 (     10336 Kb)
PagedPool Usage:      18302 (     73208 Kb)
PagedPool Maximum:    39936 (    159744 Kb)

********************* 48530 pool allocations have failed *********************
Shared Commit:         5422 (     21688 Kb)
Special Pool:             0 (         0 Kb)
Shared Process:         5762 (     23048 Kb)
PagedPool Commit:      18365 (     73460 Kb)
Driver Commit:          2347 (      9388 Kb)
Committed pages:       129014 (    516056 Kb)
Commit limit:        1342979 (   5371916 Kb)
```

We can also see another diagnostic message about pool allocation failures which may be the consequence of PTE allocation failures.