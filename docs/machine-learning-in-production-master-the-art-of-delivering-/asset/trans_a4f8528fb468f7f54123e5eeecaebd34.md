
添加 Docker 的官方 GPG 密钥。

GNU 隐私保护（GPG 或 GnuPG）是一个命令行工具，用于实现公钥加密和验证服务。GPG 在 Linux 中常用于对文件进行数字签名，从而确保软件项目文件的真实性。

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

使用以下命令设置存储库：

```
$ echo \
"deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/
docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
$(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

## 安装 Docker 引擎

```
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
sudo docker --version
```

以下图显示当前 Docker 版本：

![](img/cc4299656808e62a294f1843a1e18e72_138_0.png)

图 6.1: Docker 版本

在终端中运行以下命令以检查 Docker 服务的状态：

```
sudo systemctl status docker
```

以下图显示前一命令的输出：

![](img/cc4299656808e62a294f1843a1e18e72_138_1.png)

图 6.2: Docker 状态检查

## Docker Compose

Docker Compose 使开发者能够配置并运行多个容器。它从 docker-compose.yml 文件中读取配置。单个 docker-compose up 命令可以启动服务并运行多容器应用程序。另一方面，你可以使用 docker-compose down 命令销毁所有内容。你也可以通过添加 --volumes 标志来删除卷。

你可以使用以下命令安装 Docker Compose：

```
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

以下图显示 Docker Compose 的安装过程：

![](img/cc4299656808e62a294f1843a1e18e72_139_0.png)

授权 docker-compose 执行文件：

```
sudo chmod +x /usr/local/bin/docker-compose
```

最后，验证安装：

```
docker-compose --version
```

以下图显示当前 Docker Compose 版本：

![](img/cc4299656808e62a294f1843a1e18e72_139_1.png)

安装提供以下内容：

- Docker 引擎
- Docker CLI 客户端
- Docker Compose

## 使用 Docker 的 Hello World

这是一个示例 Docker 镜像，用于测试 Docker 是否正常工作。通过运行以下命令，你将创建第一个 Docker 容器：

```
sudo docker run hello-world
```

以下图显示前一命令的执行情况：

![](img/cc4299656808e62a294f1843a1e18e72_140_0.png)

图 6.5: Docker 镜像 - hello-world

它还会生成以下输出，告诉你幕后发生了什么：

生成此消息时，Docker 执行了以下步骤：

- 1. Docker 客户端联系了 Docker 守护进程。
- 2. Docker 守护进程从 Docker Hub 拉取了 "hello-world" 镜像。
  - (amd64)
- 3. Docker 守护进程从该镜像创建了一个新容器，该容器运行生成你当前正在阅读的输出的可执行文件。
- 4. Docker 守护进程将该输出流式传输到 Docker 客户端，然后由客户端将其发送到你的终端。

你执行了 docker run 命令，后跟镜像名称。系统中不存在所需镜像，因此它没有停止后续执行，而是从 Docker Hub 拉取了该镜像。

以下图显示系统中的 Docker 结构。如你所见，Docker 可以在共享相同基础架构的隔离环境中运行多个容器。

![](img/cc4299656808e62a294f1843a1e18e72_141_0.png)

图 6.6: Docker 堆栈

## Docker 对象

使用 Docker 时，你可以创建和使用 Docker 对象，例如镜像、容器、卷和网络。在本章中，你将学习其中一些对象。

## Dockerfile

Dockerfile 可以被视为一组命令或指令，使开发者能够构建 Docker 镜像。这些命令或指令会按顺序执行。它是一个没有扩展名的纯文本文档。

## Docker 镜像

要创建 Docker 容器，需要先创建 Docker 镜像。它存储了运行应用程序所需的所有代码和依赖项，并充当运行容器实例的模板。Docker 镜像可以上传到 Docker Hub，从此处可以将其拉取到服务器或系统中以运行容器。

要查看可用 Docker 镜像的列表，请在终端中执行以下命令：

```
docker images
```

## Docker 容器

当你运行 Docker 镜像时，会创建一个容器实例。你可以使用同一个 Docker 镜像运行任意数量的容器。它是 Docker 生态系统的重要组成部分。Docker 在隔离环境中运行容器。

当开发者运行容器时，一个名为容器层的额外层会自动创建在现有镜像层之上。Docker 容器有自己的读写层，允许开发者对该容器进行特定更改。假设你使用同一个 Docker 镜像运行三个容器，并在其中一个运行中的容器内安装了另一个版本的 Python 包。这不会影响其他容器中 Python 包的现有版本。Docker 使用 Docker 卷来管理 Docker 容器内的数据。

你在镜像或容器中创建的所有文件都是联合文件系统的一部分。但是，数据卷是 Docker 主机文件系统的一部分，并简单地挂载到容器内部。

它在容器创建时初始化。默认情况下，当容器停止时，它不会被删除。数据卷也可以跨容器共享，并且可以以只读模式挂载。

检查所有运行中容器的命令是 `docker ps`。

检查所有运行中和已停止容器的命令是 `docker ps -a`。

### 分离模式

要在后台运行 Docker，请以分离模式运行容器。你可以使用 `-d` 标志以分离模式运行容器。

## Docker 容器网络

通常，Docker 主机包含多个 Docker 容器。Docker 容器还需要与本地和远程容器进行交互和协作，以构建分布式应用程序。桥接网络是 Docker 引擎分配给容器的默认网络接口。

```
docker network ls
```

此命令将显示网络列表及其范围。输出包含以下表头：

NETWORK ID、NAME、DRIVER、SCOPE

要检查任何 Docker 容器的网络详细信息，请使用以下命令，后跟网络 ID：

```
docker network inspect <NETWORK ID>
```

## 端口映射

-p 标志用于将容器端口映射到主机端口。请参考以下示例：

```
docker run -p <myport>:<containerport> nginx
```

> 注意：要观察输出，请使用 docker logs [container_id]。

## 创建 Dockerfile

Dockerfile 遵循简单易懂的结构，即 # 注释，后跟一条指令和一个参数。通常将指令写为大写，以区分指令和参数。

### FROM

- FROM 指令为后续指令设置基础镜像。
- 有效的 Dockerfile 必须包含 FROM 指令。
- FROM 可以在 Dockerfile 中出现多次。

### CMD

- CMD 定义在创建容器时要执行的默认命令。
- CMD 在构建镜像时不会执行。
- 可以在运行时被覆盖。

### RUN

它在当前镜像之上的新层中执行一个命令，并提交结果。

### COPY

COPY 指令从 <src> 复制新文件或目录，并将它们添加到容器文件系统中的 <dest> 路径。

### ENTRYPOINT

这可帮助你将容器配置为可执行文件；它类似于 CMD。ENTRYPOINT 指令最多只能有一条；如果指定了多条，则只有最后一条会被采纳。
