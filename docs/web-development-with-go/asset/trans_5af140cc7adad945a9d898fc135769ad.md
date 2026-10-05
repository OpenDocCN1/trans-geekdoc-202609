

# 16.7. 设置服务器

注意：`restart` 命令会在服务未运行的情况下启动它，或者停止并重新启动一个正在运行的服务。

到此，我们的部署脚本就编写完成了了。进入你的 `lenslocked.com` 目录并运行以下命令：

```
$ ./scripts/release.sh
```

在你的发布脚本完成后，你的 Web 应用程序将在你的服务器上上线。例如，如果你的服务器 IP 地址为 `123.123.22.33` 且你没有设置服务器使用域名，你应该可以在浏览器中输入该地址并看到应用程序正在运行。如果你设置了域名并为服务器创建了 A 记录，那么这样做也应该可行，而且支持 HTTPS！

恭喜你发布了第一个 Web 应用程序！

# 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异（diff）。

已完成 - book.usegolang.com/16.7.7

更改 - book.usegolang.com/16.7.7-diff

# 第 17 章

# 填补空白

书的最后一章与之前的章节略有不同，因为我们将看到的大部分代码都涉及添加可选功能，而这些功能可以通过多种方式实现。

例如，当我们开始查看发送邮件时，我们将使用 Mailgun 来发送邮件，但世界上还有许多其他邮件服务，在某些公司中，他们会有自己的内部解决方案。无论如何，查看一个如何向用户发送电子邮件的示例仍然很有用。

# 17.1 删除 Cookie 并注销用户

我们的用户可能在某个时刻需要一种退出的方法，让我们来看看如何实现该功能。

创建一个注销链接大约涉及两个主要步骤：

- 1. 每当用户登录时，在导航栏中添加一个注销按钮。
- 2. 添加一个控制器和路由来处理注销并删除用户的话 Cookie。

当我们为画廊索引页添加链接时，我们已经看到过如何根据用户是否登录来自定义导航栏。添加注销链接的操作也大同相同，但由于注销是一个破坏性操作（它会删除你的话 Cookie），我们将把此放在一个表单中，以便用户必须执行 HTTP POST 请求才能进行注销。

首先打开导航栏模板。

```
$ atom views/layouts/navbar.ghtml
```

我们将添加一个 `logoutForm` 模板。我们需要在其中包含一个 `csrfField`，因为它是一个表单。

```
{{ "logoutForm" }}
<form class="navbar-form navbar-left" action="/logout" method="POST">
{{csrfField}}
<button type="submit" class="btn btn-default">Log out</button>
</form>
{{end}}
```

> 注意：我们在这里使用 `navbar-form` 类是为了确保表单在导航栏内部被正确正确渲染。

在添加模板之后，导航栏的右侧部分有我们的“登录”和“注册”链接。我们将更新这里，如果用户已登录则显示注销表单，否则我们将渲染现有的链接。

```
<ul class="nav navbar-nav navbar-right">
{{if .User}}
  <li>{{template "logoutForm"}}</li>
{{else}}
  <li><a href="/login">Log In</a></li>
  <li><a href="/signup">Sign Up</a></li>
{{end}}
</ul>
```

# 17.1. 删除 Cookie 并注销用户

我们需要添加一个控制器来处理用户注销。这是通过删除用户的会话 Cookie 实现的，这实际上意味着告诉浏览器使其过期。为了保险起见，我们还会更新用户的记忆令牌（remember token），这样即使 Cookie 被留着，它也将不再具有有效的令牌。

```
// atom controllers/users.go
```

```go
// Logout 用于删除用户的会话 Cookie
// 并使他们当前的记忆令牌失效，这将
// 注销当前用户。

// POST /logout
func (u *Users) Logout(w http.ResponseWriter, r *http.Request) {
	// 首先让 cookie 过期
	cookie := http.Cookie{
		Name:    "session_token",
		Value:   "",
		Expires: time.Now(),
		Path:    "/",
	}
	http.SetCookie(w, &cookie)

	// 然后我们更新记忆令牌
	token, err := r.Cookie("remember_token")
	if err == nil {
		u.InvalidRememberToken(token.Value)
	}

	// 最后我们重定向到首页
	http.Redirect(w, r, "/", http.StatusSeeOther)
}
```

最后，我们需要在 `main.go` 中添加路由。

```
$ atom main.go

```
r.Handle("/logout", u.Logout)
```

# 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异。

已完成 - book.usegolang.com/16.7.7

更改 - book.usegolang.com/16.7.7-diff

# 17.2 使用提示重定向

使用提示进行重定向大致分为三个步骤：

- 1. 首先我们必须开发一种持久化提示的方法。
- 2. 一旦持久化了提示，创建一个使用它们的函数。
- 3. 最后，我们在使用后清除提示。

我们目前的应用程序在需要重定向时处理提示。

# 持久化、获取和清除提示

第一部分是最复杂的，这实际上意味着它涉及的代码最多。我们已经学习过创建、获取和删除 Cookie。

让我们从持久化提示的函数开始。

```
$ atom views/data.go
```

go
import (
  // 添加两个导入
  "net/http"
  "time"
)

type Alert struct {
	Level   string
	Message string
}

func persistAlert(w http.ResponseWriter, alert Alert) {
	// 我们不希望提示在几天后出现。如果用户
	// 希望在 5 分钟后跳转，我们将
	// 让它过期。
	expiresAt := time.Now().Add(5 * time.Minute)
	lvl := http.Cookie{
		Name:    "alert_level",
		Value:   alert.Level,
		Expires: expiresAt,
		HttpOnly: true,
		Path:    "/",
	}
	msg := http.Cookie{
		Name:    "alert_message",
		Value:   alert.Message,
		Expires: expiresAt,
		HttpOnly: true,
		Path:    "/",
	}
	http.SetCookie(w, &lvl)
	http.SetCookie(w, &msg)
}
```

接下来我们需要一种清除这些提示的方法。最简单的方法通常是将过期日期设置为当前时间，这样 Cookie 会立即过期。

```go
func clearAlert(w http.ResponseWriter) {
	lvl := http.Cookie{
		Name:    "alert_level",
		Value:   "",
		Expires: time.Now(),
		HttpOnly: true,
		Path:    "/",
	}
	msg := http.Cookie{
		Name:    "alert_message",
		Value:   "",
		Expires: time.Now(),
		HttpOnly: true,
		Path:    "/",
	}
	http.SetCookie(w, &lvl)
	http.SetCookie(w, &msg)
}
```

最后，我们可能想要能够获取已经持久化的提示，因此我们将为之添加一个函数。

