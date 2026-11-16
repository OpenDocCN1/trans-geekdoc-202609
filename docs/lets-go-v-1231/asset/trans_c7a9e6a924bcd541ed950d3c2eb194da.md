

文件：cmd/web/main.go

package main

import (
	"crypto/tls" // New import
	"database/sql"
	"flag"
	"html/template"
	"log/slog"
	"net/http"
	"os"
	"time"

	"snippetbox.alexedwards.net/internal/models"

	"github.com/alexedwards/scs/mysqlstore"
	"github.com/alexedwards/scs/v2"
	"github.com/go-playground/form/v4"
	_ "github.com/go-sql-driver/mysql"
)

...

func main() {
	...

	app := &application{
		logger:      logger,
		snippets:    &models.SnippetModel{DB: db},
		templateCache: templateCache,
		formDecoder: formDecoder,
		sessionManager: sessionManager,
	}

	// Initialize a tls.Config struct to hold the non-default TLS settings we
	// want the server to use. In this case the only thing that we're changing
	// is the curve preferences value, so that only elliptic curves with
	// assembly implementations are used.
	tlsConfig := &tls.Config{
		CurvePreferences: []tls.CurveID{tls.X25519, tls.CurveP256},
	}

	// Set the server's TLSConfig field to use the tlsConfig variable we just
	// created.
	srv := &http.Server{
		Addr:      *addr,
		Handler:   app.routes(),
		ErrorLog:  slog.NewLogLogger(logger.Handler(), slog.LevelError),
		TLSConfig: tlsConfig,
	}

	logger.Info("starting server", "addr", srv.Addr)

	err = srv.ListenAndServeTLS("./tls/cert.pem", "./tls/key.pem")
	logger.Error(err.Error())
	os.Exit(1)
}

...

## 其他信息

## TLS 版本

默认情况下，Go 的 HTTPS 服务器配置为支持 TLS 1.2 和 1.3。您可以使用 `tls.Config.MinVersion` 和 `MaxVersion` 字段以及 `crypto/tls` 包中的 TLS 版本常量来自定义此设置并更改最小和最大 TLS 版本。

例如，如果您希望服务器仅支持 TLS 1.0 到 1.2 版本，可以使用如下配置：

```
tlsConfig := &tls.Config{
  MinVersion: tls.VersionTLS10,
  MaxVersion: tls.VersionTLS12,
}
```

## 密码套件

Go 支持的密码套件也定义在 `crypto/tls` 包的常量中。

但是，其中一些密码套件（具体来说，不支持完美前向保密，或使用 RC4、3DES 或 CBC_SHA256 的密码套件）被认为是弱密码套件，且默认情况下不会被 Go 的 HTTPS 服务器使用。从 Go 1.23 开始，Go 的 HTTPS 服务器默认使用的密码套件如下：

| 密码套件 | 备注 |
| :--- | :--- |
| TLS_AES_128_GCM_SHA256 | // 仅 TLS 1.3 连接 |
| TLS_AES_256_GCM_SHA384 | // 仅 TLS 1.3 连接 |
| TLS_CHACHA20_POLY1305_SHA256 | // 仅 TLS 1.3 连接 |
| TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256 | // 仅 TLS 1.2 连接 |
| TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384 | // 仅 TLS 1.2 连接 |
| TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256 | // 仅 TLS 1.2 连接 |
| TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384 | // 仅 TLS 1.2 连接 |
| TLS_ECDHE_RSA_WITH_CHACHA20_POLY1305_SHA256 | // 仅 TLS 1.2 连接 |
| TLS_ECDHE_ECDSA_WITH_CHACHA20_POLY1305_SHA256 | // 仅 TLS 1.2 连接 |
| TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA | // TLS 1.0、1.1 和 1.2 连接 |
| TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA | // TLS 1.0、1.1 和 1.2 连接 |
| TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA | // TLS 1.0、1.1 和 1.2 连接 |
| TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA | // TLS 1.0、1.1 和 1.2 连接 |

重要：出于客户端兼容性原因，此默认列表包括一些易受 Lucky Thirteen 定时攻击影响的 CBC 密码。Go 对这些密码的实现已打补丁，以提供针对潜在攻击的部分（但非完全）缓解措施。

如果要更改 Go HTTPS 服务器使用的密码套件——无论是包含默认未使用的弱密码套件，还是移除默认使用的某些密码——都可以通过 `tls.Config.CipherSuites` 字段来实现。

例如，如果您想使用默认密码列表但 *省略 CBC 密码*，可以这样配置您的 `tls.Config`：

```
tlsConfig := &tls.Config{
    CipherSuites: []uint16{
        tls.TLS_AES_128_GCM_SHA256,
        tls.TLS_AES_256_GCM_SHA384,
        tls.TLS_CHACHA20_POLY1305_SHA256,
        tls.TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256,
        tls.TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384,
        tls.TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256,
        tls.TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384,
        tls.TLS_ECDHE_RSA_WITH_CHACHA20_POLY1305_SHA256,
        tls.TLS_ECDHE_ECDSA_WITH_CHACHA20_POLY1305_SHA256,
    },
}
```

Go 将在运行时根据密码安全性、性能以及客户端/服务器硬件支持，自动选择实际使用的这些密码套件中的 *哪些*。

还需要注意（这也很有趣）的是，如果协商了 TLS 1.3 连接，则会忽略 `tls.Config.CipherSuites`。原因是 Go 支持用于 TLS 1.3 连接的所有密码套件都被认为是 *安全* 的，因此提供配置机制的意义不大。

基本上，使用 `tls.Config.CipherSuites` 设置自定义支持的密码套件列表仅会影响 TLS 1.0-1.2 连接。因此，在上述示例中，其实没有必要包含 TLS 1.3 特定的密码套件，可以将其简化为：

```
tlsConfig := &tls.Config{
	CipherSuites: []uint16{
		tls.TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256,
		tls.TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384,
		tls.TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256,
		tls.TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384,
		tls.TLS_ECDHE_RSA_WITH_CHACHA20_POLY1305_SHA256,
		tls.TLS_ECDHE_RSA_WITH_CHACHA20_POLY1305_SHA256,
	},
}
```

**重要：** 限制支持的密码套件可能意味着使用某些旧版浏览器的用户将无法访问您的网站。安全性与向后兼容性之间需要取得平衡，正确的决策将取决于您的用户群通常使用的技术。Mozilla 针对现代、中级和旧版浏览器推荐的配置可能会帮助您在此做出决策。

## 连接超时

让我们花点时间通过添加一些超时设置来提高服务器的恢复能力，如下所示：

```
File: cmd/web/main.go

package main

...

func main() {
    ...

    tlsConfig := &tls.Config{
        CurvePreferences: []tls.CurveID{tls.X25519, tls.CurveP256},
    }

    srv := &http.Server{
        Addr:         *addr,
        Handler:      app.routes(),
        ErrorLog:     slog.NewLogLogger(logger.Handler(), slog.LevelError),
        TLSConfig:    tlsConfig,

        // Add Idle, Read and Write timeouts to the server.
        IdleTimeout:  time.Minute,
        ReadTimeout:  5 * time.Second,
        WriteTimeout: 10 * time.Second,
    }

    logger.Info("starting server", "addr", srv.Addr)

    err = srv.ListenAndServeTLS("./tls/cert.pem", "./tls/key.pem")
    logger.Error(err.Error())
    os.Exit(1)
}

...
```

所有这三个超时设置 — *空闲超时*、*读取超时* 和 *写入超时* — 都是服务器范围的设置，作用于底层连接，并适用于所有请求，不论其处理程序或 URL 如何。

## IdleTimeout 设置

默认情况下，Go 在所有已接受的连接上启用保持连接（keep-alive）。这有助于减少延迟（尤其是 HTTPS 连接），因为客户端可以重用同一连接发送多个请求，而无需重复 TLS 握手。

默认情况下，保持连接的连接会在几分钟后自动关闭（确切时间取决于您的操作系统）。这有助于清理用户意外断开的连接——例如，由于客户端断电。

无法 *增加* 此默认值（除非您自己实现 `net.Listener`），但可以通过 `IdleTimeout` 设置将其 *减少*。在我们的示例中，我们将 `IdleTimeout` 设置为 1 分钟，这意味着所有保持连接的连接将在 1 分钟无活动后自动关闭。

## ReadTimeout 设置

在我们的代码中，我们还将 `ReadTimeout` 设置为 5 秒。这意味着，如果请求首次被接受后 5 秒钟仍在读取请求头或请求体，Go 将关闭底层连接。由于这是对连接的“硬”关闭，用户不会收到任何 HTTP(S) 响应。

设置较短的 `ReadTimeout` 时期有助于缓解来自慢客户端攻击（例如 Slowloris）的风险，否则此类攻击可能通过发送部分、不完整的 HTTP(S) 请求无限期保持连接打开。

> **重要：** 如果设置了 `ReadTimeout` 但未设置 `IdleTimeout`，则 `IdleTimeout` 将默认使用与 `ReadTimeout` 相同的设置。例如，如果将 `ReadTimeout` 设置为 3 秒，则副作用是所有保持连接的连接也将在 3 秒无活动后关闭。通常，我的建议是避免任何歧义，并始终为服务器设置显式的 `IdleTimeout` 值。

## WriteTimeout 设置

`WriteTimeout` 设置将在经过给定时间段（在我们的代码中为 10 秒）后尝试向连接写入数据时关闭底层连接。但其行为会略有不同，具体取决于所使用的协议。

- 对于 HTTP 连接，如果在 *读取请求头* 完成后 10 秒钟才向连接写入数据，Go 将关闭底层连接，而不是写入数据。
- 对于 HTTPS 连接，如果在请求 *首次被接受* 后 10 秒钟才向连接写入数据，Go 将关闭底层连接，而不是

