# Reduced Symbolic Information

Sometimes we have reduced symbolic information for modules which can range from stripped or public symbol files to exported only function names. In such cases we can use API function prototypes, structure definitions and possible String Parameters (page 962) to make sense of function arguments:

```
0:000:x86> kv
ChildEBP RetAddr  Args to Child
0013fe34 75a1790d 0013fe74 00000000 00000000 user32!NtUserGetMessage+0x15
0013fe50 00fc148a 0013fe74 00000000 00000000 user32!GetMessageW+0x33
0013fe90 00fc16ec 00fc0000 00000000 00354082 notepad!WinMain+0xe6
0013ff20 758233aa 7efde000 0013ffc7 77059ef2 notepad!_initterm_e+0xa1
0013ff2c 77059ef2 7efde000 57785ae5 00000000 kernel32!BaseThreadInitThunk+0xe
0013ff6c 77059ec5 00fc3689 7efde000 00000000 ntdll!77020000!_RtlUserThreadStart+0x70
0013ff84 00000000 00fc3689 7efde000 00000000 ntdll!77020000!_RtlUserThreadStart+0x1b
```

The first parameter of GetMessage API is a pointer to MSG structure:

```
0:000:x86> dt MSG 0013fe74
Symbol MSG not found.
```

From MSDN we find this structure definition:

```
typedef struct tagMSG {
    HWND   hwnd;
    UINT   message;
    WPARAM wParam;
    LPARAM lParam;
    DWORD  time;
    POINT  pt;
} MSG, *PMSG, *LPMSG;
```

```
0:000:x86> dc 0013fe74 L7
0013fe74  0007149c  00000113  0038a508  7287c5d6  .......8....r
0013fe84  2079a177  00000539  000001c0        w.y 9.......
```