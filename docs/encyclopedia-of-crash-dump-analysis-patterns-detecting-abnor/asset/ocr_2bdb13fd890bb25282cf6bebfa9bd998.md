```
0012f8e0 76ee1039 verifier!except_handler4+0x8e
0012f904 76ee100b ntdll!ExecuteHandler2+0x26
0012f9ac 76ee0e97 ntdll!ExecuteHandler+0x24
0012f9ac 71aaa3ad ntdll!KiUserExceptionDispatcher+0xf
0012fcf0 71aaa920 verifier!AVrfpDphCheckNormalHeapBlock+0x5d
0012fd0c 71aa879b verifier!AVrfpDphNormalHeapFree+0x20
0012fd60 76f31c4f verifier!AVrfDebugPageHeapFree+0x1cb
0012fda8 76efd9fa ntdll!RtlDebugFreeHeap+0x2f
0012fe9c 76ee1c21 ntdll!RtlpFreeHeap+0x5f
0012feb8 758d7a7e ntdll!RtlFreeHeap+0x14e
0012fecc 6cff4c39 kernel32!HeapFree+0x14
0012ff18 0040105f msvcr80!free+0xcd
0012ff5c 004011f1 DoubleFree!wmain+0x5f
0012ffa0 758d3833 DoubleFree!__tmainCRTStartup+0x10f
0012ffac 76eba9bd kernel32!BaseThreadInitThunk+0xe

0:000> !gflag
Current NtGlobalFlag contents: 0x02000000
hpa - Place heap allocations at ends of pages
```

If we enable heap free checking instead of page heap we get our crash on the first double free call immediately too:

![](bbox=[0.24, 0.45, 0.76, 0.94])