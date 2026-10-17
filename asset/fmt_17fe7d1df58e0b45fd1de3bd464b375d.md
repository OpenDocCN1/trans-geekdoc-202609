
示例使用了 `--pretty` 标志将输出限制为易读的格式。如果你去掉 `--pretty` 标志，将通过 `docker inspect` 命令的输出获取更多关于底层运行的信息。

我们将稍后回来看这些输出。

Swarm 部署副本有两种两种模式：

- Replicated（副本）
- Global（全局）

默认的 `replicated` 模式允许你部署所需数量的副本，并尝试均匀分布在可用节点上。

`global` 模式在每个可用节点上部署单个副本。两种模式都尊重可用性并仅在符合条件的节点上部署。例如，如果你不允许集群在管理器上部署应用程序，两种模式都只会在工作节点上部署。如果你想部署全局服务，需要在 `service create` 命令中传递 `--mode global` 标志。显然，它不支持 `--replicas` 标志，因为它在每个节点部署一个副本。

### 扩展服务

服务的另一个强大功能是通过添加或删除副本来伸缩它们。

假设业务兴隆，你的前端收到的请求数翻倍。幸运的是，你可以使用 `docker scale` 命令轻松扩展副本数量。

运行以下命令将 `web-fe` 服务从 5 个副本扩展到 10 个。

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

在后台，命令更新了集群存储中 `web-fe` 服务的期望状态从 5 个副本变为 10 个。协调循环读取了 10 个副本的新期望状态，将其与当前 5 个副本的观测状态进行比较，并增加了 5 个以使观测状态与新的期望状态同步。

再次运行 `docker service ls` 以验证操作成功完成。

如果有十个工作节点，你可能在每个工作节点上运行一个副本。

| ID | NAME | IMAGE | NODE | DESIRED | CURRENT |
|---|---|---|---|---|---|
| nwf...tpn | web-fe.1 | nigelpton/ddd-book:web0.1 | wrk1 | | 中 |
| yb0...e3e | web-fe.2 | nigelpton/ddd-book:web0.1 | wrk2 | | 中 |
| mos...g6f | web-fe.3 | nigelpton/ddd-book:web0.1 | wrk2 | | 中 |
| utn...6ak | web-fe.4 | nigelpton/ddd-book:web0.1 | wrk1 | | 中 |
| 2ge...fyy | web-fe.5 | nigelpton/ddd-book:web0.1 | wrk2 | | 中 |
| 64y...m49 | web-fe.6 | nigelpton/ddd-book:web0.1 | wrk2 | | 中 |
|  ild...51s | web-fe.7 | nigelpton/ddd-book:web0.1 | wrk1 | | 中 |
| vah...rjf | web-fe.8 | nigelpton/ddd-book:web0.1 | wrk1 | | 中 |
| xe7...fvu | web-fe.9 | nigelpton/ddd-book:web0.1 | wrk2 | | 中 |
| l7k...jkv | web-fe.10 | nigelpton/ddd-book:web0.1 | wrk1 | | 中 |

在后台，Swarm 运行一种名为 `spread` 的调度算法，该算法尝试尽可能均匀地平衡副本在可用节点上。

运行另一个 `docker service scale` 命令将副本数量调回 5。

```
$ docker service scale web-fe=5

web-fe scaled to 5

overall progress: 5 of 5 tasks

1/5: running [========================================]

2/5: running [========================================]

3/5: running [========================================]

4/5: running [========================================]

5/5: running [========================================]
```

```
5/5: running [============================================]

verify: Service web-fe converged
```

现在你已经知道如何伸缩服务了，让我们来看看如何删除它们。

### 删除服务 (Deleting services)

删除服务非常简单——可能太简单了。

运行以下命令来删除 `web-fe` 服务。使用此命令时要小心，因为它不会请求确认。

```
$ docker service rm web-fe

web-fe
```

确认它已经消失了。

| docker service ls |
| ID | NAME | MODE | REPLICAS | IMAGE | PORTS |

让我们来看看如何执行滚动更新（rollout）。

### 滚动发布更新 (Rollouts)

应用更新是生活常态，在很长一段时间里，这种更新是非常痛苦的。我个人为了重大的应用更新浪费了足够的周末，我不想再经历一次了。

幸运的是，由于有了 Docker 服务，更新设计良好的微服务应用变得简单。

**术语：** 我们使用 `rollouts`（发布）、`updates`（更新）和 `rolling updates`（滚动更新）来表示相同的意思——更新正在运行的应用程序。

你即将部署一个新服务来演示滚动更新。但在之前，你将为该服务创建一个新的覆盖网络（overlay network）。这并不是必须，但我想让你看到如何将服务连接到网络。

运行以下两个命令创建一个名为 `uber-net` 的新覆盖网络，然后检查它是否存在。

```
$ docker network create -d overlay uber-net

43wp6pzea470et4d57udn9ws
```

```
$ docker network ls

| NETWORK ID | NAME | DRIVER | SCOPE |

| 43wp6pzea47 | uber-net | overlay | swarm |

| <Snip> | | | |
```

新网络已存在，并已成功创建为作用于整个 swarm 的覆盖网络。你将在稍后的章节中学习覆盖网络，但目前只需要知道它们跨越所有 swarm 节点，并且位于同一个覆盖网络中的所有容器都可以通信，即使它们被部署在不同的节点上。

图 10.5 显示了四个 swarm 节点通过一个三层网络连接到两个底层网络。覆盖网络跨越所有四个节点，并创建一个单一的扁平二层 网络，抽象化了底层网络。所有的容器副本都连接到覆盖网络并可以相互通信。（img/ae0230bf8529bd8076c4c780dca8d3_277_0.png）图 10.5

让我们创建一个新服务并将其连接到 `uber-net` 网络。

```
$ docker service create --name uber-svc \
  --network uber-net \
  -p 8080:8080 --replicas 12 \
  nigelpton/ddd-book:web0.0
```

```
overall progress: 12 of 12 tasks

1/12: running [====================================]

2/12: running [====================================]

3/12: running [====================================]

<Snip>

12/12: running [====================================]

verify: Service converged
```

让我们逐步分析发生了什么。在第一行中，你将服务命名为 `uber-svc`。然后你使用 `--network` 标志，告诉 Docker 将所有服务副本连接到新的 `uber-net`。接着，你将每个 swarm 节点上的 8080 端口映射到 12 个副本的 8080 端口。最后，你告诉 Docker 使用哪个镜像来创建副本。这种在每个 swarm 节点（包括未运行副本的节点）上发布服务的模式被称为 `ingress mode`（接入模式），它是默认设置。另一种方案是 `host mode`（主机模式），它只在运行副本的节点上发布服务。

运行 `docker service ls` 和 `docker service ps` 来验证服务以及每个副本的状态。

| ID | NAME | REPLICAS | IMAGE | NODE | DESIRED | CURRENT |
|---|---|---|---|---|---|
| ...7e5 | uber-svc | 12/12 | nigelpton/ddd-book:web0.1 | wrk1 | | Running |
| ...wa0 | uber-svc | 12/12 | nigelpton/ddd-book:web0.1 | wrk2 | | Running |
| ...u97 | uber-svc | 12/12 | nigelpton/ddd-book:web0.1 | | |

（此处省略重复的表格内容）

版本，某些部分将响应新版本。经过足够的时间后，所有请求都将获取到新版本。

恭喜。你刚刚完成了一个对运行中的容器化应用程序的零停机滚动更新。

如果你对该服务运行 `docker service inspect --pretty` 命令，你会看到 `update parallelism`（更新并行性）和 `update delay`（更新延迟）设置已合并到服务的定义中。这意味着未来的更新将自动使用这些设置，除非你在更新命令中对它们进行了重写。

```
$ docker service inspect --pretty uber-svc

ID: mub0dgdtc8szm8ez5bs8wlt19

Name: uber-svc

Service Mode: Replicated

Replicas: 12

<Snap>

UpdateConfig:

Parallelism: 2 <<-----

Delay: 20s <<-----

</Snap>
```

### 服务日志

你可以使用 `docker service logs` 命令检查服务的日志。它会收集来自每个副本的日志并将它们显示在单个输出中。

如果你一直在跟着操作，你现在应该有一个名为 `uber-svc` 的服务，它具有 12 个副本，并映射到每个集群节点上的 `8080` 端口。打开浏览器标签页，访问任意集群节点 `8080` 端口的 IP 地址并刷新几次。

现在运行 `docker service logs` 命令来查看服务生成的任何日志消息。

```
docker service logs uber-svc

uber-svc.8.r33cra80eeut@wrk1

uber-svc.2.vid8752oj48@wrk1

uber-svc.7.jv67x3zfkyar@wrk2

uber-svc.1.zlmvo5k156@wrk2

uber-svc.3.kleeiyovue5@wrk2  | {"level":"info","message":"/"}

| {"level":"info","message":"/"}

| {"level":"info","message":"/"}

| {"level":"info","message":"/"}

| {"level":"info","message":"/"}
```

输出显示了五行，与五个不同副本服务的五个请求相关。每行左侧的长字符串是副本的名称，Docker 通过拼接服务名称、副本数量、副本 ID 以及其调度的节点名称来创建它。下表映射了请求服务的五个副本名称。

| 服务名称 | 副本数量 | 副本 ID | 节点 |
|---|---|---|---|
| uber-svc | 8 | r33cra80eeut | @wrk1 |
| uber-svc | 2 | vid8752oj48 | @wrk1 |
| uber-svc | 7 | jv67x3zfkyar | @wrk2 |
| uber-svc | 1 | zlmvvo5k156 | @wrk2 |
| uber-svc | 3 | kleeiy0vuue5 | @wrk2 |

注意 Swarm 如何在五个不同的副本之间平衡请求。在现实世界，由于浏览器和不同工具创建及处理请求的方式，你的请求可能不会这样平衡。然而，如果你刷新足够多次，最终会看到请求由不同的副本处理。

默认情况下，Docker 配置服务使用 `json-file log driver`，但存在其他驱动程序，包括：

- awlogs
- gelf
- journald（仅适用于运行 systemd 的 Linux 宿主机）
- splunk
- syslog

`json-file` 和 `journald` 是容易配置的，且它们都与 `docker service logs` 命令配合。然而，其他驱动程序并不总是与 Docker 原生命令兼容，你可能需要使用日志平台的原生工具。

以下片段来自配置为使用 `syslog` 驱动程序的 Docker 宿主机上的 `daemon.json` 文件。`daemon.json` 文件通常位于 `/etc/docker/daemon.json`，但除非你手动为自定义设置创建，否则它有时不存在。

```
{
  "log-driver": "syslog"
}
```
