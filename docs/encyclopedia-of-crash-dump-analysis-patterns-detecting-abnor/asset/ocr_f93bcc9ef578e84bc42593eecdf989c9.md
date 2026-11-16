```
0: kd> !object fffffffa800a13bb30
Object: fffffffa800a13bb30  Type: (ffffffa8006cecf30) Process
ObjectHeader: fffffffa800a13bb00 (new version)
HandleCount: 0 PointerCount: 1

0: kd> !object fffffffa8009b7e8e0
Object: fffffffa8009b7e8e0 Type: (fffffa8006cecf30) Process
ObjectHeader: fffffffa8009b7e8b0 (new version)
HandleCount: 0 PointerCount: 1
```

Such number of processes correlates with non-paged pool usage for process structures:

```
0: kd> !poolfused 3
...
Sorting by NonPaged Pool Consumed

NonPaged Paged
Tag  Allocs  Frees   Diff  Used   Allocs Frees Diff  Used
...
Proc 55488  60      55428 80328320 0    0    0    0    Process objects , Binary: nt!ps
File 51733526 51708737 24789 7150416 0    0    0    0    File objects
[...]
```

Here we recommend enabling object reference tracing either using gflags.exe or directly modifying registry:

![](bbox=[0.21, 0.49, 0.79, 0.94])