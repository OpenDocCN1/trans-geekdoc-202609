
```go
import (
    "fmt"
    "github.com/quii/learn-go-with-tests/command-line/v3/poker"
    "log"
    "os"
)

const dbFileName = "game.db.json"

func main() {
    fmt.Println("Let's play poker")
    fmt.Println("Type {Name} wins to record a win")

    db, err := os.OpenFile(dbFileName, os.O_RDWR|os.O_CREATE, 0666)

    if err != nil {
        log.Fatalf("problem opening %s %v", dbFileName, err)
    }

    store, err := poker.NewFileSystemPlayerStore(db)

    if err != nil {
        log.Fatalf("problem creating file system player store, %v", err)
    }

    game := poker.CLI{store, os.Stdin}
    game.PlayPoker()
}
```

## 你应该会得到一个错误

```
command-line/v3/cmd/cli/main.go:32:25: implicit assignment of unexported field 'playerStore' in poker.CLI literal
command-line/v3/cmd/cli/main.go:32:34: implicit assignment of unexported field 'in' in poker.CLI literal
```

这里发生的事情是因为我们试图为 `CLI` 中的字段 `playerStore` 和 `in` 赋值。这些是未导出的（私有）字段。我们可以在测试代码中这样做，因为我们的测试与 `CLI` 在同一个包 `poker` 中。但我们的 `main` 在 `package main` 中，所以它无法访问。

这凸显了 *集成你的工作* 的重要性。我们理所当然地将 `CLI` 的依赖项设为私有（因为我们不希望它们暴露给 `CLI` 的使用者），但没有为使用者提供构造它的方法。

有没有办法更早地发现这个问题？

## package mypackage_test

到目前为止，在所有其他示例中，当我们创建测试文件时，我们将其声明为与我们正在测试的同一个包。

这没问题，这意味着在偶尔想要测试包内部某些内容时，我们可以访问未导出的类型。

但鉴于我们主张 *不* 通常测试内部事物，Go 能帮助强制执行这一点吗？如果我们只能访问导出的类型（就像我们的 `main` 所做的那样）来测试我们的代码会怎样？

当你使用多个包编写项目时，我强烈建议你的测试包名称以 `_test` 结尾。当你这样做时，你将只能访问包中的公共类型。这将有助于解决这个特定情况，也有助于强制执行只测试公共 API 的纪律。如果你仍然希望测试内部实现，可以使用你想要测试的包制作一个单独的测试。

TDD 中的一句格言是，如果你无法测试你的代码，那么用户集成它可能也很困难。使用 `package foo_test` 会有所帮助，因为它会强制你像包的用户一样导入并测试你的代码。

在修复 `main` 之前，让我们将 `CLI_test.go` 内部的测试包改为 `poker_test`。

如果你有一个配置良好的 IDE，你会突然看到很多红色！如果你运行编译器，你会得到以下错误

```
./CLI_test.go:12:19: undefined: StubPlayerStore
./CLI_test.go:17:3: undefined: assertPlayerWin
./CLI_test.go:22:19: undefined: StubPlayerStore
./CLI_test.go:27:3: undefined: assertPlayerWin
```

我们现在遇到了更多关于包设计的疑问。为了测试我们的软件，我们创建了未导出的存根和辅助函数，而这些在我们的 `CLI_test` 中不再可用，因为这些辅助函数是在 `poker` 包的 `_test.go` 文件中定义的。

## 我们是否希望我们的存根和辅助函数是“公开的”？

这是一个主观的讨论。有人可能会争辩说，你不希望用便于测试的代码污染你的包 API。

在 Mitchell Hashimoto 的演讲 “Advanced Testing with Go” 中，描述了 HashiCorp 如何倡导这样做，以便包的用户在编写测试时不必重新造轮子编写存根。在我们的例子中，这意味着任何使用我们的 `poker` 包的人都不必为与我们的代码一起工作而创建自己的存根 `PlayerStore`。

就个人经验而言，我在其他共享包中使用过这种技术，在用户集成我们的包时节省时间方面被证明非常有用。

所以让我们创建一个名为 `testing.go` 的文件并添加我们的存根和辅助函数。

```
//testing.go
package poker

import "testing"

type StubPlayerStore struct {
```
```go
scores   map[string]int
winCalls []string
league   []Player
}
```

func (s *StubPlayerStore) GetPlayerScore(name string) int {
    score := s.scores[name]
    return score
}

func (s *StubPlayerStore) RecordWin(name string) {
    s.winCalls = append(s.winCalls, name)
}

func (s *StubPlayerStore) GetLeague() League {
    return s.league
}

func AssertPlayerWin(t testing.TB, store *StubPlayerStore, winner string) {
    t.Helper()

    if len(store.winCalls) != 1 {
        t.Fatalf("got %d calls to RecordWin want %d", len(store.winCalls), 1)
    }

    if store.winCalls[0] != winner {
        t.Errorf("did not store correct winner got %q want %q", store.winCalls[0], winner)
    }
}

// todo for you - the rest of the helpers
```
```

你需要使辅助函数公开（记住导出是通过首字母大写完成的）如果你希望它们对导入我们包的人可见。

在我们的 `CLI` 测试中，你需要像在不同包内使用它一样调用代码。

```go
//CLI_test.go
func TestCLI(t *testing.T) {
```
```go
func TestCLI(t *testing.T) {
    t.Run("record chris win from user input", func(t *testing.T) {
        in := strings.NewReader("Chris wins\n")
        playerStore := &poker.StubPlayerStore{}

        cli := &poker.CLI{playerStore, in}
        cli.PlayPoker()

        poker.AssertPlayerWin(t, playerStore, "Chris")
    })

    t.Run("record cleo win from user input", func(t *testing.T) {
        in := strings.NewReader("Cleo wins\n")
        playerStore := &poker.StubPlayerStore{}

        cli := &poker.CLI{playerStore, in}
        cli.PlayPoker()

        poker.AssertPlayerWin(t, playerStore, "Cleo")
    })
}
```
```

你现在会看到我们与 `main` 中相同的问题

```
./CLI_test.go:15:26: implicit assignment of unexported field 'playerStore' in poker.CLI literal
./CLI_test.go:15:39: implicit assignment of unexported field 'in' in poker.CLI literal
./CLI_test.go:25:26: implicit assignment of unexported field 'playerStore' in poker.CLI literal
./CLI_test.go:25:39: implicit assignment of unexported field 'in' in poker.CLI literal
```

解决这个问题的最简单方法是像为其他类型那样制作一个构造函数。我们还将更改 `CLI` 使其存储一个 `bufio.Scanner` 而不是读取器，因为它现在在构造时自动包装。

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

最后，我们可以回到新的 main.go 并使用我们刚刚创建的构造函数

```go
//cmd/cli/main.go
game := poker.NewCLI(store, os.Stdin)
```

尝试运行它，输入 “Bob wins”。

## 重构

我们在各自的应用中重复打开文件并从其内容创建 file_system_store。这感觉像是我们包设计上的一个小弱点，所以我们应该在其中创建一个函数来封装从路径打开文件并返回 PlayerStore。

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
