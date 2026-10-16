
```
func TestFind(t *testing.T) {
    t.Run("find first even number", func(t *testing.T) {
        numbers := []int{1, 2, 3, 4, 5, 6, 7, 8, 9, 10}

        firstEvenNumber, found := Find(numbers, func(x int) bool {
            return x%2 == 0
        })
        AssertTrue(t, found)
        AssertEqual(t, firstEvenNumber, 2)
    })
}
```

以下是实现

```go
func Find[A any](items []A, predicate func(A) bool) (value A, found bool) {
    for _, v := range items {
        if predicate(v) {
            return v, true
        }
    }
    return
}
```

同样地，因为它接受泛型类型，我们可以在很多方式中重用它

```go
type Person struct {
    Name string
}

t.Run("Find the best programmer", func(t *testing.T) {
    people := []Person{
        Person{Name: "Kent Beck"},
        Person{Name: "Martin Fowler"},
        Person{Name: "Chris James"},
    }

    king, found := Find(people, func(p Person) bool {
        return strings.Contains(p.Name, "Chris")
    })

    AssertTrue(t, found)
    AssertEqual(t, king, Person{Name: "Chris James"})
})
```

如你所见，这段代码完美无缺。

## 总结

当得体地使用时，像这样的高阶函数会使你的代码更易于阅读和维护，但请记住经验法则：

使用 TDD 过程来驱动出你实际需要的真实、具体的行为，在重构阶段你然后 *可能会* 发现一些有用的抽象来帮助整理代码。

练习将 TDD 与良好的源代码控制习惯结合起来。在尝试重构 *之前*，在测试通过时提交你的工作。这样如果搞乱了，你可以轻松地回到工作状态。

## 名称很重要

努力在 Go 之外做一些研究，这样你就不会重新发明已经存在且已有 established 名称的模式。

编写一个函数接收 `A` 的集合并将其转换为 `B`？不要称之为 `Convert`，那是 `Map`。使用这些项目的“正确”名称将减少他人的认知负担，并使其在搜索引擎中更友好以便学习更多。

## 这感觉不地道？

尝试保持开放的心态。

虽然 Go 的惯用法不会，也不应因泛型的发布而 *根本性* 地改变，但惯用法 *会* 改变——因为语言在改变！这不应该是一个有争议的观点。

说

这不是地道的

如果没有更多细节，这并不是一个可操作或有用的说法。特别是在讨论新语言特性时。

根据其优点而不是教条，与同事讨论代码模式和风格。只要你有设计良好的测试，你就可以在理解什么对你和你的团队有效时，始终进行重构和调整。

## 资源

Fold 是计算机科学中的真正基础。以下是一些有趣的资源，如果你想更深入地了解它

- 维基百科：Fold

- 关于 fold 的普遍性和表达性的教程

## 构建应用程序

现在你希望已经消化了 *Go Fundamentals* 部分，你对 Go 大多数语言特性和如何进行 TDD 有了坚实的基础。

下一节将涉及构建一个应用程序。

每一章都将在前一章的基础上迭代，根据产品负责人指示扩展应用程序的功能。

将引入新概念来帮助促进编写优秀的代码，但大部分新材料将学习 Go 标准库可以实现什么。

到最后，你应该对如何在 Go 中迭代地编写应用程序并以测试为后盾有坚实的把握。

- [HTTP 服务器] - 我们将创建一个应用程序，监听 HTTP 请求并响应它们。

- [JSON、路由和嵌入] - 我们将使我们的端点返回 JSON，探索如何进行路由并学习类型嵌入。

- [IO] - 我们将从磁盘持久化并读取数据，并将涵盖数据排序。

- [命令行] - 我们将创建一个新程序，利用迄今为止的代码来制作命令行界面。这将涉及我们重构项目以支持多个二进制文件

- [时间] - 我们将安排一些活动，这些活动根据用户输入在不同时间发生。

## HTTP 服务器

你可以在[此处]找到本章的所有代码。

你被要求创建一个 Web 服务器，用户可以在其中跟踪玩家赢得的游戏场数。

- `GET /players/{name}` 应返回一个数字，表示总胜利次数。

- `POST /players/{name}` 应记录该名字的一次胜利，每次后续 `POST` 都会递增。

我们将遵循 TDD 方法，尽快让软件跑起来，然后进行小的迭代改进，直到得到解决方案。采用这种方法，我们可以：

- 在任何给定时间保持问题空间很小

- 不走进死胡同

- 如果我们被卡住或迷失方向，执行回滚不会丢失大量工作。

## 红、绿、重构

在本书中，我们一直强调 TDD 的过程：编写一个测试并观察它失败（红），编写*最少*的代码使其工作（绿），然后重构。

在 TDD 为你提供安全保障方面，编写最少量的代码这一纪律非常重要。你应该尽可能快地脱离“红”状态。

Kent Beck 将其描述为：

让测试快速通过，过程中犯下任何必要的过错。

你可以犯这些过错，因为之后你会在测试安全的保护下进行重构。

## 如果不这样做呢？

在“红”状态下做出的修改越多，就越可能增加测试未覆盖的问题。

其想法就是，以测试为驱动、小步迭代地编写有用的代码，这样你就不会陷入几个小时的死胡同。

## 先有鸡还是先有蛋

我们如何增量构建这个功能？如果还没有存储任何内容，我们就无法 `GET` 一个玩家；而在没有 `GET` 端点的情况下，似乎很难知道 `POST` 是否起作用了。

这就是 *模拟* 大显身手的地方。

- `GET` 需要一个 `PlayerStore` *对象*来获取玩家的分数。这应该是一个接口，这样在测试时，我们可以创建一个简单的桩（stub）来测试代码，而无需实现任何实际的存储代码。

- 对于 `POST`，我们可以 *监视* 它对 `PlayerStore` 的调用，以确保它正确存储玩家数据。我们的保存实现不会与检索耦合。

- 为了快速得到一些可运行软件，我们可以做一个非常简单的内存实现，之后再用我们喜欢的任何存储机制来创建实现。

## 先编写测试

我们可以先写一个测试，通过返回一个硬编码的值使其通过，从而入门。Kent Beck 称之为“假实现”。一旦我们有了一个可以工作的测试，就可以编写更多测试，帮助我们移除那个常量。

通过做这一小步，我们可以为整个项目结构正确工作打下重要基础，而无需过多担心应用程序逻辑。

在 Go 中创建 Web 服务器，你通常会调用 `ListenAndServe`。

```go
func ListenAndServe(addr string, handler Handler) error
```

这将启动一个 Web 服务器，监听某个端口，为每个请求创建一个 goroutine，并针对一个 `Handler` 运行。

```go
type Handler interface {
    ServeHTTP(ResponseWriter, *Request)
}
```

一个类型通过实现 `ServeHTTP` 方法来实现 `Handler` 接口，`ServeHTTP` 方法接收两个参数：第一个是我们写入响应的地方，第二个是发送到服务器的 HTTP 请求。

让我们创建一个名为 `server_test.go` 的文件，为函数 `PlayerServer` 编写一个测试，该函数接收这两个参数。发送的请求将用于获取玩家的分数，我们期望它是 "20"。

```go
func TestGETPlayers(t *testing.T) {
    t.Run("returns Pepper's score", func(t *testing.T) {
        request, _ := http.NewRequest(http.MethodGet, "/players/Pepper")
        response := httptest.NewRecorder()

        PlayerServer(response, request)

        got := response.Body.String()
        want := "20"

        if got != want {
            t.Errorf("got %q, want %q", got, want)
        }
    })
}
```

为了测试我们的服务器，我们需要一个发送进来的 `Request`，并且我们想要监视我们的处理器向 `ResponseWriter` 写了什么。

- 我们使用 `http.NewRequest` 创建请求。第一个参数是请求的方法，第二个是请求的路径。`nil` 参数指的是请求体，在这种情况下我们不需要设置。

- `net/http/httptest` 中有一个现成的间谍工具，叫做 `ResponseRecorder`，我们可以使用它。它有许多有用的方法来检查作为响应写入了什么。

## 尝试运行测试

```
./server_test.go:13:2: undefined: PlayerServer
```

## 编写让测试运行的最小代码，并检查失败的测试输出

编译器会帮助你，听它的就好。

创建一个名为 `server.go` 的文件，并定义 `PlayerServer`。

```go
func PlayerServer() {}
```

再次尝试

```
./server_test.go:13:14: too many arguments in call to PlayerServer
have (*httptest.ResponseRecorder, *http.Request)
want ()
```

## 给函数添加参数

```go
import "net/http"
```

```go
func PlayerServer(w http.ResponseWriter, r *http.Request) {
}
```

代码现在可以编译，测试失败：

```
=== RUN   TestGETPlayers/returns_Pepper's_score
--- FAIL: TestGETPlayers/returns_Pepper's_score (0.00s)
    server_test.go:20: got '', want '20'
```

## 编写足够的代码使其通过

从 DI 章节，我们曾通过一个 `Greet` 函数接触过 HTTP 服务器。我们了解到 `net/http` 的 `ResponseWriter` 也实现了 `io.Writer`，因此我们可以使用 `fmt.Fprint` 将字符串作为 HTTP 响应发送。

```go
func PlayerServer(w http.ResponseWriter, r *http.Request) {
    fmt.Fprint(w, "20")
}
```

测试现在应该通过了。

## 完成脚手架

我们想把它接入一个应用程序。这很重要，因为：

- 我们将拥有 *真正可用的软件*，我们不是为了写测试而写测试，看到代码实际运行是很好的。

- 当我们重构代码时，很可能会改变程序的结构。我们希望这在应用程序中也能得到体现，作为增量方法的一部分。

为我们的应用程序创建一个新的 `main.go` 文件，并放入这段代码：

```go
package main

import (
    "log"
    "net/http"
)

func main() {
    handler := http.HandlerFunc(PlayerServer)
    log.Fatal(http.ListenAndServe(":5000", handler))
}
```

到目前为止，我们所有的应用程序代码都在一个文件中。然而，对于更大的项目来说，这并不是最佳实践，因为你会想把代码拆分到不同的文件中。

要运行它，执行 `go build`，它会收集目录中的所有 `.go` 文件并构建出一个程序。然后你可以用 `./myprogram` 执行它。

## http.HandlerFunc

之前我们探讨过，要创建一个服务器，我们需要实现 `Handler` 接口。*通常*，我们通过创建一个 `struct` 并实现其自己的 `ServeHTTP` 方法来实现该接口。然而，`struct` 的用途是保存数据，但*目前*我们没有状态，所以创建一个结构体似乎不太合适。

`HandlerFunc` 让我们避免了这一点。

`HandlerFunc` 类型是一个适配器，允许将普通函数用作 HTTP 处理器。如果 `f` 是一个具有适当签名的函数，那么 `HandlerFunc(f)` 就是一个调用 `f` 的 `Handler`。

```go
type HandlerFunc func(ResponseWriter, *Request)
```

从文档中，我们看到 `HandlerFunc` 类型已经实现了 `ServeHTTP` 方法。通过用它对我们的 `PlayerServer` 函数进行类型转换，我们现在已经实现了所需的 `Handler`。

`http.ListenAndServe(":5000"... )`

`ListenAndServe` 接收要监听的端口和一个 `Handler`。如果出现问题，Web 服务器会返回一个错误，例如端口可能已被监听。因此，我们将调用包装在 `log.Fatal` 中，以向用户记录错误。

我们现在要做的是编写另一个测试，促使我们做出积极的改变，以摆脱硬编码的值。

## 先编写测试

我们将在测试套件中添加另一个子测试，尝试获取另一个玩家的分数，这会打破我们硬编码的方法。

```go
t.Run("returns Floyd's score", func(t *testing.T) {
    request, _ := http.NewRequest(http.MethodGet, "/players/Floyd")
    response := httptest.NewRecorder()

    PlayerServer(response, request)

    got := response.Body.String()
    want := "10"

    if got != want {
        t.Errorf("got %q, want %q", got, want)
    }
})
```

```go
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

```go
type PlayerStore interface {
    GetPlayerScore(name string) int
}
```

为了让我们的 `PlayerServer` 能够使用 `PlayerStore`，它需要持有对后者的引用。现在正是调整架构的好时机，让 `PlayerServer` 变成一个结构体。

```go
type PlayerServer struct {
    store PlayerStore
}
```

最后，我们通过向新结构体添加一个方法，并放入现有的处理器代码，来实现 `Handler` 接口。
