```
State:            00001000 MEM_COMMIT
Protect:          00000004 PAGE_READWRITE
```

Also, if we inspect the raw stack data, we don’t find any **Hidden Exceptions** (page 457) there. So we conclude that the missing thread was exceptional. Indeed, there is a saved exception context in the process memory dump:

```
0:000> .exr -1
ExceptionAddress: 08a9ae18 (<Unloaded_DllB.dll>+0x001cae18)
ExceptionCode: c0000005 (Access violation)
ExceptionFlags: 00000001
NumberParameters: 1
Parameter[0]: 00000008
```