
//file_system_store_test.go
func assertNoError(t testing.TB, err error) {
    t.Helper()
    if err != nil {
        t.Fatalf("didn't expect an error but got one, %v", err)
    }
}

使用此辅助函数处理其他编译问题。最后，你应该会得到一个失败的测试：

```
=== RUN   TestRecordingWinsAndRetrievingThem
--- FAIL: TestRecordingWinsAndRetrievingThem (0.00s)
    server_integration_test.go:14: didn't expect an error but got one, problem loading player store from file /var/folders/nj/r_ccbj5d7flds0sf63yy4vb80000gn/T/db841037437, problem parsing league, EOF
```

我们无法解析联赛，因为文件为空。我们之前没有收到错误，因为我们一直只是忽略它们。

让我们通过在其中放入一些有效的 JSON 来修复我们的集成测试：

//server_integration_test.go
func TestRecordingWinsAndRetrievingThem(t *testing.T) {
    database, cleanDatabase := createTempFile(t, `[]`)
    //etc...
}

现在所有测试都通过了，我们需要处理文件为空的情况。

## 先编写测试

//file_system_store_test.go
t.Run("works with an empty file", func(t *testing.T) {
    database, cleanDatabase := createTempFile(t, "")
    defer cleanDatabase()

    _, err := NewFileSystemPlayerStore(database)
```
assertNoError(t, err)
})
```

## 尝试运行测试

```
=== RUN   TestFileSystemStore/works_with_an_empty_file
   --- FAIL: TestFileSystemStore/works_with_an_empty_file
(0.00s)
    file_system_store_test.go:108: didn't expect an error
but got one, problem loading player store from file
/var/folders/nj/r_ccbj5d7flds0sf63yy4vb80000gn/T/db019548018,
problem parsing league, EOF
```

## 编写足够代码使其通过

将我们的构造函数更改为以下内容

//file_system_store.go
func NewFileSystemPlayerStore(file *os.File) (*FileSystemPlayerStore, error) {

    file.Seek(0, 0)

    info, err := file.Stat()

    if err != nil {
        return nil, fmt.Errorf("problem getting file info from file")
    }

    if info.Size() == 0 {
        file.Write([]byte("[]"))
        file.Seek(0, 0)
    }

    league, err := NewLeague(file)

    if err != nil {
        return nil, fmt.Errorf("problem loading player store from file")
```

```
}

    return &FileSystemPlayerStore{
        database: json.NewEncoder(&tape{file}),
        league:   league,
    }, nil
}
```

file.Stat 返回我们文件的统计信息，这使我们能够检查文件的大小。如果文件为空，我们写入一个空的 JSON 数组并 Seek 回到开头，为后续代码做好准备。

## 重构

我们的构造函数现在有点混乱，所以让我们将初始化代码提取到一个函数中：

//file_system_store.go
func initialisePlayerDBFile(file *os.File) error {
    file.Seek(0, 0)

    info, err := file.Stat()

    if err != nil {
        return fmt.Errorf("problem getting file info from file %v")
    }

    if info.Size() == 0 {
        file.Write([]byte("[]"))
        file.Seek(0, 0)
    }

    return nil
}

//file_system_store.go
func NewFileSystemPlayerStore(file *os.File) (*FileSystemPlayerStore, error) {
```
err := initialisePlayerDBFile(file)
if err != nil {
	return nil, fmt.Errorf("problem initialising player db file")
}
league, err := NewLeague(file)
if err != nil {
	return nil, fmt.Errorf("problem loading player store from file")
}
return &FileSystemPlayerStore{
	database: json.NewEncoder(&tape{file}),
	league: league,
}, nil
}
```

## 排序

我们的产品负责人希望 /league 返回按分数从高到低排序的玩家。

这里需要做的主要决定是软件中应在何处执行此操作。如果我们使用的是“真实”的数据库，我们会使用 ORDER BY 之类的功能，以便排序超快。因此，实现 PlayerStore 的代码负责排序似乎更合适。

## 先编写测试

我们可以更新 TestFileSystemStore 中第一个测试的断言：

//file_system_store_test.go
t.Run("league sorted", func(t *testing.T) {
	database, cleanDatabase := createTempFile(t, `{"Name": "Cleo", "Wins": 10},
 ...
```
{"Name": "Chris", "Wins": 33}]`)
defer cleanDatabase()

store, err := NewFileSystemPlayerStore(database)

assertNoError(t, err)

got := store.GetLeague()

want := []Player{
    {"Chris", 33},
    {"Cleo", 10},
}

assertLeague(t, got, want)

// read again
got = store.GetLeague()
assertLeague(t, got, want)
})
```

传入的 JSON 的顺序是错误的，我们的 want 将检查它是否以正确的顺序返回给调用者。

## 尝试运行测试

```
=== RUN   TestFileSystemStore/league_from_a_reader,_sorted
--- FAIL: TestFileSystemStore/league_from_a_reader,_sorted
(0.00s)
    file_system_store_test.go:46: got [{Cleo 10} {Chris 33}] want [{Chris 33} {Cleo 10}]
    file_system_store_test.go:51: got [{Cleo 10} {Chris 33}] want [{Chris 33} {Cleo 10}]
```

## 编写足够代码使其通过

```
func (f *FileSystemPlayerStore) GetLeague() League {
    sort.Slice(f.league, func(i, j int) bool {
```
```
return f.league[i].Wins > f.league[j].Wins
    })
    return f.league
}
```

sort.Slice

Slice 根据提供的 less 函数对提供的切片进行排序。

简单！

## 总结

## 我们涵盖的内容

- The `Seeker` interface and its relation to `Reader` and `Writer`.
- Working with files.
- Creating an easy to use helper for testing with files that hides all the messy stuff.
- `sort.Slice` for sorting slices.
- Using the compiler to help us safely make structural changes to the application.

## 打破规则

- Most rules in software engineering aren't really rules, just best practices that work 80% of the time.
- We discovered a scenario where one of our previous "rules" of not testing internal functions was not helpful for us so we broke the rule.
- It's important when breaking rules to understand the trade-off you are making. In our case, we were ok with it because it was just one test and would've been very difficult to exercise the scenario otherwise.
- In order to be able to break the rules **you must understand them first**. An analogy is with learning guitar. It doesn't matter
how creative you think you are, you must understand and practice the fundamentals.

## 我们的软件现状

- We have an HTTP API where you can create players and increment their score.
- We can return a league of everyone's scores as JSON.
- The data is persisted as a JSON file.

## 命令行和项目结构

你可以在这里找到本章的所有代码

我们的产品负责人现在希望通过引入第二个应用程序——命令行应用程序——来转变方向。

目前，它只需要能够在用户输入 Ruth wins 时记录玩家的胜利。目的是最终成为帮助用户玩扑克的工具。

产品负责人希望数据库在两个应用程序之间共享，以便联赛根据新应用程序中记录的胜利进行更新。

## 代码回顾

我们有一个包含 main.go 文件的应用程序，它启动了一个 HTTP 服务器。对于本次练习，HTTP 服务器本身不会很有趣，但它使用的抽象会很有趣。它依赖于 PlayerStore。

```
type PlayerStore interface {
    GetPlayerScore(name string) int
    RecordWin(name string)
    GetLeague() League
}
```

在上一章中，我们创建了 FileSystemPlayerStore，它实现了该接口。我们应该能够在新应用程序中重用其中的一些内容。

## 先进行一些项目重构

我们的项目现在需要创建两个二进制文件，我们现有的 Web 服务器和命令行应用程序。

在开始新工作之前，我们应该对项目进行结构化以适应这一点。

到目前为止，所有代码都生活在一个文件夹中，路径如下所示

```
$GOPATH/src/github.com/your-name/my-app
```

要在 Go 中创建应用程序，你需要在 `package main` 中有一个 `main` 函数。到目前为止，我们所有的“领域”代码都生活在 `package main` 中，我们的 `func main` 可以引用所有内容。

到目前为止这很好，而且不夸大包结构是良好的实践。如果你花时间查看标准库，你会看到很少有大量文件夹和结构。

幸运的是，在需要时添加结构非常简单。

在现有项目内部创建一个 `cmd` 目录，并在其中创建一个 `webserver` 目录（例如 `mkdir -p cmd/webserver`）。

将 `main.go` 移入其中。

如果你安装了 `tree`，你应该运行它，你的结构应该如下所示

```
.
|-- file_system_store.go
|-- file_system_store_test.go
|-- cmd
|   |-- webserver
|   |   |-- main.go
|-- league.go
|-- server.go
|-- server_integration_test.go
|-- server_test.go
```
