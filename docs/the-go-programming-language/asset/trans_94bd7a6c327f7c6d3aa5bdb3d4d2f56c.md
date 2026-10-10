
避免脆弱测试的最简单方法是只检查你关心的属性。优先测试程序较简单且更稳定的接口，而非其内部函数。在断言时要有选择性。例如，不要检查精确的字符串匹配，而应寻找随着程序演进而保持不变的相关子串。编写一个大量函数将复杂的输出提炼为其本质，以使断言可靠，这通常是值得的。尽管这看起来像是大量的前期工作，但它能通过节省原本用于修复虚假失败测试的时间而迅速“回本”。

## 11.3 覆盖率

就其本质而言，测试永远是不完全的。正如有影响力的计算机科学家 Edsger Dijkstra 所言：“测试证明的是缺陷的存在，而非缺陷的不存在。” 任何数量的测试都无法证明一个包没有 bug。充其量，它们只能增加我们的信心，即该包在各种重要场景下都能良好工作。

测试套件对被测包的执行程度称为测试的*覆盖率*。覆盖率无法直接量化——除最简单的程序外，所有程序的动态行为都超出了精确测量的范围——但有一些启发式方法可以帮助我们将测试工作引导至更可能有用的地方。

*语句覆盖率* 是这些启发式方法中最简单、应用最广泛的一种。测试套件的语句覆盖率是指在测试期间至少被执行一次的源代码语句所占的比例。在本节中，我们将使用 Go 的 `cover` 工具（它集成在 `go test` 中）来度量语句覆盖率，并帮助识别测试中明显的空白。

下面的代码是一个表驱动测试，用于测试我们在第 7 章构建的表达式求值器：

[点击此处查看代码图像](#ch11_images.html#id318pro01_r)

`gopl.io/ch7/eval`

```
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

[点击此处查看代码图像](#ch11_images.html#id319pro01_r)

```
$ go test -v -run=Coverage gopl.io/ch7/eval
=== RUN TestCoverage
--- PASS: TestCoverage (0.00s)
PASS
ok      gopl.io/ch7/eval    0.011s
```

此命令显示覆盖率工具的用法信息：

[点击此处查看代码图像](#ch11_images.html#id319pro02_r)

```
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

[点击此处查看代码图像](#ch11_images.html#id319pro03_r)

```
$ go test -run=Coverage -coverprofile=c.out gopl.io/ch7/eval
ok      gopl.io/ch7/eval    0.032s  coverage: 68.5% of statements
```

此标志通过*插桩*生产代码来启用覆盖率数据的收集。也就是说，它修改源代码的副本，以便在执行每个语句块之前设置一个布尔变量，每个块对应一个变量。在修改后的程序退出前，它将每个变量的值写入指定的日志文件 `c.out`，并打印已执行语句所占比例的摘要。（如果你只需要摘要，请使用 `go test -cover`。）

如果使用 `-covermode=count` 标志运行 `go test`，每个块的插桩代码将递增一个计数器，而不是设置布尔值。生成的每个块执行计数日志允许对执行更频繁的“热点”块和执行较少的“冷点”块进行定量比较。

收集到数据后，我们运行 `cover` 工具，它处理日志，生成 HTML 报告，并在新浏览器窗口中打开它（图 11.3）。

```
$ go tool cover -html=c.out
```

![覆盖率报告。](graphics/coverage.png)

**图 11.3.** 覆盖率报告。

如果语句被覆盖则标记为绿色，未被覆盖则标记为红色。为清晰起见，我们给红色文本加上了背景阴影。我们可以立即看到，我们的输入中没有任何一个执行了一元运算符的 `Eval` 方法。如果我们将这个新测试用例添加到表中并重新运行前两个命令，一元表达式代码将变为绿色：

[点击此处查看代码图像](#ch11_images.html#id320pro01_r)

```
{"-x * -x", eval.Env{"x": 2}, "4"}
```

然而，那两条 `panic` 语句仍然是红色的。这不足为奇，因为这些语句本应是不可达的。

达到 100% 的语句覆盖率听起来是个崇高的目标，但在实践中通常不可行，也未必是精力的好归宿。仅仅因为一条语句被执行了，并不意味着它没有 bug；包含复杂表达式的语句必须用不同的输入执行多次才能覆盖有趣的情况。有些语句（如上述的 `panic` 语句）永远无法到达。其他语句（如处理晦涩错误的语句）难以触发，但在实践中很少被触及。测试从根本上说是一项务实的工作，是在编写测试的成本和本可通过测试预防的失败成本之间进行权衡。覆盖率工具有助于识别最薄弱的环节，但设计好的测试用例需要与编程一样严谨的思考。

## 11.4 `Benchmark` 函数

基准测试是指在固定工作负载下度量程序性能的实践。在 Go 中，基准测试函数看起来像测试函数，但带有 `Benchmark` 前缀和一个 `*testing.B` 参数，该参数提供了与 `*testing.T` 大部分相同的方法，外加一些与性能度量相关的额外方法。它还暴露了一个整数字段 `N`，指定执行被测操作的次数。

下面是一个 `IsPalindrome` 的基准测试，它在循环中调用该函数 `N` 次。

[点击此处查看代码图像](#ch11_images.html#id321pro01_r)

```
import "testing"

func BenchmarkIsPalindrome(b *testing.B) {
    for i := 0; i < b.N; i++ {
        IsPalindrome("A man, a plan, a canal: Panama")
    }
}
```

我们使用下面的命令运行它。与测试不同，默认情况下不运行任何基准测试。`-bench` 标志的参数选择要运行的基准测试。它是一个匹配 `Benchmark` 函数名称的正则表达式，其默认值不匹配任何函数。模式“`.`”会使其匹配 `word` 包中的所有基准测试，但由于只有一个，`-bench=IsPalindrome` 也是等效的。

[点击此处查看代码图像](#ch11_images.html#id321pro02_r)
