
你可以通过在启动服务时使用 `--log-driver` 和 `--log-opts` 标志强制新服务使用特定的日志驱动程序。这将覆盖 `daemon.json` 文件中的任何设置。

服务日志期望应用程序作为 PID 1 并将日志发送到 STDOUT，错误发送到 STDERR。日志驱动程序会将日志转发到通过日志驱动程序配置的位置。

### Docker Swarm – 命令

- `docker swarm init` 创建一个新的 swarm。你运行命令的节点将成为第一个管理器，该节点上的 Docker Engine 将切换到 swarm 模式。
- `docker swarm join-token` 显示将 workers 和 managers 加入 swarm 所需的命令和令牌。在命令中添加 manager 以获取管理器加入令牌，添加 worker 以获取工作节点令牌。请确保你的加入令牌安全！
- `docker node ls` 列出 managers 和 workers，包括哪个管理器是 leader。
- `docker service create` 创建一个新的服务。
- `docker service ls` 列出正在运行的服务并提供有关其状态和运行副本数量的基本信息。
- `docker service ps <service>` 提供有关单个服务副本的更详细信息。
- `docker service inspect` 提供有关服务的详细信息。
- `docker service scale` 缩放副本数量。
- `docker service update` 更新服务的属性。
- `docker service logs` 显示日志。
- `docker service rm` 删除服务。

Swarm 是 Docker 用于集群的原生技术。它类似于 Kubernetes 但更容易使用。编排组件部署并管理微服务。Swarm 是 Docker 用于集群的原生技术。它类似于 Kubernetes 但更容易使用。编排组件部署并管理微服务。Swarm 是 Docker 用于集群的原生技术。它类似于 Kubernetes 但更容易使用。编排组件部署并管理微服务。Swarm 是 Docker 用于集群的原生技术。它类似于 Kubernetes 但更容易使用。编排组件部署并管理微服务。

### 总结

Docker stacks 结合了 Compose 和 Swarm，创建一个用于部署和管理多容器应用的平台。

我将本章分为：
- 使用 Stacks
- 构建 Swarm 实验
- 示例应用
- 管理应用

### 使用 Stacks

部署和管理云原生应用是困难的。幸运的是，Stacks 提供了帮助。从架构角度来看，stacks 位于顶层——它们构建在服务之上。 构建 Swarm 实验

本节向你展示如何构建一个包含一个管理器两个工作节点的三节点 swarm。你可以在 Multipass、Play with Docker 或几乎任何环境中构建实验。然而，我不建议使用 Docker Desktop，因为你只有一个 swarm 节点。

在将作为管理器的节点上运行以下命令：

```
$ docker swarm init

Swarm initialized: current node (lhma...w4nn) is now a manager.

<Snap>
```

复制显示的 `docker swarm join` 命令并将其粘贴到你想作为 worker 的节点中。

#### 工作节点 1

```
$ docker swarm join --token SWMTKN-1-2hl6....31lgq 172.31.40.19

This node joined a swarm as a worker.
```

#### 工作节点 2

```
$ docker swarm join --token SWMTKN-1-2hl6....31lgq 172.31.40.19

This node joined a swarm as a worker.
```

从你的管理器节点运行以下命令，以确认 swarm 已初始化包含一个管理器两个工作节点。

| ID | HOSTNAME | STATUS | AVAILABILITY | MANAGER STATUS |
| --- | --- | --- | --- | --- |
| lhm...4nn | mgr1 | Ready | Active | Leader |
| b74...gz3 | wrk1 | Ready | Active | |
| 09x...um8 | wrk2 | Ready | Active | |

现在你已经有了 swarm 实验，让我们看看示例应用。

## 示例应用

图 11.2 显示了本章剩余部分使用的应用程序。这是一个多容器微服务应用，包含：

- 两个服务 (`web-fe` `redis`)
- 一个加密的覆盖网络 (`counter-net`)
- 一个卷 (`counter-vol`)
- 一个发布的端口 (` 5001`)

### 图 11.2

**术语：** 在本章中我们将我们将“服务”（service）一词来指代在集群（swarm）上管理一个或多个相同容器的 Docker 服务对象。我们还将 Compose 文件称为“栈文件”（stack file），有时会将应用程序称为“栈”（stack）。

如果你还没有执行此操作，请登录 swarm 管理器并克隆本书的 GitHub 仓库。

```
$ git clone https://github.com/nigelpoulton/ddd-book.git

Cloning into 'ddd-book'...

remote: Enumerating objects: 8904, done.

remote: Counting objects: 100% (74/74), done.

remote: Compressing objects: 100% (52/52), done.

remote: Total 8904 (delta 21), reused 70 (delta 18), pack-used

Receiving objects: 100% (8904/8904), 74.00 MiB | 4.18 MiB/s, done

Resolving deltas: 100% (1378/1378), done.
```

进入 `ddd-book/swarm-app` 文件夹。

```
$ cd ddd-book/swarm-app
```

可以随意查看 `app` 子文件夹中的应用程序，但我们将关注 `compose.yaml` 文件。

如果你查看 Compose 文件，你会发现它有三个顶层键。

- networks
- volumes
- services

**Networks**（网络）是你定义应用程序所需的网络，**volumes**（卷）定义了所需的卷，而 **services**（服务）定义了构成应用程序的微服务。该文件是*基础设施即代码*（infrastructure as code）简单示例——应用程序和基础设施定义在一个配置文件中，你从该文件中进行部署和管理。

如果你展开每个顶层键，你会看到它们是如何映射到图 11.2 的，其中包含名为 `counter-net` 的网络，一个名为 `counter-vol` 的卷，以及两个名为 `web-fe` 和 `redis` 的服务。

```yaml
networks:
  counter-net:
volumes:
  counter-vol:
services:
  web-fe:
  redis:
```

让我们来看栈文件的每个部分。

### 深入研究栈文件

栈文件与 Compose 文件相同，但在运行时有几处不同。例如，Docker Compose 允许你在运行时构建镜像，但 Docker Stacks 不行。

让我们看看栈文件中定义的网络元素。

## 网络与网络化

当你从栈文件部署应用程序时，Docker 执行的第一件事之一就是创建 `networks` 键下列出的网络。如果它们已经存在，Docker 不需要做任何操作。但如果它们不存在，它就会创建它们。

此应用程序定义了一个名为 `counter-net` 的单一加密覆盖网络。

```yaml
networks:
  counter-net:      <---- 网络名称
    driver: overlay   <---- 网络驱动程序/类型
    driver_opts:
      encrypted: 'yes' <---- 加密数据面
```

它必须是一个覆盖网络（overlay network），以便跨越集群中的所有节点。

加密数据面将保持应用程序流量的私密性，但会带来性能损失，这种损失取决于流量类型和流量流等因素。性能损失在 10% 左右并不罕见，但你应该针对自己的应用程序进行自己的测试。

栈还将 web-fe 服务发布在集群范围入口网络的 5001 端口上，并将其映射回所有服务副本的 8080 端口。这允许外部客户端通过访问端口 5001 的任意 swarm 节点来访问服务。

```yaml
services:
  web-fe:
<Snip>
    ports:
      target: 8080      <-- 服务副本在此监听
      published: 5001   <-- 外部发布到
```

让我们来看卷和挂载。

## 卷与挂载

应用程序定义了一个名为 counter-vol 的单一卷，并将其挂载到所有 web-fe 副本的 `/app` 目录。这意味着对 `/app` 文件夹的所有读写操作都将在卷中进行。

```yaml
volumes:
  counter-vol: <<----- 卷名称
services:
  web-fe:
    <Snip
    volumes:
      - type: volume
        source: counter-vol <----- 挂载 "counter-vol" 卷
        target: /app <----- 所有服务副本中的 "/app"
```

让我们来看服务。

### 服务

大多数操作发生在服务处。我们的应用程序定义了两个，我们将逐一查看它们。

#### web-fe 服务

如你所见，web-fe 服务定义了镜像、应用程序、期望的副本数量、更新应用程序的规则、重启策略、连接的网络、要发布的端口以及如何挂载卷。这些内容很多需要吸收，所以我已经在书中对其进行了注释。花点时间阅读一遍文件和注释。

```yaml
web-fe:
  image: nigelppoulton/ddd-book:swarm-app <<----- 创建所有副本
```

```yaml
command: python app.py
deploy:
  replicas: 4
  update_config:
    parallelism: 2
    delay: 10s
    failure_action: rollback
  placement:
    constraints:
      - 'node.role == worker'
  restart_policy:
    condition: on-failure
    max_attempts: 3
    delay: 5s
    window: 120s
networks:
  - counter-net
ports:
  published: 5001
  target: 8080
volumes:
  - type: volume
    source: counter-vol
    target: /app
```

最后，`volumes` 块将 `counter-vol` 卷挂载到每个服务副本的 `/app` 目录。

```yaml
web-fe:
  volumes:
    type: volume
    source: counter-vol
    target: /app
```

#### redis 服务

`redis` 服务要简单得多。它拉取 `redis:alpine` 镜像，启动单个副本，并将其附加到 `counter-net` 网络。这与 `web-fe` 服务使用的是同一个网络，这意味着这两个服务能够通过名称（“redis”和“web-fe”）进行相互通信。

```yaml
redis:
  image: "redis:alpine"
networks:
  counter-net:
```

如前提到的，Compose 文件是应用程序文档的极佳来源。我们可以阅读这个文件并知道应用程序包含两个服务、两个网络和一个卷。我们知道服务是如何通信的、它们如何在集群（swarm）之外发布，以及关于它们将如何部署、更新和从故障中重启的某些信息。

让我们来部署并管理这个应用吧。

#### 部署应用程序

如果你计划遵循本节，你需要书籍的 GitHub 仓库副本和一个集群。示例使用一个三节点集群，其中包含一个名为 `mgr1` 的管理器和两个名为 `wrk1` 和 `wrk2` 的工作节点。

### 部署应用

你使用 `docker stack deploy` 命令来部署栈（Stacks），在其基本形式下，它接受两个参数：

- 栈文件名（Compose 文件）
- 栈名称（app）

我们将使用 `ddd-book/swarm-app` 文件夹中的 `compose.yaml` 文件，并将应用命名为 `ddd`。

在集群管理器的 `swarm-app` 目录下运行所有命令。

部署栈。

```bash
$ docker stack deploy -c compose.yaml ddd

Creating network ddd_counter-net

Creating service ddd_web-fe

Creating service ddd_web-redis
```

从输出结果中有几点需要注意。

Docker 会在创建服务之前创建网络和卷。这是因为服务消耗网络和卷，如果它们不存在，服务将启动失败。

Docker 还会在每个资源的名称前加上栈的前缀。我们将栈命名为 ddd，这意味着 Docker 将为每个资源名称加上 ddd: 前缀：

- ddd_counter-net
- ddd_counter-vol
- ddd_web-fe
- ddd_redis

你可以使用常规命令检查服务、卷和网络的状态，但 `docker stack` 命令也提供了几个选项来检查栈的状态：

- `docker stack ls` 列出运行中的栈列表以及它们包含的服务数量
- `docker stack ps <stack-name>` 提供关于特定栈及其副本的更详细信息

让我们来看下这两个命令。

```bash
$ docker stack ls

NAME SERVICES

ddd 2

$ docker stack ps ddd

NAME IMAGE NODE DESIRED S

ddd_redis.1 redis:alpine mgr1 Running

ddd_web-fe.1 nigelppton/ddd-book:swarm-app wrk1 Running

ddd_web-fe.2 nigelppton/ddd-book:swarm-app wrk2 Running

ddd_web-fe.3 nigelppton/ddd-book:swarm-app wrk2 Running

<Snip>

ddd_web-fe.10 nigelppton/ddd-book:swarm-app wrk1 Running
```

`docker stack ps` 命令非常排查服务故障非常有用。你可以看到副本基于哪个镜像、副本运行在哪些节点上，以及期望状态和当前状态。

以下输出显示了在 wrk2 节点上启动 web-fe 副本的两次失败尝试。

```bash
$ docker stack ps ddd

NAME NODE DESIRED CURRENT ERROR
```

你也可以使用 `docker service logs` 命令来检查服务日志。如果你传递服务名称或 ID，你将获得所有服务副本的日志。如果你传递特定的副本名称或 ID，你将只获得该副本的日志。

接下来的示例显示了 `ddd_web-fe` 服务中所有副本的日志。

| 命令 | 输出 |
| :--- | :--- |
| docker service logs ddd_web-fe | ddd_web-fe.9.i23pu71kq12@node2 ddd_web-fe.5.z4otpnjrvc58@node2 <Snip> \| * Serving Flask app 'app' \| ddd_web-fe.6.novrixi5iuxy@node2 ddd_web-fe.6.novrixi5iuxy@node2 ddd_web-fe.6.novrixi5iuxy@node2 | * Debug mode: on * Debugger is active! * Debugger PIN: 127-233-15 |

你可以跟踪日志（`--follow`）、查看尾部日志，并且有时可以获取额外细节（--details**）。

到目前为止，你已经使用 Docker 命令证明了栈已启动运行。然而，你也可以用浏览器进行测试。

运行 `docker stack services` 命令来发现 `web-fe` 服务发布的端口。

| NAME | MODE | REPLICAS | IMAGE |
| :--- | :--- | :--- | :--- |
| ddd_redis | replicated | 1/1 | redis-alpine |
| ddd_web-fe | replicated | 4/4 | nigelppton/ddd-book:swarm-app |

```
$ docker stack ps ddd
```
