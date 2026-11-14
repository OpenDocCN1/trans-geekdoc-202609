```
00401000 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 .......00401010 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 .......00401020 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 .......00401030 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 .......00401040 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 .......
```

By stepping into the next instructions, we see that the whole text section is loaded with the real malicious instructions. If we keep stepping into the code, we see that the processes are enumerated. Therefore, let’s set a breakpoint on the proper API in the debugger command box again:

```
bp CreateToolhelp32Snapshot
```

Press F9, and when the breakpoint is hit, press ALT-F9 to return to the malware code at the address 0x0040DE6B. There, we see instructions without them being properly disassembled by the debugger, as shown here:

![](bbox=[0.117, 0.345, 0.882, 0.603])

Let’s make the debugger display those instructions properly by right-clicking any instruction in the upper-left window and selecting the option Analysis | Remove Analysis from Module, as shown here: