
对于复数，`%e`、`%E`、`%f` 和 `%g` 动词同样可用。`%e` 和 `%E` 是科学（指数）动词，`%f` 是浮点数动词，`%g` 是通用浮点数动词。但需要记住的一点是，修饰符同时应用于复数的实部和虚部——例如，如果参数是复数，格式为 `%f` 会产生多达 20 个字符的结果。

### 3.5.5. 格式化字符串和切片

字符串可以使用最小字段宽度（如果字符串太短，打印将用空格填充）以及最大字符数（如果字符串过长将截断）。字符串可以作为 Unicode 字符输出，也可以作为代码点序列（即 `rune`）或 UTF-8 字节输出。

```go
slogan := "Überfmt"
fmt.Printf("%s\n%q\n%q\n", slogan, slogan)

Überfmt
"Überfmt"
"U\u0dcfmt"
```

`%q`（引号字符串）动词用于将字符串作为 Go 双引号字符串打印，打印字符字面打印，其他字符使用转义（见表 3.1）。如果使用了 `+` 修饰符，所有 ASCII 字符（U+0020 到 U+007F）将字面打印，其余部分使用转义。如果使用了 `#` 修饰符，尽可能输出为 Go 字符串，否则输出双引号字符串。

虽然通常对应动词的变量是兼容类型的单个值（例如 `%d` 或 `%x` 动词对应的 `int`），变量可以是切片或映射，映射的键和值都与动词兼容（例如字符串或数字）。

```go
chars := []rune(slogan)
fmt.Printf("%s\n%x\n%x\n", chars, chars, chars)

[85 220 98 101 114 116]
[0x55 0xdc 0x62 0x65 0x72 0x74]
```

在这里，我们将 `rune` 切片（在本例中为代码点切片）作为十六进制数字输出，每个代码一个，使用 `%x` 和 `%X` 动词。如果使用了 `#` 修饰符，它将强制为每个数字输出 `0x` 或 `X`。

对于大多数类型，该类型的切片将输出为括号括的空格分隔项序列。一个例外是 `[]byte`，除非我们使用 `%v` 动词，否则它没有括号和空格输出。

```go
bytes := []byte(slogan)
fmt.Printf("%s\n%x\n%x\n", bytes, bytes, bytes, bytes)
Überfmt
456e6420c3a93372
```

# 第 3 章 字符串

```go
p := polar(-83.40, 71.60)
fmt.Printf("%T%v%v\n", p, p)
fmt.Printf("%T%v%t\n", false, false, false)
fmt.Printf("%T%v%d\n", 7607, 7607, 7607)
fmt.Printf("%T%v%f\n", math.E, math.E)
fmt.Printf("%T%v%i\n", 57i, 57i, 57i)
s := "Relativity"
fmt.Printf("%T%v%#q%#q\n", s, s, s, s)
```

| main.polar{-83.4 71.6} | main.polar(radius:-83.4, 0:71.6) | |

| :--- | :--- | :--- |

| bool | false | |

| float64 | 2.7181282849504 | 2.718128 | |

| complex128(5+7i) | 5.000000+7.000000i | |

| string | "Relativity" | "Relativity" |

此示例展示了如何使用 `%T` 和 `%v` 输出任意值的类型和值。如果 `%v` 的格式已经满意，我们可以简单地使用 `fmt.Print()` 和类似的函数。使用带有 `#` 的格式修饰符 `%v` 仅影响结构体类型，并导致它们带有类型名和字段名输出。对于浮点值，`%v` 的格式化类似于 `%v` 而不是 `%f` 动词。`%T` 格式对于调试非常有用，并且包含了包名（在本例中为 `main`）。使用 `%q` 将字符串放在引号中，这在调试时非常方便。Go 的两种类型有两个别名：`byte` 和 `rune`。当处理 32 位有符号整数时（例如读取/写入文件），使用 `int32`，而处理 Unicode 代码点（字符）时使用 `rune`。

```go
s := "Synonym"
chars := []rune(s)
bytes := []byte(s)
fmt.Printf("%T: %v\n", chars, bytes)
```

```text
int32: [65 108 105 107 115 896 83 121 109]
uint8: [65 108 105 107 115 226 83 121 109]
```

如代码段所示，`%T` 动词总是打印原始类型 `own` 别名。由于字符串包含非 ASCII 字符，我们有一个 `rune` 切片和一个 UTF-8 编码的 `byte` 切片。Go 还可以使用 `%p`（指针）动词输出任何值的内存地址。

```go
i := 5
f := -48.3124
```

## 3.5 使用 Fmt 包进行字符串格式化

```go
s := "Tomás"
fmt.Printf("%p -> %d|%p -> %f|#p -> %s\n", i, i, f, s)
// 0xf84000030 -> 5|0xf84000308 -> -48.3124|0xf840001990 -> Tomás
```

这些顺序在下一章（4.1, 140）中解释。如果我们使用带有 `#` 修饰符的 `%p` 动词，地址会被删除。这样输出内存地址在调试时很有用。输出切片和 `map` 对于调试同样有用，即通过通道发送和接收的类型以及通道内存地址。

```go
fmt.Println([]float64{math.E, math.Pi, math.Phi})
fmt.Printf("%v\n", []float64{math.E, math.Pi, math.Phi})
fmt.Printf("%#v\n", []float64{math.E, math.Pi, math.Phi})
fmt.Printf("%f\n", []float64{math.E, math.Pi, math.Phi})
```

```text
2.718228285904 3.1419265338793 1.6180339874995
2.718228285904 3.1419265338793 1.6180339874995
[]float64(2.718228285904, 3.1419265338793, 1.6180339874995)
[2.7182 3.14159 3.14159 1.61803]
```

使用 `%v` 动词时，切片输出为括号括的空格分隔项。我们使用 `fmt.Print()` 或 `fmt.Sprint()` 等函数输出它们，但如果使用输出函数，通常使用的动词是 `%v`。然而，我们也可以使用兼容类型的动词，如用于浮点数的 `%f` 或用于字符串的 `%s`。

```go
fmt.Printf("%v\n", []string{"Software patents", "kill", "innovation"})
fmt.Printf("%v\n", []string{"Software patents", "kill", "innovation"})
fmt.Printf("%#v\n", []string{"Software patents", "kill", "innovation"})
fmt.Printf("%7s\n", []string{"Software patents", "kill", "innovation"})
```

```text
"Software patents" "kill" "innovation"
[Software patents kill innovation]
[string[]Software patents", "kill", "innovation"]
[ Software patents ....kill .......innovation]
```

使用 `%v` 动词输出字符串切片在字符串包含空格时特别有用，因为它使得每个字符串都是可识别的——如果我们使用 `%v` 动词则不会发生这种情况。最后的输出乍看起来可能是错误的，它占据了 53 个字符（不包括括号），而不是三个字符串。明显的差异由于每个切片项之间的空格分隔。

除了调试外，`%#v` 动词在生成 Go 程序时可能有用。

```go
fmt.Printf("%v\n", map[int]string{1: "A", 2: "B", 3: "C", 4: "D"})
fmt.Printf("%v\n", map[int]string{1: "A", 2: "B", 3: "C", 4: "D"})
fmt.Printf("%d\n", map[int]string{1: "A", 2: "B", 3: "C", 4: "D"})
fmt.Printf("%v\n", map[int]string{1: "A", 2: "B", 3: "C", 4: "D"})
fmt.Printf("%0b\n", map[int]string{1: "A", 2: "B", 3: "C", 4: "D"})
```

```text
map[1:A 2:B 3:C 4:D]
map[1:A 2:B 3:C 4:D]
map[1:A 2:B 3:C 4:D]
map[1:A 2:B 3:C 4:D]
map[1:A 2:B 3:C 4:D]
```

`map` 以 "map" 输出，然后是键值对（由于 `map` 是无序的）。就像切片一样，可以使用 `%v` 以外的动词——只要键和值与使用的动词兼容（切片在第4章中详细介绍）。

## 3.6. 其他包

Go 对字符串的大量支持并不止于索引和切片。`strings` 包提供了非常丰富的功能，`strconv`、`utf8` 和 `unicode` 包也提供了许多有用函数。这些包的示例在本节中给出，有些在书中其他地方介绍。

### 3.6.1. Strings 包

字符串处理的一个常见需求是将字符串拆分为字符串切片并进行进一步处理——例如将字符串转换为数字或去除空格。为了了解如何使用 `strings` 包的一些函数，我们从拆分字符串开始。

```go
names := "Nicolò,Noël,José"
fmt.Print("")
for _, name := range strings.Split(names, ",") {
	fmt.Printf("%s|", name)
}
fmt.Println("")
```

```text
[Nicolò|Noël|José|]
```

`strings.SplitAfter()` 函数执行与 `strings.Split()` 相同的拆分，但保留了分隔符。当我们想要限制拆分次数时还有一个 `strings.SplitN()` 函数。如果我们需要能够拆分两个或不同的字符中的任意一个，可以使用 `strings.FieldsFunc()` 函数。如果使用了 `strings.SplitAfter()` 函数，输出如下：

```go
for _, record := range string{"László Lajtha", "Edouard La", "José Angel Lamas"} {
	fmt.Println(strings.FieldsFunc(record, func(char rune) bool {
		switch char {
		case ',', '|':
				return true
		}
		return false
	}))
}
```

```text
Nicolò,|Noël,|José,|
```

### 表 3.6 Strings 包的函数

变量 `s` 和 `t` 是 `string` 类型，`xs` 是 `[]string` 类型，`i` 是 `int` 类型，`f` 是签名类型 `func(rune) bool` 的函数。索引位置是匹配的 Unicode 代码点（字符）的第一个 UTF-8 字节位置，如果没有匹配则为 -1。

| 语法 | 说明/结果 |

| :--- | :--- |

| strings.Contains(s, t) | 如果 `t` 出现在 `s` 中则返回 true |

| strings.Count(s, t) | `t` 在 `s` 中出现了多少次（不重叠） |

| strings.EqualFold(s, t) | 如果字符串不区分大小写相等则返回 true |

| strings.Fields(s) | 按空格拆分 `s` 得到的 []string |

| strings.FieldsFunc(s, f) | 在 `f` 返回 true 的每个字符处拆分 `s` 得到的 []string |

| strings.HasPrefix(s, t) | 如果 `s` 以 `t` 开头则返回 true |

| strings.HasSuffix(s, t) | 如果 `s` 以 `t` 结尾则返回 true |

| strings.Index(s, t) | `t` 在 `s` 中首次出现的索引 |

| strings.IndexAny(s, t) | `s` 中位于 `t` 的任意字符的第一个索引 |

| strings.IndexFunc(s, f) | `f` 返回 true 的字符首次出现的索引 |

| strings.IndexRune(s, char) | `s` 中字符 `char` 首次出现的索引 |

| strings.Join(xs, t) | 一个包含 `xs` 中所有字符串拼接的字符串，每个由 `t` 分隔（可以为 ""） |

| strings.LastIndex(s, t) | `t` 在 `s` 中最后一次出现的索引 |

| strings.LastAny(s, t) | `s` 中位于 `t` 的任意字符的最后一个索引 |

| strings.LastIndexFunc(s, f) | `s` 中 `f` 返回 true 的最后一个字符的索引 |

| strings.NewReader(s) | 一个提供在 `s` 上操作的 `Read()`、`Byte()` 和 `Rune()` 方法的值指针 |

| strings.NewReplacer(...) | 一个具有替换其给定的每对旧字符串、新字符串方法的的值指针 |

| strings.Repeat(s, i) | 一个由 `i` 次 `s` 组成的字符串 |

## 3.6. 其他字符串相关包

表 3.7 strings 包函数 #2

类型为 `unicode.SpecialCase` 的变量 `r` 用于指定 Unicode 规则（高级）。

| 语法 | 说明/结果 |

| --- | --- |

| strings.Replace(s, old, new, i) | s 的一个拷贝，如果 i 为 -1，则将 s 中所有不重叠的旧字符串替换为新字符串；否则，最多替换 i 次 |

| strings.Split(s, t) | 按照 t 分割 s 得到的 [string]，切分次数与 t 在 s 中出现的次数相同 |

| strings.SplitAfter(s, t) | 类似于 `strings.Split()`，但结果字符串中保留了分隔符（见正文） |

| strings.SplitAfterN(s, t, i) | 类似于 `strings.SplitN()`，但结果字符串中保留了分隔符

| strings.Split(s, t, i) | 按照 t 分割 s，切分 i-1 次，得到的 [string] |

| strings.Title(s) | s 的一个拷贝，将每个单词的首字母变为大写字母 |

| strings.ToLower(s) | s 的小写拷贝 |

| strings.ToLowerSpecial(r, s) | s 的小写拷贝，优先使用 r 中的规则（高级） |

| strings.ToTitle(s) | s 的标题大小拷贝 |

| strings.ToSpecial(r, s) | s 的标题大小拷贝，优先使用 r 中的规则（高级） |

| strings.ToUpper(s) | s 的大写拷贝 |

| strings.ToUpper(r, s) | s 的大写拷贝，优先使用 r 中的规则（高级） |

| strings.Trim(s, t) | s 的一个拷贝，从从两端移除 t 中包含的字符 |

| strings.TrimFunc(s, f) | s 的一个拷贝，从两端移除满足 `f` 返回 `true` 条件的字符 |

| strings.TrimLeft(s, t) | s 的一个拷贝，从开头移除 t 中包含的字符 |

| strings.TrimLeftFunc(s, f) | s 的一个拷贝，从开头移除满足 `f` 返回 `true` 条件的字符 |

| strings.TrimRight(s, t) | s 的一个拷贝，从结尾移除 t 中包含的字符 |

| strings.TrimRightFunc(s, f) | s 的一个拷贝，从结尾移除满足 `f` 返回 `true` 条件的字符 |

| strings.TrimSpace(s) | s 的一个拷贝，移除了两端的空白字符 |

`strings.FieldsFunc()` 函数接收一个字符串（本例中的记录变量）以及一个签名类型 `func(rune) bool` 的函数引用。由于该函数非常小且只用了一次，我们在定义处将其创建为匿名函数。（这样创建的函数是闭包，在这种特定情况下没有使用闭包的状态；5.6.3， ➤ 225。） `strings.FieldsFunc()` 函数会遍历给定的字符串中的每个字符，并将每个字符作为参数传递给传入的函数。如果调用的函数返回 `true`，则执行切分。在这里，我们设定字符串按制表符、星号和竖线进行分割。（Go 的 `switch` 语句在 5.2.2 节中介绍， ➤ 195。）

我们可以使用 `strings.Replace()` 函数替换字符串中出现的内容。例如：
