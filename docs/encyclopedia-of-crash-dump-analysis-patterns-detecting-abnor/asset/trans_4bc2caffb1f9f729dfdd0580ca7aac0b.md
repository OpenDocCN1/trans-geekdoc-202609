

未加载的模块：
```
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

UNICODE 模块名称的部分也出现在校验和和时间戳中。此类部分模块名称可能出现在线程堆栈和原始堆栈数据中，例如：

```
0:000> kl
ChildEBP RetAddr
[...]
0015efc3 0366afc2 ModuleA!Validation+0x5b
WARNING: Frame IP not in any known module. Following frames may be wrong.
0015efcc 79e7c7a6 <Unloaded_ure.dll>+0x366afc1
03dc9b70 00000000 mscorwks!MethodDesc::CallDescr+0x1f
```

默认分析也受害，并建议您在系统中费力寻找 ure.dll：

```
MODULE_NAME: ure

IMAGE_NAME: ure.dll

DEBUG_FLR_IMAGE_TIMESTAMP:  750063

FAILURE_BUCKET_ID:  ure.dll!Unloaded_c0000005_APPLICATION_FAULT
```

时间戳可疑地类似于 UNICODE。在这种情况下，我们甚至可以重建模块名称：

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

```
0:000> .formats 00680054
Evaluate expression:
Hex: 00680054
Decimal: 6815828
Octal: 00032000124
Binary: 00000000 01101000 00000000 01010100
Chars: .h.T
Time: Fri Mar 20 21:17:08 1970
Float: low 9.55101e-039 high 0
Double: 3.36747e-317
```

我们将 UNICODE 的 Ux 和 Th 与 eme.dll 连接起来，得到 UxTheme.dll，这是一个可以在系统中找到的真实 DLL 名称。

## 注入符号

当我们拥有**减少的符号信息**（第 829 页）时，可以使用此模式添加缺失的符号，就像之前在这个旧案例研究 103 中所做的那样。例如，TestWER104 模块是使用静态 MFC 和 CRT 库编译的，其私有 PDB 文件包含所有必要的符号，包括 MSG 结构。我们可以将该模块加载到 notepad.exe 进程空间并应用符号：

```
0:000:x86> lm
start             end                 module name
00fc0000 00fff000   notepad   (pdb
symbols)       c:\mss\notepad.pdb\E325F5195AE94FAEB58D25C9DF8C0CFD2\notepad.pdb
10000000 10039000   WinCRT   (deferred)
727f0000 7298e000   comctl32   (deferred)
72aa0000 72af1000   winspool   (deferred)
72b10000 72b19000   version   (deferred)
72e40000 72e48000   wow64cpu   (deferred)
72e50000 72eac000   wow64win   (pdb
symbols)       c:\mss\wow64win.pdb\B2D08CC152D64E71B79167DC0A0A53E91\wow64win.pdb
72eb0000 72ee0000   wow64   (deferred)
733d0000 733e3000   dwmapi   (deferred)
735b0000 73606000   uxtheme   (deferred)
746f0000 746fc000   CRYPTBASE   (deferred)
74700000 74760000   sspicli   (deferred)
747c0000 74817000   shlwapi   (deferred)
74830000 7547a000   shell32   (deferred)
755d0000 756ab000   comdlg32   (deferred)
75650000 7567e000   imm32   (deferred)
75770000 75810000   advapi32   (deferred)
75810000 75920000   kernel32   (pdb
symbols)       c:\mss\kernel32.pdb\1C690A8592304467BB15A09CEA7180FA2\kernel32.pdb
75920000 759b0000   gdi32   (deferred)
759b0000 759f7000   KERNELBASE   (deferred)
75a00000 75b00000   user32   (pdb
symbols)       c:\mss\user32.pdb\0FCE9CC301ED4567A819705B2718E1D62\user32.pdb
75b00000 75b8f000   oleaut32   (deferred)
[...]
76e40000 76fe9000   ntdll   (deferred)
77020000 771a0000   ntdll_77020000   (pdb
symbols)       c:\mss\wntdll.pdb\D74F79EB1F8D4A45ABCD2F476CCABA2C\wntdll.pdb
0:000:x86> .sympath+ C:\DebuggingTV\TestWER\x86
Symbol search path is: srv*;C:\DebuggingTV\TestWER\x86
Expanded Symbol search path is: SRV*c:\mss*http://msdl.microsoft.com/download/symbols;c:\debuggingtv\testwer\x86
```

```
0:000:x86> .reload /f /i C:\DebuggingTV\TestWER\x86\TestWER.exe=10000000
```

```
0:000:x86> lm
start    end        module name
00fc0000 00ff0000   notepad      (pdb symbols)       c:\...\notepad.pdb
10000000 10039000   TestWER      (private pdb symbols) c:\...\TestWER.pdb
727f0000 7298e000   comctl32     (deferred)
721a0000 721af000   winspool   (deferred)
72b10000 72b19000   version    (deferred)
72e40000 72e48000   wow64cpu   (deferred)
72e50000 72eac000   wow64win   (pdb symbols) c:\...\wow64win.pdb
72eb0000 72eef000   wow64      (deferred)
733d0000 733e3000   dwmapi     (deferred)
735b0000 73606000   uxtheme    (deferred)
746f0000 746fc000   CRYPTBASE  (deferred)
74700000 74760000   sspicli    (deferred)
747c0000 74817000   shlwapi    (deferred)
74830000 7547a000   shell32    (deferred)
755d0000 7564b000   comdlg32   (deferred)
75650000 7567e000   imm32      (deferred)
75770000 75810000   advapi32   (deferred)
75810000 75920000   kernel32   (pdb symbols) c:\...\wkernel32.pdb
75920000 759b0000   gdi32      (deferred)
759b0000 759f7000   KERNELBASE (deferred)
75a00000 75b00000   user32     (pdb symbols) c:\...\wuser32.pdb
75b00000 75b8f000   oleaut32   (deferred)
[...]
76e40000 76fe9000   ntdll      (deferred)
77020000 771a0000   ntdll_77020000  (pdb symbols) c:\...\wntdll.pdb
```

```
0:000:x86> kv
ChildEBP RetAddr  Args to Child
0013fe34 75a1790d 0013fe74 00000000 00000000 user32!NtUserGetMessage+0x15
0013fe50 00fc148a 0013fe74 00000000 00000000 user32!GetMessageW+0x33
0013fe90 00fc16ec 00fc0000 00000000 00354082 notepad!WinMain+0xe6
0013ff20 758233a0 7efde000 0013ff6c 77059ef2 notepad!_initterm_e+0x1a1
0013ff2c 77059ef2 7efde000 57785ae0 00000000 kernel32!BaseThreadInitThunk+0xe
0013ff6c 77059ec5 00fc3689 7efde000 00000000 ntdll_77020000!_RtlUserThreadStart+0x70
0013ff84 00000000 00fc3689 7efde000 00000000 ntdll_77020000!_RtlUserThreadStart+0x1b
```

```
0:000:x86> dt -r MSG 0013fe74
TestWER!MSG
+0x000 hwnd            : 0x0007149c HWND__
+0x000 unused           : ??
+0x004 message          : 0x113
+0x008 wParam           : 0x38a508
+0x00c lParam           : 0n1921500630
+0x010 time             : 0x2079a177
+0x014 pt
   +0x000 x              : 0n1337
   +0x004 y              : 0n448
```

## 内联函数优化

## 托管代码

除了非托管和本机代码的**内联函数优化**（第 514 页）之外，我们还可以看到类似方法应用于 JIT 编译的代码：

```
public class ClassMain
{
    public bool time2stop = false;

    public static void Main(string[] args)
    {
        new ClassMain().Main();
    }

    public void Main()
    {
        while (!time2stop)
        {
            DoWork();
        }
    }

    volatile int inSensor, outSensor;

    void DoWork()
    {
        outSensor ^= inSensor;
    }
}
```

```
0:000> kl
ChildEBP RetAddr
WARNING: Frame IP not in any known module. Following frames may be wrong.
001fefa0 79e7c6cc 0x3200a4
001ff020 79e7c8e1 mscorwks!CallDescrWorkerWithHandler+0xa3
001ff160 79e7c783 mscorwks!MethodDesc::CallDescr+0x19c
001ff17c 79e7c90d mscorwks!MethodDesc::CallTargetWorker+0x1f
001ff190 9eeef9e5 mscorwks!MethodDesc::CallSite::Call_RetArgSlot+0x18
001ff2f4 79eef830 mscorwks!ClassLoader::RunMain+0x263
001ff55c 79ef01da mscorwks!Assembly::ExecuteMainMethod+0xa6
001ffa2c 79fb9793 mscorwks!SystemDomain::ExecuteMainMethod+0x43f
001ffa7c 79fb96df mscorwks!ExecuteEXE+0x59
001ffac4 736455ab mscorwks!_CorExeMain+0x15c
001ffad0 73747f16 mscoreei!_CorExeMain+0x38
001ffae0 73744de3 mscoreei!ShellShim__CorExeMain+0x99
001ffae8 76573833 mscoreei!_CorExeMain_Exported+0x8
001ffaf4 77c1a9bd kernel32!BaseThreadInitThunk+0xe
001ffb34 00000000 ntdll!_RtlUserThreadStart+0x23
```

```
0:000> r
eax=00000000 ebx=001fefbc ecx=015316e0 edx=0037a238 esi=0037a238 edi=00000000
eip=003200a4 esp=001fef90 ebp=001fefaf iopl=0 nv up ei pl zr na pe nc
cs=001b ss=0023 ds=0023 es=0023 fs=003b gs=0000 efl=00000246
003200a4 8079c00 cmp byte ptr [ecx+0Ch],0 ds:0023:015316ec=00
```

```
0:000> !IP2MD 003200a4
MethodDesc:   000d3048
Method Name:  ClassMain.Main()
Class:        000d1180
MethodTable:  000d3060
mdToken:      06000002
Module:       000d2c3c
IsJitted:     yes
m_CodeOrIL:   00320098
```

```
0:000> .asm no_code_bytes
Assembly options: no_code_bytes
```

```
0:000> !U 003200a4
Normal JIT generated code
ClassMain.Main()
Begin 00320098, size 13
00320098 cmp byte ptr [ecx+0Ch],0
0032009c jne 003200aa
0032009e mov eax,dword ptr [ecx+4]
003200a1 or dword ptr [ecx+8],eax
>>> 003200a4 cmp byte ptr [ecx+0Ch],0
003200a8 je 0032009e
003200aa ret
```

我们看到 DoWork 代码已内联到 Main 函数代码中。

