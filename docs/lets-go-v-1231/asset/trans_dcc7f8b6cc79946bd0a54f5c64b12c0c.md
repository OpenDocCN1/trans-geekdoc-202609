
## 用户注销

这自然带我们来到了注销用户。与注册和登录相比，实现用户注销非常简单——我们基本上只需要从会话中删除 "authenticatedUserID" 值。

同时，最好再次更新会话 ID，我们还会向会话数据中添加一条闪现消息，以向用户确认他们已注销。

让我们更新 `userLogoutPost` 处理程序，以实现上述功能。

```
File: cmd/web/handlers.go

package main

...

func (app *application) userLogoutPost(w http.ResponseWriter, r *http.Request) {
    // Use the RenewToken() method on the current session to change the session
    // ID again.
    err := app.sessionManager.RenewToken(r.Context())
    if err != nil {
        app.serverError(w, r, err)
        return
    }

    // Remove the authenticatedUserID from the session data so that the user is
    // 'logged out'.
    app.sessionManager.Remove(r.Context(), "authenticatedUserID")

    // Add a flash message to the session to confirm to the user that they've been
    // logged out.
    app.sessionManager.Put(r.Context(), "flash", "You've been logged out successfully!")

    // Redirect the user to the application home page.
    http.Redirect(w, r, "/", http.StatusSeeOther)
}
```

保存文件并重启应用程序。如果您现在点击导航栏中的‘注销’链接，您应该会被注销并重定向到主页，如下所示：

您已成功注销！

## 最新代码片段

| 标题 | 创建时间 | ID |
| :--- | :--- | :--- |
| 鹪鹩 | 05 Apr 2022 at 16:21 | #6 |
| 时不时 | 05 Apr 2022 at 14:59 | #5 |
| 哦，蜗牛 | 05 Apr 2022 at 07:32 | #4 |
| 初秋的早晨 | 05 Apr 2022 at 07:20 | #3 |
| 越过冬日森林 | 05 Apr 2022 at 07:20 | #2 |
| 一座古旧寂静的池塘 | 05 Apr 2022 at 07:20 | #1 |

## 用户授权

能够对应用程序的用户进行身份验证固然很好，但现在我们需要对这些信息做些有用的事情。在本章中，我们将引入一些授权检查，以便：

- 只有经过身份验证（即已登录）的用户才能创建新代码片段；以及
- 导航栏的内容会根据用户是否经过身份验证（已登录）而变化。具体而言：
  - 已验证的用户应看到‘主页’、‘创建代码片段’和‘注销’链接。
  - 未验证的用户应看到‘主页’、‘注册’和‘登录’链接。

正如我在前一章中简要提到的，我们可以通过检查会话数据中是否存在 "authenticatedUserID" 值来判断请求是否来自经过身份验证的用户。

那么，让我们开始吧。打开 cmd/web/helpers.go 文件，添加一个 isAuthenticated() 辅助函数来返回身份验证状态，如下所示：

```
File: cmd/web/helpers.go

package main

...

// Return true if the current request is from an authenticated user, otherwise
// return false.
func (app *application) isAuthenticated(r *http.Request) bool {
	return app.sessionManager.Exists(r.Context(), "authenticatedUserID")
}
```

这样一来，我们现在可以通过简单地调用这个 isAuthenticated() 辅助函数来检查请求是否来自经过身份验证（已登录）的用户。

下一步是找到一种方法将这些信息传递给我们的 HTML 模板，以便我们可以根据需要切换导航栏的内容。

这分为两个部分。首先，我们需要向 templateData 结构体添加一个新的 IsAuthenticated 字段：

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
	CurrentYear int
	Snippet	models.Snippet
	Snippets	[]models.Snippet
	Form		any
	Flash		string
	IsAuthenticated	bool // Add an IsAuthenticated field to the templateData struct.
}

...
```

第二步是更新我们的 `newTemplateData()` 辅助函数，以便每次渲染模板时，这些信息都会自动添加到 `templateData` 结构体中。如下所示：

```
File: cmd/web/helpers.go

package main

...

func (app *application) newTemplateData(r *http.Request) templateData {
	return templateData{
		CurrentYear: time.Now().Year(),
		Flash: app.sessionManager.PopString(r.Context(), "flash"),
		// Add the authentication status to the template data.
		IsAuthenticated: app.isAuthenticated(r),
	}
}

...
```

完成后，我们可以更新 `ui/html/partials/nav.tmpl` 文件，使用 `{{if .IsAuthenticated}}` 动作来切换导航链接，如下所示：

```
File: ui/html/partials/nav.tmpl

{{define "nav"}}
<nav>
    <div>
        <a href='/'>Home</a>
        {{-- Toggle the link based on authentication status --}}
        {{if .IsAuthenticated}}
            <a href='/snippet/create'>Create snippet</a>
        {{end}}
    </div>
    <div>
        {{-- Toggle the links based on authentication status --}}
        {{if .IsAuthenticated}}
            <form action='/user/logout' method='POST'>
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

保存所有文件，现在尝试运行应用程序。如果您当前未登录，您的应用程序主页应该如下所示：

![](img/c3e650db0d8dfdecc0f8e34a67719f65_308_0.png)

否则——如果您已登录——您的主页应该如下所示：

## 最新代码片段

| 标题 | 创建时间 | ID |
| :--- | :--- | :--- |
| 鹪鹩 | 05 Apr 2022 at 16:21 | #6 |
| 时不时 | 05 Apr 2022 at 14:59 | #5 |
| 哦，蜗牛 | 05 Apr 2022 at 07:32 | #4 |
| 初秋的早晨 | 05 Apr 2022 at 07:20 | #3 |
| 越过冬日森林 | 05 Apr 2022 at 07:20 | #2 |
| 一座古旧寂静的池塘 | 05 Apr 2022 at 07:20 | #1 |

随意尝试一下，尝试登录和登出，直到您确信导航栏的变化符合您的预期。

## 限制访问

就目前而言，我们对任何未登录的用户隐藏了‘创建代码片段’导航链接。但是，未验证的用户仍然可以通过直接访问 https://localhost:4000/snippet/create 页面来创建新代码片段。

让我们修复这个问题，这样如果未验证的用户尝试访问 URL 路径为 /snippet/create 的任何路由，他们将被重定向到 /user/login。

最简单的方法是通过一些中间件。打开 cmd/web/middleware.go 文件，创建一个新的 requireAuthentication() 中间件函数，遵循本书前面使用的相同模式：

```
File: cmd/web/middleware.go

package main

...

func (app *application) requireAuthentication(next http.Handler) http.Handler {
    return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        // If the user is not authenticated, redirect them to the login page and
        // return from the middleware chain so that no subsequent handlers in
        // the chain are executed.
        if !app.isAuthenticated(r) {
            http.Redirect(w, r, "/user/login", http.StatusSeeOther)
            return
        }

        // Otherwise set the "Cache-Control: no-store" header so that pages
        // require authentication are not stored in the users browser cache (or
        // other intermediary cache).
        w.Header().Add("Cache-Control", "no-store")

        // And call the next handler in the chain.
        next.ServeHTTP(w, r)
    })
}
```

我们现在可以将这个中间件添加到我们的 `cmd/web/routes.go` 文件中，以保护特定路由。

在我们的例子中，我们将想要保护 GET /snippet/create 和 POST /snippet/create 路由。对未登录的用户进行注销也没有多大意义，因此在 POST /user/logout 路由上使用它也是合理的。

为了帮助实现这一点，让我们将应用程序路由重新排列为两个‘组’。

第一个组将包含我们的‘未受保护’路由并使用我们现有的动态中间件链。第二个组将包含我们的‘受保护’路由，并将使用一个新的受保护中间件链——由动态中间件链加上我们的新 requireAuthentication() 中间件组成。

像这样：
