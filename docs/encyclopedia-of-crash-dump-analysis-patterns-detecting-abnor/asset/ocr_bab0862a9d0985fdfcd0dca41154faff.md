```
89540000: .-=.......... .-=.......... .-=.......... .-=..=..=-.=
89580000: .....=-.=-..... =-==....-==== ==-==-=--== =-==--..-===
895c0000: =.....==... ..-=...=-...-.- =-.--....-=.. .....-....-
89600000: .....-.=...=.. ===.....=-... =..--....=... .....=.....-
89640000: .-..-===-=... ==..-...-.-=.. =-=.=......=. .....=-...-=.
...
...
...
```

Here is another example:

```
0: kd> !vm

*** Virtual Memory Usage ***
Physical Memory: 786299 ( 3145196 Kb)
Page File: \?\C:\pagefile.sys
Current: 4193280Kb Free Space: 3407908Kb
Minimum: 4193280Kb Maximum: 4193280Kb
Available Pages: 200189 ( 800756 Kb)
ResAvail Pages: 657130 ( 2628520 Kb)
Modified Pages: 762 ( 3048 Kb)
NonPagedPool Usage: 22948 ( 91792 Kb)
NonPagedPool Max: 70145 ( 280580 Kb)
PagedPool 0 Usage: 19666 ( 78664 Kb)
PagedPool 1 Usage: 3358 ( 13432 Kb)
PagedPool 2 Usage: 3306 ( 13224 Kb)
PagedPool 3 Usage: 3312 ( 13248 Kb)
PagedPool 4 Usage: 3309 ( 13236 Kb)
**************** Excessive Paged Pool Usage ****************
PagedPool Usage: 32951 ( 131804 Kb)
PagedPool Maximum: 40960 ( 163840 Kb)
Shared Commit: 9664 ( 38656 Kb)
Special Pool: 0 ( 0 Kb)
Free System PTEs: 103335 ( 413340 Kb)
Shared Process: 45024 ( 180096 Kb)
PagedPool Commit: 32951 ( 131804 Kb)
Driver Commit: 1398 ( 5592 Kb)
Committed pages: 864175 ( 3456700 Kb)
Commit limit: 1793827 ( 7175308 Kb)
```

```
0: kd> !pooled 4
Sorting by Paged Pool Consumed

Pool Used: NonPaged Paged
Tag Allocs Used Allocs Used
CM 85 5440 11045 47915424
MyAV 0 0 186 14391520
MmSt 0 0 11795 13235744
Otbt 709 90752 2712 11108352
Ntff 5 1120 9886 8541504
...
...
...
```