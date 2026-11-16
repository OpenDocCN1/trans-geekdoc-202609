
89540000: .-=.......... .-=.......... .-=.......... .-=..=..=-.=
89580000: .....=-.=-..... =-==....-==== ==-==-=--== =-==--..-===
895c0000: =.....==... ..-=...=-...-.- =-.--....-=.. .....-....-
89600000: .....-.=...=.. ===.....=-... =..--....=... .....=.....-
89640000: .-..-===-=... ==..-...-.-=.. =-=.=......=. .....=-...-=.
...
...
...

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

| Tag | NonPaged Allocs | NonPaged Used | Paged Allocs | Paged Used |
|-----|-----------------|---------------|--------------|------------|
| CM | 85 | 5440 | 11045 | 47915424 |
| MyAV | 0 | 0 | 186 | 14391520 |
| MmSt | 0 | 0 | 11795 | 13235744 |
| Otbt | 709 | 90752 | 2712 | 11108352 |
| Ntff | 5 | 1120 | 9886 | 8541504 |
```

MyAV tag seems to be the prefix for MyAVDrv module, and this is hardly a coincidence. Looking at the list of drivers we see that MyAVDrv.sys was loaded and unloaded several times. Could it be that it did not free its non-paged pool allocations?

```
0: kd> lmv m MyAVDrv.sys
start    end    module name

Unloaded modules:
a5069000 a5084000  MyAVDrv.sys
    Timestamp: unavailable (00000000)
    Checksum: 00000000
a5069000 a5084000  MyAVDrv.sys
    Timestamp: unavailable (00000000)
    Checksum: 00000000
a5069000 a5084000  MyAVDrv.sys
    Timestamp: unavailable (00000000)
    Checksum: 00000000
b93e1000 b93fc000  MyAVDrv.sys
    Timestamp: unavailable (00000000)
    Checksum: 00000000
b9ae5000 b9b00000  MyAVDrv.sys
    Timestamp: unavailable (00000000)
    Checksum: 00000000
be775000 be790000  MyAVDrv.sys
    Timestamp: unavailable (00000000)
    Checksum: 00000000
```

Also, we see that CM tag has the most allocations and !locks command shows hundreds of threads waiting for the registry, one example of High Contention pattern (page 477):

```
0: kd> !locks

Resource @ nt!CmpRegistryLock (0x80478b00)  Shared 10 owning threads
  Contention Count = 9149810
  NumberOfSharedWaiters = 718
  NumberOfExclusiveWaiters = 21
```

Therefore, we see at least two problems in this memory dump: excessive paged pool usage and high thread contention around registry resource slowing down if not halting the system.

## Comments

Another example from ntdebugging blog^113:

To see session pool usage we need to switch to a session process first:

```
1: kd> !sprocess 3
[...]
PROCESS 88b0dd88 SessionId: 3 Cid: 1b90 Peb: 7ffde000 ParentCid: 1b84
DirBase: 4072d000 ObjectTable: d8651450 HandleCount: 414.
Image: ApplicationA.exe
[...]

1: kd> .process /r /p 88b0dd88
Implicit process is now 88b0dd88
Loading User Symbols

1: kd> !poolused 8
Sorting by Session Tag
[...]
```

Excessive nonpaged pool memory usage messages may be false positive for some WinDbg versions^114.

**!poolused 5** produces the same level of detail for paged pool as **!poolused 3** for nonpaged pool.

## Module Fragmentation

Here we discuss the user space case when we don't have enough virtual memory available for reservation due to memory fragmentation. For example, a java virtual machine is pre-allocating memory for its garbage-collected heap. However, after installing some 3rd-party software, the amount of pre-allocated memory is less than expected. In such cases, it is possible to do comparative memory dump analysis to see the difference in virtual address spaces. Original memory dump has this module distribution in memory:

```
0:000> lm
start    end        module name
```

| start | end | module name |
|-------|-----|-------------|
| 00400000 | 0040b000 | javaw (deferred) |
| 009e0000 | 009e7000 | hpi (deferred) |
| 00a30000 | 00a3e000 | verify (deferred) |
| 00a40000 | 00a59000 | java (deferred) |
| 00a60000 | 00a6d000 | zip (deferred) |
| 03ff0000 | 03fff000 | net (deferred) |
| 040a0000 | 040a8000 | nio (deferred) |
| 040b0000 | 0410a000 | hnetcfg (deferred) |
| 041d0000 | 042e2000 | awt (deferred) |
| 04540000 | 04591000 | fontmanager (deferred) |
| 04620000 | 04670000 | msctf (deferred) |
| 047c0000 | 047de000 | jpeg (deferred) |
| 05820000 | 05842000 | dcpr (deferred) |
| 05920000 | 05932000 | pkcs11wrapper (deferred) |
| 08000000 | 08139000 | jvm (deferred) |
| 10000000 | 10000000 | moduleA (deferred) |
| 68000000 | 68035000 | rsaenh (deferred) |
| 6e220000 | 6e226000 | RMProcessLink (deferred) |
| 71ae0000 | 71ae8000 | wshtcpip (deferred) |
| 71b20000 | 71b61000 | mswsock (deferred) |
| 71bf0000 | 71bf8000 | ws2help (deferred) |
| 71c00000 | 71c17000 | ws2_32 (deferred) |
| 71c20000 | 71c32000 | tsappcmp (deferred) |
| 71c40000 | 71c97000 | netapi32 (deferred) |
| 73070000 | 73097000 | winspool (deferred) |
| 76290000 | 762ad000 | imm32 (deferred) |
| 76920000 | 769e2000 | userenv (deferred) |
| 76aa0000 | 76acd000 | winmm (deferred) |
| 76b70000 | 76b7b000 | psapi (deferred) |
| 76ed0000 | 76efa000 | dnsapi (deferred) |
| 76f10000 | 76f3e000 | wldap32 (deferred) |
| 76f50000 | 76f63000 | secur32 (deferred) |
| 76f70000 | 76f77000 | winrnr (deferred) |
| 76f80000 | 76f85000 | rasadhlp (deferred) |
| 77380000 | 77411000 | user32 (deferred) |
| 77670000 | 777a9000 | ole32 (deferred) |
| 77ba0000 | 77bfa000 | msvcrt (deferred) |
| 77c00000 | 77c48000 | gdi32 (deferred) |
| 77c50000 | 77cef000 | rpcrt4 (deferred) |
| 77e40000 | 77f42000 | kernel32 (deferred) |
| 77f50000 | 77feb000 | advapi32 (deferred) |
| 78130000 | 781cb000 | msvcr80 (deferred) |
| 7c800000 | 7c8c0000 | ntdll (pdb symbols) |

We see the big gap between 100e0000 and 68000000 addresses. This means that it is theoretically possible to reserve and/or commit up to 57F20000 bytes (about 1.4Gb). **!address** WinDbg command shows that at least 1.1Gb region (shown in bold below) was reserved indeed:

```
0:000> !address
00000000 : 00000000 - 00010000
    Type      00000000
    Protect   00000001 PAGE_NOACCESS
    State     00010000 MEM_FREE
    Usage     RegionUsageFree
00010000 : 00010000 - 00001000
    Type      00020000 MEM_PRIVATE
    Protect   00000004 PAGE_READWRITE
    State     00001000 MEM_COMMIT
    Usage     RegionUsageEnvironmentBlock
00011000 : 00001000 - 0000f000
    Type      00000000
    Protect   00000001 PAGE_NOACCESS
    State     00010000 MEM_FREE
    Usage     RegionUsageFree
00020000 : 00020000 - 00001000
    Type      00020000 MEM_PRIVATE
    Protect   00000004 PAGE_READWRITE
    State     00001000 MEM_COMMIT
    Usage     RegionUsageProcessParameters
00021000 : 00021000 - 0000f000
    Type      00000000
    Protect   00000001 PAGE_NOACCESS
    State     00010000 MEM_FREE
    Usage     RegionUsageFree
00030000 : 00030000 - 00003000
    Type      00020000 MEM_PRIVATE
    Protect   00000140
    State     00001000 MEM_COMMIT
    Usage     RegionUsageStack
    Pid.Tid   97c.1b3c
...
...
...
100e0000 : 100e0000 - 000a0000
    Type      00020000 MEM_PRIVATE
    Protect   00000040 PAGE_EXECUTE_READWRITE
    State     00001000 MEM_COMMIT
    Usage     RegionUsageIsVAD
10180000 - 05cc0000
    Type      00020000 MEM_PRIVATE
    State     00002000 MEM_RESERVE
    Usage     RegionUsageIsVAD
15e40000 - 004f3000
    Type      00020000 MEM_PRIVATE
    Protect   00000040 PAGE_EXECUTE_READWRITE
    State     00001000 MEM_COMMIT
    Usage     RegionUsageIsVAD
16333000 - 45bad000
    Type      00020000 MEM_PRIVATE
    State     00002000 MEM_RESERVE
```
