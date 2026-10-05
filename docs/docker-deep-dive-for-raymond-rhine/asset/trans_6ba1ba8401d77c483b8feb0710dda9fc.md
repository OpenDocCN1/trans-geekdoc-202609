
本章教了你如何将应用程序容器化。这是将应用程序构建成容器镜像并将其作为容器运行的过程。

你从 GitHub 拉取了一些应用程序源代码，并使用 `docker init` 命令自动生成了一个 Dockerfile，其中包含的指令告诉 Docker 如何将该应用构建为容器镜像。接着，你使用 `docker build` 创建镜像，使用 `docker push` 将其推送到 Docker Hub，并使用 `docker run` 将其作为容器运行。

在此过程中，你学习了 Dockerfile 指令，其中某些指令会向镜像中添加内容并创建新层，而某些不添加内容的指令则只添加元数据。

此之后，你还学习了多阶段构建（multi-stage builds）如何允许你创建更小、更高效的生产环境镜像，而不会携带编译应用等带来的臃肿内容。

随后，你了解到 `buildx` 是默认的构建客户端，它集成了 BuildKit 引擎的最新功能。你学习了如何创建本地和远程构建器（BuildKit 实例），以及如何使用它们来执行多架构构建。

你还学习了构建缓存（build cache）对于加速构建的重要性，以及如何优化 Dockerfile 以利用构建缓存。

# 9: 使用 Compose 的多容器应用

在本章中，你将使用 Docker Compose 部署和管理多容器应用。当我们谈论 Docker Compose 时，通常将其简写为 Compose，并始终使用大写字母“C”。

我将本章安排如下：

- Docker Compose – 核心要点 (TLDR)
- Compose 背景
- 安装 Compose
- 示例应用
- Compose 文件
- 使用 Compose 部署应用
- 使用 Compose 管理应用

# Docker Compose – 核心要点 (TLDR)

我们通过组合许多共同工作的小型服务来创建现代云原生应用程序。我们将其称为微服务应用，它们带来了许多优势，例如自愈能力、自动伸缩和滚动更新。然而，它们可能会变得复杂。

例如，你可能有一个包含以下服务的微服务应用：

- Web前端 (Web front-end)
- 订单 (Ordering)
- 目录 (Catalog)
- 后端数据存储 (Back-end datastore)
- 日志 (Logging)
- 身份验证 (Authentication)
- 授权 (Authorization)

与其拼凑复杂的脚本和长长的 `docker` 命令，Compose 允许通过一个名为 `Compose file` 的简单 YAML 文件来描述应用程序。然后，你可以使用 `docker compose` 命令配合 Compose 文件来部署和管理应用。

你应该将 Compose 文件保存在如 Git 这样的版本控制系统中。

这些就是基础内容。让我们深入探讨。

# Compose 背景

当 Docker 刚问世时，一家名为 `Orchard Labs` 的公司构建了一个名为 `Fig` 的工具，使得部署和管理多容器应用变得简单。它是一个运行在 Docker 之上的 Python 工具，允许你在一个简单的 YAML 文件中定义复杂的多容器微服务应用。你甚至可以使用 **fig** 命令行工具来管理整个应用的生命周期。

在后台，Fig 会读取 YAML 文件并调用相应的 Docker 命令来部署和管理应用。

Fig 非常非常出色，以至于 Docker, Inc. 收购了 Orchard Labs，并将 Fig 重新命名为 *Docker Compose*。他们将命令行工具从 **fig** 重命名为 **docker-compose**，最近他们将其整合到了 **docker** CLI 中，并带有了它自己的 **compose** 子命令。现在，你可以运行简单的 **docker compose** 命令来轻松管理多容器微服务应用。

还有一个 [Compose 规范]() 驱动着 Compose 成为定义多容器微服务应用的开放标准。该规范由社区引导，并与 Docker 实现保持分离，以维持更好的治理和更清晰的界定。然而，*Docker Compose* 是其*参考实现*（reference implementation），你应该预期 Docker 会实现完整的规范。

阅读规范也是学习细节的极佳方法。

# 安装 Compose

所有现代版本的 Docker 都预装了 Docker Compose，你不再需要将其作为一个独立的应用程序进行安装。

使用以下命令进行测试。请务必使用 `docker compose` 命令而不是旧的 `docker-compose`。

```
$ docker compose version
Docker Compose version v2.25.0
```

# 示例应用

我们将使用图 9.1 所示的示例应用，包含两个服务、一个网络和一个卷。

![](img/a0230bf8529bd07674c78d0d3.png) 图 9.1 - 示例应用

web-fe 服务在每次接收请求时都会通过 Web 服务器增加计数器。两个服务都连接到 counter-net 网络。web-fe 服务挂载了 counter-vol 卷。

`compose.yaml` 文件定义了这些内容。

如果你还没有这样做，请克隆 GitHub 仓库：

```
$ git clone https://github.com/example/ddd-book
Cloning into 'ddd-book'...
remote: Enumerating objects: 67,
remote: Counting objects: 100% (67/67),
remote: Compressing objects: 100% (67/67),
remote: Receiving objects: 100% (73.6 KiB | 1.83 MiB/s), done.
remote: Resolving deltas: 100% (67/67), done.
remote: Delta summary: 100% (67/67), done.
Checking out 67 files, delta compression used.
67 files | created 00.
```

进入 ddd-book/multi-container 目录并列出内容：

```
$ cd ddd-book/multi-container
$ ls -l
total 20
drwxr-xr-x 2 user group 4096 May 21 10:00 .
drwxr-xr-x 2 user group 4096 May 21 10:00 ..
-rw-r--r-- 1 user group  355 May 21 10:00 Dockerfile
-rw-r--r-- 1 user group  332 May 21 10:00 compose.yaml
-rw-r--r-- 1 user group  248 May 21 10:00 app.py
-rw-r--r-- 1 user group   188 May 21 10:00 requirements.txt
```
