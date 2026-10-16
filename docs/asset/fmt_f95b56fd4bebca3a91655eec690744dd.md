
```go
t.Errorf("got %q, want %q", got, want)

}

}

func makeDelayedServer(delay time.Duration) *httptest.Server {

    return httptest.NewServer(http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {

        time.Sleep(delay)

        w.WriteHeader(http.StatusOK)

    }))

}

```

我们将创建假服务器的逻辑重构到一个名为 `makeDelayedServer` 的函数中，以将一些不感兴趣的代码移出测试并减少重复。

## defer

通过在函数调用前加上 `defer`，它现在会在 *包含函数的末尾* 调用该函数。

有时你需要清理资源，例如关闭文件，或者在我们的例子中关闭服务器以使其不再监听端口。

你希望它在函数结束时执行，但为了方便未来的代码阅读者，请将指令保留在创建服务器附近。

我们的重构是一个改进，并且在目前涵盖的 Go 特性范围内是一个合理的解决方案，但我们可以使解决方案更简单。

## Synchronising processes

- 为什么我们在 Go 擅长并发的情况下要一个接一个地测试网站速度？我们应该能够同时检查两者。
- 我们并不真正关心请求的 *确切响应时间*，我们只想知道哪个先返回。

为此，我们将引入一个新的构造 `select`，它能非常轻松清晰地帮助我们同步进程。

```go
func Racer(a, b string) (winner string) {

    select {

    case <-ping(a):

        return a

    case <-ping(b):

        return b

    }

}

```

```go
func ping(url string) chan struct{} {

    ch := make(chan struct{})

    go func() {

        http.Get(url)

        close(ch)

    }()

    return ch

}

```

## ping

我们定义了一个 `ping` 函数，它创建一个 `chan struct{}` 并返回它。

在我们的例子中，我们不 *关心* 发送到通道的类型是什么，*我们只想发出已完成的信号*，关闭通道就完美地实现了这一点！

为什么使用 `struct{}` 而不是像 `bool` 这样的其他类型？嗯，从内存角度来看，`chan struct{}` 是可用的最小数据类型，因此与 `bool` 相比我们没有分配。既然我们关闭通道而不是在上面发送任何内容，为什么要分配任何东西呢？

在同一个函数内部，我们启动一个 goroutine，该 goroutine 在完成 `http.Get(url)` 后会向该通道发送信号。

## Always `make` channels

注意我们必须使用 `make` 来创建通道；而不是写成 `var ch chan struct{}`。当你使用 `var` 时，变量会被初始化为该类型的“零值”。例如 `string` 是 ""，`int` 是 0，等等。

对于通道，零值是 `nil`，如果你尝试用 `<-` 向其发送数据，它会永远阻塞，因为你无法向 `nil` 通道发送数据

你可以在 The Go Playground 中看到这种行为

## select

如果你还记得并发章节，可以使用 `myVar := <-ch` 来等待通道发送值。这是一个 *阻塞* 调用，因为你在等待值。

`select` 让你可以等待 *多个* 通道。第一个发送值的通道“获胜”，并且 `case` 下面的代码会被执行。

我们在 `select` 中使用 `ping` 为我们的两个 `URL` 设置两个通道。哪个通道先写入其通道，其代码就会在 `select` 中执行，这会导致其 `URL` 被返回（并成为赢家）。

经过这些更改后，我们代码背后的意图非常清晰，而且实现实际上更简单。

## Timeouts

我们的最后一个需求是：如果 Racer 耗时超过 10 秒，就返回一个错误。

## 首先编写测试

```go
t.Run("returns an error if a server doesn't respond within 10s", func(t *testing.T) {

    serverA := makeDelayedServer(11 * time.Second)

    serverB := makeDelayedServer(12 * time.Second)

    defer serverA.Close()

    defer serverB.Close()

    _, err := Racer(serverA.URL, serverB.URL)

    if err == nil {

        t.Error("expected an error but didn't get one")

    }

})

```

我们已经让测试服务器延迟超过 10 秒才返回，以便触发这一场景。现在我们预期 Racer 会返回两个值：获胜的 URL（本测试中用 `_` 忽略）和一个错误。

## 尝试运行测试

```text
./racer_test.go:37:10: assignment mismatch: 2 variables but 1 value

```

## 编写最少量的代码让测试运行，并检查失败的测试输出

```go
func Racer(a, b string) (winner string, error error) {

    select {

    case <-ping(a):

        return a, nil

    case <-ping(b):

        return b, nil

    }

}

```

修改 `Racer` 的函数签名，使其返回获胜者和一个错误。在我们的正常场景中返回 `nil`。

编译器会抱怨你的第一个测试只接收一个值，所以请将该行改为 `got, _ := Racer(slowURL, fastURL)`，同时要知道我们应当在正常场景中确认不会得到错误。

如果你现在运行它，11 秒后就会失败。

```text
--- FAIL: TestRacer (12.00s)

    --- FAIL: TestRacer/returns_an_error_if_a_server_doesn't_respond_within_10s (12.00s)

        racer_test.go:40: expected an error but didn't get one

```

## 编写足够的代码使其通过

```go
func Racer(a, b string) (winner string, error error) {

    select {

    case <-ping(a):

        return a, nil

    case <-ping(b):

        return b, nil

    case <-time.After(10 * time.Second):

        return "", fmt.Errorf("timed out waiting for %s and %s", a, b)

    }

}

```

`time.After` 是一个在使用 `select` 时非常方便的函数。虽然在我们的例子中没有发生，但如果你监听的 channel 永远没有返回值，你可能会写出永远阻塞的代码。`time.After` 返回一个 `chan`（类似于 `ping`），并在你指定的时间后向其中发送一个信号。

对我们来说这非常理想：如果 `a` 或 `b` 成功返回，则它们胜出；但如果到了 10 秒，`time.After` 就会发送信号，我们便返回一个错误。

## 慢速测试

我们面临的问题是，这个测试需要 10 秒才能运行完。对于如此简单的一点逻辑来说，这感觉不太好。

我们可以让超时时间可配置。这样在测试中可以使用很短的超时时间，而在真实环境中使用时则可以设置为 10 秒。

```go
func Racer(a, b string, timeout time.Duration) (winner string, error error) {

    select {

    case <-ping(a):

        return a, nil

    case <-ping(b):

        return b, nil

    case <-time.After(timeout):

        return "", fmt.Errorf("timed out waiting for %s and %s", a, b)

    }

}

```

由于没有提供超时时间，我们的测试现在无法编译。

在急于将默认值添加到两个测试之前，先听一听它们（的需求）。

- 在“正常”测试中，我们在意超时吗？
- 需求对超时时间有明确的说明。

基于这些认识，我们来稍微重构一下，以便同时照顾到我们的测试和代码的使用者。

```go
var tenSecondTimeout = 10 * time.Second

func Racer(a, b string) (winner string, error error) {

    return ConfigurableRacer(a, b, tenSecondTimeout)

}

```

```go
func ConfigurableRacer(a, b string, timeout time.Duration) (winner string, error error) {

    select {

    case <-ping(a):

        return a, nil

    case <-ping(b):

        return b, nil

    case <-time.After(timeout):

        return "", fmt.Errorf("timed out waiting for %s and %s", a, b)

    }

}

```

我们的使用者和第一个测试可以使用 `Racer`（它在底层使用 `ConfigurableRacer`），而我们的异常路径测试可以使用 `ConfigurableRacer`。

```go
func TestRacer(t *testing.T) {

    t.Run("compares speeds of servers, returning the url of the faster one", func(t *testing.T) {

        slowServer := makeDelayedServer(20 * time.Millisecond)

        fastServer := makeDelayedServer(0 * time.Millisecond)

        defer slowServer.Close()

        defer fastServer.Close()

        slowURL := slowServer.URL

        fastURL := fastServer.URL

        want := fastURL

        got, err := Racer(slowURL, fastURL)

        if err != nil {

            t.Fatalf("did not expect an error but got one %v", err)

        }

        if got != want {

            t.Errorf("got %q, want %q", got, want)

        }

    })

    t.Run("returns an error if a server doesn't respond within 10s", func(t *testing.T) {

        server := makeDelayedServer(25 * time.Millisecond)

        defer server.Close()

        _, err := ConfigurableRacer(server.URL, server.URL, 20*time.Millisecond)

        if err == nil {

            t.Error("expected an error but didn't get one")

        }

    })

}

```

我在第一个测试中增加了一个最终检查，用来验证不会收到错误。

## 总结

### select

- 帮助你同时等待多个 channel。
- 有时候你可能希望在某个 `case` 中加入 `time.After`，以防止系统无限期阻塞。

### httptest

- 这是一种创建测试服务器的便捷方式，让你能拥有可靠且可控的测试。
- 它使用了与“真实”`net/http` 服务器相同的接口，因此既一致，又减少了你需要学习的内容。

## 反射

你可以在这里找到本章的所有代码。

来自 Twitter

golang 挑战：编写一个函数 `walk(x interface{}, fn func(string))`，它接收一个结构体 x，并为其中找到的所有字符串字段调用 fn。难度级别：递归。

要做到这一点，我们需要用到*反射*。

在计算机科学中，反射是程序检查自身结构（尤其是通过类型）的能力；它是一种元编程形式，也是一个让人困惑的重要来源。

来自 Go 博客：反射

### 什么是 `interface`？

我们一直在享受 Go 为那些处理已知类型的函数所提供的类型安全，比如 `string`、`int`，以及我们自己的类型如 `BankAccount`。

这意味着我们无需额外工作就能获得一些文档，而且如果你试图向函数传入错误的类型，编译器会发出抱怨。

不过，你可能会遇到这样的场景：想要编写一个在编译时不知道类型的函数。

Go 通过 `interface{}` 类型让我们绕过这个限制，你可以把它看作任意类型（实际上，在 Go 中 `any` 是 `interface{}` 的别名）。

因此，`walk(x interface{}, fn func(string))` 会接受任何值作为 x。

### 那么为什么不全部使用 `interface` 来获得真正灵活的函数呢？

- 作为接受 `interface` 参数的函数的使用者，你会失去类型安全。如果你本意是将 `string` 类型的 `Foo.bar` 传入函数，却不小心传入了 `int` 类型的 `Foo.baz` 呢？编译器无法告知你犯了错。你也不知道究竟可以向函数传入什么。例如，知道一个函数接受 `UserService` 是非常有用的。

- 作为这类函数的编写者，你必须能够检查传入的*任何内容*，并试图弄清楚它是什么类型、可以用它做什么。这需要通过*反射*来完成。这种做法可能相当笨拙、难以阅读，并且通常性能较差（因为必须在运行时进行检查）。

简而言之，只有在确实需要时才使用反射。

如果你想要多态函数，请考虑是否可以通过接口（注意：不是 `interface`，虽然容易混淆）来设计它，这样只要用户实现了你的函数所需的方法，就可以用多种类型来使用你的函数。

我们的函数需要能够处理许多不同的东西。一如既往，我们会采用迭代式的方法，为我们想支持的每一个新事物编写测试，并在这个过程中持续重构，直到完成。

### 首先编写测试

我们希望用一个包含字符串字段的结构体作为 `x` 来调用我们的函数。然后我们可以监视传入的函数 `fn`，以确认它是否被调用。

```go
func TestWalk(t *testing.T) {

	expected := "Chris"

	var got []string

	x := struct {

		Name string

	}{expected}

	walk(x, func(input string) {

		got = append(got, input)

	})

	if len(got) != 1 {

		t.Errorf("wrong number of function calls, got %d want %d")

	}

}

```

- 我们想要存储一个字符串切片（`got`），它保存 `walk` 传给 `fn` 的字符串。在之前的章节中，我们经常为这种场景创建专门的类型来监视函数/方法的调用，但现在我们只需为 `fn` 传入一个闭包来捕获 `got` 即可。
- 我们使用一个匿名的 `struct`，其中包含一个类型为 `string` 的 `Name` 字段，以走最简单的“快乐”路径。
- 最后，用 `x` 和这个间谍函数调用 `walk`，目前只检查 `got` 的长度；等我们有了非常基础的可运行代码，再对断言做更具体的验证。

## 尝试运行测试

```text
./reflection_test.go:21:2: undefined: walk

```

## 编写最少量的代码让测试运行并检查失败

## 测试输出

我们需要定义 `walk`

```go
func walk(x interface{}, fn func(input string)) {

}

```

再次尝试运行测试

```text
=== RUN   TestWalk

--- FAIL: TestWalk (0.00s)

    reflection_test.go:19: wrong number of function calls, got 0 want 1

```
