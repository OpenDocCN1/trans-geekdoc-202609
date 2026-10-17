
进入`/path/to/xxx`目录，找到`xxx.json`。

在表达式`cvar = avar + bvar`中，加法运算符（`+`）将`avar`与`bvar`相加，得到它们的和`cvar`

在`List.of(arg0, arg1, arg2)`中，`List`接口的工厂方法`of()`接受一系列的元素，返回包含它们的只读列表。

之后我们这样调用`cmd`命令：`cmd arg0 arg1 arg2`。

```
if (condVar > someVal) {console.log("xxx")}
```

在 `goroutine` 中启动昂贵的计算后（但由于它们的通道是非缓冲的），我们已经准备好接收它们的结果。`for` 循环每次迭代都从新的结果值开始，阻塞的 `select` 语句从那些准备好执行的语句中随机执行一个 `case`。一旦 `answer` 准备就绪，就会设置 `which` 并在循环结束前打印结果。一旦 `done` 通道关闭，我们就知道所有昂贵的计算已完成。

# 第 5 章 过程化编程

当调用内置的 `panic()` 函数时，闭包函数或方法的正常执行会立即停止。然后，任何延迟（deferred）的函数或方法都会被调用——就像该函数正常返回时一样。

最后，控制权将返回给调用者——就像该函数或方法执行了 `panic()` 一样，因此该过程会在调用者中重复发生：执行停止，调用延迟函数，依此类推。当到达 `main()` 函数时，没有调用者可以返回，因此此时程序将终止，并向 `os.Stderr` 导出堆栈跟踪，其中包含了传递原始 `panic()` 的值。

如果发生了 `panic`，上述过程通常会发生。但是，如果其中一个延迟函数或方法调用了内置的 `recover()` 函数（该函数可能只能在延迟函数或方法内部调用），`panic` 就会被中断。此时，我们可以根据需要从 `panic` 中恢复。一种解决方案是忽略 `panic`，在这种情况下，控制权将传递给带有延迟 `recover()` 调函数调用者，该函数将继续正常执行。这种方法不推荐，但如果使用，至少应该记录 `panic`，以便问题不会被完全隐藏。另一种解决方案是进行此类清理工作，然后我们自己调用 `panic()` 以继续传播问题。更常见的解决方案是将错误设置为带有延迟 `recover()` 调用的函数（之一的）返回值，从而将异常（即 `panic`）转换为错误（即 `error`）。

在任何情况下，Go 标准库都使用错误值而不是 `panic`。对于我们自己的自定义包，最好不要使用 `panic()`；或者说，不让 `panic` 泄露的最好方法是让自定义包通过 `recover()` 捕获 `panic` 并返回错误，就像标准库所做的那样。

一个说明性的例子是 Go 的基础正则表达式包 `regexp`。它有许多用于创建表达式的函数，使用 `regexp.Compile()` 和 `regexp.MustCompile()`。其中第一个返回一个编译后的正则表达式和 `nil`，或者如果传递给它的字符串不是有效的正则表达式，则返回 `nil` 和一个 `error`。第二个返回一个编译后的正则表达式，或者当表达式来自外部源（例如，由用户输入或来自文件）时发生 `panic`。当正则表达式在程序中硬编码时，第二个函数是最好的，因为它确保了当我们运行程序时，如果我们在正则表达式上犯了错误，程序将立即因 `panic` 而终止。

我们何时应该允许 `panic` 终止我们的程序，又何时应该用 `recover()` 停止它们？我们必须考虑两个相互竞争的利益。作为程序员，我们希望程序在出现逻辑错误时尽快崩溃，以便我们能够识别并修复问题。但一旦程序已经部署，我们就不希望程序发生崩溃。

对于只需通过运行程序就能捕获的问题（例如，无效的正则表达式），我们应该使用 `panic()`（或像 `regexp.MustCompile()` 这样会 `panic` 的函数），因为我们永远不会部署一个一运行就崩溃的应用。我们必须小心，只在确定会通过简单运行程序被调用的函数中这样做——例如，主包的 `init()` 函数（如果有的话）、主包的 `main()` 函数，以及我们程序导入的自定义包中的任何 `init()` 函数——此外，当然还包括这些函数调用的任何函数或方法。自然地，我们还必须确保无论程序的控制流如何，潜在的 `panic` 情况始终能被触发。

对于在任何特定运行期间可能调用也可能不调用的函数和方法，如果我们自己调用了 `panic()` 或者我们调用了会 `panic` 的函数或方法，我们应该使用 `recover()`，并将 `panic` 转换为错误。理想情况下，`recover()` 应该尽可能靠近它们所处理的 `panic`，并在可能且适当的情况下，在它们的闭包函数或方法返回之前将程序恢复到安全状态。对于主包的 `main()` 函数，我们可以放置一个顶层的“全捕获” `recover()` 来记录捕获到的 `panic`——但遗憾的是，在处理完延迟 `recover()` 后程序仍然会终止。这可以通过某种方法解决，正如我们很快将看到的。

我们将查看两个例子，第一个演示如何将 `panic` 转换为错误，第二个展示了如何让程序更健壮。

假设在我们使用的某个包深处有这样一个函数，但由于它是第三方提供的，我们无法控制，因此无法更改它。

```go
func Convert64ToInt(x int64) int {
	if math.MinInt32 <= x && x <= math.MaxInt32 {
		return int(x)
	}
	panic(fmt.Sprintf("%d is out of the int32 range", x))
}
```

此函数安全地将 `int64` 转换为 `int`，如果转换会产生无效结果，则触发 `panic`。

为什么这样的函数最初会 `panic()` 呢？我们可能希望在出现问题时立即强制崩溃，以便尽早避免编程错误。另一种情况是，我们有一个函数调用一个或多个其他函数，但一旦发生任何错误，我们希望立即将控制权返回给原始函数——因此让被调用的函数在遇到问题时 `panic`，并使用 `recover()` 捕获（来自何处的）`panic`。通常情况下，我们希望包作为错误报告问题而不是 `panic`，因此在包内部使用 `panic()` 和错误是相当常见的。另一个用途是使用 `recover()` 确保 `panic` 不泄露并作为错误报告。另一个用例是在我们的逻辑无法到达的地方放置如 `panic("unreachable")` 的调用（例如，在始终通过 `return` 语句返回的函数末尾），或者在预设条件被破坏时调用 `panic()`。这确保了如果我们破坏了此类函数的逻辑，我们很快就会得知。

如果以上理由都不适用，那么当问题发生时，我们应当做出决定并返回一个错误。因此，在这个例子中，我们希望转换成功时返回 `int` 和 `nil`，在转换失败时返回一个 `error`。这里有一个实现我们目标的包装函数：

```go
func Int64(x int64) (i int, err error) {
	defer func() {
		if e := recover(); e != nil {
			err = fmt.Errorf("%v", e)
		}
	}()
	i = Convert64ToInt(x)
	return i, nil
}
```

当调用此函数时，像往常一样，Go 会将返回值设置为其类型的零值，在本例中是 `nil` 和 `nil`。如果我们调用的自定义 `Convert64ToInt()` 函数正常返回，我们将结果赋值给返回值 `i`，并连同 `nil` 返回，表示没有发生错误。如果 `Convert64ToInt()` 触发了 `panic`，我们在延迟匿名函数中捕获 `panic`，并将 `err` 设置为错误，其文本设置为它捕获的 `panic` 的文本表示。

如 `Int64()` 函数所示，将 `panic` 转换为错误是直接的。

在第二个例子中，我们将考虑如何让 Web 服务器在面对 `panic` 时保持健壮。在第 2 章中，我们回顾了统计示例（$2.4, 72）。如果在该服务器中编写了程序错误——例如，不小心传递了 `nil` 作为 `image.Image` 值并对其调用方法——我们会得到一个 `panic`，如果没有调用 `recover()` 就会终止程序。如果该网站很重要，这显然是一个非常不理想的情况，特别是当我们希望无人运行一段时间时。我们想要的是服务器继续运行并记录任何 `panic`，以便我们能够追踪并修复它们。

我们创建了统计示例的修改版本（实际上是 `st_ans` 解决方案），文件位于 `statistics_nonstop/statistics.go`。我们所做的一个修改是在网页上添加了一个名为 "Panic!" 的额外按钮，它可以被点击以出于测试目的触发 panic。最重要的修改是，我们已经让服务器能够在发生 panic 后存活。为了帮助我们观察发生了什么，我们还在客户端被成功服务、我们收到错误请求以及服务器被重启时记录了日志。这里是一个典型日志的微型示例。

```
[127.0.0.1:41373] served OK
[127.0.0.1:41373] served OK
[127.0.0.1:41373] bad request: 'gy' is invalid
[127.0.0.1:41373] served OK
[127.0.0.1:41373] caught panic: user clicked panic button!
[127.0.0.1:41373] served OK
```

我们告诉 log 包不要使用时间戳仅仅是为了让输出在书中看起来更美观。

在查看我们所做的更改之前，我们将简要回顾一下原始代码。

```go
func main() {
	http.HandleFunc("/", homePage)
	if err := http.ListenAndServeAndServe(":9001", nil); err != nil {
		log.Fatal("failed to start server", err)
	}
}

func homePage(writer http.ResponseWriter, request *http.Request) {
	// ...
}
```

这个网站只有一个页面，尽管我们将要介绍的技术可以很容易应用到多个页面。如果发生了没有被 `recover()` 捕获的 `panic`，也就是说如果 `panic` 到达了 `main()` 函数，服务器将会终止；这正是我们必须防止的。

```go
func homePage(writer http.ResponseWriter, request *http.Request) {
	defer func() {
		if x := recover(); x != nil {
			log.Printf("%s caught panic: %v", request.RemoteAddr, x)
		}
	}()
	// ...
}
```

为了让 Web 服务器在面对 `panic` 时具有健壮性，我们必须确保每个页面处理器都有一有一个调用 `recover()` 的延迟函数。这将阻止任何 `panic` 的传播（因为 `defer` 语句在函数返回之前执行）。当然，对于一个拥有许多处理器的大型网站，添加一个用于捕获和记录 `panic` 的延迟函数涉及大量的重复，并且很容易忘记。这可以通过一个包含每个页面处理器所需的代码的包装函数来解决。只要我们更改了 `http.HandleFunc()` 的调用，我们就可以从页面处理器中省略 `recover` 代码：

```go
http.HandleFunc("/", logPanics(homePage))

func logPanics(function func(http.ResponseWriter, request *http.Request)) func(http.ResponseWriter, request *http.Request) {
	return func(writer http.ResponseWriter, request *http.Request) {
		defer func() {
			if x := recover(); x != nil {
				log.Printf("%s caught panic: %v", request.RemoteAddr, x)
			}
		}()
		function(writer, request)
	}
}
```

## 5.5. Defer、Panic 和 Recover

## 5.6. 自函数

函数是过程化编程的基石，Go 为它们提供了一类支持。Go 方法（第 6 章介绍）与 Go 函数非常相似，因此本节对于过程化和面向对象的编程都相关。以下是函数定义的基础语法：

```go
func name(optionalParameters) optionalReturnType {}
func name(optionalParameters) (optionalReturnValues) {}
```

函数可以接受零个或多个参数。如果没有参数，括号留空。如果有一个或多个参数，则写成 `params1 type, ..., paramsN type`，其中 `params1` 是单个参数名，或者是给定类型的两个或多个参数名的逗号分隔列表。参数必须按顺序传递：没有等同于 Python 命名参数的内容，尽管正如我们稍后看到的，可以实现类似的效果。

最后一个参数的类型之前可以跟一个省略号 `...`。此类函数被称为变长函数（variadic functions）；这意味着函数将接受零个或多个该类型的值作为该参数的值，在函数内部该参数的类型将是 `[]type`。

函数可以返回零个或多个值。如果没有值，可以写成 `type`。如果有两个或多个返回值，则必须使用括号，并写成 `(type1, ..., typeN)`。如果有一个或多个命名返回值，则必须使用括号，并写成 `(values1 type1, ..., valuesN typeN)`，其中 `values1` 是单个返回名，或者是给定类型的两个或多个返回名的逗号分隔列表。函数的返回值可以是全部无命名的，也可以是全部命名的，但不能混用。

具有一个或多个返回值的函数必须至少有一个 `return` 语句——或者一个 `panic()` 调用作为它们的最后语句。如果返回值是没有命名的，`return` 语句指定的数值必须与返回值数量相同，每个值的类型必须与对应的返回值匹配。如果返回值是有命名的，`return` 语句既可以像无命名情况那样指定值，也可以直接裸写（即不提供显式的返回值）。请注意，虽然裸返回（bare returns）是合法的，但它们被认为是糟糕的——书中没有任何示例会使用它们。

如果一个函数有一个或多个返回值，它的最后一个可执行语句必须是 `return` 或 `panic()`。Go 编译器足够智能，能够意识到以 `panic` 结尾的函数不会正常返回，因此在该处不需要 `return` 语句。遗憾的是，目前的 Go 编译器并不理解一个带有无条件 `else` 语句的 `if` 语句以 `return` 语句结尾，或者一个 `switch` 语句具有一个以 `return` 语句结尾的 `default` case，因此在之后不再需要额外的 `return`。在这些情况下，常见的做法是不以 `else` 或 `default` case 结尾，而是将 `return` 语句放在 `if` 或 `switch` 之后，或者干脆...

## 5.6. 自定义函数

| Δ1 == | 6.000000 == Δ2 == | 6.000000 |
| Δ1 == | 30.000000 == Δ2 == | 30.000000 |
| Δ1 == | 84.000000 == Δ2 == | 84.000000 |
| Δ1 == | 180.000000 == Δ2 == | 180.000000 |

首先，我们使用欧几里得勾股定理公式获取长度，然后使用恰好三个参数的 `Heron()` 函数应用海伦公式。我们重复了计算，只是这次直接将 `PythagoreanTriple()` 函数作为 `Heron()` 函数的参数，让 Go 将 `PythagoreanTriple()` 的三个返回值拷贝到 `Heron()` 函数的三个参数中。

```go
func Heron(a, b, c int) float64 {
	α, β, γ := float64(a), float64(b), float64(c)
	s := (α + β + γ) / 2
	return math.Sqrt(s * (s - α) * (s - β) * (s - γ))
}

func PythagoreanTriple(m, n int) (a, b, c int) {
	if m < n {
		m, n = n, m
	}
	return (m * m) - (n * n), (2 * m * n), (m * m) + (n * n)
}
```

为了完整起见，展示了 `Heron()` 和 `PythagoreanTriple()` 函数。我们为 `PythagoreanTriple()` 函数使用命名返回值完全是为了作为函数文档的补充。

### 5.6.1.2. 变长函数

变长函数是指其最后一个（或唯一）参数可以接受零或多个参数的函数。这种参数通过在最后一个或唯一参数的类型之前添加省略号（`...`）来指示。在函数内部，该参数变为给定类型的切片。例如，如果我们有一个签名为 `Join(xs ...string) string` 的函数，那么 `xs` 参数的类型将是 `[]string`。

这里有一个变长函数用法的小示例；在这种情况下，它返回传递的整数中的最小值。我们将开始查看它是如何调用的以及产生的输出。

```go
fmt.Println(MinimumInt1(5, 3), MinimumInt1(7, 3, -2, 4, 0, -8, -5))
3-8
```

# 第 5 章 过程化编程

`MinimumIntl()` 函数可以传递一个或多个 `int` 并返回其中最小的一个。

```go
func MinimumIntl(first int, rest ...int) int {
	for _, x := range rest {
		if x < first {
			first = x
		}
	}
	return first
}
```
