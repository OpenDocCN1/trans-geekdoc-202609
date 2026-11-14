
如果在延迟函数中调用内置的 `recover` 函数，且包含 `defer` 语句的函数正在发生恐慌，`recover` 会结束当前的恐慌状态并返回恐慌值。发生恐慌的函数不会从中断处继续执行，而是正常返回。如果在其他任何时候调用 `recover`，它没有任何效果并返回 `nil`。

为了说明这一点，考虑一个语言解析器的开发。即使它看起来工作良好，考虑到其工作的复杂性，晦涩的边缘情况中仍可能潜伏着 Bug。我们可能更希望解析器将这些恐慌转化为普通的解析错误，而不是崩溃，或许还会附带一条额外的消息，敦促用户提交 Bug 报告。

[点击此处查看代码图像](#part0135_split_075.html#id152pro01_r)

```
func Parse(input string) (s *Syntax, err error) {
    defer func() {
        if p := recover(); p != nil {
            err = fmt.Errorf("internal error: %v", p)
        }
    }()
    // ...parser...
}
```

`Parse` 中的延迟函数从恐慌中恢复，利用恐慌值构造错误消息；更复杂的版本可能会使用 `runtime.Stack` 包含完整的调用栈。然后延迟函数将错误赋值给 `err` 结果，并将其返回给调用者。

盲目地从恐慌中恢复是一种可疑的做法，因为恐慌后包变量的状态很少有明确的定义或文档说明。也许关键的数据结构更新未完成，文件或网络连接已打开但未关闭，或者锁已获取但未释放。此外，通过将崩溃替换为（例如）日志文件中的一行，盲目恢复可能导致 Bug 被忽视。

在同一个包内从恐慌中恢复有助于简化复杂或意外错误的处理，但作为一般规则，你不应尝试从另一个包的恐慌中恢复。公共 API 应将失败报告为 `error`。同样，你也不应从可能穿过你不维护的函数（如调用者提供的回调）的恐慌中恢复，因为你无法推断其安全性。

例如，`net/http` 包提供了一个 Web 服务器，将传入的请求分派给用户提供的处理器函数。服务器不会让这些处理器中的恐慌杀死进程，而是调用 `recover`，打印堆栈跟踪，并继续服务。这在实践中很方便，但确实存在泄漏资源或使失败的处理器处于未指定状态的风险，这可能导致其他问题。

基于上述所有原因，最安全的做法是有选择地恢复，如果有的话。换句话说，只从预期要恢复的恐慌中恢复，这应该很少见。这种意图可以通过为恐慌值使用一个独特的、未导出的类型来编码，并测试 `recover` 返回的值是否具有该类型。（我们将在下一个示例中看到一种方法。）如果是，我们将恐慌作为普通的 `error` 报告；如果不是，我们用相同的值调用 `panic` 以恢复恐慌状态。

下面的示例是 `title` 程序的一个变体，如果 HTML 文档包含多个 `<title>` 元素则报告错误。如果是这样，它通过使用特殊类型 `bailout` 的值调用 `panic` 来中止递归。

[点击此处查看代码图像](#part0135_split_076.html#id153pro01_r)

gopl.io/ch5/title3

```
// soleTitle 返回 doc 中第一个非空 title 元素的文本，
// 如果没有恰好一个则返回错误。
func soleTitle(doc *html.Node) (title string, err error) {
    type bailout struct{}

    defer func() {
        switch p := recover(); p {
        case nil:
            // 无恐慌
        case bailout{}:
            // "预期" 的恐慌
            err = fmt.Errorf("multiple title elements")
        default:
            panic(p) // 意外恐慌；继续恐慌
        }
    }()

    // 如果找到多个非空标题，则中止递归。
    forEachNode(doc, func(n *html.Node) {
        if n.Type == html.ElementNode && n.Data == "title" &&
            n.FirstChild != nil {
            if title != "" {
                panic(bailout{}) // 多个标题元素
            }
            title = n.FirstChild.Data
        }
    }, nil)
    if title == "" {
        return "", fmt.Errorf("no title element")
    }
    return title, nil
}
```

延迟处理函数调用 `recover`，检查恐慌值，如果值为 `bailout{}` 则报告普通错误。所有其他非 nil 值表示意外恐慌，在这种情况下处理函数用该值调用 `panic`，撤销 `recover` 的效果并恢复原始的恐慌状态。（此示例在一定程度上违反了我们关于不将恐慌用于“预期”错误的建议，但它紧凑地说明了机制。）

某些情况下无法恢复。例如，内存耗尽会导致 Go 运行时以致命错误终止程序。

**练习 5.19：** 使用 `panic` 和 `recover` 编写一个不包含 `return` 语句却返回非零值的函数。

# 6. 方法

自 1990 年代初以来，面向对象编程（OOP）一直是工业界和教育界的主导编程范式，此后开发的几乎所有广泛使用的语言都包含对它的支持。Go 也不例外。

虽然没有普遍接受的面向对象编程定义，但就我们的目的而言，*对象* 就是一个拥有方法的值或变量，*方法* 是与特定类型关联的函数。面向对象程序是使用方法来表达每个数据结构的属性和操作的程序，这样客户端就不需要直接访问对象的表示。

在前几章中，我们经常使用标准库中的方法，比如 `time.Duration` 类型的 `Seconds` 方法：

[点击此处查看代码图像](#part0136_split_000.html#id155pro01_r)

```
const day = 24 * time.Hour
fmt.Println(day.Seconds()) // "86400"
```

我们在 [2.5 节](#part0025.html#id-typedeclarations) 中定义了自己的一个方法，即 `Celsius` 类型的 `String` 方法：

[点击此处查看代码图像](#part0136_split_001.html#id155pro02_r)

```
func (c Celsius) String() string { return fmt.Sprintf("%g°C", c) }
```

在本章中，作为面向对象编程两章中的第一章，我们将展示如何有效地定义和使用方法。我们还将介绍面向对象编程的两个关键原则：*封装* 和 *组合*。

## 6.1 方法声明

方法的声明是在普通函数声明的变体中，在函数名前出现一个额外的参数。该参数将函数附加到该参数的类型上。

让我们在一个简单的平面几何包中编写第一个方法：

[点击此处查看代码图像](#part0136_split_002.html#id156pro01_r)

gopl.io/ch6/geometry

```
package geometry

import "math"

type Point struct{ X, Y float64 }

// 传统函数
func Distance(p, q Point) float64 {
    return math.Hypot(q.X-p.X, q.Y-p.Y)
}

// 同样的功能，但作为 Point 类型的方法
func (p Point) Distance(q Point) float64 {
    return math.Hypot(q.X-p.X, q.Y-p.Y)
}
```

额外的参数 `p` 称为方法的 *接收器*，这是早期面向对象语言的遗产，它们将调用方法描述为“向对象发送消息”。

在 Go 中，我们不使用像 `this` 或 `self` 这样的特殊名称作为接收器；我们选择接收器名称就像选择其他参数一样。由于接收器名称将被频繁使用，最好选择简短且在各方法间保持一致的名称。常见的选择是类型名称的首字母，如 `Point` 的 `p`。
