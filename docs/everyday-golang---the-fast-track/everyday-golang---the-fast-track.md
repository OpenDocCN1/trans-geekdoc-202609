# Golang 日常快速入门




![](img/0b5c3b498f62579835cf1d543b46de92_0_0.png)
![](img/0b5c3b498f62579835cf1d543b46de92_0_1.png)































![](img/0b5c3b498f62579835cf1d543b46de92_7_0.png)

图 1.1：Go 的新标志

- Go 品牌指南

以下是一些在我脑海中出现的项目，它们完全（或大部分）用 Go 编写：

- Docker - 由 Docker Inc 编写的容器引擎
- Kubernetes - 由 Google 和开源贡献者构建的容器集群系统
- Traefik - 由 Traefik Labs 构建的负载均衡器
- Istio - 用于加密 Kubernetes Pod 之间流量的服务网格
- Consul、Terraform - 由 Hashicorp 构建的基础设施管理工具
- Caddy - 由 Matt Holt 编写的高速 HTTP 服务器
- OpenFaaS - 用于托管你自己的函数的无服务器框架，由我和各种其他贡献者构建

这些只是数十万个出现在 GitHub Go 趋势页面上的项目中的几个。

正如上面所见，Go 在服务器端项目中非常流行，但它也因二进制文件可以静态链接而非常流行于编写命令行界面（CLI）。

静态链接的 Go 二进制文件既快速又小巧，且不需要额外的运行时，使其成为非常受欢迎的选择。

我个人对 Go 的亮点是：

- 可移植性 - 静态编译便于分发
- 跨编译 - 能够使用单个命令（go build）为 Linux、Windows、macOS 操作系统（OS）和 Arm 计算机构建二进制文件
- 并发模型 - Go 具有内置的并发机制，使其非常适合大小任务
- 生态系统 - 了解 Go 意味着能够为几乎任何其他开源 Go 项目或产品做出贡献
- 工具 - Go 包含自己的单元测试运行器和分析器，两者都简单易用
- 意见 - Go 对格式、风格和类型有强烈的意见，使得在代码库之间移动变得容易

除此之外，Go 在其标准库或“stdlib”中拥有令人印象深刻的一套包。在 JavaScript、Ruby 或 Java 等编程语言中，许多有用的包和实用工具需要单独安装。

- crypto - X.509 证书和加密库
- compress - 处理 zip 文件和归档
- http - 非常强大且简单的 HTTP 客户端和服务器包，包括反向代理等
- net - 直接使用套接字、URL 和 DNS
- encoding/json - 直接处理 JSON 文件
- text/template - 用于在文件中替换标记并生成文本和 HTML 的强大模板引擎
- os - 使用低级 OS 原语

你可以在这里找到完整的包列表。

在接下来的几章中，我们将探索上述一些亮点并解决各种实际问题。即使你是一名经验丰富的 Go 开发者，我也建议你完成每个练习，因为即使在 11 年后，我自己仍在学习新的方法和风格。

Go 本身是一个非常稳定的语言，很少出现弃用或破坏性更改，因此 Go 的最新版本与本材料中提到的版本关系不大。内容会根据重大更改定期更新。

## 开始使用 Go

安装 Go 有三种方法。

- 使用系统包安装 Go - 例如 msi（Windows）或 pkg（macOS）
- 使用包管理器安装 Go - 例如 apt-get（Debian）、pacman（Arch Linux）、brew（macOS）
- 下载 tar 归档并解压到指定位置（仅限 Linux）

如果你是新用户并且运行在 Windows 或 macOS 上，那么请继续使用第一个选项并从主页下载 Go。版本经常变化，因此请下载最新稳定版。

如果你喜欢使用包管理器，你应该知道他们提供的版本通常落后。你可能正在安装一个非常旧的 Go 版本，一些功能可能不可用。

### Windows 用户说明

虽然 Go 命令可以在 cmd.exe 和 PowerShell 中运行，但一些示例命令需要 UNIX 风格的 shell，而该 shell 在 macOS 和 Linux 主机上可用。

为了方便使用，建议你使用 Windows Subsystem for Linux（WSL）尝试内容，如果你的系统可用。否则，请使用 Git Bash。

Git Bash 提供了一个终端，你可以在其中运行 bash，访问 git 命令以及各种其他 UNIX 风格的命令，如 export、ls、mkdir 和 curl。

### Linux 上的直接安装

作为 Linux 用户，我经常需要在服务器、Docker 镜像或我的 Raspberry Pi 上安装 Go。我的 arkade 项目提供了一种快速高效的方式来下载最新版本，而无需构造 curl 语句或运行 tar。

从以下地址下载并安装 arkade：https://github.com/alexellis/arkade

然后运行：

```
sudo arkade system install go

Installing Go to /usr/local/
Installing version: go1.23.4 for: amd64
Downloading from: https://go.dev/dl/go1.23.4.linux-amd64.tar.gz
142.05 MiB / 142.05 MiB [--------------------------------------------------] 100.00%
Downloaded to: /tmp/go1.23.4.linux-amd64.tar.gz
Unpacking Go to: /usr/local/go

export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin
export GOPATH=$HOME/go/
```



```
total 0
drwxr-xr-x  3 alex  staff   96 12 Dec 09:04 alexellis
drwxr-xr-x  3 alex  staff   96 12 Dec 09:04 beorn7
drwxr-xr-x  3 alex  staff   96 12 Dec 09:04 golang
drwxr-xr-x  3 alex  staff   96 12 Dec 09:04 gorilla
drwxr-xr-x  3 alex  staff   96 12 Dec 09:04 matttproud
drwxr-xr-x  6 alex  staff  192 12 Dec 09:04 prometheus
```

hash-browns 的二进制文件将位于 `$GOPATH/bin/` 目录中：

```
$ ls $GOPATH/bin/

$ $GOPATH/bin/hash-browns

hash-browns by Alex Ellis
Version:      Commit:
2021/12/12 09:05:24 Listening on port: 8080
```

你可能还会在项目的 README 文件中看到 `go get` 命令。从 Go 1.17 开始，`go get` 命令将不再用于安装二进制文件。它仍然可以用于获取单个模块以供项目内使用。例如，hash-browns 项目使用了 Prometheus SDK，所以如果你从头开始一个项目，你可能会输入 `go get` 或 `go get github.com/prometheus/client_golang` 或 `go get github.com/prometheus/client_golang@v0.8.0`。

注意：你在 GitHub 上找到的一些项目可能还没有迁移到 Go modules。因此你会看到这样的一个看起来比较奇怪的版本号出现在你的 `go.mod` 文件中：`golang.org/x/sync v0.0.0-20210220032951-036812b2e83c`。字符串的最后部分是缩短的 Git 提交 SHA `036812b2e83c`。

由于 Go 1.17 默认启用 Go modules（`GO111MODULE=on`），本书的其余部分将假定你也已启用它。

注意：在较旧的 Go 版本中，当 `GO111MODULE` 被设置为 `off` 时，代码会被下载到 `$GOPATH/src/` 而不是 `$GOPATH/pkg`。在未来的 Go 版本中，不使用 Go modules 的构建可能会被完全禁用。

### Vendoring 与 Go modules

在 Go 生态系统的早期，你的程序所使用的任何依赖的源代码都被放在一个 `vendor` 文件夹中。`vendor` 文件夹会与你的应用程序代码一起提交，为你提供构建应用程序所需的任何内容的副本和备份。

在前面的例子 `hash-browns` 中，需要用到 `github.com/prometheus/procfs` 模块，它会被克隆到源代码树中，如下所示：

```
$GOPATH/src/github.com/alexellis/hash-browns
$GOPATH/src/github.com/alexellis/hash-browns/vendor/github.com/prometheus/procfs
```

各种诸如 `dep` 之类的 vendoring 工具被用来下载和管理这些依赖。这些工具现在已被弃用。一个文件会指定需要哪些包，另一个“锁文件”会指定版本。因此你随时可以 `rm -rf` `vendor` 文件夹并运行类似 `dep ensure` 的命令，以获取所有各种文件的崭新副本并恢复。

在 Go 1.13 中，引入了 Go modules 的概念，它在很大程度上与 vendoring 相似，但有一个重大变化。依赖的源代码不再需要被克隆并与你的应用程序一起提交到源代码控制中。OpenFaaS 的 40+ 个项目的过渡相对顺利，只有少数几个项目带来了麻烦，需要推迟处理。

Go modules 的另一个变化是能够在 `$GOPATH/src` 约定之外编译源代码。例如，你可以将源代码放在 `$HOME/dev/` 而不是 `$HOME/go/src/` 或你设置的其他位置。

每当你创建新的 Go 项目时，最好先运行 `go mod init`。如果你的代码位于传统的 GOPATH 结构内，那么它的名称将被自动确定；如果不是，你可以将其作为参数传入。

对比以下示例：

```
export GH_USERNAME=alexellis

$ mkdir -p $GOPATH/src/github.com/$GH_USERNAME/hash-gen
$ cd $GOPATH/src/github.com/$GH_USERNAME/hash-gen
$ go mod init
go: creating new go.mod: module github.com/alexellis/hash-gen

$ cat go.mod
module github.com/alexellis/hash-gen

go 1.16
```

而在 GOPATH 之外运行时：

```
$ mkdir /tmp/hash-gen
$ cd /tmp/hash-gen
$ go mod init

go: cannot determine module path for source directory /tmp/hash-gen (outside GOPATH, module path must be specified)

Example usage:
    'go mod init example.com/m' to initialize a v0 or v1 module
    'go mod init example.com/m/v2' to initialize a v2 module

Run 'go help mod init' for more information.
```

请尝试以下任一方式代替：

```
$ go mod init hash-gen
$ go mod init github.com/alexellis/hash-gen
```

也可以同时使用 Go modules 和 vendoring：

```
$ cd /tmp/
$ git clone https://github.com/alexellis/hash-browns
$ cd hash-browns
$ rm -rf vendor
$ go mod vendor
$ ls vendor/
```

现在可以看到 `vendor` 文件夹已经被创建。

你可以通过向 `go build` 命令添加 `-mod vendor` 参数，让 Go 使用 `vendor` 文件夹进行构建，而不是使用位于 `$GOPATH/pkg` 的本地包缓存。

```
$ go build -mod vendor
```

那么你应该使用哪种方法呢？

Vendoring 的优势在于将所有源代码和依赖保存在一个地方；它也不需要下载任何东西来执行构建。对于某些项目，例如 Kubernetes 控制器，这意味着节省时间和带宽。如果你有任何私有依赖，vendoring 可能是最简单的选择，尤其是在容器或 CI 流水线中进行构建时。

不进行 vendoring 而直接使用 modules 似乎是一种趋势，许多项目都删除了它们的 `vendor` 文件夹。这样做的一个优势是让代码审查更容易，因为在拉取请求或提交中变更的文件要少得多。处理私有 Go modules 可能会引起争议，所以提醒你留意。

另请参阅：Go modules 参考文档

## 第 2 章

### 创建你的第一个 Go 程序

你可以凭记忆创建一个 Go 程序，但我认为使用像 Visual Studio Code 这样的 IDE 更有用。Visual Studio Code 有许多可以安装的插件，用于格式化你的代码、整理代码，并为你导入的模块或包添加路径。它的自动化程度不如 JetBrains GoLand 这样的付费 IDE，但快速且免费。

创建一个文件夹 `first-go`，然后将以下内容保存为 `main.go`：

```
package main

func main() {

}
```

现在你有两种运行该程序的方法。

- 1) 运行 `go run main.go`
- 2) 运行 `go build`，然后运行生成的二进制文件 `./first-go`

现在使用 `fmt.Printf` 打印一条控制台语句。这将在文件顶部导入 `fmt` 包，VSCode 会自动运行一些 Go 插件来为你更新 `main.go` 文件。

```
package main

import (
    "fmt"
    "os"
)

func main() {
    name := os.Getenv("USER")
    fmt.Printf("Well done %s for having your first Go\n", name)
}
```

VSCode 运行的程序之一是 `gofmt`，这体现了 Go 语言鲜明的主张，让你无需学习新约定就能在不同代码库之间切换。你可以使用 `gofmt -w -s main.go` 对文本文件运行它。

注意使用了 `os.Getenv` 调用来从 `USER` 环境变量中查找你的用户名。

Windows 用户注意：尝试将 “USER” 替换为 “USERNAME”

现在，再次运行该程序，你应该会看到如上所述的输出。

![](img/0b5c3b498f62579835cf1d543b46de92_14_0.png)

图 2.1：Visual Studio Code 和我们的 first-go 应用的截图

### 添加外部依赖

虽然标准库非常庞大，但你很可能需要使用外部依赖。Go 中的依赖以源代码形式提供，可以链接到你的程序，这与 C# 或 Java 不同，后者下载的是编译后的资产（DLL 或 JAR）。因此，你通常会发现 Go 包会带有一个路径，标明它可以通过 git 下载。

你可以使用 Webhook 从第三方 API（如 GitHub.com 或 Stripe）接收事件。大多数情况下，Webhook 在头部会附带一个摘要，你可以用它来验证消息是否被篡改。

HMAC 使用发送方和接收方事先共享的对称密钥。发送方想要传输消息时会生成一个哈希——该数据会与负载一起发送。然后接收方使用共享密钥再次对负载进行签名。如果哈希匹配，则假定该负载来自发送方。

引用自 alexellis/hmac

让我们使用我的库来为我们自己的消息创建摘要，然后演示之后如何验证它。你当然可以直接使用标准库，但这个练习的重点是展示：如何引用外部依赖。你还可以浏览依赖的代码，了解如何定义你自己的库。

首先，我们应该为应用程序初始化一个 Go module。Go modules 文件 `go.mod` 列出了我们希望程序依赖的外部依赖项。

```
export GH_USERNAME="alexellis"
mkdir -p $GOPATH/src/github.com/$GH_USERNAME/validate-hmac/
cd $GOPATH/src/github.com/$GH_USERNAME/validate-hmac/

go mod init
go: creating new go.mod: module github.com/alexellis/validate-hmac
```

查看 `go.mod` 的内容：

github.com/alexellis/hmac/v2 v2.0.0/go.mod h1:07hZZgTfh5fp5+vAamzodZPlbw+aQK+n...EvL0=

go.sum 会为后续使用锁定模块的特定版本。

现在让我们使用库来验证收到的摘要：

```
package main

import (
    "fmt"
    "crypto/sha256"

    hmac "github.com/alexellis/hmac/v2"
)

func main() {

    input := []byte(`input message from API`)
    secret := []byte(`so secret`)

    digest := hmac.Sign(input, secret, sha256.New)
    fmt.Printf("Digest: %x\n", digest)

    err := hmac.Validate(input, fmt.Sprintf("sha256=%x", digest), string(secret))
    if err != nil {
        panic(err)
    }

    fmt.Printf("Digest validated.\n")
}
```

使用 go run main.go 运行程序，你会看到它按预期通过。

### 使用标志

Go 有一个内置的标志解析库。我们将在后面的章节中探索一个替代库 Cobra。我在多个项目中使用过 Cobra，但即使现在，我总是从最简单可行的方法开始。然后，如果有必要，我会转向比标准库 flags 包更复杂但功能更强大的库。

```
export GH_USERNAME="alexellis"
mkdir -p $GOPATH/src/github.com/$GH_USERNAME/validate-hmac-flags/
cd $GOPATH/src/github.com/$GH_USERNAME/validate-hmac-flags/

go mod init
go: creating new go.mod: module github.com/alexellis/validate-hmac-flags
```

在之前的示例中，我们通过硬编码输入和密钥来创建哈希，但这对我们的用户来说并不实用。让我们改用标志，这样我们就可以运行：

```
go run main.go
-message="my message" \
-secret="terces os"
```

将解决方案调整为使用 flag.StringVar 定义每个标志，然后跟上 flag.Parse：

```
$ go run main.go -message="my message"
panic: --secret is required

goroutine 1 [running]:
main.main()
    /home/alex/go/src/github.com/alexellis/validate-hmac-flags/main.go:20 +0x3ed
exit status 2
```

但我们可以通过将 secret 设置为空白来绕过这个问题，那么你如何处理这种情况？

```
if len(strings.TrimSpace(secretVar)) == 0 {
    panic("--secret is required")
}
```

我们只需用 strings.TrimSpace 包裹该值，它会移除任何空白并为我们处理这种情况。

这是完整的示例：

```
package main

import (
    "flag"
    "fmt"
    "strings"

    "github.com/alexellis/hmac"
)

func main() {
    var inputVar string
    var secretVar string

    flag.StringVar(&inputVar, "message", "", "message to create a digest from")
    flag.StringVar(&secretVar, "secret", "", "secret for the digest")
    flag.Parse()

    if len(strings.TrimSpace(secretVar)) == 0 {
        panic("--secret is required")
    }

    fmt.Printf("Computing hash for: %q\nSecret: %q\n", inputVar, secretVar)

    digest := hmac.Sign([]byte(inputVar), []byte(secretVar))
    fmt.Printf("Digest: %x\n", digest)
}
```

作为额外练习，为什么不添加一个模式，让你的 CLI 既可用于生成哈希也可用于验证哈希？

你可以添加一个使用 flag.BoolVar 的标志，例如 -generate=true/false，或者像 -mode=generate/validate 这样的字符串模式。

### 定义单独的包或库

到目前为止，我们一直在一个名为 main 的单个包中编写代码。main 包是使程序独立可运行所必需的，然而有时你会想编写一个库，以便代码能在程序之间共享。

你可能也有一个包含 main 包和一个用于代码组织的额外命名包的项目。包可以单独进行测试。

通常，以大写字母开头变量、函数或结构体意味着它将对包外的其他使用者可用。

我们将创建一个包，它可以执行与 dir 或 ls shell 命令类似的任务。

创建一个新项目：

```
$ export GH_USERNAME="alexellis"
$ mkdir -p $GOPATH/src/github.com/$GH_USERNAME/multiple-packages/
$ cd $GOPATH/src/github.com/$GH_USERNAME/multiple-packages/

$ go mod init
go: creating new go.mod: module github.com/alexellis/multiple-packages
```

现在为包创建一个名为 cmd 的文件夹：

```
$ mkdir -p $GOPATH/src/github.com/$GH_USERNAME/multiple-packages/cmd
```

然后在其中创建 ls.go：

```
package cmd
```

现在你已经定义了一个名为 cmd 的包，但它没有任何导出的函数或结构体。

```
package cmd

func ExecuteLs(path string) (string, error) {
    return "", nil
}
```

然后该命令可以由新的 main 包使用路径 github.com/alexellis/multiple-packages/cmd 导入。在某些情况下，像我们之前使用的 HMAC 库那样，项目不需要自己的 main 入口点，因为它只会被第三方作为函数消费。

在根文件夹中创建 main.go：

```
package main

import (
    "fmt"
    "os"

    "github.com/alexellis/multiple-packages/cmd"
)

func main() {
    wd, err := os.Getwd()
    if err != nil {
        fmt.Fprintf(os.Stderr, "unable to get working directory: %s",
            err.Error())
    }
}
```
```
res, err := cmd.ExecuteLs(wd)
if err != nil {
    fmt.Fprintf(os.Stderr, "unable list files in %s, error: %s",
        wd, err.Error())
}

fmt.Printf("%s\n", res)
}
```

现在用其余代码填充 ls.go 程序：

```
package cmd

import (
    "fmt"
    "os"
)

func ExecuteLs(path string) (string, error) {
    entries, err := os.ReadDir(path)
    if err != nil {
        return "", err
    }
    output := fmt.Sprintf("Files in %s\n", path)
    output += "Name\tDirectory\t\n"

    for _, e := range entries {
        output += fmt.Sprintf("%s\t%v\n", e.Name(), e.IsDir())
    }

    return output, nil
}
```

你知道吗？单元测试与源代码写在同一个包中，因此如果 main 有测试，你会将它们放在根文件夹中，而对 cmd 包的任何测试都会放在 cmd/ 文件夹内。在后面的章节中，你将学习 Go 中的单元测试。

然后试试看：

```
$ go run .
Files in /Users/alex/src/github.com/alexellis/multiple-packages
Name    Directory
cmd     true
go.mod  false
main.go false
multiple-packages      false
```

如果你想在系统上使用此程序，可以将其复制到你的 $PATH 变量中，或运行 go install，使其放置在 $GOPATH/bin/ 中

```
$ export GH_USERNAME="alexellis"
$ cd $GOPATH/src/github.com/$GH_USERNAME/multiple-packages
$ go install
$ cd /tmp/
```
```
$ multiple-packages
Files in /tmp
Name    Directory
...
```

如果在这里收到“未找到”错误，则需要在系统上将 $GOPATH/bin/ 添加到你的 $PATH 变量中。

更进一步：

- 如果你想将文本对齐到表格中，为什么不试试 TabWriter？
- 你将如何使用标志和包来添加其他命令并根据用户的输入执行它们？

Derek 是一个我编写的 GitHub 机器人，旨在更轻松地自动化开源维护并通过评论将权限委托给其他贡献者。Derek 是多包的一个很好的例子，为什么不阅读源代码，看看他的包是如何在 main.go 文件中导出和使用的呢。

## 第3章

### 为不同操作系统交叉编译

在上一章中，我们构建了一个简单的 Go 程序，它使用环境变量打印输出，但我们生成的二进制文件只能在相同的操作系统和 CPU 架构上运行。

如果你有另一台具有相同操作系统的计算机，可以将二进制文件复制到该计算机上并在没有任何更改的情况下运行。如果你在 Mac 上使用，但想在 Raspberry Pi 或 Windows 桌面上运行程序，你需要使用 Go 的内置交叉编译选项来生成不同的二进制文件。

你需要了解目标操作系统和目标 CPU 架构。

Go 支持多种操作系统，不过这些是最常用的：

- Windows
- MacOS
- Linux

Go 程序也需要为特定的 CPU 架构和版本构建。大多数时候这是一个可以避免的细节，但如果你希望你的程序在像 Raspberry Pi 或 AWS Graviton 服务器这样的 Arm 处理器上运行，你也需要记住这一点。

- 常规 PC 和云，涵盖 Intel 和 AMD CPU - x86_64
- 像 Raspberry Pi 这样的 32 位 Arm 设备称为 armhf、armv7 或 armv6l
- 64 位 Arm 服务器和设备称为 arm64 或 aarch64

如果你不指定任何选项，你的二进制文件将为你正在使用的计算机构建，否则你可以自定义选项和输出文件名。

### Go 构建参数

这是如何为 Windows、Linux 和 MacOS 构建我们的 first-go 程序：

```
GOOS=linux go build -o first-go
GOOS=darwin go build -o first-go-darwin
GOOS=windows go build -o first-go.exe
```

要为 Arm CPU 构建，只需添加以下内容：

```
GOARCH=arm GOOS=linux go build -o first-go-arm
GOARCH=arm64 GOOS=linux go build -o first-go-arm64
```

如果你想调试二进制文件的问题，可以使用 bash 命令 file 来查看它是如何构建的：

```
file first-go
first-go: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically
linked, not stripped
```




### CGO 与可移植性

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

### 从 JSON 中提取额外数据

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



根据我在企业开发领域的经验——平均而言，一名 C# 开发者会自己写一个字符串解析器，然后创建一个作为入口点的 ConsoleApp，再创建一个用于解析的 DLL 库，以及另一个用于应用程序代码的库。

与上面代码片段相比，Go 显得朴实无华。你可以用单个文件编译成一个微小的二进制文件，并且只使用标准库。就这么简单。

我建议你在每个新 CLI 中先从 `flags` 包开始，只有在达到其限制时，再考虑迁移到像 Cobra 这样更模块化的方案。

Cobra 被 Docker、Kubernetes 和 OpenFaaS 项目使用，这意味着处理器/命令可以存在于单独的文件或模块中。它也让为每个命令编写文档变得非常简单。查看这里的代码，了解我们“list functions”命令的实现。

使用“cobra”的另一个优势是它具有动词名词语法。这在我们设计用户体验时帮助很大。我们从一种有些突兀的体验转变为更流畅的体验：

```text
faas-cli -deploy \
    -image=functions/alpine \
    -name=cat \
    -fprocess=/bin/cat
```

到：

```text
faas-cli deploy \
    --image=functions/alpine \
    --name=cat \
    --fprocess=/bin/cat
```

-deploy 标志变成了名为 deploy 的子命令，并允许我们将代码移至其自己的包中。Cobra 会处理你想要添加的所有子命令的解析和帮助信息。

我们还根据关于管理多个函数的反馈创建了 YAML 格式，这使得 CLI 命令可以简单到：

```text
faas deploy -f stack.yml
```

或

```text
faas deploy -f \
    https://raw.githubusercontent.com/openfaas/faas-cli/master/stack.yml
```

> 提示：仔细挑选动词/命令，并请他人确认它们是否合理。如果某处让你感到不协调，那它很可能就是错的。这可能需要多次迭代，但你的目标是实现直观的体验。

### 自动化一切

使用像 GitHub Actions 这样免费且公开的 CI 平台创建自动化构建，以便贡献者或协作者知道他们的更改是否可以集成。

使用 GitHub Releases 来跟踪项目中的更改和里程碑。你可以在 GitHub 上设置一个构建后操作，以便为你目标的每个平台自动发布二进制产物。

如果有 Docker 镜像——在推送新版本产物时同时将其发布到 Docker Store。像 GitHub 这样的工具可以混淆凭据和密钥，以使其不会出现在日志中。

Go 项目在 Docker 中构建非常容易。以下是一个来自 inlets-operator 的示例，它是一个 Kubernetes 控制器，用于为你希望在私有集群中公开的 Kubernetes 服务创建隧道服务器：

- Dockerfile inlets-operator

确保使用多阶段构建，以便交付精简的镜像。

对于我维护的各个项目，我们倾向于将构建拆分为“CI”或“test”操作：

- ci-only.yaml for the inlets-operator

以及一个发布操作：

- publish.yaml for the inlets-operator

虽然入门很容易——你并不希望每次发布都在自己的机器上构建 3-5 个二进制文件，然后每次需要更新时再上传到网页表单。

### 与包管理器集成

如果你希望让目标受众能够轻松获取你的 CLI，那么你需要尽可能简化这一过程。这意味着要与包管理器集成。

- brew - 如果你的目标受众是开发者，那么其中很大一部分可能使用 Mac。brew 是一个包管理器，这意味着大多数 CLI 只需一个命令即可安装，例如：`brew install faas`。
- Linux - 对于 Linux 存在许多包管理器，因此我选择构建一个下载工具，该工具可以以 root 或普通用户身份运行。要获取 OpenFaaS CLI：`curl -sL https://cli.openfaas.com | sh` 或获取 Docker：`curl -sL https://get.docker.com | sh`。
- Windows - Windows 用户有多种 shell 可选，包括 Git Bash（我偏好的选项）和 Windows 子系统 Linux。WSL 可以使用 Linux curl 工具，但如果你面向的是“点一下就好”的开发者，你可能需要创建一个“双击”安装程序。

无论你做什么——确保它是自动化的，并评估你支持的每个包管理器。你有时间维护集成吗？它是由项目提供还是由社区提供？如果它坏了怎么办？例如——我们维护了一份关于如何升级我们的 brew formula 的指南。

提示：确保所选包的更新/发布周期能够匹配你的项目节奏。虽然包管理器被视为最佳实践，但在那里找到的应用版本可能会很快过时。使用 GitHub 项目的发布页面通过 HTTPS 直接下载可能是最简单、最方便的方法。

你还可以提供自动更新或帮助信息，告诉用户如何保持最新。以下是一个来自 inletsctl 的示例，它是一个用于创建临时隧道服务器的开源工具。

```text
inletsctl update
You can update inletsctl with the following:

# For Linux/MacOS:
curl -sLfs https://inletsctl.inlets.dev | sudo sh

# For Windows (using Git Bash)
curl -sLfs https://inletsctl.inlets.dev | sh

# Or download from GitHub: https://github.com/inlets/inletsctl/releases

Thanks for using inletsctl!
```

faas-cli 有代码可以告知你版本是否已过时，欢迎浏览仓库查看其工作原理。

```text
faas-cli version
___       ____   ____
/ _ \ ___ / ___| |  _ \ 
| | | / _ \___ \ | | | |
| |_| | (_) |__) || |_| |
 \___/ \___/____/ |____/

|_|

CLI:
  commit:  6b5e7a14a598527063c7c05fb4187739b6eb6d38
  version: 0.13.6
Your faas-cli version (0.13.6) may be out of date. Version: 0.13.9 is now available on GitHub.
```

### 接受贡献并收集反馈

提供一种简单的方式让人们提供反馈和贡献。CLI 应该为其操作者设计——因此要让他们轻松提交代码更改或建议。

用户反馈至关重要，但在运营开源软件项目时，我经常听到人们难以理解自己的软件是否以及如何被使用。

基本反馈可以从 GitHub 或 brew 的下载统计中收集。一些关键项目已开始使用分析平台自动收集使用数据——例如：brew、Visual Studio Code、Atom 以及 Docker for Mac/Windows。如果你选择这条路线，请确保提供隐私政策并遵守任何可能的数据保护法规。

我们曾考虑使用 Google Analytics 来收集 OpenFaaS CLI 使用信息，但从未实施。你可以在 issue #108 中阅读更多内容。它将向我们展示：

- 使用了哪些命令
- 使用了哪些编程语言函数
- 操作系统 / CLI 版本 / 世界各地的位置

即使你决定不在 CLI 中添加分析，你仍然可以收集反馈，无论你的工具是用于内部私有工作，还是开源且自由可用。

### 现在，用 Go 编写你的 CLI

用 Go 构建下一个 CLI 令人惊艳的原因有很多。从编译和执行速度，到内置或高质量包的可用性，再到自动化的便捷性。

如果你已有 CLI，并希望将其提升到下一个水平，可以查看我维护的几个 CLI，它们是在过去 5-6 年的经验和教训中构建起来的：

- faas-cli - 用于创建、部署和管理无服务器函数的 OpenFaaS CLI
- arkade - Kubernetes 的开源市场和工具下载器

即使你的 CLI 仅在工作中用于内部使用，也值得 over the Internet，然后解析 JSON 响应到一个结构体中。

那么我们该如何测试用 Go 编写的代码呢？Go 自带的测试运行器能为我们提供什么？它又提出了哪些观点？

#### 测试观点

就像 Go 对格式化、命名和包布局有强烈的观点和约定一样，它对单元测试也有同样的观点。

Go 实际上有自己的内置测试命令 `go test` 和一个 `testing` 包，二者结合提供了简洁但完整的测试体验。标准工具链还包括基准测试 `go test -bench` 和基于语句的代码覆盖率 `go test -cover`，类似于 [NCover](https://www.ndepend.com/)（.NET）或 [Istanbul](https://istanbul.js.org/)（Node.js）。

如果你从 Ruby、Java 或 .NET 等语言转向 Go，你可能会惊讶地发现没有断言库，而且某些书籍甚至极力反对使用它们。

对于 JavaScript 开发者来说，以 BDD 风格编写 Sum 方法的测试看起来会像这样：

```javascript
var expect = require('expect');

describe('Calculator', function() {
  describe('#multiply()', function() {
    it('should return -10 when 10 is multiplied by -1', function() {
      const calc = new Calculator()
      expect(calc.multiply(10, -1)).to.eql(-10)
    });
  });
});
```

上述的替代方案可能是使用 Java / C# 世界中的 `assert.AreEqual()` 类型的方法。Go 开发者不采用这种方法，如果你想看一些 Go 单元测试的示例，可以查看 OpenFaaS CLI 中解析 YAML 文件的这个测试：[stack_test.go](#)。

在 Go 中，相同的测试会更像这样：

```go
func TestMultiply_ForANegativeNumber(t *testing.T) {
    c := Calculator{}
    want := -10
    got := c.Multiply(10, -1)

    if want != got {
```

```go
    t.Fatalf("want %d, but got %d", want, got)
    }
}
```

在某些语言中，额外的库提供了对注解的支持，允许测试针对不同的值运行。

以下是来自 NUnit 的示例：

```
[Test]
[TestCase("hello@example.com")]
[TestCase("hello+plus@example.com")]
[TestCase("hello.with.dots@example.com")]
public void ValidateEmail_supports_real_emails(string emailAddress)
{
    // ARRANGE
    var sut = new EmailValidator();

    // ACT
    var result = sut.ValidateEmail(emailAddress);

    // ASSERT
    Assert.That(result.IsValid, Is.True);
}
```

在 Go 中，这可以通过测试表来实现：

```go
func TestMultiply_VariousNumbers(t *testing.T) {
    c := Calculator{}

    cases := []struct {
        a int
        b int
        want int
        name string
    }{
        {-10, 1, -10, "negative case"},
        {10, 1, 10, "positive case"},
        {10, 0, 0, "zero case"},
    }

    for _, tc := range cases {
        t.Run(tc.name, func(t *testing.T) {
            want := tc.want
            got := c.Multiply(tc.a, tc.b)

            if want != got {
                t.Fatalf("want %d, but got %d", want, got)
            }
        })
    }
}
```

如果你想看一个更复杂的例子，可以参考 OpenFaaS CLI 中根据多个变量确定正确选择的情况：`priority_test.go`

当使用断言而不是纯 Go 时：

- 测试感觉像是使用不同的语言编写的（例如 RSpec/Mocha）
- 错误可能晦涩难懂，例如 “assert: 0 == 1”
- 可能生成大量的堆栈跟踪
- 测试在第一个断言失败后停止执行，从而掩盖了失败模式

有一些第三方库可以复制 RSpec 或 Assert 的感觉。另请参阅 [stretchr/testify](https://github.com/stretchr/testify)。

免责声明：我希望你能对 Go 的方法感到舒适，即使你不习惯它。请帮我们一个忙，不要急于为 Go 寻找最近的 BDD 库。为什么？因为 Go 最强大的特性之一就是一致性，任何 Go 开发者都应该能够在不学习新库和新风格的情况下接手另一个 Go 代码库。

### 测试 Sum 方法

创建练习文件夹：

```bash
export GH_USERNAME="alexellis"
mkdir -p $GOPATH/src/github.com/$GH_USERNAME/sum-testing
cd $GOPATH/src/github.com/$GH_USERNAME/sum-testing
```

这里有一个我们想要在 main 包中测试的方法示例。我们定义了一个名为 Sum 的导出函数，它接收两个整数并将它们相加。

保存 `main.go`：

```go
package main

import "fmt"

func sum(x int, y int) int {
    // This code has a bug that adds 1
    return x + y + 1
}

func main() {
    x := 5
    y := 5
    fmt.Printf("%d + %d = %d\n", x, y, sum(x, y))
}
```

尝试运行应用程序：

```bash
go run main.go
5 + 5 = 11
```

注意存在一个 bug，我们需要对这段代码进行单元测试。

我们需要在单独的文件中编写单元测试，这通常与被测试的代码在同一个包和文件夹中，但不一定如此。保持测试与代码在一起的原因是有用的，因为：

- 它们可以作为单个包导入
- 这意味着你可以在不使其公开的情况下对私有方法进行单元测试

保存 `main_test.go`：

```go
package main

import "testing"

func Test_sum(t *testing.T) {
    x := 5
    y := 5

    want := 10
    got := sum(x, y)
    if want != got {
        t.Logf("Testing a sum of: %d %d", x, y)
        t.Errorf("Sum was incorrect want: %d, but got: %d", want, got)
    }
}
```

然后运行 `go test ./` 来运行当前包中的所有测试：

```
go test ./

--- FAIL: Test_sum (0.00s)
    /home/alex/go/src/github.com/alexellis/sum-testing/main_test.go:12: Testing a sum of: 5 5
    /home/alex/go/src/github.com/alexellis/sum-testing/main_test.go:13: Sum was incorrect
      want: 10, but got: 11
```

注意单元测试的以下几点：

- 测试方法的唯一参数是：`t *testing.T`
- 它以 Test 开头，后跟一个单词或短语，可以使用下划线分隔，或是被测试的函数。
- `t` 变量用于发出失败信号。
- `t.Log` 可用于为任何测试提供调试信息
- 文件必须保存为 `something_test.go` 格式的文件，例如：`addition_test.go`

让我们修复测试，编辑 sum 中的代码，使其不再向任何数字添加多余的 1，然后再次运行测试：

```
go test ./
ok      github.com/alexellis/sum-testing    0.001s
```

启动包测试有两种方式。这些方法适用于单元测试和集成测试 alike。

1. 在与测试相同的目录中：

```
go test
```

或指定路径：

```
go test ./pkg/parser
```

*这会选取匹配 `packagename_test.go` 的任何文件*

或

2. 通过完全限定包名

```
go test github.com/alexellis/golangbasics1
```

你可以从任何文件夹运行它。

你可以通过使用唯一名称添加额外的测试。

```go
package main

import "testing"

func Test_sum_odd_numbers(t *testing.T) {
```

```go
{1, 1, 2},
{1, 2, 3},
{2, 2, 4},
{5, 2, 7},
}

for _, table := range tables {
    got := Sum(table.x, table.y)
    if got != table.want {
        t.Errorf("Sum of (%d+%d) was incorrect, got: %d, want: %d.",
            table.x, table.y, got, table.want)
    }
}
}
```

如果你想触发错误使测试失败，则将 Sum 函数改为返回 x * y。

```text
$ go test -v
=== RUN   Test_sum
--- FAIL: Test_sum (0.00s)
    table_test.go:19: Sum of (1+1) was incorrect, got: 1, want: 2.
    table_test.go:19: Sum of (1+2) was incorrect, got: 2, want: 3.
    table_test.go:19: Sum of (5+2) was incorrect, got: 10, want: 7.
FAIL
exit status 1
FAIL    github.com/alexellis/t6 0.013s
```

何时应该使用测试表？我的观点是在你有足够多的单个单元测试重复，以至于难以维护时。或许在 2-3 个非常相似的测试之后，你可能想要花 10 分钟将它们全部转换为测试表。当测试存在重复时，它们可以在表中更易于维护。有利有弊，所以请逐案权衡。

### “go test” 的小技巧

在本节中我们将探索 `go test` 带来的几个小技巧。然后我们将把迄今为止学到的所有内容放在一个更大的示例中，在其中隔离一个依赖。

### 语句覆盖

`go test` 工具内置了语句代码覆盖率。要尝试使用我们上面的示例，输入：

```text
$ go test -cover
PASS
coverage: 50.0% of statements
ok      github.com/alexellis/golangbasics1  0.009s
```

高语句覆盖率比低覆盖率或无覆盖率更好，但指标可能具有误导性。我们需要确保不仅执行语句，还要验证行为和输出值，并在出现差异时引发错误。如果从之前的测试中删除 “if” 语句，它仍会保留 50% 的测试覆盖率，但会失去验证 “Sum” 方法行为的实用性。

### 生成 HTML 覆盖率报告

如果你使用以下两个命令，你可以可视化程序的哪些部分已被测试覆盖，哪些语句缺乏覆盖：

```
go test -cover -coverprofile=c.out
go tool cover -html=c.out -o coverage.html
```

现在你可以在网页浏览器中打开 coverage.html。

### 基准测试你的代码

基准测试是 go test 工作流程的另一个部分，对高级用例很有用。

在以下从标准库复制的代码中，使用 bcrypt 生成哈希。

```go
package main

import (
    "bytes"
    "crypto/aes"
    "crypto/cipher"
    "encoding/hex"
    "fmt"
    "io"
)

func Hash(keyValue, secret string) string {
    key, _ := hex.DecodeString(keyValue)

    bReader := bytes.NewReader([]byte(secret))

    block, err := aes.NewCipher(key)
    if err != nil {
        panic(err)
    }

    var iv [aes.BlockSize]byte
    stream := cipher.NewOFB(block, iv[:])

    var out bytes.Buffer

    writer := &cipher.StreamWriter{S: stream, W: &out}
    if _, err := io.Copy(writer, bReader); err != nil {
        panic(err)
    }

    return fmt.Sprintf("%x\n", out.Bytes())
}
```

可以按如下方式为其编写基准测试：

```go
package main

import (
    "testing"
)

func BenchmarkHash10(b *testing.B) {
    for n := 0; n < b.N; n++ {
        key := "1234567890"
```

```go
    Hash("6368616e676520746869732070617373", key)
}
}

func BenchmarkHash20(b *testing.B) {
    for n := 0; n < b.N; n++ {
        key := "12345678901234567890"
        Hash("6368616e676520746869732070617373", key)
    }
}
```

这定义了两个长度不同的键（10）和（20）字符的测试。然后你可以按如下方式运行基准测试：

```text
$ go test -bench=.
goos: linux
goarch: amd64
pkg: github.com/alexellis/bench-comp
BenchmarkHash10-8          816800             1314 ns/op
BenchmarkHash20-8          876960             1347 ns/op
PASS
ok    github.com/alexellis/bench-comp    2.288s
```

基准测试对于比较特定 CPU 上 Go 代码的性能也很有用。Arm CPU 传统上缺乏加密优化，因此该基准测试在 Raspberry Pi 上运行会慢得多。

### Go doesn’t ship your tests

此外，将名为 `addition_test.go` 的文件留在包中间可能感觉不自然。可以放心，Go 编译器和链接器不会在它生成的任何二进制文件中包含你的测试文件。

以下是我们在之前的 Golang 基础教程中使用的 net/http 包中查找生产代码与测试代码的示例。

```text
$ go list -f={{.GoFiles}} net/http
[client.go cookie.go doc.go filetransport.go fs.go h2_bundle.go header.go http.go jar.go
↪  method.go request.go response.go server.go sniff.go status.go transfer.go transport.go]

$ go list -f={{.TestGoFiles}} net/http
[cookie_test.go export_test.go filetransport_test.go header_test.go http_test.go
↪  proxy_test.go range_test.go readrequest_test.go requestwrite_test.go response_test.go
↪  responsewrite_test.go transfer_test.go transport_internal_test.go]
```

### Stress testing your tests

你的测试也可以多次运行，我发现这有助于发现我在编写的代码中出现的竞态条件或共享状态问题。

只需添加 `-test.count=100` 即可运行测试 100 次。

有时，你也会看到测试因结果被（缓存）而拒绝运行。在这种情况下，添加 `-test.count=1` 可以绕过该问题。

### Running tests in parallel

你的单元测试看起来运行良好且顺序确定，但经常在并行运行时会在进入生产环境前发现问题。这是因为我们在本地测试代码时，通常负载较低，或是串行执行。在生产系统中，我们可能有许多用户并行操作。

你可能还有一套运行缓慢的测试套件，在这种情况下并行运行可以节省时间。10 个耗时 1 秒的测试串行运行需要 10 秒，而以并行度 10 运行则可在 1 秒内完成。

考虑以下示例：

```go
package main

import (
    "testing"
    "time"
)

func Test_Slow1(t *testing.T) {
    time.Sleep(1 * time.Second)
}

func Test_Slow2(t *testing.T) {
    time.Sleep(1 * time.Second)
}

func Test_Slow3(t *testing.T) {
    time.Sleep(1 * time.Second)
}

func Test_Slow4(t *testing.T) {
    time.Sleep(1 * time.Second)
}

func Test_Slow5(t *testing.T) {
    time.Sleep(1 * time.Second)
}
```

```
$ go test ./ -v
=== RUN   Test_Slow1
--- PASS: Test_Slow1 (1.00s)
=== RUN   Test_Slow2
--- PASS: Test_Slow2 (1.01s)
=== RUN   Test_Slow3
--- PASS: Test_Slow3 (1.00s)
=== RUN   Test_Slow4
--- PASS: Test_Slow4 (1.01s)
=== RUN   Test_Slow5
--- PASS: Test_Slow5 (1.00s)
PASS
ok      github.com/alexellis/go-slow   5.343s
```

要并行运行测试，必须在测试函数中添加 t.Parallel()，然后连同 -test.parallel=N 参数一起传入。

```go
package main

import (
    "testing"
    "time"
)
```

```go
func Test_Slow1(t *testing.T) {
    t.Parallel()
    time.Sleep(1 * time.Second)
}

func Test_Slow2(t *testing.T) {
    t.Parallel()
    time.Sleep(1 * time.Second)
}

func Test_Slow3(t *testing.T) {
    t.Parallel()
    time.Sleep(1 * time.Second)
}

func Test_Slow4(t *testing.T) {
    t.Parallel()
    time.Sleep(1 * time.Second)
}

func Test_Slow5(t *testing.T) {
    t.Parallel()
    time.Sleep(1 * time.Second)
}
```

然后运行：

```
$ go test -v . -test.count=1 \
    -test.parallel 5
=== RUN   Test_Slow1
=== PAUSE Test_Slow1
=== RUN   Test_Slow2
=== PAUSE Test_Slow2
=== RUN   Test_Slow3
=== PAUSE Test_Slow3
=== RUN   Test_Slow4
=== PAUSE Test_Slow4
=== RUN   Test_Slow5
=== PAUSE Test_Slow5
=== CONT  Test_Slow1
=== CONT  Test_Slow5
=== CONT  Test_Slow4
=== CONT  Test_Slow2
=== CONT  Test_Slow3
--- PASS: Test_Slow3 (1.00s)
--- PASS: Test_Slow1 (1.00s)
--- PASS: Test_Slow5 (1.00s)
--- PASS: Test_Slow4 (1.00s)
--- PASS: Test_Slow2 (1.00s)
PASS
ok      github.com/alexellis/go-slow   1.342s
```

此测试也可以写成测试表。

```go
package main

import (
    "testing"
    "time"
)

func Test_Slow1(t *testing.T) {
    t.Parallel()
    cases := []struct {
        Name     string
        Duration time.Duration
    }{
        {Name: "Case 1", Duration: time.Second * 1},
        {Name: "Case 2", Duration: time.Second * 1},
        {Name: "Case 3", Duration: time.Second * 1},
        {Name: "Case 4", Duration: time.Second * 1},
        {Name: "Case 5", Duration: time.Second * 1},
    }

    for _, c := range cases {
        tc := c
        t.Run(tc.Name, func(t *testing.T) {
            t.Parallel()
            t.Logf("%s sleeping..", tc.Name)
            sleepFn(tc.Duration)
            t.Logf("%s slept", tc.Name)
        })
    }
}

func sleepFn(duration time.Duration) {
    time.Sleep(duration)
}
```

注意 tc 变量的使用，它将测试用例的值捕获到 t.Run 闭包中。

作为奖励，它更易读，并且耗时略少。

```
$ go test -v . -parallel 5
=== RUN   Test_Slow1
=== PAUSE Test_Slow1
=== CONT  Test_Slow1
=== RUN   Test_Slow1/Case_1
=== PAUSE Test_Slow1/Case_1
=== RUN   Test_Slow1/Case_2
=== PAUSE Test_Slow1/Case_2
=== RUN   Test_Slow1/Case_3
=== PAUSE Test_Slow1/Case_3
=== RUN   Test_Slow1/Case_4
=== PAUSE Test_Slow1/Case_4
=== RUN   Test_Slow1/Case_5
=== PAUSE Test_Slow1/Case_5
=== CONT  Test_Slow1/Case_1
=== CONT  Test_Slow1/Case_4
```

```
main_test.go:25: Case 4 sleeping..
=== CONT  Test_Slow1/Case_5
    main_test.go:25: Case 5 sleeping..
=== CONT  Test_Slow1/Case_3
    main_test.go:25: Case 3 sleeping..
=== CONT  Test_Slow1/Case_2
    main_test.go:25: Case 2 sleeping..
=== CONT  Test_Slow1/Case_1
    main_test.go:25: Case 1 sleeping..
    main_test.go:27: Case 1 slept
=== CONT  Test_Slow1/Case_2
    main_test.go:27: Case 2 slept
=== CONT  Test_Slow1/Case_5
    main_test.go:27: Case 5 slept
=== CONT  Test_Slow1/Case_4
    main_test.go:27: Case 4 slept
=== CONT  Test_Slow1/Case_3
    main_test.go:27: Case 3 slept
--- PASS: Test_Slow1 (0.00s)
    --- PASS: Test_Slow1/Case_2 (1.01s)
    --- PASS: Test_Slow1/Case_1 (1.01s)
    --- PASS: Test_Slow1/Case_5 (1.01s)
    --- PASS: Test_Slow1/Case_4 (1.01s)
    --- PASS: Test_Slow1/Case_3 (1.01s)
PASS
ok      github.com/alexellis/go-slow   1.260s
```

因此我们从略高于 5 秒减少到略低于 1.5 秒。这看起来可能微不足道，但如果你有大量测试或经常运行它们，可以更高效。

### Compile the tests to a binary

我在用 Go 多年后才学到的一件事是，测试可以像你的 CLI 或 HTTP 服务器一样编译成二进制文件。

这有什么用？

一种场景是，如果你有针对外部资源运行的测试，例如验证器或证书工具。你可以在不失去 go test 功能的情况下对其进行版本化、发布和分发。

让我们试一个例子？

```
$ git clone https://github.com/alexellis/go-execute
$ cd go-execute
```

然后以“正常”方式对其进行测试：

```
$ go test -v ./...
=== RUN   TestExec_WithShell
--- PASS: TestExec_WithShell (0.00s)
=== RUN   TestExec_CatTransformString
--- PASS: TestExec_CatTransformString (0.00s)
=== RUN   TestExec_CatWC
--- PASS: TestExec_CatWC (0.00s)
=== RUN   TestExec_WithEnvVars
--- PASS: TestExec_WithEnvVars (0.00s)
=== RUN   TestExec_WithEnvVarsInheritedFromParent
```

```text
--- PASS: TestExec_WithEnvVarsInheritedFromParent (0.00s)
=== RUN   TestExec_WithEnvVarsAndShell
--- PASS: TestExec_WithEnvVarsAndShell (0.00s)
PASS
ok      github.com/alexellis/go-execute/pkg/v1  0.798s
```

现在，让我们创建一个可分发到另一台机器上运行的二进制文件。我们只需加上 -c（编译）标志。

```bash
$ go test ./... -c
$ v1.test
```

然后，你可以运行该测试二进制文件，并传入与之前看到的类似的标志。

```text
$ ./v1.test
PASS

$ ./v1.test -test.v
# Produces the same output as "go test -v"
```

更多信息，请参见 ./v1.test --help。

关于更多基础知识，请阅读 Go 语言测试文档。

### 隔离依赖

单元测试和集成测试有什么区别？

单元测试和集成测试之间的区别在于，单元测试通常会隔离与网络、磁盘等进行通信的依赖。单元测试通常只测试一个东西，例如一个函数。

在 Go 中，可以通过接口实现隔离，但如果你有 C# 或 Java 的背景，它们在 Go 中的形式看起来会有些不同。接口是隐式实现而不是强制实现的，这意味着具体类不需要预先知道接口。

这让我们可以拥有非常小的接口，例如 io.ReadCloser，它只有两个方法，分别由 Reader 和 Closer 接口组成：

```go
Read(p []byte) (n int, err error)
```

*Reader 接口*

```go
Close() error
```

*Closer 接口*

如果你正在设计一个供第三方使用的包，那么设计接口是有意义的，这样其他人在需要时可以编写单元测试来隔离你的包。当这些接口不存在时，会给使用者带来大量的工作和维护成本。

接口可以在函数调用中被替换。因此，如果我们想测试这个方法，只需要提供一个实现了 Reader 接口的伪造类/测试替身类即可。

创建一个用于工作的文件夹：

```bash
export GH_USERNAME="alexellis"
mkdir -p $GOPATH/src/github.com/$GH_USERNAME/fake-1/
cd $GOPATH/src/github.com/$GH_USERNAME/fake-1/
```

保存 main.go：

```go
package main

import (
    "fmt"
    "io"
    "log"
)

type FakeReader struct {
    payload []byte
    position int
}

func (f *FakeReader) Read(p []byte) (n int, err error) {
    p = f.payload
    f.position += len(f.payload)
    if f.position > len(f.payload) {
        return 0, io.EOF
    }

    return len(f.payload), nil
}

func (f *FakeReader) SetFakeBytes(p []byte) {
    f.position = 0
    f.payload = p
}

func ReadAllTheBytes(reader io.Reader) []byte {
    data, err := io.ReadAll(reader)
    if err != nil {
        log.Fatal(err)
    }
    return data
}

func main() {
    fakeReader := &FakeReader{}
    want := []byte("when called, return this data")
    fakeReader.SetFakeBytes(want)
    got := ReadAllTheBytes(fakeReader)
    fmt.Printf("%d/%d bytes read.\n", len(got), len(want))
}
```

在实现自己的抽象（如上所述）之前，最好先搜索 Go 语言文档，看看是否已经有你可以使用的东西。在上面的例子中，我们也可以使用 bytes 包中的标准库：

```go
func NewReader(b []byte) *Reader
```

testing/iotest 包提供了一些 Reader 实现，它们可能很慢，或者会在读取过程中途引发错误。这些非常适合测试你的系统的韧性。你应该准备好面对这样的问题：“如果发生超时怎么办？”

### 隔离依赖的示例

让我们重构用于从 HTTP 端点获取 JSON 数据的代码。如果你还没有完成这个练习，你可以返回去现在试试。

首先，我们将创建一个新文件夹，其中包含一个名为 astros 的子包，该包将包含重构后的代码及其接口。

```bash
export GH_USERNAME="alexellis"
mkdir -p $GOPATH/src/github.com/$GH_USERNAME/isolate-astros/astros
cd $GOPATH/src/github.com/$GH_USERNAME/isolate-astros/astros
```

我们需要创建一个接口，以便我们可以用自己的数据替换 HTTP 调用。

下面的 GetWebRequest 接口指定了以下函数，用于返回给定 URL 的数据。

```go
type GetWebRequest interface {
    FetchBytes(url string) ([]byte, error)
}
```

注意：接口是隐式推断的，而不是显式地标注在结构体上。这与 C# 或 Java 等语言不同。

我们为什么要创建接口？因为我们希望能够“伪造”或用测试数据替换 HTTP 调用。

保存 isolate-astros/astros/types.go：

```go
package astros

type People struct {
    Number int `json:"number"`
}

type GetWebRequest interface {
    FetchBytes(url string) ([]byte, error)
}
```

现在将实现保存为 isolate-astros/astros/http_astros.go：

```go
package astros

import (
    "io"
    "net/http"
)

type LiveGetWebRequest struct {
}

func (LiveGetWebRequest) FetchBytes(url string) ([]byte, error) {
    req, err := http.NewRequest(http.MethodGet, url, nil)
    if err != nil {
        return []byte{}, err
    }

    req.Header.Set("User-Agent", "spacecount-tutorial")

    res, err := http.DefaultClient.Do(req)
    if err != nil {
        return []byte{}, err
    }
    defer res.Body.Close()

    body, err := io.ReadAll(res.Body)
    if err != nil {
        return []byte{}, err
    }

    return body, nil
}
```

接下来，让我们编写使用接口和真实 LiveGetWebRequest 实现的新 main.go 文件：

```go
package main

import (
    "encoding/json"
    "fmt"

    "github.com/alexellis/isolate-astros/astros"
)

func getAstronauts(getWebRequest astros.GetWebRequest) (int, error) {
    url := "http://api.open-notify.org/astros.json"
    body, err := getWebRequest.FetchBytes(url)
    if err != nil {
        return 0, err
    }
    peopleResult := astros.People{}

    if err := json.Unmarshal(body, &peopleResult); err != nil {
        return 0, err
    }
    return peopleResult.Number, err
}

func main() {
    liveClient := astros.LiveGetWebRequest{}
    number, err := getAstronauts(liveClient)
    if err != nil {
        panic(err)
    }
    fmt.Println(number)
}
```

测试一下，确保一切正常：

```text
go run .
7
```

接下来创建单元测试 main_test.go：

```go
package main

import "testing"
```

```go
// Copyright (c) OpenFaaS Author(s). All rights reserved.
// Licensed under the MIT license.

package auth

import (
    "crypto/subtle"
    "net/http"
)

type BasicAuthCredentials struct {
    User     string
    Password string
}

// DecorateWithBasicAuth enforces basic auth as a middleware with given credentials
func DecorateWithBasicAuth(next http.HandlerFunc, credentials *BasicAuthCredentials) http.HandlerFunc {
    return func(w http.ResponseWriter, r *http.Request) {
        user, password, ok := r.BasicAuth()

        const noMatch = 0
        if !ok ||
            user != credentials.User ||
            subtle.ConstantTimeCompare([]byte(credentials.Password), []byte(password)) == noMatch {

            w.Header().Set("WWW-Authenticate", `Basic realm="Restricted"`)
            w.WriteHeader(http.StatusUnauthorized)
            w.Write([]byte("invalid credentials"))
            return
        }

        next.ServeHTTP(w, r)
    }
}
```

这段代码向服务器应用 HTTP 基本认证头，因此除非你拥有凭据，否则无法登录。

我们需要以某种方式创建一个假的 http.ResponseWriter，并接收写入其中的内容，同时创建一个假的 http.Request，以便我们可以传入不同的值来测试身份验证检查是否有效。

httptest.NewRecorder() 可用于记录我们的处理器发送回的响应。

然后，我们可以使用 httptest.NewRequest 函数创建一个不会到达真实 HTTP 服务器的假请求。

```go
func Test_AuthWithValidPassword_Gives200(t *testing.T) {

    handler := func(w http.ResponseWriter, r *http.Request) {
        io.WriteString(w, "<html><body>Hello World!</body></html>")
    }
    w := httptest.NewRecorder()

    wantUser := "admin"
    wantPassword := "password"
    r := httptest.NewRequest(http.MethodGet, "http://localhost:8080", nil)

    r.SetBasicAuth(wantUser, wantPassword)
    wantCredentials := &BasicAuthCredentials{
        User:      wantUser,
        Password: wantPassword,
    }

    decorated := DecorateWithBasicAuth(handler, wantCredentials)
    decorated.ServeHTTP(w, r)

    wantCode := http.StatusOK

    if w.Code != wantCode {
        t.Fatalf("status code, want: %d, got: %d", wantCode, w.Code)
    }

    gotAuth := w.Header().Get("WWW-Authenticate")
    wantAuth := ""
    if gotAuth != wantAuth {
        t.Fatalf("WWW-Authenticate, want: %s, got: %s", wantAuth, gotAuth)
    }
}
```

要测试 HTTP 禁止状态码（403），我们可以执行以下操作：

```go
func Test_AuthWithInvalidPassword_Gives403(t *testing.T) {

handler := func(w http.ResponseWriter, r *http.Request) {
    io.WriteString(w, "<html><body>Hello World!</body></html>")
}

w := httptest.NewRecorder()

wantUser := "admin"
wantPassword := "test"
r := httptest.NewRequest(http.MethodGet, "http://localhost:8080", nil)
r.SetBasicAuth(wantUser, wantPassword)

wantCredentials := &BasicAuthCredentials{
    User:      wantUser,
    Password: "",
}

decorated := DecorateWithBasicAuth(handler, wantCredentials)
decorated.ServeHTTP(w, r)

wantCode := http.StatusUnauthorized
if w.Code != wantCode {
    t.Fatalf("status code, want: %d, got: %d", wantCode, w.Code)
}

gotAuth := w.Header().Get("WWW-Authenticate")
}
```




```go
wantAuth := `Basic realm="Restricted"`
if gotAuth != wantAuth {
    t.Fatalf("WWW-Authenticate, want: %s, got: %s", wantAuth, gotAuth)
}
}
```

你可以克隆 Git 仓库并像这样运行测试：

```
mkdir -p $GOPATH/src/github.com/openfaas/
cd $GOPATH/src/github.com/openfaas/
git clone --depth=1 https://github.com/openfaas/faas-provider
cd faas-provider

go test -v ./auth/
=== RUN   Test_AuthWithValidPassword_Gives200
--- PASS: Test_AuthWithValidPassword_Gives200 (0.00s)
=== RUN   Test_AuthWithInvalidPassword_Gives403
--- PASS: Test_AuthWithInvalidPassword_Gives403 (0.00s)
=== RUN   Test_ReadFromCustomLocation_AndNames
--- PASS: Test_ReadFromCustomLocation_AndNames (0.00s)
=== RUN   Test_ReadFromCustomLocation_DefaultNames
--- PASS: Test_ReadFromCustomLocation_DefaultNames (0.00s)
PASS
ok      github.com/openfaas/faas-provider/auth  0.002s
```

## 第 7 章：使用 Goroutines 并发工作

在计算中，并发意味着能够同时处理多个任务，但不一定在完全相同的时间内对它们进行工作。这个概念经常与并行计算混淆，并行计算是指同时对多个任务取得进展的行为。

Go 对并发的解决方案是 Goroutines。文档将“goroutine”定义为：“由 Go 运行时管理的轻量级线程。”

为什么这很重要？操作系统（OS）线程通常创建和协调成本很高。Go 的方法被描述为“lightweight”线程，这意味着操作系统（OS）线程和 Goroutines 之间不一定存在 1:1 的关系，使其更快、更具可扩展性。

如果想深入了解 Goroutines 和同步技术，你可能也会喜欢 The Go Programming Language（Addison-Wesley）。

在本章中，我想介绍一些实用示例，展示你今天如何开始。我还会提到一个常见的陷阱，即使是最有经验的 Golang 程序员也可能遇到。

我们将涵盖：编写你的第一个 Goroutine、在循环中创建 Goroutines、通过 WaitGroups 同步、使用 Error groups 进行错误处理、使用通道并限制进行中的工作量。

### 使用 Goroutines 的简单示例

在这个示例中，我们有一个 printLater 函数，它模拟了一个运行缓慢的调用，慢到我们可能希望并发运行多个调用并在最后收集结果，而不是串行运行每个调用并等待更长时间。

```go
package main

import (
    "fmt"
    "os"
    "time"
)

func main() {
    printLater("Hello\n", time.Millisecond*100)
    printLater("World\n", time.Millisecond*100)
    printLater(os.Getenv("USER")+"\n", time.Millisecond*100)
}

func printLater(msg string, duration time.Duration) {
    time.Sleep(duration)
    fmt.Printf(msg)
}
```

运行此程序时，会得到以下输出，大约需要 300ms 执行：

```
$ go run main.go
Hello
World
alex
```

现在想象 printLater 方法实际上是之前从远程 HTTP 服务器获取和提取 JSON 的示例。我们可以通过使用 Goroutines 并发执行 HTTP 调用，将总运行时间从 300ms 优化到大约 100ms。

```go
package main

import (
    "fmt"
    "os"
    "time"
)

func main() {
    go func() {
        printLater("Hello\n", time.Millisecond*100)
    }()
    go func() {
        printLater("World\n", time.Millisecond*100)
    }()
    go func() {
        printLater(os.Getenv("USER")+"\n", time.Millisecond*100)
    }()
}

func printLater(msg string, duration time.Duration) {
    time.Sleep(duration)
    fmt.Printf(msg)
}
```

现在运行此程序时，它将在没有任何输出的情况下退出。这是因为 Goroutines 异步执行，因此需要与主程序的执行流程同步。

你可以通过使用通道，或标准库 sync 包中的其他一些原语来同步 Goroutines。WaitGroup 是我最喜欢的示例之一。

WaitGroup 的主要目的是阻塞并等待多个任务完成。

要使用 WaitGroup，首先使用任务数量调用 Add 函数，然后设置你的 Goroutines。在每个 Goroutine 内部，需要在完成时调用 Done。最后，在同步工作的函数中，调用 wg.Wait()，它将在那里阻塞执行，直到所有例程都调用了 Done 且未完成的任务设为 0。

```go
package main

import (
    "fmt"
    "os"
    "sync"
    "time"
)

func main() {
    wg := sync.WaitGroup{}
    wg.Add(3)

    go func() {
        defer wg.Done()
        printLater("Hello\n", time.Millisecond*100)
    }()
    go func() {
        defer wg.Done()
        printLater("World\n", time.Millisecond*100)
    }()
    go func() {
        defer wg.Done()
        printLater(os.Getenv("USER")+"\n", time.Millisecond*100)
    }()

    wg.Wait()
}

func printLater(msg string, duration time.Duration) {
    time.Sleep(duration)
    fmt.Printf(msg)
}
```

现在我们看到代码已完成，并打印所有消息。我们可以判断工作是并发执行的，因为消息似乎顺序错乱。

```
$ go run main.go
World
Hello
alex
```

此示例无法处理错误，需要注意的是，如果一个 Goroutine 调用 panic()，则整个应用程序将失败。我们将在稍后探讨两种错误处理方法。

### 避免 Goroutines 的常见错误

现在让我们探讨一个常见的 Goroutines 错误，我自己也时不时会犯。

现在你已经了解了定义和同步 Goroutines 的方法，引入循环会很诱人，有时也更高效。

```go
package main

import (
    "fmt"
    "sync"
    "time"
)

func main() {
    wg := sync.WaitGroup{}
    workItems := 5
    wg.Add(workItems)

    for i := 1; i <= workItems; i++ {
        go func() {
            defer wg.Done()
            printLater(
                fmt.Sprintf("Hello from %d\n", i),
                time.Millisecond*100)
        }()
    }

    wg.Wait()
}

func printLater(msg string, duration time.Duration) {
    time.Sleep(duration)
    fmt.Printf(msg)
}
```

现在运行示例：

```
$ go run ./
Hello from 6
Hello from 6
Hello from 6
Hello from 6
Hello from 6
```

注意消息对每个 5 个响应都显示 `Hello from 6`？循环捕获了 i 变量的最终值并将其用于每个 Goroutine。

为了解决这个问题，我们可以将 i 变量作为参数传递给 Goroutine，或者使用新的局部变量在闭包中捕获它。

以下是第一种方法：

```go
for i := 1; i <= workItems; i++ {
    go func(j int) {
        defer wg.Done()
        printLater(
            fmt.Sprintf("Hello from %d\n", j),
            time.Millisecond*100)
    }(i)
}
```

注意我们的 Goroutine 的签名如下所示更改：

```go
i := 1
go func(j int) {
    fmt.Printf("Value is: %d", j)
}(i)
```

在第二种方法中，我们定义一个新的局部变量 j 来捕获 i 的值：

```go
for i := 1; i <= workItems; i++ {
    j := i
    go func() {
        defer wg.Done()
        printLater(
            fmt.Sprintf("Hello from %d\n", j),
            time.Millisecond*100)
    }()
}
```

在这两种情况下，我们都会得到预期的输出：

```
Hello from 4
Hello from 3
Hello from 5
Hello from 1
Hello from 2
```

### 错误组

另一种并行同步工作的方式是通过 Golang 团队提供的非官方“errgroup”包。

在上面的示例中，这变得更有用，因为我们的任何 Goroutine 都可以返回错误并被捕获，而无需编写代码通过通道同步消息。

errgroup 不仅可以并发运行多个 Goroutine，还可以按流水线方式串行运行它们，在进入下一个任务之前检查每个任务的错误。

要使用一个 *error group*，导入 `"golang.org/x/sync/errgroup"` 包，然后使用 `g := errgroup.Group{}` 定义一个新的 errgroup，然后为每个工作项调用 `g.Go(func() error { })`。你会注意到 `g.Go()` 函数接受一个可以返回错误 的函数。如果没有错误，则返回 `nil`，否则返回错误，整个执行将退出并将错误冒泡到同步函数。

```go
package main

import (
    "fmt"
    "os"
    "time"

    "golang.org/x/sync/errgroup"
)

func main() {
    g := errgroup.Group{}
    g.Go(func() error {
        printLater("Hello\n", time.Millisecond*100)
        return nil
    })
    g.Go(func() error {
        // printLater("World\n", time.Millisecond*100)
        return fmt.Errorf("world failed")
    })
    g.Go(func() error {
        printLater(os.Getenv("USER")+"\n", time.Millisecond*100)
        return nil
```



```
})

    err := g.Wait()
    if err != nil {
        fmt.Fprintf(os.Stderr, "error found: %s", err.Error())
        os.Exit(1)
    }
    fmt.Print("All work completed as expected")
}

func printLater(msg string, duration time.Duration) {
    time.Sleep(duration)
    fmt.Printf(msg)
}
```

运行代码时，你将看到以下输出：

```
$ go run ./
Hello
alex
error found: world failed
```

你可以在软件包的文档中了解更多关于*错误组*的信息。

### 限制对昂贵资源的请求

在使用 Goroutine 时，很容易陷入不良状况：像网络连接、数据库连接或打开的文件等资源被消耗得过多。Go 源码中有一个名为 “internal/singleflight” 的包，用于限制 DNS 查找的进行中请求。Go 团队认为它非常有用，于是将其导出并单独维护，以便我们也能从中受益。

你可以在这里查看外部版本：golang.org/x/sync/singleflight

它的API与我们刚刚看过的错误组类似：

```
package main

import (
    "fmt"
    "golang.org/x/sync/singleflight"
)

type ISSPosition struct {
    Latitude  float64 `json:"latitude"`
    Longitude float64 `json:"longitude"`
}

func (i *ISSPosition) String() string {
    return fmt.Sprintf("(%f,%f)", i.Latitude, i.Longitude)
}

func main() {
    s := singleflight.Group{}
    key := "key for resource"
```

```
res, err, shared := s.Do(key, func() (any, error) {
    return ISSPosition{Latitude: 40.0, Longitude: -0.31}, nil
})

fmt.Printf("Shared response? %v\n", shared)
if err != nil {
    fmt.Println(err)
    return
}
position := res.(ISSPosition)

fmt.Printf("Position: %s\n", position.String())
}
```

请注意：

- 响应以 “any” 返回，这与写 “interface{}” 相同，因此任何结果都需要被解包（unwrap）。
- 有一个名为 “key” 的变量，意味着 singleflight 组可以用于多个调用。

如果 key 与现有调用匹配，你将在该调用就绪时获得其响应；如果调用与某个 key 不匹配，它会在完成之前收集其他所有传入的请求。

如果你觉得有用，你还可以判断自己是获得了共享响应，还是作为第一个调用者获得了响应的原始副本。

在我们的示例中，我们永远不会得到共享响应，所以让我们构建一个带有 HTTP 服务器的示例，并模拟多个连接和用户。

你可以在 “singleflight-simple” 文件夹中找到源代码。

假设你正在托管一个 HTTP 服务器，该服务器需要调用另一台服务器并返回结果，而该查询需要 2 秒。如果在 2 秒内收到 1 个请求，那么你将对上游服务器发出 1 次调用；但如果你收到 1000 个请求，那么在同一时间段内你将发出 1000 次调用。

如果 API 调用开销很大或可能被限流，这就尤其成问题。2022 年夏天，我们在 OpenFaaS 网关中实现了 singleflight 模式，这大大减少了从零开始扩容期间的 API 调用。为后端实现单飞查询 #1734

让我们通过一个使用 singleflight 和 HTTP 的示例来实践，这很可能也是你需要使用它的场景。

http://api.open-notify.org/iss-now.json 上的 OpenAPI 会向我们展示国际空间站（ISS）的纬度和经度，不过我们可能想重新格式化响应，使其只包含纬度和经度这两个值。

API 响应：

```
{
  "timestamp": 1658399875,
  "iss_position": {
    "latitude": "43.6602",
    "longitude": "-160.8366",
  },
  "message": "success"
}
```

期望的输出：

```
{
  "latitude": "43.6602",
  "longitude": "-160.8366",
}
```

你可以在 “singleflight-http” 文件夹中找到源代码。

```
package main

import (
    "encoding/json"
    "fmt"
    "io"
    "log"
    "net/http"
    "time"

    "golang.org/x/sync/singleflight"
)

type ISSRes struct {
    Position ISSPosition `json:"iss_position"`
}

type ISSPosition struct {
    Latitude  string `json:"latitude"`
    Longitude string `json:"longitude"`
}

func main() {

    s := singleflight.Group{}

    http.HandleFunc("/position", func(w http.ResponseWriter, r *http.Request) {

        uri := "http://api.open-notify.org/iss-now.json"
        res, err, _ := s.Do(uri, func() (any, error) {

            fmt.Printf("HTTP call to: %s\n", uri)

            req, err := http.NewRequest(http.MethodGet, uri, nil)
            if err != nil {
                return nil, fmt.Errorf("unable to create request: %s", err)
            }

            res, err := http.DefaultClient.Do(req)
            if err != nil {
                return nil, fmt.Errorf("unable to make request: %s", err)
            }
            var body []byte

            if res.Body != nil {
                defer res.Body.Close()
                body, _ = io.ReadAll(res.Body)
            }

            if res.StatusCode != http.StatusOK {
                return nil, fmt.Errorf("bad status: %d, body: %s", res.StatusCode, string(body))
            }
```

```
i := &ISSRes{}
if err := json.Unmarshal(body, i); err != nil {
return nil, fmt.Errorf("can't unmarshal response: %s, error: %s", string(body), err)
}

return i.Position, nil
})

if err != nil {
    http.Error(w, err.Error(), http.StatusInternalServerError)
    return
}

position := ISSPosition{
    Latitude:  res.(ISSPosition).Latitude,
    Longitude: res.(ISSPosition).Longitude,
}

encoded, _ := json.Marshal(position)
w.Header().Add("Content-Type", "application/json")
w.Write(encoded)
})

port := 8080
server := &http.Server{
    Addr:          fmt.Sprintf(":%d", port),
    ReadTimeout:   10 * time.Second,
    WriteTimeout:  10 * time.Second,
    MaxHeaderBytes: 1 << 20,
}
log.Printf("Listening on port: %d\n", port)
log.Printf("Endpoints available: /position")
log.Fatal(server.ListenAndServe())
}
```

运行该示例，使用 curl 调用它，然后再使用 hey 调用：

```
curl -s http://127.0.0.1:8080/position
{"latitude":"-40.3230","longitude":"-77.2043"}
```

每次命中该端点时，你都会看到消息：“HTTP call to: http://api.open-notify.org/iss-now.json”。现在尝试用 10 个并发用户生成流量，总共 10 个请求：

```
hey -c 10 -n 10 http://127.0.0.1:8080/position
```

当我运行这个时，我只看到“HTTP call to”被打印了一次。

尝试持续 5 秒的更长时间段：

```
hey -c 10 -z 5s http://127.0.0.1:8080/position
```

我注意到在这 5 秒内共发起了 330 次调用，而只有 33 次是对 API 的上游调用。

如果需要，你可以通过使用 Go map 引入缓存来进一步优化 API。请记住，缓存还需要一个失效策略来使数据过期，以便根据需要刷新。

### 在 Goroutine 之间共享数据

在 Go 中，在内存限制范围内，有两种在 Goroutine 之间共享数据的方法。第一种是创建一个带有锁机制的类型，这样读取方或写入方可以获得锁，以防止两个 Goroutine 试图更新同一份数据，进而避免产生竞争条件。

在第一个示例中，我们的代码可能看起来类似于：

```go
package main

import (
    "sync"
)

type ScrapeRun struct {
    Result []ScrapeResult
    Lock   *sync.Mutex
}

type ScrapeResult struct {
    HTTPCode   int
    HTTPLength int
    Error      error
}
```

在主程序流程中，你应该编写与下面类似的代码：

```go
package main

import (
    "fmt"
    "io"
    "net/http"
    "sync"
)

type ScrapeRun struct {
    Results map[string]ScrapeResult
    Lock    *sync.Mutex
}

type ScrapeResult struct {
    HTTPCode   int
    HTTPLength int64
    Error      error
}

func scrape(url string, sr *ScrapeRun) {
    res, err := http.Get(url)
    if err != nil {
        sr.Lock.Lock()
        defer sr.Lock.Unlock()

        sr.Results[url] = ScrapeResult{
            Error:    err,
            HTTPCode: http.StatusBadGateway,
```


```go
fmt.Printf("- %s = error: %s\n", k, v.Error.Error())
    } else {
        fmt.Printf("- %s = [%d] %d bytes\n", k, v.HTTPCode, v.HTTPLength)
    }
}
}
```

这是运行程序后的输出：

```text
$ go run .
- https://notfound.example.com/ = error: Get "https://notfound.example.com/": dial tcp:
  lookup notfound.example.com: no such host
- https://openfaas.com/ = [200] 32696 bytes
- https://inlets.dev/ = [200] 69805 bytes
```

你知道吗？sync.Mutex 会对对象施加独占锁，这意味着在锁释放之前，任何其他读写操作都无法进行。如果对象同时存在读者和写者，这可能会导致瓶颈。

sync.RWMutex 类型可以用作 sync.Mutex 的直接替代品，它允许任意数量的读者获取锁，或单个写者获取锁。

```go
package main

import (
    "sync"
)

func main() {
    lock := sync.RWMutex{}
    go readOperation(data, "key", &lock)
    go writeOperation(data, "key", "value", &lock)

    // Add synchronisation for the two routines here.
}

func readOperation(data map[string]string, key string, lock *sync.RWMutex) {
    lock.RLock()
    defer lock.RUnlock()
    fmt.Println(data["key"])
}

func writeOperation(data map[string]string, key, value string, lock *sync.RWMutex) {
    lock.Lock()
    defer lock.Unlock()
    data[key] = value
}
```

在这种情况下，读写操作可以同时发生，因为写锁不会阻塞读取值的函数。

这种模式在真实世界中的用例是什么？也许你有一个内存缓存，保存着活跃客户列表。该列表需要通过联网下载，这可能是一项开销很大的操作。随后，该列表会与 HTTP 服务器中的多个 Goroutine 或处理程序共享。读锁将用于访问数据，而写锁将由类似定时器或长时间运行的循环使用，以更新缓存中的条目。

第二种方法是让 Goroutine 直接输出数据，不共享类型。调用代码随后可以汇总结果，无需创建带锁的单独类型。你将在下面看到这种方法的示例：

```go
var uri string
flag.StringVar(&uri, "uri", "", "uri to fetch")
flag.Parse()

titleCh := make(chan string)
errorCh := make(chan error)

go titleOf(uri, titleCh, errorCh)

select {
case title := <-titleCh:
    fmt.Printf("Title: %s\n", title)
case err := <-errorCh:
    fmt.Printf("Error: %s\n", err.Error())
    os.Exit(1)
}
}

func titleOf(uri string, titleCh chan string, errCh chan error) {
    req, err := http.NewRequest(http.MethodGet, uri, nil)
    if err != nil {
        errCh <- err
        return
    }

    res, err := http.DefaultClient.Do(req)
    if err != nil {
        errCh <- err
        return
    }
    if res.Body != nil {
        defer res.Body.Close()

        res, _ := io.ReadAll(res.Body)
        for _, l := range strings.Split(string(res), "\n") {
            if strings.Contains(l, "<title>") {
                titleCh <- l
                return
            }
        }
    }

    errCh <- fmt.Errorf("no title found")
}
```

下面是一个运行工作负载的示例，包含三个不同的网站，然后是几个错误场景。

```text
$ go run . -uri https://inlets.dev
Title:   <title>Inlets - The Cloud Native Tunnel</title>

$ go run . -uri https://github.com/alexellis/
Title:   <title>alexellis (Alex Ellis) · GitHub</title>

$ go run .
Error: Get "": unsupported protocol scheme ""
exit status 1

$ go run . -uri https://gitzub.com
Error: Get "https://gitzub.com": dial tcp: lookup gitzub.com: no such host
exit status 1
```

### 使用上下文处理超时

现在，这里还存在另一个潜在问题。某些网站可能会挂起或无限期地保持连接打开。Go 提供了一个称为“context”（上下文）的概念，可以将其传递给使用外部资源的调用，就像上面的 HTTP 请求一样。

Context（上下文）会携带一个截止时间、一个取消信号以及其他值，跨过 API 边界。

你可以在这里查看 context 包的文档：context。

有些库函数允许通过参数传入 Context，但如果没有可用的 Context，你可以使用以下方法获取后台上下文：

```go
ctx := context.Background()
```

你也可能会看到使用 context.TODO() 的情况，这可以用于没有可用的上下文，或者不清楚该使用哪个上下文的时候。

它的 API 还提供了几个实用方法，用于定义取消策略：

```go
func WithCancel(parent Context) (ctx Context, cancel CancelFunc)
```

需要传入一个父上下文，当调用 cancel 函数时，任何正在进行的操作都必须停止，并应释放资源。

```go
func WithDeadline(parent Context, d time.Time) (Context, CancelFunc)
```

这个函数与 WithCancel 类似，不同的是它有一个截止时间/日期，在未来的某个时间点，操作应当被取消。这对于 HTTP 请求或访问外部系统时很有用。

```go
func WithTimeout(parent Context, timeout time.Duration) (Context, CancelFunc)
```

WithTimeout 函数也类似，但它提供了一个辅助函数，因此可以传入一个超时值，而不是未来的实际日期。

在下面的示例中，你将看到 WithTimeout 是如何工作的。

```go
package main

import (
  "context"
  "flag"
  "fmt"
  "io"
  "net/http"
  "os"
  "strings"
  "time"
)

func main() {
    var uri string
    var timeout time.Duration

    flag.StringVar(&uri, "uri", "", "uri to fetch")
    flag.DurationVar(&timeout, "timeout", time.Second*5, "timeout for HTTP client")

    flag.Parse()

    titleCh := make(chan string)
    errorCh := make(chan error)

    go titleOf(uri, timeout, titleCh, errorCh)

    select {
    case title := <-titleCh:
        fmt.Printf("Title: %s\n", title)
    case err := <-errorCh:
        fmt.Printf("Error: %s\n", err.Error())
        os.Exit(1)
    }
}

func titleOf(uri string, timeout time.Duration, titleCh chan string, errCh chan error) {
    ctx, cancel := context.WithTimeout(context.Background(), timeout)
    defer cancel()

    req, err := http.NewRequestWithContext(ctx, http.MethodGet, uri, nil)
    if err != nil {
        errCh <- err
        return
    }

    res, err := http.DefaultClient.Do(req)
    if err != nil {
        errCh <- err
        return
    }

    if res.Body != nil {
        defer res.Body.Close()
        res, _ := io.ReadAll(res.Body)
        for _, l := range strings.Split(string(res), "\n") {
            if strings.Contains(l, "<title>") {
                titleCh <- l
                return
            }
        }
    }

    errCh <- fmt.Errorf("no title found")
}
```

现在，让我们将超时设置得更激进一些，比如 10ms，并引入一个 flag，以便我们能够轻松配置该值。

```text
$ go run . -uri https://github.com/alexellis --timeout 10ms
Error: Get "https://github.com/alexellis": context deadline exceeded
exit status 1

$ go run . -uri https://github.com/alexellis --timeout 1000ms
Error: Get "https://github.com/alexellis": context deadline exceeded
exit status 1

$ go run . -uri https://github.com/alexellis --timeout 3000ms
Title:  <title>alexellis (Alex Ellis) · GitHub</title>
```

所以看起来，我们需要一个相当宽裕的超时时间，才能从英国的一台客户端获取我的 GitHub 个人资料。

### 限制并发任务

到目前为止，我们所看到的所有技术都不允许我们限制资源。在某些时候，你可能会超过某个限制，比如你的机器上允许的文件数或 HTTP 连接数，或者你的“数据库即服务”所允许的数据库连接数。

在这些情况下，考虑限制工作负载是很有用的。OpenFaaS CLI 中实现了一种类似的技术，用于构建、推送和部署函数。

默认情况下，并发级别为 1，但可以被覆盖，因此如果你需要构建 8 个函数，你可以让其中 4 个同时被处理。你可以将这种方法看作一个“窗口”，4 个 Goroutine 会启动，并接收 8 份工作中的 4 份。当进行中的工作降到 3 份时，剩余队列中的 4 件任务中的另一件将被处理，直到所有工作完成且没有剩余为止。

下面的模式更新了我们的 `titleOf` 方法，使其无需 channel 即可运行，并返回 `(string, error)` 形式的结果。

```go
func titleOf(uri string, timeout time.Duration) (string, error) {
    ctx, cancel := context.WithTimeout(context.Background(), timeout)
    defer cancel()

    req, err := http.NewRequestWithContext(ctx, http.MethodGet, uri, nil)
    if err != nil {
        return "", err
    }

    res, err := http.DefaultClient.Do(req)
    if err != nil {
        return "", err
    }

    if res.Body != nil {
        defer res.Body.Close()
        res, _ := io.ReadAll(res.Body)
        for _, l := range strings.Split(string(res), "\n") {
            if strings.Contains(l, "<title>") {
                return uri, nil
            }
        }
    }
}
```




```
return "", fmt.Errorf("no title found")
}
```

我们随后添加了 workQueue 概念以及若干个 worker（Goroutines），它们从队列中读取任务。WaitGroup 则允许每个 worker 在处理完成后发出信号。

```go
package main

import (
    "context"
    "flag"
    "fmt"
    "io"
    "log"
    "net/http"
    "os"
    "strings"
    "sync"
    "time"
)

func main() {
    uris := []string{"https://github.com/alexellis",
        "https://github.com/openfaas",
        "https://github.com/inlets",
        "https://github.com/docker",
        "https://github.com/kubernetes",
        "https://github.com/moby",
        "https://github.com/hashicorp",
        "https://github.com/civo",
    }

    var w int
    flag.IntVar(&w, "w", 1, "amount of workers")
    flag.Parse()

    titleMap, errs := fetch(uris, w)
    if len(errs) > 0 {
        for _, err := range errs {
            fmt.Fprintf(os.Stderr, "error %s", err.Error())
        }
        os.Exit(1)
    }

    for k, v := range titleMap {
        fmt.Printf("%s has %s\n", k, v)
    }
}

func fetch(uris []string, workers int) (map[string]string, []error) {
    titles := make(map[string]string)

    var errs []error

    workQueue := make(chan string)

    wg := sync.WaitGroup{}
    wg.Add(workers)
    for i := 0; i < workers; i++ {
        worker := i
        go func(worker int, workQueue chan string) {
            log.Printf("[Worker: %d] Started work.", worker)

            for uri := range workQueue {
                log.Printf("[Worker: %d] Getting: %s", worker, uri)

                start := time.Now()
                title, err := titleOf(uri, time.Second*5)
                if err != nil {
                    errs = append(errs, err)
                }
                log.Printf("[Worker: %d] Got: %s (%.2fs)",
                    worker,
                    uri,
                    time.Since(start).Seconds())

                titles[uri] = title
            }
            log.Printf("[Worker: %d] Finished work.", worker)
            wg.Done()
        }(worker, workQueue)
    }

    go func() {
        for _, u := range uris {
            workQueue <- u
        }
        close(workQueue)
    }()

    wg.Wait()
    return titles, errs
}
```

-w 标志控制并发度。

观察使用单个 worker 与使用 4 个 worker 时输出和耗时上的差异。

```
$ time go run main.go -w 1
2021/06/18 18:42:30 [Worker: 0] Started work.
2021/06/18 18:42:30 [Worker: 0] Getting: https://github.com/alexellis
2021/06/18 18:42:32 [Worker: 0] Got: https://github.com/alexellis (1.82s)
2021/06/18 18:42:32 [Worker: 0] Getting: https://github.com/openfaas
2021/06/18 18:42:33 [Worker: 0] Got: https://github.com/openfaas (0.60s)
2021/06/18 18:42:33 [Worker: 0] Getting: https://github.com/inlets
2021/06/18 18:42:33 [Worker: 0] Got: https://github.com/inlets (0.44s)
2021/06/18 18:42:33 [Worker: 0] Getting: https://github.com/docker
2021/06/18 18:42:34 [Worker: 0] Got: https://github.com/docker (0.70s)
2021/06/18 18:42:34 [Worker: 0] Getting: https://github.com/kubernetes
2021/06/18 18:42:34 [Worker: 0] Got: https://github.com/kubernetes (0.55s)
2021/06/18 18:42:34 [Worker: 0] Getting: https://github.com/moby
2021/06/18 18:42:35 [Worker: 0] Got: https://github.com/moby (0.47s)
2021/06/18 18:42:35 [Worker: 0] Getting: https://github.com/hashicorp
2021/06/18 18:42:35 [Worker: 0] Got: https://github.com/hashicorp (0.45s)
2021/06/18 18:42:35 [Worker: 0] Getting: https://github.com/civo
2021/06/18 18:42:36 [Worker: 0] Got: https://github.com/civo (0.86s)
2021/06/18 18:42:36 [Worker: 0] Finished work.
https://github.com/openfaas has    <title>OpenFaaS · GitHub</title>
https://github.com/inlets has      <title>inlets · GitHub</title>
https://github.com/docker has      <title>Docker · GitHub</title>
https://github.com/kubernetes has  <title>Kubernetes · GitHub</title>
https://github.com/moby has        <title>Moby · GitHub</title>
https://github.com/hashicorp has   <title>HashiCorp · GitHub</title>
https://github.com/civo has        <title>Civo · GitHub</title>
https://github.com/alexellis has   <title>alexellis (Alex Ellis) · GitHub</title>

real    0m6.206s
user    0m0.556s
sys     0m0.188s
```

```
$ time go run main.go -w 4
2021/06/18 18:41:56 [Worker: 0] Started work.
2021/06/18 18:41:56 [Worker: 0] Getting: https://github.com/alexellis
2021/06/18 18:41:56 [Worker: 3] Started work.
2021/06/18 18:41:56 [Worker: 3] Getting: https://github.com/openfaas
2021/06/18 18:41:56 [Worker: 2] Started work.
2021/06/18 18:41:56 [Worker: 1] Started work.
2021/06/18 18:41:56 [Worker: 1] Getting: https://github.com/docker
2021/06/18 18:41:56 [Worker: 2] Getting: https://github.com/inlets
2021/06/18 18:41:57 [Worker: 2] Got: https://github.com/inlets (0.55s)
2021/06/18 18:41:57 [Worker: 2] Getting: https://github.com/kubernetes
2021/06/18 18:41:57 [Worker: 3] Got: https://github.com/openfaas (0.65s)
2021/06/18 18:41:57 [Worker: 3] Getting: https://github.com/moby
2021/06/18 18:41:57 [Worker: 1] Got: https://github.com/docker (0.89s)
2021/06/18 18:41:57 [Worker: 1] Getting: https://github.com/hashicorp
2021/06/18 18:41:57 [Worker: 2] Got: https://github.com/kubernetes (0.46s)
2021/06/18 18:41:57 [Worker: 2] Getting: https://github.com/civo
2021/06/18 18:41:58 [Worker: 3] Got: https://github.com/moby (0.70s)
2021/06/18 18:41:58 [Worker: 3] Finished work.
2021/06/18 18:41:58 [Worker: 0] Got: https://github.com/alexellis (1.45s)
2021/06/18 18:41:58 [Worker: 0] Finished work.
2021/06/18 18:41:58 [Worker: 2] Got: https://github.com/civo (0.53s)
2021/06/18 18:41:58 [Worker: 2] Finished work.
2021/06/18 18:41:58 [Worker: 1] Got: https://github.com/hashicorp (1.15s)
2021/06/18 18:41:58 [Worker: 1] Finished work.
https://github.com/docker has    <title>Docker · GitHub</title>
https://github.com/kubernetes has    <title>Kubernetes · GitHub</title>
https://github.com/moby has    <title>Moby · GitHub</title>
https://github.com/alexellis has    <title>alexellis (Alex Ellis) · GitHub</title>
https://github.com/civo has    <title>Civo · GitHub</title>
https://github.com/hashicorp has    <title>HashiCorp · GitHub</title>
https://github.com/inlets has    <title>inlets · GitHub</title>
https://github.com/openfaas has    <title>OpenFaaS · GitHub</title>

real    0m2.319s
user    0m0.545s
sys     0m0.101s
```

这大约相差 4 秒。我们仅通过实现并发就获得了这一速度提升。工作队列随后限制了打开请求的數量。

要在实际中看到这一模式，可在 faas-cli 中查看 build.go 命令。

## 第 8 章
### 使用数据库存储数据

几乎所有业务线应用程序都需要某种形式的存储，因此在本章中我将向你展示如何连接到 PostgreSQL 数据库。对于其他数据库，你需要找到不同的库，但方法会类似。

并非所有 Go 库都相同。有些使用纯 Go 代码，而其他库则链接到现有的 C/C++ 代码生态系统。那些引用 CGO 的库需要 CGO，这可能会引入其他问题和可移植性问题。

我在编写这本电子书时发现最有帮助的工具之一就是待办清单，因此让我们从这个例子开始。你可以根据自己的需要随意自定义模式、字段和操作。

为练习创建目录：

```
export GH_USERNAME="alexellis"
mkdir -p $GOPATH/src/github.com/$GH_USERNAME/todo-database/
cd $GOPATH/src/github.com/$GH_USERNAME/todo-database/
```

创建 schema.sql：

```
CREATE TABLE todo (
  id            INT GENERATED ALWAYS AS IDENTITY,
  description   text NOT NULL,
  created_date  timestamp NOT NULL,
  completed_date timestamp NULL
);
```

我们使用的是扁平模式，只有一个表。id 字段是生成的，然后我们有一个用于待办事项文本的较长字段，以及创建/完成日期字段。只有 completed_date 字段可以接受空值。

一旦你定义了模式，就该配置数据库或安装 PostgreSQL，以便获取凭据或连接字符串并创建模式。

我决定在 DigitalOcean 上使用 PostgreSQL 11 创建一个数据库。这是一项托管服务，你会在 AWS 和 GCP 等其他云提供商那里找到类似的服务。

你可以使用 psql 工具连接并创建数据库。或者，你也可以在应用程序启动时输入 CREATE 语句。一些作者编写代码来在应用程序启动时自动执行数据库创建和模式迁移等维护任务。

我从仪表板获得的连接字符串为： postgresql://doadmin:ildkg2my7g7lqqxh@todo-pg11-do-user-2197152-0.b.db.ondigitalocean.com:25060/defaultdb?sslmode=require

部署应用程序时，请注意不要硬编码任何机密数据。你可能希望使用具有严格权限的配置文件，或使用环境变量读取密码和地址。



### 创建数据库集群

### 选择数据库引擎

数据库集群运行单个数据库引擎，该引擎为一个或多个独立数据库提供支持。

![](img/0b5c3b498f62579835cf1d543b46de92_78_0.png)

### 选择集群配置

集群创建后，您可以随时添加、移除或调整节点大小。

![](img/0b5c3b498f62579835cf1d543b46de92_78_1.png)

图 8.1：在 DigitalOcean 上创建的托管 PostgreSQL 数据库

```
package main

import (
    "database/sql"
    "flag"
    "fmt"
    "time"
    _ "github.com/lib/pq"
)

type Todo struct {
    ID            int
    Description   string
    CreatedDate   time.Time
    CompletedDate *time.Time
}
```

这里，我们定义了一个 Todo 结构体，用于将数据库中的条目加载到内存中。我们还介绍了 database/sql 包，它可与不同库一起使用，但为操作提供单一接口。

在我们的案例中，我们将使用 lib/pq 库，它是“pure Go”，意味着我们无需启用 CGO 即可使用它。

接下来，定义连接数据库所需的所有标志，以及应用程序所需的标志。如果您编写的是服务器端软件，您可以从环境变量中读取这些值，或者如果您在 Kubernetes 上使用 OpenFaaS，则可以从挂载在 /var/openfaas/secrets/NAME 的文件读取。

```
func main() {
    var (
        user, password, host, dbName, sslMode, todo, action string
    )
    var port int
```

```
flag.StringVar(&user, "user", "", "PostgreSQL username")
flag.StringVar(&password, "password", "", "PostgreSQL password")
flag.StringVar(&host, "host", "", "PostgreSQL host")
flag.IntVar(&port, "port", 0, "PostgreSQL port")
flag.StringVar(&dbName, "dbname", "", "PostgreSQL database name")
flag.StringVar(&sslMode, "sslmode", "require", "PostgreSQL ssl mode")

flag.StringVar(&todo, "todo", "", "Todo item")
flag.StringVar(&action, "action", "create", "Action for todo item")

flag.Parse()
```

接下来，我们将定义尝试建立数据库连接的流程，然后是创建和列出操作。也许您可以自行编写 update 和 done 操作作为练习的扩展？

```
db, err := connect(user, password, host, dbName, sslMode, port)
if err != nil {
    panic(err)
}

switch action {
case "create":
    err := create(db, todo)
    if err != nil {
        panic(err)
    }
case "list":
    todos, err := list(db)
    if err != nil {
        panic(err)
    }
    for _, t := range todos {
        fmt.Printf("- %q\t%s\n", t.Description, t.CreatedDate.String())
    }
default:
    panic("Supported actions are: list, create")
}
}
```

现在进入 connect 方法。这里我们构造一个连接字符串，通常由托管 SQL 服务提供。如果没有，您可以从各个部分构造它。DigitalOcean 上的 PostgreSQL 服务还需要一个“strict” sslmode 标志。

```
func connect(user, password, host, dbName, sslMode string, port int) (*sql.DB, error) {
connStr := "postgres://" + user + ":" + password + "@" + host + ":" + fmt.Sprintf("%d", port) + "/" + dbName + "?sslmode=" + sslMode

db, err := sql.Open("postgres", connStr)
if err != nil {
    return nil, err
}

err = db.Ping()
if err != nil {
```

```
```go
return nil, err
}

return db, nil
}
```
```

这是如何执行插入操作的。注意 $1 会被替换为 `todo` 字符串。通过使用这种语法而不是 `fmt.Sprintf` 或字符串连接，我们在一定程度上获得了防止 SQL 注入攻击的保护，在这种攻击中，用户可能会在值中插入额外的 SQL 语句。

```
```go
func create(db *sql.DB, todo string) error {
    res, err := db.Query(`INSERT INTO
        todo
        (id, description, created_date)
        VALUES
        (DEFAULT, $1, now());`,
        todo)
    if err != nil {
        return err
    }
    defer res.Close()
    return nil
}
```
```

list 函数返回 Todo 结构体的切片。您可以使用相同的 $1 技术为 SELECT 语句指定键或排序顺序。

最后，Scan 函数用于使用正确的类型将行中的值填充到类型中。您看，我们无需将日期字符串解析为 `time.Time`，例如？

```
```go
func list(db *sql.DB) ([]Todo, error) {
    rows, err := db.Query(`SELECT
        id,
        description,
        created_date,
        completed_date
        FROM todo;`)

    if err != nil {
        return []Todo{},
            fmt.Errorf("unable to get from todo table: %w", err)
    }

    todos := []Todo{}
    defer rows.Close()
    for rows.Next() {
        result := Todo{}
        err := rows.Scan(&result.ID,
            &result.Description,
            &result.CreatedDate,
            &result.CompletedDate)
        if err != nil {
            return []Todo{}, fmt.Errorf("row scan error: %w", err)
        }
        todos = append(todos, result)
```

```
```
}
return todos, nil
}
```
```

然后就轮到您了，试试看：

```
```shell
$ go build && ./todo \
  -user doadmin \
  -password ildkg2my7g7lqqxh \
  -host todo-pg11-do-user-2197152-0.b.db.ondigitalocean.com \
  -port 25060 \
  -dbname defaultdb \
  -todo "Publish this book" \
  -action create
```
```

现在列出您的待办事项：

```
```shell
$ go build && ./todo \
  -user doadmin \
  -password ildkg2my7g7lqqxh \
  -host todo-pg11-do-user-2197152-0.b.db.ondigitalocean.com \
  -port 25060 \
  -dbname defaultdb \
  -action list

- "Publish this book"   2021-06-21 10:57:04.374785 +0000 +0000
```
```

接下来，您可以探索添加缺失的功能，并考虑使用表格并添加一些颜色。您可能还希望过滤掉所有具有完成日期的项目。查看 tabwriter 包以格式化您的 CLI 输出。

类似 Cobra 的 CLI 框架可以通过将操作变成动词来提高可用性，例如：

```
```shell
$ ./todo list
$ ./todo create "Publish the next version of this eBook"
$ ./todo close "Weekly shopping"
```
```

了解我们下面使用的两个库的更多信息：

- lib/pq
- database/sql

对于更完整的包含外键关系模式和自定义数据库函数的示例，请参阅我在 OpenFaaS 博客上的示例：How to build a Serverless Single Page App

## 第 9 章

### 编写自己的 YAML 配置文件

12 Factor Apps 的趋势是通过环境变量而不是文件使所有配置可用。这使得它们易于使用容器部署，因为文件往往需要额外的权限或创建和挂载文件系统。

然而，环境变量也有缺点，例如长度，以及当它们很多时的复杂性。由于所有输入都在同一级别，嵌套也很困难。您可能会发现配置文件是答案。

### YAML 实际应用的实用示例

在 OpenFaaS CLI 中，我们添加了一个配置文件来存储您登录的不同安装的凭据。CLI 还有一个用于您部署的函数的配置文件，名为 stack.yml。

```
version: 1.0
provider:
  name: openfaas
  gateway: http://127.0.0.1:8080

functions:
  gumroad-upgrade:
    lang: node12
    handler: ./gumroad-upgrade
    image: alexellis2/gumroad-upgrade:0.2.1
    environment:
      subject: "Your bonus upgrade to my video workshop"
      sender: sales@openfaas.com
      region: "eu-west-1"
    secrets:
      - ses-access-key-id
      - ses-access-token
      - seller-id
      - secret-url
```

配置构建和部署函数的 OpenFaaS YAML 文件示例

我使用最多的库是 gopkg.in/yaml.v2。它适合用例，是我解析或保存 YAML 的首选库。

### 读写您自己的 YAML 模式

创建一个新文件夹并为示例初始化它：

```
```bash
export GH_USERNAME="alexlellis"
mkdir -p $GOPATH/src/github.com/$GH_USERNAME/yaml-config/
cd $GOPATH/src/github.com/$GH_USERNAME/yaml-config/
```
```

要加载配置文件，您需要定义多个结构体并对其进行注释，就像我们对 JSON 示例所做的那样。

```
```go
type Spec struct {

    // Name name of the function
    Name string `yaml:"name"`


    // Image docker image name of the function
    Image string `yaml:"image"`

    Environment map[string]string `yaml:"environment,omitempty"`


    // Limits for the function
    Limits *FunctionResources `yaml:"limits,omitempty"`
}

// FunctionResources Memory and CPU
type FunctionResources struct {
    Memory string `yaml:"memory"`
    CPU    string `yaml:"cpu"`
}
```
```

如上所示，我们本会放置 `json:"field"` 的地方，我们只需写 yaml，然后继续使用非常相似的接口将文本反序列化为对象。

创建 main.go：

```
```go
package main

import (
    "fmt"
    "os"

    yaml "gopkg.in/yaml.v2"
)

// Add above structs here

func main() {
    bytesOut, err := os.ReadFile("config.yaml")
    if err != nil {
        panic(err)
    }

    spec := Spec{}
    if err := yaml.Unmarshal(bytesOut, &spec); err != nil {
        panic(err)
    }

    fmt.Printf("Function name: %s\tImage: %s\tEnvs: %d\n", spec.Name, spec.Image,
        len(spec.Environment))
}
```




试一试：

go run main.go

函数名称：gumroad-bot      镜像：ghcr.io/alexellis/gumroad-bot      环境变量：1

你可以使用 Marshal 函数将配置文件或 YAML 文件写入磁盘。请修改以下示例：

```
func main() {
    spec := Spec{
        Image: "docker.io/functions/figlet:latest",
        Name:  "figlet",
    }

    bytesOut, err := yaml.Marshal(spec)
    if err != nil {
        panic(err)
    }

    err = os.WriteFile("figlet.yaml", bytesOut, os.ModePerm)
    if err != nil {
        panic(err)
    }
    fmt.Printf("Wrote: figlet.yaml. OK.\n")
}
```

试一试：

```
$ go run main.go

Wrote: figlet.yaml. OK.

$ cat figlet.yaml

name: figlet
image: docker.io/functions/figlet:latest
```

在之前的工作中，我发现通过读取输入文件并使用这个库生成 YAML，我可以非常快速地创建大量 CI 任务。总的来说，它为我节省了很多时间。

### 合并对象

如果你创建了一个包含许多不同字段的大型 schema，那么最好维护一个示例文件，并允许用户为任何需要自定义的值提供覆盖。

我们在 OpenFaaS 项目中使用了 mergo 库，并且体验很好，不过你也可以找到其他实现类似功能的库。

这种方法适用于你内存中的任何结构体，并非 YAML 所特有。

为示例创建一个新文件夹：

```
export GH_USERNAME="alexellis"
mkdir -p $GOPATH/src/github.com/$GH_USERNAME/merge-objects
cd $GOPATH/src/github.com/$GH_USERNAME/merge-objects
```

API 的工作方式如下：

```
merged := Spec{}
```

```
overrides := Spec{}

err := mergo.Merge(merged, override, mergo.WithOverride)
if err != nil {
    return merged, err
}
```

下面是一个实际示例：

```
package main

import (
    "fmt"
    "github.com/imdario/mergo"
    yaml "gopkg.in/yaml.v2"
)

// Paste the struct definitions in here.

func main() {
    base := Spec{
        Image: "docker.io/functions/figlet:latest",
        Name:  "figlet",
    }

    production := Spec{
        Environment: map[string]string{"stage": "production"},
        Limits:      &FunctionResources{Memory: "1Gi", CPU: "100Mi"},
    }

    overrides := []Spec{
        base,
        production,
    }

    merged := Spec{}
    for _, override := range overrides {
        err := mergo.Merge(&merged, override, mergo.WithOverride)
        if err != nil {
            panic(err)
        }
    }

    bytesOut, err := yaml.Marshal(merged)
    if err != nil {
        panic(err)
    }

    fmt.Printf("Merged content:\n\n%s\n", string(bytesOut))
}
```

输出：

```
$ go run main.go

Merged content:

name: figlet
image: docker.io/functions/figlet:latest
environment:
    stage: production
limits:
    memory: 1Gi
    cpu: 100Mi
```

你看到 “stage” 字段和 limits 的生产配置是如何覆盖在基础配置之上的吗？

在代码中，你可以在哪里使用对象合并呢？

## 第10章

### 将版本信息注入你的二进制文件

在本章中，我将向你展示如何在构建时将变量注入到你的 Golang 可执行文件中。

我们在 OpenFaaS 社区中使用这一技术的两种方式如下：

- 注入版本信息，例如 Git 提交 ID（77b4dce）和 Git 标签（0.1.0）
- 添加平台信息，例如该二进制是面向 Raspberry Pi 还是台式 PC
- 添加用于验证 open-core 功能许可证的公钥

这些信息会成为编译后应用程序的一部分，但仅在构建时确定一次，而不是在运行时确定。

下面是一个示例，Docker 项目的 CLI 中包含了 77b4dce 提交 ID，以及构建它时使用的 Go 版本。

```
$ docker version
Client: Docker Engine - Community
  Version:           19.03.13
  API version:       1.40
  Go version:        go1.13.15
  Git commit:        4484c46d9d
  Built:             Wed Sep 16 17:02:52 2020
  OS/Arch:           linux/amd64
  Experimental:      false
```

为什么要添加版本信息？

当用户提交错误报告时，应用程序中带有版本号有多么有用和宝贵，怎么说都不为过。它还可以帮助你发现过时的版本，并让用户通过运行程序的版本命令来验证他们正在使用的版本。

### 捕获有用的变量

在开始之前，想一想在构建时注入哪些内容更有意义？它可以是任何东西，从 CI 机器的主机名，到 Web 服务调用的结果，或者更常见的 Git 日志中的最后一条提交 ID。

我们就使用最后一条 Git 提交 ID。

创建一个带有 README 的测试 Git 项目

```
$ mkdir /tmp/git-tester && \
cd /tmp/git-tester && \
git init && \
echo "Let's work with Git" > README && \
git add . && \
git commit -m "Initial" && \
```

```
echo "Let's keep working" >> README && \
git add . && \
git commit -m "First update"
```

现在，你会在 Git 日志中看到两次提交：

```
$ git log
commit 67b05a31758848e1e5237ad5ae1dc11c22d4e71e
Author: Alex Ellis <alexellis2@gmail.com>
Date:   Tue Aug 8 08:37:20 2017 +0100

    First update

commit 9b906b6d02d803111250a974ed8042c4760cde7f
Author: Alex Ellis <alexellis2@gmail.com>
Date:   Tue Aug 8 08:37:20 2017 +0100

    Initial
```

下面是如何找到最后一次提交的 ID：

```
$ git rev-list -1 HEAD
67b05a31758848e1e5237ad5ae1dc11c22d4e71e
```

接下来，我们可以将其捕获到一个环境变量中：

```
$ export GIT_COMMIT=$(git rev-list -1 HEAD) && \
  echo $GIT_COMMIT

67b05a31758848e1e5237ad5ae1dc11c22d4e71e
```

### 准备你的代码

让我们构建一个示例，打印我们在构建时注入的版本。

```
export GH_USERNAME="alexellis"
mkdir -p $GOPATH/src/github.com/$GH_USERNAME/inject-commit/
cd $GOPATH/src/github.com/$GH_USERNAME/inject-commit/
```

编辑 main.go：

```
package main

import (
    "fmt"
)

func main() {
    fmt.Println("Hello world")
}
```

为了传递构建时变量，我们需要在 main 包中创建一个变量。我们将其命名为 var GitCommit string。

```
package main
```

```
flag.BoolVar(&version, "version", false, "Print the version")
flag.Parse()

if version {
    fmt.Printf("Version: %s\n", GitCommit)
}
fmt.Printf("Hello world\n")
}
```

```
$ go build -ldflags "-X main.GitCommit=$GIT_COMMIT" && ./inject-commit -version
Version: a38eef50779c6e659b405a14e80b51148e6d4cb1

Hello world

$ go build -ldflags "-X main.GitCommit=$GIT_COMMIT" && ./inject-commit
Hello world
```

### 使用 Docker 完成

一旦你确定了构建时变量，你可能需要更新你的 Dockerfile。

编写一个 Dockerfile：

```
FROM golang:1.22

WORKDIR /go/src/github.com/alexellis/inject-commit
COPY .git .
COPY app.go .

RUN GIT_COMMIT=$(git rev-list -1 HEAD) && \
    go build -ldflags "-X main.GitCommit=$GIT_COMMIT"

CMD [".git-tester", "-version"]
```

*Dockerfile*

运行构建，然后试一试：

```
$ docker build -t inject-commit .
$ docker run -ti inject-commit
Hello world, version: 67b05a31758848e1e5237ad5ae1dc11c22d4e71e
```

在使用 Go 构建 Docker 镜像时，你需要使用多阶段构建，只发布你的二进制文件，而不是发布 golang:1.22 镜像——该镜像是 SDK，与你的程序相比体积相对较大。你还需要切换到非 root 用户，以便容器能够在没有不必要特权的情况下运行。

这只是一个最小的示例，向你展示如何开始使用 Docker 和 Go 构建时变量。你可以更进一步，通过使用多阶段构建来优化 Docker 镜像的大小。

### 生产环境中的示例

查看 alexellis/k3sup，了解带有版本信息的静态二进制文件。对于同时随 Docker 镜像发布的二进制文件，请查看 openfaas/of-watchdog 或 openfaas/faas-cli。

```
$ k3sup version
_  _____
```

```
| |-|_-|/ _-_- _-_- 
| |/ | \ _- | | | | ' \ 
| < __) \ _ \ | ] | | | ) | 
|-| \ _-_/ _- \_, | . \ 
          |-| 
Version: 0.9.13
Git Commit: 95fc8b074a6e0ea48ea03a695491e955e32452ea
```

你可以看到，我在这里更进一步添加了一个 ASCII 标志，如果你亲自运行这个示例，你会看到该标志也是红色的。请查看代码了解具体实现。




## 第11章

### 在应用程序中嵌入数据

将除代码之外的额外资源随应用程序一起发布可能会很有用。一种常见的方法是嵌入文件或数据。

在“使用数据库存储数据”章节中，我们创建了一个待办事项应用，该应用需要手动创建模式来定义表。但如果我们的应用程序在启动时能够创建表（如果它尚不存在），会怎样呢？

从 Go 1.16 开始，embed 包使这变得简单。在此之前需要许多第三方库。

Go 文档展示了三种实现方法：

```go
import _ "embed"

//go:embed schema.sql
var tableCreate string
print(tableCreate)
```

在构建时，schema.sql 的内容将被构建到应用程序中，并通过 tableCreate 字符串提供。这与我们之前看到的将版本注入应用程序的技术非常相似。

如果你有一个图像，那么你希望将其字节编码为二进制 []byte 切片。

```go
import _ "embed"

//go:embed logo.png
var logo []byte
fmt.Printf("Total bytes: %d\n", len(logo))
```

一旦在内存中，logo 就可以通过 HTTP 连接提供给客户端、被修改或写入磁盘等。

使用 embed.FS 接口意味着与前一个示例不同，数据不会保存在变量的内存中，可以按需加载。这种方法对于大文件很有用。

```go
import "embed"

//go:embed ubuntu-20-cloudinit.iso
var f embed.FS
data, _ := f.ReadFile("ubuntu-20-cloudinit.iso")
fmt.Printf("Total bytes: %d\n", len(data))
```

Go 是一种非常好的系统编程语言，你会找到许多用于管理文件系统和网络的包。你可以潜在地在应用程序内部分发类似 ISO 镜像的东西，以便随时将其写入磁盘。

我们将要查看的第四个选项是我在想要随用 Go 编写的 HTTP 服务器或 API 一起分发类似 React.js 前端时会使用的方法。

```go
import "embed"

// frontend holds our static web server content.
//go:embed image/* template/*
//go:embed public/index.html
//go:embed css/*
var frontend embed.FS
```

现在你可以简单地将 embed.FS 链接到自定义 HTTP 中间件或处理器，并从特定路由或路径向用户提供文件。你将在本书后面了解更多关于 HTTP 服务器的内容，不过这是 Go 文档中给出的示例：

```go
http.Handle("/public/",
	http.StripPrefix("/public/",
		http.FileServer(http.FS(frontend))))
```

你的 API 可以绑定到路径 /api/v1/，然后任何你嵌入的静态内容都将从 /public/ 提供服务。

## 第12章

### 使用模板创建动态内容

模板用于用在运行时提供的输入替换文件或文本块（模板）中的标记或表达式。

它们看起来与前端模板技术（如 Embedded Ruby (ERb)）中发现的表达式相似，因此你可能已经觉得它们很直观。

模板可以简单到单行文本，也可以是多行块。模板可以从磁盘读取、通过互联网读取，或保存在内存中的 const 中。

下面是一个基于 Golang 文档的示例：

```
Dear {{.Name}},

{{if .Attended}}
It was a pleasure to see you at the wedding.
{{- else}}
It is a shame you couldn't make it to the wedding.
{{- end}}

Best wishes,
Alex
```

首先，我们需要将模板加载到内存中，然后构造一个类型化结构体或内联结构体以传递要放置在文件中的值，然后我们执行它以获得结果。.Name 将被直接替换，但 .Attended 将导致以下两句话之一被添加到信件中。

```go
package main

import (
    "bytes"
    "fmt"
    "text/template"
)

const letter = `Dear {{.Name}},
{{if .Attended}}
It was a pleasure to see you at the wedding.
{{- else}}
It is a shame you couldn't make it to the wedding.
{{- end}}
Best wishes,
Alex`

func main() {
```

```go
people := []struct {
    Name     string
    Attended bool
}{
    {
        Name:     "Alex",
        Attended: true,
    },
    {
        Name:     "Mick",
        Attended: false,
    },
}

t := template.Must(template.New("letter").Parse(letter))

for _, person := range people {
    buffer := bytes.Buffer{}
    err := t.Execute(&buffer, person)
    if err != nil {
        panic(err)
    }
    fmt.Printf("Letter for %s:\n\n%s\n", person.Name, buffer.String())
}
```

运行示例我们看到以下输出：

```
$ go run main.go
Letter for Alex:

Dear Alex,

It was a pleasure to see you at the wedding.
Best wishes,
Alex

Letter for Mick:

Dear Mick,

It is a shame you couldn't make it to the wedding.
Best wishes,
Alex
```

每当我想为应用程序添加 HTML 前端时，我就会使用 Go 模板并将 HTML 模板文件与代码一起嵌入。

### 高级模板：range 与自定义函数

我在我的赞助商门户中使用模板来列出并打印出我新闻通讯的所有以前版本。

以下是打印出该列表的代码片段：

![](img/0b5c3b498f62579835cf1d543b46de92_96_0.png)

图 12.1：以前新闻邮件的列表

```
<div class="card">
  <h5 class="card-header">Insiders Updates</h5>
  <div class="card-body">
    <h5 class="card-title">Click on an update below, or use your browser to search for topics.</h5>
    <ul>
      <!-- Be a good person, and do not scrape this HTML -->
      {{ range $in, $el:= .Updates }}
        {{ if ($.Updates.YearBreak $in) }}
        </ul>
        <p><b>{{ $el.Date.Year }}</b></p>
        <ul>
        {{ end }}
        <li id="{{ $el.ID }}"><a href="{{ $.Path "/update" }}?id={{ $el.ID }}">{{ $el.Description }}</a></li>
      {{ end }}
    </ul>
  </div>
</div>
```

在示例中，我使用了 range 关键字遍历 Updates 切片，其中包含多个 Update 结构体。

事情随后变得稍微复杂一些，因为我想根据帖子的年份来拆分列表，以便将其拆分为块或组。

在行 {{ if ($.Updates.YearBreak $in) }} 中，你可以看到我调用一个函数来确定何时换行。将自定义函数添加到模板的最简单方法是向模板中访问的类型添加函数。

```go
// Update represents an InsidersUpdate stored as a Gist
type Update struct {
    ID          string    `json:"id,omitempty"`
    Description string    `json:"description,omitempty"`
    Date        time.Time `json:"date,omitempty"`
    MarkdownURL string    `json:"markdownUrl,omitempty"`
    HTMLURL     string    `json:"htmlUrl,omitempty"`
}

type Updates []Update

// YearBreak returns whether the previous item was in
// another year
func (u Updates) YearBreak(i int) bool {
    if i == 0 {
        return true
    }

    return u[i-1].Date.Year() != u[i].Date.Year()
}
```

通过检查当前项的索引和前一项，我们可以确定是否在年份和电子邮件列表的断点处。

### 实际模板 - arkade

我要分享的最后一个示例是 arkade 项目，其中模板对于确定要下载的 CLI 的哪个版本很有用。

如果所有维护者和供应商在 CLI 命名上使用一种约定，那么我们只需要一个模板即可用于所有下载，但事实并非如此。

你可能想知道为什么这些模板被编译到 Go 二进制文件中？Tool 结构体可以被 Marshal 到 JSON 文件中以进行动态更新，但将所有内容放在一个地方并能够快速进行单元测试似乎对我们有效。

```
tools = append(tools,
Tool{
Owner:      "inlets",
Repo:       "inlets-pro",
Name:       "inlets-pro",
Description: "Cloud Native Tunnel for HTTP and TCP traffic.",
BinaryTemplate: `{{ if HasPrefix .OS "ming" -}}
{{.Name}}.exe
{{- else if eq .OS "darwin" -}}
{{.Name}}-darwin
{{- else if eq .Arch "armv6l" -}}
{{.Name}}-armhf
{{- else if eq .Arch "armv7l" -}}
{{.Name}}-armhf
{{- else if eq .Arch "aarch64" -}}
```




```
{{.Name}}-arm64
{{- else -}}
{{.Name}}
{{- end -}}`,
```

当评估此模板时，它会获取运行 uname -a 的信息，然后确定适用于您的操作系统和硬件类型的正确文件名。

使用 Go 模板的一个缺点是它们无法进行静态验证。它们仅在执行时才会被验证，因此对于 arkade，我们引入了一项政策，即编写单元测试以覆盖每个代码路径。

正如我们在上一章中所学到的，go test -cover 可以帮助我们验证是否执行了所有代码路径。

```go
func Test_DownloadInletsProCli(t *testing.T) {
    tools := MakeTools()
    name := "inlets-pro"

    tool := getTool(name, tools)

    tests := []test{
        {
            os:      "ming",
            arch:    arch64bit,
            version: "0.8.3",
            url:     `https://github.com/inlets/inlets-pro/releases/download/0.8.3/inlets-pro.exe`,
        },
        {
            os:      "linux",
            arch:    arch64bit,
            version: "0.8.3",
            url:     `https://github.com/inlets/inlets-pro/releases/download/0.8.3/inlets-pro`,
        },
        {
            os:      "linux",
            arch:    archARM64,
            version: "0.8.3",
            url:     `https://github.com/inlets/inlets-pro/releases/download/0.8.3/inlets-pro-arm64`,
        },
        {
            os:      "darwin",
            arch:    arch64bit,
            version: "0.8.3",
            url:     `https://github.com/inlets/inlets-pro/releases/download/0.8.3/inlets-pro-darwin`,
        },
    }

    for _, tc := range tests {
        got, err := tool.GetURL(tc.os, tc.arch, tc.version)
        if err != nil {
            t.Fatal(err)
        }
        if got != tc.url {
```

## 第13章

### 编写一个 HTTP 服务器

使用 Go 编写的最有用的项目之一是 HTTP 服务器。它也是仅使用标准库文件即可开始的最简单的项目之一。

```go
package main

import (
    "fmt"
    "log"
    "net/http"
    "time"
)

func main() {
    http.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
        log.Printf("Request received")
        w.Write([]byte("Hello world"))
    })

    port := 8080
    s := &http.Server{
        Addr:         fmt.Sprintf(":%d", port),
        ReadTimeout:  10 * time.Second,
        WriteTimeout: 10 * time.Second,
        MaxHeaderBytes: 1 << 20,
    }
    log.Printf("Listening on port: %d\n", port)
    log.Fatal(s.ListenAndServe())
}
```

测试一下：

```bash
# In terminal 1
go run main.go

# In terminal 2
$ curl http://localhost:8080 ; echo

Hello world
```

http.Request 包含 HTTP 请求的上下文和内容，您可以在此处或在 IDE 中的 IntelliSense 中探索源代码。

#### 读取请求

HTTP 请求有几种发送数据的方式，您可以在函数中使用这些方式来决定做什么：

- 正文
- HTTP 头
- 查询字符串
- 路径
- 主机头

创建一个新项目并测试：

```bash
export GH_USERNAME="alexellis"
mkdir -p $GOPATH/src/github.com/$GH_USERNAME/yaml-config/
cd $GOPATH/src/github.com/$GH_USERNAME/yaml-config/

go mod init http-server

touch main.go
```

这是一个如何读取它们的示例：

```go
package main

import (
    "fmt"
    "io"
    "log"
    "net/http"
    "time"
)

func main() {
    http.HandleFunc("/info", func(w http.ResponseWriter, r *http.Request) {
        log.Printf("==================================================")
        log.Printf("Query-string: %s", r.URL.RawQuery)
        log.Printf("Path: %s", r.URL.Path)
        log.Printf("Method: %s", r.Method)
        log.Printf("Path: %s", r.Host)
        for k, v := range r.Header {
            log.Printf("Header %s=%s", k, v)
        }

        if r.Body != nil {
            body, _ := io.ReadAll(r.Body)
            log.Printf("Body: %s", string(body))
        }
        log.Printf("==================================================")

        w.WriteHeader(http.StatusAccepted)
    })

    port := 8080
    s := &http.Server{
        Addr: fmt.Sprintf(":%d", port),
        ReadTimeout: 10 * time.Second,
        WriteTimeout: 10 * time.Second,
        MaxHeaderBytes: 1 << 20,
    }
    log.Printf("Listening on port: %d\n", port)
    log.Fatal(s.ListenAndServe())
}
```

让我们使用 curl 尝试一下 HTTP GET 和 HTTP POST：

```bash
# Terminal 1
$ go run main.go
2021/06/08 11:11:30 Listening on port: 8080

# Terminal 2
$ curl -i http://127.0.0.1:8080/info

2021/06/08 11:11:37 ====================================================
2021/06/08 11:11:37 Query-string:
2021/06/08 11:11:37 Path: /info
2021/06/08 11:11:37 Method: GET
2021/06/08 11:11:37 Path: localhost:8080
2021/06/08 11:11:37 Header User-Agent=[curl/7.68.0]
2021/06/08 11:11:37 Header Accept=[*/*]
2021/06/08 11:11:37 Body:
2021/06/08 11:11:37 ====================================================
```

注意 curl 发送的 User-Agent，以及缺少 HTTP 正文。我们还获得了路径，该路径被内部路由处理用来运行我们定义的函数。

```bash
# Terminal 2
$ curl -i -H "Content-type: application/json" \
-d '{"mode": "green"}' http://localhost:8080/info?insert=true

2021/06/08 11:13:28 ====================================================
2021/06/08 11:13:28 Query-string: insert=true
2021/06/08 11:13:28 Path: /info
2021/06/08 11:13:28 Method: POST
2021/06/08 11:13:28 Path: localhost:8080
2021/06/08 11:13:28 Header Content-Length=[17]
2021/06/08 11:13:28 Header User-Agent=[curl/7.68.0]
2021/06/08 11:13:28 Header Accept=[*/*]
2021/06/08 11:13:28 Header Content-Type=[application/json]
2021/06/08 11:13:28 Body: {"mode": "green"}
2021/06/08 11:13:28 ====================================================
```

这里我们传递了 JSON，因此可以看到 content-type 和 body 与 POST 方法一起定义。

#### 高级路由处理

您可以向 HTTP 处理程序添加逻辑，使其仅响应某些 HTTP 方法，或根据路径采取不同的操作，不过也有许多可用的库可以减少代码重复。

Gorilla 的 mux 是最受欢迎的之一，并在 OpenFaaS 和 inlets 项目中使用。

在此示例中，函数路径可以接受一个名称作为参数，该名称将被解析并在无需任何用户操作的情况下提供。正则表达式允许字母数字加连字符，并且至少需要一个字符。

```go
r.HandleFunc("/function/{name:[-a-zA-Z_0-9-]+}", functionProxy)
```

在处理程序内部，mux.Vars() 辅助函数用于查询名称：

```go
return func(w http.ResponseWriter, r *http.Request) {
    vars := mux.Vars(r)
    name := vars["name"]
    log.Printf("Invoking function: %s", name)
}
```

该库还支持流式风格来定义行为，其中方法可以链接起来定义逻辑。

在此示例中，不同的 HTTP 动词被绑定到不同的处理程序，以管理用于管理函数的 REST 端点。

```go
r.HandleFunc("/system/functions", listFunctions).Methods(http.MethodGet)
r.HandleFunc("/system/functions", deployFunction).Methods(http.MethodPost)
r.HandleFunc("/system/functions", deleteFunction).Methods(http.MethodDelete)
r.HandleFunc("/system/functions", updateFunction).Methods(http.MethodPut)
```

让我们尝试一个完整示例：

```bash
export GH_USERNAME="alexellis"
mkdir -p $GOPATH/src/github.com/$GH_USERNAME/mux/
cd $GOPATH/src/github.com/$GH_USERNAME/mux/
go mod init mux

touch main.go
```

然后将此代码添加到 main.go：

```go
package main

import (
    "fmt"
    "log"
    "net/http"
    "time"

    "github.com/gorilla/mux"
)

func main() {

    router := mux.NewRouter()
    router.HandleFunc("/customer/{id:[-a-zA-Z_0-9.]+}", func(w http.ResponseWriter, r *http.Request) {
        v := mux.Vars(r)
        id := v["id"]
        if id == "alex" {
            w.Write([]byte(fmt.Sprintf("Found customer: %s", id)))
        } else {
            http.Error(w, fmt.Sprintf("Customer %s not found", id), http.StatusNotFound)
        }
    })

    tcpPort := 8080
    s := &http.Server{
        Addr:         fmt.Sprintf(":%d", tcpPort),
        ReadTimeout:  time.Second * 10,
        WriteTimeout: time.Second * 10,
```


```go
MaxHeaderBytes: http.DefaultMaxHeaderBytes, // 1MB - can be overridden by setting Server.MaxHeaderBytes.
    Handler:        router,
}
log.Printf("Listening on: %d", tcpPort)
log.Fatal(s.ListenAndServe())
}
```

然后试试看：

```text
# Terminal 1
$ go run main.go

# Terminal 2
$ curl -i http://127.0.0.1:8080/customer/alex

HTTP/1.1 200 OK
Date: Tue, 08 Jun 2021 10:32:16 GMT
Content-Length: 20
Content-Type: text/plain; charset=utf-8

Found customer: alex

$ curl -i http://127.0.0.1:8080/customer/john

HTTP/1.1 404 Not Found
Content-Type: text/plain; charset=utf-8
X-Content-Type-Options: nosniff
Date: Tue, 08 Jun 2021 10:32:55 GMT
Content-Length: 24

Customer john not found
```

### 编写 HTTP 中间件

HTTP 中间件是一种在端点的主 HTTP 处理器执行之前或之后运行的函数。你可能需要这样做的原因包括：日志记录与追踪、身份验证与授权，以及应用其他规则或解析。

让我们尝试一个完整的示例，该示例会拒绝任何没有 Bearer 头（通常用于身份验证）的 HTTP 请求：

```sh
export GH_USERNAME="alexellis"
mkdir -p $GOPATH/src/github.com/$GH_USERNAME/http-bearer
cd $GOPATH/src/github.com/$GH_USERNAME/http-bearer
go mod init http-bearer

touch main.go
```

代码如下：

```go
package main

import (
    "fmt"
```
```
"log"
"net/http"
"os"
"time"
)

func makeAuth(token string, next http.HandlerFunc) http.HandlerFunc {
    return func(w http.ResponseWriter, r *http.Request) {
        if b := r.Header.Get("Authorization"); len(b) == 0 || b != "Bearer: "+token {
            http.Error(w, "Not authorized", http.StatusUnauthorized)
        } else {
            next(w, r)
        }
    }
}

func main() {
    token := os.Getenv("TOKEN")
    next := func(w http.ResponseWriter, r *http.Request) {
        w.Write([]byte("Authorized"))
    }

    http.HandleFunc("/customer/", makeAuth(token, next))

    tcpPort := 8080
    s := &http.Server{
        Addr:           fmt.Sprintf(":%d", tcpPort),
        ReadTimeout:    time.Second * 10,
        WriteTimeout:   time.Second * 10,
        MaxHeaderBytes: http.DefaultMaxHeaderBytes,
    }
    log.Printf("Listening on: %d", tcpPort)
    log.Fatal(s.ListenAndServe())
}
```

请注意，makeAuth 函数在 HTTP 授权头周围添加了一个 if 守卫；如果未找到该头部或令牌不匹配，则不会进行“next”HTTP 调用。这样，你可以按需链式使用任意数量的 HTTP 中间件，例如先授权再记录日志，以及其他任何需要的操作。

试试运行：

```
# Terminal 1
go run main.go

# Terminal 2

curl http://127.0.0.1:8080/customer/alex -H "Authorization: Bearer: test"
Authorized

curl http://127.0.0.1:8080/customer/alex
Not authorized
```

```go
})

s := &http.Server{
	Addr:           fmt.Sprintf(":%d", port),
	ReadTimeout:    readTimeout,
	WriteTimeout:   writeTimeout,
	MaxHeaderBytes: 1 << 20, // Max header of 1MB
	Handler:        metricsMux,
}

s.ListenAndServe()
}
```

现在：

```bash
# Terminal 1
go run main.go

# Terminal 2
curl http://127.0.0.1:8080/metrics
```

你会看到关于 `/metrics` 端点本身的 HTTP 指标：

```text
# HELP promhttp_metric_handler_requests_in_flight Current number of scrapes being served.
# TYPE promhttp_metric_handler_requests_in_flight gauge
promhttp_metric_handler_requests_in_flight 1
# HELP promhttp_metric_handler_requests_total Total number of scrapes by HTTP status code.
# TYPE promhttp_metric_handler_requests_total counter
promhttp_metric_handler_requests_total{code="200"} 1
promhttp_metric_handler_requests_total{code="500"} 0
promhttp_metric_handler_requests_total{code="503"} 0
```

然后你还会看到内存信息、Go 版本、活跃的 Goroutine 数量以及许多其他细节。

```text
# HELP go_goroutines Number of goroutines that currently exist.
# TYPE go_goroutines gauge
go_goroutines 8

# HELP go_info Information about the Go environment.
# TYPE go_info gauge
go_info{version="go1.15.6"} 1

# HELP go_memstats_alloc_bytes Number of bytes allocated and still in use.
# TYPE go_memstats_alloc_bytes gauge
go_memstats_alloc_bytes 1.152704e+06
# HELP go_memstats_alloc_bytes_total Total number of bytes allocated, even if freed.
# TYPE go_memstats_alloc_bytes_total counter
go_memstats_alloc_bytes_total 1.152704e+06
```

一旦部署了 Prometheus，你就可以配置它来抓取 Go 应用程序。如果你从其 GitHub 发布页面下载 Prometheus，则可以将它作为普通可执行程序运行。

在压缩包中你会看到 prometheus 和 prometheus.yml 文件。解压文件并编辑 prometheus.yaml。

```yaml
# my global config
global:
  scrape_interval:      15s # Set the scrape interval to every 15 seconds. Default is every 1 minute.
```
```
evaluation_interval: 15s # Evaluate rules every 15 seconds. The default is every 1 minute.
# scrape_timeout is set to the global default (10s).

# Alertmanager configuration
alerting:
  alertmanagers:
  - static_configs:
    - targets:
      # - alertmanager:9093

# Load rules once and periodically evaluate them according to the global
  'evaluation_interval'.
rule_files:
  # - "first_rules.yml"
  # - "second_rules.yml"

# A scrape configuration containing exactly one endpoint to scrape:
# Here it's Prometheus itself.
scrape_configs:
  # The job name is added as a label `job=<job_name>` to any timeseries scraped from this
  config.
  - job_name: 'prometheus'

    # metrics_path defaults to '/metrics'
    # scheme defaults to 'http'.
    static_configs:
    - targets: ['localhost:9090']
```

在 scrape_configs 下，为你的微服务添加一个 job 名称和抓取目标。

```
# The job name is added as a label `job=<job_name>` to any timeseries scraped from this
  config.
- job_name: 'service'

  # metrics_path defaults to '/metrics'
  # scheme defaults to 'http'.
  static_configs:
  - targets: ['localhost:8080']
```

如果部署在集群或网络中，目标地址将从 localhost 改为服务可达的 IP 地址或 DNS 名称，例如：gateway:8080。

```
# In Terminal 1
$ ./prometheus --config.file=./prometheus.yml

# In Terminal 2
$ go run main.go
```

你可以通过以下地址访问 Prometheus UI：

http://127.0.0.1:9090

在“Status”和“Targets”下，你可以查看这两个目标以及它们上次被抓取的时间。如果访问端点时有任何问题，你也可以在这里看到。

抓取配置

![](img/0b5c3b498f62579835cf1d543b46de92_109_0.png)

图 14.1：抓取配置

指标浏览器（地球形按钮）会显示所有可用于浏览的指标。

![](img/0b5c3b498f62579835cf1d543b46de92_109_1.png)

图 14.2：指标浏览器

表格视图在查看数字时也很有用。

你可以编写的最有用的查询之一是检查服务上某些 HTTP 请求的速率。此查询查找 200 / OK 响应，但你可能想挑选出特定的错误码来检测问题。

显示查询速率的图表

```
rate(
    promhttp_metric_handler_requests_total{
        code="200",
        job="service"
    }[1m]
)
```

在 1 分钟窗口内，针对 service 作业的 HTTP 200 状态码，追踪 promhttp_metric_handler_requests_total 指标的调用速率。

请记住，这只是 Prometheus 端点本身的状态码，因此它还没有对我们服务可能发出的任何 API 调用进行检测。不过，这仍有价值，因为它还可以通过类似的查询来跟踪尚未清理的 Goroutine 泄漏：

```
rate(
    go_goroutines{
        job="service"
    }[1m]
)
```

请注意，“job” 正在查看我们 HTTP 服务器的抓取端点。如果你愿意，你也可以查看 Prometheus 自身运行的 Goroutine 数量，因为它在“prometheus”作业下对自身进行检测。

### 为我们的微服务跟踪 HTTP 指标

我们现在将构建一个微服务，它可以为任何输入内容生成 SHA256 哈希，并对有效输入返回 200 状态码。当请求体不存在且 HTTP 方法不是 POST 时，该服务将返回 400 错误。

完成后，我们将能够为你希望检测的任何 HTTP 中间件或处理器测量速率、错误和持续时间（RED）指标。

```
export GH_USERNAME="alexellis"
mkdir -p $GOPATH/src/github.com/$GH_USERNAME/custom-metrics/
cd $GOPATH/src/github.com/$GH_USERNAME/custom-metrics/
go mod init metrics

touch main.go
touch metrics.go
```

创建 metrics.go：

```go
package main

import (
    "net/http"

    "github.com/prometheus/client_golang/prometheus"
    "github.com/prometheus/client_golang/prometheus/promauto"
    "github.com/prometheus/client_golang/prometheus/promhttp"
)

type HttpMetrics struct {
    RequestsTotal           *prometheus.CounterVec
    RequestDurationHistogram *prometheus.HistogramVec
}

func NewHttpMetrics() HttpMetrics {
    return HttpMetrics{
        RequestsTotal: promauto.NewCounterVec(prometheus.CounterOpts{
            Subsystem: "http",
            Name:      "requests_total",
            Help:      "total HTTP requests processed",
        }, []string{"code", "method"}),
        RequestDurationHistogram: promauto.NewHistogramVec(prometheus.HistogramOpts{
```




```
Subsystem: "http",
Name:    "request_duration_seconds",
Help:    "Seconds spent serving HTTP requests.",
Buckets: prometheus.DefBuckets,
}, []string{"code", "method"}),
}
}

// InstrumentHandler instruments any HTTP handler for the request
// total and request duration metric
func InstrumentHandler(next http.HandlerFunc, _http HttpMetrics) http.HandlerFunc {
    return promhttp.InstrumentHandlerCounter(_http.RequestsTotal,
        promhttp.InstrumentHandlerDuration(_http.RequestDurationHistogram, next))
}
```

现在创建 main.go:

```
package main

import (
    "crypto/sha256"
    "encoding/hex"
    "fmt"
    "io"
    "log"
    "net/http"
    "time"

    "github.com/prometheus/client_golang/prometheus/promhttp"
)

// computeSum generates a SHA256 hash of the body
func computeSum(body []byte) []byte {
    h := sha256.New()
    h.Write(body)
    hashed := hex.EncodeToString(h.Sum(nil))
    return []byte(hashed)
}

func main() {
    port := 8080
    readTimeout := time.Millisecond * 500
    writeTimeout := time.Millisecond * 500

    mux := http.NewServeMux()

    httpMetrics := NewHttpMetrics()
    instrumentedHash := InstrumentHandler(func(w http.ResponseWriter, r *http.Request) {
        if r.Method != http.MethodPost {
            w.WriteHeader(http.StatusBadRequest)
            return
        }
        if r.Body != nil {
            body, _ := io.ReadAll(r.Body)

        fmt.Fprintf(w, "%s", computeSum(body))
    }
}, httpMetrics)

mux.HandleFunc("/hash", instrumentedHash)

mux.Handle("/metrics", promhttp.Handler())

s := &http.Server{
    Addr:           fmt.Sprintf(":%d", port),
    ReadTimeout:    readTimeout,
    WriteTimeout:   writeTimeout,
    MaxHeaderBytes: 1 << 20, // Max header of 1MB
    Handler:        mux,
}
log.Printf("Listening on: %d", port)
s.ListenAndServe()
}
```

运行示例并确保 Prometheus 也在运行。

```
# Terminal 1
$ go run .

# Terminal 2

$ curl -i http://127.0.0.1:8080/hash
HTTP/1.1 400 Bad Request
Date: Tue, 08 Jun 2021 14:30:29 GMT
Content-Length: 0

$ curl -i http://127.0.0.1:8080/hash -d "Golang"

HTTP/1.1 200 OK
Date: Tue, 08 Jun 2021 14:30:51 GMT
Content-Length: 64
Content-Type: text/plain; charset=utf-8

50e56e797c4ac89f7994a37480fce29a8a0f0f123a695e2dc32d5632197e2318
```

现在查看指标端点，或访问 Prometheus 仪表板。

```
$ curl http://localhost:8080/metrics

# HELP http_request_duration_seconds Seconds spent serving HTTP requests.
# TYPE http_request_duration_seconds histogram
http_request_duration_seconds_bucket{code="200",method="post",le="1"} 1
http_request_duration_seconds_sum{code="200",method="post"} 0.000130832
http_request_duration_seconds_count{code="200",method="post"} 1

http_request_duration_seconds_bucket{code="400",method="get",le="1"} 1
http_request_duration_seconds_sum{code="400",method="get"} 5.4304e-05
http_request_duration_seconds_count{code="400",method="get"} 1
# HELP http_requests_total total HTTP requests processed
# TYPE http_requests_total counter
http_requests_total{code="200",method="post"} 1
http_requests_total{code="400",method="get"} 1
```

你将看到 http_request_duration_seconds_bucket/sum/count 中的直方图值，以及 http_requests_total 中每个状态的计数。

### 向 Prometheus 数据添加自定义指标

此时，添加自己的额外自定义指标相对简单。

- 1) 定义指标并为其命名，确保它保持在处理程序的作用域内
- 2) 在指标上调用 `prometheus.MustRegister`
- 3) 在处理程序内调用指标的方法以递增/递减或记录自定义数据

编辑之前的示例（custom-metrics）。为简洁起见，我移除了 RED 指标，但你可以将两者结合。

```
package main

import (
    "crypto/sha256"
    "encoding/hex"
    "fmt"
    "io"
    "log"
    "net/http"
    "time"

    "github.com/prometheus/client_golang/prometheus"
    "github.com/prometheus/client_golang/prometheus/promhttp"
)

// computeSum generates a SHA256 hash of the body
func computeSum(body []byte) []byte {
    h := sha256.New()
    h.Write(body)
    hashed := hex.EncodeToString(h.Sum(nil))
    time.Sleep(time.Second * 5)
    return []byte(hashed)
}
```

注意添加的 5 秒休眠以显示并发请求。除非我们增加一些延迟，否则可能很难看到 gauge 上升。

```
func main() {
    port := 8080
    readTimeout := time.Second * 10
    writeTimeout := time.Second * 10

    mux := http.NewServeMux()

    hashesInflight := prometheus.NewGauge(prometheus.GaugeOpts{
        Subsystem: "http",
        Name:      "hashes_inflight",
        Help:      "total hashes inflight",
    })
    prometheus.MustRegister(hashesInflight)
}
```

像 Gauge 这样的指标需要在将要使用的 HTTP 处理程序的作用域内定义。而且 `prometheus.MustRegister` 也是必需的。

然后只需在开始时调用 `metric.Inc()`，完成时调用 `metric.Dec()`。

```
customHash := func(w http.ResponseWriter, r *http.Request) {
    if r.Method != http.MethodPost {
        w.WriteHeader(http.StatusBadRequest)
        return
    }
    if r.Body != nil {
        defer r.Body.Close()

        hashesInflight.Inc()
        defer hashesInflight.Dec()

        body, _ := io.ReadAll(r.Body)
        fmt.Fprintf(w, "%s", computeSum(body))
    }
}
```

其余代码与之前相同：

```
mux.HandleFunc("/hash", customHash)
mux.Handle("/metrics", promhttp.Handler())

s := &http.Server{
    Addr:           fmt.Sprintf(":%d", port),
    ReadTimeout:    readTimeout,
    WriteTimeout:   writeTimeout,
    MaxHeaderBytes: 1 << 20, // Max header of 1MB
    Handler:        mux,
}
log.Printf("Listening on: %d", port)
s.ListenAndServe()
}
```

运行示例：

```
# Terminal 1:
$ go run main.go

# Terminal 2:

# Run this 3-5 times quickly hitting up in between each
$ curl localhost:8080/hash -d test &

# Then quickly run:

$ curl -s localhost:8080/metrics | grep inflight
# HELP promhttp_metric_handler_requests_in_flight Current number of scrapes being served.
# TYPE promhttp_metric_handler_requests_in_flight gauge
promhttp_metric_handler_requests_in_flight 5
```

现在你已经学会了如何添加自定义指标和用于跟踪函数的标准 HTTP RED 指标。

### Prometheus Collector 接口

Collector 接口在 Prometheus 中很重要，当你想要扩展从应用程序导出的指标或标签时。我倾向于认为它更适用于数据来自第三方 API 或远程端点（如数据库或 Kubernetes API 服务器）的情况。

我倾向于将收集器实现为新类型。此代码改编自 OpenFaaS 网关，该网关在每个安装的生产环境中使用。

```
type Exporter struct {
}

func NewExporter() *Exporter {
    return &Exporter{
    }
}

// Describe is to describe the metrics for Prometheus
func (e *Exporter) Describe(ch chan<- *prometheus.Desc) {

}

// Collect exports the values for each metric to Prometheus
func (e *Exporter) Collect(ch chan<- prometheus.Metric) {

}
```

两个重要的方法是“Describe”——让 Prometheus 知道正在导出哪些指标，以及“Collect”——实际数据在此导出。这些函数由 Prometheus 异步调用，你无需自己调用它们。

你只需要注册 Exporter 的实例。

```
e := NewExporter()
prometheus.MustRegister(e)
```

此时，每次 Prometheus 服务器抓取时，Prometheus Go SDK 都会先调用 Describe 然后调用 Collect。

那么用代码填充这些方法看起来是什么样子的？

我将删减示例，使其仅显示一个字段，即 Kubernetes 中每个 OpenFaaS 函数存在多少个副本。function_name 的各种标签值将在每次 Collect 代码运行时重置，然后动态填充。

我们还将编写一个假 API，返回 OpenFaaS 集群中每个函数的副本数。我们将从无数据开始，然后添加一些数据，看到它出现在指标中，然后将其删除并看到它被删除且不再被跟踪或导出，展示 Collector 接口对动态数据的有用性。

api.go:

```
package main

func newAPIQuery() *APIQuery {
    return &APIQuery{
        Response: make(map[string]int64),
    }
}

type APIQuery struct {
```

```go
type APIQuery struct {
	Response map[string]int64
}

func (a *APIQuery) Register(name string, replicas int64) {
	a.Response[name] = replicas
}

func (a *APIQuery) Remove(name string) {
	delete(a.Response, name)
}

func (a *APIQuery) QueryFunctions() map[string]int64 {
	return a.Response
}
```

API 有一个 map，我们将通过 HTTP 请求修改它，请求 /register 和 /remove 端点，传入函数名称和/或副本数量的查询字符串。通常，如果这是生产代码，我们还希望使用锁定机制，以确保对 map 的安全并发访问。

#### exporter.go

```go
package main

import (
	"github.com/prometheus/client_golang/prometheus"
)

type Exporter struct {
	ServiceReplicasGauge *prometheus.GaugeVec
	api                  *APIQuery
}

func NewExporter(api *APIQuery) *Exporter {
	return &Exporter{
		api: api,
		ServiceReplicasGauge: prometheus.NewGaugeVec(
			prometheus.GaugeOpts{
				Namespace: "gateway",
				Name:      "service_count",
				Help:      "Current count of replicas for function",
			},
			[]string{"function_name"},
		),
	}
}

// Describe is to describe the metrics for Prometheus
func (e *Exporter) Describe(ch chan<- *prometheus.Desc) {
	e.ServiceReplicasGauge.Describe(ch)
}

// Collect exports the values for each metric to Prometheus
func (e *Exporter) Collect(ch chan<- prometheus.Metric) {
	e.ServiceReplicasGauge.Reset()

	for serviceName, replicas := range e.api.QueryFunctions() {
		e.ServiceReplicasGauge.
			WithLabelValues(serviceName).
			Set(float64(replicas))
	}

	e.ServiceReplicasGauge.Collect(ch)
}
```

在 Describe 方法中，我们已向 Prometheus 说明了它需要保存数据的所有各种指标。

After running `go mod init prometheus-collector`:

#### main.go

```go
package main

import (
	"fmt"
	"log"
	"net/http"
	"strconv"
	"time"

	"github.com/prometheus/client_golang/prometheus"
	"github.com/prometheus/client_golang/prometheus/promhttp"
)

func main() {
	port := 8080
	readTimeout := time.Millisecond * 500
	writeTimeout := time.Millisecond * 500

	mux := http.NewServeMux()
	api := newAPIQuery()

	e := NewExporter(api)
	prometheus.MustRegister(e)

	mux.Handle("/metrics", promhttp.Handler())
	mux.Handle("/remove", http.HandlerFunc(
		func(w http.ResponseWriter, r *http.Request) {
			name := r.URL.Query().Get("name")
			api.Remove(name)
		}))

	mux.Handle("/register", http.HandlerFunc(
		func(w http.ResponseWriter, r *http.Request) {
			name := r.URL.Query().Get("name")
			replicasV := r.URL.Query().Get("replicas")
			replicas, _ := strconv.ParseInt(replicasV, 10, 64)
			api.Register(name, int64(replicas))
			w.WriteHeader(http.StatusAccepted)
		}))

	s := &http.Server{
		Addr:           fmt.Sprintf(":%d", port),
		ReadTimeout:    readTimeout,
		WriteTimeout:   writeTimeout,
		MaxHeaderBytes: 1 << 20, // Max header of 1MB
		Handler:        mux,
	}
	log.Printf("Listening on: %d", port)
	s.ListenAndServe()
}
```

在 Collect 方法中，我们重置指标，然后添加 API 响应中存在的所有项目。如果删除了某个项目，则它将不再作为服务指标的一部分导出。

运行示例，你将看不到任何指标，因为我们没有任何内容可导出：

```sh
go run . &
```

```sh
curl -s http://127.0.0.1:8080/metrics | grep gateway
```

现在使用 API /register 端点添加三个函数及其副本数：

```sh
curl -s "http://127.0.0.1:8080/register?name=email&replicas=1"
curl -s "http://127.0.0.1:8080/register?name=payment&replicas=3"
curl -s "http://127.0.0.1:8080/register?name=scrape&replicas=0"
```

再次尝试该端点：

```sh
curl -s http://127.0.0.1:8080/metrics | grep gateway
```

```
# HELP gateway_service_count Current count of replicas for function
# TYPE gateway_service_count gauge
gateway_service_count{function_name="email"} 1
gateway_service_count{function_name="payment"} 3
gateway_service_count{function_name="scrape"} 0
```

现在删除 email 函数的副本，并查看它也永久从服务 /metrics 端点被抓取时返回的值集合中移除。

```sh
curl -s "http://127.0.0.1:8080/remove?name=email"
```

```sh
curl -s http://127.0.0.1:8080/metrics | grep gateway
```

```
# HELP gateway_service_count Current count of replicas for function
# TYPE gateway_service_count gauge
gateway_service_count{function_name="payment"} 3
gateway_service_count{function_name="scrape"} 0
```

我建议在你拥有动态数据集或从第三方系统获取数据时使用 Collector 接口，在本例中是从 Kubernetes API 获取。

你可以在 samples/prometheus-collector 文件夹中找到完整的代码示例。

## 第 15 章

### 构建和发布 Go 二进制文件

无论你编写的是 CLI 还是 HTTP 服务器，大多数情况下 Go 代码都可以编译成静态二进制文件，该文件是自包含的，可以在你指定的目标系统上运行。

在之前的章节中我们介绍了交叉编译，此时你应该考虑是否需要针对单一环境，例如 Windows、Linux 或 MacOS，或多个环境。

### Release-it 示例

[Release-it](https://github.com/release-it/release-it) 仓库是一个可通过 GitHub Actions 构建和发布的静态 Go 二进制文件的示例。它使用一个 [Makefile](https://github.com/release-it/release-it/blob/main/Makefile)，因此也可以在其他 CI 管道中运行，或在你创建新版本时手动运行。

Makefile 具有以下属性，所有这些在之前的章节中都已介绍过：

- 它为多个平台和操作系统构建二进制文件
- 它将 Commit 和 Version 从 git 注入到最终二进制文件中

```makefile
Version := $(shell git describe --tags --dirty)
# Version := "dev"
GitCommit := $(shell git rev-parse HEAD)
LDFLAGS := "-s -w -X main.Version=$(Version) -X main.GitCommit=$(GitCommit)"

.PHONY: all
all: gofmt dist

.PHONY: gofmt
gofmt:
	@test -z $(shell gofmt -l ./ | tee /dev/stderr) || (echo "[WARN] Fix formatting issues with 'make fmt'" && exit 1)

.PHONY: dist
dist:
	mkdir -p bin/
	CGO_ENABLED=0 GOOS=linux go build -mod=vendor -a -ldflags $(LDFLAGS) -o bin/release-it-amd64
	CGO_ENABLED=0 GOOS=darwin go build -mod=vendor -a -ldflags $(LDFLAGS) -o bin/release-it-darwin
	GOARM=7 GOARCH=arm CGO_ENABLED=0 GOOS=linux go build -mod=vendor -a -ldflags $(LDFLAGS) -o bin/release-it-arm
	GOARCH=arm64 CGO_ENABLED=0 GOOS=linux go build -mod=vendor -a -ldflags $(LDFLAGS) -o bin/release-it-arm64
	GOOS=windows CGO_ENABLED=0 go build -mod=vendor -a -ldflags $(LDFLAGS) -o bin/release-it.exe
```

此外，它还会运行 gofmt 以确保质量。

如果项目中有任何单元测试，我们可以为其添加额外的目标，例如：

```makefile
.PHONY: gotest
gotest:
	go test ./...
```

然后将 all 行更新为 `gofmt gotest dist`，这样就会为我们运行每个任务。

克隆示例并构建它：

```sh
$ mkdir $GOPATH/src/github.com/alexellis/
$ cd $GOPATH/src/github.com/alexellis/
$ git clone https://github.com/alexellis/release-it
$ cd release-it
$ make
```

默认情况下 make 会尝试运行 all 目标，但你也可以运行 make gofmt，如果你想在提交构建之前测试格式。

你会在 bin/ 文件夹中找到每个二进制文件，如果它与你的系统匹配的 OS/architecture 对，可以在你的系统上运行，或复制到另一系统上运行。

![](img/0b5c3b498f62579835cf1d543b46de92_121_0.png)

Figure 15.1: GitHub 的发布页面

当你向用户发布二进制文件时，GitHub 的发布功能会很有用，因为它允许你手动或通过自动化上传二进制文件。

### 使用 GitHub Action 发布你的二进制文件

GitHub Actions 对于开源仓库（即公开仓库）免费使用，并且也为私有仓库提供一定数量的免费分钟数。此示例应可适应 Jenkins 或 GitLab CI 等其他平台，因为概念在很大程度上是相同的。




在我们的示例中，我们首先会从GitHub上针对发布标签检出代码，然后运行`make all`，接着将发布产物上传到GitHub Release。

```
name: publish
on:
  push:
    tags:
      - '*'
jobs:
  publish:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@master
        with:
          fetch-depth: 1
      - name: Make all
        run: make all
      - name: Upload release binaries
        uses: alexellis/upload-assets@0.4.1
        env:
          GITHUB_TOKEN: ${{ github.token }}
        with:
          asset_paths: '["./bin/release-it*"]'
```

工作流文件中的每个步骤都可以使用特定的GitHub Action，例如`alexellis/upload-assets@0.4.1`或`actions/checkout@master`；而当该字段留空时，则会使用基础系统，比如`ubuntu-latest`。在Ubuntu基础运行环境中，你可以执行标准的Shell和构建命令，例如`make all`。

`alexellis/upload-assets` Action是我创建并用于我所维护的各种开源项目的，它支持上传多个文件。

用户随后就可以下载你的二进制文件，并在自己的系统上运行它。

例如：

```
$ cd /tmp/
$ curl -sLSf \
  -o ./release-it \
  https://github.com/alexellis/release-it/releases/download/0.2.11/release-it-darwin \
  && chmod +x ./release-it \
  && ./release-it

release-it: 0.2.11, commit: 4379cbf694c55bd98f5080d76ac5972fd89dcc65
```

## 第16章

### 发布Docker容器镜像

我会交替使用“Docker镜像”和“容器镜像”这两个术语，因为许多人只通过Docker了解容器。

首先，你需要一个Dockerfile，它的作用类似于之前的Makefile：构建一个可以分发给用户的二进制文件。

这个Dockerfile将是多阶段（multi-stage）的，同时也支持多架构（multi-architecture）。

- 多阶段——构建代码所需的SDK不会包含在最终镜像中
- 多架构——构建产物可以在不止一个目标平台上运行

当你的目标平台是Arm服务器而开发机是Intel或AMD时，多架构构建非常重要；反过来，如果你是Apple M1用户，也同样重要。

我们继续使用上一节中的`release-it`仓库。

```
FROM --platform=${BUILDPLATFORM:-linux/amd64} golang:1.22 as builder

ARG TARGETPLATFORM
ARG BUILDPLATFORM
ARG TARGETOS
ARG TARGETARCH

ARG Version
ARG GitCommit

ENV CGO_ENABLED=0
ENV GO111MODULE=on

WORKDIR /go/src/github.com/alexellis/release-it

COPY . .

RUN CGO_ENABLED=${CGO_ENABLED} GOOS=${TARGETOS} GOARCH=${TARGETARCH} \
    go test -v ./...

RUN CGO_ENABLED=${CGO_ENABLED} GOOS=${TARGETOS} GOARCH=${TARGETARCH} \
    go build -ldflags \
    "-s -w -X 'main.Version=${Version}' -X 'main.GitCommit=${GitCommit}'" \
    -o /usr/bin/release-it .

FROM --platform=${BUILDPLATFORM:-linux/amd64} gcr.io/distroless/static:nonroot
WORKDIR /
COPY --from=builder /usr/bin/release-it /
```

恭喜，你现在已经构建了一个静态Golang二进制文件，将其发布到了GitHub Release页面，同时交付了你的第一个多架构Docker镜像，它可以在两种不同的目标平台上运行。

### 从GitHub Actions发布Docker容器

现在，如果你想为自己的GitHub仓库发布容器镜像，最后一步就是为它定义一个GitHub Action。

创建以下文件`.github/workflows/publish.yaml`并提交。每当你创建标签时，它都会执行一次发布构建，因此你在UI或API中为仓库创建的每个GitHub Release都会触发构建。

```yaml
name: publish

on:
  push:
    tags:
      - '*'

permissions:
  actions: read
  checks: write
  contents: read
  packages: write

jobs:
  publish:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@master
        with:
          fetch-depth: 1

      - name: Get TAG
        id: get_tag
        run: echo TAG=latest-dev >> $GITHUB_ENV
      - name: Get Repo Owner
        id: get_repo_owner
        run: echo "REPO_OWNER=$(echo ${{ github.repository_owner }} | tr '[:upper:]' '[:lower:]')" > $GITHUB_ENV

      - name: Set up QEMU
        uses: docker/setup-qemu-action@v3
      - name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v3

      - name: Login to Container Registry
        uses: docker/login-action@v3
        with:
          username: ${{ github.repository_owner }}
          password: ${{ secrets.GITHUB_TOKEN }}
          registry: ghcr.io

      - name: Release build
        id: release_build
        uses: docker/build-push-action@v5
        with:
          outputs: "type=registry,push=true"
          platforms: linux/amd64,linux/arm/v6,linux/arm64
          build-args: |
            Version=${{ env.TAG }}
            GitCommit=${{ github.sha }}
          tags: |
            ghcr.io/${{ env.REPO_OWNER }}/release-it:${{ github.sha }}
            ghcr.io/${{ env.REPO_OWNER }}/release-it:${{ env.TAG }}
            ghcr.io/${{ env.REPO_OWNER }}/release-it:latest
```

你可以看到，`build-args`的填充方式与我们在本地运行`docker build`或`buildx`时相同，然后我们还添加了一些用于设置QEMU的额外Action。QEMU被`buildx`用来交叉编译你的代码，使其能在其他机器上运行。

平台列表（`linux/amd64, linux/arm/v6, linux/arm64`）意味着该容器可以在Raspberry Pi OS、64位Arm服务器以及常规Intel/AMD服务器上运行。

如果你使用`ghcr.io`，事情会简单得多：GitHub Actions会提供一个临时令牌，用于发布镜像。只需确保你记得包含上面提到的`permissions`和`packages: write`部分，以便令牌具有适当的权限。对于Docker Hub或私有registry，你需要创建一对单独的密钥，例如`DOCKER_USERNAME`和`DOCKER_PASSWORD`，然后更新`docker/login-action@v2`步骤来使用它们。

请注意，使用GHCR时，你的容器镜像默认可能被设置为私有。你需要将其设为公开才能共享，否则需要对你的Docker引擎或Kubernetes集群进行身份验证。

## 第17章

### 你接下来的旅程

我希望你喜欢我分享的这些配方和示例，它们来自我自己过去5-6年使用Go和开源社区的旅程。当然，我一直在学习，书中部分示例曾经是博客文章，但现在已经过时了。

### 提供反馈

如果你有反馈，或者发现了错误，请随时联系我，这样我们可以一起改进这本电子书，让它惠及更多人。邮箱：[contact@openfaas.com](mailto:contact@openfaas.com)。

同样，如果你的团队或公司正在工作中使用Go，并希望获得建议或与熟悉Go和分布式系统的人交流，也请随时联系。

### 为开源做贡献

我们也在为社区维护的各种开源项目寻找贡献者。这是一个很好的方式，可以让你大展身手，并将所学付诸实践。

- [OpenFaaS](https://www.openfaas.com/)——可移植的开源无服务器函数平台
- [arkade](https://github.com/alexellis/arkade)——直接从GitHub Releases安装CLI和Kubernetes应用的市场
- [k3sup](https://github.com/alexellis/k3sup)——使用K3s在个人电脑和云上启动Kubernetes集群
- [derek](https://github.com/alexellis/derek)——一个GitHub机器人，可自动完成开源项目中的维护者任务，并通过issue/PR评论向贡献者授予权限
- [inlets-operator](https://github.com/inlets/inlets-operator)——一个Kubernetes Operator，可为私有Kubernetes集群中的任意LoadBalancer服务提供公网IP

### 我的其他内容

OpenFaaS本身是用Go编写的，它是一个可运行在Kubernetes、单台VM或Raspberry Pi上的无服务器平台。电子书和视频工作坊[Serverless For Everyone Else](https://openfaas.com)已经售出450份，是开始学习函数的好去处。

我还有一个关于使用Kubernetes（k3s）构建Raspberry Pi集群的工作坊，内容涵盖如何从网络存储启动Raspberry Pi。网络存储比SD卡更快、更高效。电子书和视频工作坊可以在Gumroad上单独购买或作为套装购买：[Netbooting workshop for Raspberry Pi with K3s](https://gumroad.com/l/netbooting)。

如果你[在Twitter上关注我 @alexellisuk](https://twitter.com/alexellisuk)，就能看到我发布新视频、活动和博客文章的消息，这些内容可能会发布在多个平台上。

最后，感谢你购买这本电子书。无论你身处Golang旅程的哪个阶段，希望你都乐在其中。





## 第18章

### OpenFaaS与Go

![](img/0b5c3b498f62579835cf1d543b46de92_128_0.png)

图18.1：OpenFaaS标志

OpenFaaS 是一个开源、可移植且与云厂商无关的无服务器平台。

欢迎阅读你的专属附加内容，仅面向高级版读者。

### 本章涵盖的主题

- 无服务器的用例
- OpenFaaS 简介
- 适用于 OpenFaaS 的 Go 模板
- 构建并测试你的第一个函数
- 对函数进行单元测试
- 在本地迭代
- 拆分为多个文件和子包
- 使用机密和数据库
- 在多个环境之间管理配置
- 自定义域名和路由
- 下一步该去哪里

### 无服务器的用例

说到“无服务器”，我发现潜在用户要么“一下就懂了”，要么完全没抓住要点。当你读到本书这一节时，我不确定你属于哪一类。

我经常听到那些每天编写 HTTP 微服务、或者为客户构建平台间集成的开发者说：“我们还没准备好用无服务器”或者“我没有这种用例”。

比较难解释的一点是：函数就是微服务，只是更加专门化。

函数往往具备以下特点：

- 比微服务更小
- 更聚焦于单一用例或职责
- 自动扩缩容并自动监控
- 通过模板构建，无需处理 HTTP 服务器

但它们覆盖的用例与微服务相同。它们可以读写数据库，可以为客户提供网页服务并拥有自定义域名，还可以用来运行批处理作业和处理数据。几乎没有什么事是函数做不到的。

当我们说“函数”时，实际上是在说：“这是一种带有额外管理能力的微服务”，而通过统一的方式管理所有服务，可以减少重复劳动，让你更快地交付代码。

所以，如果你以编写、维护或监控后端服务为生，那么你在日常工作中很可能用得上函数。

另见：Serverless 2.0: Get started with the PLONK Stack • Alex Ellis • GOTO 2019

我在博客文章《探索来自企业和社区的无服务器用例》中，介绍了来自社区和商业用户的具体用例。

### OpenFaaS 简介

我对 Go 最早的记忆，是在 2015 年学习和撰写关于 Docker 的文章时。可复现构建的概念解决了当时我所在公司的一个重大痛点，但这项技术与当时使用的技术相比简直是天壤之别，于是我踏上了向他人讲解它的旅程。2016 年，Docker 发布了“Swarm”产品，它允许多台运行容器的计算机作为分布式系统的一部分协同工作。大概也就是在那时，我听说了 FaaS 和无服务器这两个术语，而我当时完全不知道它们之间的区别。

直到我开始尝试使用 AWS Lambda 来编写、调试和发布 Alexa 技能时，我才意识到容器能为函数带来什么。

当时，无法直接在 AWS Lambda 中运行 Go 代码，常见的技巧是向 Node.js 运行时添加一个二进制文件，并让它在每次请求时被执行。然后是管道的问题。在一家大型企业工作时，我无法理解为什么将源代码控制连接到 AWS Lambda 并使其直接部署变更如此困难。相反，当时通行的方法是使用 ZIP 文件和在本机编译的二进制文件。

正是在那时，我开始了 OpenFaaS 的创建，当时（2016 年底）它还叫“faas”，第一个版本在次年五月的 Dockercon 主舞台上进行了演示。其中一个演示涉及对 alexellis/faas GitHub 仓库上的 Star 事件进行响应。每收到一个 Star，就会生成一张虚拟拍立得照片，上传到 S3 存储桶，并展示在大屏幕上。

那时候，如果你问 10 个人“无服务器”是什么意思，他们可能会根据自己所在的公司、接触函数的程度以及开始接触的时间给出不同的答案。我从 2016 年开始接触，当时“无服务器”在很大程度上等同于“函数即服务”（FaaS）。各个工作组曾试图定义这个术语或制定规范，但这些努力最终只形成了薄弱的标准和大量的困惑。我曾参与 CNCF 的无服务器工作组，该小组撰写了 CNCF 白皮书。

当我与 OpenFaaS 用户交流时，他们往往不太关心按量计费有多细、是否需要服务器管理，而更看重一个与云厂商无关的运行时，用于运行代码和处理事件。

### 与云函数的价值对比

那么，OpenFaaS 相对于云函数的价值在哪里？

- 避免被特定云厂商锁定。这意味着如果你有一个产品，你可以将其运行在公有云上为客户提供服务，也可以运行在客户自己的本地私有云中。
- 自己设定限制。与其被告知一个函数允许的最大内存、最大大小、并发请求数或超时时间，你可以自己设置这些参数。如果你遇到了一个限制，并且它影响到了重要客户，你会怎么做？
- 对解决方案进行白标。一些公司将 OpenFaaS 集成为其平台中一个运行函数的“黑盒”。这让他们的平台能够为用户运行代码并扩展平台自身。ADOPTERS 文件中的例子包括 Waylay（一个低代码平台）和 LivePerson（一个面向客户的聊天平台）。
- 扩展和调整。如果你需要对接某个消息队列或数据库，你可以编写代码来实现。如果你需要自定义函数的创建或运行方式，你可以分叉代码并对其进行修改以满足需求。

### 优点与缺点

与此同时，我们也应该谈谈 OpenFaaS 相对于云函数的缺点。

每个云厂商（如 Azure、Google Cloud 等）往往会让其云函数平台与其托管服务进行非常紧密的集成。如果你需要与 AWS 托管服务进行非常紧密的集成，那么 AWS Lambda 可能更适合你的需求。

OpenFaaS 相对容易运行，而且自从我们创建了 faasd 之后，部署几个函数不再需要你了解 Kubernetes。然而，如果你还没有使用 Kubernetes，在某些情况下使用云函数可能更简单。

如果你正在为客户搭建一个你不想负责维护的函数，那么托管云函数所带来的支持服务可能会让你更放心。话虽如此，如果你是顾问，你可以为一个集群运行 OpenFaaS，服务所有客户。

一些在 AWS 上使用 Kubernetes 的终端用户公司告诉我们，他们更倾向于用一种方式来部署和管理所有代码，这意味着使用 OpenFaaS 而不是托管的 Lambda 平台。归根结底，你需要评估自己的需求，决定你是想要灵活性和自主性，由自己来支持和运行函数，还是想要一个托管平台，让云厂商承担部分职责。

### 你能在哪里运行 OpenFaaS 函数？

你构建的任何 OpenFaaS 函数都会被打包成一个容器镜像。然后你可以将其部署到至少三个不同的平台上，只要它们支持 HTTP 微服务，甚至可能更多。

- OpenFaaS——无论你在哪里听到“OpenFaaS”这个词，它很可能指的是运行在 Kubernetes 上的 OpenFaaS。你可以从云厂商那里获得托管的 Kubernetes，这意味着控制平面无需你操心。然后你只需要管理节点，但这些节点也可以自动扩缩容。竞价实例可以大幅降低云主机的成本。
- faasd——faasd 与 Kubernetes 上使用的 OpenFaaS 相同，但专门针对低开销和低资源需求进行了优化。它运行在单一主机上。
- Google Cloud Run——你为 OpenFaaS 构建的大多数函数都可以在 Google 的 Cloud Run 上运行。你将按使用量付费，除了镜像本身之外，你无需管理任何东西。这不是完整的 OpenFaaS 体验，但对某些用户来说可能很有用。

在开始本节中的任何示例之前，你需要先搭建好 OpenFaaS。

在你想构建函数的任何电脑上安装 Docker 和 faas-cli。

### 适用于 OpenFaaS 的 Go 模板

OpenFaaS 提供了三个 Go 模板，供你用来构建函数：

- `go` —— 一个使用 cgi/bin 方法的旧式模板
- `golang-http` —— 一个 Go 模板，为你提供用户友好的 HTTP 请求/响应结构体
- `golang-middleware` —— 我最喜欢的模板，为你提供 Go 标准库中的中间件




OpenFaaS 模板存储在多个 Git 仓库中。pull 命令会将特定仓库中的所有模板获取到你的模板文件夹。

```bash
faas-cli template pull \
    https://github.com/openfaas/golang-http-template
```

模板存储包含官方和社区模板的列表，可以代替输入完整 URL 使用：

```bash
faas-cli template store pull golang-http
```

查看结果：

```text
Fetch templates from repository: https://github.com/openfaas/golang-http-template at
2021/07/23 16:01:59 Attempting to expand templates from
↪  https://github.com/openfaas/golang-http-template
2021/07/23 16:02:01 Fetched 2 template(s) : [golang-http golang-middleware] from
↪  https://github.com/openfaas/golang-http-template

$ ls ./template/
golang-http      golang-middleware
```

golang-http 模板提供请求和响应风格，与托管云函数采用的方法最为相似。

查看 `template/golang-http/function/handler.go` 的内容：

```go
package function

import (
    "fmt"
    "net/http"

    handler "github.com/openfaas/templates-sdk/go-http"
)

// Handle a function invocation
func Handle(req handler.Request) (handler.Response, error) {
    var err error

    message := fmt.Sprintf("Body: %s", string(req.Body))

    return handler.Response{
        Body:       []byte(message),
        StatusCode: http.StatusOK,
    }, err
}
```

- HTTP 请求体可在 `req.Body` 变量中使用。
- HTTP 头可在 `req.Headers` 中使用。
- HTTP 查询字符串、路径和方法也可在 `req.QueryString`、`req.Path` 和 `req.Method` 中使用。

golang-middleware 模板则提供标准的 HTTP 请求处理器：

`template/golang-middleware/function/handler.go` 的内容：

```go
package function

import (
    "fmt"
    "io"
    "net/http"
)

func Handle(w http.ResponseWriter, r *http.Request) {
    var input []byte

    if r.Body != nil {
        defer r.Body.Close()

        body, _ := io.ReadAll(r.Body)

        input = body
    }

    w.WriteHeader(http.StatusOK)
    w.Write([]byte(fmt.Sprintf("Body: %s", string(input))))
}
```

OpenFaaS 和 Cloud Run 都需要容器，因此通常需要 Dockerfile。通过使用模板，Dockerfile 以及所有常见的样板代码（如如何设置 HTTP 服务器并在 TCP 端口上开始监听）都被抽象掉了。这些事情仍然会发生，但已从你的工作流程中隐藏起来，无需在每个函数中重复。

### 你的第一个函数

让我们创建一个函数，对你发送给它的任何输入计算 bcrypt 哈希。Bcrypt 通常用于对数据库中存储的密码进行哈希处理。

另请参阅：https://pkg.go.dev/golang.org/x/crypto/bcrypt

决定要将函数的容器镜像上传到何处，并设置以下环境变量：

```
export OPENFAAS_PREFIX="ghcr.io/alexellis"
export OPENFAAS_PREFIX="docker.io/alexellis2"
export OPENFAAS_PREFIX="private.gcr.io/my-company"
```

Docker Hub 和 GitHub Container Registry 提供了良好的起点。你也可以使用自己的私有仓库，前提是为此配置了 OpenFaaS。

确保你已登录 Docker：

```
docker login
```

如果在上一步中尚未设置，现在设置你的环境变量。

```
export OPENFAAS_PREFIX="docker.io/alexellis2"
```

为函数创建一个文件夹：

```
export GH_USERNAME="alexellis"
mkdir -p $GOPATH/src/github.com/$GH_USERNAME/bcrypt-fn/
cd $GOPATH/src/github.com/$GH_USERNAME/bcrypt-fn/
```

现在使用 golang-middleware 模板为新函数搭建脚手架：

```
faas-cli template store pull golang-middleware

faas-cli new --lang golang-middleware \
  bcrypt-fn
```

查看生成的 bcrypt-fn.yml 文件的内容：

```
version: 1.0
provider:
  name: openfaas
  gateway: http://127.0.0.1:8080
functions:
  bcrypt-fn:
    lang: golang-middleware
    handler: ./bcrypt-fn
    image: docker.io/alexellis2/bcrypt-fn:latest
```

你可以将 latest 标签更改为特定版本，例如 0.1.0，然后在每次构建函数前递增此版本号。

更新 bcrypt-fn/handler.go 文件，使其对你发送的任何输入计算 bcrypt 哈希：

```
package function

import (
  "fmt"
  "io"
  "net/http"

  "golang.org/x/crypto/bcrypt"
)

func Handle(w http.ResponseWriter, r *http.Request) {
  var input []byte

  if r.Body != nil {
    defer r.Body.Close()
    body, _ := io.ReadAll(r.Body)
    input = body
  }

  res, err := bcrypt.GenerateFromPassword(input, bcrypt.DefaultCost)
  if err != nil {
    http.Error(w, fmt.Sprintf("Error: %s", err), http.StatusInternalServerError)
    return
  }

  w.WriteHeader(http.StatusOK)
  w.Write(res)
}
```

运行以下步骤来设置导入的模块：

```
cd bcrypt-fn
go mod init
go mod tidy
```

然后 `cd ..` 返回到项目的顶层目录，在那里有 `bcrypt-fn.yml` 文件。

你必须始终在 `handler.go` 文件旁边运行 `go mod` 命令，而不是在 YAML 文件的层级运行。

### 构建你的函数

构建和部署函数的流程如下：

- `faas-cli build` 在本地 Docker 库中创建容器镜像
- `faas-cli push` 将镜像推送到远程容器仓库
- `faas-cli deploy` 使用 REST API 调用将函数部署到你的 OpenFaaS 网关

上述三个命令可通过 `faas-cli up` 命令运行。

所有这些命令都可以在 CI/CD 流水线中运行。

将你的 OpenFaaS 网关 URL 设置为环境变量并运行 `faas-cli up` 来试用该函数。

```sh
export OPENFAAS_URL=http://127.0.0.1:8080

export DOCKER_BUILDKIT=1

faas-cli build --build-arg GO111MODULE=on -f bcrypt-fn.yml
```

`export DOCKER_BUILDKIT=1` 步骤将指示 Docker 使用 buildkit 而不是其传统的构建函数方法。Buildkit 可以工作得更快，因为它可以以更智能的方式缓存层，并且还可以并行运行多个步骤。最终，这意味着你的构建会更快。

接下来会发生的是函数的 Dockerfile 将被执行。它在模板中隐藏在：`template/golang-middleware/Dockerfile`。如果你愿意，现在可以阅读它。

在另一个窗口中，调用容器：

```sh
curl --data-binary "functions" \
  http://127.0.0.1:8080/function/bcrypt-fn

$2a$10$ziCqH4XsqdfO5SQ4QqCenuF9qi1hhW50N7f4914fqZjacU5PzJsqq
```

每次运行函数时，你都会得到相同的结果。你还会注意到持续时间相对较慢，因为该算法设计为 CPU 密集型。

使用以下命令计时调用：

```sh
time curl --data-binary "functions" \
  http://127.0.0.1:8080/function/bcrypt-fn

$2a$10$MypsuxBUfgTQa4IcW/XW3u.1uV/uWp4ktp/q3T10TFg4Exqjz9pge
real    0m0.108s
user    0m0.012s
sys     0m0.012s
```

你也可以检查 HTTP 头中的 `X-Duration-Seconds:` 头，它是函数运行所需的时间，而不是 curl 与容器之间的往返时间。

```sh
curl -i --data-binary "functions" \
  http://127.0.0.1:8080/function/bcrypt-fn

HTTP/1.1 200 OK
Content-Length: 60
Content-Type: text/plain; charset=utf-8
```

进入目录，运行 go build 然后调用处理器：

```
faas-cli build --shrinkwrap -f bcrypt-fn.yml
cd ./build/bcrypt-fn

# Remove the function's go.mod
rm ./build/bcrypt-fn/go.mod

# Create one at the top-level
go mod init
go mod tidy

go build

./handler
```

请注意，处理器不会打印任何输出，但你可以在 8082 端口上调用它：

```
curl http://localhost:8082

$2a$10$iho.B7JZNX8DDp610./eheEUxBuCOTEWGS47aIhuXchRSV0oYfYnW
```

这是一种高级技术，但可以在出现问题且需要在短时间内进行大量编辑时用于在本地测试函数。

### 将代码拆分为多个文件

大多数情况下，你的 handler.go 文件会相对较短，但如果你想为了可读性将其拆分为多个文件。

考虑 handler.go 已演进为返回包含哈希和计算成本的 JSON 结构体，而不是直接返回哈希。

```
package function

import (
    "encoding/json"
    "fmt"
    "io"
    "net/http"

    "golang.org/x/crypto/bcrypt"
)

type HashResponse struct {
    Hash string
    Cost int
}

func Handle(w http.ResponseWriter, r *http.Request) {
    var input []byte

    if r.Body != nil {
        defer r.Body.Close()
        body, _ := io.ReadAll(r.Body)
        input = body
    }
}
```

```
cost := bcrypt.DefaultCost
res, err := bcrypt.GenerateFromPassword(input, cost)
if err != nil {
    http.Error(w, fmt.Sprintf("Error: %s", err), http.StatusInternalServerError)
    return
}

h := HashResponse{
    Hash: string(res),
    Cost: cost,
}

hBytes, _ := json.Marshal(h)

w.WriteHeader(http.StatusOK)
w.Write(hBytes)
}
```

我们可以把这段代码拆分成 types.go 和 handler.go：

types.go：

```
package types

type HashResponse struct {
    Hash string
    Cost int
}
```

然后是 handler.go：

```
package function

import (
    "encoding/json"
    "fmt"
    "io"
    "net/http"
    "golang.org/x/crypto/bcrypt"
)

func Handle(w http.ResponseWriter, r *http.Request) {
    var input []byte

    if r.Body != nil {
        defer r.Body.Close()
        body, _ := io.ReadAll(r.Body)
        input = body
    }

    cost := bcrypt.DefaultCost
    res, err := bcrypt.GenerateFromPassword(input, cost)
    if err != nil {
        http.Error(w, fmt.Sprintf("Error: %s", err), http.StatusInternalServerError)
        return
    }

    h := HashResponse{
        Hash: string(res),
        Cost: cost,
    }
    hBytes, _ := json.Marshal(h)

    w.WriteHeader(http.StatusOK)
    w.Write(hBytes)
}
```

请注意，这两个文件都以 package function 开头，因此它们可以访问彼此的方法。如果你想为这个包添加任何单元测试，情况也是如此。

你可以在同一个包内添加文件，而无需添加子包。子包更适用于在函数之间共享代码，或进行逻辑上的关注点分离。

### 引入子包

以上一个示例为基础，创建一个名为 types 的新文件夹，然后创建 types/types.go：

```
package types

type HashResponse struct {
    Hash string
    Cost int
}
```

然后是 handler.go：

```
package function

import (
    "encoding/json"
    "fmt"
    "handler/function/types"
    "io"
    "net/http"

    "golang.org/x/crypto/bcrypt"
)

func Handle(w http.ResponseWriter, r *http.Request) {
    var input []byte

    if r.Body != nil {
        defer r.Body.Close()
        body, _ := io.ReadAll(r.Body)
        input = body
    }

    cost := bcrypt.DefaultCost
    res, err := bcrypt.GenerateFromPassword(input, cost)
    if err != nil {
        http.Error(w, fmt.Sprintf("Error: %s", err), http.StatusInternalServerError)
        return
    }

    h := types.HashResponse{
        Hash: string(res),
        Cost: cost,
    }
    hBytes, _ := json.Marshal(h)

    w.WriteHeader(http.StatusOK)
    w.Write(hBytes)
}
```

请注意，h := HashResponse{ 变为了 h := types.HashResponse{，以便访问新包。该包是以 handler/function/types 的形式导入的，这是模板的标准做法。

此时，faas-cli build 可以正常工作，但 go test 可能无法解析该函数，所以请进入 go.mod 目录并运行以下命令：

```
cd bcrypt-fn

# Should fail
go build

go mod edit -replace=handler/function=./
go get handler/function
cd ..

# Should resolve the error
go build
```

这会告诉本地系统在顶层目录中查找 handler/function。

### 使用密钥和数据库

在“使用数据库存储数据”一章中，我们介绍了如何连接数据库。请再次执行这些步骤，创建一个名为 todo 的数据库表，并采用指定的模式。

这里我们将重点讨论如何定义从函数访问数据库所需的密钥和配置，以及如何在请求之间保持连接。

这两个概念都可以通过函数的 YAML 文件进行配置。

-   对于机密数据，始终使用密钥。
-   对于非机密配置，你可以使用环境变量。

机密数据是指你希望保密、不愿与他人分享的任何信息，例如数据库主机、密码和用户名。

非机密配置则是类似“debug: true”或“output: json”的内容。

### 创建 todo-fn 示例

创建一个新函数：

```
export GH_USERNAME="alexellis"
mkdir -p $GOPATH/src/github.com/$GH_USERNAME/todo-fn/
cd $GOPATH/src/github.com/$GH_USERNAME/todo-fn/
```

现在使用 golang-middleware 模板搭建一个新函数：

```
faas-cli template store pull golang-middleware

faas-cli new --lang golang-middleware \
    todo-fn
```

我从 DigitalOcean 控制台获取的连接字符串是：postgresql://doadmin:ildkq2my7g7lqqxh@todo-pg11-do-user-2197152-0.b.db.ondigitalocean.com:25060/defaultdb?sslmode=require

使用 faas-cli secret create 命令将其拆分，以创建多个密钥。

```
faas-cli secret create db-user --from-literal $DBUSER
faas-cli secret create db-pass --from-literal $DBPASS
```

创建函数后，你可以将其添加到 YAML 文件的 secrets: 部分，这样它将在运行时被附加。

密钥将被挂载到 /var/openfaas/secrets/<NAME>。文本字符串和二进制文件均受支持。

然后编辑 todo-fn.yml，并添加以下 secrets 和 environment 部分。

```yaml
version: 1.0
provider:
  name: openfaas
  gateway: http://127.0.0.1:8080
functions:
  todo-fn:
    lang: golang-middleware
    handler: ./todo-fn
    image: docker.io/alexellis2/todo-fn:latest
    secrets:
    - db-user
    - db-pass
    environment:
      db_host: "todo-pg11-do-user-2197152-0.b.db.ondigitalocean.com"
      db_port: "25060"
      db_name: "defaultdb"
      db_ssl_mode: "require"
```

创建 todo-fn/types.go 并添加以下内容：

```
package function

import (
    "time"

    _ "github.com/lib/pq"
)

type Todo struct {
    ID            int       `json:"Id"`
    Description   string    `json:"description"`
    CreatedDate   time.Time `json:"created_date"`
    CompletedDate *time.Time `json:"completed_date,omitempty"`
}
```

我为每个字段添加了 json 注解，以便输出的 JSON 与数据库字段使用相似的名称。这一步是可选的。

创建 db.go。代码与上一章大体相同，我只是将输入改为了一个 Todo 结构体，而不是普通字符串。

```go
package function

import (
    "database/sql"
    "fmt"

    _ "github.com/lib/pq"
)

func connect(user, password, host, dbName, sslMode string, port int) (*sql.DB, error) {
    connStr := "postgres://" + user + ":" + password + "@" + host + ":" + fmt.Sprintf("%d",
        port) + "/" + dbName + "?sslmode=" + sslMode

    db, err := sql.Open("postgres", connStr)
    if err != nil {
        return nil, err
    }

    err = db.Ping()
    if err != nil {
        return nil, err
    }

    return db, nil
}

func create(db *sql.DB, todo Todo) error {
    if len(todo.Description) == 0 {
        return fmt.Errorf("description is required")
    }

    res, err := db.Query(`INSERT INTO
        todo
        (id, description, created_date)
        VALUES
        (DEFAULT, $1, now());`,
        todo.Description)

    if err != nil {
        return err
    }

    defer res.Close()
    return nil
}

func list(db *sql.DB) ([]Todo, error) {
    rows, err := db.Query(`SELECT
        id,
        description,
        created_date,
        completed_date
FROM todo;`)

    if err != nil {
        return []Todo{},
            fmt.Errorf("unable to get from todo table: %w", err)
    }

    todos := []Todo{}
    defer rows.Close()
    for rows.Next() {
        result := Todo{}
        err := rows.Scan(&result.ID,
            &result.Description,
            &result.CreatedDate,
            &result.CompletedDate)
        if err != nil {
            return []Todo{}, fmt.Errorf("row scan error: %w", err)
        }
        todos = append(todos, result)
    }
    return todos, nil
}
```

### 探索请求

现在我们需要编写一个 handler 来运行上述代码。在上一章中，我们使用一个 CLI 标志来决定要执行的操作。

我们没有任何 CLI 标志，但我们有一个完整的 HTTP 请求，可以据此决定要做什么：

-   HTTP 请求体（解析为 JSON 类型）
-   HTTP 查询字符串
-   HTTP 方法
-   HTTP 路径
-   其他自定义 HTTP 头

或者我们可以组合使用上述任意选项，例如“GET”配合某个路径“/todo/list”，或“DELETE”配合“/todo/delete/1”。这部分由你决定。

我会尽量保持简单，以便你至少能看到一种实际有效的方法。

下面的代码从函数的 YAML 文件中读取各种密钥和环境变量，并创建与数据库的连接。

```
var (
    dbUser   string
    dbPass   string
    host     string
    dbName   string
    sslMode  string
    port     int
    dbConn   *sql.DB
)

// init reads the various secrets and configuration required
// and then opens a DB connection, or panics if this fails.
// In the case of a failure, see the container's logs
func init() {
    var err error
```



```
dbUser, err = readSecret("db-user")
if err != nil {
    log.Fatalf("invalid db-user %s", err.Error())
}

dbPass, err = readSecret("db-pass")
if err != nil {
    log.Fatalf("invalid db-pass %s", err.Error())
}

dbName = os.Getenv("db_name")
host = os.Getenv("db_host")
sslMode = os.Getenv("db_ssl_mode")

if val, ok := os.LookupEnv("db_port"); ok {
    p, err := strconv.Atoi(val)
    if err != nil {
        log.Panicf("db_port is not a valid int: %s", err.Error())
    }
    port = p
}

dbConn, err = connect(dbUser, dbPass, host, dbName, sslMode, port)
if err != nil {
    log.Fatalf("connection error %s", err.Error())
}
}

// readSecret reads a file from /var/openfaas/secrets/<name> or
// returns an error
func readSecret(name string) (string, error) {
    data, err := os.ReadFile("/var/openfaas/secrets/" + name)
    if err != nil {
        return "", err
    }
    return strings.TrimSpace(string(data)), nil
}
```

然后我们结合 HTTP 方法和请求负载来决定如何处理请求。你可以列出待办事项或创建新事项。

```
// Handle creates a new todo item when a JSON body is
// passed with a description property using the HTTP POST method
//
// The GET method returns a list of all todo items in the database
// or a specific item when a /todo/<id> is passed.
func Handle(w http.ResponseWriter, r *http.Request) {

    var todo Todo
    action := ""
    if r.Method == "POST" {
        action = "create"
```
```
body, err := io.ReadAll(r.Body)
if err != nil {
    http.Error(w, "Error reading request body", http.StatusBadRequest)
    return
}
if err := json.Unmarshal(body, &todo); err != nil {
    http.Error(w, "Error parsing JSON", http.StatusBadRequest)
    return
}

} else if r.Method == "GET" {
    action = "list"
}

switch action {
case "create":
    err := create(dbConn, todo)
    if err != nil {
        http.Error(w, fmt.Sprintf("Unable to create todo item: %s", err.Error()),
            http.StatusInternalServerError)
        return
    }
    w.WriteHeader(http.StatusCreated)

case "get":
    todos, err := list(dbConn)
    if err != nil {
        http.Error(w, fmt.Sprintf("Unable to read todo items: %s", err.Error()),
            http.StatusInternalServerError)
        return
    }

    w.Header().Set("Content-Type", "application/json")
    body, _ := json.Marshal(todos)
    w.Write(body)

case "list":
    todos, err := list(dbConn)
    if err != nil {
        http.Error(w, fmt.Sprintf("Unable to read todo items: %s", err.Error()),
            http.StatusInternalServerError)
        return
    }
    w.Header().Set("Content-Type", "application/json")
    body, _ := json.Marshal(todos)
    w.Write(body)
default:
    http.Error(w, "Operation not supported", http.StatusBadRequest)
}
}
```

试一试：

```
cd todo-fn
go mod init
go mod tidy
cd ..

faas-cli up -f todo-fn.yml --build-arg GO111MODULE=on
```

现在测试该函数，你应该在表中有按照本书前面示例操作时创建的待办事项。我将 curl 的输出通过管道传给 jq 工具，它可以美化输出 JSON。

```
curl -s http://127.0.0.1:8080/function/todo-fn | jq
[
  {
    "id": 1,
    "description": "create",
    "created_date": "2021-06-21T10:53:46.176964Z",
  },
  {
    "id": 2,
    "description": "Publish this book",
    "created_date": "2021-06-21T10:57:04.374785Z",
  }
]
```

让我们尝试插入一个新的待办事项：

```
curl -i --data-binary '{"description": "Publish the serverless add-on"}' \
  http://127.0.0.1:8080/function/todo-fn
```

状态码是 202 Accepted，这正是我们所预期的。

```
curl -i --data-binary '{"description": "Publish the serverless add-on"}' \
  http://127.0.0.1:8080/function/todo-fn

HTTP/1.1 201 Created
Content-Length: 0
Content-Type: application/x-www-form-urlencoded
Date: Tue, 23 Nov 2021 11:41:32 GMT
X-Call-Id: 8776e2d9-97d7-4386-9aac-1579914811ab
X-Duration-Seconds: 0.035766
X-Start-Time: 1637667692744212162
```

我们还能获得运行时间（35ms）和一个唯一的调用 ID，可用于将日志与请求关联起来。

现在数据库中有三个事项：

```
curl -s http://127.0.0.1:8080/function/todo-fn | jq
[
  {
    "id": 1,
    "description": "create",
    "created_date": "2021-06-21T10:53:46.176964Z",
    "completed_date": null
  },
  {
```
```json
    "id": 2,
    "description": "Publish this book",
    "created_date": "2021-06-21T10:57:04.374785Z",
    "completed_date": null
  },
  {
    "id": 3,
    "description": "Publish the serverless add-on",
    "created_date": "2021-11-23T11:41:32.771247Z",
    "completed_date": null
  }
]
```

我们要如何以 RESTful 风格添加一个端点来获取特定的待办事项？

或许我们可以添加代码来处理 `/todo/{id}` 端点。

```go
// Handle creates a new todo item when a JSON body is
// passed with a description property using the HTTP POST method
//
// The GET method returns a list of all todo items in the database
// or a specific item when a /todo/<id> is passed.
func Handle(w http.ResponseWriter, r *http.Request) {

    var todo Todo
    action := ""
    if r.Method == "POST" {
        action = "create"

        body, err := io.ReadAll(r.Body)
        if err != nil {
            http.Error(w, "Error reading request body", http.StatusBadRequest)
            return
        }
        if err := json.Unmarshal(body, &todo); err != nil {
            http.Error(w, "Error parsing JSON", http.StatusBadRequest)
            return
        }

    } else if r.Method == "GET" {
        if strings.HasPrefix(r.URL.Path, "/todo/") {
            action = "get"
            idVal := strings.TrimPrefix(r.URL.Path, "/todo/")
            id, err := strconv.Atoi(idVal)
            if err != nil {
                http.Error(w, "Error reading todo ID from request URL", http.StatusBadRequest)
                return
            }
            todo = Todo{
                ID: id,
            }
        } else {
            action = "list"
        }
    }
```
```go
}

switch action {
case "create":
    err := create(dbConn, todo)
    if err != nil {
        http.Error(w, fmt.Sprintf("Unable to create todo item: %s", err.Error()),
            http.StatusInternalServerError)
        return
    }
    w.WriteHeader(http.StatusCreated)

case "get":
    todos, err := list(dbConn)
    if err != nil {
        http.Error(w, fmt.Sprintf("Unable to read todo items: %s", err.Error()),
            http.StatusInternalServerError)
        return
    }
    var target *Todo
    for _, t := range todos {
        if t.ID == todo.ID {
            target = &t
            break
        }
    }

    if target == nil {
        http.Error(w, fmt.Sprintf("Unable to find todo item: %d", todo.ID),
            http.StatusNotFound)
        return
    }

    w.Header().Set("Content-Type", "application/json")
    body, _ := json.Marshal(target)
    w.Write(body)

case "list":
    todos, err := list(dbConn)
    if err != nil {
        http.Error(w, fmt.Sprintf("Unable to read todo items: %s", err.Error()),
            http.StatusInternalServerError)
        return
    }
    w.Header().Set("Content-Type", "application/json")
    body, _ := json.Marshal(todos)
    w.Write(body)
default:
    http.Error(w, "Operation not supported", http.StatusBadRequest)
}
}
```

再次运行 faas-cli up 可以确认行为符合预期：

```bash
curl -s http://127.0.0.1:8080/function/todo-fn/todo/3 | jq
{
  "id": 3,
  "description": "Publish the serverless add-on",
  "created_date": "2021-11-23T11:41:32.771247Z"
}
```

### 完整示例

handler.go

```go
package function

import (
	"database/sql"
	"encoding/json"
	"fmt"
	"io"
	"log"
	"net/http"
	"os"
	"strconv"
	"strings"
)

var (
	dbUser  string
	dbPass  string
	host    string
	dbName  string
	sslMode string
	port    int
	dbConn  *sql.DB
)

// init reads the various secrets and configuration required
// and then opens a DB connection, or panics if this fails.
// In the case of a failure, see the container's logs
func init() {
	var err error

	dbUser, err = readSecret("db-user")
	if err != nil {
		log.Fatalf("invalid db-user %s", err.Error())
	}

	dbPass, err = readSecret("db-pass")
	if err != nil {
		log.Fatalf("invalid db-pass %s", err.Error())
	}

	dbName = os.Getenv("db_name")
	host = os.Getenv("db_host")
```



```go
http.Error(w, "Error reading todo ID from request URL", http.StatusBadRequest)
    return
}
    todo = Todo{
        ID: id,
    }
} else {
    action = "list"
}
}

switch action {
case "create":
    err := create(dbConn, todo)
    if err != nil {
        http.Error(w, fmt.Sprintf("Unable to create todo item: %s", err.Error()),
            http.StatusInternalServerError)
        return
    }
    w.WriteHeader(http.StatusCreated)

case "get":
    todos, err := list(dbConn)
    if err != nil {
        http.Error(w, fmt.Sprintf("Unable to read todo items: %s", err.Error()),
            http.StatusInternalServerError)
        return
    }
    var target *Todo
    for _, t := range todos {
        if t.ID == todo.ID {
            target = &t
            break
        }
    }

    if target == nil {
        http.Error(w, fmt.Sprintf("Unable to find todo item: %d", todo.ID),
            http.StatusNotFound)
        return
    }

    w.Header().Set("Content-Type", "application/json")
    body, _ := json.Marshal(target)
    w.Write(body)

case "list":
    todos, err := list(dbConn)
    if err != nil {
        http.Error(w, fmt.Sprintf("Unable to read todo items: %s", err.Error()),
            http.StatusInternalServerError)
        return
    }
    w.Header().Set("Content-Type", "application/json")
body, _ := json.Marshal(todos)
    w.Write(body)
default:
    http.Error(w, "Operation not supported", http.StatusBadRequest)
    }
}
```

db.go

```
package function

import (
    "database/sql"
    "fmt"
    _ "github.com/lib/pq"
)

func connect(user, password, host, dbName, sslMode string, port int) (*sql.DB, error) {
    connStr := "postgres://" + user + ":" + password + "@" + host + ":" + fmt.Sprintf("%d", port) + "/" + dbName + "?sslmode=" + sslMode

    db, err := sql.Open("postgres", connStr)
    if err != nil {
        return nil, err
    }

    err = db.Ping()
    if err != nil {
        return nil, err
    }

    return db, nil
}

func create(db *sql.DB, todo Todo) error {
    if len(todo.Description) == 0 {
        return fmt.Errorf("description is required")
    }

    res, err := db.Query(`INSERT INTO
    todo
    (id, description, created_date)
    VALUES
    (DEFAULT, $1, now());`,
        todo.Description)

    if err != nil {
        return err
    }

    defer res.Close()
    return nil
}
```

```
func list(db *sql.DB) ([]Todo, error) {
    rows, err := db.Query(`SELECT
        id,
        description,
        created_date,
        completed_date
        FROM todo;`)

    if err != nil {
        return []Todo{},
            fmt.Errorf("unable to get from todo table: %w", err)
    }

    todos := []Todo{}
    defer rows.Close()
    for rows.Next() {
        result := Todo{}
        err := rows.Scan(&result.ID,
            &result.Description,
            &result.CreatedDate,
            &result.CompletedDate)
        if err != nil {
            return []Todo{}, fmt.Errorf("row scan error: %w", err)
        }
        todos = append(todos, result)
    }
    return todos, nil
}
```

types.go:

```
package function

import (
    "time"
    _ "github.com/lib/pq"
)

type Todo struct {
    ID            int       `json:"id"`
    Description   string    `json:"description"`
    CreatedDate   time.Time `json:"created_date"`
    CompletedDate *time.Time `json:"completed_date,omitempty"`
}
```

todo-fn.yml:

```
version: 1.0
provider:
  name: openfaas
  gateway: http://127.0.0.1:8080
functions:
  todo-fn:
lang: golang-middleware
handler: ./todo-fn
image: docker.io/alexellis2/todo-fn:latest
secrets:
  - db-user
  - db-pass
environment:
  db_host: "todo-pg11-do-user-2197152-0.b.db.ondigitalocean.com"
  db_port: "25060"
  db_name: "defaultdb"
  db_ssl_mode: "require"
```

### 在多个环境之间管理配置

每当你在 staging 和 production 环境之间迁移此应用程序时，你需要更改其数据库 URL 和密钥。

密钥相对简单设置，你只需在两个环境中运行 faas-cli secrets 并按需设置值即可。

对于环境变量，你可以创建覆盖文件并在部署期间指定这些文件。

示例内容：staging.yaml：

```
environment:
  db_host: "todo-pg11-do-user-2197152-0.b.db.ondigitalocean.com"
  db_port: "25060"
  db_name: "defaultdb"
  db_ssl_mode: "require"
```

示例内容：todo-fn.yaml：

```
version: 1.0
provider:
  name: openfaas
  gateway: http://127.0.0.1:8080
functions:
  todo-fn:
    lang: golang-middleware
    handler: ./todo-fn
    image: docker.io/alexellis2/todo-fn:latest
    secrets:
      - db-user
      - db-pass
    environment_file:
      - ${OF_ENV:-staging}.yaml
```

此配置将 staging.yaml 作为默认值，但如果你将 OF_ENV 变量配置为 prod，则会改用 prod.yaml 中的值。

了解有关 YAML 的更多信息 - 环境变量替换

### 进一步任务

以下是你可以完成的一些进一步任务来测试你的知识：

- 你将如何重构代码为子包，使数据库代码存在于单独的包中？
- 你能否使用正则表达式代替字符串匹配来使代码更高效？

```
ID string
}

func Handle(w http.ResponseWriter, r *http.Request) {
    m := http.NewServeMux()

    m.HandleFunc("/v1/create", makeCreate())
    m.HandleFunc("/v1/list", makeList())

    m.ServeHTTP(w, r)
}

func makeCreate() func(http.ResponseWriter, *http.Request) {
    return func(w http.ResponseWriter, r *http.Request) {
        if r.Body != nil {
            defer r.Body.Close()
            c := Customer{}
            data, _ := io.ReadAll(r.Body)
            if err := json.Unmarshal(data, &c); err != nil {
            http.Error(w, "unable to parse input as a Customer", http.StatusInternalServerError)
                return
            }

            log.Printf("Create for %s", c.ID)
            w.WriteHeader(http.StatusCreated)
        }
    }
}

func makeList() func(http.ResponseWriter, *http.Request) {
    return func(w http.ResponseWriter, r *http.Request) {
        c := []Customer{
            {ID: "1"},
        }
        out, _ := json.Marshal(c)
        w.Header().Set("Content-Type", "application/json")
        w.Write(out)
    }
}
```

部署函数后，你可以调用它并查看各种路径的处理程序：

```
$ curl -s http://127.0.0.1:8082/v1/list|jq
[
  {
    "ID": "1"
  }
]

$ curl -s http://127.0.0.1:8082/v1/create
unable to parse input as a Customer

$ curl -i -s -d '{"ID": "2"}' http://127.0.0.1:8082/v1/create
HTTP/1.1 201 Created
```

你应该能够使用第三方库中的 mux，但请记住，使用 Mux 不一定“更好”

或比使用 switch 或 if 语句检查 URL 前缀来决定做什么更符合惯用法。

如果你想编写完整的 HTTP 微服务，并且不想使用函数处理程序，这也是一个选项，但你需要维护自己的 Dockerfile 或模板。模板抽象掉了用 Go 编写的 HTTP 端点所需的大量样板代码。

查看 OpenFaaS Workload 定义，了解需要做什么才能让 OpenFaaS 管理现有容器，或使用 OpenFaaS 模板构建的容器。

### 后续步骤

OpenFaaS 在 https://docs.openfaas.com/ 提供全面的参考文档。

你可能还喜欢：

- Serverless for Everyone Else - OpenFaaS 的手册，其中包含许多用 Node.js 和 JavaScript 编写的示例。
- Introduction to Serverless on Kubernetes - 由 Linux Foundation 委托的一门课程，涵盖 OpenFaaS 和 Python。
- The OpenFaaS blog - 用于用例、案例研究和新闻。

如果你已经在生产环境或工作中为内部业务使用 OpenFaaS，请向 ADOPTERS.md 文件发送一个条目以通知维护者。根据下载统计数据，这里仅代表了部分商业用户。

如果你想了解有关 OpenFaaS 在工作中的更多信息，请查看支持页面：openfaas.com/support
