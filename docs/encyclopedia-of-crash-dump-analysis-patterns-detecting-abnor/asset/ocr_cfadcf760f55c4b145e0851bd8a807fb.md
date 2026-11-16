If we compare with the last session #8 we see that the latter has only two processes:

```
0: kd> !sprocess 8
Dumping Session 8

__MM_SESSION_SPACE fffffffa600bafc000
_MMSESSION fffffffa600bafcb40
PROCESS fffffa80103a4480
SessionId: 8 Cid: 2858 Peb: 7fffffdff000 ParentCid: 2660
DirBase: a04bb000 ObjectTable: fffffff8801cb926a0 HandleCount: 534.
Image: csrss.exe

PROCESS fffffa801065b770
SessionId: 8 Cid: 2878 Peb: 7fffffdff000 ParentCid: 2660
DirBase: 5da40000 ObjectTable: fffffff8801ce5e440 HandleCount: 235.
Image: winlogon.exe
```

Such anomalies may point to a disconnected session that failed to terminate due to some unresponsive session process, or a session that is stuck in session initialization process launch sequence due to threads blocked in wait chains. Here process threads need to be analyzed.

# Comments

Terminal session management systems may also preallocate sessions to make logon faster.

In the case of many terminal sessions on Windows we can dump processes sorted by session via !sprocess -4 to spot **Incomplete Sessions** (page 496).