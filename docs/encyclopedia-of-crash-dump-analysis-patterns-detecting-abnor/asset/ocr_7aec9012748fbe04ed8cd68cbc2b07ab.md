If we run it, the process size will never grow. GC thread will collect and free unreferenced Leak classes. This can be seen from inspecting memory dumps saved by userdump.exe after the start, 2, 6, and 12 minutes later. The GC heap never grows higher than 1Mb and the number of CLRHeapLeak.Leak and System.Byte[] objects always fluctuates between 100 and 500. For example, for the 12th minute we have the following statistics:

```
0:000> .loadby sos mscorwks

0:000> !eeheap -gc
Number of GC Heaps: 1
generation 0 starts at 0x0147160c
generation 1 starts at 0x0147100c
generation 2 starts at 0x01471000
ephemeral segment allocation context: (0x014dc53c, 0x014dd618)
  segment begin allocated size
  004aedb8 790d7ae4 790f7064 0x00001f580(128384)
  01470000 01471000 014dd618 0x0006c618(443928)
Large object heap starts at 0x02471000
  segment begin allocated size
  02470000 02471000 02473250 0x00002250(8784)
Total Size 0x8dde8(581096)
------------------------------
GC Heap Size 0x8dde8(581096)
```

```
0:000> !dumpheap -stat
total 2901 objects
Statistics:
      Count    TotalSize Class Name
      1       12 System.Security.Permissions.SecurityPermission
      1       24 System.OperatingSystem
      1       24 System.Version
      1       24 System.Reflection.Assembly
      1       28 System.SharedStatics
      1       36 System.Int64[]
      1       40 System.AppDomainSetup
      3       60 System.RuntimeType
      5       60 System.Object
      2       72 System.Security.PermissionSet
      1       72 System.ExecutionEngineException
      1       72 System.StackOverflowException
      1       72 System.OutOfMemoryException
      1      100 System.AppDomain
      7      100 Free
      2      144 System.Threading.ThreadAbortException
      4      328 System.Char[]
    418     5016 CLRHeapLeak.Leak
      5      8816 System.Object[]
    2026 1286332 System.String
    418   433048 System.Byte[]
Total 2901 objects
```