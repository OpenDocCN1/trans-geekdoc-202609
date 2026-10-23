
## ./... 模式

大多数 `go` 工具都支持 `./...` 通配符模式，例如 `go fmt ./...`、`go vet ./...` 和 `go test ./...`。此模式匹配当前目录和所有子目录，但排除 `vendor` *目录*。

一般来说，这很有用，因为它意味着我们不会不必要地格式化、检查或测试 `vendor` 目录中的代码——并且我们的 `make audit` 规则不会因为这些 vendored 包 *内部* 可能存在的问题而失败。

## 第 20.5 章。

## 构建二进制文件

目前我们一直使用 `go run` 命令（或最近的 `make run/api`）运行 API。但在本章中，我们将重点介绍如何*构建一个可执行二进制文件*，以便在无需安装 Go 工具链的情况下分发并在其他机器上运行。

构建二进制文件需要使用 `go build` 命令。简单示例的使用方式如下：

```bash
$ go build -o=./bin/api ./cmd/api
```

当我们运行此命令时，`go build` 会将 `cmd/api` 包（以及任何依赖包）*编译*为包含机器码的文件，然后将它们*链接*在一起形成可执行二进制文件。在上面的命令中，可执行二进制文件将输出到 `./bin/api`。

为方便起见，让我们在 makefile 中添加一个新的 `build/api` 规则来运行此命令，如下所示：

```
File: Makefile
```

```
$ ./bin/api -port=4040 -db-dsn=postgres://greenlight:pa55word@localhost/greenlight
{"level":"INFO","time":"2021-04-18T14:06:11Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-18T14:06:11Z","message":"starting server","properties":{"addr":":4040","env":"development"}}
```

### 减小二进制文件大小

如果仔细查看可执行二进制文件，您会发现其大小为 10470419 字节（约 10.5MB）。

```
$ ls -l ./bin/api
-rwxrwxr-x 1 alex alex 10470419 Apr 18 16:05 ./bin/api
```

> **注意：** 如果您跟随操作，您的二进制文件大小可能会略有不同。它取决于您的操作系统，以及您使用的 Go 的确切版本和第三方依赖项。

通过指示 Go 链接器从二进制文件中剥离 DWARF 调试信息和符号表，可以将二进制文件大小减少约 25%。我们可以在 go build 命令中使用链接器标志 -ldflags="-s" 来实现，如下所示：

```
File: Makefile

...
#
================================================================================
======= #
# BUILD
#
================================================================================
======= #

## build/api: build the cmd/api application
.PHONY: build/api
build/api:
    @echo 'Building cmd/api...'
    go build -ldflags='-s' -o=./bin/api ./cmd/api
```

如果再次运行 `make build/api`，您现在应该会发现二进制文件的大小已减少到 8 MB 以下。

```
$ make build/api
Building cmd/api...
go build -ldflags='-s' -o=./bin/api ./cmd/api
$ ls -l ./bin/api
-rwxrwxr-x 1 alex alex 7618560 Apr 18 16:08 ./bin/api
```

需要注意的是，剥离 DWARF 信息和符号表会使使用 Delve 或 gdb 等工具调试可执行文件变得更加困难。但通常情况下，您并不经常需要这样做——而且 Rob Pike 甚至提出了一个[开放提案]，建议将来将省略 DWARF 信息作为链接器的默认行为。

### 交叉编译

默认情况下，`go build` 命令会输出适用于您*本地机器操作系统和架构*的二进制文件。但它也支持交叉编译，因此您可以生成适用于不同机器的二进制文件。如果您在一个操作系统上开发，在另一个操作系统上部署，这尤其有用。

要查看 Go 支持的所有操作系统/架构组合列表，您可以运行 `go tool dist list` 命令，如下所示：

```text
$ go tool dist list
aix/ppc64
android/386
android/amd64
android/arm
android/arm64
darwin/amd64
...
```

您可以通过在运行 `go build` 时设置 `GOOS` 和 `GOARCH` 环境变量来指定要创建二进制文件的操作系统和架构。例如：

```
$ GOOS=linux GOARCH=amd64 go build {args}
```

在本书的下一节中，我们将介绍如何在 Digital Ocean 托管的 Ubuntu Linux 服务器上部署可执行二进制文件。为此，我们需要一个专为运行在具有 `linux/amd64` 操作系统和架构组合的机器上而设计的二进制文件。

因此，让我们更新 `make build/api` 规则，使其创建两个二进制文件——一个用于本地机器，另一个用于部署到 Ubuntu Linux 服务器。

```
File: Makefile

...

#
================================================================================
====== #
# BUILD
#
================================================================================
====== #

## build/api: build the cmd/api application
.PHONY: build/api
build/api:
    @echo 'Building cmd/api...'
    go build -ldflags='-s' -o=./bin/api ./cmd/api
```

```
GOOS=linux GOARCH=amd64 go build -ldflags='-s' -o=./bin/linux_amd64/api ./cmd/api
```

如果您跟随操作，请继续再次运行 `make build/api`。

您应该会看到现在创建了两个二进制文件——交叉编译的二进制文件位于 `./bin/linux_amd64` 目录下，如下所示：

```
$ make build/api
Building cmd/api...
go build -ldflags='-s' -o=./bin/api ./cmd/api
GOOS=linux GOARCH=amd64 go build -ldflags='-s' -o=./bin/linux_amd64/api ./cmd/api
$ tree ./bin
./bin
├── api
└── linux_amd64
    └── api
```

作为一般规则，您可能不希望将 Go 二进制文件与源代码一起提交到版本控制中，因为它们会显著增加存储库的大小。

因此，如果您跟随操作，让我们快速在 `.gitignore` 文件中添加一条额外的规则，指示 Git 忽略 `bin` 目录的内容。

```
$ echo 'bin/' >> .gitignore
$ cat .gitignore
.envrc
bin/
```

## 附加信息

### 构建缓存

需要注意的是，go build 命令会将构建输出缓存到 Go 构建缓存中。此缓存输出将在适当的未来构建中再次重用，这可以显著加快应用程序的整体构建时间。

如果您不确定构建缓存的位置，可以通过运行 go env GOCACHE 命令来检查：

```
$ go env GOCACHE
/home/alex/.cache/go-build
```

您还应注意，构建缓存不会自动检测代码通过 cgo 导入的 C 库的任何更改。因此，如果自上次构建以来您更改了 C 库，则在运行 `go build` 时需要使用 -a 标志强制重建所有包。或者，您也可以使用 `go clean` 清除缓存：

```
$ go build -a -o=/bin/foo ./cmd/foo      # Force all packages to be rebuilt
$ go clean -cache                      # Remove everything from the build cache
```

> **注意：** 如果您在非 `main` 包上运行 `go build`，构建输出将存储在构建缓存中以便重用，但不会生成可执行文件。

## 管理和自动化版本号

本书一开始，我们将应用程序的版本号硬编码为 cmd/api/main.go 文件中的常量 "1.0.0"。

在本章中，我们将采取措施使查看和管理此版本号变得更容易，并解释如何基于 Git 提交自动生成版本号并将其集成到应用程序中。

### 显示版本号

让我们首先更新我们的应用程序，以便可以通过使用 -version 命令行标志运行二进制文件来轻松检查版本号，如下所示：

```
$ ./bin/api -version
Version:      1.0.0
```

从概念上讲，实现起来相当直接。我们需要定义一个布尔版本命令行标志，检查此标志 on
