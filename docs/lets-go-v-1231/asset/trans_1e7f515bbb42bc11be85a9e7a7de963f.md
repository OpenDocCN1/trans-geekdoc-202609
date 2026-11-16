

## 错误请求

要使表单提交正常工作，我们需要使用 `nosurf.Token()` 函数获取 CSRF 令牌，并将其添加到每个表单中的隐藏 `csrf_token` 字段。因此，下一步是向我们的 `templateData` 结构体添加一个新的 `CSRFToken` 字段：

```
File: cmd/web/templates.go

package main

import (
	"html/template"
	"path/filepath"
	"time"

	"snippetbox.alexedwards.net/internal/models"
)

type templateData struct {
	CurrentYear	 int
	Snippet		 models.Snippet
	Snippets	 []models.Snippet
	Form		 any
	Flash		 string
	IsAuthenticated bool
	CSRFToken	 string // Add a CSRFToken field.
}

...
```

由于注销表单可能出现在每个页面上，因此通过我们的 `newTemplateData()` 辅助函数自动将 CSRF 令牌添加到模板数据中是合理的。这意味着每次渲染页面时，它都将可用于我们的模板。

请继续按照以下方式更新 `cmd/web/helpers.go` 文件：

```
File: cmd/web/helpers.go

package main

import (
	"bytes"
	"errors"
	"fmt"
	"net/http"
	"time"

	"github.com/go-playground/form/v4"
	"github.com/justinas/nosurf" // New import
)

...

func (app *application) newTemplateData(r *http.Request) templateData {
	return templateData{
		CurrentYear: time.Now().Year(),
		Flash: app.sessionManager.PopString(r.Context(), "flash"),
		IsAuthenticated: app.isAuthenticated(r),
		CSRFToken: nosurf.Token(r), // Add the CSRF token.
	}
}

...
```

最后，我们需要更新应用程序中的所有表单，以在隐藏字段中包含此 CSRF 令牌。

如下所示：

```
File: ui/html/pages/create.tpl

{{define "title"}}Create a New Snippet{{end}}

{{define "main"}}
<form action='/snippet/create' method='POST'>
    <!-- Include the CSRF token -->
    <input type='hidden' name='csrf_token' value='{{.CSRFToken}}'>
    <div>
        <label>Title:</label>
        {{with .Form.FieldErrors.title}}
            <label class='error'>{{.}}</label>
        {{end}}
        <input type='text' name='title' value='{{.Form.Title}}'>
    </div>
    <div>
        <label>Content:</label>
        {{with .Form.FieldErrors.content}}
            <label class='error'>{{.}}</label>
        {{end}}
        <textarea name='content'>{{.Form.Content}}</textarea>
    </div>
    <div>
        <label>Delete in:</label>
        {{with .Form.FieldErrors.expires}}
            <label class='error'>{{.}}</label>
        {{end}}
        <input type='radio' name='expires' value='365' {{if (eq .Form.Expires 365)}}checked{{end}}> One Year
        <input type='radio' name='expires' value='7' {{if (eq .Form.Expires 7)}}checked{{end}}> One Week
        <input type='radio' name='expires' value='1' {{if (eq .Form.Expires 1)}}checked{{end}}> One Day
    </div>
    <div>
        <input type='submit' value='Publish snippet'>
    </div>
</form>
{{end}}
```

```
File: ui/html/pages/login.tmpl

{{define "title"}}login{{end}}

{{define "main"}}
<form action='/user/login' method='POST' novalidate>
<!-- Include the CSRF token -->
<input type='hidden' name='csrf_token' value='{{.CSRFToken}}'>
{{range .Form.NonFieldErrors}}
<div class='error'>{{.}}</div>
{{end}}
<div>
<label>Email:</label>
{{with .Form.FieldErrors.email}}
<label class='error'>{{.}}</label>
{{end}}
<input type='email' name='email' value='{{.Form.Email}}'>
</div>
<div>
<label>Password:</label>
{{with .Form.FieldErrors.password}}
<label class='error'>{{.}}</label>
{{end}}
<input type='password' name='password'>
</div>
<div>
<input type='submit' value='Login'>
</div>
</form>
{{end}}
```

```
File: ui/html/pages/signup.tmpl

{{define "title"}}Signup{{end}}

{{define "main"}}
<form action='/user/signup' method='POST' novalidate>
    <!-- Include the CSRF token -->
    <input type='hidden' name='csrf_token' value='{{.CSRFToken}}'>
    <div>
        <label>Name:</label>
        {{with .Form.FieldErrors.name}}
            <label class='error'>{{.}}</label>
        {{end}}
        <input type='text' name='name' value='{{.Form.Name}}'>
    </div>
    <div>
        <label>Email:</label>
        {{with .Form.FieldErrors.email}}
            <label class='error'>{{.}}</label>
        {{end}}
        <input type='email' name='email' value='{{.Form.Email}}'>
    </div>
    <div>
        <label>Password:</label>
        {{with .Form.FieldErrors.password}}
            <label class='error'>{{.}}</label>
        {{end}}
        <input type='password' name='password'>
    </div>
    <div>
        <input type='submit' value='Signup'>
    </div>
</form>
{{end}}
```

```
File: ui/html/partials/nav.tmpl

{{define "nav"}}
<nav>
    <div>
        <a href='/'>Home</a>
        {{if .IsAuthenticated}}
            <a href='/snippet/create'>Create snippet</a>
        {{end}}
    </div>
    <div>
        {{if .IsAuthenticated}}
            <form action='/user/logout' method='POST'>
                <!-- Include the CSRF token -->
                <input type='hidden' name='csrf_token' value='{{.CSRFToken}}'>
                <button>Logout</button>
            </form>
        {{else}}
            <a href='/user/signup'>Signup</a>
            <a href='/user/login'>Login</a>
        {{end}}
    </div>
</nav>
{{end}}
```

请再次运行应用程序，然后查看其中一个表单的源代码。你应该看到它现在在隐藏字段中包含了一个 CSRF 令牌，如下所示。

![](img/c3e650db0d8dfdecc0f8e34a67719f65_322_0.png)

如果你尝试提交表单，现在应该可以正确运行了。

## 其他信息

## SameSite 'Strict' 设置

如果需要，你可以将会话 Cookie 改为使用 `SameSite=Strict` 设置，而不是（默认的）`SameSite=Lax`。如下所示：

```
sessionManager := scs.New()
sessionManager.Cookie.SameSite = http.SameSiteStrictMode
```

但需要注意的是，使用 `SameSite=Strict` 会阻止用户浏览器为所有跨站点用途发送会话 Cookie——包括使用 GET 和 HEAD 等 HTTP 方法的安全请求。

虽然这听起来更安全（确实如此！），但缺点是，当用户从另一个网站点击链接进入你的应用程序时，不会发送会话 Cookie。这意味着，即使他们拥有包含 "authenticatedUserID" 值的活跃会话，你的应用程序也会最初将用户视为“未登录”。

因此，如果你的应用程序可能会有其他网站链接到它（或通过电子邮件或私人消息服务共享指向它的链接），那么 `SameSite=Lax` 通常是更合适的设置。

## SameSite Cookie 和 TLS 1.3

本章前面我曾说过，我们不能完全依赖 SameSite Cookie 属性来防止 CSRF 攻击，因为并非所有浏览器都完全支持它。

但这条规则有一个例外，原因是不存在既支持 TLS 1.3 又不支持 SameSite Cookie 的浏览器。

换句话说，如果你将 TLS 1.3 设置为服务器 TLS 配置中的最低支持版本，那么所有能够使用你的应用程序的浏览器都将支持 SameSite Cookie。

```
tlsConfig := &tls.Config{
	MinVersion: tls.VersionTLS13,
}
```

只要你只允许向应用程序发送 HTTPS 请求，并强制将 TLS 1.3 作为最低 TLS 版本，你就不需要采取任何额外的 CSRF 攻击缓解措施（例如使用 `justinas/nosurf` 包）。只需确保你始终：

- 将 `SameSite=Lax` 或 `SameSite=Strict` 设置在会话 Cookie 上；以及
- 对于任何更改状态的请求，使用 POST、PUT 或 DELETE HTTP 方法。

## 使用请求上下文

目前，我们对用户进行身份验证的逻辑只是简单地检查其会话数据中是否存在 `authenticatedUserID` 值，如下所示：

```
func (app *application) isAuthenticated(r *http.Request) bool {
	return app.sessionManager.Exists(r.Context(), "authenticatedUserID")
}
```

我们可以通过查询用户数据库表来使此检查更加可靠，以确保 `authenticatedUserID` 值是真实且有效的（即，我们在用户上次登录后没有删除其账户）。

但是，执行此额外的数据库检查有一个小问题。

我们的 `isAuthenticated()` 辅助函数在每个请求周期中可能会被多次调用。目前我们使用了两次——一次在 `requireAuthentication()` 中间件中，另一次在 `newTemplateData()` 辅助函数中。因此，如果我们直接从 `isAuthenticated()` 辅助函数中查询数据库，每个请求都会进行重复的数据库往返。这效率不高。

更好的方法是在某个中间件中执行此检查，以确定当前请求是否来自已验证的用户，然后将该信息传递给链中所有后续处理程序。

那么我们该怎么做呢？请求上下文登场了。

在本节中，你将学习：

- 什么是请求上下文，如何使用它，以及何时适合使用它。
- 如何在实践中使用请求上下文在处理程序之间传递有关当前用户的信息。

