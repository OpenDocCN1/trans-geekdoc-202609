

## MSHTML!CTextArea::CreateElement+0x13:

```
Breakpoint 0 hit
eax=03018300 ebx=00000000 ecx=03170000 edx=011868ca esi=03b3bdc4 edi=6dde62e0
eip=6dde62f3 esp=03b3bdb0 ebp=03b3bdb0 iopl=0         nv up ei pl zr na pe nc
cs=0023  ss=002b  ds=002b  es=002b  fs=0053  gs=002b             efl=00000246
MSHTML!CTextArea::CreateElement+0x13:
6dde62f3 85c0            test    eax,eax
```

此时，EAX 中存放的是内存地址 0x03018300，即创建后的文本区域对象。此时我们希望为 MSHTML!CTxtPtr::InsertRange 启用断点 2，以便跟踪与文本区域元素关联的分配中 a 的复制。启用此断点（使用 be 2）后，按两次 F5 以第二次命中断点 2。命中断点后，按住 F8 单步执行，直到到达 memcpy 调用，如下所示：

```
0:007> be 2
0:007> g
Breakpoint 2 hit
eax=00000001 ebx=00000039 ecx=03b3bd84 edx=fdef0000 esi=030a80f0 edi=00000001
eip=6d93bef0 esp=03b3bd44 ebp=03b3be04 iopl=0         nv up ei ng nz na pe cy
cs=0023  ss=002b  ds=002b  es=002b  fs=0053  gs=002b             efl=00000287
MSHTML!CTxtPtr::InsertRange:
6d93bef0 8bff            mov     edi,edi
0:007> g
Breakpoint 2 hit
eax=00000269 ebx=00000039 ecx=03b3bd84 edx=00000265 esi=030a80f0 edi=00000265
eip=6d93bef0 esp=03b3bd44 ebp=03b3be04 iopl=0         nv up ei pl nz na pe nc
cs=0023  ss=002b  ds=002b  es=002b  fs=0053  gs=002b             efl=00000206
MSHTML!CTxtPtr::InsertRange:
6d93bef0 8bff            mov     edi,edi
```

## 由于篇幅限制，已截断。F8 被按住直到到达下一条指令：

```
0:007> t
eax=0050dafa ebx=03b3bd84 ecx=000004ca edx=00002000 esi=02fec0d0 edi=00000072
eip=6d93bf91 esp=03b3bd00 ebp=03b3bd40 iopl=0         nv up ei pl nz na pe nc
cs=0023  ss=002b  ds=002b  es=002b  fs=0053  gs=002b             efl=00000206
MSHTML!CTxtPtr::InsertRange+0x9d:
6d93bf91 ff15d001a56e    call    dword ptr [MSHTML!_imp__memcpy_s
```

可以看到，我们已到达从 MSHTML!CTxtPtr::InsertRange 到 memcpy_s 的调用。EAX 寄存器保存地址 0x0050dafa，即 a 将被写入的目标地址。以下是 memcpy_s 函数完成前该地址处的内存，随后是用于跳出函数的 gu 命令，以及另一次内存转储：

```
0:007> dd 0050dafa
0050dafa 00000000 00000000 00000000 00000000
0050db0a 00000000 00000000 00000000 00000000
0050db1a 00000000 00000000 00000000 00000000
0050db2a 00000000 00000000 00000000 00000000
0050db3a 00000000 00000000 00000000 00000000
0050db4a 00000000 00000000 00000000 00000000
0050db5a 00000000 00000000 00000000 00000000
0050db6a 00000000 00000000 00000000 00000000
```

```
0:007> gu
eax=00000000 ebx=03b3bd84 ecx=00000000 edx=00000000 esi=02fec0d0 edi=00000072
eip=6d93bf97 esp=03b3bd00 ebp=03b3bd40 iopl=0         nv up ei pl zr na pe nc
cs=0023  ss=002b  ds=002b  es=002b  fs=0053  gs=002b             efl=00000246
MSHTML!CTxtPtr::InsertRange+0xa3:
6d93bf97 8b4508        mov     eax,dword ptr [ebp+8] ss:002b:03b3bd48=39000000
```

```
0:007> dc 0050dafa
0050dafa 00610061 00610061 00610061 00610061  a.a.a.a.a.a.a.
0050db0a 00610061 00610061 00610061 00610061  a.a.a.a.a.a.a.
0050db1a 00610061 00610061 00610061 00610061  a.a.a.a.a.a.a.
0050db2a 00610061 00610061 00610061 00610061  a.a.a.a.a.a.a.
0050db3a 00610061 00610061 00610061 00610061  a.a.a.a.a.a.a.
0050db4a 00610061 00610061 00610061 00610061  a.a.a.a.a.a.a.
0050db5a 00610061 00610061 00610061 00610061  a.a.a.a.a.a.a.
0050db6a 00000061 00000000 00000000 00000000  a.............
```

可以看到，我们的 a 已复制到内存中。这就是你在浏览器窗口中可以直观看到的 a 的实际地址。当发生内存泄漏时，这将变得明显。接下来，我们禁用断点 2，并为 MSHTML!CStr::_Alloc+0x43 启用断点 3。我们还需要在 a 刚被写入的地址上设置一个“访问断点”，因为该位置对内存泄漏很重要。我们需要从地址 0x0050dafa 减去 2 字节，使其 4 字节对齐。做出这些更改后，列出断点以验证其是否正确。

```
0:007> bd 2
0:007> be 3
0:007> ba w4 0050daf8
0:007> bl
```

```
0 e 6dde62f3    0001 (0001)  0:****  MSHTML!CTextArea::CreateElement+0x13
1 e 6db02cab    0001 (0001)  0:****  MSHTML!BASICPROPPARAMS::SetStringProperty
2 d 6d93bef0    0001 (0001)  0:****  MSHTML!CTxtPtr::InsertRange
3 e 6d8d7174    0001 (0001)  0:****  MSHTML!CStr::_Alloc+0x43
4 d 7727fc40    0001 (0001)  0:****  urlmon!CoInternetCreateSecurityManager
5 d 6e0df435    0001 (0001)  0:****  MSHTML!_HeapRealloc<>
6 d 75bbea5f    0001 (0001)  0:****  ole32!CoTaskMemAlloc+0x13
7 e 0050daf8 w 4 0001 (0001) 0:****
```

可以通过断点编号旁边的 e 或 d 来查看断点是否启用或禁用。我们准备好按 F5 继续执行。我们立即命中了 MSHTML!CStr::_Alloc+43 的断点。出于某种原因，尽管我们将断点设置为 +4f，但它显示为 +43。暂时可以忽略这一点，因为它似乎仍在 test eax, eax 指令的适当位置中断。让我们记录 EAX 中保存的 0x04ec71b8 地址，因为它也将存储我们的 a，稍后将展示这一点。执行几次 gu 后，我们的 a 将出现在该地址处。此块地址很重要，因为它很快将因 eventhandler 函数而被重新分配。

```
Breakpoint 3 hit
eax=04ec71b8 ebx=03018344 ecx=00420000 edx=00427920 esi=00000000 edi=00000039
eip=6d8d7174 esp=03b3c184 ebp=03b3c198 iopl=0         nv up ei pl zr na pe nc
cs=0023  ss=002b  ds=002b  es=002b  fs=0053  gs=002b             efl=00000246
MSHTML!CStr::_Alloc+0x43:
6d8d7174 85c0            test    eax,eax
0:007> gu  # Executed a couple of times until the address in EAX held our a's
0:007> dc 04ec71b8
04ec71b8  00000072 00610061 00610061 00610061  r...a.a.a.a.a.a.
04ec71c8  00610061 00610061 00610061 00610061  a.a.a.a.a.a.a.a.
04ec71d8  00610061 00610061 00610061 00610061  a.a.a.a.a.a.a.a.
04ec71e8  00610061 00610061 00610061 00610061  a.a.a.a.a.a.a.a.
04ec71f8  00610061 00610061 00610061 00610061  a.a.a.a.a.a.a.a.
04ec7208  00610061 00610061 00610061 00610061  a.a.a.a.a.a.a.a.
04ec7218  00610061 00610061 00610061 00610061  a.a.a.a.a.a.a.a.
04ec7228  00610061 00000061 8892b1a1 80000000  a.a.............
```

另请注意，CStr::_Alloc 执行的内存分配的以下反汇编：

```
mov    ecx, _g_hProcessHeap ; hHeap
call   ??$HeapAlloc@$0A@@MemoryProtection
```

分配使用进程堆，跟踪执行显示 MemGC 未保护这些分配。接下来，我们在调试器中继续执行，并立即再次命中 MSHTML!CStr::_Alloc+43 断点：

```
Breakpoint 3 hit
eax=04ec74b8 ebx=0301834c ecx=00420000 edx=00427920 esi=00000000 edi=00000039
eip=6d8d7174 esp=03b37ff0 ebp=03b38004 iopl=0         nv up ei pl zr na pe nc
cs=0023  ss=002b  ds=002b  es=002b  fs=0053  gs=002b             efl=00000246
MSHTML!CStr::_Alloc+0x43:
6d8d7174 85c0            test    eax,eax
```

我们记录 EAX 中保存的 0x04ec74b8 地址，因为它也与此断点的先前命中以及我们的源代码相关。接下来，我们禁用断点 3 并继续执行。继续执行后，我们到达 MSHTML!BASICPROPPARAMS::SetStringProperty 断点，该断点在由 form.reset() 状态更改触发的 eventhandler 函数内部到达：

```
0:007> bd 3
0:007> g
Breakpoint 1 hit
eax=00000000 ebx=03018300 ecx=6d996258 edx=04ed48ac esi=00000000 edi=6d996244
eip=6db02cab esp=03b39d14 ebp=03b39d3c iopl=0         nv up ei pl zr na pe nc
cs=0023 ss=002b ds=002b es=002b fs=0053 gs=002b             efl=00000246
MSHTML!BASICPROPPARAMS::SetStringProperty:
6db02cab 8bff          mov     edi,edi
```

这发生在文本区域默认值设置为 “foo”之前。我们现在将为 MSHTML!_HeapRealloc<0> 启用断点。这会导致在对 MSHTML!CStr::_Alloc 分配的初始块进行大小调整的 realloc 调用时暂停执行。

```
0:007> be 5
0:007> g
Breakpoint 5 hit
eax=04ec71bc ebx=04ed48ac ecx=03b39c8c edx=00000000 esi=03018344 edi=00000003
eip=6e0df435 esp=03b39c74 ebp=03b39c94 iopl=0         nv up ei pl nz na pe nc
cs=0023 ss=002b ds=002b es=002b fs=0053 gs=002b             efl=00000206
MSHTML!_HeapRealloc<>:
6e0df435 8bff          mov     edi,edi
0:007> bd 5
```

如你所见，EAX 保存地址 0x04ec71bc，即我们从 MSHTML!CStr::_Alloc 跟踪到的初始块的相同地址。实际上，它相差几个字节，但这只是由于对齐造成的。以下输出是在我们按住 F8 键几秒钟后显示的，一旦看到对 memmove 的调用，就小心停止：

```
0:007> t
eax=0000000c ebx=0047fb88 ecx=0000000c edx=00427920 esi=04ec71b8 edi=0047fb88
eip=777d898e esp=03b39a98 ebp=03b39aa0 iopl=0         nv up ei ng nz na po cy
cs=0023 ss=002b ds=002b es=002b fs=0053 gs=002b             efl=00000283
ntdll!memmove+0xe:
777d898e 8bc1          mov     eax,ecx
```

进入 memmove 几条指令后，源地址和目标地址参数分别加载到 ESI 和 EDI 中。EDI 中是调整大小后的块的目标地址，该块最终将被设置为 “foo”。ESI 保存我们在 realloc 调用中刚看到的块的地址。让我们使用 !heap 命令检查移动前源块的状态，然后在退出这些函数调用后再次检查：

