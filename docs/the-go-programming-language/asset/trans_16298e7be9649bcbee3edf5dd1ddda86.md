
## 我们如何知道给定随机输入时函数的预期输出？

有两种策略。第一种是编写该函数的另一种实现，该实现使用效率较低但更简单、更清晰的算法，并检查两种实现是否给出相同的结果。第二种是根据某种模式创建输入值，以便我们知道预期的输出。

下面的示例使用第二种方法：`randomPalindrome` 函数根据构造生成已知为回文的单词。

[点击此处查看代码图像](#ch11_images.html#id307pro01_r)

```go
import "math/rand"

// randomPalindrome 返回一个回文，其长度和内容
// 源自伪随机数生成器 rng。
func randomPalindrome(rng *rand.Rand) string {
    n := rng.Intn(25) // 随机长度，最长 24
    runes := make([]rune, n)
    for i := 0; i < (n+1)/2; i++ {
        r := rune(rng.Intn(0x1000)) // 随机 rune，最大为 '\u0999'
        runes[i] = r
        runes[n-1-i] = r
    }
    return string(runes)
}

func TestRandomPalindromes(t *testing.T) {
    // 初始化一个伪随机数生成器。
    seed := time.Now().UTC().UnixNano()
    t.Logf("Random seed: %d", seed)
    rng := rand.New(rand.NewSource(seed))

    for i := 0; i < 1000; i++ {
        p := randomPalindrome(rng)
        if !IsPalindrome(p) {
            t.Errorf("IsPalindrome(%q) = false", p)
        }
    }
}
```

由于随机测试是非确定性的，因此至关重要的是，失败测试的日志要记录足够的信息以复现故障。在我们的示例中，传给 `IsPalindrome` 的输入 `p` 已经告诉了我们所需的一切，但对于接受更复杂输入的函数，记录伪随机数生成器的种子（如我们上面所做）可能比转储整个输入数据结构更简单。有了该种子值，我们可以轻松修改测试以确定性地重放故障。

通过使用当前时间作为随机性来源，每次运行测试时都会探索新的输入，贯穿其整个生命周期。如果您的项目使用自动化系统定期运行所有测试，这将特别有价值。

### 练习 11.3

`TestRandomPalindromes` 仅测试回文。编写一个随机测试来生成并验证*非*回文。

### 练习 11.4

修改 `randomPalindrome` 以测试 `IsPalindrome` 对标点符号和空格的处理。

## 11.2.2 测试命令

`go test` 工具适用于测试库包，但稍加努力我们也可以用它来测试命令。通常名为 `main` 的包会生成可执行程序，但它也可以作为库被导入。

让我们为 [2.3.2 节](#ebook_split_022.html#id-flag) 中的 `echo` 程序编写一个测试。我们已将程序拆分为两个函数：`echo` 完成实际工作，而 `main` 解析并读取标志值，并报告 `echo` 返回的任何错误。

[点击此处查看代码图像](#ch11_images.html#id308pro01_r)

`gopl.io/ch11/echo`

```go
// Echo 打印其命令行参数。
package main

import (
    "flag"
    "fmt"
    "io"
    "os"
    "strings"
)

var (
    n = flag.Bool("n", false, "省略尾随换行符")
    s = flag.String("s", " ", "分隔符")
)

var out io.Writer = os.Stdout // 测试期间会被修改

func main() {
    flag.Parse()
    if err := echo(!*n, *s, flag.Args()); err != nil {
        fmt.Fprintf(os.Stderr, "echo: %v\n", err)
        os.Exit(1)
    }
}

func echo(newline bool, sep string, args []string) error {
    fmt.Fprint(out, strings.Join(args, sep))
    if newline {
        fmt.Fprintln(out)
    }
    return nil
}
```

在测试中，我们将使用各种参数和标志设置调用 `echo`，并检查它在每种情况下是否打印正确的输出，因此我们给 `echo` 添加了参数以减少其对全局变量的依赖。话虽如此，我们也引入了另一个全局变量 `out`，即写入结果的 `io.Writer`。通过让 `echo` 通过该变量写入，而不是直接写入 `os.Stdout`，测试可以替换一个不同的 `Writer` 实现，以记录写入的内容供后续检查。这是测试代码，位于文件 `echo_test.go` 中：

[点击此处查看代码图像](#ch11_images.html#id309pro01_r)

```go
package main

import (
    "bytes"
    "fmt"
    "testing"
)

func TestEcho(t *testing.T) {
    var tests = []struct {
        newline bool
        sep     string
        args    []string
        want    string
    }{
        {true, "", []string{}, "\n"},
        {false, "", []string{}, ""},
        {true, "\t", []string{"one", "two", "three"}, "one\ttwo\tthree\n"},
        {true, ",", []string{"a", "b", "c"}, "a,b,c\n"},
        {false, ":", []string{"1", "2", "3"}, "1:2:3"},
    }

    for _, test := range tests {
        descr := fmt.Sprintf("echo(%v, %q, %q)",
            test.newline, test.sep, test.args)

        out = new(bytes.Buffer) // 捕获的输出
        if err := echo(test.newline, test.sep, test.args); err != nil {
            t.Errorf("%s failed: %v", descr, err)
            continue
        }
        got := out.(*bytes.Buffer).String()
        if got != test.want {
            t.Errorf("%s = %q, want %q", descr, got, test.want)
        }
    }
}
```

请注意，测试代码与生产代码位于同一个包中。尽管包名为 `main` 且定义了 `main` 函数，但在测试期间，该包作为一个库，向测试驱动程序暴露 `TestEcho` 函数；其 `main` 函数会被忽略。

通过将测试组织为表格，我们可以轻松添加新的测试用例。让我们看看测试失败时会发生什么，通过向表格添加此行：

[点击此处查看代码图像](#ch11_images.html#id310pro01_r)

```go
{true, ",", []string{"a", "b", "c"}, "a b c\n"}, // 注意：错误的预期！
```

`go test` 打印

[点击此处查看代码图像](#ch11_images.html#id310pro02_r)

```
$ go test gopl.io/ch11/echo
--- FAIL: TestEcho (0.00s)
    echo_test.go:31: echo(true, ",", ["a" "b" "c"]) = "a,b,c", want "a b c\n"
FAIL
FAIL    gopl.io/ch11/echo   0.006s
```

错误消息按顺序描述了尝试的操作（使用类 Go 语法）、实际行为和预期行为。有了这样信息丰富的错误消息，在您甚至还没定位到测试源代码之前，可能就已经对根本原因有了相当好的了解。

被测代码不调用 `log.Fatal` 或 `os.Exit` 非常重要，因为这些会让进程戛然而止；调用这些函数应被视为 `main` 的专属权利。如果发生完全意外的情况导致函数 panic，测试驱动程序会恢复，尽管测试当然会被视为失败。预期的错误（如因错误的用户输入、缺失文件或不当配置导致的错误）应通过返回非 nil 的 `error` 值来报告。幸运的是（虽然作为说明很不幸），我们的 `echo` 示例太简单了，永远不会返回非 nil 错误。

## 11.2.3 白盒测试

对测试进行分类的一种方式是根据它们对被测包内部工作原理所需了解的程度。*黑盒* 测试除包的 API 暴露的内容及其文档规定的内容外，不假设包的任何内部细节；包的内部是不透明的。相反，*白盒* 测试拥有包内部函数和数据结构的特权访问权，可以进行普通客户端无法进行的观察和更改。例如，白盒测试可以检查包的数据类型不变量在每次操作后是否得以维护。（*白盒* 之名沿用至今，但 *透明盒* 会更准确。）
