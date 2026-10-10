
```
// "program" 的日文片假名写法
s := ""
fmt.Printf("% x\n", s) // "e3 83 97 e3 83 ad e3 82 b0 e3 83 a9 e3 83 a0"
r := []rune(s)
fmt.Printf("%x\n", r)  // "[30d7 30ed 30b0 30e9 30e0]"
```

(第一个 `Printf` 中的动词 `% x` 会在每对十六进制数字之间插入一个空格。)

如果将一个 rune 切片转换为字符串，它会生成每个 rune 的 UTF-8 编码的连接：

```
fmt.Println(string(r)) // "プログラム"
```

将整数值转换为字符串会将该整数解释为一个 rune 值，并生成该 rune 的 UTF-8 表示形式：

```
fmt.Println(string(65))     // "A"，而不是 "65"
fmt.Println(string(0x4eac)) // "京"
```

如果 rune 无效，则会替换为替换字符：

```
fmt.Println(string(1234567)) // "�"
```

### 3.5.4 字符串和字节切片

有四个标准包对于操作字符串尤为重要：`bytes`、`strings`、`strconv` 和 `unicode`。`strings` 包提供了许多用于搜索、替换、比较、修剪、分割和连接字符串的函数。

`bytes` 包拥有用于操作类型为 `[]byte` 的字节切片的类似函数，字节切片与字符串共享一些特性。因为字符串是不可变的，逐步构建字符串可能涉及大量的分配和复制。在这种情况下，使用 `bytes.Buffer` 类型会更高效，我们马上就会演示。

`strconv` 包提供了用于布尔值、整数和浮点数与其字符串表示之间相互转换的函数，以及用于给字符串加引号和去引号的函数。

`unicode` 包提供了诸如 `IsDigit`、`IsLetter`、`IsUpper` 和 `IsLower` 等函数，用于对 rune 进行分类。每个函数接受单个 rune 参数并返回一个布尔值。`ToUpper` 和 `ToLower` 等转换函数将 rune 转换为指定的大小写（如果它是字母的话）。所有这些函数都使用 Unicode 标准类别来处理字母、数字等。`strings` 包也有类似的函数，也叫 `ToUpper` 和 `ToLower`，它们会返回一个新字符串，其中原始字符串的每个字符都应用了指定的转换。

下面的 `basename` 函数灵感来源于同名的 Unix shell 实用工具。在我们的版本中，`basename(s)` 会移除 `s` 中看起来像文件系统路径（组件由斜杠分隔）的任何前缀，并移除看起来像文件类型的任何后缀：

```
fmt.Println(basename("a/b/c.go")) // "c"
fmt.Println(basename("c.d.go"))   // "c.d"
fmt.Println(basename("abc"))      // "abc"
```

`basename` 的第一个版本在没有库函数帮助的情况下完成所有工作：

gopl.io/ch3/basename1

```
// basename 移除目录组件和 .后缀。
// 例如：a => a, a.go => a, a/b/c.go => c, a/b.c.go => b.c
func basename(s string) string {
    // 丢弃最后一个 '/' 及其之前的所有内容。
    for i := len(s) - 1; i >= 0; i-- {
        if s[i] == '/' {
            s = s[i+1:]
            break
        }
    }
    // 保留最后一个 '.' 之前的所有内容。
    for i := len(s) - 1; i >= 0; i-- {
        if s[i] == '.' {
            s = s[:i]
            break
        }
    }
    return s
}
```

一个更简单的版本使用了 `strings.LastIndex` 库函数：

gopl.io/ch3/basename2

```
func basename(s string) string {
    slash := strings.LastIndex(s, "/") // 如果未找到 "/" 则为 -1
    s = s[slash+1:]
    if dot := strings.LastIndex(s, "."); dot >= 0 {
        s = s[:dot]
    }
    return s
}
```

`path` 和 `path/filepath` 包提供了一组更通用的函数，用于操作分层名称。`path` 包适用于任何平台上以斜杠分隔的路径。它不应用于文件名，但适用于其他领域，例如 URL 的路径组件。相比之下，`path/filepath` 使用宿主平台的规则操作文件名，例如 POSIX 上的 `/foo/bar` 或 Microsoft Windows 上的 `c:\foo\bar`。

让我们继续看另一个子字符串示例。任务是获取一个整数的字符串表示形式，例如 `"12345"`，并每三位插入一个逗号，如 `"12,345"`。此版本仅适用于整数；处理浮点数留作练习。

gopl.io/ch3/comma

```
// comma 在非负十进制整数字符串中插入逗号。
func comma(s string) string {
    n := len(s)
    if n <= 3 {
        return s
    }
    return comma(s[:n-3]) + "," + s[n-3:]
}
```

`comma` 的参数是一个字符串。如果其长度小于或等于 3，则不需要逗号。否则，`comma` 会使用一个由除最后三个字符外的所有字符组成的子字符串递归调用自身，并将逗号和最后三个字符追加到递归调用的结果中。

字符串包含一个字节数组，一旦创建便不可变。相比之下，字节切片的元素可以自由修改。

字符串可以转换为字节切片，也可以转回字符串：

```
s := "abc"
b := []byte(s)
s2 := string(b)
```

从概念上讲，`[]byte(s)` 转换会分配一个新的字节数组来保存 `s` 的字节副本，并生成一个引用该数组全部内容的切片。优化编译器在某些情况下可能会避免分配和复制，但通常需要复制以确保 `s` 的字节保持不变，即使 `b` 的字节随后被修改。使用 `string(b)` 从字节切片转回字符串也会进行复制，以确保生成的字符串 `s2` 不可变。

为了避免转换和不必要的内存分配，`bytes` 包中的许多实用函数直接对应 `strings` 包中的同类函数。例如，这里有 `strings` 包中的六个函数：

```
func Contains(s, substr string) bool
func Count(s, sep string) int
func Fields(s string) []string
func HasPrefix(s, prefix string) bool
func Index(s, sep string) int
func Join(a []string, sep string) string
```

以及 `bytes` 包中对应的函数：

```
func Contains(b, subslice []byte) bool
func Count(s, sep []byte) int
func Fields(s []byte) [][]byte
func HasPrefix(s, prefix []byte) bool
func Index(s, sep []byte) int
func Join(s [][]byte, sep []byte) []byte
```

唯一的区别在于字符串被字节切片取代了。

`bytes` 包提供了 `Buffer` 类型，用于高效操作字节切片。`Buffer` 最初为空，但随着 `string`、`byte` 和 `[]byte` 等类型的数据被写入而增长。正如下面的示例所示，`bytes.Buffer` 变量无需初始化，因为其零值可用：

gopl.io/ch3/printints

```
// intsToString 类似于 fmt.Sprint(values) 但会添加逗号。
func intsToString(values []int) string {
    var buf bytes.Buffer
    buf.WriteByte('[')
    for i, v := range values {
        if i > 0 {
            buf.WriteString(", ")
        }
        fmt.Fprintf(&buf, "%d", v)
    }
    buf.WriteByte(']')
    return buf.String()
}

func main() {
    fmt.Println(intsToString([]int{1, 2, 3})) // "[1, 2, 3]"
}
```

当将任意 rune 的 UTF-8 编码追加到 `bytes.Buffer` 时，最好使用 `bytes.Buffer` 的 `WriteRune` 方法，但对于 `'['` 和 `']'` 等 ASCII 字符，`WriteByte` 也完全可以。
