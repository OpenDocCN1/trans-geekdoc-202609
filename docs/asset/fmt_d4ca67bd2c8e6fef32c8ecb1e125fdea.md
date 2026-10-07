
你仍然在 Docker Hub 上有一个镜像副本，并在本地文件系统中 spin 应用。可以随意删除这些。

### 章节总结

在本章中，你将一个 Wasm 应用容器化并在 Wasm 容器中运行了它。

Wasm 是驱动云计算下一一浪潮的新技术。Wasm 应用比传统的 Linux 容器更小、更快、更安全且更具移植性。然而，它们并不那么灵活。例如，在编写时，Wasm 应用对于具有密集 I/O 要求或复杂网络的应用并不理想。

幸运的是，Docker 已经支持了 Wasm，并且 Docker Desktop 配带了许多流行的 Wasm 运行时。这意味着你可以使用 `docker build` 和 `docker run` 等行业标准工具来对 Wasm 应用进行容器化并运行。你甚至可以将它们推送到如 Docker Hub 等 OCI 注册表中。

## 13: Docker 网络

总是网络的问题！

每当我们遇到基础设施问题时，总是总是归咎于网络。我们之所以这样做的原因之一是网络处于一切的核心。考虑到这一点，对 Docker 网络有深入的理解至关重要。

在 Docker 早期，网络化非常困难。幸运的是，如今这几乎成了一种享受 ;)

本章将带你快速上手 Docker 网络的基础知识。你将学习容器网络模型（CNM）和 libnetwork 背后的所有理论，并将在大量示例中进行实践。你将在下一章中学习叠加网络（overlay networks）。

我将本章分为以下部分：

- Docker 网络 – 简要概述 (TLDR)
- Docker 网络理论
- 通过端口映射实现单主机桥接网络
- 连接到现有网络和 VLAN
- 服务发现
- 入口负载均衡

在我们开始之前，有几点说明。

我们将涵盖的内容都与 Linux 容器有关，我建议你使用 Multipass 或 Play with Docker 之类的工具进行练习，因为它们让你轻松访问我们将用到的某些 Linux 命令。我不建议在 Docker Desktop 上进行练习，因为它将所有内容运行在 Linux 虚拟机内部，你将无法访问 Linux 命令。

某些示例解释了网络在集群（swarm）上如何工作。只有在你运行 Swarm 集群时才能跟随这些示例。

### Docker 网络 – 简要概述 (TLDR)

Docker 运行由许多容器组成的微服务应用，这些容器共同工作形成整个应用。这些容器需要能够通信，并且某些必须连接到外部服务，例如物理服务器、虚拟机或其他设备。

幸运的是，Docker 为这两个需求都提供了解决方案。

Docker 网络基于 libnetwork，libnetwork 是一个名为容器网络模型（CNM）的开源架构的参考实现。

为了提供开箱即用的体验，Docker 配备了满足最常见网络需求的所有内容，包括多主机容器间网络以及连接到现有 VLAN 的选项。然而，该模型是可插的，生态系统可以通过接入 libnetwork 的驱动程序来扩展 Docker 的网络能力。

最后但同样重要的是，libnetwork 还提供了原生的服务发现和基础负载均衡。

这就是大局。让我们进入细节部分。

### Docker 网络理论

在最高层上，Docker 网络基于以下三个组件：

- 容器网络模型 (CNM)
- Libnetwork
- 驱动程序 (Drivers)

CNM 是设计规范，概述了 Docker 网络的基础构建块。

Libnetwork 是 CNM 的真实实现。它作为 Moby 项目的一部分开源，并被 Docker 及其他平台使用。

驱动程序通过实现特定的网络拓扑（如 VXLAN 叠加网络）来扩展该模型。

图 13.1 显示了这三者。

![](img/aae0230bf8529bd80767c4c780dca8d3_338_0.png)

图 13.1

让我们仔细观察每一个。

#### 容器网络模型 (CNM)

一切都始于设计。

Docker 网络的设计指南是 CNM，它概述了 Docker 网络的基础构建块。

我建议你阅读[规范文档]，但从高层次来说，它定义了三个构建块：

- 沙箱 (Sandboxes)
- 端点 (Endpoints)
- 网络 (Networks)

沙箱是容器内部的隔离网络栈。它包含了以太网接口、端口、路由表、DNS 配置以及你对网络栈所期待的所有切。

端点是虚拟网络接口，看起来、用起来、感觉就像普通的网络接口。它们将沙箱连接到网络。

网络是虚拟交换机（通常是 802.1d 桥的软件实现）。因此，它们将需要通信的一个多个端点分组并隔离。

图 13.2 显示了这三者如何连接并与熟悉的设施组件。使用 CNM 术语，端点将沙箱连接到网络。你创建的每个容器将有一个沙箱，并至少有一个端点将其连接到网络。

![](img/aae0230bf8529bd80767c4c780dca8d3_340_0.png)

正如名称所示，容器网络模型的核心是为容器提供网络支持。图 13.3 显示了 CNM 组件与容器的关系——每个容器都有自己的沙箱，该沙箱托管容器的整个网络栈，包括一个或多个作为以太网接口并可以连接到网络的端点。

![](img/aae0230bf8529bd80767c4c780dca8d3_341_0.png)

图 13.3

容器 A 只有一个接口（端点）且只连接到网络 A。然而，容器 B 有两个接口分别连接到网络 A 和网络 B。这些容器可以相互通信，因为它们都连接到了网络 A。但是，容器 B 内部的两个端点无法相互通信，因为它们在不同的网络上。

理解端点的行为完全像普通的网络适配器也很重要，这意味着你只能将它们连接到单个网络。这就是为什么容器 B 如果想连接到两个网络，就需要两个端点。

图 13.4 通过添加 Docker 宿主机进一步扩展了图表。尽管两个容器都运行在同一宿主机上，但它们的网络栈是完全隔离的，并且只能通过网络进行通信。

![](img/aae0230bf8529bd80767c4c780dca8d3_342_0.png)

图 13.4

#### Libnetwork

Libnetwork 是 CNM 的参考实现。它是开源的、跨平台的（Linux 和 Windows），由 Moby 项目维护并被 Docker 使用。

在 Docker 创建 libnetwork 之前，它在守护进程内部实现了所有的网络代码。然而，随着时间的推移，守护进程变得越来越臃肿，且难以供其他项目使用。因此，Docker 从守护进程中移除了网络代码，并基于 CNM 设计将其重构为一个名为 libnetwork 的外部库。今天，Docker 在 libnetwork 中实现了所有的核心网络功能。

除了实现 CNM 的核心组件外，libnetwork 还实现了网络控制面，包括管理 API、服务发现和基于入口的容器负载均衡。

#### 驱动程序 (Drivers)

libnetwork 实现了控制面，但它依赖驱动程序来实现数据面。例如，驱动程序负责创建网络并确保隔离性和连通性。

Docker 自带了几个驱动程序，我们有时称它们为原生驱动或本地驱动。这些包括 `bridge`、`overlay` 和 `macvlan`，它们构建了最常见的网络拓扑。第三方也可以编写网络驱动程序来实现其他网络拓扑和更高级配置。

图 13.5 显示了 libnetwork 和驱动程序的作用，以及它们与控制面和数据面职责的关系。

![](img/aae0230bf8529bd80767c4c780dca8d3_344_0.png)

你创建的每个网络由一个驱动程序所有，该驱动程序创建并管理有关网络的一切。例如，如果你创建一个名为 prod-fe-cuda 的叠加网络，Docker 将调用 overlay 驱动来创建该网络及其资源。

为了满足复杂、流动环境的需求，单个 Docker 宿主机或 Swarm 集群可以拥有由不同驱动程序管理的异构网络。

让我们来看看单主机桥接网络以及连接到现有网络。你将在下一章中学习叠加网络。

### 单主机桥接网络

最简单的 Docker 网络类型是单主机桥接网络。

该名称告诉了我们两点：

- **Single-host（单主机）** 告诉我们该网络仅跨越单个 Docker 节点
- **Bridge（桥接）** 告诉我们它是 802.1d 桥接器（二层交换机）的实现

Docker 使用内置的桥接驱动创建单主机桥接网络。如果你运行 Windows 容器，你将需要使用 nat 驱动，但从本质上来说，它们的工作是相同的。

图 13.6 显示了两个具有相同本地桥接网络的 Docker 节点，它们都被命名为 **mynet**。尽管网络是相同的，但它们是独立且隔离的，这意味着图片中的容器无法通信，即使节点属于同一个集群（swarm）。

![](img/aae0230bf8529bd80767c4c780dca8d3_346_0.png)

### 图 13.6

每个新的 Docker 节点都会获得一个名为 **bridge** 的默认单主机桥接网络，除非你使用 `--network` 标志对其进行覆盖，否则 Docker 会将新容器连接到。

以下命令显示了在 Docker 安装上运行 `docker network ls` 命令的输出。

```
$ docker network ls

| NETWORK ID | NAME | DRIVER | SCOPE |

| :--- | :--- | :--- | :--- |

| c7464dce29ce | bridge | bridge | local default |

| c65ab180d580 | host | host | local |

| 42a783df0fbe | none | null | local |
```

一如既往，你可以运行 `docker inspect` 命令来获取更多信息。我强烈建议在你自己的系统上运行该命令并研究输出。

```
$ docker network inspect bridge

[
  {
    "Name": "bridge",
    "Id": "c7464dce2...ba2e3b8",
    "Scope": "local",
    "Driver": "bridge",
    "EnableIPv6": false,
    "IPAM": {
      "Driver": "default",
      "Options": null,
      "Config": [
        {
          "Subnet": "172.17.0.0/16",
          "Gateway": "172.17.0.1"
        }
      ]
    },
    "Internal": false,
    "Attachable": false,
    "Ingress": false,
    "ConfigFrom": {
      "Network": ""
    },
    <Snip>
  }
]
```

所有的桥接网络都基于经过长期验证的 Linux 桥接技术，该技术在 Linux 内核中已存在 20 多年。这意味着它们是高性能且高度稳定的。这也意味着你可以使用标准的 Linux 工具对其进行检查。

所有基于 Linux 的 Docker 节点上的默认桥接网络都称为 bridge，并映射到主机内核中名为 docker0 的底层 Linux 桥接器。如图 13.7 所示。

![](img/aae0230bf8529bd80767c4c780dca8d3_348_0.png)

**图 13.7 - 将默认 Docker "bridge" 网络映射到主机内核中的 "docker0" 桥接器**

你可以运行 `docker network inspect` 命令来确认桥接网络是否基于主机内核中的 docker0。如果你在 Windows 上使用 PowerShell，你将需要 grep 替换为 Select-String。

```
$ docker network inspect bridge | grep bridge.name
"com.docker.network.bridge.name": "docker0",
```

现在运行这些 Linux 命令从 Linux 主机检查 docker 0 桥接器。你可能需要手动安装 brctl 工具。

```
$ brctl show
bridge name     bridge id STP enabled interfaces
docker0         8000.0242aff9eb4f no
docker_gwbridge 8000.02427abba76b no
$ ip link show docker0
3: docker0:<BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc...\link/ether 02:42:af:f9:eb:4f brd ff:ff:ff:ff
```

第一条命令列出了你主机上所有的桥接器，并显示它们是否连接了任何设备。书中的示例显示了没有任何设备的 docker0 桥接器。第二条命令显示了 docker0 桥接器的配置和状态。图 13.8 显示了容器连接到桥接网络的完整栈，该网络随后映射到主机内核中的 docker0 桥接器。它还显示了你如何使用端口映射在接口上发布设备。

![](img/aae0230bf8529bd80767c4c780dca8d3_350_0.png)

在接下来的几步中，你将完成所有操作：
1. 创建一个新的桥接网络
2. 将容器连接到新网络
3. 检查新网络
4. 测试基于名称的

运行以下命令创建一个名为 `localnet` 的新单主机网络。

```
$ docker network create -d localnet
f918f1bb02373bf94615d99cb2bef14ede935f28e4b86
```

命令返回的长数字是网络的 ID，你将在下一步中需要它。如所预期，该命令创建了一个名为 localnet 的新桥接网络，你可以用通常的 docker 命令对其进行列出和检查。然而，在后台，它还在主机内核中创建了一个新的 Linux 桥接器。运行另一个 brctl show 命令查看它。

| brctl show | bridge name | bridge id | STP enabled | interface |
| :--- | :--- | :--- | :--- | :--- |
| br-f918f1bb0602 | 8000.0242372a886b | no | |
| docker0 | 8000.02425ee84bc | no | |
| docker_gwbridge | 8000.02427abba76b | no | |

书中的示例显示了一个名为 f918f1bb02 且没有任何设备的桥接器。如果你仔细观察该名称，你会识别出它是你创建的新的 localnet 网络 ID 的前 12 个字符。此时，主机上的桥接器配置看起来如图 13.9 所示。

图 13.9

让我们创建一个名为 c1 的容器并将其连接到 localnet 网络。你可能需要安装 jq 工具。

一旦你创建了容器，检查 localnet 以验证它是否连接到内核中的桥接器。

```bash
$ docker run -d --name c1
  --network localnet
  sleep infinity
```

Docker 宿主机上的端口。它有点笨拙并且有很多局限性，但对于偶尔的测试和开发工作可能有用。

图 13.11 显示了运行两个容器的单个 Docker 宿主机。右侧的 web 容器在端口 80 上运行 Web 服务器，映射到 Docker 宿主机的端口 5005。左侧的 client 容器向 Docker 宿主机端口 5005 发送请求，外部客户端也这样做。两个请求都将命中宿主机端口 5005，并重定向到运行在 web 容器中的 Web 服务器。

![](img/aae0230bf8529bd80767c4c780dca8d3_356_0.png)

图 13.11

让我们测试一下设置，看看它是否有效。

创建一个名为 `web` 的新容器，在端口 80 上运行 NGINX，并将其映射到 Docker 宿主机的端口 5005。如果你仍然登录在上一个示例的容器中，需要先输入 `exit`。

```
$ docker run -d --name web \
--network localnet \
--publish 5005:80 \
nginx
```

验证端口映射。

```
$ docker port web
80/tcp -> 0.0.0.0:5005
80/tcp -> [::]:5005
```

输出显示 Docker 宿主机上的所有接口都存在端口映射。

你可以通过将 Web 浏览器指向 Docker 宿主机端口 5005 来测试外部访问。你需要知道 Docker 宿主机的 IP 或 DNS 名称（如果你是在 Multipass 上跟着操作，它可能可能是你的 Multipass 虚拟机的 192.168.x.x 地址）。你将看到 “Welcome to nginx!” 页面。

让我们创建另一个容器，看看它是否能通过端口映射到达 web 容器。

运行以下命令在 **bridge** 网络上创建一个名为 **client** 的新容器。

```bash
$ docker run -it --name client --network bridge alpine sh
```

该命令将你带入容器，你的提示符会发生变化。

安装 **curl** 工具。

```bash
### apk add curl
fetch https://dl-cdn.alpinelinux.org/alpine/v3.19/main/aarch64
fetch https://dl-cdn.alpinelinux.org/alpine/v3.19/community/aarch6
(1/8) Installing ca-certificates (20240226-r0)
<Snip>
```

现在连接到 Docker 宿主机端口 **5005** 的 IP，看看是否可以到达容器。

```bash
