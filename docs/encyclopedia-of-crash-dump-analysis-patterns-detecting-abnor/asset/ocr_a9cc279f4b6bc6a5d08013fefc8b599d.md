# Reference Leak

Objects such as processes may be referenced internally in addition to using handles. If their reference counts are unbalanced, we may have **Reference Leak** pattern. For example, we have an instance of thousands of **Zombie Processes** (page 1158), but we don’t see **Handle Leaks** (page 416) from their parent processes if we analyze ParentCids:

```
0: kd> !process 0 0
[...]
PROCESS fffffa801009a060
    SessionId: 0  Cid: 2e270    Peb: 7fffffdb000  ParentCid: 032c
    DirBase: 12ba37000  ObjectTable: 00000000  HandleCount:  0.
    Image: conhost.exe

PROCESS fffffa8009b7e8e0
    SessionId: 1  Cid: 2e0c8    Peb: 7fffffd9000  ParentCid: 10a0
    DirBase: 21653e000  ObjectTable: 00000000  HandleCount:  0.
    Image: taskmgr.exe

PROCESS fffffa8009e7a450
    SessionId: 0  Cid: 2e088    Peb: 7efdf0000  ParentCid: 0478
    DirBase: 107f02000  ObjectTable: 00000000  HandleCount:  0.
    Image: AppA.exe

PROCESS fffffa8009e794b0
    SessionId: 0  Cid: 2e394    Peb: 7fffffd3000  ParentCid: 032c
    DirBase: 210ffc000  ObjectTable: 00000000  HandleCount:  0.
    Image: conhost.exe

PROCESS fffffa8009ed4060
    SessionId: 0  Cid: 2dee4    Peb: 7efdf0000  ParentCid: 0478
    DirBase: 11b7c7000  ObjectTable: 00000000  HandleCount:  0.
    Image: AppB.exe

PROCESS fffffa800a13bb30
    SessionId: 0  Cid: 2e068    Peb: 7fffffd5000  ParentCid: 032c
    DirBase: 1bb3c1000  ObjectTable: 00000000  HandleCount:  0.
    Image: conhost.exe

PROCESS fffffa80096f26b0
    SessionId: 0  Cid: 2e320    Peb: 7efdf0000  ParentCid: 0478
    DirBase: 6ad4c000  ObjectTable: 00000000  HandleCount:  0.
    Image: AppC.exe

PROCESS fffffa8009c44060
    SessionId: 0  Cid: 2e300    Peb: 7fffffd0000  ParentCid: 032c
    DirBase: 10df06000  ObjectTable: 00000000  HandleCount:  0.
    Image: conhost.exe
[...]
```