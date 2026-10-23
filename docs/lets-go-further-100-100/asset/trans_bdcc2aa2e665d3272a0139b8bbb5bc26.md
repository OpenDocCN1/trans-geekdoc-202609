
**重要：** 本书的这一部分只有在你使用 Git 时才真正相关。如果你不使用，那完全没问题，你可以毫无问题地跳到下一章。

否则，如果你正在跟随操作（并且尚未执行），请继续在项目目录的根目录初始化一个新的 Git 仓库：

```
$ git init
Initialized empty Git repository in /home/alex/Projects/greenlight/.git/
```

然后像这样创建一个包含项目目录中所有文件的新提交：

```
$ git add .
$ git commit -m "Initial commit"
```

如果你使用 `git log` 命令查看提交历史，你会看到此提交的 *哈希*。

```
$ git log
commit 0f8573aab79f3cbee17d39901d5cb200121c7ed1 (HEAD -> master)
Author: Alex Edwards <alex@alexedwards.net>
Date:   Sun Apr 18 18:29:48 2021 +0200

    Initial commit
```

在我的例子中，提交哈希是 `0f8573aab79f3cbee17d39901d5cb200121c7ed1` —— 但你的会是不同的值。

你也可以使用 `git describe` 命令来获取仓库当前状态的‘可读性’描述符。像这样：

```
$ git describe --always --dirty
0f8573a
```

在这种情况下，我们可以看到 `git describe` 返回的是 *提交哈希的缩写版本*。我们还使用了 `--dirty` 标志，这意味着如果仓库中有任何未提交的更改，描述符将以 "`-dirty`" 为后缀。例如 `0f8573a-dirty`。

让我们更新我们的项目，以便在构建可执行文件时，将 `git describe` 的输出作为应用程序的‘版本号’烧录到二进制文件中。

为此，我们首先需要做的就是将 `cmd/api/main.go` 文件中的 `version` 常量改为变量，因为无法将值‘烧录’到常量中。

```
File: cmd/api/main.go

package main

...

// Remove the hardcoded version number and make version a variable instead of a constant.
var (
    buildTime string
    version   string
)

...
```

然后让我们更新 Makefile，使用与构建时间相同的模式，将 git describe 输出烧录到应用程序的 version 变量中。像这样：

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

current_time = $(shell date --iso-8601=seconds)
git_description = $(shell git describe --always --dirty)
linker_flags = '-s -X main.buildTime=${current_time} -X main.version=${git_description}'

## build/api: build the cmd/api application
.PHONY: build/api
build/api:
    @echo 'Building cmd/api...'
    go build -ldflags=${linker_flags} -o=./bin/api ./cmd/api
    GOOS=linux GOARCH=amd64 go build -ldflags=${linker_flags} -o=./bin/linux_amd64/api ./cmd/api
```

在这一点上，让我们再次快速运行 `git describe`：

```
$ git describe --always --dirty
0f8573a-dirty
```

这个输出是有意义的——上一次提交的哈希是 `0f8573a...`，而 `-dirty` 后缀表示我们的仓库现在包含未提交的更改（自上次提交以来我们修改了 `cmd/api/main.go` 和 `Makefile` 文件）。

让我们提交这些最近的更改，再次运行 `make build/api`，然后检查二进制文件中的版本号。像这样：

```
$ git add .
$ git commit -m "Generate version number automatically"
[master 76c976a] Generate version number automatically
  2 files changed, 6 insertions(+), 7 deletions(-)
```

```
$ make build/api
Building cmd/api...
go build -ldflags='-s -X main.buildTime=2021-04-18T18:43:32+02:00 -X main.version=76c976a' -o=./bin/api ./cmd/api
GOOS=linux GOARCH=amd64 go build -ldflags='-s -X main.buildTime=2021-04-18T18:43:32+02:00 -X main.version=76c976a' -o=./bin/linux_amd64/api ./cmd/api

$ ./bin/api -version
Version:      76c976a
Build time:   2021-04-18T18:43:32+02:00
```

我们可以看到，我们的二进制文件现在报告它是从 *具有该提交哈希的仓库的干净版本* 76c976a 构建的。让我们将其与项目的 `git log` 输出进行交叉检查：

```
$ git log
commit 76c976a07d0fce3d813f3a4748574f81b1e24226 (HEAD -> master)
Author: Alex Edwards <alex@alexedwards.net>
Date:   Sun Apr 18 18:39:17 2021 +0200

    Generate version number automatically

commit 0f8573aab79f3cbee17d39901d5cb200121c7ed1
Author: Alex Edwards <alex@alexedwards.net>
Date:   Sun Apr 18 18:29:48 2021 +0200

    Initial commit
```

看起来不错——我们 Git 历史中的提交哈希与我们的应用程序版本号完全一致。这意味着我们现在可以轻松识别特定二进制文件包含的确切代码——我们只需要使用 `-version` 标志运行二进制文件，然后将其与 Git 仓库历史进行交叉引用即可。

## 使用 Git 标签

在某些项目中，你可能希望用标签注释某些 Git 提交，通常是为了表示正式的发布版本号。

为了说明这一点，让我们像这样将 `v1.0.0` 标签添加到我们最新的提交中：

```
$ git tag v1.0.0
$ git log
commit 76c976a07d0fce3d813f3a4748574f81b1e24226 (HEAD -> master, tag: v1.0.0)
Author: Alex Edwards <alex@alexedwards.net>
Date:   Sun Apr 18 18:39:17 2021 +0200

    Generate version number automatically

...
```

如果你以这种方式为提交添加标签，那么在调用 `git describe` 生成应用程序版本号时，使用 `--tags` 和 `--long` 标志是个好主意。这将强制输出采用以下格式：

```
{tag}-{number of additional commits}-g{abbreviated commit hash}
```

让我们快速看看这对我们的项目目前是什么样子的：

```bash
$ git describe --always --dirty --tags --long
v1.0.0-0-g76c976a
```

因此，在这种情况下，我们可以从版本号看出，仓库基于 `v1.0.0`，在其之上没有额外的提交，最新的提交哈希是 `76c976a`。前缀提交哈希的 `g` 字符代表‘git’，存在是为了帮助区分该哈希与其他版本控制系统生成的哈希。

让我们更新我们的 `Makefile`，在生成版本号时使用这些额外的标志，像这样：

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

current_time = $(shell date --iso-8601=seconds)
git_description = $(shell git describe --always --dirty --tags --long)
linker_flags = '-s -X main.buildTime=${current_time} -X main.version=${git_description}'

...
```

然后继续提交此更改，重建二进制文件并检查版本号。你的输出应类似于这样：

```
$ git add .
$ git commit -m "Use --tags and --long flags when generating version number"
$ make build/api
$ ./bin/api -version
Version:      v1.0.0-1-gf27fd0f
Build time:   2021-04-18T18:54:05+02:00
```

版本号现已更改为 v1.0.0-1-gf27fd0f，表示二进制文件是使用来自提交 f27fd0f 的仓库代码构建的，该提交领先于 v1.0.0 标签 1 个提交。

在基础设施和架构方面，我们将在一台 Ubuntu Linux 服务器上运行所有内容。我们的技术栈将包括一个 PostgreSQL 数据库和 Greenlight API 的可执行二进制文件，其运行方式与本书迄今为止所见的大致相同。但除此之外，我们还将在 Greenlight API 前运行 Caddy 作为 *反向代理*。

使用 Caddy 有几个好处。它将自动为我们处理和终止 HTTPS 连接——包括通过 Let’s Encrypt 自动生成和管理 TLS 证书——我们还可以使用 Caddy 轻松限制对指标端点的互联网访问。

在本节中你将学习如何：

- 在 Digital Ocean 上部署一台运行 Ubuntu Linux 的服务器来托管你的应用程序。
- 自动化服务器配置——包括创建用户账户、配置防火墙和安装必要的软件。
- 自动化更新应用程序并将更改部署到服务器的过程。
- 如何使用 systemd 以非 root 用户身份将应用程序作为后台服务运行。
- 使用 Caddy 作为应用程序前面的反向代理来自动管理 TLS 证书并处理 HTTPS 连接。
