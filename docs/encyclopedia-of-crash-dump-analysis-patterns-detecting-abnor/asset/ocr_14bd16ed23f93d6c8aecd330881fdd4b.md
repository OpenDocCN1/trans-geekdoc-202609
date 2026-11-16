# Value Adding Process

This is a frequently observed pattern in terminal services environments when we see one or several process names listed in each session but not necessarily required. They are usually running to provide some user experience enhancements. In such cases, if observed functional problems correspond to the purpose of running additional processes we might want to eliminate them for testing and troubleshooting purposes.

```
0: kd> !sprocess 12
Dumping Session 12

__MM_SESSION_SPACE fffff880e5d5000
__MMSESSION fffff880e5d5b40
PROCESS fffffa800d50b30
SessionId: 12 Cid: 0b04 Peb: 7ffffffdc000 ParentCid: 1478
DirBase: 6bb77000 ObjectTable: fffff8a003f280b0 HandleCount: 158.
Image: csrss.exe

PROCESS fffffa80030c7060
SessionId: 12 Cid: 1a48 Peb: 7fffffd8000 ParentCid: 1478
DirBase: 0a33c000 ObjectTable: fffff8a003c46c00 HandleCount: 179.
Image: winlogon.exe

PROCESS fffffa8008250b30
SessionId: 12 Cid: 18c8 Peb: 7fffffd000 ParentCid: 1a48
DirBase: 0350d000 ObjectTable: fffff8a0025b6840 HandleCount: 226.
Image: LogonUI.exe

PROCESS fffffa8008b00530
SessionId: 12 Cid: 1508 Peb: 7fffffd000 ParentCid: 02f0
DirBase: 02f65000 ObjectTable: fffff8a003b7e530 HandleCount: 197.
Image: ExcitingFeatureX.exe

[...]
```