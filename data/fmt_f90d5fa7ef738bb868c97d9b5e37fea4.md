
在这段代码中：

- `/snippet/:id` 模式包含一个命名捕获 `:id`。该命名捕获的作用类似于通配符，而模式的其余部分则是字面匹配。`Pat` 会在运行时在后台将命名捕获的内容添加到 URL 查询字符串中。
- `mux.Get()` 方法用于注册 URL 模式和处理器，该处理器仅在请求为 GET HTTP 方法时才会被调用。还提供了相应的 `Post()`、`Put()`、`Delete()` 等方法。
- `Pat` 不允许你直接注册处理器函数，因此你需要使用 `http.HandlerFunc()` 适配器对其进行转换。

考虑到以上这些，让我们进入 `routes.go` 文件并更新它以使用 `Pat`：

文件：`cmd/web/routes.go`

```go
package main

import (
    "net/http"
    "github.com/bmizerany/pat" // 新的导入
    "github.com/justinas/alice"
)

func (app *application) routes() http.Handler {
    standardMiddleware := alice.New(app.recoverPanic, app.logRequest, secureHeads)
    mux := pat.New()
    mux.Get("/", http.HandlerFunc(app.home))
    mux.Get("/snippet/create", http.HandlerFunc(app.createSnippet))
    mux.Post("/snippet/create", http.HandlerFunc(app.createSnippet))
    mux.Get("/snippet/:id", http.HandlerFunc(app.showSnippet)) // 移动到了下方
    fileServer := http.FileServer(http.Dir("./static"))
    mux.Get("/static/", http.StripPrefix("/static", fileServer))
    return standardMiddleware.Then(mux)
}
```

有重要点需要指出。

- `Pat` 按照注册的顺序进行匹配。在我们的应用程序中，一个 GET `/snippet/create` 的 HTTP 请求实际上是两个路由的有效匹配——它是对 `/snippet/create` 的精确匹配，也是 `/snippet/:id` 的通配符匹配（路径中的 "create" 部分将被视为 `:id` 参数）。精确匹配优先级更高，我们需要在注册任何通配符路由之前注册精确匹配路由。
- 以尾部斜杠（`/static/`）结尾 URL 模式工作方式与 Go 内置的 `servemux` 相同。任何匹配模式开头的请求将被调度到相应的处理器。
- 模式 `/` 是特殊情况。它只会匹配 URL 路径恰好为 `/` 的请求。

考虑到这些点，我们现在还需要对 `handlers.go` 文件进行一些更改：

```go
package main

...

func (app *application) home(w http.ResponseWriter, r *http.Request) {
    // 因为 Pat 精确匹配 "/" 路径，我们现在可以移除处理器中
    // 对 r.URL.Path == "/" 的手动检查。
    s, err := app.snippets.Latest()
    if err != nil {
        app.serverError(w, err)
        return
    }
    app.render(w, r, "home.page.tmpl", &templateData{
        Snippets: s,
    })
}

func (app *application) showSnippet(w http.ResponseWriter, r *http.Request) {
    // 添加一个新的 createSnippetHandler，它现在返回一个占位符
    w.Write([]byte("Create a new snippet..."))
}

func (app *application) createSnippet(w http.ResponseWriter, r *http.Request) {
    // 对 Method == "POST" 的检查现在是多的，可以删除。
    title := "My snippet"
    content := "Some content"
    expires := 24h
    id, err := app.snippets.Insert(title, content, expires)
    if err != nil {
        app.serverError(w, err)
        return
    }
    // 修改重定向以使用新的 URL 样式 /snippet/:id
    http.Redirect(w, r, fmt.Sprintf("/snippet/%d", id), http.StatusOther)
}
```

最后，我们需要更新 `home.page.tmpl` 中的表格，以便链接也使用新的 `/snippet/:id` URL 样式。

```html
{{template "base"}}
{{define "title"}}Home{{end}}
{{define "body"}}
<h2>Latest Snippets</h2>
{{if .Snippets}}
<table>
<tr>
<th>Title</th>
<th>Created</th>
<th>ID</th>
</tr>
{{range .Snippets}}
<tr>
<td><a href="/snippet/{{.ID}}">{{.Title}}</a></td>
<td>{{.Created}}</td>
<td>{{.ID}}</td>
</tr>
{{end}}
</table>
{{else}}
<p>There's nothing to see yet!</p>
{{end}}
{{end}}
```

完成这些操作后，重启应用程序，你现在应该可以通过语义化的 URL 查看片段。例如：`http://localhost:4000/snippet/1`。

你也可以看到使用不支持的方法请求会返回 405 响应。尝试对该 URL 使用 POST 请求：

```bash
$ curl -I -X POST http://localhost:4000/snippet/1
HTTP/1.1 405 Method Allowed
Allow: HEAD, GET
Content-Type: text/plain; charset=utf-8
X-Content-Type-Options: nosniff
X-Frame-Options: deny
X-XSS-Protection: 1; mode=block
Date: Mon, 23 Jul 2018 10:10:33 GMT
Content-Length: 19
```

## 处理表单

在本书的这一部分，我们将专注于允许 Web 应用程序的用户通过 HTML 表单创建新片段，如下所示：

处理此表单的高级工作流将遵循标准的 Post-Redirect-Get 模式并如下：

- 1. 用户向 `/snippet/create` 发起 GET 请求时显示空白表单。
- 2. 用户完成表单并通过 POST 请求提交到服务器。

通过这些你将学习：

- 如何解析和访问 POST 请求发送的表单数据。
- 对表单数据进行常用检查的技术。
- 用于提示验证失败并使用之前提交的数据填充表单字段的用户友好模式。
- 如何通过在独立的复重用包中创建验证来保持处理器整洁。

### 设置表单

让我们开始创建一个 `ui/html/create.page.tmpl` 文件来存放表单的 HTML...

```bash
$ touch ui/html/create.page.tmpl
```

... 然后添加以下标记，使用我们在书中之前使用的相同模式：

```html
File: ui/html/create.page.tmpl
{{template "base" .}}
{{define "title"}}Create a New Snippet{{end}}
{{define "body"}}
<form action='/snippet/create' method='POST'>
  <div>
    <label>Title:</label>
    <input type='text' name='title'>
  </div>
  <div>
    <label>Content:</label>
    <textarea name='content'></textarea>
  </div>
  <div>
    <label>Delete in:</label>
    <input type='radio' name='expires' value='365' checked> One Year
    <input type='radio' name='expires' value='7'> One Week
    <input type='radio' name='expires' value='1'> One Day
  </div>
  <div>
    <input type='submit' value='Publish snippet'>
  </div>
</form>
{{end}}
```

```html
<h1><a href='/Snippetbox'>a></h1>
<nav>
  <a href='/Home'></a>
  <!-- 添加新表单的链接 -->
  <a href='/snippet/create'>创建片段</a>
</nav>
<section>
  {{template "body"}}
  </section>
  {{template "footer"}}
  <script src="static/js/main.js" type="text/javascript"></script>
</body>
</html>
{{end}}
{{end}}
```

最后，我们需要更新 `createSnippetForm` 处理器，使其像下面这样渲染我们的新页面：

```go
File: cmd/web/handlers.go
package main

...

func (app *application) createSnippetForm(w http.ResponseWriter, r *http.Request) {
  app.render(w, r, "create.page.tmpl", nil)
}

...
```

此时，你可以启动应用程序并在浏览器中访问 `http://localhost:4000/snippet/create`。你应该能看到一个像这样的表单：

![](img/fbb9e40b020fe1d7cb903215faaef07e_255_0.png)

### 解析表单数据

得益于之前在 RESTful 路由部分所的工作，`POST /snippets/create` 请求已经能够分发到我们的 `createSnippet` 处理器。现在我们将更新这个处理器，在提交表单时处理并使用表单数据。

从高层次来说，我们可以将其分为两个不同的步骤。

- 1. 首先，我们需要使用 `r.ParseForm()` 方法来解析请求体。这会检查请求格式是否正确，然后将表单数据存储在请求的 `r.PostForm` map 中。如果在解析请求体时遇到任何错误（例如没有请求体，或请求体太大无法处理），它将返回一个错误。`r.ParseForm()` 方法还是等幂的；可以安全地在同一个请求上多次调用，而不会产生任何副作用。
- 2. 随后，我们可以使用 `r.PostForm.Get()` 方法获取 `r.PostForm` 中包含的表单数据。例如，我们可以通过 `r.PostForm.Get("title")` 获取标题字段的值。如果表单中没有匹配的字段名，它将返回空字符串 `""`，这与我们在书中之前查询字符串参数的方式类似。

打开你的 `cmd/web/handlers.go` 文件并更新以包含以下代码：

```go
File: cmd/web/handlers.go
package main

...

func (app *application) createSnippet(w http.ResponseWriter, r *http.Request) {
    // 首先我们调用 r.ParseForm()，它将 POST 请求体中的任何数据
    // 添加到 r.PostForm map 中。这对于 PUT 和 PATCH 请求
    // 同样有效。如果有任何错误，我们将使用 app.ClientError 辅助函数
    // 向用户发送 400 Bad Request 响应。
    err := r.ParseForm()
    if err != nil {
        app.clientError(w, http.StatusBadRequest)
        return
    }

    // 使用 r.PostForm.Get() 方法从 r.PostForm map 中
    // 获取相关数据字段。
    title := r.PostForm.Get("title")
    content := r.PostForm.Get("content")
    expires := r.PostForm.Get("expires")

    // 使用表单数据在数据库中创建新的片段记录。
    id, err := app.snippets.Insert(title, content, expires)
    if err != nil {
        app.serverError(w, err)
        return
    }

    http.Redirect(w, r, fmt.Sprintf("/snippet/%d", id), http.StatusSeeOther)
}
```

好了，让我们试一下！重启应用程序并尝试用片段的标题和内容填充表单，类似于这样：

![](img/fbb9e40b020fe1d7cb903215faaef07e_258_0.png)

然后提交表单。如果一切运行正常，你应该被重定向到一个显示你新片段的页面，如下所示：

### 附加信息

#### r.Form Map

在上面的代码中，我们通过 `r.PostForm` map 访问了表单值。但另一种方法是使用（实质然不同的）`r.Form` map。

`r.PostForm` map 仅在 POST、PATCH 和 PUT 请求时被填充，并包含来自请求体的表单数据。相比之下，`r.Form` map 对于所有请求（无论其 HTTP 方法）都会被填充，并包含来自任何请求体和查询字符串参数的表单数据。因此，如果我们的表单提交到 `/snippet/create?foo=bar`，我们也可以通过调用 `r.Form.Get("foo")` 获取 `foo` 的值。注意，在发生冲突时，请求体的值将优先于查询字符串。

如果你的应用程序在 HTML 表单和 URL 中发送数据，或者不在乎参数传递的方式，那么使用 `r.Form` map 可能会很有用。但在我们这里，这些并不适用。我们期望表单数据只在请求体中发送，因此通过 `r.PostForm` 访问它们是合理的。

#### FormValue 和 PostFormValue 方法

`net/http` 包还提供了 `r.FormValue()` 和 `r.PostFormValue()` 方法。这些本质上是快捷函数，它们会替你调用 `r.ParseForm()`，然后从 `r.Form` 或 `r.PostForm` 获取相应值。我建议避免这些快捷函数，因为它们会静默忽略 `r.ParseForm()` 返回的错误。

#### 多值字段

严格来说，`r.PostForm.Get()` 方法只返回字段的第一个值。如果你想处理多个值的字段，可以使用 `r.PostForm`，如下：

```html
<input type="checkbox" name="items" value="foo">
<input type="checkbox" name="items" value="bar">
<input type="checkbox" name="items" value="baz">
```

在这种情况下，你需要处理 `url.Values` 类型。对于多值，你可以这样遍历 map：

```go
for i, item := range r.PostForm["items"] {
    fmt.Fprintf(w, "%d: %s\n", i, item)
}
```

#### 表单大小

除非你发送的是 multipart 数据（即表单具有 `enctype="multipart/form-data"` 属性），否则 POST、PATCH 请求体是有限制的。如果你想更改这个限制，可以使用 `MaxBytesReader` 函数：

```go
// 将请求体大小限制为 4096 字节
r.Body = http.MaxBytesReader(w, r.Body, 4096)
err := r.ParseForm()
if err != nil {
    http.Error(w, "Bad Request", http.StatusBadRequest)
    return
}
```
