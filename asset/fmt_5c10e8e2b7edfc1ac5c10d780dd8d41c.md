
```go
usage[user] = 980000000 // simulate a 980MB-used condition

CheckQuota(user)

if notifiedUser == "" && notifiedMsg == "" {
    t.Fatalf("notifyUser not called")
}

if notifiedUser != user {
    t.Errorf("wrong user (%s) notified, want %s",
        notifiedUser, user)
}

const wantSubstring = "98% of your quota"

if !strings.Contains(notifiedMsg, wantSubstring) {
    t.Errorf("unexpected notification message <<%s>>, "+
        "want substring %q", notifiedMsg, wantSubstring)
}
```

存在一个问题：测试函数返回后，`CheckQuota` 不再按预期工作，因为它仍在使用测试的 `notifyUser` 伪实现。（更新全局变量时总存在这种风险。）我们必须修改测试以恢复之前的值，使后续测试不受影响，且必须在所有执行路径上（包括测试失败和 panic）都执行恢复。这自然用到了 `defer`。

```go
func TestCheckQuotaNotifiesUser(t *testing.T) {
    // Save and restore original notifyUser.
    saved := notifyUser
    defer func() { notifyUser = saved }()

    // Install the test's fake notifyUser.
    var notifiedUser, notifiedMsg string
    notifyUser = func(user, msg string) {
        notifiedUser, notifiedMsg = user, msg
    }

    // ...rest of test...
}
```

此模式可用于临时保存和恢复各种全局变量，包括命令行标志、调试选项和性能参数；安装和移除钩子，使生产代码在发生有趣事件时调用测试代码；以及诱导生产代码进入罕见但重要的状态，如超时、错误，甚至并发活动的特定交错时序。

仅因为 `go test` 通常不并发运行多个测试，以这种方式使用全局变量才是安全的。

# 11.2.4 外部测试包

考虑包 `net/url`（提供 URL 解析器）和 `net/http`（提供 Web 服务器和 HTTP 客户端库）。正如预期，高层包 `net/http` 依赖低层包 `net/url`。然而，`net/url` 中的一个测试是演示 URL 与 HTTP 客户端库交互的示例。换句话说，低层包的测试导入了高层包。

![A test of net/url depends on net/http.](img/testcycle.png)

**图 11.1.** `net/url` 的测试依赖 `net/http`。

如果在 `net/url` 包中声明此测试函数，将在包导入图中形成循环（如图 11.1 中的向上箭头所示），但正如第 10.1 节所述，Go 规范禁止导入循环。

我们通过在*外部测试包*中声明测试函数来解决此问题，即在 `net/url` 目录下的文件中，其包声明为 `package url_test`。额外的后缀 `_test` 向 `go test` 发出信号：它应构建一个仅包含这些文件的额外包并运行其测试。可以将此外部测试包视为导入路径为 `net/url_test` 的包，但它不能在此名称或任何其他名称下被导入。

因为外部测试位于单独的包中，它们可以导入也依赖被测包的辅助包；包内测试无法做到这一点。从设计层级来看，外部测试包在逻辑上高于它所依赖的两个包，如图 11.2 所示。

![External test packages break dependency cycles.](img/externaltest.png)

**图 11.2.** 外部测试包打破依赖循环。

通过避免导入循环，外部测试包允许测试（特别是*集成测试*，即测试多个组件的交互）自由导入其他包，就像应用程序一样。

## 使用 `go list` 工具总结包文件

我们可以使用 `go list` 工具来总结包目录中哪些 Go 源文件是生产代码、包内测试和外部测试。我们将以 `fmt` 包为例。`GoFiles` 是包含生产代码的文件列表；这些是 `go build` 将包含在应用程序中的文件：

```bash
$ go list -f={{.GoFiles}} fmt
[doc.go format.go print.go scan.go]
```

`TestGoFiles` 是也属于 `fmt` 包的文件列表，但这些文件的名称都以 `_test.go` 结尾，仅在构建测试时包含：

```bash
$ go list -f={{.TestGoFiles}} fmt
[export_test.go]
```

包的测试通常位于这些文件中，虽然 `fmt` 包异常地没有测试；我们稍后将解释 `export_test.go` 的用途。

`XTestGoFiles` 是构成外部测试包 `fmt_test` 的文件列表，因此这些文件必须导入 `fmt` 包才能使用它。同样，它们仅在测试期间包含：

```bash
$ go list -f={{.XTestGoFiles}} fmt
[fmt_test.go scan_test.go stringer_test.go]
```

有时外部测试包可能需要对被测包的内部拥有特权访问，例如白盒测试必须位于单独的包中以避免导入循环。在这种情况下，我们使用一个技巧：向包内的 `_test.go` 文件添加声明，以将必要的内部暴露给外部测试。因此，该文件为测试提供了包的“后门”。如果源文件仅为此目的而存在且本身不包含测试，通常称为 `export_test.go`。

例如，`fmt` 包的实现需要 `unicode.IsSpace` 的功能作为 `fmt.Scanf` 的一部分。为避免创建不希望的依赖，`fmt` 不导入 `unicode` 包及其大量数据表；相反，它包含一个更简单的实现，称为 `isSpace`。

为确保 `fmt.isSpace` 和 `unicode.IsSpace` 的行为不发生偏离，`fmt` 审慎地包含了一个测试。这是一个外部测试，因此无法直接访问 `isSpace`，所以 `fmt` 通过声明一个持有内部 `isSpace` 函数的导出变量为其打开了后门。这就是 `fmt` 包的 `export_test.go` 文件的全部内容。

```go
package fmt

var IsSpace = isSpace
```

此测试文件不定义测试；它只是为外部测试声明导出符号 `fmt.IsSpace`。每当外部测试需要使用某些白盒测试技术时，也可以使用此技巧。

## 11.2.5 编写有效的测试

许多 Go 新手对 Go 测试框架的极简主义感到惊讶。其他语言的框架提供识别测试函数的机制（通常使用反射或元数据），在测试运行前后执行“设置”和“拆卸”操作的钩子，以及用于断言常见谓词、比较值、格式化错误消息和中止失败测试的实用函数库（通常使用异常）。虽然这些机制可以使测试非常简洁，但生成的测试往往看起来像是用外语编写的。此外，虽然它们可能正确地报告 `PASS` 或 `FAIL`，但它们的方式可能对倒霉的维护者不友好，给出晦涩的失败消息，如 `"assert: 0 == 1"` 或大量的堆栈跟踪。

Go 对测试的态度形成了鲜明对比。它期望测试作者自己完成大部分工作，定义函数以避免重复，就像为普通程序所做的那样。测试过程不是机械填表；测试也有用户界面，尽管其唯一的用户也是其维护者。好的测试在失败时不会崩溃，而是打印清晰简洁的问题症状描述，或许还有其他相关的上下文事实。理想情况下，维护者不需要阅读源代码即可理解测试失败。好的测试不应在一次失败后放弃，而应尝试在一次运行中报告多个错误，因为失败的模式本身可能揭示问题。

下面的断言函数比较两个值，构造通用错误消息并停止程序。它易于使用且正确，但失败时错误消息几乎毫无用处。它没有解决提供良好用户界面的难题。

```go
import (
    "fmt"
    "strings"
    "testing"
)

// 一个糟糕的断言函数。
func assertEqual(x, y int) {
    if x != y {
        panic(fmt.Sprintf("%d != %d", x, y))
    }
}

func TestSplit(t *testing.T) {
    words := strings.Split("a:b:c", ":")
    assertEqual(len(words), 3)
    // ...
}
```

从这个意义上说，断言函数患有*过早抽象*：通过将此特定测试的失败视为两个整数的简单差异，我们放弃了提供有意义上下文的机会。我们可以通过从具体细节入手来提供更好的消息，如下例所示。只有在给定测试套件中出现重复模式时，才是引入抽象的时候。

```go
func TestSplit(t *testing.T) {
    s, sep := "a:b:c", ":"
    words := strings.Split(s, sep)
    if got, want := len(words), 3; got != want {
        t.Errorf("Split(%q, %q) returned %d words, want %d",
            s, sep, got, want)
    }
    // ...
}
```

现在测试报告了被调用的函数、其输入以及结果的意义；它明确标识了实际值和期望值；并且即使此断言失败也会继续执行。一旦我们编写了这样的测试，自然的下一步通常不是定义一个函数来替换整个 `if` 语句，而是在一个循环中执行测试，其中 `s`、`sep` 和 `want` 变化，就像 `IsPalindrome` 的表驱动测试一样。

前面的示例不需要任何实用函数，但当然这不应阻止我们在函数有助于简化代码时引入它们。（我们将在 13.3 节 中查看这样一个实用函数 `reflect.DeepEqual`。）好测试的关键是从实现你想要的具体行为开始，然后才使用函数来简化代码并消除重复。最好的结果很少是从抽象的、通用的测试函数库开始获得的。

**练习 11.5：** 扩展 `TestSplit` 以使用输入和期望输出的表格。

## 11.2.6 避免脆弱的测试

当遇到新但有效的输入时经常失败的应用程序称为*有缺陷的*；当对程序进行合理更改时虚假失败的测试称为*脆弱的*。正如有缺陷的程序让用户沮丧一样，脆弱的测试让维护者恼火。最脆弱的测试，几乎对生产代码的任何更改（无论好坏）都会失败，有时称为*变更检测器*或*现状*测试，处理它们所花费的时间会迅速耗尽它们曾经似乎提供的任何好处。

当被测函数产生复杂输出（如长字符串、精密数据结构或文件）时，很容易检查输出是否完全等于编写测试时预期的某个“黄金”值。但随着程序的发展，输出的部分内容很可能会改变，可能是向好的方向，但终究是改变了。不仅仅是输出；具有复杂输入的函数经常因为测试中使用的输入不再有效而中断。

避免脆弱测试的最简单方法是只检查你关心的属性。优先测试程序较简单且更稳定的接口，而非其内部函数。在断言时要有选择性。例如，不要检查精确的字符串匹配，而应寻找随着程序演进而保持不变的相关子串。编写一个大量函数将复杂的输出提炼为其本质，以使断言可靠，这通常是值得的。尽管这看起来像是大量的前期工作，但它能通过节省原本用于修复虚假失败测试的时间而迅速“回本”。

## 11.3 覆盖率

就其本质而言，测试永远是不完全的。正如有影响力的计算机科学家 Edsger Dijkstra 所言：“测试证明的是缺陷的存在，而非缺陷的不存在。” 任何数量的测试都无法证明一个包没有 bug。充其量，它们只能增加我们的信心，即该包在各种重要场景下都能良好工作。

测试套件对被测包的执行程度称为测试的*覆盖率*。覆盖率无法直接量化——除最简单的程序外，所有程序的动态行为都超出了精确测量的范围——但有一些启发式方法可以帮助我们将测试工作引导至更可能有用的地方。

*语句覆盖率* 是这些启发式方法中最简单、应用最广泛的一种。测试套件的语句覆盖率是指在测试期间至少被执行一次的源代码语句所占的比例。在本节中，我们将使用 Go 的 `cover` 工具（它集成在 `go test` 中）来度量语句覆盖率，并帮助识别测试中明显的空白。

下面的代码是一个表驱动测试，用于测试我们在第 7 章构建的表达式求值器：

```go
func TestCoverage(t *testing.T) {
    var tests = []struct {
        input string
        env   Env
        want  string // 来自 Parse/Check 的预期错误或来自 Eval 的预期结果
    }{
        {"x % 2", nil, "unexpected '%'"},
        {"!true", nil, "unexpected '!'"},
        {"log(10)", nil, `unknown function "log"`},
        {"sqrt(1, 2)", nil, "call to sqrt has 2 args, want 1"},
        {"sqrt(A / pi)", Env{"A": 87616, "pi": math.Pi}, "167"},
        {"pow(x, 3) + pow(y, 3)", Env{"x": 9, "y": 10}, "1729"},
        {"5 / 9 * (F - 32)", Env{"F": -40}, "-40"},
    }

    for _, test := range tests {
        expr, err := Parse(test.input)
        if err == nil {
            err = expr.Check(map[Var]bool{})
        }
        if err != nil {
            if err.Error() != test.want {
                t.Errorf("%s: got %q, want %q", test.input, err, test.want)
            }
            continue
        }
        got := fmt.Sprintf("%.6g", expr.Eval(test.env))
        if got != test.want {
            t.Errorf("%s: %v => %s, want %s",
                test.input, test.env, got, test.want)
        }
    }
}
```

首先，让我们检查测试是否通过：

```bash
$ go test -v -run=Coverage gopl.io/ch7/eval
=== RUN TestCoverage
--- PASS: TestCoverage (0.00s)
PASS
ok      gopl.io/ch7/eval    0.011s
```

此命令显示覆盖率工具的用法信息：

```bash
$ go tool cover
Usage of 'go tool cover':
Given a coverage profile produced by 'go test':
    go test -coverprofile=c.out
Open a web browser displaying annotated source code:
    go tool cover -html=c.out
...
```

`go tool` 命令运行 Go 工具链中的一个可执行文件。这些程序位于目录 `$GOROOT/pkg/tool/${GOOS}_${GOARCH}` 中。得益于 `go build`，我们很少需要直接调用它们。

现在我们使用 `-coverprofile` 标志运行测试：

```bash
$ go test -run=Coverage -coverprofile=c.out gopl.io/ch7/eval
ok      gopl.io/ch7/eval    0.032s  coverage: 68.5% of statements
```

此标志通过*插桩*生产代码来启用覆盖率数据的收集。也就是说，它修改源代码的副本，以便在执行每个语句块之前设置一个布尔变量，每个块对应一个变量。在修改后的程序退出前，它将每个变量的值写入指定的日志文件 `c.out`，并打印已执行语句所占比例的摘要。（如果你只需要摘要，请使用 `go test -cover`。）

如果使用 `-covermode=count` 标志运行 `go test`，每个块的插桩代码将递增一个计数器，而不是设置布尔值。生成的每个块执行计数日志允许对执行更频繁的“热点”块和执行较少的“冷点”块进行定量比较。

收集到数据后，我们运行 `cover` 工具，它处理日志，生成 HTML 报告，并在新浏览器窗口中打开它（图 11.3）。
