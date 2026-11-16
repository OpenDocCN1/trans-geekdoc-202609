
```
File: cmd/web/handlers_test.go

package main

import (
	"bytes"
	"io"
	"log/slog" // New import
	"net/http"
	"net/http/httptest"
	"testing"

	"snippetbox.alexedwards.net/internal/assert"
)

func TestPing(t *testing.T) {
	// Create a new instance of our application struct. For now, this just
	// contains a structured logger (which discards anything written to it).
	app := &application{
		logger: slog.New(slog.NewTextHandler(io.Discard, nil)),
	}

	// We then use the httptest.NewTLSServer() function to create a new test
	// server, passing in the value returned from our app.routes() method as
	// the handler for the server. This starts up a HTTP server which listens on a
	// randomly-chosen port of your local machine for the duration of the test.
	// Notice that we defer a call to ts.Close() so that the server is shutdown
	// when the test finishes.
	ts := httptest.NewTLSServer(app.routes())
	defer ts.Close()

	// The network address that the test server is listening on is contained in
	// the ts.URL field. We can use this along with the ts.Client().Get() method
	// to make a GET /ping request against the test server. This returns a
	// http.Response struct containing the response.
	rs, err := ts.Client().Get(ts.URL + "/ping")
	if err != nil {
		t.Fatal(err)
	}

	// We can then check the value of the response status code and body using
	// the same pattern as before.
	assert.Equal(t, rs.StatusCode, http.StatusOK)

	defer rs.Body.Close()
	body, err := io.ReadAll(rs.Body)
	if err != nil {
		t.Fatal(err)
	}
	body = bytes.TrimSpace(body)

	assert.Equal(t, string(body), "OK")
}
```

关于这段代码，有几点需要指出和讨论。

- 当我们调用 `httptest.NewTLSServer()` 初始化测试服务器时，需要将 `http.Handler` 作为参数传入——该处理程序会在测试服务器收到每个 HTTPS 请求时被调用。在我们的情况中，我们传入的是 `app.routes()` 方法的返回值，这意味着对测试服务器的请求将使用我们所有的真实应用程序路由、中间件和处理程序。

这是本书前面工作的一大好处，当时我们将所有应用程序路由都隔离在 `app.routes()` 方法中。

- 如果您测试的是 HTTP（而非 HTTPS）服务器，则应改用 `httptest.NewServer()` 函数创建测试服务器。

- `ts.Client()` 方法返回测试服务器客户端（类型为 `http.Client`），我们应始终使用此客户端向测试服务器发送请求。可以配置客户端来调整其行为，我们将在本章末尾说明如何操作。

- 您可能会好奇，为什么我们只设置了应用程序结构体的 `logger` 字段，而没有设置其他字段。原因是 `logRequest` 和 `recoverPanic` 中间件需要记录器，而我们的应用程序在每个路由上都会使用这两个中间件。如果不设置这两个依赖项就尝试运行此测试，会导致 panic。

不管怎样，让我们试一下这个新测试：

```
$ go test ./cmd/web/
--- FAIL: TestPing (0.00s)
    handlers_test.go:41: got 404; want 200
    handlers_test.go:51: got: Not Found; want: OK
FAIL
FAIL    snippetbox.alexedwards.net/cmd/web    0.007s
```

如果您一直在跟进，到这一步应该会得到失败。

从测试输出可以看出，我们的 GET /ping 请求返回的状态码是 404，而不是我们期望的 200。这是因为我们尚未在路由器上注册 GET /ping 路由。

现在来修复这个问题：

```
File: cmd/web/routes.go

package main

...

func (app *application) routes() http.Handler {
    mux := http.NewServeMux()

    mux.Handle("GET /static/", http.FileServerFS(ui.Files))

    // Add a new GET /ping route.
    mux.HandleFunc("GET /ping", ping)

    dynamic := alice.New(app.sessionManager.LoadAndSave, noSurf, app.authenticate)

    mux.Handle("GET /{$}", dynamic.ThenFunc(app.home))
    mux.Handle("GET /snippet/view/{id}", dynamic.ThenFunc(app.snippetView))
    mux.Handle("GET /user/signup", dynamic.ThenFunc(app.userSignup))
    mux.Handle("POST /user/signup", dynamic.ThenFunc(app.userSignupPost))
    mux.Handle("GET /user/login", dynamic.ThenFunc(app.userLogin))
    mux.Handle("POST /user/login", dynamic.ThenFunc(app.userLoginPost))

    protected := dynamic.Append(app.requireAuthentication)

    mux.Handle("GET /snippet/create", protected.ThenFunc(app.snippetCreate))
    mux.Handle("POST /snippet/create", protected.ThenFunc(app.snippetCreatePost))
    mux.Handle("POST /user/logout", protected.ThenFunc(app.userLogoutPost))

    standard := alice.New(app.recoverPanic, app.logRequest, commonHeaders)

    return standard.Then(mux)
}
```

如果您再次运行测试，一切现在都应该能够通过。

```
$ go test ./cmd/web/
ok  snippetbox.alexedwards.net/cmd/web  0.008s
```

## 使用测试辅助函数

我们的 TestPing 测试现在运行良好。但将其中一些代码拆分为辅助函数是个不错的机会，这样随着我们向项目添加更多端到端测试，就可以重复使用这些函数了。

关于测试辅助方法放在哪里，并没有绝对的规定。如果某个辅助函数仅在特定的 `*_test.go` 文件中使用，那么将其内联在该文件的测试旁边可能更合理。在另一个极端，如果您计划在多个包的测试中使用某个辅助函数，则可能希望将其放入名为 `internal/testutils`（或类似名称）的可重用包中，以便测试文件导入。

在我们的情况中，辅助函数将用于测试整个 `cmd/web` 包中的代码，而不会用于其他地方，因此将它们放在新的 `cmd/web/testutils_test.go` 文件中似乎是合理的。

如果您一直在跟进，请现在创建这个文件...

`$ touch cmd/web/testutils_test.go`

然后添加以下代码：

```
File: cmd/web/testutils_test.go

package main

import (
	"bytes"
	"io"
	"log/slog"
	"net/http"
	"net/http/httptest"
	"testing"
)

// Create a newTestApplication helper which returns an instance of our
// application struct containing mocked dependencies.
func newTestApplication(t *testing.T) *application {
	return &application{
		logger: slog.New(slog.NewTextHandler(io.Discard, nil)),
	}
}

// Define a custom testServer type which embeds a httptest.Server instance.
type testServer struct {
	*httptest.Server
}

// Create a newTestServer helper which initializes and returns a new instance
// of our custom testServer type.
func newTestServer(t *testing.T, h http.Handler) *testServer {
	ts := httptest.NewTLSServer(h)
	return &testServer{ts}
}

// Implement a get() method on our custom testServer type. This makes a GET
// request to a given url path using the test server client, and returns the
// response status code, headers and body.
func (ts *testServer) get(t *testing.T, urlPath string) (int, http.Header, string) {
	rs, err := ts.Client().Get(ts.URL + urlPath)
	if err != nil {
		t.Fatal(err)
	}

	defer rs.Body.Close()
	body, err := io.ReadAll(rs.Body)
	if err != nil {
		t.Fatal(err)
	}

	body = bytes.TrimSpace(body)

	return rs.StatusCode, rs.Header, string(body)
}
```

基本上，这只是对本章中已编写的启动测试服务器并向其发送 GET 请求的代码进行了泛化。

让我们回到 TestPing 处理程序，利用这些新辅助函数：

```
File: cmd/web/handlers_test.go

package main

import (
	"net/http"
	"testing"

	"snippetbox.alexedwards.net/internal/assert"
)

func TestPing(t *testing.T) {
	app := newTestApplication(t)

	ts := newTestServer(t, app.routes())
	defer ts.Close()

	code, _, body := ts.get(t, "/ping")

	assert.Equal(t, code, http.StatusOK)
	assert.Equal(t, body, "OK")
}
```

同样，如果您再次运行测试，一切仍然应该能够通过。

```
$ go test ./cmd/web/
ok   snippetbox.alexedwards.net/cmd/web   0.013s
```

现在这已经非常不错了。我们已经有了一个整洁的模式来启动测试服务器并向其发送请求，在端到端测试中涵盖了我们的路由、中间件和处理程序。我们还将部分代码拆分为辅助函数，这将使编写未来的测试更快、更容易。

## Cookie 和重定向

到目前为止，本章中我们一直使用测试服务器客户端的默认设置。但我希望做一些更改，使其更适合测试我们的 Web 应用程序。具体来说：

- 我们希望客户端能够自动存储 HTTPS 响应中发送的任何 Cookie，以便在适当时将其包含在后续发送回测试服务器的请求中。在本书后面，当我们需要 Cookie 支持多个请求来测试抗 CSRF 措施时，这将很有用。

- 我们不希望客户端自动跟随重定向。相反，我们希望它返回服务器发送的第一个 HTTPS 响应，以便我们可以针对该特定请求测试响应。
