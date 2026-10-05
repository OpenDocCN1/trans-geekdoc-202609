
Docker 将重新把节点加入集群，在后续命令中，它将显示为 **ready**（就绪）和 **reachable**（可访问）。

你应该锁定你的生产集群并保护好解锁密钥。

## 专用管理器节点

默认情况下，Swarm 在工作节点（workers）**和**管理器（managers）上运行用户应用程序。但是，你可能希望配置你的生产集群仅在工作节点上运行用户应用程序。这允许管理器专门负责控制平面的职责。

在任何管理器节点上运行以下命令以防止其运行用户应用程序。你需要使用管理节点的名称，如果你想强制用户应用程序仅运行在工作节点上，则需要在所有管理器节点上运行该命令。

```
$ docker node update --availability drain mgr1
```

你将在之后部署具有多个副本的服务时看到此操作产生的影响。

现在你已经构建了集群并理解了**领导者**（leaders）和**管理器**（manager）高可用的概念，让我们转向应用端。

## 在集群上部署和管理应用

Swarm 节点可以运行普通容器，也可以运行名为 *services*（服务）的增强容器。每个 *service* 接收单个容器定义，并为其增强云原生功能，如自愈、扩展以及自动滚动和回滚。

在本节中，你将部署一个简单的 Web 服务器作为 *swarm service*，并查看如何扩展、滚动和删除它。

Swarm 允许通过两种方式创建和管理服务：

1. 命令式（Imperatively）通过命令行
2. 声明式（Declaratively）通过 Compose 文件

我们将在下一节介绍 Compose 文件。现在我们将关注命令式方法。

运行以下命令部署一个名为 **web-fe** 的新服务，并带有五个相同的副本。

```
$ docker service create --name web-fe \
-p 8080:8080 \
--replicas 5 \
nigelpoulton/ddd-book:web0.1
```

```
z7oveargqmru0u2vc5o7ql0p
overall progress: 5 out 5 tasks
1/5: running [================================]
2/5: running [============================]
3/5: running [============================]
4/5: running [============================]
5/5: running [============================]
verify: Service converged
```

`docker service create` 命令告诉 Docker 部署一个新的服务。`--name` 标志将其称为 web-fe，`-p` 标志将每个节点的 8080 端口映射到每个副本（容器）内部的 8080 端口，`--replicas` 标志告诉 Swarm 部署五个副本。

当我们指代服务时，交叉使用 replicas（副本）和 containers（容器）术语。你的 Docker 客户端将命令发送给集群管理器，领导管理器（leader manager）启动了部署五个副本的任务。你配置此集群使得用户应用程序不在管理器上运行，这意味着五个副本将运行在你的工作节点上。每个接收任务的工作节点拉取了镜像，启动了容器并创建了端口映射。

然而，此并未结束。你发布的命令请求具有五个副本的服务，Swarm 将其存储在集群中作为 *desired state*（期望状态）。在后台，Swarm 运行一个 *reconciliation*（协调）循环，不断比较集群的 *observed state*（观测状态）与 *desired state*。当两个状态匹配时，世界一切正常，不需要进一步操作。当它们不匹配时，Swarm 会采取行动使 *observed state* 与 *desired state* 一致。

例如，如果托管五个副本之一的 *worker* 失败，集群的 *observed state* 将从 5 个副本变为 4 个，不再匹配 5 个的 *desired state*。一旦集群发现差异，它将启动一个新的副本将 *observed state* 回到 *desired state*。我们称之为 *reconciliation*（协调）或 *self-healing*（自愈），它是云原生应用的核心原则。

你很快就会学会期望状态和协调也是扩展、滚动和回滚的核心。

## 查看和检查服务

运行 `docker service ls` 命令查看集群上所有的服务。

| ID | NAME | MODE | REPLICAS | IMAGE |
|---|---|---|---|---|
| z7o...uw | web-fe | replicated | 5/5 | ... |

输出显示了一个基本配置和状态信息。此外，你可以看到服务的名称以及五个副本都在运行。如果你在部署服务后过早运行命令，某些副本可能不在运行状态。这通常是因为工作节点仍在拉取镜像并启动副本。

你可以运行 `docker service ps` 命令查看服务副本列表及其每个副本的状态。

| ID | NAME | IMAGE | NODE | DES |
|---|---|---|---|---|
| 817...f6z | web-fe.1 | nigelpoulton/ddd-book:web0.1 | wrk1 | Run |
| ald...mzn | web-fe.2 | nigelpoulton/ddd-book:web0.1 | wrk1 | Run |
| cc0...ar0 | web-fe.3 | nigelpoulton/ddd-book:web0.1 | wrk2 | Run |
| 6f0...azu | web-fe.4 | nigelpoulton/ddd-book:web0.1 | wrk1 | Run |
| dyl...p3e | web-fe.5 | nigelpoulton/ddd-book:web0.1 | wrk2 | Run |

输出单独成行显示每个副本，包括它运行的节点以及每个副本的期望状态和当前观测状态。如预期的那样，你有五个副本分布在你所有的工作节点上。

如果你需要服务的详细信息，可以运行 `docker service inspect` 命令。

```
$ docker service inspect --pretty web-fe
ID: z7ovearqmruwk0u2vc5o7ql0p
Name: web-fe
Service Mode: Replicated
Replicas: 5
Placement:
UpdateConfig:
Parallelism: 1
On failure: pause
Monitoring Period: 5s
Max failure ratio: 0
Update order: stop-first
RollbackConfig:
Parallelism: 1
On failure: pause
Monitoring Period: 5s
Max failure ratio: 0
Rollback order: stop-first
ContainerSpec:
Image: nigelpoulton/ddd-book:web0.1@sha256:8d6280c0042..
Init: false
Resources:
Endpoint Mode: vip
Ports:
PublishedPort = 8080
Protocol = tcp
TargetPort = 8080
PublishMode = ingress
```

示例使用了 `--pretty` 标志将输出限制为易读的格式。如果你去掉 `--pretty` 标志，将通过 `docker inspect` 命令的输出获取更多关于底层运行的信息。

我们将稍后回来看这些输出。

Swarm 部署副本有两种两种模式：

- Replicated（副本）
- Global（全局）

默认的 `replicated` 模式允许你部署所需数量的副本，并尝试均匀分布在可用节点上。

`global` 模式在每个可用节点上部署单个副本。两种模式都尊重可用性并仅在符合条件的节点上部署。例如，如果你不允许集群在管理器上部署应用程序，两种模式都只会在工作节点上部署。如果你想部署全局服务，需要在 `service create` 命令中传递 `--mode global` 标志。显然，它不支持 `--replicas` 标志，因为它在每个节点部署一个副本。

## 扩展服务

服务的另一个强大功能是通过添加或删除副本来伸缩它们。

假设业务兴隆，你的前端收到的请求数翻倍。幸运的是，你可以使用 `docker scale` 命令轻松扩展副本数量。

运行以下命令将 web-fe 服务从 5 个副本扩展到 10 个。

```
$ docker service scale web-fe=10
web-fe scaled to 10
overall progress: 10 out of 10 tasks
1/10: running [================================]
```

```
2/10: running [============================]
3/10: running [============================]
4/10: running [============================]
5/10: running [============================]
6/10: running [============================]
7/10: running [============================]
8/10: running [============================]
9/10: running [============================]
10/10: running [============================]
```

在后台，命令更新了集群存储中 web-fe 服务的期望状态从 5 个副本变为 10 个。协调循环读取了 10 个副本的新期望状态，将其与当前 5 个副本的观测状态进行比较，并增加了 5 个以使观测状态与新的期望状态同步。

再次运行 `docker service ls` 以验证操作成功完成。
