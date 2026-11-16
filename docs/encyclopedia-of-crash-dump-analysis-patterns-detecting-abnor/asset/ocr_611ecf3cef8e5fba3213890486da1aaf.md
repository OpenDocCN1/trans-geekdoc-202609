# Mixed Objects

# Kernel Space

Here is another pattern of a **Deadlock** variety involving mixed objects in kernel space. Let's look at a complete **Manual Dump** (page 625) file from a hanging system:

```
0: kd> !analyze -v

NMI_HARDWARE_FAILURE (80)
This is typically due to a hardware malfunction.  The hardware supplier should
be called.
Arguments:
Arg1: 004f4f54
Arg2: 00000000
Arg3: 00000000
Arg4: 00000000
```

Here we have a problem to read all executive resource locks:

```
3: kd> !locks
**** DUMP OF ALL RESOURCE OBJECTS ****

Resource @ nt!CmpRegistryLock (0x808a48c0)   Shared 36 owning threads
  Contention Count = 48
    Threads: 86eace0-01<**> 8b76db40-01<**> 8b76ddb0-01<**> 89773020-01<**>
             87222db0-01<**> 87024ba8-01<**> 89a324f0-01<**> 86b4e298-01<**>
             87925b40-01<**> 86b4db40-01<**> 8701f738-01<**> 86ffb198-01<**>
             86b492f0-01<**> 8701bad8-01<**> 86ae2db0-01<**> 86c85db0-01<**>
             86a9ddb0-01<**> 86a86db0-01<**> 86aa7db0-01<**> 86a4f5c0-01<**>
             86c5adb0-01<**> 8767ba38-01<**> 86afedb0-01<**> 89877960-01<**>
             8772cdb0-01<**> 87348628-01<**> 874d6748-01<**> 872365e0-01<**>
             87263970-01<**> 873bf020-01<**> 86c13db0-01<**> 893dcdb0-01<**>
             86afa020-01<**> 878e5020-01<**> 874959f8-01<**> 86b2dc70-01<**>
KD: Scanning for held locks..Error 1 in reading nt!_ERESOURCE.SystemResourcesList.Flink @ f76ee2a0
```

This is probably because the dump was **Truncated** (page 1015):

```
Loading Dump File [MEMORY.DMP]
Kernel Complete Dump File: Full address space is available

WARNING: Dump file has been truncated. Data may be missing.
```