

## 附加信息

## 堆栈跟踪

你可以使用 `debug.Stack()` 函数获取一个 *堆栈跟踪*，它概述了应用程序中 *当前 goroutine* 的执行路径。将其作为日志条目的属性包含在内，有助于调试错误。

如果你愿意，可以更新 `serverError()` 方法，使其在日志条目中包含堆栈跟踪，如下所示：

```
package main

import (
	"net/http"
	"runtime/debug"
)

func (app *application) serverError(w http.ResponseWriter, r *http.Request, err error) {
	var (
		method = r.Method
		uri    = r.URL.RequestURI()
		// Use debug.Stack() to get the stack trace. This returns a byte slice, which
		// we need to convert to a string so that it's readable in the log entry.
		trace = string(debug.Stack())
	)

	// Include the trace in the log entry.
	app.logger.Error(err.Error(), "method", method, "uri", uri, "trace", trace)

	http.Error(w, http.StatusText(http.StatusInternalServerError), http.StatusInternalServerError)
}
```

日志条目输出则类似这样（为便于阅读，已添加换行）：

```
time=2024-03-18T11:29:23.000+00:00 level=ERROR msg="open . /ui/html/pages/home.tmpl:
no such file or directory" method=GET uri=/ trace="goroutine 6 [running]:\nruntime/debug.Stack()\n\t/usr/local/go/src/runtime/debug/stack.go:24 +0x5e\nmain.(*application).serverError(0xc00006c048, {0x8221b0, 0xc0000f40e0}, 0x37,\n{0x820600, 0xc0000ab\n5c0})\n\t/home/alex/code/snippetbox/cmd/web/handlers.go:14 +0x74\nmain.(*application)
.home(0x107, {0x8221b02}, {0xc0000f40e0}, 0xc0000fe000)\n\t/home/alex/code/snippetbo
x/cmd/web/handlers.go:24 +0x16a\nnet/http.HandlerFunc.ServeHTTP(0x4459e0?, {0x8221b\n0?, 0xc0000f40e0?}, 0xc65c7a?)\n\t/usr/local/go/src/net/http/server.go:2136 +0x29\n\nnet/http.(*ServeMux).ServeHTTP(0xa74fde0, {0x8221b0, 0xc0000f40e0}, 0xc0000fe000)\n\n\t/usr/local/go/src/net/http/server.go:2514 +0x142\nnet/http.serverHandler.ServeHTT
P({0xc0000aaf00?}, {0x8221b02}, {0xc0000f40e0?}, 0x6?)\n\t/usr/local/go/src/net/http/
server.go:2938 +0x8be\nnet/http.(*conn).serve(0xc0000c0120, {0xc00029e0, 0xc0000aae10}
)\n\t/usr/local/go/src/net/http/server.go:2009 +0x5f4\ncreated by net/http.(*Server).
Serve in goroutine 1\n\t/usr/local/go/src/net/http/server.go:3086 +0x5cb\n"
```

## 隔离应用程序路由

在重构代码时，还有一项更改值得进行。

我们的 main() 函数开始变得有些拥挤，为了保持清晰和专注，我想将应用程序的路由声明移动到一个独立的 routes.go 文件中，如下所示：

```
$ touch cmd/web/routes.go
```

```
File: cmd/web/routes.go

package main

import "net/http"

// The routes() method returns a servemux containing our application routes.
func (app *application) routes() *http.ServeMux {
	mux := http.NewServeMux()

	fileServer := http.FileServer(http.Dir("./ui/static/"))
	mux.Handle("GET /static/", http.StripPrefix("/static", fileServer))

	mux.HandleFunc("GET /{$}", app.home)
	mux.HandleFunc("GET /snippet/view/{id}", app.snippetView)
	mux.HandleFunc("GET /snippet/create", app.snippetCreate)
	mux.HandleFunc("POST /snippet/create", app.snippetCreatePost)

	return mux
}
```

然后我们可以更新 main.go 文件以使用这个：

```
File: cmd/web/main.go

package main

...

func main() {
	addr := flag.String("addr", ":4000", "HTTP network address")
	flag.Parse()

	logger := slog.New(slog.NewTextHandler(os.Stdout, nil))

	app := &application{
		logger: logger,
	}

	logger.Info("starting server", "addr", *addr)

	// Call the new app.routes() method to get the servemux containing our routes,
	// and pass that to http.ListenAndServe().
	err := http.ListenAndServe(*addr, app.routes())
	logger.Error(err.Error())
	os.Exit(1)
}
```

这样要整洁得多。我们应用程序的路由现在已被隔离并封装在 app.routes() 方法中，而我们的 main() 函数的职责仅限于：

- 解析应用程序的运行时配置设置；
- 为处理程序建立依赖项；以及
- 运行 HTTP 服务器。

## 数据库驱动的响应

为了让我们的 Snippetbox Web 应用程序真正有用，我们需要一个存储（或持久化）用户输入数据的地方，并能在运行时动态查询此数据存储。

我们可以为应用程序使用许多不同的数据存储——每种都有不同的优缺点——但我们将选择流行的关系型数据库 MySQL。

> 注意：本书此部分中的所有通用代码模式也适用于 PostgreSQL 或 SQLite 等其他数据库。如果你正在跟进并更愿意使用替代数据库，可以使用，但我建议现在先使用 MySQL 来了解一切如何运作，并在读完本书后将数据库更换作为练习练习。

在本节中你将学习如何：

- 安装数据库驱动程序，作为 MySQL 和你的 Go 应用程序之间的“中间人”。
- 从你的 Web 应用程序连接到 MySQL（具体来说，你将学习如何建立可重用连接池）。
- 创建一个独立的 models 包，以便你的数据库逻辑可重用并与 Web 应用程序解耦。
- 使用 Go 的 database/sql 包中的相应函数执行不同类型的 SQL 语句，以及如何避免可能导致服务器资源耗尽的常见错误。
- 通过正确使用占位符参数防止 SQL 注入攻击。
- 使用事务，以便你可以在一个原子操作中执行多个 SQL 语句。

## 设置 MySQL

如果你正在跟进，现在需要在计算机上安装 MySQL。官方 MySQL 文档包含所有操作系统的全面安装说明，但如果你使用 Mac OS，应该能够使用以下命令安装：

```bash
$ brew install mysql
```

或者如果你使用支持 apt 的 Linux 发行版（如 Debian 和 Ubuntu），可以使用以下命令安装：

```bash
$ sudo apt install mysql-server
```

在安装 MySQL 期间，你可能会被要求为 root 用户设置密码。如果设置了，请记得记住它；下一步会用到它。

## 脚手架数据库

安装 MySQL 后，你应该能够在终端中以 root 用户身份连接到它。执行此操作的命令取决于你安装的 MySQL 版本。对于 MySQL 5.7 及更高版本，你可以通过键入以下内容来连接：

```bash
$ sudo mysql
mysql>
```

但如果不起作用，请尝试以下命令，输入安装期间设置的密码。

```bash
$ mysql -u root -p
Enter password:
mysql>
```

连接后，我们首先需要在 MySQL 中建立一个数据库来存储项目的所有数据。将以下命令复制并粘贴到 mysql 提示符中，以使用 UTF8 编码创建一个新的 snippetsbox 数据库。

```
-- Create a new UTF-8 `snippetbox` database.
CREATE DATABASE snippetbox CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
-- Switch to using the `snippetbox` database.
USE snippetbox;
```

然后复制并粘贴以下 SQL 语句，创建一个新的 `snippets` 表来存储我们应用程序的文本片段：

```
-- Create a `snippets` table.
CREATE TABLE snippets (
 id INTEGER NOT NULL PRIMARY KEY AUTO_INCREMENT,
 title VARCHAR(100) NOT NULL,
 content TEXT NOT NULL,
 created DATETIME NOT NULL,
 expires DATETIME NOT NULL
);
-- Add an index on the created column.
CREATE INDEX idx_snippets_created ON snippets(created);
```

此表中的每条记录都将有一个整型 `id` 字段，它将作为文本片段的唯一标识符。它还将有一个短文本 `title`，而片段内容本身将存储在 `content` 字段中。我们还将保留关于片段 `created` 和 `expires` 时间的一些元数据。

我们还可以向 `snippets` 表中添加一些占位符条目（我们将在接下来的几章中使用）。我将使用一些短俳句作为文本片段的内容，但它们包含什么并不重要。

```
-- Add some dummy records (which we'll use in the next couple of chapters).
INSERT INTO snippets (title, content, created, expires) VALUES (
 'An old silent pond',
 'An old silent pond...\nA frog jumps into the pond,\nSplash! Silence again.\n\n– Matsuo Bashō',
 UTC_TIMESTAMP(),
 DATE_ADD(UTC_TIMESTAMP(), INTERVAL 365 DAY)
);
INSERT INTO snippets (title, content, created, expires) VALUES (
 'Over the wintry forest',
 'Over the wintry\nforest, winds howl in rage\nwith no leaves to blow.\n\n– Natsume Soseki',
 UTC_TIMESTAMP(),
 DATE_ADD(UTC_TIMESTAMP(), INTERVAL 365 DAY)
);
INSERT INTO snippets (title, content, created, expires) VALUES (
 'First autumn morning',
 'First autumn morning\n\nthe mirror I stare into\nshows my father''s face.\n\n– Murakami Kijo',
 UTC_TIMESTAMP(),
 DATE_ADD(UTC_TIMESTAMP(), INTERVAL 7 DAY)
);
```

