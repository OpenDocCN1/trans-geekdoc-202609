# .NET CLR Monitors

This is a high contention pattern variant where the contention is around a monitor object. For example, we have a **Distributed CPU Spike** (page 243) for some threads:

```
0:000> !runaway
  User Mode Time
  Thread       Time
  9:6ff4    0 days 0:07:39.019
  12:6b88   0 days 0:06:19.786
  11:6bf0   0 days 0:06:13.889
  10:6930   0 days 0:06:09.240
  16:3964   0 days 0:05:44.483
  17:6854   0 days 0:05:35.326
  13:668c   0 days 0:05:35.123
  14:5594   0 days 0:05:34.858
  15:7248   0 days 0:05:23.111
  2:c54     0 days 0:00:41.215
  4:1080    0 days 0:00:00.349
  7:10f0    0 days 0:00:00.302
  0:c3c     0 days 0:00:00.271
[...]
```

If we look at their stack traces, we find them all blocked trying to enter a monitor⁹³, for example:

```
0:000> ~*k

[...]

 12 Id: d50.6b88 Suspend: 0 Teb: 000007ff`fff80000 Unfrozen
 Child-SP RetAddr Call Site
00000000`1a98e798 000007fe`fd0c1420 ntdll!ZwWaitForMultipleObjects+0xa
00000000`1a98e7a0 00000000`76e82cf3 KERNELBASE!WaitForMultipleObjectsEx+0xe8
00000000`1a98e8a0 000007fe`f82e0669 kernel32!WaitForMultipleObjectsExImplementation+0xb3
00000000`1a98e930 000007fe`f82bdec9 mscorwks!WaitForMultipleObjectsEx_SO_TOLERANT+0xc1
00000000`1a98e9d0 000007fe`f82a0569 mscorwks!Thread::DoAppropriateAptStateWait+0x41
00000000`1a98ea30 000007fe`f82beaec mscorwks!Thread::DoAppropriateWaitWorker+0x191
00000000`1a98eb30 000007fe`f81f1b9a mscorwks!Thread::DoAppropriateWait+0x5c
00000000`1a98eba0 000007fe`f82df3c9 mscorwks!CLREvent::WaitEx+0xbe
00000000`1a98ec50 000007fe`f81ac6be mscorwks!AwareLock::EnterEpilog+0xc9
00000000`1a98ed20 000007fe`f81c7b2b mscorwks!AwareLock::Enter+0x72
00000000`1a98ed50 000007fe`f87946af mscorwks!AwareLock::Contention+0x1fb
00000000`1a98ee20 000007ff`00161528 mscorwks!JITutil_MonContention+0xdf
00000000`1a98efd0 000007ff`0016140e 0x7ff`00161528
00000000`1a98f040 000007ff`00167271 0x7ff`0016140e
```