```
Unloaded modules:
00410053 008a00a3  Unknown_Module_00410053
    Timestamp: Tue Mar 17 20:27:26 1970 (0064002E)
    Checksum: 006CC06C
00010755 007407c5  1
    Timestamp: Wed Feb 04 21:26:01 1970 (002E0069)
    Checksum: 006CC064
00000011 411096d2  eme.dll
    Timestamp: Thu Apr 02 01:33:25 1970 (00780055)
    Checksum: 00680054
Missing image name, possible paged-out or corrupt data.
0064002e 000d009a  Unknown_Module_0064002e
    Timestamp: unavailable (00000000)
    Checksum: 00000000
```

Here parts of UNICODE module names appear in checksums and timestamps as well. Such partial module names can appear on thread stacks and raw stack data, for example:

```
0:000> kl
ChildEBP RetAddr
[...]
0015efc3 0366afc2 ModuleA!Validation+0x5b
WARNING: Frame IP not in any known module. Following frames may be wrong.
0015efcc 79e7c7a6 <Unloaded_ure.dll>+0x366afc1
03dc9b70 00000000 mscorwks!MethodDesc::CallDescr+0x1f
```

Default analysis falls victim too and suggests ure.dll that you would try hard to find on your system:

```
MODULE_NAME: ure

IMAGE_NAME: ure.dll

DEBUG_FLR_IMAGE_TIMESTAMP:  750063

FAILURE_BUCKET_ID:  ure.dll!Unloaded_c0000005_APPLICATION_FAULT
```

The timestamp is suspiciously UNICODE-like. In such cases, we can even reconstruct the module name:

```
00000011 411096d2  eme.dll
    Timestamp: Thu Apr 02 01:33:25 1970 (00780055)
    Checksum: 00680054

0:000> .formats 00780055
Evaluate expression:
  Hex:     00000000`00780055
  Decimal: 7864405
  Octal:   000000000000036000125
  Binary:  00000000 00000000 00000000 00000000 00000000 00000000 01111000 00000000 01010101
  Chars:   .....x.U
  Time:    Thu Apr 02 01:33:25 1970
  Float:   low 1.10204e-038 high 0
  Double:  3.88553e-317
```