

### 练习 11.2

为 `IntSet` 编写一组测试（[§6.5](#part0058.html#id-intset)），检查其每次操作后的行为是否等同于基于内置 map 的集合。将你的实现保存下来，以便在[练习 11.7](#part0108.html#id-ex-intsetbenchmark)中进行基准测试。

## 11.2.1 随机化测试

表驱动测试便于检查函数是否能在精心挑选的、能覆盖逻辑中有趣情况的输入上正常工作。另一种方法是*随机化测试*，它通过随机构造输入来探索更广泛的输入范围。

给定随机输入，我们如何知道函数的预期输出是什么？有两种策略。第一种是编写该函数的另一种实现，该实现使用效率较低但更简单、更清晰的算法，然后检查两种实现是否给出相同的结果。第二种是按照某种模式创建输入值，以便我们知道预期的输出是什么。

下面的示例使用第二种方法：`randomPalindrome` 函数根据其构造方式生成已知为回文的单词。

[点击此处查看代码图像](#part0141_split_011.html#id307pro01_r)

```go
import "math/rand"

// randomPalindrome returns a palindrome whose length and contents
// are derived from the pseudo-random number generator rng.
func randomPalindrome(rng *rand.Rand) string {
    n := rng.Intn(25) // random length up to 24
    runes := make([]rune, n)
    for i := 0; i < (n+1)/2; i++ {
        r := rune(rng.Intn(0x1000)) // random rune up to '\u0999'
        runes[i] = r
        runes[n-1-i] = r
    }
    return string(runes)
}

func TestRandomPalindromes(t *testing.T) {
    // Initialize a pseudo-random number generator.
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

由于随机化测试是非确定性的，失败测试的日志必须记录足够的信息以复现失败至关重要。在我们的例子中，传给 `IsPalindrome` 的输入 `p` 就告诉了我们所有需要知道的信息，但对于接受更复杂输入的函数，记录伪随机数生成器的种子（如我们上面所做）可能比转储整个输入数据结构更简单。有了该种子值，我们可以轻松修改测试以确定性地重放失败。

通过使用当前时间作为随机性来源，测试在其整个生命周期内每次运行时都会探索新的输入。如果你的项目使用自动化系统定期运行所有测试，这尤其有价值。

**练习 11.3：** `TestRandomPalindromes` 只测试回文。编写一个随机化测试来生成并验证*非*回文。

**练习 11.4：** 修改 `randomPalindrome` 以测试 `IsPalindrome` 对标点和空格的处理。

## 11.2.2 测试命令

`go test` 工具适用于测试库包，但稍加努力也可用它来测试命令。名为 `main` 的包通常会生成可执行程序，但它也可以作为库被导入。

让我们为[第 2.3.2 节](#part0023.html#id-flag)中的 `echo` 程序编写测试。我们将程序拆分为两个函数：`echo` 完成实际工作，而 `main` 解析并读取标志值，并报告 `echo` 返回的任何错误。

[点击此处查看代码图像](#part0141_split_012.html#id308pro01_r)

`gopl.io/ch11/echo`

```go
// Echo prints its command-line arguments.
package main

import (
    "flag"
    "fmt"
    "io"
    "os"
    "strings"
)

var (
    n = flag.Bool("n", false, "omit trailing newline")
    s = flag.String("s", " ", "separator")
)

var out io.Writer = os.Stdout // modified during testing

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

在测试中，我们将使用各种参数和标志设置来调用 `echo`，并检查它在每种情况下是否打印正确的输出，因此我们给 `echo` 添加了参数以减少其对全局变量的依赖。虽说如此，我们也引入了另一个全局变量 `out`，即将结果写入的 `io.Writer`。通过让 `echo` 通过该变量写入，而不是直接写入 `os.Stdout`，测试可以替换一个不同的 `Writer` 实现，记录写入的内容以供后续检查。这是文件 `echo_test.go` 中的测试：

[点击此处查看代码图像](#part0141_split_013.html#id309pro01_r)

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

        out = new(bytes.Buffer) // captured output
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

注意测试代码与生产代码在同一个包中。虽然包名是 `main` 且定义了 `main` 函数，但在测试期间，该包作为一个库，向测试驱动程序暴露 `TestEcho` 函数；其 `main` 函数会被忽略。

通过将测试组织为表格，我们可以轻松添加新的测试用例。让我们向表中添加此行，看看测试失败时会发生什么：

[点击此处查看代码图像](#part0141_split_014.html#id310pro01_r)

```go
{true, ",", []string{"a", "b", "c"}, "a b c\n"}, // NOTE: wrong expectation!
```

`go test` 打印

[点击此处查看代码图像](#part0141_split_015.html#id310pro02_r)

```
$ go test gopl.io/ch11/echo
--- FAIL: TestEcho (0.00s)
    echo_test.go:31: echo(true, ",", ["a" "b" "c"]) = "a,b,c", want "a b c\n"
FAIL
FAIL    gopl.io/ch11/echo   0.006s
```

错误消息按顺序描述了尝试的操作（使用类 Go 语法）、实际行为和预期行为。有了这样信息丰富的错误消息，在你甚至还没定位到测试源代码之前，可能就已经对根本原因有了相当好的了解。

被测试的代码不应调用 `log.Fatal` 或 `os.Exit`，这一点很重要，因为这些会立即停止进程；调用这些函数应被视为 `main` 的专有权利。如果发生完全意外的情况导致函数 panic，测试驱动程序会恢复，尽管测试当然会被视为失败。预期的错误（如由错误的用户输入、缺失文件或不当配置引起的错误）应通过返回非 nil 的 `error` 值来报告。幸运的是（作为演示却很不幸），我们的 `echo` 示例太简单了，以至于永远不会返回非 nil 的错误。

## 11.2.3 白盒测试

