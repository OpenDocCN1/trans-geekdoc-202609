
## 第6 章 面向对象编程

```go
if err != nil {
    return data, err
}
return data[:], nil // 切片掉所有未使用的字节
```

就像我们之前看到的 `exchange` 函数一样，这个函数并不知道也不在乎传递的是什么特定类型的值——只要它是某种 `io.Reader` 即可。

如果读取成功，数据切片将被重新切片，以将其长度缩减为实际读取的字节数。如果我们不这样做，且大小太大，我们得到的是读取的数据后面跟着一串字节（每个值均为 0x0）。例如，如果不进行切片，david 将输出为 `DavidBalfour\x000\x000\x000`。

注意，我们并不需要在接口和满足该的任何类型之间建立自定义连接——类型可以“继承”或“扩展”一个接口；只需提供所需的方法就足够了。这使得 Go 变得极其灵活——我们可以随时添加新的接口、类型和方法，而不会破坏继承树。

### 6.3.1. 接口嵌入

Go 接口（以及结构体，正如我们在下一节中看到的）对嵌入提供了很好的支持。接口可以嵌入其他接口，其效果几乎等同于我们在嵌入接口中直接写了被嵌入接口的方法签名。让我们用一个简单的例子来说说明这一点。

```go
type LowerCase interface {
    LowerCase()
}

type UpperCase interface {
    UpperCase()
}

type LowerUpperCase interface {
    LowerCase // 相当于我们写了 LowerCase()
    UpperCase // 相当于我们写了 UpperCase()
}
```

`LowerUpperCase` 接口指定了一个单一方法 `LowerCase()`，它不接受参数也不返回任何内容。`UpperCase` 接口也类似。`LowerUpperCase` 嵌入了另外两个接口。这意味着一个具体类型要满足 `LowerUpperCase` 接口，必须拥有 `LowerCase()` 和 `UpperCase()` 方法。

### 6.3. 接口

在这个微小的例子中，嵌入看起来优势不大。然而，如果我们向前两个接口添加额外的方法（例如，`LowerCaseSpecial()` 和 `UpperCaseSpecial()`），`LowerUpperCase` 接口将自动包含它们，而我们无需修改它的代码。

```go
type FixCaser interface {
    FixCase()
}
type ChangeCaser interface {
    LowerUpperCase // 相当于我们写了 LowerCase(); UpperCase
    FixCaser // 相当于我们写了 FixCase()
}
```

我们又增加了两个接口，所以我们现在有了一种嵌入接口的层次结构，如图 6.2 所示。

| 抽象接口 | 具体类型 |
| --- | --- |
| ChangeCaser | *Part // 是一个 ChangeCaser |
| LowerUpperCaseaser | *Part // 是一个 fmt.Stringer |
| LowerCaser | *StringPair // 是一个 ChangeCaser |
| LowerCase() | *StringPair // 是一个 Exchanger |
| | *StringPair // 是一个 io.Reader |
| | *StringPair // 是一个 fmt.Stringer |
| UpperCaser | Values |
| UpperCase() | part := Part{1439, "File"} |
| FixCaser | pair := StringPair{"Murray", "Bookchin"} |
| FixCase() | |

图 6.2 Caser 接口、类型和示例值

当然，接口本身没有用；我们需要实现它们的具体类型才能它们发挥作用。

```go
func (part *Part) FixCase() {
    part.Name = fixCase(part.Name)
}
```

我们之前见过自定义的 `Part` 类型（260）。在这里，我们添加了一个额外方法 `FixCase()`，它作用于 Part 的 `Name` 字段，就像我们之前看到的 `LowerCase()` 和 `UpperCase()` 方法一样。所有更改大小写的方法都使用指针接收者，因为它们修改了被调用的值。

`LowerCase()` 和 `UpperCase()` 方法使用标准库函数实现，而 `FixCase()` 方法依赖于自定义的 `fixCase()` 函数——这种依赖函数执行工作的微小方法模式在 Go 中非常常见。

`Part.String()` 方法（260）实现了标准库的 `fmt.Stringer` 接口，这意味着任何 `Part`（或 `*Part`）都将使用该方法返回的字符串进行打印。

```go
func fixCase(s string) string {
    var chars []rune
    upper := true
    for _, char := range s {
        if upper {
            char = unicode.ToUpper(char)
        } else {
            char = unicode.ToLower(char)
        }
        chars = append(chars, char)
        upper = unicode.IsSpace(char) || unicode.Is(unicode.Hyphen, char)
    }
    return string(chars)
}
```

这个简单的函数返回它接收到的字符串的副本，其中每个字符都已转小写，除了第一个字符以及每个空白字符或连字符后的第一个字符（这些字符是大大写的）。例如，给定字符串 "lobster sackville-baggings"，函数将返回 "Lobelia Sackville-Baggins"。

自然，我们可以让任何自定义类型满足一个或所有 caser 接口。

```go
func (pair *StringPair) UpperCase() {
    pair.first = strings.ToUpper(pair.first)
    pair.second = strings.ToUpper(pair.second)
}
func (pair *StringPair) LowerCase() {
    pair.first = strings.ToLower(pair.first)
    pair.second = strings.ToLower(pair.second)
}
```
