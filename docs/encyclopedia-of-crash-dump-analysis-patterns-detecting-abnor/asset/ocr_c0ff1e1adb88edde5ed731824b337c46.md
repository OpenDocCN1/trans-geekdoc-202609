```
func() { func2(1); }      func2(int i) { int var; };
push 1                    push ebp                    sub esp, 4
call func2                mov ebp, esp
```

![](bbox=[0.18, 0.19, 0.83, 0.4])

```
0:011> !teb
TEB at 7ffd8000
    ExceptionList: 0184ebdc
    StackBase: 01850000
    StackLimit: 01841000
    SubSystemTib: 00000000
    FiberData: 00001e00
    ArbitraryUserPointer: 00000000
    Self: 7ffd8000
    EnvironmentPointer: 00000000
    ClientId: 0000061c . 00001b60
    RpcHandle: 00000000
    Tls Storage: 00000000
    PEB Address: 7ffdf000
    LastErrorValue: 0
    LastStatusValue: c0000034
    Count Owned Locks: 0
    HardErrorMode: 0
```

```
0:011> dds 01841000 01850000
01841000 00000000
...
...
...
0184eef0 0184ef0c
0184eef4 7615df2 localspl!SplDriverEvent+0x21
0184eef8 00bc3e08
0184eefc 00000003
0184ef00 00000001
0184ef04 00000000
0184ef08 0184efb0
0184ef0c 0184ef30
```