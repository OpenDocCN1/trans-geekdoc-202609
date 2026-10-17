
```go
//CLI.go
type CLI struct {
    playerStore PlayerStore
    in          *bufio.Scanner
}

func NewCLI(store PlayerStore, in io.Reader) *CLI {
    return &CLI{
        playerStore: store,
        in:          bufio.NewScanner(in),
    }
}
```

通过这样做，我们就可以简化并重构我们的读取代码

```go
//CLI.go
func (cli *CLI) PlayPoker() {
    userInput := cli.readLine()
    cli.playerStore.RecordWin(extractWinner(userInput))
}

func extractWinner(userInput string) string {
    return strings.Replace(userInput, " wins", "", 1)
}

func (cli *CLI) readLine() string {
    cli.in.Scan()
    return cli.in.Text()
}
```

将测试改为使用构造函数，我们应该会使测试重新通过。

最后，我们可以回到新的 `main.go` 并使用我们刚刚创建的构造函数

```go
//cmd/cli/main.go
game := poker.NewCLI(store, os.Stdin)
```

尝试运行它，输入 “Bob wins”。

## 重构

我们在各自的应用中重复打开文件并从其内容创建 `file_system_store`。这感觉像是我们包设计上的一个小弱点，所以我们应该在其中创建一个函数来封装从路径打开文件并返回 `PlayerStore`。

```
//file_system_store.go
func FileSystemPlayerStoreFromFile(path string) (*FileSystemPlayerStore, func(), error) {
    db, err := os.OpenFile(path, os.O_RDWR|os.O_CREATE, 0666)

    if err != nil {
        return nil, nil, fmt.Errorf("problem opening %s %v", path, err)
    }

    closeFunc := func() {
        db.Close()
    }

    store, err := NewFileSystemPlayerStore(db)

    if err != nil {
        return nil, nil, fmt.Errorf("problem creating file system player store, %v", err)
    }

    return store, closeFunc, nil
}
```

现在重构我们的两个应用程序以使用此函数来创建存储。

## CLI 应用程序代码

```
//cmd/cli/main.go
package main

import (
```

```go
"fmt"
"github.com/quii/learn-go-with-tests/command-line/v3"
"log"
"os"
)

const dbFileName = "game.db.json"

func main() {
    store, close, err := poker.FileSystemPlayerStoreFromFile(dbFileName)
    if err != nil {
        log.Fatal(err)
    }
    defer close()
    fmt.Println("Let's play poker")
    fmt.Println("Type {Name} wins to record a win")
    poker.NewCLI(store, os.Stdin).PlayPoker()
}
```

## Web服务器应用代码

```go
//cmd/webserver/main.go
package main

import (
    "github.com/quii/learn-go-with-tests/command-line/v3"
    "log"
    "net/http"
)

const dbFileName = "game.db.json"

func main() {
    store, close, err := poker.FileSystemPlayerStoreFromFile(dbFileName)
    if err != nil {
        log.Fatal(err)
    }

    defer close()

    server := poker.NewPlayerServer(store)

    if err := http.ListenAndServe(":5000", server); err != nil {
        log.Fatalf("could not listen on port 5000 %v", err)
    }
}
```

注意这种对称性：尽管用户界面不同，但设置几乎完全相同。这感觉像是对我们目前设计的一个很好的验证。还要注意，`FileSystemPlayerStoreFromFile` 返回一个关闭函数，因此我们可以在使用完 `Store` 后关闭底层文件。

## 总结

## 包结构

本章意味着我们想要创建两个应用程序，并复用我们目前已经编写的领域代码。为此，我们需要更新包结构，以便我们各自的 `mains` 有独立的文件夹。

这样做时，由于未导出的值，我们遇到了集成问题，这进一步证明了在小组件中工作并经常集成的重要性。

我们学习了 `mypackage_test` 如何帮助我们创建一个测试环境，该环境对于与你的代码集成的其他包来说有着相同的体验，可帮助你发现集成问题，并了解你的代码使用起来有多容易（或不易！）。

## 读取用户输入

我们看到从 `os.Stdin` 读取非常容易使用，因为它实现了 `io.Reader`。我们使用 `bufio.Scanner` 轻松地逐行读取用户输入。

## 简单的抽象带来更简单的代码复用

将 `PlayerStore` 集成到我们的新应用中几乎不费吹灰之力（一旦我们做了包调整），随后测试也非常容易，因为我们也决定公开我们的 stub 版本。

## 时间

你可以在这里找到本章的所有代码。

产品负责人希望我们通过帮助一群人玩德州扑克来扩展命令行应用程序的功能。

你不需要知道太多关于扑克的知识，只需要知道在一定的时间间隔内，所有玩家都需要被告知一个稳步增加的“盲注”数值。

我们的应用程序将帮助跟踪盲注何时应该上涨，以及应该上涨多少。

- 当它启动时，会询问有多少玩家在玩。这将决定“盲注”下注上涨前的可用时间。

  - 基础时间为5分钟。

  - 每增加一个玩家，增加1分钟。

  - 例如，6名玩家等于盲注为11分钟。

- 盲注时间结束后，游戏应提醒玩家新的盲注下注金额。

- 盲注从100筹码开始，然后是200、400、600、1000、2000，并继续加倍，直到游戏结束（我们之前的“Ruth wins”功能仍然应该结束游戏）。

在上一章中，我们开始构建命令行应用程序，它已经接受 `{name} wins` 的指令。以下是当前 CLI 代码的样子，但在开始之前，请务必也熟悉其他代码。

```go
type CLI struct {
    playerStore PlayerStore
    in          *bufio.Scanner
}
```

```go
func NewCLI(store PlayerStore, in io.Reader) *CLI {
    return &CLI{
        playerStore: store,
        in:          bufio.NewScanner(in),
    }
}
```

```go
func (cli *CLI) PlayPoker() {
    userInput := cli.readLine()
    cli.playerStore.RecordWin(extractWinner(userInput))
}
```

```go
func extractWinner(userInput string) string {
    return strings.Replace(userInput, " wins", "", 1)
}
```

```go
func (cli *CLI) readLine() string {
    cli.in.Scan()
    return cli.in.Text()
}
```

## time.AfterFunc

我们希望程序能够根据玩家数量，在特定的时间段打印盲注下注值。

为了限制我们需要做的工作范围，我们暂时忽略玩家数量部分，先假设有5个玩家，这样我们可以测试每隔10分钟打印一次新的盲注下注值。

像往常一样，标准库已经为我们提供了 `func AfterFunc(d Duration, f func()) *Timer`。

`AfterFunc` 等待时间过去，然后在其自己的 goroutine 中调用 `f`。它返回一个 `Timer`，可以使用其 `Stop` 方法取消调用。

## time.Duration

`Duration` 表示两个时刻之间的流逝时间，以 `int64` 纳秒计数。

`time` 库有许多常量，可让你乘以这些纳秒，从而使它们在我们将要处理的场景中更具可读性。

```
5 * time.Second
```

当我们调用 `PlayPoker` 时，我们将调度所有盲注提醒。

不过，测试这个可能有点棘手。我们想要验证每个时间段都调度了正确的盲注金额，但如果你查看 `time.AfterFunc` 的签名，其第二个参数是它将运行的函数。在 Go 中你不能比较函数，因此我们无法测试传入了哪个函数。所以我们需要在 `time.AfterFunc` 周围编写某种包装器，它将接受运行时间和要打印的金额，以便我们可以对其进行检查。

## 先编写测试

向我们的测试套件添加一个新测试。

```go
t.Run("it schedules printing of blind values", func(t *testing.T) {
    in := strings.NewReader("Chris wins\n")
    playerStore := &poker.StubPlayerStore{}
    blindAlerter := &SpyBlindAlerter{}

    cli := poker.NewCLI(playerStore, in, blindAlerter)
    cli.PlayPoker()

    if len(blindAlerter.alerts) != 1 {
        t.Fatal("expected a blind alert to be scheduled")
    }
})
```

你会注意到我们创建了一个 `SpyBlindAlerter`，试图将其注入到我们的 CLI 中，然后检查在调用 `PlayPoker` 后是否调度了一个提醒。

（请记住，我们先从最简单的场景开始，然后会逐步迭代。）

以下是 `SpyBlindAlerter` 的定义。

```go
type SpyBlindAlerter struct {
    alerts []struct {
        scheduledAt time.Duration
        amount      int
    }
}

func (s *SpyBlindAlerter) ScheduleAlertAt(duration time.Duration, amount int) {
    s.alerts = append(s.alerts, struct {
        scheduledAt time.Duration
        amount      int
    }{duration, amount})
}
```

## 尝试运行测试

```
./CLI_test.go:32:27: too many arguments in call to poker.NewCLI
    have (*poker.StubPlayerStore, *strings.Reader,
*SpyBlindAlerter)
    want (poker.PlayerStore, io.Reader)
```

## 编写最少的代码使测试运行，并检查失败的测试输出

我们添加了一个新参数，编译器正在报错。*严格来说*，最少的代码是让 `NewCLI` 接受一个 `*SpyBlindAlerter`，但我们稍微取巧一下，直接将依赖定义为一个接口。

```go
type BlindAlerter interface {
    ScheduleAlertAt(duration time.Duration, amount int)
}
```

然后将其添加到构造函数中。

```go
func NewCLI(store PlayerStore, in io.Reader, alerter BlindAlerter) {
```

你的其他测试现在会失败，因为它们没有向 `NewCLI` 传入 `BlindAlerter`。

对 `BlindAlerter` 的间谍测试与其他测试无关，所以在测试文件中添加。

```go
var dummySpyAlerter = &SpyBlindAlerter{}
```

然后在其他测试中使用它来修复编译问题。通过将其标记为“dummy”，测试的读者可以清楚地知道它并不重要。

> 虚拟对象会被传递，但实际上从不使用。通常它们只是用来填充参数列表。

测试现在应该可以编译，而我们的新测试失败。

```
=== RUN   TestCLI
=== RUN   TestCLI/it_schedules_printing_of_blind_values
--- FAIL: TestCLI (0.00s)
--- FAIL: TestCLI/it_schedules_printing_of_blind_values (0.00s)
    CLI_test.go:38: expected a blind alert to be scheduled
```

## 写足够代码使其通过

我们需要在 CLI 上添加 `BlindAlerter` 作为字段，以便在 `PlayPoker` 方法中引用它。

```go
type CLI struct {
    playerStore PlayerStore
    in          *bufio.Scanner
    alerter     BlindAlerter
}

func NewCLI(store PlayerStore, in io.Reader, alerter BlindAlerter) {
    return &CLI{
        playerStore: store,
        in:          bufio.NewScanner(in),
        alerter:     alerter,
    }
}
```

使测试通过，我们可以随意调用我们的 `BlindAlerter`

```go
func (cli *CLI) PlayPoker() {
    cli.alerter.ScheduleAlertAt(5*time.Second, 100)
    userInput := cli.readLine()
    cli.playerStore.RecordWin(extractWinner(userInput))
}
```

接下来我们希望检查它是否按预期为 5 名玩家安排了所有提醒

## 先写测试

```go
t.Run("it schedules printing of blind values", func(t *testing.T
```
