# Incorrect Symbolic Information

Most of the time this pattern is associated with function names and offsets, for example, _module!foo_ vs. _module!foo+100_. In some cases, the module name is incorrect itself or absent altogether. This can happen in complete memory dumps when we forget to reload user space symbols after changing the process context, for example:

```
; previous process context of firefox.exe
; switching to winlogon.exe context

kd> .process fffffffadfe718c040
Implicit process is now fffffffadf`e718c040

kd> !process fffffffadfe718c040
PROCESS fffffffadfe718c040
    SessionId: 0 Cid: 017c    Peb: 7fffffd9000  ParentCid: 0130
    DirBase: 01916000  ObjectTable: fffffa800099a890  HandleCount:  754.
    Image: winlogon.exe
    VadRoot fffffffadfe75e91f0 Vads 190 Clone 0 Private 2905. Modified 10047. Locked 0.
    DeviceMap fffffa8000004950
                                 Token             fffffa800122a060
    ElapsedTime               77 Days 02:14:26.109
    UserTime                  00:00:04.156
    KernelTime                00:00:02.359
    QuotaPoolUsage[PagedPool] 143128
    QuotaPoolUsage[NonPagedPool] 191072
    Working Set Sizes (now,min,max) (541, 50, 345) (2164KB, 200KB, 1380KB)
    PeakWorkingSetSize        6323
    VirtualSize               108 Mb
    PeakVirtualSize           118 Mb
    PageFaultCount            212547
    MemoryPriority            BACKGROUND
    BasePriority              13
    CommitCharge              3733

[...]
```