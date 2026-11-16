```
0: kd> dp rbx+28 L10
00000000`023ac150 00000000`00001244 00000000`000001b5
00000000`023ac160 00000000`0000f3fc ffffffff`00000000
00000000`023ac170 00000000`000021ac 00000000`00000000
00000000`023ac180 00000000`02735fc0 00000000`00000001
00000000`023ac190 00000000`00000000 01cf07ac`9fa06d27
00000000`023ac1a0 00000000`00000000 00000000`00000000
00000000`023ac1b0 ffffffff`ffffffff 00000000`00000000
00000000`023ac1c0 00000000`00000000 00000000`00000000
```

We check all these handles (OwnerThread seems comes earlier with NumberActive field missing, but that could just differences between the old x86 structure implemented in ReactOS and x64 Windows):

```
0: kd> !handle 00000000`00001244

PROCESS fffffff8a04a16b260
SessionId: 0 Cid: 03c0    Peb: 7fffffdc000  ParentCid: 0350
DirBase: 195950000  ObjectTable: fffffff8a0032424e0  HandleCount: 5252.
Image: lsm.exe

Handle table at fffffff8a0032424e0 with 5252 entries in use

1244: Object: fffffff8a04a79ad50  GrantedAccess: 00100003 Entry: fffffff8a022b39910
Object: fffffff8a04a79ad50  Type: (fffff8a048fc8790) Semaphore
ObjectHeader: fffffff8a04a79ad20 (new version)
HandleCount: 1  PointerCount: 438
```

```
0: kd> !handle 00000000`00000f3c

PROCESS fffffff8a04a16b260
SessionId: 0 Cid: 03c0    Peb: 7fffffdc000  ParentCid: 0350
DirBase: 195950000  ObjectTable: fffffff8a0032424e0  HandleCount: 5252.
Image: lsm.exe

Handle table at fffffff8a0032424e0 with 5252 entries in use

0f3c: Object: fffffff8a04fa81f60  GrantedAccess: 00100003 Entry: fffffff8a02cd3ecf0
Object: fffffff8a04fa81f60  Type: (fffff8a048fc8790) Semaphore
ObjectHeader: fffffff8a04fa81f30 (new version)
HandleCount: 1  PointerCount: 1
```