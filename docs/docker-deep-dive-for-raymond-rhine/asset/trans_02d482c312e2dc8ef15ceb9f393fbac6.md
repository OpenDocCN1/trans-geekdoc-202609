

运行以下命令拉取 redis 镜像并验证它是否存在于你的本地仓库中。

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

# 镜像仓库 (Image registries)

我们将镜像存储在称为仓库（registries）的集中位置。仓库的作用是安全地存储镜像，并使其易从不同环境中访问。

图 6.2 显示了仓库在“构建 > 传输 > 运行”流水线中的核心作用。

![](img/aae0230bf8529bd80767c4c780dca8d3_86_0.png)

图 6.2

大多数现代仓库实现了 OCI 分发规范，我们有时称之为 *OCI 仓库*。大多数仓库还实现了 Docker Registry v2 API，这意味着你可以使用 Docker CLI 和其他 API 工具来查询它们并以标准方式与它们交互。某些仓库还提供了高级功能，如镜像扫描和与构建流水线的集成。

最常见的仓库是 Docker Hub，但也存在其他仓库，包括基于互联网的第三方仓库和安全的本地仓库。然而，如前所述，Docker 是有主张的，除非你告诉它不同仓库的，否则它将默认使用 Docker Hub。在本书剩余部分我们将使用 Docker Hub，但这些原理适用于其他仓库。

镜像仓库包含一个或多个*镜像存储 (image repositories)*，而镜像存储包含一个或多个镜像。图 6.3 显示了一个具有三个存储的镜像仓库，每个存储包含一个或多个镜像。

![](img/aae0230bf8529bd80767c4c780dca8d3_87_0.png)

图 6.3 - 仓库架构

# 官方仓库 (Official repositories)

Docker Hub 有*官方仓库*的概念，这些是由 Docker 和应用供应商审核并筛选的镜像之家。这意味着它们*应该*包含最新的、高质量的安全的、文档完备且遵循良好实践的代码。

大多数流行的应用程序和操作系统在 Docker Hub 上都有官方仓库，它们很容易识别，因为它们位于 Docker Hub 命名空间的最顶层，并带有绿色的 Docker 官方镜像徽章。以下列表显示了几个存在于 Docker Hub 命名空间顶层的官方仓库及其 URL：

- nginx: https://hub.docker.com/_nginx/
- busybox: https://hub.docker.com/_busybox/
- redis: https://hub.docker.com/_redis/
- mongo: https://hub.docker.com/_mongo/

图 6.4 显示了 Docker Hub 上的 Alpine 和 NGINX 官方仓库。两者都有绿色的 Docker 官方镜像徽章，且拉取次数均超过十亿。此外，注意两者适用于广泛 CPU 架构。

![](img/aae0230bf8529bd80767c4c780dca8d3_89_0.png)

图 6.4 - Docker Hub 上的官方仓库

# 非官方仓库 (Unofficial repositories)

以下列表显示了我在非官方仓库的西部西部中的两个个人仓库，你不应该信任它们。

- nigelpoulton/gsd — https://hub.docker.com/r/nigelpoulton/gsd/
- nigelpoulton/k8sbook — https://hub.docker.com/r/nigelpoulton/k8book/

注意它们存在于 **nigelpoulton** 二级命名空间之下。这是表明它们不是官方仓库的几个迹象之一。

虽然非官方仓库中有许多优秀的镜像，但你应该始终假设任何来自非官方仓库的镜像都是**不安全的**。这基于永远不信任互联网软件的良好实践。事实上，在下载和使用 Docker 官方镜像时你也应该保持谨慎。

# 镜像命名与标记 (Image naming and tagging)

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

```几点需要注意：

- 如前所述，如果你在存储名称后没有指定镜像标签，Docker 假设你要 `latest`。如果仓库没有标记为 `latest` 的镜像，命令将失败。
- 标记为 `latest` 的镜像并不保证是最新的。

从非官方仓库拉取镜像几乎与官方仓库一样——你只需要在存储名称之前添加 Docker 用户名或组织。以下示例显示了从所有 nigelpoulton 的 tu-demo 存储拉取 v2 镜像。

```
$ docker pull nigelpoulton/tu-demo:v2
```

要从不同的仓库拉取镜像，你只需要在存储名称之前添加仓库的 DNS 名称。例如，以下命令从 GitHub Container Registry (ghcr.io) 上 Brandon Mitchell 的 regclient/regsync 仓库拉取最新镜像。

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

