
其中‘work’是指让测试通过，‘right’是指重构代码，而‘fast’是指优化代码使其例如运行更快。我们只能在让它工作并让它正确之后才‘让它变快’。我们很幸运，被给出的代码已经被证明是可工作的，并且不需要重构。我们绝不应该在另外两个步骤完成之前尝试‘让它变快’，因为

> [过早优化是万恶之源](#) -- Donald Knuth

## Select

你可以在这里找到本章的所有代码

你被要求创建一个名为 WebsiteRacer 的函数，它接收两个 URL 并通过发送 HTTP GET 请求来“竞赛”它们，并返回最先返回的 URL。如果它们在 10 秒内都未返回，则应返回错误。

为此，我们将使用

- `net/http` 来发起 HTTP 调用。
- `net/http/httptest` 来帮助我们测试它们。
- `goroutines`。
- `select` 来同步进程。

## Write the test first

让我们从一个天真的实现开始来启动。

```go
func TestRacer(t *testing.T) {
    slowURL := "http://www.facebook.com"
    fastURL := "http://www.quii.dev"

    want := fastURL
    got := Racer(slowURL, fastURL)

    if got != want {
        t.Errorf("got %q, want %q", got, want)
    }
}
```

我们知道这并不完美且存在问题，但它能让我们开始。重要的是不要过早地纠结于第一次就做到完美。

## Try to run the test

./racer_test.go:14:9: undefined: Racer

## Write the minimal amount of code for the test to run and check the failing test output

```go
func Racer(a, b string) (winner string) {
    return
}
```

racer_test.go:25: got '', want 'http://www.quii.dev'

## Write enough code to make it pass

```go
func Racer(a, b string) (winner string) {
    startA := time.Now()
    http.Get(a)
    aDuration := time.Since(startA)

    startB := time.Now()
    http.Get(b)
    bDuration := time.Since(startB)

    if aDuration < bDuration {
        return a
    }

    return b
}
```

对每个 URL：

1. 我们使用 `time.Now()` 来记录在尝试获取 URL 之前的时刻。
2. 然后我们使用 `http.Get` 来尝试获取 `URL` 的内容。此函数返回一个 `http.Response` 和一个 `error`，但目前我们对这些值不感兴趣。
3. `time.Since` 接收开始时间并返回一个 `time.Duration` 的差值。

完成这些之后，我们只需比较持续时间即可看出哪个更快。

## Problems

这可能对你来说会或不会让测试通过。问题是我们正在访问真实网站来测试自己的逻辑。

测试使用 HTTP 的代码非常常见，Go 在标准库中提供了工具来帮助你测试它。

在模拟和依赖注入章节中，我们介绍了理想情况下我们不希望依赖外部服务来测试代码，因为它们可能

- 慢
- 不稳定
- 无法测试边界情况

在标准库中，有一个名为 `net/http/httptest` 的包，你可以在其中轻松创建模拟 HTTP 服务器。

让我们更改我们的测试以使用模拟，这样我们就有可靠且可控的服务器来进行测试。

```go
func TestRacer(t *testing.T) {

    slowServer := httptest.NewServer(http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        time.Sleep(20 * time.Millisecond)
        w.WriteHeader(http.StatusOK)
    }))

    fastServer := httptest.NewServer(http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        w.WriteHeader(http.StatusOK)
    }))

    slowURL := slowServer.URL
    fastURL := fastServer.URL

    want := fastURL
    got := Racer(slowURL, fastURL)

    if got != want {
        t.Errorf("got %q, want %q", got, want)
    }

    slowServer.Close()
    fastServer.Close()
}
```

语法可能看起来有点繁琐，但慢慢来即可。

httptest.NewServer 接收一个 http.HandlerFunc，我们通过一个匿名函数将其传入。

http.HandlerFunc 是一个类型，看起来像这样：type HandlerFunc func(http.ResponseWriter, *http.Request)。

它所说的基本上是它需要一个接收 ResponseWriter 和 Request 的函数，这对于 HTTP 服务器来说并不奇怪。

事实证明这里并没有什么额外的魔法，这也是你在 Go 中编写真实 HTTP 服务器的方式。唯一的区别是我们将其包装在 httptest.NewServer 中，这使得在测试中使用它更容易，因为它会找到一个空闲端口进行监听，然后你可以在测试完成后关闭它。

在我们的两个服务器内部，我们让慢速服务器在收到请求时进行短暂的 time.Sleep，以使其比另一个服务器慢。两个服务器随后都使用 w.WriteHeader(http.StatusOK) 向调用方写回 OK 响应。

```go
got := Racer(slowURL, fastURL)

    if got != want {
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

为什么使用 `struct{}` 而不是像 `bool` 这样的其他类型？嗯，从内存角度来看，`chan struct{}` 是可用的最小数据类型，因此与 `bool` 相比我们没有分配。既然我们

关闭通道而不是在上面发送任何内容，为什么要分配任何东西呢？

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
