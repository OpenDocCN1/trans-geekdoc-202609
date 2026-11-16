# Handle Leak

Sometimes **Handle Leaks** (page 416) also result in insufficient memory especially if handles point to structures allocated by OS. Here is the typical example of the handle leak resulted in freezing several servers. The complete memory dump shows exhausted non-paged pool:

```
0: kd> !vm

*** Virtual Memory Usage ***
Physical Memory:      1048352 (   4193408 Kb)
Page File: \\?\C:\pagefile.sys
  Current:  4190208 Kb  Free Space:   3749732 Kb
  Minimum:  4190208 Kb  Maximum:      4190208 Kb
Available Pages:      697734 (   2790936 Kb)
ResAvail Pages:       958085 (   3832340 Kb)
Locked IO Pages:           95 (        380 Kb)
Free System PTEs:     199971 (    799884 Kb)
Free NP PTEs:            105 (        420 Kb)
Free Special NP:           0 (         0 Kb)
Modified Pages:          195 (        780 Kb)
Modified PF Pages:       195 (        780 Kb)
NonPagedPool Usage:    65244 (    260976 Kb)
NonPagedPool Max:      65503 (    262012 Kb)
**************** Excessive NonPaged Pool Usage *****************
PagedPool 0 Usage:     6576 (     26304 Kb)
PagedPool 1 Usage:      629 (      2516 Kb)
PagedPool 2 Usage:      624 (      2496 Kb)
PagedPool 3 Usage:      608 (      2432 Kb)
PagedPool 4 Usage:      625 (      2500 Kb)
PagedPool Usage:       9062 (     36248 Kb)
PagedPool Maximum:     66560 (    266240 Kb)

***************** 184 pool allocations have failed ***************

Shared Commit:          7711 (     30844 Kb)
Special Pool:              0 (         0 Kb)
Shared Process:        10625 (     42500 Kb)
PagedPool Commit:       9102 (     36408 Kb)
Driver Commit:          1759 (      7036 Kb)
Committed pages:      425816 (   1703264 Kb)
Commit limit:        2052560 (   8210240 Kb)
```