

写入数据。这意味着如果你使用 HTTPS（就像我们这样做），将 `WriteTimeout` 设置为大于 `ReadTimeout` 的值是明智的。

请牢记，处理程序所做的写入会被缓冲，并在处理程序返回时一次性写入连接。因此，`WriteTimeout` 的一般理念 *并非* 防止长时间运行的处理程序，而是防止处理程序返回的数据写入耗时过长。

## 附加信息

### `ReadHeaderTimeout` 设置

`http.Server` 还提供了一个 `ReadHeaderTimeout` 设置，我们在应用程序中尚未使用它。它的工作方式与 `ReadTimeout` 类似，只不过它仅应用于 HTTP(S) 标头的读取。因此，如果将 `ReadHeaderTimeout` 设置为 3 秒，则如果请求被接受后的 3 秒钟内仍在读取请求标头，连接将被关闭。但是，即使过了 3 秒钟，读取请求体仍可以继续进行，而连接不会被关闭。

如果你想对读取请求标头应用服务器范围的限制，但在读取请求体方面希望在不同路由上实现不同的超时（可能使用 `http.TimeoutHandler()` 中间件），这会很有用。

对于我们的 Snippetbox Web 应用程序，没有任何操作需要为每个路由设置读取超时——读取所有路由的请求标头和请求体都应该能在 5 秒钟内舒适地完成，因此我们将继续使用 `ReadTimeout`。

### `MaxHeaderBytes` 设置

`http.Server` 包含一个 `MaxHeaderBytes` 字段，你可以使用它来控制服务器解析请求标头时将读取的最大字节数。默认情况下，Go 允许的最大标头长度为 1MB。

例如，如果你想将最大标头长度限制为 0.5MB，则会编写：

```
srv := &http.Server{
    Addr:      *addr,
    MaxHeaderBytes: 524288,
    ...
}
```

如果超过了 MaxHeaderBytes，则用户将自动收到 431 Request Header Fields Too Large 响应。

这里需要指出一个陷阱：Go 会始终在你设置的数值上额外添加 4096 字节的余量。如果你需要 MaxHeaderBytes 是一个精确的或非常低的数值，则需要将此因素考虑在内。

## 用户身份验证

在本书的这一部分，我们将向应用程序添加一些用户身份验证功能，以便只有已注册并登录的用户才能创建新代码片段。未登录的用户仍然可以查看代码片段，并且还可以注册一个帐户。

工作流程将如下所示：

- 1. 用户将通过访问 /user/signup 处的表单并输入其姓名、电子邮件地址和密码来注册。我们将把这些信息存储在一个新的 users 数据库表中（我们稍后将创建该表）。
- 2. 用户将通过访问 /user/login 处的表单并输入其电子邮件地址和密码来登录。
- 3. 然后我们将检查数据库，看他们输入的电子邮件和密码是否与 users 表中的某个用户匹配。如果匹配，则用户已成功通过身份验证，我们将使用键 "authenticatedUserID" 将相关的用户 id 值添加到其会话数据中。
- 4. 当收到任何后续请求时，我们可以检查用户的会话数据中是否存在 "authenticatedUserID" 值。如果存在，则我们知道用户已成功登录。我们可以一直检查此项，直到会话过期，届时用户将需要再次登录。如果会话中不存在 "authenticatedUserID"，则我们知道用户未登录。

从很多方面来说，本部分的大量内容只是以不同的方式将我们已学习的内容组合在一起。因此，这既是对你理解程度的一次良好试金石，也是对一些关键概念的提醒。

你将学习：

- 如何为用户实现基本的注册、登录和登出功能。
- 在数据库中加密和存储用户密码的安全方法。
- 使用中间件和会话验证用户是否已登录的稳健且简单直接的方法。
- 如何防止跨站点请求伪造（CSRF）攻击。

## 路由设置

让我们先通过向应用程序添加五条新路由来开始本部分，使其如下所示：

| 路由模式 | 处理程序 | 操作 |
| :--- | :--- | :--- |
| GET /{$} | home | 显示主页 |
| GET /snippet/view/{id} | snippetView | 显示特定代码片段 |
| GET /snippet/create | snippetCreate | 显示创建新代码片段的表单 |
| POST /snippet/create | snippetCreatePost | 创建新代码片段 |
| GET /user/signup | userSignup | 显示注册新用户的表单 |
| POST /user/signup | userSignupPost | 创建新用户 |
| GET /user/login | userLogin | 显示用户登录表单 |
| POST /user/login | userLoginPost | 对用户进行身份验证并登录 |
| POST /user/logout | userLogoutPost | 注销用户 |
| GET /static/ | http.FileServer | 提供特定静态文件 |

请注意，新的有状态更改的处理程序 — userSignupPost、userLoginPost 和 userLogoutPost — 都使用 POST 请求，而不是 GET。

如果你在跟随操作，请打开 handlers.go 文件，并按如下方式为五个新处理程序函数添加占位符：

```
File: cmd/web/handlers.go

package main

...

func (app *application) userSignup(w http.ResponseWriter, r *http.Request) {
	fmt.Fprintln(w, "Display a form for signing up a new user...")
}

func (app *application) userSignupPost(w http.ResponseWriter, r *http.Request) {
	fmt.Fprintln(w, "Create a new user...")
}

func (app *application) userLogin(w http.ResponseWriter, r *http.Request) {
	fmt.Fprintln(w, "Display a form for logging in a user...")
}

func (app *application) userLoginPost(w http.ResponseWriter, r *http.Request) {
	fmt.Fprintln(w, "Authenticate and login the user...")
}

func (app *application) userLogoutPost(w http.ResponseWriter, r *http.Request) {
	fmt.Fprintln(w, "Logout the user...")
}
```

完成后，让我们在 `routes.go` 文件中创建相应的路由：

```
File: cmd/web/routes.go

package main

...

func (app *application) routes() http.Handler {
	mux := http.NewServeMux()

	fileServer := http.FileServer(http.Dir("./ui/static/"))
	mux.Handle("GET /static/", http.StripPrefix("/static", fileServer))

	dynamic := alice.New(app.sessionManager.LoadAndSave)

	mux.Handle("GET /{$}", dynamic.ThenFunc(app.home))
	mux.Handle("GET /snippet/view/{id}", dynamic.ThenFunc(app.snippetView))
	mux.Handle("GET /snippet/create", dynamic.ThenFunc(app.snippetCreate))
	mux.Handle("POST /snippet/create", dynamic.ThenFunc(app.snippetCreatePost))

	// Add the five new routes, all of which use our 'dynamic' middleware chain.
	mux.Handle("GET /user/signup", dynamic.ThenFunc(app.userSignup))
	mux.Handle("POST /user/signup", dynamic.ThenFunc(app.userSignupPost))
	mux.Handle("GET /user/login", dynamic.ThenFunc(app.userLogin))
	mux.Handle("POST /user/login", dynamic.ThenFunc(app.userLoginPost))
	mux.Handle("POST /user/logout", dynamic.ThenFunc(app.userLogoutPost))

	standard := alice.New(app.recoverPanic, app.logRequest, commonHeaders)

	return standard.Then(mux)
}
```

最后，我们还需要更新 `nav.tmpl` 部分以包含新页面的导航项：

```
File: ui/html/partials/nav.tmpl

{{define "nav"}}
<nav>
  <div>
    <a href='/'>Home</a>
    <a href='/snippet/create'>Create snippet</a>
  </div>
  <div>
    <a href='/user/signup'>Signup</a>
    <a href='/user/login'>Login</a>
    <form action='/user/logout' method='POST'>
      <button>Logout</button>
    </form>
  </div>
</nav>
{{end}}
```

如果你愿意，此时可以运行应用程序，你应该会在导航栏中看到类似这样的新项目：

![](img/c3e650db0d8dfdecc0f8e34a67719f65_274_0.png)

如果你点击新链接，它们应该会以相关的占位符纯文本响应进行回复。例如，如果你点击 'Signup' 链接，你应该会看到类似这样的响应：

