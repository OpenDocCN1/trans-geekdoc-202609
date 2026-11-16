+   suspicious path names

```
Age: 7, Pdb: d:\work\BekKonnekt\Client_src_code_New\Release\Blackjoe_new.pdb

Debug Directories(1)

Type Size Address Pointer
cv 46 2094 894 Format: RSDS, guid, 1, C:\MyWork\screens_dll\Release\screens_dll.pdb
```

+   suspicious image path (although could be just dynamic code generation for .NET assemblies)

+   uninitialized image resources

```
0:002> lmv m C6DC
start    end        module name
012a0000 012a9000   C6DC    C (no symbols)
    Loaded symbol image file: C6DC.tmp
    Image path: C:\Users\User\AppData\Local\Temp\C6DC.tmp
    Image name: C6DC.tmp
    Timestamp:        Sun May 30 20:18:32 2010 (4C02BA08)
    CheckSum:         00000000
    ImageSize:        00009000
    File version:     0.0.0.0
    Product version:  0.0.0.0
    File flags:       0 (Mask 0)
    File OS:          0 Unknown Base
    File type:        0.0 Unknown
    File date:        00000000.00000000
    Translations:     0000.04b0 0000.04e4 0409.04b0 0409.04e4
```

# Comments

.imgscan might not be able to find all hidden modules (**Debugger Omission** pattern, page 220).

Timestamps might be suspicious too.