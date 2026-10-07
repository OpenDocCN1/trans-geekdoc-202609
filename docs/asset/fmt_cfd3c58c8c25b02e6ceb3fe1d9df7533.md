
如果 Docker 没有运行，输出中可能会出现类似这样的错误：

```
Server:

ERROR: error during connecting: this error may indicate that the docker daemon is not running...
```

一旦验证 Docker 正在运行，我们就可以导航到包含 `Dockerfile` 的目录并运行此命令：

```
docker build -t housing
```

## 容器

其中 `housing` 是赋予镜像的名字。注意命令末尾的点 `.` 表示在当前目录构建。随着镜像的构建，日志将流式传输到控制台。这是一个成功的构建消息示例：

```
[+] Building 8s (1/10) FINISHED
```

我们可以通过打开终端并运行此命令来验证 Docker 正在运行：

```
docker images
```

输出包含了所有镜像：

| REPOSITORY | TAG | IMAGE ID | CREATED | SIZE |
|---|---|---|---|---|
| housing | latest | 3038c4147f | 44 seconds ago | 1.3GB |

我们可以使用以下命令从镜像运行一个新的容器：

```
docker run
```

输出包含了预期的 R 平方值：

`R-squared: 0.6092160009090456`

我们可以通过运行此命令查看所有容器：

```
docker ps -a
```
