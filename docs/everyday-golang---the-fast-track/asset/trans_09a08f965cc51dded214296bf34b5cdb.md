
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

## 使用标志

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

## 定义单独的包或库

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
