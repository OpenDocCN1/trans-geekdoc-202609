
```
if resp.StatusCode != statusCode {

	t.Log("exp:", statusCode)

	t.Log("got:", resp.StatusCode)

	t.Fatal("status codes don't match")

}

var d Document

if err := xml.NewDecoder(resp.Body).Decode(&d); err != nil {

	t.Fatal("unable to decode the response:", err)

}

if len(d.Channel.Items) != 1 {

	t.Fatal("not seeing 1 item in the feed: %d", len(d.Channel.Items))

}

}
```

# 7.4 内部 Web 端点

如果我正在构建一个 Web 服务，我希望在不构建和运行服务的情况下测试端点。目标是加载路由器并执行这些端点，而不需要处理所有网络相关的事务。标准库为此提供了支持。

```go
package handlers

import (
	"encoding/json"
	"net/http"
)

func Routes() {
	http.HandleFunc("/sendjson", sendJSON)
}

func sendJSON(rw http.ResponseWriter, r *http.Request) {
	u := struct {
	Name string
	Email string
	}(
	Name:  "Bill",
	Email: "bill@ardanlabs.com",
	)
	rw.Header().Set("Content-Type", "application/json")
	rw.WriteHeader(200)
	json.NewEncoder(rw).Encode(&u)
}
```

这段代码声明了一个名为 `handlers` 的新包以及名为 `sendJSON` 的需要测试的函数。在这种情况下，处理函数返回了字面量结构体的 JSON 表示，状态码为 200。

`Routes` 函数将 `sendJSON` 处理程序绑定到 `http` 包默认服务器复用器中的 `/sendjson` 路由。这意味着对 http://domain.com/sendjson 的任何调用都将由复用器路由到 `sendJSON` 处理函数。

# 列表 7.10

```go
package handlers_test

import (
    "encoding/json"
    "net/http"
    "net/http/httptest"
    "testing"
    "github.com/ardanlabs/gotraining/app/handlers"
)

func init() {
    handlers.Routes()
}

func TestSendJSON(t *testing.T) {
    url := "/sendjson"
    statusCode := 200
    r := httptest.NewRequest("GET", url, nil)
    w := httptest.NewRecorder()
    http.DefaultServeMux.ServeHTTP(w, r)
}
```

测试的第一步是使用 `init` 函数确保所有路由都已加载到复用器中。这是通过调用 `handlers.Routes` 函数实现的。这类测试中经常犯的一个大错误就是忘记加载路由。

路由加载后，下一步是构造一个请求并构造一个实现了 `http.ResponseWriter` 接口的值。`httptest` 包对这两者提供了支持。`httptest.NewRequest` 构建了针对 `/sendjson` 路由的 GET 请求。`httptest.NewRecorder` 构建了实现 `http.ResponseWriter` 接口的具体值，并可以直接对其进行检查以验证 Web 调用是否成功或失败。

运行测试的关键是从复用器中调用 `ServeHTTP` 函数。由于我在代码中使用了 `http.DefaultServerMux`，因此我是在那里调用 `ServeHTTP` 的。我可能选择使用的任何复用器都将实现此方法。一旦我调用了该方法，我就是在要求复用器通过路由处理请求并将响应应用到具体的记录器值中。

# 列表 7.11

```go
func TestSendJSON(t *testing.T) {
	if w.Code != 200 {
		t.Log("exp:", statusCode)
		t.Log("got:", w.StatusCode)
		t.Fatal("status codes don't match")
	}
	var u struct {
		Name string
		Email string
	}
	if err := json.NewDecoder(w.Body).Decode(&u); err != nil {
		t.Fatal("unable to decode the response:", err)
	}
	exp := "Bill"
	if u.Name != exp {
		t.Log("exp:", exp)
		t.Log("got:", u.Name)
		t.Fatal("user name does not match")
	}
	exp = "bill@ardanlabs.com"
	if u.Email != exp {
		t.Log("exp:", exp)
		t.Log("got:", u.Email)
		t.Fatal("user name does not match")
	}
}
```

现在，使用记录器值，我可以检查路由是否符合预期。首先我检查状态码是否为 200。然后尝试将响应 JSON 反序列化为具体类型。如果成功，我会检查 `Name` 和 `Email` 字段。如果一切正确，测试通过。

这种测试是在不需要运行 Web 服务的情况下执行的。

### 7.5 子测试 (Sub-Tests)

有时我希望在一个测试函数下将一组测试分组。我可能有一个表格测试（table test），可以在命令行控制测试哪些数据。我也可能希望并行运行一系列测试。如果遇到这些用例，Go 提供的子测试支持正是我需要的。

# 列表 7.12

```go
package sample_test

import (
    "net/http"
    "testing"
)

func TestDownload(t *testing.T) {
    tt := []struct {
        name       string
        url        string
        statusCode int
    }{
        {
            "ok",
            "https://www.ardanlabs.com/blog/index",
            http.StatusOK,
        },
        {
            "notfound",
            "http://rss.cnn.com/rss/topstorie",
            http.StatusNotFound,
        },
    }
    // ...
```

该测试将像我之前看到的表格测试一样测试 URL。这里的不同在于表格有一个名为 `name` 的字段，我将为每个条目创建一个子测试。给每个子测试一个唯一的名称是重要的，这样我就可以用最少的字符来运行它。

# 列表 7.13

```go
for _, test := range tt {
    test := test
    tf := func(t *testing.T) {
        resp, err := http.Get(test.url)
        if err != nil {
            t.Fatal("unable to get URL: %s", test.url, err)
        }
        defer resp.Body.Close()
        if resp.StatusCode != test.StatusCode {
            t.Log("exp:", test.StatusCode)
            t.Log("got:", resp.StatusCode)
            t.Fatal("status codes don't match")
        }
    }
    t.Run(test.name, tf)
}
```

循环内部的代码有几处变化。循环内部的第一行代码创建了一个局部作用域的变量。这是为了防止闭包问题。然后声明一个函数并赋值给变量 `tf`。该函数被传递给底部的 `t.Run` 调用。通过 `t.Run` 按名称注册子测试。一旦注册了所有测试，就可以一起执行，也可以在命令行中指定单独执行。

# 列表 7.14

```bash
$ go test -v
$ go test -run TestDownload/ok -v
$ go test -run TestDownload/notfound -v
```

这就是我运行所有子测试或指定任何单个子测试的方法。子测试的另一个酷功能：可以使用 `t.Parallel` 方法并行运行测试。

# 列表 7.15

```go
for _, tt := range tt {
  test := tt
  tf := func(t *testing.T) {
    t.Parallel()
    // ...
  }
  // ...
}
```

通过在函数的第一行添加 `t.Parallel()` 调用，测试工具将并行运行所有注册的测试，从而加快执行速度。

# 章：基准测试 (Benchmarking)

在本章，我将学习如何在 Go 中编写基准测试并使用语言提供的内置支持。我将学会基准测试可能会误，在解释结果时需要小心。

### 8.1 基准测试 (Basic Benchmark)

同时，在运行基准测试之前，我只是在猜测。Go 的一点在于，我永远不需要猜测。这就是工具链的方式。标准库和 Go 工具链包含了编写基准测试所需的一切。它首先是在要基准测试的包内创建一个遵循 `_test.go` 命名规范的文件，然后使用大写的 `Benchmark` 单词为每个函数添加基准测试函数。

# 列表 8.1

```go
sample_test.go
package sample

import (
	"testing"
)

func BenchmarkDownload(b *testing.B) {}
func BenchmarkUpload(b *testing.B) {}
```

这些是我可以在 `sample_test.go` 文件中声明的基准测试函数示例。函数中 Benchmark 单词后的第一个字母必须大写开头。如果不是，测试工具将认为该函数不是基准测试。另一个重要点是基准函数接受一个 `*testing.B` 指针作为唯一参数。

这里有一个非常感兴趣的基准测试可以运行：

```go
package basic

import (
	"fmt"
	"testing"
)

var gs string

func BenchmarkSprint(b *testing.B) {
	var s string
	for i := 0; i < b.N; i++ {
		s = fmt.Sprintf("hello")
	}
	gs = s
}

func BenchmarkSprintf(b *testing.B) {
	var s string
	for i := 0; i < b.N; i++ {
		s = fmt.Sprintf("hello")
	}
	gs = s
}
```

这个基准测试的前提是想知道哪个版本的 `Sprint` 更快，普通版本还是格式版本。当人们被问及时，他们倾向于说是普通版本，因为没有格式化。这些这些人总是错误的。

```bash
$ go test -bench -benchtime 3s -benchmem
goos: darwin
arch: amd64
pkg: github.com/ardanlabs/gotraining/topics/go/testing/benchmarks/basic
cpu: Intel(R) (TM) i9-9880HK CPU @ 2.40GHz
| | ns/op | B/op | allocs/op |
|---|---|---|---|
| BenchmarkSprint-16 | 56965252 | 55.48 ns/op | 5 B/op | 1 allocs/op |
| BenchmarkSprintf-16 | 80984947 | 42.46 ns/op | 5 B/op | 1 allocs/op |
```

从结果中可以看出，格式版本每次操作快 13 纳秒。差异微乎其微，但确实存在。

# 列表 8.4

```go
var gs string

func BenchmarkSprint(b *testing.B) {
    var gs string
    for i := 0; i < b.N; i++ {
        s = fmt.Sprint("hello")
    }
    gs = s
}
```

每个基准测试的核心都是从 `i` 到 `b.N` 的循环。循环内部放置了要进行基测试的代码。为了理解这个循环，我需要了解一个名为 `-benchtime` 的设置。

`-benchtime` 代表在提供结果之前运行循环的总时间。这里变得有点意思了，因为我不能根据时间来运行循环，只能根据迭代次数来运行。需要确定为了匹配 `-benchtime` 所需的迭代次数。

匹配 `-benchtime` 的正确 `b.N` 是通过一些尝试错误完成的。在运行基准测试的最开始，工具会将 `b.N` 的值设置为 1 并运行循环。然后它会将 `b.N` 的值乘以 100，直到接近 `-benchtime`。然后，算法就可以固定一个可用的 `b.N`。

# 列表 8.5

```go
var gs string
var a []int

func BenchmarkSprint(b *testing.B) {
    var gs string
    a = append(a, b.N)
    for i := 0; i < b.N; i++ {
        s = fmt.Sprint("hello")
    }
    if len(a) > 4 {
        fmt.Println(a)
    }
    gs = s
}
```

我添加了在每次调用基准测试函数时捕获 `b.N` 值的。。已知在某些情况下需要 5 次调用才能找到正确的 `b.N`，这时我就输出切片的内容。

# 列表 8.6
BenchmarkSprint-16 [1 100 10000 1000000 54495168]

我看到工具在 5 次尝试后确定了一个 `b.N` 的值，在尝试百万次迭代后找到了正确的数字。

这是编译器基准测试的另一个重要方面。编译器会将此代码编译成二进制文件以运行基准测试。循环内部的代码与生产环境中的运行保持准确是非常重要的。任何微小的变化都可能改变编译器构建代码的方式，或者代码在运行时的行为。

回到 Sprint 基准测试的原始代码。

# 列表 8.7

```go
var gs string

func BenchmarkSprint(b *testing.B) {
  var s string
  for i := 0; i < b.N; i++ {
    s = fmt.Sprint("hello")
  }
  gs = s
}
```

这个基准测试衡量的是调用 `Sprint` 的性能。注意 `Sprint` 函数在调用后返回了一个新字符串。在运行基准测试时，捕获该返回值是非常重要的，因为这代表了生产代码中使用该函数的真实行为。

如果我不捕获 `Sprint` 调用的返回值，编译器可能会将函数调用从编译后的二进制文件中剔除。如果不捕获返回值，该函数就是无用的，因为单代码的行为本身不会改变程序的行为。如果编译器选择丢弃对 `Sprint` 的调用，基准测试将只是运行一个空循环，提供不准确的结果。

当我运行基准测试时，我在命令行上使用以下调用。

# 列表 8.8

```
$ go test -bench . -benchtime 3s -benchmem
```
