

[单击此处查看代码图像](#ch02_images.html#id043pro01_r)

`gopl.io/ch2/cf`

```go
// Cf 将其数值参数转换为摄氏度和华氏度。
package main

import (
    "fmt"
    "os"
    "strconv"

    "gopl.io/ch2/tempconv"
)

func main() {
    for _, arg := range os.Args[1:] {
        t, err := strconv.ParseFloat(arg, 64)
        if err != nil {
            fmt.Fprintf(os.Stderr, "cf: %v\n", err)
            os.Exit(1)
        }
        f := tempconv.Fahrenheit(t)
        c := tempconv.Celsius(t)
        fmt.Printf("%s = %s, %s = %s\n",
            f, tempconv.FToC(f), c, tempconv.CToF(c))
    }
}
```

导入声明将一个短名称绑定到导入的包，该名称可用于在整个文件中引用其内容。上面的 `import` 让我们可以通过使用 *限定标识符*（qualified identifier），如 `tempconv.CToF`，来引用 `gopl.io/ch2/tempconv` 中的名称。默认情况下，短名称即为包名——本例中为 `tempconv`——但导入声明可指定一个替代名称以避免冲突（[§10.3](#ebook_split_098.html#id-thepackagedeclaration)）。

`cf` 程序将单个数值命令行参数转换为其在摄氏度和华氏度下的值：

```
$ go build gopl.io/ch2/cf
$ ./cf 32
32°F = 0°C, 32°C = 89.6°F
$ ./cf 212
212°F = 100°C, 212°C = 413.6°F
$ ./cf -40
-40°F = -40°C, -40°C = -40°F
```

导入包后又不引用它属于错误。此检查有助于消除随着代码演变而变得不必要的依赖，尽管在调试期间这可能会成为一种烦恼，因为注释掉一行代码（如 `log.Print("got here!")`）可能会移除对包名 `log` 的唯一引用，导致编译器报错。在这种情况下，你需要注释掉或删除不必要的 `import`。

更好的做法是使用 `golang.org/x/tools/cmd/goimports` 工具，它会根据需要自动在导入声明中插入和移除包；大多数编辑器都可配置为在每次保存文件时运行 `goimports`。与 `gofmt` 工具一样，它也会按规范格式美化 Go 源文件。

**练习 2.2：** 编写一个通用的单位转换程序，类似于 `cf`，从命令行参数读取数字，如果没有参数则从标准输入读取，并将每个数字转换为摄氏度和华氏度等温度单位、英尺和米等长度单位、磅和千克等重量单位，等等。

### 2.6.2 包初始化

包初始化首先按声明顺序初始化包级变量，只不过会优先解析依赖关系：

[单击此处查看代码图像](#ch02_images.html#id044pro01_r)

```go
var a = b + c     // a 第三个初始化，值为 3
var b = f()       // b 第二个初始化，值为 2，通过调用 f
var c = 1         // c 第一个初始化，值为 1

func f() int { return c + 1 }
```

如果包有多个 `.go` 文件，它们将按提供给编译器的顺序初始化；`go` 工具会在调用编译器前按名称对 `.go` 文件排序。

每个在包级声明的变量最初都以其初始化表达式的值（如果有）开始其生命周期，但对于某些变量（如数据表），初始化表达式可能不是设置其初始值的最简单方法。在这种情况下，`init` 函数机制可能更简单。任何文件都可以包含任意数量的仅声明为以下形式的函数：

```go
func init() { /* ... */ }
```

此类 `init` 函数无法被调用或引用，但除此之外它们是普通函数。在每个文件中，`init` 函数会在程序启动时自动执行，按声明顺序依次执行。

包的初始化是一次一个进行的，按程序中的导入顺序，依赖优先，因此导入 `q` 的包 `p` 可以确信在 `p` 的初始化开始前 `q` 已完全初始化。初始化自底向上进行；`main` 包是最后被初始化的。以此方式，在应用程序的 `main` 函数开始之前，所有包都已完全初始化。

下面的包定义了一个 `PopCount` 函数，返回 `uint64` 值中设置的位数（即值为 1 的位数），这称为其 *population count*（人口计数/位计数）。它使用 `init` 函数预计算一个结果表 `pc`，包含每个可能的 8 位值，这样 `PopCount` 函数无需执行 64 步，只需返回八次表查找的总和即可。（这绝对 *不是* 计算位数的最快算法，但它便于演示 `init` 函数，并展示如何预计算值表，这通常是一种有用的编程技巧。）

[单击此处查看代码图像](#ch02_images.html#id045pro01_r)

`gopl.io/ch2/popcount`

```go
package popcount

// pc[i] 是 i 的人口计数（population count）。
var pc [256]byte

func init() {
    for i := range pc {
        pc[i] = pc[i/2] + byte(i&1)
    }
}

// PopCount 返回 x 的人口计数（设置位的数量）。
func PopCount(x uint64) int {
    return int(pc[byte(x>>(0*8))] +
        pc[byte(x>>(1*8))] +
        pc[byte(x>>(2*8))] +
        pc[byte(x>>(3*8))] +
        pc[byte(x>>(4*8))] +
        pc[byte(x>>(5*8))] +
        pc[byte(x>>(6*8))] +
        pc[byte(x>>(7*8))])
}
```

注意 `init` 中的 `range` 循环仅使用了索引；值是不必要的，因此无需包含。该循环也可写为：

```go
for i, _ := range pc {
```

我们将在下一节和 [第 10.5 节](#ebook_split_100.html#id-blankimports) 中看到 `init` 函数的其他用法。

**练习 2.3：** 重写 `PopCount` 以使用循环代替单个表达式。比较两个版本的性能。([第 11.4 节](#ebook_split_107.html#id-benchmarkfunctions) 展示了如何系统地比较不同实现的性能。)

**练习 2.4：** 编写一个 `PopCount` 版本，通过将参数移位 64 个位位置，每次测试最右边的位来计数。比较其性能与查表版本的性能。

**练习 2.5：** 表达式 `x&(x-1)` 会清除 `x` 最右边的非零位。编写一个利用此事实计数位数的 `PopCount` 版本，并评估其性能。

## 2.7 作用域

声明将名称与程序实体（如函数或变量）关联。声明的 *作用域*（scope）是源代码中使用该声明名称引用该声明的部分。

不要将作用域与生命周期混淆。声明的作用域是程序文本的一个区域；它是编译时属性。变量的生命周期是程序执行期间变量可被程序其他部分引用的时间范围；它是运行时属性。

语法 *块*（block）是包含在大括号中的语句序列，如包围函数体或循环体的大括号。在语法块内声明的名称在该块外不可见。该块包围其声明并决定其作用域。我们可以将块的概念推广到包括源代码中未显式用大括号包围的其他声明分组；我们将它们全部称为 *词法块*（lexical blocks）。存在一个包含整个源代码的词法块，称为 *全局块*（universe block）；每个包一个；每个文件一个；每个 `for`、`if` 和 `switch` 语句一个；`switch` 或 `select` 语句中每个 case 一个；当然，每个显式语法块也有一个。

