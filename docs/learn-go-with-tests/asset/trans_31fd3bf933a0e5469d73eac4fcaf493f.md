

所以，我们知道在底层，我们最终是使用 `Writer` 将问候语发送到某个地方。让我们利用这个现有的抽象，让我们的代码可测试且更具复用性。

## 先编写测试

```go
func TestGreet(t *testing.T) {
    buffer := bytes.Buffer{}
    Greet(&buffer, "Chris")

    got := buffer.String()
    want := "Hello, Chris"

    if got != want {
        t.Errorf("got %q want %q", got, want)
    }
}
```

`bytes` 包中的 `Buffer` 类型实现了 `Writer` 接口，因为它有方法 `Write(p []byte) (n int, err error)`。

所以，我们会在测试中使用它作为我们的 `Writer` 传入，然后在我们调用 `Greet` 之后，可以检查它被写入了什么内容。

## 尝试运行测试

测试将无法编译

```
./di_test.go:10:7: too many arguments in call to Greet
    have (*bytes.Buffer, string)
    want (string)
```

## 编写最少量的代码让测试运行，并检查失败输出

## 测试输出

*听从编译器的建议，修复问题。*

```go
func Greet(writer *bytes.Buffer, name string) {
    fmt.Printf("Hello, %s", name)
}
```

Hello, Chris di_test.go:16: got '' want 'Hello, Chris'

测试失败了。注意，名字被打印出来了，但它输出到了标准输出（stdout）。

## 编写足够的代码使其通过

使用 writer 将问候语发送到我们测试中的 buffer 中。记住，`fmt.Fprintf` 类似于 `fmt.Printf`，但它需要一个 `Writer` 来发送字符串，而 `fmt.Printf` 默认输出到 stdout。

```go
func Greet(writer *bytes.Buffer, name string) {
    fmt.Fprintf(writer, "Hello, %s", name)
}
```

现在测试通过了。

## 重构

之前编译器告诉我们传入一个指向 `bytes.Buffer` 的指针。这在技术上是正确的，但并不是很有用。

为了说明这一点，尝试将 `Greet` 函数接入到一个我们希望它打印到 stdout 的 Go 应用中。

```go
func main() {
    Greet(os.Stdout, "Elodie")
}
```

./di.go:14:7: cannot use os.Stdout (type *os.File) as type *bytes.Buffer in argument to Greet

如前所述，`fmt.Printf` 允许你传入一个 `io.Writer`，我们知道 `os.Stdout` 和 `bytes.Buffer` 都实现了它。

如果我们将代码改为使用更通用的接口，我们现在就可以在测试和应用程序中使用它了。

```go
package main

import (
    "fmt"
    "io"
    "os"
)

func Greet(writer io.Writer, name string) {
    fmt.Fprintf(writer, "Hello, %s", name)
}

func main() {
    Greet(os.Stdout, "Elodie")
}
```

## 更多关于 `io.Writer` 的内容

还有哪些其他地方我们可以使用 `io.Writer` 写入数据？我们的 `Greet` 函数到底有多通用？

## 互联网

运行以下代码

```go
package main

import (
    "fmt"
    "io"
    "log"
    "net/http"
)

func Greet(writer io.Writer, name string) {
    fmt.Fprintf(writer, "Hello, %s", name)
}

func MyGreeterHandler(w http.ResponseWriter, r *http.Request) {
    Greet(w, "world")
}

func main() {
    log.Fatal(http.ListenAndServe(":5000", http.HandlerFunc(MyGr
}
```

运行程序并访问 [http://localhost:5000](http://localhost:5000)。你会看到你的问候函数被使用。

HTTP 服务器将在后面的章节中介绍，所以不必过于担心细节。

当你编写 HTTP 处理器时，你会得到一个 `http.ResponseWriter` 和用于发起请求的 `http.Request`。当你实现服务器时，你使用该 writer 来*写入*你的响应。

你大概能猜到 `http.ResponseWriter` 也实现了 `io.Writer`，所以这就是为什么我们可以在处理器中复用我们的 `Greet` 函数。

## 总结

我们的第一轮代码不容易测试，因为它将数据写到了一个我们无法控制的地方。

*在测试的驱动下*，我们重构了代码，以便我们可以控制数据写入的*位置*，通过**注入依赖**，这使我们能够：

- **测试我们的代码** 如果你不能*轻松地*测试一个函数，通常是因为函数中硬编码了依赖*或*全局状态。例如，如果你有一个被某种服务层使用的全局数据库连接池，那么测试很可能很困难，而且运行缓慢。依赖注入会促使你注入一个数据库依赖（通过接口），然后你可以用测试中可控的东西来模拟它。
- **分离关注点**，解耦*数据去向*与*数据生成方式*。如果你觉得一个方法/函数承担了太多职责（生成数据*并且*写入数据库？处理 HTTP 请求*并且*执行领域逻辑？），依赖注入可能就是你需要的工具。
- **让我们的代码可以在不同上下文中复用** 我们的代码可以使用的第一个“新”上下文是在测试中。但更进一步，如果有人想用你的函数尝试一些新东西，他们可以注入自己的依赖。

## 那 mock 呢？我听说做 DI 需要它，而且它很邪恶

Mock 将在后面详细讨论（而且它并不邪恶）。你使用 mock 来替换你注入的真实事物，用一个你可以在测试中控制和检查的伪装版本。但在我们的例子中，标准库已经有一些现成的东西供我们使用。

## Go 标准库真的很棒，花时间研究它

通过对 `io.Writer` 接口有一定熟悉度，我们可以在测试中使用 `bytes.Buffer` 作为我们的 `Writer`，然后我们可以使用标准库中的其他 `Writer`，让我们的函数在命令行应用或 Web 服务器中使用。

你对标准库越熟悉，就越会看到这些通用接口，然后你可以在自己的代码中复用它，让你的软件在多种场景中可复用。

这个例子深受《The Go Programming language》一书中某一章的影响，如果你喜欢这个例子，去买这本书吧！

## Mocking

你可以在本章找到所有代码

你被要求编写一个程序，从 3 开始倒计时，每行打印一个数字（间隔 1 秒），当它到达零时打印“Go!”并退出。

```
3
2
1
Go!
```

我们将通过编写一个名为 `Countdown` 的函数来解决这个问题，然后将其放入一个 `main` 程序中，如下所示：

```
package main

func main() {
    Countdown()
}
```

虽然这是一个相当简单的程序，但要完整地测试它，我们仍然需要像往常一样采用*迭代式、测试驱动*的方法。

我说的迭代是什么意思？我们确保尽量采取最小的步骤来获得*有用的软件*。

我们不想在理论上经过一番修修补补后就能工作的代码上花费很长时间，因为那往往是开发者陷入兔子洞的方式。**能够将需求切分得尽可能小，从而拥有可工作的软件，是一项重要的技能。**

以下是我们如何划分工作并逐步迭代：

- 打印 3
- 打印 3、2、1 和 Go!
- 每一行之间等待一秒钟

## 先编写测试

我们的软件需要打印到 stdout，我们在 DI 部分已经看到了如何使用 DI 来促进这类测试。

```go
func TestCountdown(t *testing.T) {
    buffer := &bytes.Buffer{}

    Countdown(buffer)

    got := buffer.String()
    want := "3"

    if got != want {
        t.Errorf("got %q want %q", got, want)
    }
}
```

如果你对像 `buffer` 这样的东西不熟悉，请重新阅读[前一节](the_previous_section)。

我们知道我们希望 `Countdown` 函数将数据写入某个地方，而 `io.Writer` 是在 Go 中将其捕获为接口的事实标准方式。

- 在 `main` 中，我们会发送到 `os.Stdout`，这样用户就能在终端看到倒计时打印。
- 在测试中，我们会发送到 `bytes.Buffer`，这样我们的测试就可以捕获生成的数据。

## 尝试运行测试

```
./countdown_test.go:11:2: undefined: Countdown
```

## 编写最少量的代码让测试运行，并检查失败的测试输出

定义 `Countdown`

```go
func Countdown() {}
```

再试一次

./countdown_test.go:11:11: too many arguments in call to Countdown
have (*bytes.Buffer)
want ()

编译器在告诉你函数签名应该是什么样的，所以更新它。

```go
func Countdown(out *bytes.Buffer) {}
```

countdown_test.go:17: got '' want '3'

完美！

## 编写足够的代码使其通过

```go
func Countdown(out *bytes.Buffer) {
    fmt.Fprint(out, "3")
}
```

我们使用 `fmt.Fprint`，它接受一个 `io.Writer`（如 `*bytes.Buffer`）并向其发送一个字符串。测试应该通过。

## 重构

