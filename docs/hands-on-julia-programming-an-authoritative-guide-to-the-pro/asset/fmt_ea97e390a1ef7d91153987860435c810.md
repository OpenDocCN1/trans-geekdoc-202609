
随着计算机的普及，计算不再局限于特定区域变得显而易见。其次，数据交换要求数据能在任何可用的计算系统中呈现。第三，随着存储和内存价格下降，表示文本所需的内存可超越单字节限制。一群来自各组织和学术界的计算机科学家与语言学家在 Unicode Consortium（Unicode 联盟）旗下共同推出了 **Universal Coded Character Set**（**UCS**，通用编码字符集）。1991 年首批引入的字符集包含约 7000 个字符，采用 2 字节表示，称为 UCS-2。但随着更多语言加入规范，字符迅速增长，随即决定采用 4 字节表示，称为 UCS-4。实际上，Unicode 规范定义了 16 个码位平面，每个大小为 65536（2^16），但仅少数值被实际使用。技术上讲，32 位中仅 20 位用于实际用途。然而，许多计算机系统在操作系统中实现了宽字符：Windows 通过 Windows NT 开发了原生 16 位操作系统，并停止了旧版 Windows 95 代码库。在 90 年代末和千禧年初，代码需通过宏分别编译 8 位和 16 位版本。

## 宽字符与 UTF-8 的诞生

世界另一端正忙于重写操作系统内核以支持宽字符。甚至一些类 UNIX 系统也将宽字符实现为 4 字节。Ken Thompson 提出了一个新颖想法：复用 C 语言编码作为 Unicode 字符的基础。但 C 编码或 C 字符串无法直接用于 UCS-2 和 UCS-4，因为它们包含整字节的 NULL 数据，而 C 语言以 0 作为字符串终止符。例如，UCS-2 中字符 ‘a’ 为 U+0061，其前导字节为 0。

他希望 Unicode 字符以如下方式表示：

1.  ASCII 字符在新编码中保持有效，即 0x00-0x7F 范围内的字符无需转换。
2.  值 ≥ 128 的字符必须用多字节表示。
3.  新编码必须有前导字节指示后续读取的字节数。
4.  歧义时，选择字节数最少的编码。
5.  前导字节和尾随字节的模式需使违规易于识别，便于在无 CRC 等冗余检查的情况下传输。
6.  除实际 NUL 字符外，无其他字符包含全零字节。

最终方案如下：

![](n4upl4fndq2.jpeg)

**Figure 7.1:** UTF-8 Representation of the Unicode Characters

该表示称为 **UTF-8**。超出 21 位的编码如何处理？目前 Unicode 规范未使用超过 21 位信息，但该方案可容纳高达 36 位信息，覆盖整个 UCS-4 范围。类似地，还引入了 **UTF-16**，以 2 字节为单位扩展字符码；也存在 **UTF-32** 转换方案。

## Julia 对 Unicode 的原生支持

Julia 语言原生支持 Unicode，甚至变量和常量可使用 Unicode 字符。内部上，Julia 字符串（`String` 类型）以 UTF-8 编码存储为 Unicode 字符流。Julia 中的字符（`Char`）在 UTF-8 编码下表示为最多 4 字节值。原始字节用 `UInt8` 表示，而非 `Char`。不过，Julia 支持用其他编码表示字符串，也可通过 Julia 接口开发自定义字符码和字符串。与原生 C/C++ 应用交互时，可能需要将字符串作为 `Cstring` 传递。`Cstring` 是 C 语言期望的以零结尾的字符串。

## 字体、字形与文本计算

观察不同字体下字符 a 的表示：

![](n4upl4fndq3.jpeg)

**Figure 7.2:** Character'a' written with glyphs from various fonts

字体和字形提供字符的视觉外观。作为编程语言，Julia 不提供控制字体或字形选择的机制，这些通常属于文字处理或渲染软件（如 Microsoft Word、Adobe InDesign）范畴。

了解文本计算各方面后，我们来评估 Julia 如何满足这些需求。

## Julia 字符串初始化

在 Julia 中，`String` 对象可通过以下字面量表达式初始化。

```julia
julia> str = "This is a string"
"This is a string"
```

字符串不可变。创建后无法修改。另一种定义方式可保留格式和换行符，特殊字符无需额外引用。

```julia
julia> str = """
This is a preformatted
"string" """
" \nThis is a preformatted \n\"string\" "
```

字符串可插入其他变量的计算结果以生成最终输出。

```julia
julia> a = "Jack";
julia> b = "Jill";
julia> c = "100";
julia> str = "$a owes $b $c dollars"
"Jack owes Jill 100 dollars"
```

字符串中的特殊字符（如引号 `"` 或反斜杠 `\`）需用反斜杠 `\` 转义。

```julia
julia> str = "This is a \"quoted\\  ' string"
"This is a \"quoted\\  ' string"
```

下节将介绍与字符串交互的各种方法。

> **Note:** 字符串不可变，因此即使垃圾回收发生，它们仍可驻留在系统内存中而不被覆盖。内存调试器可读取随机内存位置。若有密码等敏感数据，应考虑使用字节或字符数组结构，并在数据消费后覆盖内存位置。取消引用内存对象并强制调用垃圾回收可能不是最安全的选项。

## 字符串标准方法回顾

### 字符串比较

`String` 对象可使用标准比较运算符 `isequal(==)`、`isless(<)` 或 `>` 进行比较，通常采用字典序。

```julia
julia> s1 = "abc"
julia> s2 = "def"
julia> s1 < s2
true
julia> s2 > s1
true
julia> s1 = "abc"
julia> s2 = "abc"
julia> s1 == s2
true
```

“egal” 运算符（`===`）比较对象身份，对于不可变的 `String` 对象，将进行逐位比较。

```julia
julia> s1 === s2
true
```

### 字符串迭代

正如数组和集合，字符串也是字符序列的自然集合。因此遍历 `String` 时可枚举字符。

```julia
julia> s = "Julia";
julia> for c in s
       println(c)
       end
J
u
```
