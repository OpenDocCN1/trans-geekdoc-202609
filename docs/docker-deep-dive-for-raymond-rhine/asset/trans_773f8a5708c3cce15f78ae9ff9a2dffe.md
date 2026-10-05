

# 图 11.2

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

如果你展开每个顶层键，你会看到它们是如何映射到图 11.2 的，其中包含名为 **counter-net** 的网络，一个名为 **counter-vol** 的卷，以及两个名为 **web-fe** 和 **redis** 的服务。

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

# 深入研究栈文件

栈文件与 Compose 文件相同，但在运行时有几处不同。例如，Docker Compose 允许你在运行时构建镜像，但 Docker Stacks 不行。

让我们看看栈文件中定义的网络元素。

# 网络与网络化

当你从栈文件部署应用程序时，Docker 执行的第一件事之一就是创建 **networks** 键下列出的网络。如果它们已经存在，Docker 不需要做任何操作。但如果它们不存在，它就会创建它们。

此应用程序定义了一个名为 **counter-net** 的单一加密覆盖网络。

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

# 卷与挂载

应用程序定义了一个名为 counter-vol 的单一卷，并将其挂载到所有 web-fe 副本的 /app 目录。这意味着对 /app 文件夹的所有读写操作都将在卷中进行。

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

# 服务

大多数操作发生在服务处。我们的应用程序定义了两个，我们将逐一查看它们。

# web-fe 服务

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

