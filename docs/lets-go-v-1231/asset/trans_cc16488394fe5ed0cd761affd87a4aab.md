
content，而不是完全等于它。让我们快速为 assert 包添加一个新的 StringContains() 函数来帮助实现这一点：

```
File: internal/assert/assert.go

package assert

import (
	"strings" // New import
	"testing"
)

...

func StringContains(t *testing.T, actual, expectedSubstring string) {
	t.Helper()

	if !strings.Contains(actual, expectedSubstring) {
		t.Errorf("got: %q; expected to contain: %q", actual, expectedSubstring)
	}
}
```

然后打开 cmd/web/handlers_test.go 文件，像这样创建一个新的 TestSnippetView 测试：

```
File: cmd/web/handlers_test.go

package main

...

func TestSnippetView(t *testing.T) {
	// Create a new instance of our application struct which uses the mocked
	// dependencies.
	app := newTestApplication(t)

	// Establish a new test server for running end-to-end tests.
	ts := newTestServer(t, app.routes())
	defer ts.Close()

	// Set up some table-driven tests to check the responses sent by our
	// application for different URLs.
	tests := []struct {
		name      string
		urlPath   string
		wantCode  int
		wantBody  string
	}{
		{
			name:   "Valid ID",
			urlPath: "/snippet/view/1",
			wantCode: http.StatusOK,
			wantBody: "An old silent pond...",
		},
		{
			name:   "Non-existent ID",
			urlPath: "/snippet/view/2",
			wantCode: http.StatusNotFound,
		},
		{
			name: "Negative ID",
			urlPath: "/snippet/view/-1",
			wantCode: http.StatusNotFound,
		},
		{
			name: "Decimal ID",
			urlPath: "/snippet/view/1.23",
			wantCode: http.StatusNotFound,
		},
		{
			name: "String ID",
			urlPath: "/snippet/view/foo",
			wantCode: http.StatusNotFound,
		},
		{
			name: "Empty ID",
			urlPath: "/snippet/view/",
			wantCode: http.StatusNotFound,
		},
	]

	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			code, _, body := ts.get(t, tt.urlPath)

			assert.Equal(t, code, tt.wantCode)

			if tt.wantBody != "" {
				assert.StringContains(t, body, tt.wantBody)
			}
		})
	}
}
```

如果再次启用 `-v` 标志运行测试，现在应该在输出中看到新的通过的 TestSnippetView 子测试：

```
$ go test -v ./cmd/web/
=== RUN   TestPing
--- PASS: TestPing (0.00s)
=== RUN   TestSnippetView
=== RUN   TestSnippetView/Valid_ID
=== RUN   TestSnippetView/Non-existent_ID
=== RUN   TestSnippetView/Negative_ID
=== RUN   TestSnippetView/Decimal_ID
=== RUN   TestSnippetView/String_ID
=== RUN   TestSnippetView/Empty_ID
--- PASS: TestSnippetView (0.01s)
    --- PASS: TestSnippetView/Valid_ID (0.00s)
    --- PASS: TestSnippetView/Non-existent_ID (0.00s)
    --- PASS: TestSnippetView/Negative_ID (0.00s)
    --- PASS: TestSnippetView/Decimal_ID (0.00s)
    --- PASS: TestSnippetView/String_ID (0.00s)
    --- PASS: TestSnippetView/Empty_ID (0.00s)
=== RUN   TestCommonHeaders
--- PASS: TestCommonHeaders (0.00s)
=== RUN   TestHumanDate
=== RUN   TestHumanDate/UTC
=== RUN   TestHumanDate/Empty
=== RUN   TestHumanDate/CET
--- PASS: TestHumanDate (0.00s)
    --- PASS: TestHumanDate/UTC (0.00s)
    --- PASS: TestHumanDate/Empty (0.00s)
    --- PASS: TestHumanDate/CET (0.00s)
PASS
ok   snippetbox.alexedwards.net/cmd/web   0.015s
```

顺便说一句，注意子测试名称是如何被规范化的吗？Go 会在测试输出中自动将子测试名称中的空格替换为下划线（任何不可打印字符也会被转义）。

## 测试 HTML 表单

在本章中，我们将为 POST /user/signup 路由添加一个端到端测试，该路由由我们的 userSignupPost 处理程序处理。

由于我们的应用程序执行反 CSRF 检查，测试此路由变得稍微复杂一些。除非请求包含有效的 CSRF 令牌和 Cookie，否则我们对 POST /user/signup 发出的任何请求都将始终收到 400 Bad Request 响应。为了绕过这个问题，我们需要在测试中模拟真实用户的工作流程，如下所示：

- 1. 发起 GET /user/signup 请求。这将返回一个响应，该响应在响应头中包含 CSRF Cookie，在响应体中包含注册页面的 CSRF 令牌。
- 2. 从 HTML 响应体中提取 CSRF 令牌。
- 3. 发起 POST /user/signup 请求，使用与步骤 1 中相同的 http.Client（这样它会自动在 POST 请求中携带 CSRF Cookie），并将 CSRF 令牌与我们要测试的其他 POST 数据一起包含在内。

让我们先向 cmd/web/testutils_test.go 文件添加一个新的辅助函数，用于从 HTML 响应体中提取 CSRF 令牌（如果存在）：

```
File: cmd/web/testutils_test.go

package main

import (
	"bytes"
	"html" // New import
	"io"
	"log/slog"
	"net/http"
	"net/http/cookiejar"
	"net/http/httptest"
	"regexp" // New import
	"testing"
	"time"

	"snippetbox.alexedwards.net/internal/models/mocks"

	"github.com/alexedwards/scs/v2"
	"github.com/go-playground/form/v4"
)

// Define a regular expression which captures the CSRF token value from the
// HTML for our user signup page.
var csrfTokenRX = regexp.MustCompile(`<input type='hidden' name='csrf_token' value='(.+)' />`)

func extractCSRFToken(t *testing.T, body string) string {
	// Use the FindStringSubmatch method to extract the token from the HTML body.
	// Note that this returns an array with the entire matched pattern in the
	// first position, and the values of any captured data in the subsequent
	// positions.
	matches := csrfTokenRX.FindStringSubmatch(body)
	if len(matches) < 2 {
		t.Fatal("no csrf token found in body")
	}

	return html.UnescapeString(matches[1])
}
...
```

> **注意：** 你可能会好奇，为什么在返回 CSRF 令牌之前要使用 `html.UnescapeString()` 函数。原因是 Go 的 `html/template` 包会自动转义所有动态渲染的数据……包括我们的 CSRF 令牌。由于 CSRF 令牌是一个 base64 编码的字符串，它可能包含 `+` 字符，这将被转义为 `&#43;`。因此，从 HTML 中提取令牌后，我们需要通过 `html.UnescapeString()` 来获取原始令牌值。

现在已经就位了，让我们回到 `cmd/web/handlers_test.go` 文件并创建一个新的 `TestUserSignup` 测试。

首先，我们将让它发起一个 `GET` `/user/signup` 请求，然后从 HTML 响应体中提取并打印出 CSRF 令牌。如下所示：

```
File: cmd/web/handlers_test.go

package main

...

func TestUserSignup(t *testing.T) {
	// Create the application struct containing our mocked dependencies and set
	// up the test server for running an end-to-end test.
	app := newTestApplication(t)
	ts := newTestServer(t, app.routes())
	defer ts.Close()

	// Make a GET /user/signup request and then extract the CSRF token from the
	// response body.
	_, body := ts.get(t, "/user/signup")
	csrfToken := extractCSRFToken(t, body)

	// Log the CSRF token value in our test output using the t.Logf() function.
	// The t.Logf() function works in the same way as fmt.Printf(), but writes
	// the provided message to the test output.
	t.Logf("CSRF token is: %q", csrfToken)
}
```

重要的是，必须使用 `-v` 标志（以启用详细输出）运行测试，才能看到来自 `t.Logf()` 函数的任何输出。

现在就去做：

```
$ go test -v -run="TestUserSignup" ./cmd/web/
=== RUN   TestUserSignup
--- handlers_test.go:81: CSRF token is: "C92tcpQpLn6aiUaf8XAonwy+YjcVnyaAa0vfkdL6vJqoNSbgaTtdBRC61PfMoGP2ojv+sZI8dSUikah3mFR
=== PASS: TestUserSignup (0.01s)
PASS
ok      snippetbox.alexedwards.net/cmd/web        0.010s
```

好的，看起来运行正常。测试正在顺利运行，并打印出我们从响应体 HTML 中提取的 CSRF 令牌。

> **注意：** 如果你在稍后立即再次运行此测试，而不更改 `cmd/web` 包中的任何内容，你将在测试输出中得到相同的 CSRF 令牌，_因为测试结果已被缓存_。

## 测试 POST 请求

现在让我们回到我们的 `cmd/web/testutils_test.go` 文件，并在我们的 `testServer` 类型上创建一个新的 `postForm()` 方法，我们可以使用它向测试服务器发送 `POST` 请求。
