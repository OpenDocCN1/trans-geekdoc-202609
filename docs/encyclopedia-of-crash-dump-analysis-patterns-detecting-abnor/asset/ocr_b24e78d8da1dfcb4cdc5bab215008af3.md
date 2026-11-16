| Current paged pool allocations | 0x0 for 00000000 bytes |
| --- | --- |
| Peak paged pool allocations | 0x0 for 00000000 bytes |
| Current nonpaged pool allocations | 0x0 for 00000000 bytes |
| Peak nonpaged pool allocations | 0x0 for 00000000 bytes |

To check in a process user dump that Application Verifier (and gflags) was enabled we use !avrf and !gflags WinDbg extension commands:

```
0:001> !avrf
Application verifier is not enabled for this process.
Page heap has been enabled separately.

0:001> !gflag
Current NtGlobalFlag contents: 0x02000000
hpa - Place heap allocations at ends of pages
```

Here is an example of an instrumented stack trace:

```
68546e88 verifier!AVrfpDphFindBusyMemoryNoCheck+0xb8
68546f95 verifier!AVrfpDphFindBusyMemory+0x15
68547240 verifier!AVrfpDphFindBusyMemoryAndRemoveFromBusyList+0x20
68549080 verifier!AVrfDebugPageHeapFree+0x90
77190aac ntdll!RtlDebugHeapHeap+0x2f
7714a8ff ntdll!RtlpFreeHeap+0x5d
770f2a32 ntdll!RtlFreeHeap+0x142
75bf14d1 kernel32!HeapFree+0x14
748d4c39 msvcrt80!free+0xcd
[...]
00a02bb2 ServiceA!ServiceMain+0x302
767175a8 sechost!ScSvcctrlThreadA+0x21
75fb3677 kernel32!BaseThreadInitThunk+0xe
770f9d42 ntdll!_RtlUserThreadStart+0x70
770f9d15 ntdll!_RtlUserThreadStart+0x1b
```

Here is another example that shows instrumentation difference. We run **Double Free** (page 267) fault modeling application and see its stack trace from a crash dump:

```
0:000> !gflag
Current NtGlobalFlag contents: 0x00000000
```