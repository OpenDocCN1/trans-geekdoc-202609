

```
0: kd> ub fffffff880`0177e271
DriverA!CallProvider+0x13e:
fffff880`0177e24e mov     qword ptr [r11-10h],rax
fffff880`0177e252 mov     qword ptr [r11-8],r12
fffff880`0177e256 mov     byte  ptr [r11-45h],0E0h
fffff880`0177e25b mov     rcx,qword ptr [rdi+40h]
fffff880`0177e25f call    qword ptr [DriverA!_imp_IoGetAttachedDevice (fffff880`017790b0)]
fffff880`0177e265 mov     rdx,rbp
fffff880`0177e268 mov     rcx,rax
fffff880`0177e26b call    qword ptr [DriverA!_imp_IofCallDriver (fffff880`01779068)]
```

## 用户模式

用户模式下的栈溢出模式具有其自身的特征异常代码和堆栈跟踪：

```
FAULTING_IP:
StackOverflow!SoFunction+27
00401317 6a00 push 0

EXCEPTION_RECORD: fffffffd -- (.exr 0xffffffffffffffff)
ExceptionAddress: 00401300 (StackOverflow!SoFunction+0x00000010)
  ExceptionCode: c00000fd (Stack overflow)
  ExceptionFlags: 00000000
NumberParameters: 2
  Parameter[0]: 00000001
  Parameter[1]: 00882ffc
```

0:000> kL

| 子 EBP | 返回地址 | 符号 |
|---|---|---|
| 00083000 | 00401317 | StackOverflow!SoFunction+0x10 |
| 00083010 | 00401317 | StackOverflow!SoFunction+0x27 |
| 00083020 | 00401317 | StackOverflow!SoFunction+0x27 |
| 00083030 | 00401317 | StackOverflow!SoFunction+0x27 |
| 00083040 | 00401317 | StackOverflow!SoFunction+0x27 |
| 00083050 | 00401317 | StackOverflow!SoFunction+0x27 |
| 00083060 | 00401317 | StackOverflow!SoFunction+0x27 |
| 00083070 | 00401317 | StackOverflow!SoFunction+0x27 |
| 00083080 | 00401317 | StackOverflow!SoFunction+0x27 |
| 00083090 | 00401317 | StackOverflow!SoFunction+0x27 |
| 000830a0 | 00401317 | StackOverflow!SoFunction+0x27 |
| 000830b0 | 00401317 | StackOverflow!SoFunction+0x27 |
| 000830c0 | 00401317 | StackOverflow!SoFunction+0x27 |
| 000830d0 | 00401317 | StackOverflow!SoFunction+0x27 |
| 000830e0 | 00401317 | StackOverflow!SoFunction+0x27 |
| 000830f0 | 00401317 | StackOverflow!SoFunction+0x27 |
| 00083100 | 00401317 | StackOverflow!SoFunction+0x27 |
| 00083110 | 00401317 | StackOverflow!SoFunction+0x27 |
| 00083120 | 00401317 | StackOverflow!SoFunction+0x27 |
| 00083130 | 00401317 | StackOverflow!SoFunction+0x27 |

可能会有成千上万个堆栈帧：

```
0:000> kL 2000
...
000a2fa0 00401317 StackOverflow!SoFunction+0x27
000a2fb0 00401317 StackOverflow!SoFunction+0x27
000a2fc0 00401317 StackOverflow!SoFunction+0x27
000a2fd0 00401317 StackOverflow!SoFunction+0x27
000a2fe0 00401317 StackOverflow!SoFunction+0x27
000a2ff0 00401317 StackOverflow!SoFunction+0x27
```

要到达底部并避免过度滚动，我们可以转储原始堆栈数据，搜索 StackOverflow!SoFunction+0x27 的重复模式的结束位置，并尝试手动重建堆栈跟踪的底部：

0:000> !teb

| 属性 | 值 |
|---|---|
| TEB 地址 | 7efdd000 |
| 异常列表 | 0017fdf0 |
| 堆栈基址 | 00180000 |
| 堆栈限制 | 00081000 |
| 子系统 TIB | 00000000 |
| 协程数据 | 00001e00 |
| 任意用户指针 | 00000000 |
| 自身 | 7efdd000 |
| 环境指针 | 00000000 |
| 客户端 ID | 00001dc4 . 00001b74 |
| RPC 句柄 | 00000000 |
| TLS 存储 | 7efdd02c |
| PEB 地址 | 7efde000 |
| 最后错误值 | 0 |
| 最后状态值 | c0000034 |
| 拥有的锁数 | 0 |
| 硬错误模式 | 0 |

```
0:000> dds 00081000 00180000
...
0017fc74  00401317 StackOverflow!SoFunction+0x27
0017fc78  00000000
0017fc7c  a3a8ea65
0017fc80  0017fc90
0017fc84  00401317 StackOverflow!SoFunction+0x27
0017fc88  10001843
0017fc8c  a3a8ea95
0017fc90  0017fca0
0017fc94  00401317 StackOverflow!SoFunction+0x27
0017fc98  0017fcb8
0017fc9c  a3a8ea85
0017fca0  0017fcb0
0017fca4  00401317 StackOverflow!SoFunction+0x27
0017fca8  00000003
0017fcac  a3a8eab5
0017fcb0  0017fcc0
**0017fcb4  00401317 StackOverflow!SoFunction+0x27**
0017fcb8  76c68738 user32!_EndUserApiHook+0x11
0017fcbc  a3a8ea85
0017fcc0  0017fcdd
**0017fcc4  00401317 StackOverflow!SoFunction+0x27**
0017fcc8  76c6a6cc user32!DefWindowProcW+0x94
0017fccc  a3a8ead5
0017fcd0  0017fce0
**0017fcd4  00401317 StackOverflow!SoFunction+0x27**
0017fcd8  0037311e
0017fcdc  a3a8ea5
0017fce0  0017fcf0
**0017fce4  00401317 StackOverflow!SoFunction+0x27**
0017fce8  0017fcdd
0017fcec  a3a8eaf5
```

```
0017fcf0 0017fd00
0017fcf4 00401317 StackOverflow!SoFunction+0x27
0017fcf8 76c6ad0f user32!NtUserBeginPaint+0x15
0017fcfc a3a8eae5
0017fd00 0017fd5c
0017fd04 00401272 StackOverflow!WndProc+0xe2
0017fd08 00401190 StackOverflow!WndProc
0017fd0c 00000003
0017fd10 cf017ada
...
```

我们使用 k WinDbg 命令的扩展版本，并提供 EBP、ESP 和 EIP 以查看其启动的函数：

```
0:000> r
eax=a3b739e5 ebx=00000000 ecx=ac430000 edx=ffeff944 esi=0037311e edi=00000000
eip=00401300 esp=00082ff8 ebp=00083000 iopl=0 nv up ei ng nz na po nc
cs=0023 ss=002b ds=002b es=002b fs=0053 gs=002b efl=00010282
StackOverflow!SoFunction+0x10:
00401300 89442404 mov dword ptr [esp+4],eax ss:002b:00082ffc=00000000
```

0:000> k L=0017fcf0 00082ff8 00401300

| 子 EBP | 返回地址 | 符号 |
|---|---|---|
| 0017fcb0 | 00401317 | StackOverflow!SoFunction+0x10 |
| 0017fd00 | 00401272 | StackOverflow!SoFunction+0x27 |
| 0017fd5c | 76c687af | StackOverflow!WndProc+0xe2 |
| 0017fd88 | 76c68936 | user32!InternalCallWinProc+0x23 |
| 0017fe00 | 76c6a571 | user32!UserCallWinProcCheckWow+0x109 |
| 0017fe5c | 76c6a5dd | user32!DispatchClientMessage+0xe0 |
| 0017fe98 | 77ccee2e | user32!__fnDWORD+0x2b |
| 0017fedc | 0040107d | ntdll!KiUserCallbackDispatcher+0x2e |
| 0017ff08 | 0040151e | StackOverflow!wWinMain+0x7d |
| 00402ba0 | 20245c8b | StackOverflow!__tmainCRTStartup+0x176 |

我们可以看出它始于 WndProc。

## 注释

一位读者向我们发送了此程序及其对应的 WinDbg 输出：

```
void func1(void);

void __cdecl main(void)
{
    func1();
}

void func1(void)
{
    func1();
}
```

```
0:000> .lastevent
Last event: d0c.e94: Stack overflow - code c00000fd (first chance)

0:000> k L50
ChildEBP RetAddr
00103000 002a1e88 test!func1+0x3
00103008 002a1e88 test!func1+0x8
00103010 002a1e88 test!func1+0x8
00103018 002a1e88 test!func1+0x8
...
```

```
0:000> !teb
TEB at 7ffdf000
ExceptionList: 001ffa1c
StackBase: 00200000
StackLimit: 00101000
...
```

```
0:000>dds 101000 200000
...[ebp][ret addr]... mainframe...
001ff9d4 002a1e88 test!func1+0x8
001ff9d8 001ff9e0
001ff9dc 002a1e88 test!func1+0x8
001ff9e0 001ff9e8
001ff9e4 002a1f8 test!main+0x8
001ff9e8 001ffa2c
001ff9ec 002a1174 test!__mainCRTStartup+0x122
001ff9f0 00000001
001ff9f4 00551388
001ff9f8 00651928
001ff9fc bc2792b1
001ffa00 00000000
001ffa04 00000000
001ffa08 7ffdc000
001ffa0c 00000000
001ffa10 00000000
001ffa14 001ff9fc
```

```
001ffa18 b33a09b6
001ffa1c 001ffa68
001ffa20 002a1619 test!_except_handler4
001ffa24 bc124925
001ffa28 00000000
001ffa2c 001ffa38
001ffa30 75911194 kernel32!BaseThreadInitThunk+0xe
001ffa34 7ffdc000
001ffa38 001ffa78
001ffa3c 7747b495 ntdll!__RtlUserThreadStart+0x70
001ffa40 7ffdc000
001ffa44 7747f154 ntdll!_RtlpSecMemListHead
001ffa48 00000000
001ffa4c 00000000
001ffa50 7ffdc000
001ffa54 00000000
001ffa58 00000000
001ffa5c 00000000
001ffa60 001ffa44
001ffa64 00000000
001ffa68 ffffffff
001ffa6c 7743d75d ntdll!_except_handler4
001ffa70 00178d24
001ffa74 00000000
001ffa78 001ffa90
001ffa7c 7747b468 ntdll!_RtlUserThreadStart+0x1b
001ffa80 002a12dc test!mainCRTStartup
001ffa84 7ffdc000
001ffa88 00000000
001ffa8c 00000000
001ffa90 00000000
001ffa94 00000000
001ffa98 002a12dc test!mainCRTStartup
...
0:000> r
eax=00651928 ebx=00000000 ecx=6ca33714 edx=00000000 esi=00000001 edi=002a3378
eip=002a18e3 esp=00103000 ebp=00103000 iopl=0 nv up ei pl zr na pe nc
cs=001b ss=0023 ds=0023 es=0023 fs=003b gs=0000 efl=00010246
test!func1+0x3:
002a18e3 e8f8ffffff call test!func1 (002a18e0)
0:000> k 1ff9d8 103000 2a18e3
Requested number of stack frames (0x1ff9d8) is too large! The maximum number is 0xffff.
^ Range error in 'k 1ff9d8 103000 2a18e3'
0:000> k L=1ff9d8 103000 2a18e3
```

| 子 EBP | 返回地址 | 符号 |
|---|---|---|
| 001ff9d8 | 002a18e8 | test!func1+0x3 |
| 001ff9e0 | 002a18f8 | test!func1+0x8 |
| 001ff9e8 | 002a1174 | test!main+0x8 |
| 001ffa2c | 75911194 | test!__tmainCRTStartup+0x122 |
| 001ffa38 | 7747b495 | kernel32!BaseThreadInitThunk+0xe |
| 001ffa78 | 7747b468 | ntdll!__RtlUserThreadStart+0x70 |
| 001ffa90 | 00000000 | ntdll!_RtlUserThreadStart+0x1b |

## 堆栈跟踪

### Linux

这是之前为 Mac OS X（第 918 页）和 Windows（第 926 页）平台描述的 **堆栈跟踪** 模式的 Linux 变体。这里我们展示了在没有调试符号（已剥离的可执行文件）的情况下的堆栈跟踪，以及如何从保留了调试符号的可执行文件中应用调试符号：

```
(gdb) bt
#0 0x000000000043e4f1 in nanosleep ()
#1 0x0000000000043e3c0 in sleep ()
#2 0x0000000000400789 in main ()

(gdb) symbol-file ./App/App.debug
Reading symbols from /home/Apps/App/App.debug...done.

(gdb) bt
#0 0x000000000043e4f1 in nanosleep ()
#1 0x0000000000043e3c0 in sleep ()
#2 0x0000000000400789 in main (argc=1, argv=0x7fff5d1572d8) at main.cpp:85
```

