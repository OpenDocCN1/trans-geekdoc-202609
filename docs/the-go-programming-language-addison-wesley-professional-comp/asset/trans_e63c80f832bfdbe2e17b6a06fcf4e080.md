
# The `defer` Statement

## Example: Title Extraction

```go
func title(url string) error {
    resp, err := http.Get(url)
    if err != nil {
        return err
    }

    // Check Content-Type is HTML (e.g., "text/html; charset=utf-8").
    ct := resp.Header.Get("Content-Type")
    if ct != "text/html" && !strings.HasPrefix(ct, "text/html;") {
        resp.Body.Close()
        return fmt.Errorf("%s has type %s, not text/html", url, ct)
    }

    doc, err := html.Parse(resp.Body)
    resp.Body.Close()
    if err != nil {
        return fmt.Errorf("parsing %s as HTML: %v", url, err)
    }

    visitNode := func(n *html.Node) {
        if n.Type == html.ElementNode && n.Data == "title" &&
            n.FirstChild != nil {
            fmt.Println(n.FirstChild.Data)
        }
    }
    forEachNode(doc, visitNode, nil)
    return nil
}
```

[Click here to view code image](#part0135_split_057.html#id144pro02_r)

## Typical Session

```
$ go build gopl.io/ch5/title1
$ ./title1 http://gopl.io
The Go Programming Language
$ ./title1 https://golang.org/doc/effective_go.html
Effective Go - The Go Programming Language
$ ./title1 https://golang.org/doc/gopher/frontpage.png
title: https://golang.org/doc/gopher/frontpage.png
    has type image/png, not text/html
```

观察重复的 `resp.Body.Close()` 调用，它确保 `title` 在所有执行路径上（包括失败时）都关闭网络连接。随着函数变得更复杂并需要处理更多错误，这种清理逻辑的重复可能会成为维护问题。让我们看看 Go 独特的 `defer` 机制是如何简化事情的。

## How `defer` Works

从语法上讲，`defer` 语句是一个由关键字 `defer` 修饰的普通函数或方法调用。函数和参数表达式在语句执行时求值，但实际调用被*推迟*到包含 `defer` 语句的函数结束时，无论是正常结束（通过执行 return 语句或运行到函数末尾），还是异常结束（通过 panic）。可以推迟任意数量的调用；它们按与推迟顺序相反的顺序执行。

`defer` 语句常用于成对的操作，如打开和关闭、连接和断开、或加锁和解锁，以确保在所有情况下都释放资源，无论控制流多么复杂。释放资源的 `defer` 语句的正确位置是在成功获取资源之后立即放置。在下面的 `title` 函数中，单个推迟调用替换了之前对 `resp.Body.Close()` 的两次调用：

[Click here to view code image](#part0135_split_058.html#id145pro01_r)

`gopl.io/ch5/title2`

```go
func title(url string) error {
    resp, err := http.Get(url)
    if err != nil {
        return err
    }
    defer resp.Body.Close()

    ct := resp.Header.Get("Content-Type")
    if ct != "text/html" && !strings.HasPrefix(ct, "text/html;") {
        return fmt.Errorf("%s has type %s, not text/html", url, ct)
    }

    doc, err := html.Parse(resp.Body)
    if err != nil {
        return fmt.Errorf("parsing %s as HTML: %v", url, err)
    }

    // ...print doc's title element...

    return nil
}
```

## Other Resource Examples

### File Operations

同样的模式可用于网络连接以外的其他资源，例如关闭打开的文件：

[Click here to view code image](#part0135_split_059.html#id145pro02_r)

`io/ioutil`

```go
package ioutil

func ReadFile(filename string) ([]byte, error) {
    f, err := os.Open(filename)
    if err != nil {
        return nil, err
    }
    defer f.Close()
    return ReadAll(f)
}
```

### Mutex Locking

或用于解锁互斥锁（[§9.2](#part0089.html#id-mutex)）：

```go
var mu sync.Mutex
var m = make(map[string]int)

func lookup(key string) int {
    mu.Lock()
    defer mu.Unlock()
    return m[key]
}
```

## Debugging with `defer`

`defer` 语句还可用于在调试复杂函数时配对“进入时”和“退出时”的动作。下面的 `bigSlowOperation` 函数立即调用 `trace`，它执行“进入时”动作，然后返回一个函数值，该函数被调用时执行相应的“退出时”动作。通过这种方式推迟对返回函数的调用，我们可以在一条语句中检测函数的入口和所有出口，甚至可以在两个动作之间传递值，如 `start` 时间。但别忘了 `defer` 语句中的最后一对括号，否则“进入时”动作会在退出时发生，而“退出时”动作根本不会发生！

[Click here to view code image](#part0135_split_060.html#id146pro01_r)

`gopl.io/ch5/trace`

```go
func bigSlowOperation() {
    defer trace("bigSlowOperation")() // don't forget the extra parentheses
    // ...lots of work...
    time.Sleep(10 * time.Second) // simulate slow operation by sleeping
}

func trace(msg string) func() {
    start := time.Now()
    log.Printf("enter %s", msg)
    return func() { log.Printf("exit %s (%s)", msg, time.Since(start)) }
}
```

每次调用 `bigSlowOperation` 时，它都会记录其进入和退出以及两者之间的 elapsed 时间。（我们用 `time.Sleep` 来模拟慢速操作。）

[Click here to view code image](#part0135_split_061.html#id146pro02_r)

```
$ go build gopl.io/ch5/trace
$ ./trace
2015/11/18 09:53:26 enter bigSlowOperation
2015/11/18 09:53:36 exit bigSlowOperation (10.000589217s)
```

## Deferred Functions and Return Values

推迟函数在 return 语句更新了函数的结果变量*之后*运行。因为匿名函数可以访问其外层函数的变量，包括命名结果，所以推迟的匿名函数可以观察函数的结果。

### Observing Results

考虑函数 `double`：

[Click here to view code image](#part0135_split_062.html#id147pro01_r)

```go
func double(x int) int {
    return x + x
}
```

通过命名其结果变量并添加 `defer` 语句，我们可以让函数在每次被调用时打印其参数和结果。

[Click here to view code image](#part0135_split_063.html#id147pro02_r)

```go
func double(x int) (result int) {
    defer func() { fmt.Printf("double(%d) = %d\n", x, result) }()
    return x + x
}

_ = double(4)
// Output:
// "double(4) = 8"
```

对于像 `double` 这样简单的函数，这招有点大材小用，但在有许多 return 语句的函数中可能很有用。

### Modifying Results

推迟的匿名函数甚至可以更改外层函数返回给调用者的值：

```go
func triple(x int) (result int) {
    defer func() { result += x }()
    return double(x)
}

fmt.Println(triple(4)) // "12"
```

## Deferred Calls in Loops

因为推迟函数直到函数执行的最末尾才执行，循环中的 `defer` 语句值得额外审视。下面的代码可能会耗尽文件描述符，因为直到所有文件都被处理完才会关闭文件：

[Click here to view code image](#part0135_split_064.html#id147pro03_r)

```go
for _, filename := range filenames {
    f, err := os.Open(filename)
    if err != nil {
        return err
    }
    defer f.Close() // NOTE: risky; could run out of file descriptors
    // ...process f...
}
```

## Solution: Helper Function

一个解决方案是将循环体（包括 `defer` 语句）移到另一个函数中，在每次迭代时调用该函数。

[Click here to view code image](#part0135_split_065.html#id147pro04_r)

```go
for _, filename := range filenames {
    if err := doFile(filename); err != nil {
        return err
    }
}

func doFile(filename string) error {
    f, err := os.Open(filename)
    if err != nil {
        return err
    }
    defer f.Close()
    // ...process f...
}
```

## Example: Improved Fetch Program

下面的示例是一个改进的 `fetch` 程序（[§1.5](#part0016.html#id-fetchingaurl)），它将 HTTP 响应写入本地文件而不是标准输出。它使用 `path.Base` 函数从 URL 路径的最后一个组件派生文件名。

[Click here to view code image](#part0135_split_066.html#id148pro01_r)

`gopl.io/ch5/fetch`
