
> 注：根据您的背景和编程经验，您可能不会将此日志记录器视为模拟对象。您可能会将其称为假对象、存根或其他完全不同的东西。但名称并不重要——不同的人对它们有不同的称呼。重要的是，我们使用的东西暴露了与生产对象相同的接口，用于测试目的。

另两个值得我们模拟的依赖是 models.SnippetModel 和 models.UserModel 数据库模型。通过为这些创建模拟对象，我们可以在不需要设置完整的 MySQL 数据库测试实例的情况下，测试我们处理程序的行为。

## 模拟数据库模型

如果您在跟随本教程，请创建一个新的 internal/models/mocks 包，其中包含 snippets.go 和 user.go 文件，用于存放数据库模型模拟对象，如下所示：

```
$ mkdir internal/models/mocks
$ touch internal/models/mocks/snippets.go
$ touch internal/models/mocks/users.go
```

让我们首先创建 models.SnippetModel 的模拟对象。为此，我们将创建一个简单的结构体，它实现与生产 models.SnippetModel 相同的方法，但这些方法将返回一些固定的虚拟数据，而不是实际数据。

```
File: internal/models/mocks/snippets.go

package mocks

import (
	"time"

	"snippetbox.alexedwards.net/internal/models"
)

var mockSnippet = models.Snippet{
	ID:      1,
	Title:   "An old silent pond",
	Content: "An old silent pond...",
	Created: time.Now(),
	Expires: time.Now(),
}

type SnippetModel struct{}

func (m *SnippetModel) Insert(title string, content string, expires int) (int, error) {
	return 2, nil
}

func (m *SnippetModel) Get(id int) (models.Snippet, error) {
	switch id {
	case 1:
		return mockSnippet, nil
	default:
		return models.Snippet{}, models.ErrNoRecord
	}
}

func (m *SnippetModel) Latest() ([]models.Snippet, error) {
	return []models.Snippet{mockSnippet}, nil
}
```

让我们对我们的 `models.UserModel` 也做同样的操作，如下所示：

```
File: internal/models/mocks/users.go

package mocks

import (
	"snippetbox.alexedwards.net/internal/models"
)

type UserModel struct{}

func (m *UserModel) Insert(name, email, password string) error {
	switch email {
	case "dupe@example.com":
		return models.ErrDuplicateEmail
	default:
		return nil
	}
}

func (m *UserModel) Authenticate(email, password string) (int, error) {
	if email == "alice@example.com" && password == "pa$word" {
		return 1, nil
	}

	return 0, models.ErrInvalidCredentials
}

func (m *UserModel) Exists(id int) (bool, error) {
	switch id {
	case 1:
		return true, nil
	default:
		return false, nil
	}
}

```

## 初始化模拟对象

在构建的下一步中，让我们回到 `testutils_test.go` 文件，更新 `newTestApplication()` 函数，以便它创建一个带有测试所需所有依赖项的 `application` 结构体。

```
File: cmd/web/testutils_test.go

package main

import (
	"bytes"
	"io"
	"log/slog"
	"net/http"
	"net/http/cookiejar"
	"net/http/httptest"
	"testing"
	"time" // New import

	"snippetbox.alexedwards.net/internal/models/mocks" // New import

	"github.com/alexedwards/scs/v2" // New import
	"github.com/go-playground/form/v4" // New import
)

func newTestApplication(t *testing.T) *application {
	// Create an instance of the template cache.
	templateCache, err := newTemplateCache()
	if err != nil {
		t.Fatal(err)
	}

	// And a form decoder.
	formDecoder := form.NewDecoder()

	// And a session manager instance. Note that we use the same settings as
	// production, except that we don't set a Store for the session manager.
	// If no store is set, the SCS package will default to using a transient
	// in-memory store, which is ideal for testing purposes.
	sessionManager := scs.New()
	sessionManager.Lifetime = 12 * time.Hour
	sessionManager.Cookie.Secure = true

	return &application{
		logger:  slog.New(slog.NewTextHandler(io.Discard, nil)),
		snippets: &mocks.SnippetModel{}, // Use the mock.
		users:   &mocks.UserModel{},     // Use the mock.
		templateCache: templateCache,
		formDecoder:   formDecoder,
		sessionManager: sessionManager,
	}
}
...
```

如果您现在尝试运行测试，编译将失败并出现以下错误：

```
$ go test ./cmd/web
# snippetbox.alexedwards.net/cmd/web [snippetbox.alexedwards.net/cmd/web.test]
cmd/web/testutils_test.go:40:19: cannot use &mocks.SnippetModel{} (value of type *mocks.SnippetModel) as type *models.Snippet
cmd/web/testutils_test.go:41:19: cannot use &mocks.UserModel{} (value of type *mocks.UserModel) as type *models.UserModel in
FAIL	snippetbox.alexedwards.net/cmd/web [build failed]
FAIL
```

发生这种情况是因为我们的 application 结构体期望指向 models.SnippetModel 和 models.UserModel 实例的指针，但我们却试图使用指向 mocks.SnippetModel 和 mocks.UserModel 实例的指针。

惯用的修复方法是更改我们的 application 结构体，使其使用由模拟对象和生产数据库模型都满足的接口。

> 提示：如果您不熟悉 Go 中接口的概念，那么我推荐阅读这篇博客文章中的介绍。

为此，让我们回到我们的 internal/models/snippets.go 文件，创建一个新的 SnippetModelInterface 接口类型，用于描述我们实际 SnippetModel 结构体所拥有的方法。

```
File: internal/models/snippets.go

package models

import (
	"database/sql"
	"errors"
	"time"
)

type SnippetModelInterface interface {
	Insert(title string, content string, expires int) (int, error)
	Get(id int) (Snippet, error)
	Latest() ([]Snippet, error)
}

...
```

让我们也对我们的 UserModel 结构体做同样的操作：

```
File: internal/models/users.go

package models

import (
    "database/sql"
    "errors"
    "strings"
    "time"

    "github.com/go-sql-driver/mysql"
    "golang.org/x/crypto/bcrypt"
)

type UserModelInterface interface {
    Insert(name, email, password string) error
    Authenticate(email, password string) (int, error)
    Exists(id int) (bool, error)
}

...
```

现在我们已经定义了这些接口类型，让我们更新 application 结构体，使用它们而不是具体的 SnippetModel 和 UserModel 类型。如下所示：

```
File: cmd/web/main.go

package main

import (
    "crypto/tls"
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

type application struct {
    logger      *slog.Logger
    snippets    models.SnippetModelInterface // Use our new interface type.
    users       models.UserModelInterface    // Use our new interface type.
    templateCache map[string]*template.Template
    formDecoder *form.Decoder
    sessionManager *scs.SessionManager
}

...
```

如果您现在再次尝试运行测试，一切应该都能正常工作。

```
$ go test ./cmd/web/
ok   snippetbox.alexedwards.net/cmd/web   0.008s
```

让我们花一点时间停下来，回顾一下我们刚刚所做的事情。

我们更新了 application 结构体，使 snippets 和 users 字段不再具有具体的 *models.SnippetModel 和 *models.UserModel 类型，而是使用接口。

只要某个类型具有满足接口所需的方法，我们就可以在 application 结构体中使用它们。我们的“真实”数据库模型（如 models.SnippetModel）和模拟数据库模型（如 mocks.SnippetModel）都满足这些接口，因此我们现在可以互换使用它们。

## 测试 snippetView 处理程序

一切准备就绪后，让我们开始为我们的 snippetView 处理程序编写端到端测试，该处理程序使用这些模拟依赖项。

作为这项测试的一部分，我们的 snippetView 处理程序中的代码将调用 mock.SnippetModel.Get() 方法。为了提醒您，除非 snippet ID 为 1，否则此模拟模型方法会返回 models.ErrNoRecord —— 当 ID 为 1 时，它将返回以下模拟 snippet：

```
var mockSnippet = models.Snippet{
  ID:      1,
  Title:   "An old silent pond",
  Content: "An old silent pond...",
  Created: time.Now(),
  Expires: time.Now(),
}
```

具体来说，我们想要测试：

- 1. 对于请求 GET /snippet/view/1，我们收到 200 OK 响应，且相关模拟 snippet 包含在 HTML 响应体中。

- 2. 对于所有其他 GET /snippet/view/* 请求，我们应该收到 404 Not Found 响应。

对于第一部分，我们想要检查请求体是否包含一些特定的
