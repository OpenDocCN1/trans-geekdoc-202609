# Hidden Stack Trace

Sometimes, a stack trace from **Stack Trace Collection** (page 943) may look well-formed at first sight, for example, having an expected start frames:

```
0:000> ~*k

[...]
# 19 Id: 16a4.21f4 Suspend: 0 Teb: 7e95b000 Unfrozen
ChildEBP RetAddr
0c2de6b0 74eb112f ntdll!NtWaitForMultipleObjects+0xc
0c2de83c 76ca7b89 KERNELBASE!WaitForMultipleObjectsEx+0xcc
0c2de858 76d0b7bf kernel32!WaitForMultipleObjects+0x19
0c2dec98 76d00295 kernel32!WerpReportFaultInternal+0x50b
0c2deca8 76ce1709 kernel32!WerpReportFault+0x74
0c2decb4 74f5f705 kernel32!BasepReportFault+0x19
0c2ded3c 76fb4f84 KERNELBASE!UnhandledExceptionFilter+0x1f4
0c2ded54 76fb5728 ntdll!TppExceptionFilter+0x30
0c2ded64 76fc595a ntdll!TppWorkerpInnerExceptionFilter+0xe
0c2df914 76fc7c04 ntdll!TppWorkerThread+0x87f5a
0c2df928 76f1ad1f kernel32!BaseThreadInitThunk+0x24
0c2df970 76f1acea ntdll!_RtlUserThreadStart+0x2f
0c2df980 00000000 ntdll!_RtlUserThreadStart+0x1b
[...]
```

So, we may think something wrong happened in `ntdll!TppWorkerThread` code (although 0x87f5a offset looks suspicious). However, in reality, in this case, due to exception filter logic (or some other reason in different cases), we have **Hidden Stack Trace**. When looking at `UnhandledExceptionFilter` parameters (or raw stack as in the case of **Hidden Exceptions**, page 455), we find an exception context:

```
0:019> kv
ChildEBP RetAddr Args to Child
0c2de6b0 74eb112f 00000003 0c2de880 00000001 ntdll!NtWaitForMultipleObjects+0xc
0c2de83c 76ca7b89 00000003 0c2de880 00000000 KERNELBASE!WaitForMultipleObjectsEx+0xcc
0c2de858 76d0b7bf 00000003 0c2de880 00000000 kernel32!WaitForMultipleObjects+0x19
0c2dec98 76d00295 00000000 00000001 00000000 kernel32!WerpReportFaultInternal+0x50b
0c2deca8 76ce1709 0c2ded3c 74f5f705 0c2ded94 kernel32!WerpReportFault+0x74
0c2decb4 74f5f705 0c2ded94 00000001 a79b7895 kernel32!BasepReportFault+0x19
0c2ded3c 76fb4f84 0c2ded94 0c2ded94 00000000 KERNELBASE!UnhandledExceptionFilter+0x1f4
0c2ded54 76fb5728 00000000 00000000 0c2df914 ntdll!TppExceptionFilter+0x30
0c2ded64 76fc595a 0c2df8d0 76f0a070 0c2df914 ntdll!TppWorkerpInnerExceptionFilter+0xe
0c2df914 76fc7c04 0f79e380 76ca7be0 0ab54024 ntdll!TppWorkerThread+0x87f5a
0c2df928 76f1ad1f 0f79e380 a59141d7 00000000 kernel32!BaseThreadInitThunk+0x24
0c2df970 76f1acea ffffffff 76f00233 00000000 ntdll!_RtlUserThreadStart+0x2f
0c2df980 00000000 76e4a00 0f79e380 00000000 ntdll!_RtlUserThreadStart+0x1b
0:019> dd 0c2ded94 L2
0c2ded94 0c2deef8 0c2def48
```