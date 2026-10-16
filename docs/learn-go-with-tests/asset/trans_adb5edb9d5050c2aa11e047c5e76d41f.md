
```
import "io"

type tape struct {
    file io.ReadWriteSeeker
}

func (t *tape) Write(p []byte) (n int, err error) {
    t.file.Seek(0, 0)
    return t.file.Write(p)
}
```

注意我们现在只实现了 `Write`，因为它封装了 `Seek` 部分。这意味着我们的 `FileSystemStore` 只需要引用一个 `Writer` 即可。

//file_system_store.go
type FileSystemPlayerStore struct {
    database io.Writer
    league   League
}

## 更新构造函数以使用 Tape

```
//file_system_store.go
func NewFileSystemPlayerStore(database io.ReadWriteSeeker) *FileSystemPlayerStore {
    database.Seek(0, 0)
    league, _ := NewLeague(database)

    return &FileSystemPlayerStore{
        database: &tape{database},
        league:   league,
    }
}
```

最后，我们可以通过从 `RecordWin` 中移除 `Seek` 调用来实现我们想要的惊人收益。是的，这感觉不算多，但至少意味着如果我们进行其他类型的写入，我们可以依赖我们的 `Write` 按需行为。此外，它现在让我们可以单独测试可能有问题的代码并修复它。

让我们编写一个测试，在其中我们希望用比原始内容更小的内容更新文件的整个内容。

## 先编写测试

我们的测试将创建一个包含一些内容的文件，尝试使用 tape 写入它，然后再次读取所有内容以查看文件中的内容。在 tape_test.go 中：

//tape_test.go
func TestTape_Write(t *testing.T) {
    file, clean := createTempFile(t, "12345")
    defer clean()

    tape := &tape{file}

    tape.Write([]byte("abc"))

    file.Seek(0, 0)
    newFileContents, _ := ioutil.ReadAll(file)

    got := string(newFileContents)
    want := "abc"

    if got != want {
        t.Errorf("got %q want %q", got, want)
    }
}

## 尝试运行测试

```
=== RUN   TestTape_Write
--- FAIL: TestTape_Write (0.00s)
    tape_test.go:23: got 'abc45' want 'abc'
```

正如我们所想！它写入了我们想要的数据，但保留了原始数据的其余部分。

## 编写足够代码使其通过

`os.File` 有一个 `truncate` 函数，可以让我们有效地清空文件。我们应该能够直接调用它来获得我们想要的结果。

将 `tape` 改为以下内容：

```go
//tape.go
type tape struct {
    file *os.File
}

func (t *tape) Write(p []byte) (n int, err error) {
    t.file.Truncate(0)
    t.file.Seek(0, 0)
    return t.file.Write(p)
}
```

编译器将在我们期望 `io.ReadWriteSeeker` 但传入 `*os.File` 的多个地方失败。你现在应该能够自己修复这些问题，但如果卡住了，只需查看源代码即可。

一旦你完成它，重构我们的 `TestTape_Write` 测试应该就能通过了！

### 另一个小重构

在 `RecordWin` 中我们有这一行
`json.NewEncoder(f.database).Encode(f.league)`

我们不需要每次写入时都创建一个新的编码器，我们可以在构造函数中初始化一个并重用它。

在我们的类型中存储对 `Encoder` 的引用，并在构造函数中初始化它：

//file_system_store.go
type FileSystemPlayerStore struct {
    database *json.Encoder
    league   League
}

func NewFileSystemPlayerStore(file *os.File) *FileSystemPlayerStore {
    file.Seek(0, 0)
    league, _ := NewLeague(file)

    return &FileSystemPlayerStore{
        database: json.NewEncoder(&tape{file}),
        league:   league,
    }
}

在 RecordWin 中使用它。

```
func (f *FileSystemPlayerStore) RecordWin(name string) {
    player := f.league.Find(name)

    if player != nil {
        player.Wins++
    } else {
        f.league = append(f.league, Player{name, 1})
    }

    f.database.Encode(f.league)
}
```

## 我们刚才是不是破坏了一些规则？测试私有事物？没有接口？

## 关于测试私有类型

确实，一般来说你应该避免测试私有事物，因为这有时会导致测试与实现过于紧密耦合，从而妨碍未来的重构。

然而，我们必须不要忘记测试应该给我们 *信心*。

我们对实现是否能在添加任何编辑或删除功能时正常工作没有信心。我们不想让代码保持原样，特别是如果这是由多个人共同开发的，他们可能不了解我们初始方法中的不足。

最后，这只是一个测试！如果我们决定改变其工作方式，删除该测试也不会造成灾难，但我们至少为未来的维护者记录了该需求。

## 接口

我们起初使用 `io.Reader` 编写代码，因为这是对新 `PlayerStore` 进行单元测试的最简单路径。随着代码的开发，我们转向了 `io.ReadWriter`，然后是 `io.ReadWriteSeeker`。我们随后发现标准库中除了 `*os.File` 之外没有真正实现它的东西。我们本可以决定自己编写或使用开源实现，但感觉为测试创建临时文件更为务实。

最后，我们需要 `Truncate`，它也在 `*os.File` 上。这本是一个选项，可以创建我们自己的接口来捕获这些需求。

```
type ReadWriteSeekTruncate interface {
    io.ReadWriteSeeker
    Truncate(size int64) error
}
```

但这到底给我们带来了什么？请记住我们并没有 *模拟*，对于 **文件系统** 存储来说，接受 `*os.File` 以外的任何类型是不现实的，所以我们不需要接口提供的多态性。

不要害怕像我们在这里一样随意更改类型并进行实验。使用静态类型语言的好处是编译器会在每次更改时帮助你。

## 错误处理

在开始处理排序之前，我们应该确保对当前代码满意并清除可能存在的技术债务。尽快获得可工作的软件（保持在红色状态之外）是一个重要原则，但这并不意味着我们应该忽略错误情况！

如果我们回到 `FileSystemStore.go`，在我们的构造函数中有 `league, _ := NewLeague(f.database)`。

`NewLeague` 如果无法从我们提供的 `io.Reader` 解析联赛，则可能返回错误。

当时忽略它很务实，因为我们已经有失败的测试了。如果我们当时同时处理它，我们就会同时处理两件事。

让我们让我们的构造函数能够返回错误。

```
//file_system_store.go
func NewFileSystemPlayerStore(file *os.File) (*FileSystemPlayerStore, error) {
    file.Seek(0, 0)
    league, err := NewLeague(file)

    if err != nil {
        return nil, fmt.Errorf("problem loading player store from file")
    }

    return &FileSystemPlayerStore{
        database: json.NewEncoder(&tape{file}),
        league:   league,
    }, nil
}
```

请记住提供有帮助的错误信息非常重要（就像你的测试一样）。互联网上的人开玩笑说大多数 Go 代码是：

```
if err != nil {
    return err
}
```

这 100% 不是惯用的。向错误信息中添加上下文信息（即导致错误的操作）会使操作软件变得容易得多。

如果你尝试编译，你会得到一些错误。

```
./main.go:18:35:  multiple-value  NewFileSystemPlayerStore()  in single-value context
./file_system_store_test.go:35:36:                  multiple-value NewFileSystemPlayerStore() in single-value context
./file_system_store_test.go:57:36:                  multiple-value NewFileSystemPlayerStore() in single-value context
./file_system_store_test.go:70:36:                  multiple-value NewFileSystemPlayerStore() in single-value context
./file_system_store_test.go:85:36:                  multiple-value NewFileSystemPlayerStore() in single-value context
./server_integration_test.go:12:35:                multiple-value NewFileSystemPlayerStore() in single-value context
```

在 main 中，我们希望退出程序并打印错误。

//main.go
store, err := NewFileSystemPlayerStore(db)

if err != nil {
    log.Fatalf("problem creating file system player store, %v", err)
}
```

在测试中我们应该断言没有错误。我们可以创建一个助手来帮助处理这个问题。
