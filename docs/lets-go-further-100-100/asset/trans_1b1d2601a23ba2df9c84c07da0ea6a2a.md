
`requirePermission()` 中间件能正确协同工作，以允许或拒绝访问特定端点。

## 模块代理与依赖本地化（Vendoring）

在 Go 代码中使用第三方包的一个风险是，包仓库可能不再可用。例如，`httprouter` 包在我们的应用程序中扮演着核心角色，如果作者决定从 GitHub 上删除它，我们将不得不手忙脚乱地寻找替代品。

（我并不是说 `httprouter` 会发生这种情况——只是用它举例！）

幸运的是，Go 提供了两种方法可以降低这种风险：*模块代理和依赖本地化（vendoring）*。

### 模块代理

从版本 1.13 开始，Go 默认支持*模块代理*（也称为*模块镜像*）。这些服务会从原始权威仓库（例如 GitHub、GitLab 或 Bitbucket 上的仓库）镜像源代码。

在机器上运行 `go env` 命令，可以打印 Go 操作环境的设置。输出应该类似这样：

```
$ go env
GO111MODULE=""
GOARCH="amd64"
GOBIN=""
GOCACHE="/home/alex/.cache/go-build"
GOENV="/home/alex/.config/go/env"
GOEXE=""
GOFLAGS=""
GOHOSTARCH="amd64"
GOHOSTOS="linux"
GOINSECURE=""
GOMODCACHE="/home/alex/go/pkg/mod"
GONOPROXY=""
GONOSUMDB=""
GOOS="linux"
GOPATH="/home/alex/go"
GOPRIVATE=""
GOPROXY="https://proxy.golang.org,direct"
GOROOT="/usr/local/go"
GOSUMDB="sum.golang.org"
GOTMPDIR=""
GOTOOLDIR="/usr/local/go/pkg/tool/linux_amd64"
GCCGO="gccgo"
AR="ar"
CC="gcc"
CXX="g++"
CGO_ENABLED="1"
GOMOD="/home/alex/Projects/greenlight/go.mod"
CGO_CFLAGS="-g -O2"
CGO_CPPFLAGS=""
CGO_CXXFLAGS="-g -O2"
CGO_FFLAGS="-g -O2"
CGO_LDFLAGS="-g -O2"
PKG_CONFIG="pkg-config"
GOGCCFLAGS="..."
```

这里需要关注的是 `GOPROXY` 设置，它包含一个以逗号分隔的模块镜像列表。默认情况下，其值如下：

```
GOPROXY="https://proxy.golang.org,direct"
```

我们看到的 URL `https://proxy.golang.org` 指向一个由 Google 的 Go 团队维护的*模块镜像*，其中包含数万个开源 Go 包的源代码副本。

每当你使用 `go` 命令获取包时——无论是通过 `go get` 还是某个 `go mod *` 命令——它都会首先尝试从这个镜像检索源代码。

如果镜像已经存储了所需包和版本号的源代码副本，它会立即以 zip 文件形式返回该代码。否则，如果尚未存储，镜像将尝试从权威仓库获取代码，代理转发给你，并存储以供将来使用。

如果镜像根本无法获取代码，那么它将返回错误响应，`go` 工具将回退到直接从权威仓库获取副本（感谢 `GOPROXY` 设置中的 `direct` 指令）。

使用模块镜像作为第一个获取位置有几个好处：

- `https://proxy.golang.org` 模块镜像*通常*会长期存储包，从而在原始仓库从互联网上消失时提供一定程度的保护。
- 一旦存储在 `https://proxy.golang.org` 模块镜像中，就无法覆盖或删除包。这有助于防止包作者（或攻击者）发布具有*相同版本号*的修改版本时可能出现的任何 bug 或问题。
- 从 `https://proxy.golang.org` 镜像获取模块通常比从权威仓库获取要快得多。

在大多数情况下，我通常建议保持 `GOPROXY` 设置为默认值。

但如果你不想使用 Google 提供的模块镜像，或者你处于阻止它的防火墙后面，还有其他替代方案，例如 https://goproxy.io 和微软提供的 https://athens.azurefd.net，你可以尝试。或者你甚至可以使用开源 Athens 和 goproxy 项目托管自己的模块镜像。

例如，如果你想切换到使用 `https://goproxy.io` 作为主要镜像，然后回退到使用 `https://proxy.golang.org` 作为次要镜像，再回退到直接获取，你可以像这样更新你的 `GOPROXY` 设置：

```bash
$ export GOPROXY=https://goproxy.io,https://proxy.golang.org,direct
```

或者如果你想完全禁用模块镜像，只需将值设置为 `direct`，像这样：

```
$ export GOPROXY=direct
```

### 依赖本地化（Vendoring）

Go 的模块镜像功能很棒，我推荐使用。但它并不是所有开发者和所有项目的银弹。

例如，也许你不想使用 Google 或其他第三方提供的模块镜像，但也不想承担托管自己的镜像的开销。或者你可能需要在没有网络访问的环境中例行工作。在这些场景中，你可能仍然希望降低依赖消失的风险，但使用模块镜像不可能或不吸引人。

你还应该注意，默认的 `proxy.golang.org` 模块镜像并不绝对保证会永远存储模块副本。从 FAQ 中：

> > *proxy.golang.org 不会永远保存所有模块。这有很多原因，但一个原因是如果 proxy.golang.org 无法检测到合适的许可证。在这种情况下，只有临时缓存的模块副本会*
> *被提供，如果模块从原始来源被删除并变得过时，它可能会不可用。*

此外，如果你需要在 5 年或 10 年后回到一个“冷”代码库，`proxy.golang.org` 模块镜像仍然可用吗？希望它会——但很难确定。

因此，出于这些原因，使用 `go mod vendor` 命令对项目依赖进行*依赖本地化*仍然是一种明智的做法。以这种方式进行依赖本地化，基本上会将第三方包的源代码完整副本存储在项目中的一个 *vendor* 文件夹中。

让我们演示如何做到这一点。我们将首先调整 `Makefile`，添加一个新的 `vendor` 规则，该规则调用 `go mod tidy`、`go mod verify` 和 `go mod vendor` 命令，如下所示：

```
File: Makefile

...

#
================================================================================
====== #
# QUALITY CONTROL
#
================================================================================
====== #

## audit: tidy and vendor dependencies and format, vet and test all code
.PHONY: audit
audit: vendor
```

```make
@ echo 'Formatting code...'
go fmt ./...
@ echo 'Vetting code...'
go vet ./...
staticcheck ./...
@ echo 'Running tests...'
go test -race -vet=off ./...

## vendor: tidy and vendor dependencies
.PHONY: vendor
vendor:
    @echo 'Tidying and verifying module dependencies...'
    go mod tidy
    go mod verify
    @echo 'Vendoring dependencies...'
    go mod vendor
```

除了添加 `vendor` 规则之外，我们还做了其他一些更改：

- 我们从 `audit` 规则中移除了 `go mod tidy` 和 `go mod verify` 命令。
- 我们添加了 `vendor` 规则作为 `audit` 的前提条件，这意味着每次执行 `audit` 规则时它都会自动运行。

为了明确这里的幕后情况，让我们快速了解一下运行 `make vendor` 时会发生什么：

- `go mod tidy` 命令将确保 `go.mod` 和 `go.sum` 文件列出我们项目所需的所有依赖项（并且没有不必要的依赖项）。
- `go mod verify` 命令将验证模块缓存中存储的依赖项（位于机器上的 `$GOPATH/pkg/mod`）是否与 `go.sum` 文件中的加密哈希匹配。
- `go mod vendor` 命令会将必要的源代码从模块缓存复制到项目根目录中一个新的 `vendor` 目录中。

让我们尝试运行这个新的 vendor 规则，如下所示：

```
$ make vendor
Tidying and verifying module dependencies...
go mod tidy
go mod verify
all modules verified
Vendoring dependencies...
go mod vendor
```

完成后，你应该会看到创建了一个新的 `vendor` 目录，其中包含所有源代码的副本以及一个 `modules.txt` 文件。`vendor` 文件夹中的目录结构应该类似于这样：

```
$ tree -L 3 ./vendor/
./vendor/
├── github.com
│   ├── felixge
│   │   └── httpsnoop
│   └── go-mail
```

