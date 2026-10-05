

```yaml
services:
  web-fe:             <----- 服务名称。容器将
  deploy:
    replicas: 1          <----- 为该服务部署单个容器
    build:               <----- 从当前目录下的 Dockerfile 构建
    command: python app.py <----- 启动时执行此命令
    ports:
      target: 8080       <----- 映射容器内的端口
      published: 5001 <----- ...映射到 Docker 宿机的 5001 端口
  networks:
    counter-net          <----- 将容器连接到 "counter" 网络
  volumes:
    type: volume
    source: counter-vol <----- 挂载 "counter-vol" 卷
    target: /app         <----- ...挂载到容器内的 "/app"
```

让我们逐一分析。

- **web-fe:** 是服务的名称，所有作为此服务创建创建的容器其名称中都包含“web-fe”。
- **deploy.replicas: 1** 告诉 Docker 为此服务部署单个容器。你可以指定不同的副本数量来为该服务部署多个相同的容器。然而，这在 Docker 安装上无法实现，因为你只有一个 Docker 宿主机，且只有一个容器可以使用 Docker Desktop 宿主机上的 5001 端口。你将在 **Deploying apps with Docker stacks** 章节中学习如何为此服务部署多个副本。

- **build:** 告诉 Docker 根据当前目录下的 Dockerfile 构建此服务容器的镜像。
- **command: python app.py** 是 Docker 在为此服务创建的每个容器内部执行的命令。镜像中必须存在 **app.py** 文件，且镜像必须安装了 Python。Dockerfile 会处理这两个需求。
- **ports:** 在此处将服务容器的网络端口映射到 Docker 宿主机。此示例映射了容器内部的 5001 端口。
- **networks:** 告诉 Docker 将此服务的容器连接到 **counter-net** 网络。该网络应该已经存在或者在 **networks** 顶层键中定义。
- **volumes:** 告诉 Docker 将 **counter-vol** 卷挂载到所有服务容器内部的 `/app` 目录。该卷应该已经存在或者在 **volumes** 顶层键中定义。

总之，Compose 将指示 Docker 为 **web-fe** 服务部署单个容器。它将从相同目录下的 Dockerfile 构建新镜像，并从该镜像启动容器。当容器启动时，其名称将包含 **web-fe** 并运行 **python app.py** 命令。它将连接到 **counter-net** 网络，在宿主机的 5001 端口上暴露 Web 服务，并将 counter-vol 卷挂载到 /app。如果你定义了多个副本（容器），它们将是完全相同的。

**注意：** 你不需要在 Compose 文件中指定 `command: python app.py` 选项，因为它已经在 Dockerfile 中定义过了。不过，我在这里展示它是为了让你知道它是如何工作的。你也可以使用 Compose 来覆盖 Dockerfile 中的指令。

`redis` 服务要简单得多。

让我们来看这一个。

- **redis:** 是服务的名称，所有作为此服务创建的容器其名称中都包含“redis”部分。
- **deploy.replicas: 1** 告诉 Docker 为此服务部署单个容器。
- **image: redis:alpine** 告诉 Docker 从 Docker Hub 拉取 redis:alpine 镜像并使用它启动服务的容器。
- **networks:** 告诉 Docker 将服务的容器连接到 counter-net 网络。

将两个服务都连接到 counter-net 网络意味着它们可以通过名称相互解析并进行通信。这是重要的，因为下面 app.py 文件的片段显示了 Web 应用通过名称与 redis 服务进行通信。

```python
import time
import redis
from flask import Flask, render_template
app = Flask(__name__)
cache = redis.Redis(host='redis', port=6379) <----- "redis" 是
<Snip>
```

networks 和 volumes 块非常简单，定义了一个名为 counter-net 的网络和一个名为 counter-vol 的卷。

```yaml
networks: <----- 此块定义了一个新网络
  counter-net:
volumes: <----- 此块定义了一个新卷
  counter-vol:
```

现在我们理解了 Compose 文件是如何工作的的，让我们来部署应用。

# 使用 Compose 部署应用

在本节中，你将使用 Compose 文件来部署应用。你需要该书籍 GitHub 仓库的本地副本，并且需要在 **multi-container** 文件夹中运行所有命令。

运行以下命令来部署应用：

```bash
docker compose -f docker-compose.yml up -d
```
（注：根据上下文推断上述命令，因为 OCR 文字被裁剪了）。

