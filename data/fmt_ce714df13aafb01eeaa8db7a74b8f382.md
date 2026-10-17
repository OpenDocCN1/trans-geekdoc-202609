
许多类型声明这种形式的 `String` 方法，因为它控制着该类型的值在由 `fmt` 包打印为字符串时的外观，正如我们将在第 7.1 节中看到的那样。

```
c := FToC(212.0)
fmt.Println(c.String()) // "100°C"
fmt.Printf("%v\n", c)   // "100°C"; 无需显式调用 String
fmt.Printf("%s\n", c)   // "100°C"
fmt.Println(c)          // "100°C"
fmt.Printf("%g\n", c)   // "100"; 不调用 String
fmt.Println(float64(c)) // "100"; 不调用 String
```

## 2.6 包和文件

Go 语言中的包与其他语言中的库或模块作用相同，支持模块化、封装、单独编译和复用。包的源代码位于一个或多个 `.go` 文件中，通常存放在一个目录里，目录名以导入路径结尾；例如，`gopl.io/ch1/helloworld` 包的文件存放在目录 `$GOPATH/src/gopl.io/ch1/helloworld` 中。

每个包为其声明提供了一个独立的*命名空间*。例如，在 `image` 包中，标识符 `Decode` 指代的函数与 `unicode/utf16` 包中的同名标识符不同。要从包外引用函数，我们必须*限定*标识符，以明确是指 `image.Decode` 还是 `utf16.Decode`。

包还通过控制哪些名称在包外可见（即*导出*），来实现信息隐藏。在 Go 中，一条简单的规则决定了哪些标识符被导出：以大写字母开头的标识符会被导出。

为了演示基础知识，假设我们的温度转换软件变得流行，我们想将其作为一个新包提供给 Go 社区。该如何做呢？

让我们创建一个名为 `gopl.io/ch2/tempconv` 的包，这是前一个示例的变体。（此处我们打破了按顺序编号示例的惯例，以使包路径更现实。）该包本身存储在两个文件中，以展示包内不同文件中的声明如何被访问；在实际中，像这样微小的包只需一个文件即可。

我们将类型、常量及其方法的声明放在 `tempconv.go` 中：

`gopl.io/ch2/tempconv`

```go
// Package tempconv performs Celsius and Fahrenheit conversions.
package tempconv

import "fmt"

type Celsius float64
type Fahrenheit float64

const (
    AbsoluteZeroC Celsius = -273.15
    FreezingC     Celsius = 0
    BoilingC      Celsius = 100
)

func (c Celsius) String() string    { return fmt.Sprintf("%g°C", c) }
func (f Fahrenheit) String() string { return fmt.Sprintf("%g°F", f) }
```

将转换函数放在 `conv.go` 中：

```go
package tempconv

// CToF converts a Celsius temperature to Fahrenheit.
func CToF(c Celsius) Fahrenheit { return Fahrenheit(c*9/5 + 32) }

// FToC converts a Fahrenheit temperature to Celsius.
func FToC(f Fahrenheit) Celsius { return Celsius((f - 32) * 5 / 9) }
```

每个文件都以 `package` 声明开头，定义包名。导入包时，其成员通过 `tempconv.CToF` 等限定名来引用。包级名称（如一个文件中声明的类型和常量）对该包的所有其他文件可见，就好像源代码都在一个文件中一样。注意 `tempconv.go` 导入了 `fmt`，但 `conv.go` 没有，因为它未使用 `fmt` 中的任何内容。

因为包级 `const` 名称以大写字母开头，它们也可以通过限定名（如 `tempconv.AbsoluteZeroC`）访问：

```
fmt.Printf("Brrrr! %v\n", tempconv.AbsoluteZeroC) // "Brrrr! -273.15°C"
```

在导入 `gopl.io/ch2/tempconv` 的包中，要将摄氏温度转换为华氏温度，可以编写如下代码：

```
fmt.Println(tempconv.CToF(tempconv.BoilingC)) // "212°F"
```

紧接在 `package` 声明之前的*文档注释*（§10.7.4）为整个包提供文档。按照惯例，它应以摘要句开头，风格如上所示。每个包中只应有一个文件包含包文档注释。大量的文档注释通常放在单独的文件中，按惯例命名为 `doc.go`。

**练习 2.1：** 向 `tempconv` 添加类型、常量和函数，以处理开尔文温标下的温度，其中零开尔文为 −273.15°C，且 1K 的差值与 1°C 幅度相同。

### 2.6.1 导入

在 Go 程序中，每个包由一个称为*导入路径*的唯一字符串标识。这些字符串出现在 `import` 声明中，如 `"gopl.io/ch2/tempconv"`。语言规范未定义这些字符串的来源或含义；由工具来解释它们。使用 `go` 工具（第 10 章）时，导入路径表示一个目录，其中包含一个或多个 Go 源文件，它们共同构成该包。

除了导入路径，每个包还有一个*包名*，即出现在其 `package` 声明中的简短（且不一定唯一）名称。按照惯例，包名与其导入路径的最后一段匹配，这使得预测 `gopl.io/ch2/tempconv` 的包名为 `tempconv` 变得容易。

要使用 `gopl.io/ch2/tempconv`，我们必须导入它：

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

导入声明将一个短名称绑定到导入的包，该名称可用于在整个文件中引用其内容。上面的 `import` 让我们可以通过使用 *限定标识符*（qualified identifier），如 `tempconv.CToF`，来引用 `gopl.io/ch2/tempconv` 中的名称。默认情况下，短名称即为包名——本例中为 `tempconv`——但导入声明可指定一个替代名称以避免冲突（§10.3）。

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

我们将在下一节和 第 10.5 节 中看到 `init` 函数的其他用法。

**练习 2.3：** 重写 `PopCount` 以使用循环代替单个表达式。比较两个版本的性能。（第 11.4 节 展示了如何系统地比较不同实现的性能。）

**练习 2.4：** 编写一个 `PopCount` 版本，通过将参数移位 64 个位位置，每次测试最右边的位来计数。比较其性能与查表版本的性能。

**练习 2.5：** 表达式 `x&(x-1)` 会清除 `x` 最右边的非零位。编写一个利用此事实计数位数的 `PopCount` 版本，并评估其性能。

## 2.7 作用域

声明将名称与程序实体（如函数或变量）关联。声明的 *作用域*（scope）是源代码中使用该声明名称引用该声明的部分。

不要将作用域与生命周期混淆。声明的作用域是程序文本的一个区域；它是编译时属性。变量的生命周期是程序执行期间变量可被程序其他部分引用的时间范围；它是运行时属性。

语法 *块*（block）是包含在大括号中的语句序列，如包围函数体或循环体的大括号。在语法块内声明的名称在该块外不可见。该块包围其声明并决定其作用域。我们可以将块的概念推广到包括源代码中未显式用大括号包围的其他声明分组；我们将它们全部称为 *词法块*（lexical blocks）。存在一个包含整个源代码的词法块，称为 *全局块*（universe block）；每个包一个；每个文件一个；每个 `for`、`if` 和 `switch` 语句一个；`switch` 或 `select` 语句中每个 case 一个；当然，每个显式语法块也有一个。

声明的词法块决定了其作用域，作用域范围可大可小。内置类型、函数和常量（如 `int`、`len` 和 `true`）的声明位于全局块，可在整个程序中引用。位于任何函数之外的声明，即*包级*声明，可从同一个包中的任意文件引用。导入的包（如 `tempconv` 示例中的 `fmt`）在*文件级*声明，因此只能在同一文件中引用，若要在同一包的另一文件中引用，则需再次 `import`。许多声明（如 `tempconv.CToF` 函数中的变量 `c`）是*局部*的，因此只能在同一函数内部，甚至仅在函数的某一部分中引用。

控制流标签的作用域（由 `break`、`continue` 和 `goto` 语句使用）是整个包含它的函数。

只要每个声明位于不同的词法块中，程序就可以包含多个同名声明。例如，可以声明一个与包级变量同名的局部变量。或者，如第 2.3.3 节所示，可以声明一个名为 `new` 的函数参数，尽管同名函数已在全局块中预先声明。不过不要滥用此特性；重声明的作用域越大，越容易让读者感到意外。

当编译器遇到一个名称引用时，它会从最内层的包含词法块开始，向外逐层查找声明，直到全局块。如果找不到声明，则报告“未声明的名称”错误。如果一个名称在外层块和内层块均有声明，内层声明会被优先找到。此时称内层声明*遮蔽*或*隐藏*了外层声明，使其无法访问：

```
func f() {}

var g = "g"

func main() {
    f := "f"
    fmt.Println(f) // "f"; 局部变量 f 遮蔽了包级函数 f
    fmt.Println(g) // "g"; 包级变量
    fmt.Println(h) // 编译错误: undefined: h
}
```

在函数内部，词法块可嵌套至任意深度，因此一个局部声明可遮蔽另一个。大多数块由控制流结构创建，如 `if` 语句和 `for` 循环。下面的程序有三个名为 `x` 的不同变量，因为每个声明出现在不同的词法块中。（此例说明作用域规则，并非良好风格！）

```
func main() {
    x := "hello!"
    for i := 0; i < len(x); i++ {
        x := x[i]
        if x != '!' {
            x := x + 'A' - 'a'
            fmt.Printf("%c", x) // "HELLO" (每次迭代一个字母)
        }
    }
}
```

表达式 `x[i]` 和 `x + 'A' - 'a'` 分别引用了外层块中 `x` 的声明；稍后我们将解释这一点。（注意后者*不*等同于 `unicode.ToUpper`。）

如前所述，并非所有词法块都对应显式的大括号包裹的语句序列；有些仅是隐式存在。上述 `for` 循环创建了两个词法块：循环体的显式块，以及一个额外包含初始化子句所声明变量（如 `i`）的隐式块。在隐式块中声明的变量，其作用域为 `for` 语句的条件、后置语句（`i++`）和循环体。

下面的示例也有三个名为 `x` 的变量，分别声明在不同的块中——一个在函数体，一个在 `for` 语句的块，一个在循环体——但只有两个块是显式的：

```
func main() {
    x := "hello"
    for _, x := range x {
        x := x + 'A' - 'a'
        fmt.Printf("%c", x) // "HELLO" (每次迭代一个字母)
    }
}
```

与 `for` 循环类似，`if` 语句和 `switch` 语句也会在其主体块之外创建隐式块。以下 `if`-`else` 链中的代码展示了 `x` 和 `y` 的作用域：
