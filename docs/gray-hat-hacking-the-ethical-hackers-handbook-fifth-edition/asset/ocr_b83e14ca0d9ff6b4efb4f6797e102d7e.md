```
$ ~/android/dex2jar-0.0.9.15/d2j-dex2jar.sh classes.dex
dex2jar classes.dex -> classes-dex2jar.jar
```

To see the source code in JD-GUI, open the file classes-dex2jar.jar. Figure 18-1 shows JD-GUI with decompiled Java source code. It is possible to export all decompiled class files from JD-GUI using the File | Save All Sources option.

![](bbox=[0.12, 0.2, 0.88, 0.805])

Figure 18-1 JD-GUI decompiled Java source code

One problem with decompilers is that they are very sensitive to byte code modification, which can prevent them from recovering any sensible source code. Another problem with decompilers is that they don't offer a side-by-side comparison with disassembly, and wrong