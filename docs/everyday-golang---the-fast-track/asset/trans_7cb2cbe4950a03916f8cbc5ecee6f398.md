

## CGO 与可移植性

CGO 使得创建调用 C 代码的 Go 包成为可能。

“CGO”是 Go 链接 C/C++ 库的能力，有时在使用某些库时需要用到它，例如 SQLite，以及一些 Go 标准库中没有的 Linux 加密包。

CGO 让可移植性变得更加困难，也超出了本书的讨论范围。我个人建议，如果你打算交叉编译应用程序，那么无论如何都要避免使用 CGO。

确保你没有使用任何 CGO 的一个好方法，是通过 `CGO_ENABLED=0` 环境变量，你可以在构建命令前加上它。

另请参阅：Go 文档中关于 CGO 的内容，以及 Dave Cheney 所写的《cgo is not Go》。

```
file first-go-arm
first-go-arm: ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, not stripped

file first-go-arm64
first-go-arm64: ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, not stripped
```

如果你使用 bash 命令 `du`，可以看到二进制文件的大小，其中包含调试符号。

```
du -h ./first-go

2.0M    ./first-go
```

有时可以通过去除调试符号来让这个文件变得更小。

```
GOOS=linux go build -a -ldflags "-s -w"

du -h first-go
1.4M    first-go

first-go: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, stripped
```

请注意更小的体积，以及 `file` 命令输出中的 “stripped”。

## 第 4 章

### 从 HTTP 端点获取 JSON

这一定是刚入门的 Go 程序员最常见的任务之一。你已经安装了 Go，并开始开发 CLI，现在你需要与外部 API 对接，发起一个 HTTP “GET” 请求。这个 API 很可能会使用 JSON。

我们将查询一个免费提供的端点，它会告诉我们当前太空中有多少宇航员，以及他们的名字。

我们将使用 Go 标准库中的 HTTP 和 JSON，与其他语言不同，我们不需要安装任何外部包。

### 开始

为你的新项目创建一个文件夹（此处可以使用你的 GitHub 用户名）：

```
export GH_USERNAME="alexellis"
mkdir -p $GOPATH/src/github.com/$GH_USERNAME/get-json/
cd $GOPATH/src/github.com/$GH_USERNAME/get-json/
```

现在保存一个名为 `main.go` 的新文件：

```go
package main

func main() {

}
```

这个程序实际上是一个没有任何打印语句的 hello-world。

继续运行这个程序，你有两种方式：

```
go run main.go
```

或者构建一个二进制文件，然后运行它。

```
go build
./get-json
```

现在添加一条打印语句：

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello world")
}
```

现在你可以再次构建并运行代码。注意，你也可以在编译时通过 `-o` 指定二进制文件的输出名称：

```
go build -o get-json
./get-json
```

Go 提供了一种基于约定的文件格式化方式，你可以用以下命令格式化文件及其缩进：

```
gofmt -s -w main.go
```

`-w` 选项会将改动写入文件。

正如我们在前面章节中探讨过的，Go 应用程序无需进一步修改即可为其他操作系统进行交叉编译。下面是为 Windows 构建上述代码的方法：

```
GOOS=windows go build -o get-json.exe
```

### 学习解析 JSON

接下来让我们解析一些 JSON。在 Go 中，我们可以将 JSON 文档转换为一个结构体，这有助于以结构化的方式访问数据。如果文档与结构体不匹配，就会抛出错误。

我们以 Open Notify 小组提供的一个 API 为例——它显示太空中的宇航员人数以及他们的姓名。

### 太空中的宇航员 JSON

它看起来有点像这样：

```json
{"people": [{"craft": "ISS", "name": "Sergey Ryzhikov"}, {"craft": "ISS", "name": "Andrey Borisenko"}, {"craft": "ISS", "name": "Shane Kimbrough"}, {"craft": "ISS", "name": "Oleg Novitskiy"}, {"craft": "ISS", "name": "Thomas Pesquet"}, {"craft": "ISS", "name": "Peggy Whitson"}], "message": "success", "number": 6}
```

根据维基百科：

> 在计算机科学中，marshalling（美式拼写为 marshaling）是将对象的内存表示转换为适合存储或传输的数据格式的过程。它通常用在数据需要在计算机程序的不同部分之间移动，或从一个程序移动到另一个程序时。

如果你有 Python、Ruby 或 Node 背景，那么 Go 中的 “Unmarshal” 行为通常对应着你之前把文本解析为 JSON 的操作。

Go 会接收一个结构体的引用，然后尝试将输入映射到该数据结构中。相反的操作是 “Marshal”，它将对象序列化为文本或二进制表示。

我们将导入 `fmt` 包以使用 `Println` 函数，并导入 `encoding/json` 包，以便将 JSON 文本 Unmarshal 到结构体中。

创建 `main.go`：

```go
package main

import (
    "encoding/json"
    "fmt"
)

type people struct {
    Number int `json:"number"`
}

func main() {
    text := `{"people": [{"craft": "ISS", "name": "Sergey Ryzhikov"}, {"craft": "ISS", "name": "Andrey Borisenko"}, {"craft": "ISS", "name": "Shane Kimbrough"}, {"craft": "ISS", "name": "Oleg Novitskiy"}, {"craft": "ISS", "name": "Thomas Pesquet"}, {"craft": "ISS", "name": "Peggy Whitson"}], "message": "success", "number": 6}`
    textBytes := []byte(text)

    p := people{}
    err := json.Unmarshal(textBytes, &p)
    if err != nil {
        fmt.Println(err)
        return
    }
    fmt.Println(p.Number)
}
```

我们硬编码了 Open Notify 的 JSON 响应，以便一次只处理一个行为。

`json.Unmarshal` 函数处理的是 `[]byte` 类型而不是字符串，因此我们使用 `[]byte(stringHere)` 来创建所需的格式。

为了使用结构体来 unmarshal JSON 文本，我们通常需要用一些标签（tag）来装饰它，以帮助标准库理解如何映射这些属性：

```go
type people struct {
    Number int `json:"number"`
}
```

属性名需要以大写字母开头，这会将它们标记为可导出或公开的。如果你的结构体属性与 JSON 中的属性相同，那么可以跳过这个标签。

另一件需要注意的事情是，我们向方法传入了新的/空的 people 结构体的地址。你可以试着去掉 `&` 符号，但值会被设置在空结构体的另一个副本中。如果你来自按引用传递参数的语言，这可能看起来有些奇怪。

### 通过 HTTP 获取 JSON

现在我们已经能够解析与我们的 API 匹配的 JSON 文档，接下来编写一个 HTTP 客户端，从互联网获取这段文本。

Go 在 `net/http` 包中内置了 HTTP 客户端，但它在超时时间过长方面存在问题，而且有一些知名文章建议你显式地在请求上设置超时。

在 Go 中有更简洁的创建 HTTP 请求的方式，但通过添加自定义超时，我们能让应用程序更健壮。

现在创建 `main.go`：

```go
package main

import (
    "encoding/json"
    "fmt"
    "io"
    "log"
    "net/http"
    "time"
)

type people struct {
    Number int `json:"number"`
}

func main() {

    url := "http://api.open-notify.org/astros.json"

    spaceClient := http.Client{
        Timeout: time.Second * 2, // Timeout after 2 seconds
    }

    req, err := http.NewRequest(http.MethodGet, url, nil)
    if err != nil {
        log.Fatal(err)
    }

    req.Header.Set("User-Agent", "spacecount-tutorial")

    res, err := spaceClient.Do(req)
    if err != nil {
        log.Fatal(err)
    }

    if res.Body != nil {
        defer res.Body.Close()
    }

    body, err := io.ReadAll(res.Body)
    if err != nil {
        log.Fatal(err)
    }

    p := people{}
    err = json.Unmarshal(body, &p)
    if err != nil {
        log.Fatal(err)
    }

    fmt.Println(p.Number)
}
```

如果你习惯编写 Node.js，那么你会习惯大多数 I/O 操作返回一个可能为 null 的错误。Go 中也是如此，而且在这里检查错误会让代码变得相当冗长。你可能想把代码中的部分内容重构为独立的方法——一个用于下载，一个用于 unmarshal JSON 数据。

尝试解析 HTTP 响应并不总是合理的，一种情况是返回的 HTTP 状态码不是 200。下面是你如何从响应中获取 HTTP 状态码：

```
fmt.Printf("HTTP status: %s\n", res.Status)
```

如果你不确定 JSON 模式是否稳定，并且预计它有时会返回无效的 JSON，那么你可以

