```
5: kd> !pte b044e000-4
VA b044dffc

PDE at 00000000C062C010    PTE at 00000000C582268
contains 000000001A0A3C863  contains 0000000000000000
pfn 10aa3c     -DA--KWEV
```

WinDbg was unable to get all stack frames, and we don’t see big frame values (“Memory” column below):

```
5: kd> knf 100
*** Stack trace for last set context - .thread/.cxr resets it
# Memory ChildEBP RetAddr
00     b044e034 f7b840ac nt!SEH_prolog+0x1b
01     20 b044e054 f7b84e66 Ntfs!NtfsMapStream+0x4b
02     74 b044e0c8 f7b84045 Ntfs!NtfsReadMftRecord+0x86
03     38 b044e100 f7b8404f Ntfs!NtfsReadFileRecord+0x7a
04     38 b044e138 f7b7cdb5 Ntfs!NtfsLookupInFileRecord+0x37
05     d8 b044e210 f7b6efef Ntfs!NtfsWriteFileSizes+0x76
06     50 b044e260 f7b6eead Ntfs!NtfsFlushAndPurgeScb+0xd4
07     204 b044e464 f7b7e302 Ntfs!NtfsCommonCleanup+0x1ca8
08     170 b044e5d4 8081dce5 Ntfs!NtfsFsdCleanup+0xcf
09     14 b044e5e8 f70fac53 nt!IofCallDriver+0x45
0a     28 b044e610 8081dc5e fltMgr!FltpDispatch+0x6f
0b     14 b044e624 f420576a nt!IofCallDriver+0x45
0c     10 b044e634 f4202621 component2!Dispatch+0x4
0d     c   b044e640 8081dc5e component2!Dispatch+0x53
0e     14 b044e654 f4e998c7 nt!IofCallDriver+0x45
0f     28 b044e67c f4e9997c component!PassThrough+0xbb
10     c   b044e688 8081dc5e component!Dispatch+0x78
11     14 b044e69c f41e27ff nt!IofCallDriver+0x45
WARNING: Stack unwind information not available. Following frames may be wrong.
12     24 b044e6c0 f41e1ed driver+0xc2ff
13     00000000 00000000 driver+0xc1ed
```

To see all components involved, we need to dump raw stack data (12Kb is 0x3000). There we can also see some Software Exceptions (page 875) processed and get some partial stack traces for them. Some caution is required because stack traces might be incomplete and misleading due to overwritten stack data.

```
5: kd> dds b044e000 b044e000+3000
...
...
...
...
b044ebc4 b044ec74
b044ebc8 b044ec50
b044ebcc f41f9458 driver+0x1e458
b044ebd0 b044f140
b044ebd4 b044ef44
b044ebd8 b044f138
b044ebdc 80877290 nt!RtlDispatchException+0x8c
b044ebe0 b044ef44
b044ebe4 b044f138
b044ebe8 b044ec74
b044ebec b044ec50
b044ebf0 f41f9458 driver+0x1e458
b044ebf4 8a7668c0
```