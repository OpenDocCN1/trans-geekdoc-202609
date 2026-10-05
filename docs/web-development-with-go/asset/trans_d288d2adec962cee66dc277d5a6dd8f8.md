
我们的服务器将知道在 PATH 变量所列出的其中一个目录中运行名为 go 的程序。

安装好 Go 后，我们将创建一个目录来存储我们的源代码。在不设置自定义 $GOPATH 环境变量的情况下，此目录是更改的，因此如果你不熟悉我们正在做什么，请严格按照步骤操作。

```
$ cd ~
$ mkdir -p go/src
```

通过运行 `go version` 来测试。

```
$ go version
```

或者，你可以在运行 `go` 命令时定义二进制文件的绝对路径。

```
/usr/local/go/bin/go version
```

## 16.7.4 设置 Caddy

Caddy¹¹⁰ 是一个用 Go 编写的 HTTP Web 服务器，我们将使用它来通过 Let's Encrypt 免费设置 HTTPS。Caddy 为我们处理了这一切所有工作，允许我们设置 DNS 服务器，然后创建一个简单的 Caddyfile（Caddy 的配置文件）并启动 Caddy。

在使用 Caddy 之前，我们需要构建它。如果你还没有登录服务器，请通过 SSH 登录到你的服务器。

注意：构建 Caddy 需要 Go 1.8 或更高版本。

¹⁰https://caddyserver.com/

## 16.7. 设置服务器

```
$ ssh root@123.123.22.33
```

然后导航到安装 Go 时创建的 Go 源代码目录，获取我们需要的包。

```
$ cd ~/go/src
$ go get -u github.com/mholt/caddy
$ go get -u github.com/caddyserver/builds
```

我们需要进入 mholt/caddy 项目来构建 Caddy。

```
$ cd ~/go/src/github.com/mholt/caddy/caddy
```

然后我们需要使用 `go run` 命令来构建它，并提供操作系统和架构标志位。

```
$ go run build.go -goos=linux -goarch=amd64
```

这可能需要几时间，但一旦 Caddy 完成构建，你就可以通过运行二进制文件来测试它。

```
$ ./caddy
Activating privacy features... done.
http://:2015
WARNING: File descriptor limit 1024 is too low for production servers.
At least 8192 is recommended. Fix with "ulimit -n 8192".
```

按下 ctrl-c 停止服务器，暂时不用担心该警告。我们将在完成部署应用程序之前处理它。

我们将刚刚创建的 caddy 二进制文件复制到 /usr/local/bin/ 目录，以便以后能够方便地访问它。

```
$ cp ../caddy /usr/local/bin/
```

我们需要设置一个服务文件来告知 systemd¹ 关于 Caddy，systemd 用于 Ubuntu 16.04 中管理系统进程。例如，我们将使用它来确保在服务器重启后重启 Caddy 和我们的 Web 应用程序。如果我们的任何一个应用程序崩溃，我们还可以设置重启的频率和时机。

```
$ sudo nano /etc/systemd/system/caddy.service
```

一旦打开服务文件，向其中填入以下内容：

```
[Unit]
Description=caddy server for serving lenslocked.com
[Service]
WorkingDirectory=/root/app
ExecStart=/usr/local/bin/caddy -email you@email.com
Restart=always
RestartSec=120
LimitNOFILE=192
[Install]
WantedBy=multi-user.target
```

### Box 16.8. 解释我们的服务文件

我们的服务文件分为三个部分：Unit、Service 和 Install。

第一部分用于描述我们创建的服务。在我们的情况下，我们只提供了一个通用的描述。

> ¹¹https://en.wikipedia.org/wiki/Systemd

## 16.7. 设置服务器

在第二部分中，我们定义了服务如何工作。`WorkingDirectory` 行定义了服务应该启动的位置。也就是说，它在运行任何命令之前应该进入哪个文件夹？

ExecStart 是我们的服务应该运行的命令。我们使用 caddy 二进制文件的绝对路径以避免任何问题，并将 “your@email.com” 替换为你自己的电子邮件地址。这用于与 Let’s Encrypt 通信以获取你的 SSL 证书。

接下来的两行描述了当服务崩溃时何时以及以及频率重启。我们希望将重启限制为每 120 秒一次，以避免意外超过 Let’s Encrypt 的 API 限制。如果你超过了 API 限制，你将在一段时间内无法通过他们的 API 获取新的 SSL 证书。

最后，`LimitNOFILE` 行用于解决我们首次启动 Caddy 时收到的“文件描述符限制”警告。

在最后部分即 install 部分，我们说明了如何启用我们的服务。通常你不需要自定义此部分，关于如何操作的细节不在本书的范围内。

按下 ctrl-x 退出 nano，然后按 y 确认你想保存，然后按回车确认我们想要使用提供的原始文件名。

现在我们需要重新加载内容以便我们的新文件被识别，并启用我们的新服务。

```
systemctl daemon-reload
systemctl enable caddy.service
```

我们可以通过重启 caddy 服务然后打印服务的日志来测试这一点，但首先我们需要创建服务尝试启动运行的 app 目录。

```
$ mkdir /root/app
$ sudo service caddy restart
$ journalctl -r
```

注意：journalctl 允许我们查看服务的日志，-r 标志表示按反序显示它们，这样我们就能先看到最新的日志。

输出应该类似于下面的输出，但你可能会发现如数字、服务器名称以及日期和显示方式有所不同。

```
.. caddy[10060]: http://:2015
ncaddy[10060]: Activating privacy features... done
```

注意：按下 q 退出 journalctl 日志。

我们现在不需要 caddy，所以可以停止它。

```
$ sudo service caddy stop
```

最后，我们需要设置一个 Caddyfile 来配置我们的 caddy 服务。我们将在 Web 应用程序源代码中创建它，以便人员可以在不登录生产服务器的情况下进行更改，但更改仍然推送到服务器。

```
$ touch Caddyfile
```

你的 Caddyfile 会根据你的使用情况而异。以下是两个潜在的 Caddyfile，第一个用于域名，第二个用于 IP 地址。

```
www.lenslocked.com {
  gzip
  proxy localhost:3000 {
    transparent
  }
}
```

在这个 Caddyfile 中，我们定义了我们的域名，然后是 Caddy 如何处理传入的请求。代理 Web 请求意味着我们的 Caddy 服务器将接收任何传入的请求并将其转发到 localhost:3000。

代理的 `transparent` 部分用于在将请求发送到 localhost 之前添加几个请求标头，例如添加用户的 IP 地址。我们不会使用该标头，但从经验来看，它们长期来看是有用的。

没有域名的 Caddyfile 基本上是一样的，但我们无法将其隔离到单个域名。

```
:80 {
  gzip
  proxy localhost:3000
    transparent
  }
}
```

我们现在还不会将其推送到服务器，而将在下一节创建部署脚本时处理它。

## 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异。

- 完成版 - book.usegolang.com/16.7.4
- 更改 - book.usegolang.com/16.7.4-diff

## 16.7.5 为我们的应用创建服务

就像我们为 Caddy 做的那样，我们需要为我们的 Web 应用程序添加服务。我们的服务将处理启动 Web 应用程序、在服务器重启或由于任何原因崩溃时重启它。

如果你还没有登录服务器，请通过 SSH 登录到你的服务器。

```
$ ssh root@123.123.22.33
```

为我们的应用程序创建一个服务文件。

```
$ sudo nano /etc/systemd/system/lenslocked.com.service
```

我们将在此文件中填入与我们为 Caddy 使用非常类似的 systemd 服务定义，只是这个将启动我们的 Web 应用程序。

```
[Unit]
Description=lenslocked.com app

[Service]
WorkingDirectory=/root/app
ExecStart=/root/app/server -prod
Restart=always
```

