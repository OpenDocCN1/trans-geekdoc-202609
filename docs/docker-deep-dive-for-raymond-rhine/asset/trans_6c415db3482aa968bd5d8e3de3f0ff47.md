

为你的系统拉取正确的镜像是一回事，但为所有不同的架构构建镜像又是呢？

`docker buildx` 命令让创建多架构镜像变得简单。例如，你可以在 `linux/arm` 的 Docker Desktop 上为 `linux/amd64` 以及可能的其他架构构建镜像。我们将在后续章节中执行此类构建，但 `docker buildx` 提供了两种创建多架构镜像的方法：

- 模拟 (Emulation)
- 构建云端 (Build Cloud)

模拟模式通过在运行目标架构的 QEMU 虚拟机内部在你的本地机器上执行不同架构的构建。它在大多数情况下都能工作，但速度较慢且没有共享缓存。

Build Cloud 是 Docker, Inc. 提供的一项新服务，在云端原生硬件上执行构建，不需要模拟。它非常快，允许你与同事共享公共构建缓存，并无缝集成到 Docker Desktop 以及任何支持云驱动的 buildx 版本的 Docker Engine 中。它还与 GitHub Actions 和其他 CI 解决方案集成。在编写本文时，Docker Build Cloud 是一项需要付费的订阅服务。

我们将在后续章节中同时使用这两者，但我运行了以下命令使用 Build Cloud 构建了 `nigelpoulton/tu-demo` 镜像的 AMD 和 ARM 版本。

```
$ docker buildx build \
  --builder=cloud-nigelpoulton-ddd-cloud \
  --platform=linux/amd64,linux/arm64 \
  -t nigelpoulton/tu-demo:latest --push
```

## 使用 Docker Scout 进行漏洞扫描有很多工和插件可以扫描镜像中的已知漏洞。

我们将查看 Docker Scout，因为它内置于 Docker 的几乎每一个层，包括 CLI、Docker Desktop、Docker Hub 以及 scout.docker.com 门户。它是一个非常优秀的服务，但需要付费订阅。虽然存在其他类似的产品和服务，但大多数都需要付费订阅。

最新版本的 Docker Desktop 预装了 Scout CLI 插件并已就绪。如果你运行的是不同版本的 Docker，可能可以通过 GitHub 仓库安装 CLI 插件。

你可以使用 `docker scout quickview` 命令获取镜像的漏洞概览。以下命令分析了 `nigelpoulton/tu-demo:latest` 镜像。如果本地不存在副本，它将从 Docker Hub 拉取并在本地进行分析。

```
docker scout quickview nigelpoulton/tu-demo:latest

  SBOM of image already cached, 66 packages indexed

| Target | nigelpoulton/tu-demo:latest | 0C |
| :--- | :--- | :--- |
| digest | b4210d0aa52f | |
| Base image | python:3-alpine | 0C |
| Updated base image | python:3.11-alpine | 0C |
```

输出显示为零严重漏洞 (0C)、一个高 (1H)、一个中等 (1M) 和零低风险 (0L)。

你可以使用 `docker scout cves` 命令获取更详细的信息，包括修复建议。

```
docker scout cves nigelpoulton/tu-demo:latest

✓ SBOM of image already cached, 66 packages indexed
✗ Detected 1 vulnerable package with 2 vulnerabilities
```

## 概述

分析的镜像
| Target | nigelpoulton/tu-demo:latest |
| :--- | :--- |
| digest | b4210d0aa52f |
| platform | linux/arm64/v8 |
| vulnerabilities | 0C 1H 1M 0L |
| size | 26 MB |
| packages | 66 |

## 软件包与漏洞
0C 1H 1M 0L expat 2.5.0-r2
pkg:apk/alpine/expat@2.5.0-r27os_name=alpine&os_version=31

x HIGH CVE-2023-52425
https://cve.docker.com/v/CVE-2023-52425
Affected range : <2.6.0-r0
Fixed version : 2.6.0-r0
```我截取了输出，使其只显示严重和高风险漏洞，但有几点是很清楚的：

- 它检测到了一个包含两个漏洞的受影响包
- 受影响的包名为 expat，我们正在运行的漏洞版本是 2.5.0-r2
- 它列出的漏洞为 CVE-2023-52425
- 它包含一个指向更多信息的 Scout 报告链接
- 它建议我们更新到包含修复的的2.6.0-r0 版本

图 6.14 显示了这在 Docker Desktop 中的外观，你可以在 Docker Hub 中获得类似的集成和视图。

![](img/aae0230bf8529bd80767c4c780dca8d3_116_0.png)

图 6.14 - Scout 与 Docker Desktop 的集成

scout.docker.com 门户提供概述仪表板，允许你配置策略，并让你设置与 Docker Hub 以及其他注册表的集成，以远程扫描和监控多个仓库。

## 删除镜像

你可以使用 `docker rmi` 命令删除镜像。rmi 是 remove image 的缩写。

删除镜像会将它们从本地仓库中移除，不再出现在 `docker images` 命令中。该操作还会删除本地文件系统中包含层数据的所有目录。然而，在删除所有引用这些镜像之前，Docker 不会删除多个镜像共享的层。

你可以通过名称、短 ID 或 SHA 删除镜像。你也可以用同一个命令删除多个镜像。

以下命令删除了三个镜像——一个通过名称，一个通过短 ID，一个通过 SHA。为了方便阅读，我精简了输出。

```
$ docker rmi redis:latest af111729d35a sha256:c5b1261d...f8elad6b
Untagged: redis:latest
Deleted: sha256:76d5908f5e19fdd73daf956a38826f790336ee4707d9028f
```

Untagged: nigelpoulton/tu-demo:v2
Deleted: sha256:af111729d35a09fd
```

