
### 模拟依赖项

现在我们已经解释了测试 Web 应用程序的一些通用模式，在本章中，我们将变得更加严肃，为我们的 `showSnippet` 处理器和 `GET /snippet/:id` 路由编写一些测试。

但首先，让我们聊聊依赖项。

在整个项目中，我们通过 `application` 结构体将依赖注入到处理器中，它目前看起来如下：

```go
type application struct {
    errorLog      *log.Logger
    infoLog       *log.Logger
    session       *sessions.Session
    snippets      *mysql.SnippetModel
    templateCache map[string]*template.Template
    users         *mysql.UserModel
}
```

在测试时，模拟（mock）这些依赖项有时比与生产应用程序中使用完全相同的依赖项是有意义的。

例如，在上一章中，我们使用向 `ioutil.Discard` 消息的日志器模拟了 `errorLog` 和 `infoLog` 依赖项，而不是我们在生产应用程序中使用的 `os.Stdout` 和 `os.Stderr` 流：

```go
func newTestApplication(t *testing.T) *application {
    return &application{
        errorLog: log.New(ioutil.Discard, "", 0),
        infoLog: log.New(ioutil.Discard, "", 0),
    }
}
```

模拟这些项并写入 `ioutil.Discard` 的原因是为了避免在运行 `go test -v` 时用不必要的日志消息填满我们的测试输出。

**注意：** 根据你的背景和编程经验，你可能不认为这些日志器是模拟对象。你可能把它们命名为 fakes（伪造）、stubs（存根）或其他完全不同的名称。但名称并不重要——不同的人对它们的称呼不同。重要的是，为了测试之目的，我们正在使用与生产对象暴露相同接口的东西。

我们认为有意义可以进行模拟的另外两个依赖项是 `mysql.SnippetModel` 和 `mysql.UserModel` 数据库模型。通过创建它们的模拟对象，我们就可以在不需要设置整个 MySQL 数据库实例的情况下测试处理器的行为。

### 模拟数据库模型

如果你正在跟着操作，请创建一个新的 `pkg/models/mock` 包以及两个新的 `snippets.go` 和 `users.go` 文件来存放数据库模型模拟对象，如下所示：

```bash
$ mkdir pkg/models/mock
$ touch pkg/models/mock/snippets.go
$ touch pkg/models/mock/users.go
```

让我们从创建 `mysql.SnippetModel` 的模拟对象开始。为了做到，我们将创建一个简单的结构体，实现与我们生产 `mysql.SnippetModel` 相同的方法，但让这些方法返回一些固定的虚拟数据。

```go
File: pkg/models/mock/snippets.go
package mock

import (
    "time"
    "alexedwards.net/snippetbox/pkg/models"
)

var mockSnippet = &models.Snippet{
    ID: 1,
    Title: "An old silent pond",
    Content: "An old silent pond...",
    Created: time.Now(),
    Expires: time.Now(),
}

type SnippetModel struct{}

func (m *SnippetModel) Insert(title, content, expires string) (int, error) {
    return 1, nil
}

func (m *SnippetModel) Get(id int) (*models.Snippet, error) {
    return mockSnippet, nil
}

func (m *SnippetModel) Latest() ([]*models.Snippet, error) {
    return []*models.Snippet{mockSnippet}, nil
}

func (m *SnippetModel) Delete(id int) error {
    return nil
}
```

让我们对 `mysql.UserModel` 执行同样的操作：

```go
File: pkg/models/mock/users.go
package mock

import (
    "time"
    "alexedwards.net/snippetbox/pkg/models"
)

var mockUser = &models.User{
    ID:    1,
    Name:  "Alice",
    Email: "alice@example.com",
    Created: time.Now(),
}

type UserModel struct{}

func (m *UserModel) Insert(name, email string) (int, error) {
    return 1, nil
}

func (m *UserModel) Authenticate(email, password string) (int, error) {
    if email == "alice@example.com" && password == "password" {
        return 1, nil
    }
    return 0, models.ErrAuthentication
}

func (m *UserModel) Get(id int) (*models.User, error) {
    return mockUser, nil
}

func (m *UserModel) QuerySearch() ([]*models.User, error) {
    return []*models.User{mockUser}, nil
}

func (m *UserModel) Delete(id int) error {
    return nil
}
```

### 初始化模拟项

对于下一步，让我们回到 `testutils_test.go` 并更新 `newTestApplication()` 函数，使其创建一个包含必要依赖的应用程序结构体。

```go
func newTestApplication(t *testing.T) *application {
    // 创建模板缓存。
    templateCache, err := newTemplateCache("../ui/")
    if err != nil {
        t.Fatal(err)
    }

    // 创建会话实例，设置与生产环境相同。
    session := sessions.New([]byte("3dSm5MyfgFH7k"))
    session.Lifetime = 12 * time.Hour
    session.Secure = true

    // 初始化依赖，日志器和
    // 数据库模型使用模拟对象。
    return &application{
        errorLog:      log.New(ioutil.Discard, "", 0),
        infoLog:       log.New(ioutil.Discard, "", 0),
        session:       session,
        snippets:      &mock.SnippetModel{},
        templateCache: templateCache,
        users:         &mock.UserModel{},
    }
}
```

当你运行测试时，工作目录将被设置为当前执行测试的包目录。因此，如果你在测试中读取任何文件，你需要确保文件路径是相对于该特定文件的。

如果你现在尝试运行测试，它将失败并显示以下消息：

```bash
$ go test ./cmd/web
### alexewwards.net/snippetbox/cmd/web [alexewwards.net/snippetbox/cmd/web.test]
cmd/web/testutilis_test.go:28:3: cannot use mock.SnippetModel literal (type *mock.SnippetModel
cmd/web/testutilis_test.go:30:3: cannot use mock.UserModel literal (type *mock.U
FAIL alexewwards.net/snippetbox/cmd/web [build failed]
```

发生这种情况的原因是我们的应用程序结构体期望 `mysql.SnippetModel` 和 `mysql.UserModel` 指针，但我们实际上正在尝试使用 `mock.SnippetModel` 和 `mock.UserModel` 指针。

解决此问题的惯用方法是更改我们的应用程序结构体，使其使用接口，接口可以由我们的模拟模型和生产数据库模型满足。

提示：如果你不熟悉 Go 中接口（interfaces）的概念，那么这篇博客文章有一非常很好的介绍，我建议阅读一下。

一种有助于保持代码简单的良好模式是在应用程序结构体（struct）中内联定义接口，如下：

```go
File: cmd/web/main.go
package main

import (
    "crypto/tls"
    "database/sql"
    "flag"
    "html/template"
    "log"
    "net/http"
    "os"
    "time"
    alexedwards.net/snippet/pkg/models" // 新导入
    "alexedwards.net/snippet/pkg/models/mysql"
    github.com/go-sql-driver/mysql
    "github.com/golangcollege/sessions"
)

type contextKey string

var contextKeyUser = contextKey("user")

type application struct {
    errorLog *log.Logger
    infoLog *log.Logger
    session *sessions.Session
    snippets interface {
        Insert(string, string, string) (int, error)
        Get(int) (*models.Snippet, error)
        Latest(([])*models.Snippet, error)
    }
    templateCache map[string]*template.Template
    users interface {
        Insert(string, string, string) error
        Authenticate(string, string) (int, error)
        Get(int) (*models.User, error)
    }
}
```

现在如果你尝试运行测试，一切都应该能够正常工作。

```bash
$ go test ./cmd/web/
alexedwards.net/snippetbox/cmd/web 0.027s
```

让我们花一点时间停下来，反思一下我们刚刚的操作。

我们更新了应用程序结构体，使其不再使用 `snippets` 和具体类型 `*mysql.SnippetModel` 和 `mysql.UserModel`，而是改用接口。

只要一个对象具有满足接口所需的方法，我们就可以在“生产环境”数据库模型（位于 `pkg/models/mysql` 包下）和模拟数据库模型（位于 `pkg/models/mock` 包下）中使用它们来满足接口，因此我们现在可以交叉使用它们。

### 测试 showSnippet 处理程序

现在一切都已准备就绪，让我们开始为我们的 `GET /snippet/:id` 路由编写端到端测试，该路由使用了这些模拟依赖项。

作为测试的一部分，我们 `showSnippet` 处理程序中的代码将调用 `mock.SnippetModel.Get()` 方法。提醒一下，除非 snippet ID 为 1，否则该模拟模型将返回 `models.ErrNoRecord` —— 它将返回以下模拟片段：

```go
var mockSnippet = &models.Snippet{
    ID: 1,
    Title: "An old silent pond",
    Content: "An old silent pond...",
    Created: time.Now(),
    Expires: time.Now(),
}
```

具体来说，我们想要测试的是：

- 对于请求 `GET /snippet/1`，我们收到 `200 OK` 响应，并在 HTML 响应体中包含相关的模拟片段。
- 对于所有其他 `GET /snippet/*` 的请求，我们应该收到 `404 Not Found` 响应。

打开 `cmd/web/handlers_test.go` 文件并创建一个新的 `TestShowSnippet` 测试：

```go
File: cmd/web/handlers_test.go
package main

import (
    "bytes" // 新导入
    "net/http"
    "testing"
)

...

func TestShowSnippet(t *testing.T) {
    // 创建我们应用程序结构体的新实例，该实例使用了模拟的依赖项。
    app := newTestApplication(t)

    // 建立一个新的测试服务器来运行端到端测试。
    ts := newTestServer(t, app.routes())
    defer ts.Close()

    // 设置表驱动测试，以检查应用程序对不同 URL
    // 发送的响应。
    tests := []struct {
        name     string
        urlPath  string
        wantCode int
        wantBody []byte
    }{
        {"Valid ID", "snippet/1", http.StatusOK, []byte("An old silent pond.")},
        {"Non-existent ID", "snippet/2", http.StatusNotFound, nil},
        {"Negative ID", "snippet/-1", http.StatusNotFound, nil},
        {"Decimal ID", "snippet/1.23", http.StatusNotFound, nil},
        {"String ID", "snippet/foo", http.StatusNotFound, nil},
        {"Empty ID", "/snippet/", http.StatusNotFound, nil},
        {"Trailing slash", "/snippet/1", http.StatusNotFound, nil},
    }

    for _, tt := range tests {
        t.Run(tt.name, func(t *testing.T) {
```

当你再次运行测试时，所有测试都应该通过，并且你会看到包含新的 `TestShowSnippet` 测试的输出，看起来类似于所示：

```bash
$ go test -v ./cmd/web/
=== RUN TestPing
PASS: TestPing (0.01s)
=== RUN TestShowSnippet
=== RUN TestShowSnippet/Valid_ID
=== RUN TestShowSnippet/Non-existent_ID
=== RUN TestShowSnippet/Negative_ID
=== RUN TestShowSnippet/Decimal_ID
=== RUN TestShowSnippet/String_ID
=== RUN TestShowSnippet/Empty_ID
=== RUN TestShowSnippet/Trailing_slash
PASS: TestShowSnippet (0.00s)
PASS: TestShowSnippet/Valid_ID (0.00s)
PASS: TestShowSnippet/Non-existent_ID (0.00s)
PASS: TestShowSnippet/Negative_ID (0.00s)
PASS: TestShowSnippet/Decimal_ID (0.00s)
PASS: TestShowSnippet/String_ID (0.00s)
PASS: TestShowSnippet/Empty_ID (0.00s)
```
