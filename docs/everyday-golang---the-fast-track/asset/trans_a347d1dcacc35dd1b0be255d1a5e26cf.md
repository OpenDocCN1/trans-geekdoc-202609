
扩展解析代码，使其打印出错误中收到的值。这样，你不仅可以了解解析失败，还能知道失败的原因。

```
err := json.Unmarshal(body, &p)
if err != nil {
    log.Fatalf("unable to parse value: %q, error: %s",
    string(body), err.Error())
}
```

有许多机器人和自动化应用程序会抓取网站并访问 API。为了成为互联网上的好公民，你应该了解公认的规则和标准。

还有一行重要的代码我想重点说明。我在 HTTP 请求的头部设置了 User-Agent。这让远程服务器能够了解接收到的流量类型。某些网站甚至会拒绝空的或通用的 User-Agent 字符串。

```
req.Header.Set("User-Agent", "spacecount-tutorial")
```

对于某些 API，你可能需要使用特定的 User-Agent，或模拟浏览器会传递的值。

了解更多关于 User-Agent 头的信息：Mozilla 上的 User-Agents

如果你决定使用 Go 程序访问 HTML 页面，你应该了解 robots.txt 等其他机制：

robots.txt 文件告诉搜索引擎爬虫哪些页面或文件可以或不可以从你的网站请求。这主要用于避免用请求压垮你的网站；它并不是阻止网页被 Google 收录的机制。

以下是代码提取到自己的函数中然后从 main() 函数调用时的可能样子。

```
package main

import (
    "encoding/json"
    "fmt"
    "io"
    "log"
    "net/http"
)

type people struct {
    Number int `json:"number"`
}

func main() {
    apiURL := "http://api.open-notify.org/astros.json"

    people, err := getAstros(apiURL)
    if err != nil {
        log.Fatal(err)
    }
    fmt.Printf("%d people found in space.\n", people.Number)
}
```

然后我们的函数将改为如下：

```
func getAstros(apiURL string) (people, error) {
    p := people{}

    req, err := http.NewRequest(http.MethodGet, apiURL, nil)
    if err != nil {
        return p, err
    }

    req.Header.Set("User-Agent", "spacecount-tutorial")

    res, err := http.DefaultClient.Do(req)
    if err != nil {
        return p, err
    }

    if res.Body != nil {
        defer res.Body.Close()
    }

    body, err := io.ReadAll(res.Body)
    if err != nil {
        return p, err
    }

    err = json.Unmarshal(body, &p)
    if err != nil {
        return p, err
    }

    return p, nil
}
```

请注意，我们有相同数量的 return 语句，但只有一个 log 语句。我们的代码对他人更有用了，因为并非每个调用者都希望在出现错误时调用 log.Fatal，例如如果服务器返回错误，调用者可能希望重试请求而不是直接退出。

减少行数的另一件事是“内联” if 语句：

```
p := people{}
if err := json.Unmarshal(body, &p); err != nil {
    return p, err
}
```

这使得代码更简洁，但也意味着 err 变量的作用域仅限于 if 语句，不会泄漏到函数的作用域中。

## 从 JSON 中提取额外数据

JSON 中还为每艘飞行器上的每个人都有一个元素或对象。

为 person 元素定义一个结构体：

```
type person struct {
    Name string `json:"name"`
}
```

然后将其添加到你的 people 结构体中：

```
type people struct {
    Number int       `json:"number"`
    Person []person  `json:"people"`
}
```

更新你的 main.go 以打印新的字段：

```
func main() {
    apiURL := "http://api.open-notify.org/astros.json"

    people, err := getAstros(apiURL)
    if err != nil {
        log.Fatal(err)
    }
    fmt.Printf("%d people found in space.\n", people.Number)

    for _, p := range people.Person {
        fmt.Printf("Let's wave to: %s\n", p.Name)
    }
}
```

2021 年 3 月 5 日的结果如下：

```
7 people found in space.
Let's wave to: Sergey Ryzhikov
Let's wave to: Kate Rubins
Let's wave to: Sergey Kud-Sverchkov
Let's wave to: Mike Hopkins
Let's wave to: Victor Glover
Let's wave to: Shannon Walker
Let's wave to: Soichi Noguchi
```

我们现在编写了一些代码来通过 HTTP 获取资源，将其解析为 JSON，处理错误并使其可重用。然后我们通过提取函数来加固代码并使其更有用。

## 第 5 章：编写出色的 CLI 的五种方法

我们正经历命令行界面（CLI）的复兴——从 Node.js 到 Go 再到像 .NET 这样不太流行的语言，每种编程语言都有 CLI，开发者们都喜欢它们。

命令行界面应该使用起来感觉很棒，而不是令人不适或以任何方式令人惊讶。你应该关注最受欢迎的 CLI 使用的风格、用户体验和方法，并从中吸取教训。

CLI（命令行界面）是应用程序的基于文本的界面，易于自动化，操作快速，并且可以与其他 CLI 结合创建工作流。

概念是相通的：几乎每个生产力应用程序都有一个软盘的图片。它做什么？不需要猜测或阅读文档。它是保存按钮。同样，`-v` 表示为此命令打印详细输出。

做得好的 CLI：

- 上手容易
- 恰好足够完成任务
- 能与其他 CLI 互操作（通过管道或文件）
- 不会让用户感到意外

所以以下是五种方法，可以确保你的下一个 CLI 是开发者喜欢使用并会告诉朋友的工具。

### 选择 Go

在阅读一本关于 Go 的书时，我主张使用 Go 编写 CLI，这可能并不令人惊讶，但原因如下。

我更喜欢用 Go 编写的 OpenFaaS CLI，而不是用 JavaScript 和 Node.js 编写的 Serverless Framework Inc CLI：

- 编译为单个静态二进制文件

使用 Go，你可以提供一个包含整个应用程序或 CLI 的单个静态二进制文件，针对你选择的平台。要针对不同的 CPU 或操作系统，只需在构建时传入环境覆盖。与 JavaScript 不同，你必须安装 Node.js，然后从 npm 安装数百或数千个微小的包。

以下是 Linux、Mac、Windows 以及 Raspberry Pi 的二进制文件：

```
GOOS=linux go build -o cli
GOOS=darwin go build -o cli-darwin
GOOS=windows go build -o cli.exe
GOARCH=armv7 GOOS=linux go build -o cli-rpi
```

就是这样——还有更多平台可用，比如 FreeBSD。你不需要安装任何依赖项，最终输出的二进制文件可以非常小。

请参阅电子书的前几章，了解静态二进制文件的深入介绍以及如何支持多种架构。

- 一致的风格

Go 是一种有主见的语言，虽然项目偏好的编辑器可能有所不同——你会遇到一致的样式、格式化和构建工具标准。像 Node.js 这样的东西可能涉及任意数量的“任务运行器”或“转译器”——或语言中更晦涩的变体，如 TypeScript 或 CoffeeScript。

Go 具有一致的风格，并且是经过精心设计以消除歧义的。为什么这很重要？它使开发者能够轻松贡献，而无需花费大量时间学习代码库、工具链或所选风格。截至撰写时，OpenFaaS 的 CLI 有 810 次提交，整个项目有超过 8000 次提交，来自 340 名个人开发者。

- 在每个平台上都快速

Go 在所有平台上都很快速，没有初始延迟。如果你曾经使用过用 Python 或 Node.js 编写的 CLI，那么你可能习惯了每次使用 CLI 时都会出现初始延迟。在像 Raspberry Pi 这样的平台上情况更糟，在那里运行 node hello-world.js 只需 1.5-3.0 秒即可开始运行第一条指令。

- 易于使用 REST API

Go 包含一个直截了当的 http 客户端，并内置支持 xml、json 和二进制格式的工作。还有一个非常好的用于处理 YAML 的库，在 OpenFaaS 中这里使用：`stack.go`

可能有原因使 Node.js 或其他语言更适合你的用例。如果你已经决定用 Go 构建 CLI——那么你可以获得快速、小巧且易于分发的二进制文件的优势。

你知道你可以分发一个安装 Go CLI 的 npm 包吗？我第一次看到 Cloudflare 这样做，我们也为 OpenFaaS CLI 采用了同样的方法 `npm install -g @openfaas/faas-cli`。

代码从 GitHub 发布页面下载 faas-cli 二进制文件的最新版本，然后将其放置在文件系统的正确位置。

### 解析标志和参数

Go 标准库包含一个 `flag` 包，可以在几行代码中用于解析标志或参数。

```
package main

import (
    "flag"
    "fmt"
    "os"
)

func main() {
    var image string
    flag.StringVar(&image, "image", "", "Docker image")
    flag.Parse()

    if len(image) == 0 {
        fmt.Fprintf(os.Stderr, "You must specify a Docker image name")
    }

    fmt.Printf("Your Docker image was: %s", image)
}
```
