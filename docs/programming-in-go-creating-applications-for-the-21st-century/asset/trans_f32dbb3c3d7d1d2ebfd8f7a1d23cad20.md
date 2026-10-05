

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

```
names = "António\tAndré\tFriedrich\t\tjean\tÉlisabeth\tIsabella \t"
names = strings.Replace(names, "\t", " ", -1)
fmt.Printf("%s\n", names)
```

| António André Friedrich...Jean Élisabeth Isabella... |

`strings.Replace()` 函数接收要处理的字符串、一个替换字符串以及替换次数（-1 表示尽可能多），并返回一个执行了所有（不重叠）替换的字符串。

在读取人类输入或来自外部来源的字符串时，我们通常希望对其空白字符进行标准化：即移除任何开头和结尾的空白字符，并将内部的一个或多个字符的序列替换为单个空格。

```
fmt.Printf("%s\n", SimpleSimplifyWhitespace(names))
```

|António André Friedrich Jean Élisabeth Isabella|

这是一个单行实现的 `SimpleSimplifyWhitespace()` 函数。

```go
func SimpleSimplifyWhitespace(s string) string {
    return strings.Join(strings.Fields(strings.TrimSpace(s)), " ")
}
```

`strings.TrimSpace()` 函数返回所传字符串的拷贝，并去除了开头和结尾的空白字符。`strings.Fields()` 函数按照任意数量的空白分割字符串并返回一个 `[]string`。而 `strings.Join()` 函数接收一个 `[]string` 和一个分隔符（可以是空字符串，尽管这里是空格），并返回一个单一字符串，其中 `[]string` 中的所有字符串由分隔符连接。通过组合使用这三个函数，我们实现了空白字符的标准化。

当然，我们可以使用 `bytes.Buffer` 通过单次遍历来更高效地简化空白字符。

```go
func SimplifyWhitespace(s string) string {
    var buffer bytes.Buffer
    skip := true
    for _, char := range s {
        if unicode.IsSpace(char) {
            if !skip {
                buffer.WriteRune(' ')
                skip = true
            }
        } else {
            buffer.WriteRune(char)
            skip = false
        }
    }
    s = buffer.String()
    if skip && len(s) > 0 {
        s = s[:len(s)-1]
    }
    return s
}
```

`SimplifyWhitespace()` 函数遍历接收到的字符串中的字符，使用 `unicode.IsSpace()` 函数跳过任何开头空白（表 3.11., ➤ 119）。它通过将字符写入 `bytes.Buffer` 来积累字符，并对于任何一个或多个内部空白序列，它写入单个空格。在最后，移除任何结尾空格（该算法允许最多一个），并返回结果字符串。稍后将显示使用正则表达式的简单版本 ➤ 128。

`strings.Map()` 函数可用于替换或移除字符串中的字符。它接收两个参数，第一个是映射函数，第二个是字符串。`strings.Map()` 函数遍历字符串中的每个字符，并为每个字符调用映射函数。如果函数返回负值，则字符被丢弃；如果返回正值，则字符被替换；如果返回相同的值，则字符保持不变。

```go
result := strings.Map(func(r rune) rune {
    if r == 'a' {
        return 'A'
    }
    return r
}, "apple")
fmt.Println(result) // Apple
```

`strings.Replace()` 函数可以用于用另一个字符串替换子字符串的所有出现处。它接收字符串、要查找的子字符串、替换字符串以及替换次数。如果次数为 -1，则替换所有匹配。

```go
result := strings.Replace("hello world", "world", "go", 1)
fmt.Println(result) // hello go
```

`strings.ReplaceAll()` 函数是替换子字符串所有出现处的便利方法。它接收字符串、要查找的子字符串和替换字符串作为参数。

```go
reader := strings.NewReader("Café")
for i := 0; i < 4; i++ {
    char, size, err := reader.ReadRune()
    if err != nil {
        if err == io.EOF {
            break
        }
        panic(err)
    }
    fmt.Printf("%U %c %d: %X\n", char, char, size, []byte(char))
}
```

