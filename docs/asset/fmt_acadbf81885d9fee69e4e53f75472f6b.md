
查看更改 - book.usegolang.com/17.5.3-diff

# 17.5.4 控制器动作与视图

接下来，我们需要创建 `http` 处理器（即 MVC 中的控制器动作）和用于渲染及处理重置密码表单的视图。我们将从视图开始。

```
$ atom controllers/users.go
```

```go
func NewUsers(us models.UserService email *email.Client) *Users {
	return Users{
	tNewView: views.New("bootstrap", "users/new"),
	LoginView: views.New("bootstrap", "users/login"),
	ForgotPwView: views.New("bootstrap", "users/forgot_pw"),
	ResetPwView: views.New("bootstrap", "users/reset_pw"),
	us: us,
	emailer: email,
	}
}

type Users struct {
	NewView:      +views.View
	LoginView:     +views.View
	ForgotPwView: +views.View
	ResetPwView:  +views.View
	us:           models.UserService
	emailer:      +email.Client
}
```

现在，我们需要为我们的 `Users` 类型添加方法来处理这些表单，

# 17.5. 重置密码

我们还需要一个方法，用于通过 URL 查询参数提供的预填充数据来渲染 `ResetPwView`。

让我们从处理忘记密码表单的代码开始。首先，我们需要定义用于表示表单数据的结构体类型。我们将在两个表单之间共享此类型，以减少代码量。

```go
// ResetPwForm 用于处理忘记密码表单
// 和重置密码表单。
type ResetPwForm struct {
  Email    string `schema:"email"`
  Token    string `schema:"token"`
  Password string `schema:"password"`
}
```

注意：我们添加了 `schema` 标签，以便 `gorilla/schema` 包可以解析 `http` 表单并将值填充到该类型的结构体中。

接下来是 `InitiateReset` 函数，它将用于处理忘记密码表单。此表单只有一个字段——用户的电子邮件地址——所以我们可以忽略 `ResetPwForm` 类型中的其他字段。

```go
// POST /forgot
func (u *Users) InitiateReset(w http.ResponseWriter, r *http.Request) {
  var vd = views.Data
  var form ResetPwForm
  vd.Yield = &form
  if err := parseForm(r, &form); err != nil {
    vd.SetAlert(err)
    u.ForgotPwView.Render(w, r, vd)
    return
  }

  token, err := u.us.InitiateReset(form.Email)
  if err != nil {
    vd.SetAlert(err)
    u.ForgotPwView.Render(w, r, vd)
    return
  }
}

// TODO: 给用户发送密码重置邮件。在
// 期间，我们需要“使用” token 变量
_ = token
  views.RedirectAlert(w, r, "reset", http.StatusFound, views.Alert({
  Level: views.AlertLvlSuccess,
  Message: "重置密码的说明已通过邮件发送给您。",
  }))
```

我们最终需要向用户发送包含其重置令牌的邮件，但目前我们用一个 `TODO` 注释预留了该部分。我们将在下一节中处理它。在此期间，我们需要添加 `_ =` 部分来欺骗编译器，使其认为我们使用了 `token` 变量，因为在向用户发送邮件之前，我们不会使用它。

注意：使用 `_ =` 这种技巧并不总是个好主意，因为可能会导致代码中出现许多未使用的变量。我在这种情况下使用它是因为我知道我们在本章的下一节将会使用它。

除了给用户发送邮件外，我们代码的其他部分是创建 `views.Data` 和 `form` 变量，通过 `parseForm` 函数解析表单，并使用我们的 `UserService` 提供的方法启动密码重置。

最后几行——`RedirectAlert` 函数调用——可能有点新奇，因为我们刚刚在本节中创建了该函数，但我们所做的只是重置用户，同时在您访问的下一个页面上渲染提醒。

接下来，我们需要处理密码表单的渲染，并用任何 URL 查询参数对其进行预填充。这将允许我们将用户引导到密码重置表单，且其重置令牌已经填充其中。

为了实现这一点，我们创建一个 `ResetPw` 处理器，它解析 URL 查询参数，然后使用这些数据渲染重置密码表单。如果没有提供任何参数，字段将为空为空，否则，我们将自动填充数据。

# 17.5. 重置密码

```go
// ResetPw 显示重置密码表单，并有一个方法
// 让我们能够通过 URL 查询参数提供的令牌
// 预填充表单数据。
//
// GET /reset
func (u *Users) ResetPw(w http.ResponseWriter, r *http.Request) {
	var views views.Data
	var form ResetPwForm
	views.Yield = &form
	if err := parseURLParams(r, &form); err != nil {
		views.SetAlert(err)
	}
	u.ResetPwView.Render(w, r, views)
}
```

我们将添加到用户控制器的最后一个函数将用于处理重置密码表单。

```go
// CompleteReset 处理重置密码表单
// POST /reset
func (u *Users) CompleteReset(w http.ResponseWriter, r *http.Request) {
	var views views.Data
	var form ResetPwForm
	views.Yield = &form
	if err := parseForm(r, &form); err != nil {
		views.SetAlert(err)
	}
	u.ResetPwView.Render(w, r, views)
	return
}

	user, err := u.us.CompleteReset(form.Token, form.Password)
	if err != nil {
		views.SetAlert(err)
		u.ResetPwView.Render(w, r, views)
		return
	}

	u.signIn(w, user)
	views.RedirectAlert(w, r, "/galleries", http.StatusFound, views.Alert({
	Level: views.AlertLevelSuccess,
	Message: "您的密码已重置，您已登录！"
	}))
}
```

在 `CompleteReset` 中，我们首先解析表单以获取令牌和新密码。

一旦有了数据，就可以调用用户服务提供的 `CompleteReset` 方法，允许它执行任何需要的模型相关的工作。完成后，用户的 `CompleteReset` 方法将返回一个带有更新密码的用户，或者一个错误。如果发生错误，我们再次渲染重置密码表单，但否则，我们知道用户的密码已经更新，我们将直接他们登录，而不是强制他们输入刚刚更改的密码。

最后，我们希望将用户重定向到画廊页面，并显示通知他们已更新密码的提醒。

有了用户控制器，我们现在需要为添加的内容创建路由。

```
$ atom main.go
```

在您的 `main` 函数中添加以下路由。

```go
r.Handle("/forget
```

> 注意：`ForgotPwView` 使用的是 `Handle` 方法而不是 `HandleFunc` 方法，因为它是 `http.Handler` 接口。

### 源代码

下方链接包含了完整的源代码以及本节中所有更改代码的差异对比。

已完成 - book.usegolang.com/17.5.3

查看更改 - book.usegolang.com/17.5.3-diff

# 17.5.5 给用户发送邮件并构建 URL

我们几乎完成了密码重置功能；最后一步是向用户发送包含其重置令牌的邮件。通过强制用户阅读邮件，我们正在验证他们是否拥有该账户的邮箱箱。

让我们首先在 `email` 包中添加一些常量，用于构建我们的密码重置邮件。

```
$ atom email/mailgun.go
```

首先是邮件主题。

```go
const resetSubject = "重置密码的说明。"
```

然后是用于构建邮件文本版本的模板。在这种情况下，我们将使用 `fmt.Sprint` 函数来填充任何数据，但您也可以根据情况选择 `text/template` 或 `html/template` 包。

```
const resetTextTemplate = `你好！
你请求了重置密码。如果是你，请点击下面的链接：
%s

如果你被要求令牌，请使用以下值：
`
```

> https://golang.org/pkg/fmt#Sprint

现在，当我们想要创建邮件时，可以用 `%s` 字符替换为 URL 和重置令牌。这不像使用模板那样安全，因为我们的变量是没有命名的，而且为了创建有效的邮件，我们需要对模板了解更多，但考虑到此模板的简单，这应该不是问题。如果您的模板变得复杂，请记得考虑使用模板包或其他方法。

最后，我们需要为邮件的 HTML 版本准备一个模板。

```go
const resetHTMLTmpl = `你好！<br/>
<br/>
你请求了重置密码。如果是你，请点击下面的链接：<br/>
<a href="%s"></a><br/>
<br/>
如果你被要求令牌，请使用以下值：<br/>
<br/>
%s<br/>
如果你没有请求重置密码，你可以安全地忽略这封邮件，你的账户将
<br/>
<br/>
Best,

```

HTML 版本与文本版本几乎相同，但我们在每一个相同的地方都放置了换行符，并为链接使用了 `<...>` 标签，它接收两个字符串变量，因此我们在构建这部分时需要传入三个变量。

在编写使用这些模板的代码之前，我们需要讨论如何构建带有编码查询参数的 URL。虽然我们可以直接发送

## 17.5. 重置密码

向用户发送带有密码重置令牌和重置页面链接的电子邮件很容易，但许多用户已经开始期待更好的体验了。现在大多数密码重置邮件都会包含一个通过 URL 查询参数嵌入令牌的链接。然后，当用户点击该链接时，表单将自动填充重置令牌字段，因此用户就无需手动填写。

为了在 Go 中实现这一点，我们将使用 `net/url` 包8。具体来说，我们将使用专门为查询参数设计的 `Values` 类型9。

构建经过编码后的查询参数最简单的方法是构造一个 `url.Values` 对象，然后将它的 `Encode` 方法10 的输出与你想要使用的基础 URL 结合。

```
v := url.Values()
v.Set("token", "encode-me-!#(&&)")
resetURL := "https://lenslocked.com/reset?" + v.Encode()
// resetURL is
// https://lenslocked.com/reset?token=encode-me-%21%23%40%28%29%26
```

有了这些知识，我们可以使用 `url.Values` 类型来构造重置密码，同时为我们的邮件客户端添加一个 `ResetPw` 方法。

```go
const resetBaseURL = "https://www.lenslocked.com/reset"
func (c *Client) ResetPwToEmail(email, token string) error {
	v := url.Values()
	v.Set("token", token)
	resetURL := resetBaseURL + "?" + v.Encode()
	resetText := fmt.Sprintf(resetTextTemplate, resetURL, token)
	message := mailgun.NewMessage(from, resetSubject, resetText, email)
	resetHTML := fmt.Sprintf(resetHTMLTemplate, resetURL, resetURL, token)
	message.SetHTML(resetHTML)
	err := c.Send(message)
	return err
}
```

> ^8https://golang.org/pkg/net/url/

9https://golang.org/pkg/net/url#Values

10https://golang.org/pkg/net/url#Values.Encode

## 710 第 17 章。填补空白

现在我们已经准备好在用户提交忘记密码表单后，向他们发送带有密码重置令牌的电子邮件了。

```
$ atom controllers/users.go
```

在 `InitiateReset` 方法内部找到 "TODO"。我们在那里也添加了一行 `_ = token`。将 TODO 替换为以下代码，它将使用我们刚刚创建的 `ResetPw` 方法向用户发送密码重置令牌邮件。

```go
func (u *Users) InitiateReset(w http.ResponseWriter, r *http.Request) {
  // ...保持未更改的代码

  err := u.mailer.ResetPw(form.Email, token)
  if err != nil {
    vd.SetAlert(err)
    u.ForgotPwView.Render(w, r, vd)
    return
  }

  // ... 代码未更改的代码
}
```

就是这样。我们已经完成了密码重置功能，这是我们在书中将添加的最后一个功能。

### 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异（diff）。

- 已完成 - book.usegolang.com/17.5.5

- 更改 - book.usegolang.com/17.5.5-diff

# 17.6. 下一步该去哪里？

## 17.6 我下一步该去哪里？

首先，我想说声贺你！我们在本课程中构建的内容绝非同小事，对于完成了这本书和你的应用程序，你应该感到自豪！

虽然我们不会在书中涵盖更多功能，但这并不意味着你需要停止。继续学习的绝佳方法是继续为你的 Web 应用程序添加新功能、构建新的应用，或者……

# 18.2. 使用 GORENAME 进行重构

```
$ get golang.org/x/tools/cmd/gorename
```

`gorename` 的工作需要两部分信息：你想要重命的变量、类型或函数，以及你想要使用的新名称。有了这些信息，它将解析你所有的 Go 代码，并尝试用更改后的名称更新对该代码的注释和引用。当你重构某些过去编写的许多不同包中使用的代码时，这会非常有用。

为了给出一个真实的例子，我们将重命名在第 12.7 节中重构的 `ErrInvalidID` 和 `ErrInvalidPassword` 变量。

我们将查看的第一个变量是 `ErrInvalidID`。我们想将其重命名为 `ErrInvalidID`，但在本节中这并不是必要的。通常情况下，将包名包裹在双引号中，并将整个字符串包裹在单引号中，以确保不会出现任何意外问题。

```
$ gorename -from "'lenslocked.com/models'.ErrInvalidID' -to 'ErrInvalidID'
```

在执行此操作时，你通常需要在 `from` 部分定义整个包，但在本节中这不是必要的。通常情况下，将包名包裹在双引号中，并将整个字符串包裹在单引号中，以确保不会出现任何意外问题。

## 框 18.1. gorename 错误

正如我们之前讨论的，`gorename` 会处理你 GOPATH 中的所有代码，因此如果这些代码中的任何部分有问题，在使用重命名工具时可能会看到错误。错误信息可能很长，但通常以如下消息结束：

```
gorename: couldn't load packages due to errors: some/package/name
```

> 如果你看到这个，我建议临时将该损坏的代码移动到另一个目录，以便继续操作。希望 `gorename` 将来能更新以处理这种情况。

假设你还没有进行过重构，运行该命令应该得到类似下方的输出。

```
Renamed 2 occurrences in 1 file in 1 package.
```

此响应意味着 `gorename` 更新了单个源文件中的两处代码。我们在变量正上方的注释也应该得到更新，因为 `gorename` 会尝试更新这些显眼位置的注释。

接下来，我们需要对 `ErrInvalidPassword` 错误执行相同的操作。

```
$ gorename -from 'lenslocked.com/models.ErrInvalidPassword' \ \
to `ErrPasswordIncorrect`
```

注意：反斜杠 (`\`) 的存在是因为该命令跨到了第二行，反斜杠告诉终端我们还有更多输入要提供。
