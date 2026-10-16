
通常，获取证书需要三个步骤：证书请求、域名验证和证书发放。首先，你向 Let’s Encrypt 请求你的域名的证书。Let’s Encrypt 然后会确认你的域名以确保你管理它。一旦 Let’s Encrypt 确认你是域名的合法所有者，它就会为你发放证书，供你的 Web 服务器使用 HTTPS。每个证书有效期为 90 天，但建议每 60 天续期，以防止服务中断。

Caddy 内置 ACME 协议支持，若能正确推断其托管的域名，Caddy 会自动请求、验证并安装 Let’s Encrypt 证书。我们将在“Adding Automatic HTTPS”（第 237 页）中讨论最佳做法。Caddy 还会自动处理证书续期，免除你记录证书到期日期的麻烦。

**218** 第 10 章

**_Caddy 如何融入方程？_**

Caddy 与其他流行的 Web 服务器（如 NGINX、Apache）类似。它最适合放在网络边缘，介于客户端和 Web 服务之间，如图 10-1 所示。

客户端

PHP-FPM

WordPress

客户端

Caddy

Web 服务

数据库

第三方 API

客户端

静态文件

*图 10-1：Caddy 反向代理客户端请求到 Web 服务*

Caddy 可提供静态文件并代理客户端与后端服务之间的请求，这称为 *反向代理*。在此示例中，你可以看到 Caddy 通过 PHP 的 FastCGI 进程管理器（PHP-FPM）为 WordPress 博客提供服务，同时提供静态文件和基于 Go 的 Web 服务。本章后面会复现类似的架构（不含 WordPress 博客）。

Caddy 通过抽象客户端与 Web 服务的方式，与我们在代码中使用抽象的方式类似。如果你使用 Caddy 的自动 TLS、静态文件服务器、数据压缩、访问控制和日志功能，就无需在每个 Web 服务中额外添加这些功能。此外，使用 Caddy 的好处在于可以将网络拓扑抽象给客户端。随着服务受欢迎程度提升，Web 服务的容量限制对客户端产生负面影响时，你可以向 Caddy 添加更多 Web 服务，并指示 Caddy 在多个服务之间均衡负载，而不会影响客户端。

**获取 Caddy**

本章将使用 Caddy 2 版本。安装方式在本节中描述。

**_下载 Caddy_**

你可以使用 Caddy 团队构建的静态二进制文件进行安装。该二进制文件可通过 *https://caddyserver.com/* 链接下载。Caddy 还提供 Docker 镜像、DigitalOcean 滴点、基于 Debian 衍生的 APT 源以及在 Fedora Copr 构建系统中用于 Fedora、CentOS 或红帽企业 Linux 的包。详情请参见 *https://caddyserver.com/docs/download* 的安装文档。

Caddy: 现代 Web 服务器 **219**

**_从源码编译 Caddy_**

如果在你的操作系统和架构上找不到合适的静态二进制文件，或希望自定义 Caddy，也可以从源码编译 Caddy。

Caddy 依赖 Go 的模块支持，因此在运行下面的命令前，需要至少使用 Go 1.14：

$ **git clone "https://github.com/caddyserver/caddy.git"**

克隆到 'caddy'...

$ **cd caddy/cmd/caddy**

$ **go build**

克隆 Caddy Git 仓库并切换到 *caddy/cmd/caddy* 子目录，这里是主包所在的目录。执行 go build 可为你的操作系统和架构生成名为 *caddy* 的二进制文件。为简化后续命令，本章其余部分假设 *caddy* 二进制文件在 PATH 中。

在该子目录下，请注意 *main.go* 文件。后续章节将在介绍如何通过添加模块来自定义 Caddy 时再次用到它。

**运行和配置 Caddy**

为配置 Caddy，它会在 TCP 端口 2019 上提供管理端点，通过该端点可以实时与 Caddy 的配置交互。你可以通过向该端点发送 JSON 来配置 Caddy，也可以通过 GET 请求读取配置。Caddy 完整的 JSON API 文档可在 *https://caddyserver.com/docs/json/* 查看。

在配置前，你需要先启动 Caddy。运行以下命令可让 Caddy 以后台进程方式启动：

$ **caddy start**

2006/01/02 15:04:05.000 INFO admin endpoint started

{"address": "tcp/localhost:2019", "enforce_origin": false, "origins": ["localhost:2019", "[::1]:2019", "127.0.0.1:2019"]}

2006/01/02 15:04:05.000 INFO serving initial configuration

Successfully started Caddy (pid=24587) - Caddy is running in the background

日志会显示 admin endpoint 已启动，Caddy 正在使用初始配置。你在与管理端点交互时，还会在标准输出中看到日志。

Caddy 的默认配置为空。下面我们发送有意义的配置数据给 Caddy。列表 10-1 使用 curl 命令向 Caddy 的管理端点的 load 资源发送 JSON。

$ **curl localhost:2019/load \\**

1 **\-X POST -H "Content-Type: application/json" \\**

**\-d '**

**220** 第 10 章

**{**

**"apps": {**

**"http": {**

**"servers": {**

**"hello": {**

**"listen": ["localhost:2020"],**

2 **"routes": [{

**"handle": [{

**"handler": "static_response",

**"body": "Hello, world!"**

**}]**

**}]**

**}**

**}**

**}**

**}**

**}'**

*列表 10-1：向 Caddy 的管理端点发送配置*

你向 Caddy 实例（监听端口 2019）的 load 资源发送包含 JSON 的 POST 请求。顶层 apps 命名空间列出在运行时 Caddy 将加载的应用。此例告诉 Caddy 加载 http 应用。http 应用的配置包含一个或多个服务器。这里设置了一个名为 hello 的服务器，监听 localhost 端口 2020。你可以为服务器起任何你喜欢的名字。

由于 listen 值是数组，你可以配置该服务器监听多个套接字地址。Caddy 会将这些地址传递给 net.Listen，正如第 3 章所示。你也可以指定端口范围，如 localhost:2020-2025。Caddy 会识别为范围并展开为独立的套接字地址。你可以通过在套接字地址前加前缀来限制网络类型，例如 udp/localhost:2020 表示在 localhost 的 UDP 端口 2020 上绑定。斜杠不是地址的一部分，而是分隔符。若要绑定到 Unix 域套接字 /tmp/caddy.sock，则需指定地址 unix//tmp/caddy.sock。

hello 服务器的 routes 值 2 是一个路由数组，类似于前一章的多路复用器，决定服务器如何处理进入的请求。如果路由匹配请求，Caddy 会将请求转发给该路由数组中的每个处理器。由于 handle 是数组，你可以在同一路由下指定多个处理器，Caddy 会像链式中间件一样依次将请求传递给每个处理器。此例中，我们为匹配所有请求的单一路由添加了一个处理器。我们使用内置的 static_response 处理器 3，它会在响应体中写入 body 的值（本例中为 “Hello, world!”）。

Caddy: 现代 Web 服务器 **221**

如果配置无误，Caddy 会立即使用新配置。让我们确认 Caddy 是否现在正在监听。

