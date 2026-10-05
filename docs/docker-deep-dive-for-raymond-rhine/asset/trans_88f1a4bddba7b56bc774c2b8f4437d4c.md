

```
"sha256:a48b3b3d0c5a693840e7e4abd7971f130b444753,
"sha256:ea2d4594dbbbef4009441a33dd1dd4c5076d7fe09a"
},
```

如前文所述，输出显示了七层，因为基础镜像有四层，而 Dockerfile 又增加了三层。

图 8.5 将 Dockerfile 指令映射到镜像层。带有箭头的粗体指令会创建层；其他指令则创建元数据。层 ID 在你的环境中会有所不同。

![](img/aae0230bf8529bd80767c4c780dca8d3_190_0.png)

图 8.5

**注意：** 旧版本的构建器不会为 WORKDIR 指令创建层。然而，该指令会修改文件系统权限，当前的构建器会创建一个非常小的层。这种行为在未来可能会发生变化。

通常认为，使用 Docker 官方镜像和验证发布者镜像作为你创建的新镜像的基础层是一项良好实践。这是因为它们保持了高标准，并能对已知漏洞快速修复。

## 使用多阶段构建进入生产环境

在容器镜像方面……越大越坏！例如：

-   大意味着速度慢
-   大意味着更多的潜在漏洞
-   大意味着更大的攻击面

由于这些原因，你的容器镜像应该只包含在生产环境中运行你的应用程序**需要**的内容。

这就是多阶段构建大显身手的地方。

从高层来说，多阶段构建使用一个带有多个 FROM 指令的单个 Dockerfile —— 每个指令代表一个一个新的构建阶段。这允许你拥有一个阶段，在包含编译器和其他构建工具的大型镜像内部进行构建应用程序的繁重工作，然后你还有另一个阶段，将编译后的应用拷贝到精简镜像（slim image）中用于生产环境。构建器甚至可以并行运行不同的阶段以加快构建速度。

图 8.6 显示了一个高层工作流。阶段 1 构建了一个包含所有所需构建和编译工具的镜像。阶段 2 将应用代码拷贝到镜像并进行构建。阶段 3 创建了一个微小的生产就绪镜像，仅包含编译后的应用以及运行它所需的任何内容。

![](img/aae0230bf8529bd80767c4c780dca8d3_192_0.png)

图 8.6

让我们来看一个例子！

我们将使用该书籍 GitHub 仓库中 `multi-stage` 文件夹下的代码。这是一个简单的 Go 应用，其客户端和服务器借自 GitHub 上的 Docker 示例项目 `buildme` 仓库。如果你不是 Go 程序员，不要担心；你不需要是。你只需要知道它会将客户端和服务器应用编译成可执行文件，这些文件不需要 Go 语言或任何其他工具或运行时即可执行。

是 Dockerfile：

```
FROM golang:1.22.1-alpine AS Stage 0
WORKDIR /src
COPY go.mod go.sum .
RUN go mod download
COPY . .

FROM base AS build-client << Stage 1
RUN go build -o /bin/client ./cmd/client

FROM base AS build-server << Stage 2
RUN go build -o /bin/server ./bin/server

FROM scratch AS prod << Stage 3
COPY --from=build-client /bin/client /bin/
COPY --from=build-server /bin/server /bin/
ENTRYPOINT [ "/bin/server" ]
```

需要注意的第一点是有四个 FROM 指令。每一个指令都是一个独立的构建阶段，Docker 从 0 开始对它们进行编号。然而，我们为每个阶段提供了一个友好的名称：

- Stage 0 称为 base，构建一个包含编译工具等内容的镜像
- Stage 1 称为 build-client，编译客户端可执行文件
- Stage 2 称为 build-server，编译服务器可执行文件
- Stage 3 称为 prod，将客户端和服务器可执行文件拷贝到精简镜像中

每个阶段都会输出一个中间镜像，后续阶段可以使用该镜像。然而，当最终阶段完成后，Docker 会删除它们。

base 阶段的目标是创建一个可重用的构建镜像，包含阶段 1 和 2 构建客户端和服务器应用所需的所有工具。此阶段创建的镜像仅用于编译可执行文件，而不用于生产。它拉取了 `golang:1.22.1-alpine` 镜像，该镜像解压缩后超过 300MB。它将工作目录设置为 `/src` 并从你的目录中拷贝 `go.mod` 和 `go.sum` 文件。这些文件列出了应用程序的依赖。之后，它使用 `RUN` 指令安装依赖，然后使用 `COPY` 指令将应用程序代码拷贝到镜像中。这一切创建一个包含许多构建内容的巨大镜像。当此构建阶段完成后，它会输出一个后续阶段可以使用的大镜像。build-client 阶段没有拉取新镜像。相反，它使用 `FROM base AS build-client` 指令使用 base 阶段创建的中间镜像。然后它发布一个 RUN 指令将客户端应用编译为二进制文件。该阶段的目标是创建一个包含编译后的客户端二进制文件的镜像，供后续阶段引用。build-server 阶段对服务器执行了相同的操作，并输出一个类似的镜像供后续阶段使用。prod 阶段拉取了最小的 `scratch` 镜像。它运行运行两个 `COPY --from=` 指令，从 build-client 阶段拷贝编译后的客户端应用，从 build-server 阶段拷贝编译后的服务器应用。然后它告诉 Docker 在作为容器启动时运行服务器应用。该阶段输出最终的生产镜像，极小的镜像内仅包含客户端和服务器二进制文件以及告知如何启动应用的元数据。构建器将首先运行 base 阶段，然后并行运行 build-client 和 build-server 阶段，最后运行 prod 阶段。

它始终尝试并行运行阶段，但只有在不存在依赖关系时才能这样做。例如，build-client 和 build-server 阶段依赖于 base 阶段，在 във阶段完成之前无法运行（两者都从 FROM 开始）。然而，build-client 和 build-server 阶段之间没有相互依赖，因此它们之间可以并行运行。

