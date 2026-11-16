

```
0:000> ~2s
eax=00000000 ebx=00000000 ecx=1ba9f488 edx=00000001 esi=1952bd40 edi=00000000
eip=7c82860c esp=1ba9fff54 ebp=1ba9ffb8 iopl=0 nv up ei pl zr na pe nc
cs=001b ss=0023 ds=0023 es=0023 fs=003b gs=0000 efl=00240246
ntdll!KiFastSystemCallRet:
7c82860c ret
```

```
0:022> !teb
TEB at 7ff99000
ExceptionList: 1ba9ffdc
StackBase: 1baa0000
StackLimit: 1ba8f000
SubSystemTib: 00000000
FiberData: 00001e00
ArbitraryUserPointer: 00000000
Self: 7ff99000
EnvironmentPointer: 00000000
ClientId: 00001054 . 00001584
RpcHandle: 00000000
Tls Storage: 00000000
PEB Address: 7ffd5000
LastErrorValue: 0
LastStatusValue: c0000034
Count Owned Locks: 0
HardErrorMode: 0
```

```
0:022> dds 1ba8f000 1ba00000
1ba8f000 00000000
1ba8f004 00000000
[...]
1ba939e8 00000000
1ba939ec 00000000
1ba939f0 00000037
1ba939f4 1906e6c0
1ba939f8 064e1112 3rdPartyExtension!DllUnregisterServer+0xe1f1f
1ba939fc 1a042678
1ba93a00 034d2918
1ba93a04 00000000
1ba93a08 1a422660
1ba93a0c 00000008
1ba93a10 064e18ea 3rdPartyExtension!DllUnregisterServer+0xe26f7
1ba93a14 1a422678
1ba93a18 00000001
1ba93a1c 034d2870
1ba93a20 034d2b78
1ba93a24 0000001f
1ba93a28 00000007
1ba93a2c 034d2870
1ba93a30 1a01fc68
1ba93a34 00000001
1ba93a38 1ba93a54
1ba93a3c 064e1bf5 3rdPartyExtension!DllUnregisterServer+0xe2952
1ba93a40 034d2b78
1ba93a44 00000000
1ba93a48 00000000
1ba93a4c 06e7b498
1ba93a50 00000212
1ba93a54 1ba93c00
1ba93a58 6e4e3bce 3rdPartyExtension!DllUnregisterServer+0xe49db
1ba93a5c 00000001
1ba93a60 00000001
1ba93a64 00000000
1ba93a68 115d7fbc
1ba93a6c 0e67b498
1ba93a70 062de91d 3rdPartyExtension+0xe91d
1ba93a74 0000020c
1ba93a78 1ba93b78
1ba93a7c 06363797 3rdPartyExtension+0x93797
1ba93a80 00000024
1ba93a84 00000000
1ba93a88 00000000
1ba93a8c 1ba93ee0
[...]
```

```
0:022> ub 064e1112
3rdPartyExtension!DllUnregisterServer+0xe1f0d:
064e1100 jge 3rdPartyExtension!DllUnregisterServer+0xe1f16 (064e1109)
064e1102 mov ecx,dword ptr [ecx+10h]
064e1105 cmp ecx,eax
064e1107 jne 3rdPartyExtension!DllUnregisterServer+0xe1f0a (064e10fd)
064e1109 push ecx
064e110a push ebx
064e110b mov ecx,edi
064e110d call 3rdPartyExtension!DllUnregisterServer+0xe1d17 (064e0f0a)
```

## 值引用

有时我们有一个值或指针或句柄，想要知道所有引用它的内存地址。这可以通过虚拟内存搜索（s WinDbg 命令）来完成。如果我们要在代码中查找引用（例如，对于池标记，请参阅案例研究 215），可以将搜索与 !for_each_module WinDbg 扩展命令结合使用。还有用于物理页面的 !search 命令。我们在高级 Windows 内存转储分析培训 216 中介绍了此值引用模式，包含逐步完整的内存转储分析练习。对于对象引用，还有最近添加的 !obtrace 命令，WinDbg 帮助中有很好的示例。

## 注释

查找整个虚拟地址空间中指向某个值的指针的有用命令：!heap -x -v。

如果我们有一个带有句柄引用的对象，可以搜索其进程句柄容器，例如，对于僵尸进程，可以转储所有进程的所有句柄表：!handle 0 3 0 Process。

如果我们有对象地址，可以使用 !findhandle 来查找其进程容器：

```
002c: Object: fffffa80a95cb610 GrantedAccess: 001fffff Entry: fffff8a0000030b0
Object: fffffa80a95cb610 Type: (fffffa80a943bf30) Thread
ObjectHeader: fffffa80a95cb5e0 (new version)
HandleCount: 1 PointerCount: 2

0: kd> !findhandle fffffa80a95cb610
Now checking process fffffa80a943b6d0...
[fffffa80a943b6d0 System]
2c: Entry fffff8a0000030b0 Granted Access 1fffff
```

## 变量子迹

在分析 **Spiking 线程**（第 885 页）跨 **快照集合<sup>217</sup>** 时，我们有兴趣找出最可能负责的模块（或函数）（例如，内部“循环”）。在这里，我们可以比较来自不同内存转储的相同线程堆栈轨迹，并找到它们的**变量子迹**。对于这种子迹，我们会在 **kv 样式输出** 中看到变化：在返回地址、堆栈帧值和可能的参数中。启动变量子迹的调用点是最可能的候选者（取决于快照数量）。例如，考虑以下伪代码：

```
ModuleA!start()
{
    ModuleA!func1();
}
ModuleA!func1()
{
    ModuleB!func2();
}
ModuleB!func2()
{
    while (...)
    {
        ModuleB!func3();
    }
}
ModuleB!func3()
{
    ModuleB!func4();
}
ModuleB!func4()
{
    ModuleB!func5();
}
ModuleB!func5()
{
    // ...
}
```

这里，变量堆栈轨迹部分将对应于 _ModuleB_ 帧。内存转储可以保存在“while”循环内部的任何位置以及向下的调用中，堆栈轨迹向下的最后一个可变返回地址将属于 _ModuleB!func2_ 地址范围。不可变部分将从 _ModuleA!func1_ 地址范围开始：

```
// snapshot 1

RetAddr
ModuleB!func4+0x20
ModuleB!func3+0x10
ModuleB!func2+0x40
ModuleA!func1+0x10
ModuleA!start+0x300
```

```
// snapshot 2

RetAddr
ModuleB!func2+0x20
ModuleA!func1+0x10
ModuleA!start+0x300
```

```
// snapshot 3

RetAddr
ModuleB!func3+0x20
ModuleB!func2+0x40
ModuleA!func1+0x10
ModuleA!start+0x300
```

为了说明这种分析模式，我们采用了来自“加速反汇编、重构与反编译218”培训的内存单元图（MCD）方法，并在此介绍抽象堆栈轨迹记法（ASTN）图，其中不同模块使用不同颜色，变化使用不同填充模式突出显示。以下来自后续保存的进程内存转储的三个 ASTN 图说明了我们不久前分析的实际堆栈轨迹。我们看到，变量子迹仅包含第三方 ModuleB 调用。此外，循环可能包含在 ModuleB 内部，因为所有 ModuleA 帧都是不可变的，包括 Child-SP 和 Args 列的值。

![](img/d6dfefc8f9ab7106c77a723ff84aaa6d_1058_0.png)

| 标签 |
|-------|
| ModuleA |
| ModuleA |
| ModuleA |
| ModuleA |
| ModuleA |
| ModuleA |
| ModuleA |
| ModuleA |
| ModuleA |
| kernel32 |
| ntdll |

| 标签 |
|-------|
| kernel32 |
| ModuleB |
| ModuleB |
| ModuleB |
| ModuleB |
| ModuleA |
| ModuleA |
| ModuleA |
| ModuleA |
| ModuleA |
| ModuleA |
| ModuleA |
| ModuleA |
| ModuleA |
| ModuleA |
| ModuleA |
| ModuleA |
| ModuleA |
| ModuleA |
| ModuleA |
| ModuleA |
| ModuleA |
| ModuleA |
| kernel32 |
| ntdll |

![](img/d6dfefc8f9ab7106c77a723ff84aaa6d_1060_0.png)

如果我们有下面的 ASTN 图，我们将得出结论：循环位于 *ModuleA* 中，而 *ModuleB* 列的变化是执行的副作用：

![](img/d6dfefc8f9ab7106c77a723ff84aaa6d_1060_1.png)

![](img/d6dfefc8f9ab7106c77a723ff84aaa6d_1061_0.png)

![](img/d6dfefc8f9ab7106c77a723ff84aaa6d_1061_1.png)

![](img/d6dfefc8f9ab7106c77a723ff84aaa6d_1061_2.png)

| | | | | | ModuleA |
| | | | | | ModuleA |
| | | | | | ModuleA |
| | | | | | ModuleA |
| | | | | | ModuleA |
| | | | | | ModuleA |
| | | | | | ModuleA |
| | | | | | ModuleA |
| | | | | | ModuleA |
| | | | | | ModuleA |
| | | | | | kernel32 |
| | | | | | ntdll |

## 版本特定扩展

这是一种与 **平台特定调试器** 模式（第 804 页）类似的模式，通过建议进一步调试操作的方向来实现。当调试器依赖于与平台（或应用程序）版本不同的专用模块时，会给出类似说明。我们在此考虑一个 .NET 示例，其中打开转储仅显示它可能是手动保存的（**手动转储**，第 630 页），并可能带有需要挖掘的 **隐藏异常**（第 457 页）：

```
0:000> !analyze -v

FAULTING_IP:
+
00000000`00000000 ?? ???

EXCEPTION_RECORD: ffffffff`ffffffff -- (.exr 0xffffffffffffffff)
ExceptionAddress: 0000000000000000
ExceptionCode: 80000003 (Break instruction exception)
ExceptionFlags: 00000000
NumberParameters: 0
```

我们注意到 .NET 分析尝试失败，以及如何纠正它的以下说明：

```
_MANAGED_STACK: !dumpstack -EE
Failed to load data access DLL, 0x80004005
Verify that 1) you have a recent build of the debugger (6.2.14 or newer)
2) the file mscordacwks.dll that matches your version of mscorwks.dll is in the version directory
3) or, if you are debugging a dump file, verify that the file mscordacwks_<arch>_<arch>_<version>.dll is on your symbol path.
4) you are debugging on the same architecture as the dump file. For example, an IA64 dump file must be debugged on an IA64 machine.
```

您也可以运行调试器命令 .cordll 来控制调试器对 mscordacwks.dll 的加载。.cordll -ve -u -l 将执行详细重新加载。如果成功，SOS 命令应在重试后正常工作。

如果您正在调试小型转储，需要确保可执行文件路径也指向 mscorwks.dll。

因为我们知道在事后调试机器上安装了 .NET 框架，所以我们检查目标模块版本：

```
0:000> lmv m mscorwks
start end module name
00007fe`ee380000 00007fe`000007fe`eed1000 mscorwks (pdb symbols)
Loaded symbol image file: mscorwks.dll
Image path: C:\Windows\Microsoft.NET\Framework64\v2.0.50727\mscorwks.dll
Image name: mscorwks.dll
Timestamp: Sun Feb 06 20:53:54 2011 (4D4F0A62)
CheckSum: 00990593
ImageSize: 00990000
File version: 2.0.50727.5444
```

