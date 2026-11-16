

package main

...

func (app *application) userLoginPost(w http.ResponseWriter, r *http.Request) {
	var form userLoginForm
	err := app.decodePostForm(r, &form)
	if err != nil {
		app.clientError(w, http.StatusBadRequest)
		return
	}

	form.CheckField(validator.NotBlank(form.Email), "email", "This field cannot be blank")
	form.CheckField(validator.Matches(form.Email, validator.EmailRX), "email", "This field must be a valid email address")
	form.CheckField(validator.NotBlank(form.Password), "password", "This field cannot be blank")

	if !form.Valid() {
		data := app.newTemplateData(r)
		data.Form = form

		app.render(w, r, http.StatusUnprocessableEntity, "login.tmpl", data)
		return
	}

	id

## 实现“更改密码”功能

在这个练习中，你的目标是添加一个功能，让经过身份验证的用户可以使用类似于此的表单来更改他们的密码：

![](img/c3e650db0d8dfdecc0f8e34a67719f65_428_0.png)

在此练习中，请确保：

- 要求用户输入当前密码，并验证它是否与 users 表中的哈希密码匹配（以确认发出请求的确实是本人）。
- 在更新 users 表之前，先对他们的新密码进行哈希处理。

### 步骤 1

创建两个新路由和处理程序：

- GET /account/password/update 映射到新的 accountPasswordUpdate 处理程序。
- POST /account/password/update 映射到新的 accountPasswordUpdatePost 处理程序。

这两条路由都应仅限经过身份验证的用户访问。

显示建议代码

### 步骤 2

创建一个新的 ui/html/pages/password.tmpl 文件，其中包含更改密码表单。此表单应：

- 包含三个字段：currentPassword、newPassword 和 newPasswordConfirmation。
- 提交时将表单数据 POST 到 /account/password/update。
- 发生验证错误时，为每个字段显示错误。
- 发生验证错误时，不重新显示密码。

提示：你可能希望参考我们在用户注册表单上所做的工作，将其作为这里的指南。

然后更新 cmd/web/handlers.go 文件，添加一个新的 accountPasswordUpdateForm 结构体，用于将表单数据解析其中，并更新 accountPasswordUpdate 处理程序以显示此空表单。

作为经过身份验证的用户访问 https://localhost:4000/account/password/update 时，它应该看起来类似于此：

![](img/c3e650db0d8dfdecc0f8e34a67719f65_430_0.png)

显示建议代码

### 步骤 3

更新 accountPasswordUpdatePost 处理程序，以执行以下表单验证检查，并在出现任何失败时重新显示表单及相关错误消息。

- 所有三个字段均为必填项。
- newPassword 值必须至少为 8 个字符长。
- newPassword 和 newPasswordConfirmation 值必须匹配。

![](img/c3e650db0d8dfdecc0f8e34a67719f65_431_0.png)

显示建议代码

### 步骤 4

在你的 `internal/models/users.go` 文件中创建一个新的 `UserModel.PasswordUpdate()` 方法，其签名如下：

```
func (m *UserModel) PasswordUpdate(id int, currentPassword, newPassword string) error
```

在此方法中：

- 从数据库中检索由 `id` 参数给定的 ID 的用户的用户详细信息。
- 检查 `currentPassword` 值是否与该用户的哈希密码匹配。如果不匹配，返回 `ErrInvalidCredentials` 错误。
- 否则，对 `newPassword` 值进行哈希处理，并更新 `users` 表中相关用户的 `hashed_password` 列。

同时更新 UserModelInterface 接口类型，以包含你刚刚创建的 PasswordUpdate() 方法。

[显示建议代码]

### 步骤 5

更新 accountPasswordUpdatePost 处理程序，以便在表单有效时调用 UserModel.PasswordUpdate() 方法（请记住，用户的 ID 应该在会话数据中）。

在发生 models.ErrInvalidCredentials 错误时，通知用户在 currentPassword 表单字段中输入了错误的值。否则，向用户会话添加一条闪现消息，说明他们的密码已成功更改，并将他们重定向到其账户页面。

[显示建议代码]

### 步骤 6

更新账户页面以包含指向更改密码表单的链接，类似于此：

![](img/c3e650db0d8dfdecc0f8e34a67719f65_432_0.png)

显示建议代码

### 步骤 7

尝试运行应用程序的测试。你应该会得到一个失败，因为 mocks.UserModel 类型不再满足 models.UserModelInterface 结构体中指定的接口。通过向模拟对象添加适当的 PasswordUpdate() 方法来修复此问题，并确保测试通过。

显示建议代码

### 建议代码

### 建议代码

### 步骤 1 的建议代码

```
File: cmd/web/handlers.go

package main

...

func (app *application) accountPasswordUpdate(w http.ResponseWriter, r *http.Request) {
    // Some code will go here later...
}

func (app *application) accountPasswordUpdatePost(w http.ResponseWriter, r *http.Request) {
    // Some code will go here later...
}
```

```
File: cmd/web/routes.go

package main

...

func (app *application) routes() http.Handler {
	mux := http.NewServeMux()

	mux.Handle("GET /static/", http.FileServerFS(ui.Files))

	mux.HandleFunc("GET /ping", ping)

	dynamic := alice.New(app.sessionManager.LoadAndSave, noSurf, app.authenticate)

	mux.Handle("GET /{$}", dynamic.ThenFunc(app.home))
	mux.Handle("GET /about", dynamic.ThenFunc(app.about))
	mux.Handle("GET /snippet/view/{id}", dynamic.ThenFunc(app.snippetView))
	mux.Handle("GET /user/signup", dynamic.ThenFunc(app.userSignup))
	mux.Handle("POST /user/signup", dynamic.ThenFunc(app.userSignupPost))
	mux.Handle("GET /user/login", dynamic.ThenFunc(app.userLogin))
	mux.Handle("POST /user/login", dynamic.ThenFunc(app.userLoginPost))

	protected := dynamic.Append(app.requireAuthentication)

	mux.Handle("GET /snippet/create", protected.ThenFunc(app.snippetCreate))
	mux.Handle("POST /snippet/create", protected.ThenFunc(app.snippetCreatePost))
	mux.Handle("GET /account/view", protected.ThenFunc(app.accountView))

	// Add the two new routes, restricted to authenticated users only.
	mux.Handle("GET /account/password/update", protected.ThenFunc(app.accountPasswordUpdate))
	mux.Handle("POST /account/password/update", protected.ThenFunc(app.accountPasswordUpdatePost))
	mux.Handle("POST /user/logout", protected.ThenFunc(app.userLogoutPost))

	standard := alice.New(app.recoverPanic, app.logRequest, commonHeaders)

	return standard.Then(mux)
}
```

### 步骤 2 的建议代码

```
File: ui/html/pages/password.tmpl

{{define "title"}}Change Password{{end}}

{{define "main"}}
<h2>Change Password</h2>
<form action='/account/password/update' method='POST' novalidate>
    <input type='hidden' name='csrf_token' value='{{.CSRFToken}}'>
    <div>
        <label>Current password:</label>
        {{with .Form.FieldErrors.currentPassword}}
        <label class='error'>{{.}}</label>
        {{end}}
        <input type='password' name='currentPassword'>
    </div>
    <div>
        <label>New password:</label>
        {{with .Form.FieldErrors.newPassword}}
        <label class='error'>{{.}}</label>
        {{end}}
        <input type='password' name='newPassword'>
    </div>
    <div>
        <label>Confirm new password:</label>
        {{with .Form.FieldErrors.newPasswordConfirmation}}
        <label class='error'>{{.}}</label>
        {{end}}
        <input type='password' name='newPasswordConfirmation'>
    </div>
    <div>
        <input type='submit' value='Change password'>
    </div>
</form>
{{end}}
```

```
File: cmd/web/handlers.go

package main

...

type accountPasswordUpdateForm struct {
    CurrentPassword         string `form:"currentPassword"`
    NewPassword             string `form:"newPassword"`
    NewPasswordConfirmation string `form:"newPasswordConfirmation"`
    validator.Validator     `form:"-"`
}

func (app *application) accountPasswordUpdate(w http.ResponseWriter, r *http.Request) {
    data := app.newTemplateData(r)
    data.Form = accountPasswordUpdateForm{}

    app.render(w, r, http.StatusOK, "password.tmpl", data)
}

...
```

### 步骤 3 的建议代码

