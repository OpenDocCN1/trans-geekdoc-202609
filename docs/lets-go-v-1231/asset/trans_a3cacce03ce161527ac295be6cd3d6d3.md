

要运行 generate_cert.go 工具，你需要知道计算机上 Go 标准库源代码安装的位置。如果你使用的是 Linux、macOS 或 FreeBSD，并且按照官方安装说明操作，那么 generate_cert.go 文件应该位于 /usr/local/go/src/crypto/tls 下。

如果你使用 macOS 并通过 Homebrew 安装了 Go，该文件可能位于 /usr/local/Cellar/go/<version>/libexec/src/crypto/tls/generate_cert.go 或类似路径。

知道文件位置后，你可以这样运行 generate_cert.go 工具：

```
$ go run /usr/local/go/src/crypto/tls/generate_cert.go --rsa-bits=2048 --host=localhost
2024/03/18 11:29:23 wrote cert.pem
2024/03/18 11:29:23 wrote key.pem
```

在幕后，这个 generate_cert.go 命令分两个阶段工作：

- 1. 首先生成一个 2048 位的 RSA 密钥对，这是一个加密安全的公钥和私钥。
- 2. 然后它将私钥存储在 key.pem 文件中，并为主机 localhost 生成一个包含公钥的自签名 TLS 证书——并将其存储在 cert.pem 文件中。私钥和证书都采用 PEM 编码，这是大多数 TLS 实现使用的标准格式。

你的项目仓库现在应该如下所示：

![](img/c3e650db0d8dfdecc0f8e34a67719f65_254_0.png)

就这样！我们现在已经有了一个可在开发期间使用的自签名 TLS 证书（及其对应的私钥）。

## 其他信息

## mkcert 工具

作为 generate_cert.go 工具的替代方案，你可以考虑使用 mkcert 来生成 TLS 证书。虽然这需要一些额外的设置，但其优势在于生成的证书是本地受信任的——这意味着你可以用于测试和开发，而不会在 Web 浏览器中收到安全警告。

## 运行 HTTPS 服务器

既然我们有了自签名 TLS 证书和相应的私钥，启动 HTTPS Web 服务器就变得简单而轻松——我们只需打开 `main.go` 文件，将 `srv.ListenAndServe()` 方法替换为 `srv.ListenAndServeTLS()` 即可。

修改你的 `main.go` 文件以匹配以下代码：

```
package main

...

func main() {
	addr := flag.String("addr", ":4000", "HTTP network address")
	dsn := flag.String("dsn", "web:pass@/snippetbox?parseTime=true", "MySQL data source name")
	flag.Parse()

	logger := slog.New(slog.NewTextHandler(os.Stderr, nil))

	db, err := openDB(*dsn)
	if err != nil {
		logger.Error(err.Error())
		os.Exit(1)
	}

	defer db.Close()

	templateCache, err := newTemplateCache()
	if err != nil {
		logger.Error(err.Error())
		os.Exit(1)
	}

	formDecoder := form.NewDecoder()

	sessionManager := scs.New()
	sessionManager.Store = mysqlstore.New(db)
	sessionManager.Lifetime = 12 * time.Hour
	// Make sure that the Secure attribute is set on our session cookies.
	// Setting this means that the cookie will only be sent by a user's web
	// browser when a HTTPS connection is being used (and won't be sent over an
	// insecure HTTP connection).
	sessionManager.Cookie.Secure = true

	app := &application{
		logger:      logger,
		snippets:    &models.SnippetModel{DB: db},
		templateCache: templateCache,
		formDecoder: formDecoder,
		sessionManager: sessionManager,
	}

	srv := &http.Server{
		Addr:     *addr,
		Handler:  app.routes(),
		ErrorLog: slog.NewLogLogger(logger.Handler(), slog.LevelError),
	}

	logger.Info("starting server", "addr", srv.Addr)

	// Use the ListenAndServeTLS() method to start the HTTPS server. We
	// pass in the paths to the TLS certificate and corresponding private key as
	// the two parameters.
	err = srv.ListenAndServeTLS("./tls/cert.pem", "./tls/key.pem")
	logger.Error(err.Error())
	os.Exit(1)
}

...
```

运行此代码后，我们的服务器仍将监听 4000 端口——唯一的区别是它现在将使用 HTTPS 而不是 HTTP 进行通信。

照常运行它：

```
$ cd $HOME/code/snippetbox
$ go run ./cmd/web
time=2024-03-18T11:29:23.000+00:00 level=INFO msg="starting server" addr=:4000
```

如果你在 Web 浏览器中打开 https://localhost:4000/，你很可能会收到浏览器警告，因为 TLS 证书是自签名的，类似于下面的截图。

![](img/c3e650db0d8dfdecc0f8e34a67719f65_257_0.png)

- 如果你和我一样使用 Firefox，请点击“高级”，然后点击“接受风险并继续”。

- 如果你使用 Chrome 或 Chromium，请点击“高级”，然后点击“继续访问 localhost（不安全）”链接。

之后，应用程序主页应该会出现（尽管 URL 栏中仍然会显示警告）。

在 Firefox 中，它看起来应该大致如下：

## Snippetbox

## 最新代码片段

| 标题 | 创建时间 | ID |
| :--- | :--- | :--- |
| 鹪鹩 | 2022 年 4 月 5 日 16:21 | #6 |
| 时不时 | 2022 年 4 月 5 日 14:59 | #5 |
| 0 只蜗牛 | 2022 年 4 月 5 日 07:32 | #4 |
| 初秋的早晨 | 2022 年 4 月 5 日 07:20 | #3 |
| 越过冬日森林 | 2022 年 4 月 5 日 07:20 | #2 |
| 古老的静谧池塘 | 2022 年 4 月 5 日 07:20 | #1 |

如果你使用 Firefox，我建议按 Ctrl+I 来检查主页的页面信息：

![](img/c3e650db0d8dfdecc0f8e34a67719f65_259_0.png)

此处的“安全 > 技术详情”部分确认我们的连接已加密并按预期工作。

就我而言，可以看到正在使用 TLS 版本 1.3，我的 HTTPS 连接使用的加密套件是 TLS_AES_128_GCM_SHA256。我们将在下一章详细讨论加密套件。

> **旁注：** 如果你想知道上面的截图中“网站身份”部分的“Acme Co”是谁或是什么，那只是 `generate_cert.go` 工具使用的一个硬编码占位符名称。

## 其他信息

## HTTP 请求

需要注意的是，我们的 HTTPS 服务器 *仅支持 HTTPS*。如果你尝试向其发送常规 HTTP 请求，服务器会向用户返回 400 Bad Request 状态和消息

"Client sent an HTTP request to an HTTPS server"。不会记录任何日志。

```
$ curl -i http://localhost:4000/
HTTP/1.0 400 Bad Request

Client sent an HTTP request to an HTTPS server.
```

## HTTP/2 连接

使用 HTTPS 的一个巨大优点是，如果客户端支持，Go 会自动将连接升级为 HTTP/2。

这是件好事，因为这意味着最终我们的页面对用户来说加载会更快。如果你不熟悉 HTTP/2，可以观看 Brad Fitzpatrick 在 GoSF 聚会上的演讲，了解基础知识以及 HTTP/2 在 Go 内部的实现方式。

如果你使用的是最新版本的 Firefox，应该能看到这一点。按 Ctrl+Shift+E 打开开发者工具，查看主页的响应头时，你应该能看到所使用的协议是 HTTP/2。

![](img/c3e650db0d8dfdecc0f8e34a67719f65_260_0.png)

## 证书权限

需要注意的是，运行 Go 应用程序的用户必须对 cert.pem 和 key.pem 文件都有读取权限，否则 ListenAndServeTLS() 将返回权限被拒绝错误。

默认情况下，generate_cert.go 工具会为 cert.pem 文件授予所有用户的读取权限，但只为 key.pem 文件的所有者授予读取权限。就我而言，权限如下：

```
$ cd $HOME/code/snippetbox/tls
$ ls -l
total 8
-rw-rw-r-- 1 alex alex 1090 Mar 18 16:24 cert.pem
-rw------- 1 alex alex 1704 Mar 18 16:24 key.pem
```

一般来说，最好将私钥的权限设置得尽可能严格，仅允许所有者或特定组读取。

## 版本控制

如果你使用版本控制系统（如 Git 或 Mercurial），可能需要添加忽略规则，以免不小心提交 tls 目录的内容。以 Git 为例：

```
$ cd $HOME/code/snippetbox
$ echo 'tls/' >> .gitignore
```

## 配置 HTTPS 设置

Go 为其 HTTPS 服务器提供了良好的默认设置，但仍可以优化和自定义服务器的行为。

一个几乎总是值得做的更改是限制 TLS 握手期间可能使用的 *椭圆曲线*。Go 支持一些椭圆曲线，但截至 Go 1.23，只有 `tls.CurveP256` 和 `tls.X25519` 有汇编实现。其他曲线非常耗 CPU，因此省略它们有助于确保服务器在高负载下保持高性能。

要进行此调整，我们可以创建一个包含非默认 TLS 设置的 `tls.Config` 结构体，并在启动服务器之前将其添加到 `http.Server` 结构体中。

我来演示：

