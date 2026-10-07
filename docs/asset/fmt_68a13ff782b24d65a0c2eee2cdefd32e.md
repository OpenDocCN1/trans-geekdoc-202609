
本章中的一些图表显示了 `shim` 组件。

`shim` 是一种流行的软件工程模式，Docker Engine 在 `containerd` 和 OCI 层之间使用它们，带来了以下益处：

- 无守护进程容器
- 提高效率
- 使 OCI 层变得可扩展

我们已经提到过无守护进程容器。

在效率方面，`containerd` 为每个新容器 `fork` 出一个 `shim` 和一个 `runc` 进程。然而，每个 `runc` 进程在容器开始运行后就会退出，留下 `shim` 进程作为容器的父进程。`shim` 是轻量级的，位于 `containerd` 和容器之间。它报告容器状态并执行低级任务，例如保持容器的 STDIN 和 STDOUT 流打开。

`shim` 还让将 `runc` 替换为其他低级运行时成为可能。

在 Linux 系统上，Docker 将我们讨论的组件实现为以下独立的二进制文件：

- `/usr/bin/dockerd`（Docker 守护进程）
- `/usr/bin/containerd`
- `/usr/bin/containerd-shim-runc-v2`
- `/usr/bin/runc`

你可以通过运行 `ps` 命令在基于 Linux 的 Docker 宿主机看到所有这些内容。某些进程只有在系统有运行的容器时才会存在，如果你在 Mac 上使用 Docker Desktop，则看不到它们，因为 Docker Engine 运行在虚拟机内部。

在编写本文时，Docker 已经剥离了守护进程的大部分功能，让守护进程专注于提供 API。

### 章节总结

Docker Engine 是一个能够轻松构建、分发和运行容器的平台。它实现了 OCI 标准，是一个由许多微小、专用组件组成的模块化应用程序。

Docker 守护进程实现了 Docker API，但大多数其他功能已被剥离，并作为 `containerd` 和 `runc` 等独立的可组合工具实现。

`containerd` 执行镜像管理任务并监督容器的生命周期管理，例如启动、停止和删除容器。Docker, Inc. 最初编写了它，然后将其贡献给了 CNCF。它被归类为高级运行时，并被许多其他项目（包括 Kubernetes、Firecracker 和 Fargate）使用。

`containerd` 依赖于名为 `runc` 的低级运行时与宿主机内核交互并构建容器。`runc` 是 OCI runtime-spec 的参考实现，并期望从符合 OCI 规范的边界中启动容器。`containerd` 与 `runc` 通信，并确保 Docker 镜像作为符合 OCI 规范的边界呈现给 `runc`。

`runc` 基于 `libcontainer` 的代码，你可以将其作为独立的 CLI 工具运行以创建容器，它几乎用在所有使用 `containerd` 的地方。

`shim` 让将 `containerd` 与其他低级运行时成为可能。

## 6：与镜像配合

在本章中，我们将深入研究 Docker 镜像。你将学习镜像是什么、如何与它们交互，以及它们在底层是如何工作的。你将在第 8 章“应用程序容器化”中学习如何构建自己的镜像。

我将章节安排如下：

- Docker 镜像 – 概述 (TLDR)
- 镜像简介介绍
- 拉取镜像
- 镜像仓库
- 镜像命名和标记
- 镜像与层
- 按摘要拉取镜像
- 多架构镜像
- 使用 Docker Scout 进行漏洞扫描
- 删除镜像

### Docker 镜像 – 概述 (TLDR)

在开始之前，以下所有术语的意思都是相同的，我们将交替使用：*镜像 (Image)、Docker 镜像 (Docker image)、容器镜像 (container image)* 和 OCI 镜像。

镜像是一个只读包，包含了运行应用程序所需的所有内容。这意味着它们包含了应用程序代码、依赖项、一组极简的操作系统构建体和元数据。你可以从单个镜像启动多个容器。

如果你熟悉 VMware，镜像有点像虚拟机模板——虚拟机模板像一个已停止的虚拟机，而镜像像一个已停止的容器。如果你是一个开发者，镜像类似于*类 (classes)* —— 你可以从类中创建一个或多个对象，而你可以从一个镜像中创建一个或多个容器。

获取镜像最简单的方法是从*仓库 (registry)* 中拉取。Docker Hub 是最常见的仓库，而*拉取 (pulling)* 镜像会将其下载到本地机器，Docker 在那里它可以启动一个或多个容器。还存在其他仓库，Docker 与所有它们都能工作。

镜像是通过堆叠独立的*层 (layers)* 制成的，并将它们表示为单一的统一对象。其中一层可能包含操作系统组件，另一层可能包含应用程序依赖项，Docker 堆叠这些层并使它们看起来像一个统一系统。

镜像通常很小。例如，官方的 NGINX 镜像约为 60MB，官方的 Redis 镜像约为 40MB。然而，Windows 镜像可能巨大。

这就是核心介绍。让我们进一步深入。

### 镜像简介

我们已经说过镜像像是停止的容器。你甚至可以停止容器并从它创建一个新镜像。基于这种想法，镜像是*构建时 (build-time)* 构建体，而容器是*运行时 (run-time)* 构建体。图 6.1 显示了*构建和运行*的性质，你可以从单个镜像启动多个容器。

![](img/aae0230bf8529bd80767c4c780dca8d3_81_0.png)

图 6.1

`docker run` 命令启动容器的最常用方式。一旦容器运行，镜像和容器就绑定了，只有当你删除了使用它的容器后才能删除该镜像。

容器设计用于运行单个应用程序或微服务。因此，它们应该只包含代码和依赖项。

例如，官方的 Alpine Linux 镜像目前约为 3MB。这是因为它没有带六种 shell、三种不同的包管理器以及你“可能”每十年需要一次的工具。事实上，镜像不带 shell 或包管理器已越来越常见——如果应用程序在运行时不需要它，镜像就不会包含它。我们称这些为精简镜像。

另一个让镜像保持较小的原因是缺少操作系统内核。这是因为容器使用它们运行所在的宿主机内核。大多数镜像中与操作系统相关的组件是文件系统，你有时会听到人们说包含操作系统。

不幸，Windows 镜像可能巨大。例如，某些 Windows 镜像可能有几个 GB 大，推送和拉取需要很长时间。

### 拉取镜像

干净的 Docker 安装有一个本地仓库。

本地仓库是本地机器上用于存储镜像以便方便访问的区域。我们有时称之为镜像缓存，在 Linux 上它通常位于 `/var/lib/docker/<storage-driver>`。然而，如果你使用 Docker Desktop，它将在 Docker 虚拟机内部。

运行以下命令检查你的本地仓库内容。此示例中有三个与运行的三个 Docker Desktop 扩展相关的镜像。你的将会不同，并且可能是空的。

| REPOSITORY | TAG | IMAGE ID | CREATED |
|---|---|---|---|
| docker/disk-usage-extension | 0.2.9 | f4c95478a537 | 2 周前 |
| docker/logs-explorer-extension | 0.2.6 | 417dd9a8f96d | 2 个月前 |
| portainer/portainer-docker-extension | 2.19.4 | 908d04d20e86 | 2 个月前 |

获取镜像的过程被称为*拉取 (pulling)*。

运行以下命令拉取 `redis` 镜像并验证它是否存在于你的本地仓库中。

**注意：如果你在 Linux 上进行操作，且尚未将用户账户添加到本地 docker Unix 组，你可能需要在所有后续命令的开头加上 `sudo`。**

```
$ docker pull redis

Using default tag: latest ----- Assume the 'latest'

latest: Pulling from library/redis ----- Assume you want to

08df40659127: Download complete ----- Pulling layer

4f4b700ef54: Already exists ----- Pulling layer (loca

4fe7aaab04: Download complete ----- Pulling layer

57de0f129a55: Download complete ----- Pulling layer

546e941f15b: Download complete ----- Pulling layer

f7f7da262cd8: Download complete ----- Pulling layer

f45ab649e450: Download complete ----- Pulling layer

983f900bbc88: Download complete ----- Pulling layer

Digest: sha256:76d5908f5e19fdd73daf956a38826f79033ee4707d90283

Status: Downloaded new image for redis:latest

docker.io/redis:latest ----- docker.io = Docker
```

```
$ docker images

REPOSITORY TAG CREATED SIZE

redis latest 11c3e418c296 2 weeks ago 223MB
```

该镜像现在存在于你的本地仓库中。然而，我在 `docker pull` 的输出中标记了几行有趣的内容。我们将在本章节稍后的部分详细介绍它们，但现在值得简单提一下。

Docker 是有主张的，并且在拉取镜像时做了两个假设：

- 1. 它假设你想拉取标记为 `latest` 的镜像。
- 2. 它假设你想从 Docker Hub 拉取镜像。

你可以覆盖这两项设置，但如果你不覆盖它们，Docker 将使用这些作为默认值。

Redis 镜像有八个层。然而，Docker 只拉取了七层，因为它已经有了其中某一层的本地副本。这是因为我的系统运行了 Portainer Docker Desktop 扩展，它基于一个与 Redis 镜像共享公共层的镜像。你很快就会学到这一点，镜像可以共享层，而 Docker 足够智能，只拉取它尚未的层。

我们将在本章节稍后详细讨论这些点。

## 镜像仓库 (Image registries)

我们将镜像存储在称为仓库（registries）的集中位置。仓库的作用是安全地存储镜像，并使其易从不同环境中访问。

图 6.2 显示了仓库在“构建 > 传输 > 运行”流水线中的核心作用。

![](img/aae0230bf8529bd80767c4c780dca8d3_86_0.png)

图 6.2

大多数现代仓库实现了 OCI 分发规范，我们有时称之为 *OCI 仓库*。大多数仓库还实现了 Docker Registry v2 API，这意味着你可以使用 Docker CLI 和其他 API 工具来查询它们并以标准方式与它们交互。某些仓库还提供了高级功能，如镜像扫描和与构建流水线的集成。

最常见的仓库是 Docker Hub，但也存在其他仓库，包括基于互联网的第三方仓库和安全的本地仓库。然而，如前所述，Docker 是有主张的，除非你告诉它不同仓库的，否则它将默认使用 Docker Hub。在本书剩余部分我们将使用 Docker Hub，但这些原理适用于其他仓库。

镜像仓库包含一个或多个*镜像存储 (image repositories)*，而镜像存储包含一个或多个镜像。图 6.3 显示了一个具有三个存储的镜像仓库，每个存储包含一个或多个镜像。

![](img/aae0230bf8529bd80767c4c780dca8d3_87_0.png)

图 6.3 - 仓库架构

### 官方仓库 (Official repositories)

Docker Hub 有*官方仓库*的概念，这些是由 Docker 和应用供应商审核并筛选的镜像之家。这意味着它们*应该*包含最新的、高质量的安全的、文档完备且遵循良好实践的代码。

大多数流行的应用程序和操作系统在 Docker Hub 上都有官方仓库，它们很容易识别，因为它们位于 Docker Hub 命名空间的最顶层，并带有绿色的 Docker 官方镜像徽章。以下列表显示了几个存在于 Docker Hub 命名空间顶层的官方仓库及其 URL：

- nginx: https://hub.docker.com/_nginx/
- busybox: https://hub.docker.com/_busybox/
- redis: https://hub.docker.com/_redis/
- mongo: https://hub.docker.com/_mongo/

图 6.4 显示了 Docker Hub 上的 Alpine 和 NGINX 官方仓库。两者都有绿色的 Docker 官方镜像徽章，且拉取次数均超过十亿。此外，注意两者适用于广泛 CPU 架构。

![](img/aae0230bf8529bd80767c4c780dca8d3_89_0.png)

图 6.4 - Docker Hub 上的官方仓库

### 非官方仓库 (Unofficial repositories)

以下列表显示了我在非官方仓库的西部西部中的两个个人仓库，你不应该信任它们。

- nigelpoulton/gsd — https://hub.docker.com/r/nigelpoulton/gsd/
- nigelpoulton/k8sbook — https://hub.docker.com/r/nigelpoulton/k8book/

注意它们存在于 `nigelpoulton` 二级命名空间之下。这是表明它们不是官方仓库的几个迹象之一。

虽然非官方仓库中有许多优秀的镜像，但你应该始终假设任何来自非官方仓库的镜像都是**不安全的**。这基于永远不信任互联网软件的良好实践。事实上，在下载和使用 Docker 官方镜像时你也应该保持谨慎。

## 镜像命名与标记 (Image naming and tagging)

大多数时候，你将根据名称处理镜像，并且可以从名称中学习很多关于镜像的信息。图 6.5 显示了一个完全限定的镜像名称，包括仓库名称、用户/组织名称、存储名称和标签。如果你没有指定，Docker 会自动填充仓库和标签值。

![](img/aae0230bf8529bd80767c4c780dca8d3_90_0.png)

引用官方仓库的镜像非常简单。你只需要提供用冒号分隔的存储名称和镜像名称。有时我们把镜像名称称为标签。从官方仓库拉取镜像的格式是：`docker pull <repository>:<tag>`

之前的示例通过以下命令拉取了 Redis 镜像。它拉取了标记为 `latest` 的镜像。

```
$ docker pull redis:latest
```

以下示例显示了如何拉取几个官方镜像：

```
$ docker pull mongo:7.0.5 从官方仓库拉取标记为 7.0.5 的镜像

$ docker pull busybox:glibc 从官方仓库拉取标记为 glibc 的镜像

$ docker pull alpine 从官方仓库拉取标记为 latest 的镜像
```
几点需要注意：

- 如前所述，如果你在存储名称后没有指定镜像标签，Docker 假设你要 `latest`。如果仓库没有标记为 `latest` 的镜像，命令将失败。
- 标记为 `latest` 的镜像并不保证是最新的。

从非官方仓库拉取镜像几乎与官方仓库一样——你只需要在存储名称之前添加 Docker 用户名或组织。以下示例显示了从所有 nigelpoulton 的 tu-demo 存储拉取 v2 镜像。

```
$ docker pull nigelpoulton/tu-demo:v2
```

要从不同的仓库拉取镜像，你只需要在存储名称之前添加仓库的 DNS 名称。例如，以下命令从 GitHub Container Registry (`ghcr.io`) 上 Brandon Mitchell 的 `regclient/regsync` 仓库拉取最新镜像。

```
$ docker pull ghcr.io/regclient/regsync:latest

latest: Pulling from regclient/regsync

614f2b64ccf9: Download complete

7746d6728537: Download complete

685af2c79c31: Download complete

4c377311167a: Download complete

662e9541e042: Download complete

digest: sha256:149a95d473d6beed2a1404d7c3b000ddffa583a94836587ba8e33

Status: Downloaded newer image for ghcr.io/regclient/regsync:latest

ghcr.io/regclient/regsync:latest
```

注意拉取（pull）的操作与 Docker Hub 看起来完全相同。这是因为 GHCR 支持 OCI 镜像规范并实现了 Docker Registry v2 API。

### 具有多个标签的镜像

你可以为单个镜像赋予任意数量的标签。

从表面上看，以下输出似乎列出了三个镜像。但仔细观察会发现，其实只有两个 —— `b4210d0aa52f` 镜像被标记为 `latest` 和 `v1`。

```
$ docker images

REPOSITORY             TAG      IMAGE ID        CREATED

igelpoulton/tu-demo  latest   b4210d0aa52f  2 days ago

igelpoulton/tu-demo  v1       b4210d0aa52f  2 days ago
```
