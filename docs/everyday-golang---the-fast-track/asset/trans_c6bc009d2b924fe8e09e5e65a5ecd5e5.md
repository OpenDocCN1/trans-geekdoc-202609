
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

## Vendoring 与 Go modules

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
