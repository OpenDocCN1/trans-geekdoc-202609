
当然，与“现实世界”的软件相比，这微不足道，但原则依然适用。TDD 是一项需要练习才能发展的技能，但通过将问题分解为可测试的较小组件，你将更容易编写软件。

## 整数

[你可以在这里找到本章的所有代码]

整数的行为正如你所预期的那样。让我们编写一个 `Add` 函数来试试。创建一个名为 `adder_test.go` 的测试文件，并编写以下代码。

**注意：** Go 源文件在每个目录中只能有一个 `package`，请确保你的文件分开组织。[这里有很好的解释。]( )

## 先编写测试

```go
package integers

import "testing"

func TestAdder(t *testing.T) {
    sum := Add(2, 2)
    expected := 4

    if sum != expected {
        t.Errorf("expected '%d' but got '%q'", expected, sum)
    }
}
```

你会注意到我们使用 `%d` 作为格式字符串，而不是 `%q`。这是因为我们希望打印整数而不是字符串。

还要注意，我们不再使用 `main` 包，而是定义了一个名为 `integers` 的包，正如其名，这个包将把处理整数的函数（如 `Add`）分组。

## 尝试运行测试

运行测试 `go test`

检查编译错误

```
./adder_test.go:6:9: undefined: Add
```

## 编写最少的代码使测试运行，并检查失败的测试输出

编写足够的代码来满足编译器，仅此而已——记住，我们希望检查我们的测试是否因为正确的原因而失败。

```
package integers

func Add(x, y int) int {
    return 0
}
```

当你有一个以上相同类型的参数（在我们的例子中是两个整数）时，不需要写成 `(x int, y int)`，可以简写为 `(x, y int)`。

现在运行测试，我们应该满意测试正确地报告了问题。

```
adder_test.go:10: expected '4' but got '0'
```

如果你注意到了，我们在上一节学习了命名返回值，但这里没有使用它。它通常应在结果的含义从上下文中不清楚时使用；在我们的例子中，`Add` 函数会加总参数是相当清楚的。你可以参考这个 wiki 了解更多细节。

## 编写足够的代码使其通过

在 TDD 最严格的意义上，我们现在应该编写*最少的代码使测试通过*。一个吹毛求疵的程序员可能会这样做：

```go
func Add(x, y int) int {
    return 4
}
```

啊哈！又被耍了，TDD 是个骗局，对吧？

我们可以再写一个测试，用一些不同的数字来强制该测试失败，但那感觉像一场猫捉老鼠的游戏。

等我们更熟悉 Go 的语法后，我会介绍一种叫做“基于属性的测试”的技术，它可以避免让开发者烦恼，并帮助你发现 bug。

现在，让我们正确地修复它：

```go
func Add(x, y int) int {
    return x + y
}
```

如果你重新运行测试，它们应该会通过。

## 重构

在*实际*代码中，我们确实没有太多可以改进的地方。

我们之前探讨过，通过命名返回参数，它会出现在文档中，也会出现在大多数开发者的文本编辑器中。

这很棒，因为它有助于提高你所编写代码的可用性。最好用户只需查看类型签名和文档就能理解你代码的用法。

你可以用注释为函数添加文档，这些注释会出现在 Go Doc 中，就像你查看标准库文档时一样。

```
// Add takes two integers and returns the sum of them.
func Add(x, y int) int {
    return x + y
}
```

## 示例

如果你真的想更进一步，你可以制作示例。你会在标准库的文档中找到很多示例。

通常在代码库之外找到的代码示例，例如 README 文件中的示例，往往由于未经检查而变得过时并与实际代码不一致。

Go 示例会像测试一样被执行，所以你可以确信示例反映了代码的实际行为。

示例作为包测试套件的一部分被编译（并可选择执行）。

与典型测试一样，示例是位于包的 `_test.go` 文件中的函数。在 `adder_test.go` 文件中添加以下 `ExampleAdd` 函数。

```
func ExampleAdd() {
    sum := Add(1, 5)
    fmt.Println(sum)
    // Output: 6
}
```

（如果你的编辑器没有自动导入包，编译步骤会失败，因为你会在 `adder_test.go` 中缺少 `import "fmt"`。强烈建议你研究如何在任何你使用的编辑器中自动修复这类错误。）

如果你的代码发生变化，使示例不再有效，你的构建将会失败。

运行包的测试套件，我们可以看到示例函数无需我们做进一步安排即可执行：

```
$ go test -v
=== RUN   TestAdder
--- PASS: TestAdder (0.00s)
=== RUN   ExampleAdd
--- PASS: ExampleAdd (0.00s)
```

请注意，如果你删除注释 `// Output: 6`，示例函数将不会执行。尽管该函数会被编译，但不会被执行。

通过添加这段代码，示例将出现在 godoc 的文档中，使你的代码更加易于访问。

要试用它，请运行 `godoc -http=:6060` 并导航到 `http://localhost:6060/pkg/`

在这里你会看到所有包的列表，你将能找到你的示例文档。

如果你将带有示例的代码发布到公共 URL，你可以在 `pkg.go.dev` 上分享你的代码文档。例如，这里是本章的最终 API。这个网络界面允许你搜索标准库包和第三方包的文档。

## 总结

我们涵盖的内容：

-   更多 TDD 工作流的实践

-   整数、加法

-   编写更好的文档，以便我们代码的用户能快速理解其用法

-   如何使用我们代码的示例，这些示例会作为我们测试的一部分被检查

## 迭代

你可以在这里找到本章的所有代码

要在 Go 中重复做某事，你需要使用 `for`。在 Go 中没有 `while`、`do`、`until` 关键字，你只能使用 `for`。这是一件好事！

让我们为一个重复字符 5 次的函数编写一个测试。

目前为止没有新东西，所以试着自己写一下来练习吧。

## 先编写测试

```
package iteration

import "testing"

func TestRepeat(t *testing.T) {
    repeated := Repeat("a")
    expected := "aaaaa"

    if repeated != expected {
        t.Errorf("expected %q but got %q", expected, repeated)
    }
}
```

## 尝试运行测试

```
./repeat_test.go:6:14: undefined: Repeat
```

## 为测试运行编写最少的代码并检查失败的测试输出

*保持纪律！你现在不需要知道任何新东西就能让测试正确地失败。*

全部你现在需要做的就是让它能够编译，以便你可以检查测试是否写得很好。

```go
package iteration

func Repeat(character string) string {
    return ""
}
```

知道你已经足够了解 Go 来为一些基本问题编写测试，不是很好吗？这意味着你现在可以随意修改生产代码，并且知道它会按预期运行。

`repeat_test.go:10: expected 'aaaaa' but got ''`

## 编写足够代码使其通过

`for` 语法非常普通，遵循大多数类似 C 的语言。

```go
func Repeat(character string) string {
    var repeated string
    for i := 0; i < 5; i++ {
        repeated = repeated + character
    }
    return repeated
}
```

与 C、Java 或 JavaScript 等其他语言不同，`for` 语句的三个组成部分周围没有括号，并且大括号 `{ }` 总是必需的。你可能会想知道下面这行发生了什么

```
var repeated string
```

因为我们目前为止一直使用 `:=` 来声明并初始化变量。然而，`:=` 只是这两个步骤的简写。在这里我们只声明一个字符串变量。因此使用显式版本。我们也可以使用 `var` 来声明函数，正如我们稍后会看到的。

运行测试，它应该会通过。

`for` 循环的额外变体在此描述。

## 重构

现在是时候重构并引入另一个构造 `+=` 赋值运算符了。

```go
const repeatCount = 5
```

```go
func Repeat(character string) string {
    var repeated string
    for i := 0; i < repeatCount; i++ {
        repeated += character
    }
    return repeated
}
```

`+=` 被称为“加法和赋值运算符”，将右操作数添加到左操作数并将结果赋给左操作数。它也适用于整数等其他类型。

## 基准测试

在 Go 中编写基准测试是该语言的另一个一等特性，它与编写测试非常相似。

```go
func BenchmarkRepeat(b *testing.B) {
    for i := 0; i < b.N; i++ {
        Repeat("a")
    }
}
```

你会发现代码与测试非常相似。

`testing.B` 让你可以访问名称晦涩的 `b.N`。

当基准代码执行时，它会运行 `b.N` 次并测量所需时间。

代码运行的次数不应该影响你，框架会确定一个“良好”的值以便获得一些不错的结果。

要运行基准测试，请执行 `go test -bench=.`。（或在 Windows PowerShell 中执行 `go test -bench="."`）

```
goos: darwin
goarch: amd64
pkg: github.com/quii/learn-go-with-tests/for/v4
10000000        136 ns/op
PASS
```

`136 ns/op` 的意思是我们的函数平均需要 136 纳秒运行（在我电脑上）。这相当不错！为此测试它运行了 10000000 次。

*注意* 默认情况下基准测试是顺序运行的。

## 练习题

- 修改测试，使调用者可以指定字符重复的次数，然后修复代码

- 编写 `ExampleRepeat` 来记录你的函数

- 查看 [字符串](strings) 包。找到你认为可能有用的函数，并通过像我们这里一样编写测试来尝试它们。投入时间学习标准库将会在长期内真正得到回报。

## 总结

- 更多 TDD 练习

- 学会了 `for`

- 学会了如何编写基准测试

## 数组和切片

你可以在这里找到本章的所有代码

数组允许你按特定顺序在变量中存储多个相同类型的元素。

当你有一个数组时，通常需要遍历它们。因此，让我们利用我们新获得的 `for` 知识来创建一个 `Sum` 函数。`Sum` 将接收一个数字数组并返回总和。

让我们使用我们的 TDD 技能

## 先写测试

创建一个新文件夹来工作。创建一个名为 `sum_test.go` 的新文件并插入以下内容：

```go
package main

import "testing"

func TestSum(t *testing.T) {
    numbers := [5]int{1, 2, 3, 4, 5}

    got := Sum(numbers)
    want := 15

    if got != want {
        t.Errorf("got %d want %d given, %v", got, want, numbers)
    }
}
```

数组有一个 *固定容量*，你在声明变量时定义。我们可以通过两种方式初始化数组：

- `[N]type{value1, value2, ..., valueN}` 例如 `numbers := [5]int{1, 2, 3, 4, 5}`

- `[...]type{value1, value2, ..., valueN}` 例如 `numbers := [...]int{1, 2, 3, 4, 5}`

有时在错误消息中打印函数的输入也很有用。在这里，我们使用 `%v` 占位符来打印“默认”格式，这对于数组来说效果很好。

[阅读有关格式字符串的更多信息](Read more about the format strings)

## 尝试运行测试

如果你使用 `go mod init main` 初始化了 `go mod`，你会收到错误 `_testmain.go:13:2: cannot import "main"`。这是因为根据常见做法，`package main` 只应包含其他包的集成，而不包含可单元测试的代码，因此 Go 不允许你导入名为 `main` 的包。

要修复这个问题，你可以将 `go.mod` 中的 `main` 模块重命名为其他任意名称。

一旦上述错误修复，如果你运行 `go test`，编译器将以熟悉的 `./sum_test.go:10:15: undefined: Sum` 错误失败。现在我们可以继续编写实际的待测试方法。

### 为测试运行编写最少的代码并检查失败的测试输出

在 `sum.go` 中

```go
package main

func Sum(numbers [5]int) int {
    return 0
}
```

你的测试现在应该会以清晰的错误消息失败

```
sum_test.go:13: got 0 want 15 given, [1 2 3 4 5]
```

## 编写足够代码使其通过

```go
func Sum(numbers [5]int) int {
    sum := 0
    for i := 0; i < 5; i++ {
        sum += numbers[i]
    }
    return sum
}
```

要从数组的特定索引获取值，只需使用 `array[index]` 语法。在这种情况下，我们使用 `for` 迭代 5 次来遍历数组并将每个项目加到 `sum` 上。

## 重构

让我们引入 `range` 来帮助清理我们的代码

```go
func Sum(numbers [5]int) int {
    sum := 0
    for _, number := range numbers {
        sum += number
    }
    return sum
}
```

`range` 让你遍历数组。每次迭代时，`range` 返回两个值 - 索引和值。我们选择使用 `_` blank identifier 来忽略索引值。

## 数组及其类型

数组的一个有趣属性是大小被编码在其类型中。如果你尝试将 `[4]int` 传递给期望 `[5]int` 的函数，它将无法编译。它们是不同的类型，所以就像尝试将字符串传递给想要 `int` 的函数一样。

你可能会觉得数组有固定长度很麻烦，而且大多数时候你可能不会使用它们！

Go 有切片，它们不编码集合的大小，而是可以有任意大小。

下一个需求将是求和不同大小的集合。

## 先写测试

我们现在将使用切片类型，它允许我们拥有任意大小的集合。语法与数组非常相似，你只需在声明时省略大小即可

```
mySlice := []int{1,2,3} rather than myArray := [3]int{1,2,3}
```

```go
func TestSum(t *testing.T) {
    t.Run("collection of 5 numbers", func(t *testing.T) {
        numbers := [5]int{1, 2, 3, 4, 5}
        
        got := Sum(numbers)
        want := 15
        
        if got != want {
            t.Errorf("got %d want %d given, %v", got, want, numbers)
        }
    })
}
```

```go
t.Run("collection of any size", func(t *testing.T) {
    numbers := []int{1, 2, 3}

    got := Sum(numbers)
    want := 6

    if got != want {
        t.Errorf("got %d want %d given, %v", got, want, numbers)
    }
})
```

## 尝试并运行测试

这无法编译

```
./sum_test.go:22:13: cannot use numbers (type []int) as type [5]int in argument to Sum
```

## 为测试运行编写最少的代码并检查失败的测试输出

这里的问题是我们有两个选择

- 通过将 `Sum` 的参数改为切片而不是数组来破坏现有 API。这样做时，我们可能会毁掉某人的日子，因为我们的其他测试将不再编译！

- 创建一个新函数

在我们的例子中，没有其他人使用我们的函数，所以与其维护两个函数，不如只有一个。

```go
func Sum(numbers []int) int {
    sum := 0
    for _, number := range numbers {
        sum += number
    }
    return sum
}
```
