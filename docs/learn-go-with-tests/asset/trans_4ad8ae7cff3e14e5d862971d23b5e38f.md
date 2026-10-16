
```
t.Errorf("got %q, want %q", got, want)
}
})
```

You may have been := httptest.NewRecorder()

        PlayerServer(response, request)

        assertResponseBody(t, response.Body.String(), "20")
    })

    t.Run("returns Floyd's score", func(t *testing.T) {
        request := newGetScoreRequest("Floyd")
        response := httptest.NewRecorder()

        PlayerServer(response, request)

        assertResponseBody(t, response.Body.String(), "10")
    })
}

func newGetScoreRequest(name string) *http.Request {
    req, _ := http.NewRequest(http.MethodGet, fmt.Sprintf("/players/%s", name))
    return req
}

func assertResponseBody(t testing.TB, got, want string) {
    t.Helper()
    if got != want {
        t.Errorf("response body is wrong, got %q want %q", got, want)
    }
}
```

然而，我们依然不应该满足。我们的服务器竟然知道这些分数，这让人感觉不对劲。

我们的重构已经清楚地告诉我们接下来该做什么。

我们将分数计算从处理器的主体中移到了一个名为 `GetPlayerScore` 的函数里。这看起来正是利用接口来分离关注点的合适位置。

让我们把我们重构出的这个函数改成一个接口。

```
```go
type PlayerStore interface {
    GetPlayerScore(name string) int
}
```
```

为了让我们的 `PlayerServer` 能够使用 `PlayerStore`，它需要持有对后者的引用。现在正是调整架构的好时机，让 `PlayerServer` 变成一个结构体。

```
```go
type PlayerServer struct {
    store PlayerStore
}
```
```

最后，我们通过向新结构体添加一个方法，并放入现有的处理器代码，来实现 `Handler` 接口。

```
```go
func (p *PlayerServer) ServeHTTP(w http.ResponseWriter, r *http.Request) {
    player := strings.TrimPrefix(r.URL.Path, "/players/")
    fmt.Fprint(w, p.store.GetPlayerScore(player))
}
```
```

唯一其他的改动是，我们现在调用 `store.GetPlayerScore` 来获取分数，而不是调用我们定义的本地函数（现在可以删除它了）。

下面是我们服务器的完整代码清单。

```
```go
//server.go
type PlayerStore interface {
    GetPlayerScore(name string) int
```
```

}

type PlayerServer struct {
    store PlayerStore
}

func (p *PlayerServer) ServeHTTP(w http.ResponseWriter, r *http.Request) {
    player := strings.TrimPrefix(r.URL.Path, "/players/")
    fmt.Fprintf(w, p.store.GetPlayerScore(player))
}
```

## 修复问题

这些改动不少，我们知道我们的测试和应用程序将无法编译，但别紧张，让编译器来处理吧。

```
./main.go:9:58: type PlayerServer is not an expression
```

我们需要修改测试，改为创建 `PlayerServer` 的新实例，然后调用它的 `ServeHTTP` 方法。

```
//server_test.go
func TestGETPlayers(t *testing.T) {
    server := &PlayerServer{}

    t.Run("returns Pepper's score", func(t *testing.T) {
        request := newGetScoreRequest("Pepper")
        response := httptest.NewRecorder()

        server.ServeHTTP(response, request)

        assertResponseBody(t, response.Body.String(), "20")
    })

    t.Run("returns Floyd's score", func(t *testing.T) {
        request := newGetScoreRequest("Floyd")
        response := httptest.NewRecorder()
```

```
server.ServeHTTP(response, request)

    assertResponseBody(t, response.Body.String(), "10")
})
}
```

注意，我们还不必担心如何创建存储（store），我们只是想尽快让编译器通过。

你应该养成这样的习惯：优先让代码能编译，然后再让代码通过测试。

如果在代码尚未编译时添加更多功能（如桩存储），我们可能会给自己带来更多的编译问题。

现在，`main.go` 也会因为同样的原因无法编译。

```
func main() {
    server := &PlayerServer{}
    log.Fatal(http.ListenAndServe(":5000", server))
}
```

最后，一切都能编译了，但测试却失败了。

```
=== RUN   TestGETPlayers/returns_the_Pepper's_score
panic: runtime error: invalid memory address or nil pointer dereference [recovered]
    panic: runtime error: invalid memory address or nil pointer dereference
```

这是因为我们在测试中没有传入 `PlayerStore`。我们需要创建一个桩（stub）存储。

```
//server_test.go
type StubPlayerStore struct {
    scores map[string]int
}

func (s *StubPlayerStore) GetPlayerScore(name string) int {
```

```
score := s.scores[name]
return score
}
```

对我们测试而言，使用 map 是创建桩键值存储的一种快速简单的方法。现在，让我们为测试创建一个这样的存储，并将其传入 `PlayerServer`。

```
//server_test.go
func TestGETPlayers(t *testing.T) {
    store := StubPlayerStore{
        map[string]int{
            "Pepper": 20,
            "Floyd": 10,
        },
    }
    server := &PlayerServer{&store}

    t.Run("returns Pepper's score", func(t *testing.T) {
        request := newGetScoreRequest("Pepper")
        response := httptest.NewRecorder()

        server.ServeHTTP(response, request)

        assertResponseBody(t, response.Body.String(), "20")
    })

    t.Run("returns Floyd's score", func(t *testing.T) {
        request := newGetScoreRequest("Floyd")
        response := httptest.NewRecorder()

        server.ServeHTTP(response, request)

        assertResponseBody(t, response.Body.String(), "10")
    })
}
```

现在我们的测试通过了，而且看起来更好。由于引入了存储，代码背后的意图更加清晰了。我们在告诉读者：因为我们把这些数据放在 `PlayerStore` 中，所以

当你将它与 `PlayerServer` 一起使用时，你应当得到以下响应。

## 运行应用程序

现在我们的测试已通过，完成这次重构所需做的最后一件事，就是检查我们的应用程序是否正常工作。程序应该能启动，但如果你尝试访问 http://localhost:5000/players/Pepper，你会得到一个糟糕的响应。

原因在于我们还没有传入 `PlayerStore`。

我们需要实现一个 `PlayerStore`。但现在这有点困难，因为我们还没有存储任何有意义的数据，所以暂时只能硬编码。

```
//main.go
type InMemoryPlayerStore struct{}

func (i *InMemoryPlayerStore) GetPlayerScore(name string) int {
    return 123
}

func main() {
    server := &PlayerServer{&InMemoryPlayerStore{}}
    log.Fatal(http.ListenAndServe(":5000", server))
}
```

如果你再次运行 `go build` 并访问同样的 URL，你应该会得到 "123"。这不算好，但在我们真正存储数据之前，这是能做到的最好情况了。另外，我们的主应用程序启动后却不能真正工作，这也让人感觉不好。我们不得不手动测试来发现问题。

关于下一步要做什么，我们有几个选择

- 处理玩家不存在的情况
- 处理 `POST /players/{name}` 场景

