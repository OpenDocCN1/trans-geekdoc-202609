```
00bfffb4 7c57b3bc ntdll!RtlpTimerThread+0x42
00bfffec 00000000 KERNEL32!BaseThreadStart+0x52

1: kd> dds 0006fee0
0006fee0 0006ff08
0006fee4 76b93701 3rdPartyGINA!WlxDisplaySASNotice+0x43
0006fee8 000755e8
0006feec 76b90000 3rdParty
0006fef0 00000578
0006fef4 00000000
0006fef8 76b9370b 3rdParty!WlxDisplaySASNotice+0x4d
0006fefc 00080de0
0006ff00 00000008
0006ff04 00000080
0006ff08 0006ff20
0006ff0c 010164c6 winlogon!MainLoop+0x96
0006ff10 00080de0
0006ff14 5ffa0000
0006ff18 000755e8
0006ff1c 00000000
0006ff20 0006ff58
0006ff24 01014960 winlogon!WinMain+0x37a
0006ff28 000755e8
0006ff2c 00000005
0006ff30 0072c9c
0006ff34 00000001
0006ff38 000001bc
0006ff3c 00000005
0006ff40 00000001
0006ff44 0000000d
0006ff48 00000000
0006ff4c 00000000
0006ff50 00000000
0006ff54 0000ffe4
0006ff58 006ffff4
0006ff5c 0101cd06 winlogon!WinMainCRTStartup+0x156
```

We can also filter stacks that belong to processes having the same module name, for example, `svchost.exe`201.

Sometimes the collection of all stack traces from all threads in the system can disprove or decrease the plausibility of the hypothesis that some module is involved. In one case, the customer claimed that the specific driver was involved in the server freeze. However, there was no such module found in all thread stacks.

# Comments

There are also commands **!sprocess** and **!for_each_thread**.