

# 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异（diff）。

完成 - book.usegolang.com/10.4.2

更改 - book.usegolang.com/10.4.2

# 10.4.3 从注册表单获取密码

我们有方法对密码进行哈希，但如果我们不从注册表单解析密码并将其设置到用户模型中，这种方法毫无用。幸运的是，在用户控制器中这一更改非常快速。

```
$ atom controllers/users.go
```

我们将更新 `Create` 方法，由于我们的 `SignupForm` 已经有了密码字段，我们只需要将其添加到用户模型中。

> 列表 10.5: 使用表单
func (u *Users) Create(w http.ResponseWriter, r *http.Request) {
// ... 保持不变
  user := models.User{
    Name: form.Name,
    Email: form.Email,
    Password: form.Password,
  }
// ... 保持不变
}

现在我们的密码正在从注册表单中解析，被添加到用户模型，并通过用户服务调用创建用户。

# 10.4 为我们的用户实现密码哈希

处理密码哈希但我们还没有完全完成。我们仍然需要讨论加盐（salting）和加料（peppering）。

# 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异。

完成 - book.usegolang.com/10.4.3

更改 - book.usegolang.com/10.4.3

# 10.4.4 加盐和加料

在我们准备好创建哈希密码的用户之前，我们需要做的最后一件事是实现盐和加料。幸运的是，我们实际上不需要做任何事情，因为 bcrypt 会为我们处理这一点。

> 10.3. bcrypt 如何存储盐的？

每当 bcrypt 创建哈希时，它在返回之前还会添加一些额外数据。例如，假设我们有了如下由 bcrypt 生成的哈希：

```
$2a$10$
```

这个哈希可以被拆分为几个部分：

```
$2a$
10$
```

当你将这些部分组合在一起时，创建了原始哈希，但它们分别告诉 bcrypt 关于哈希的信息。第一部分 `$2a$` 用于告诉 bcrypt 我们正在使用的格式以及如何处理哈希的剩余部分。这就是为什么它在前面的——除非我们知道格式，否则我们对剩余部分做不了。第二部分是哈希的成本（cost）。在这种情况下我们有 `10$`，这意味着我们使用的成本是 10。在编写时，10 是 Go bcrypt 包的默认成本。这是我们在 base64 编码的密码中使用的盐。最后我们有最后一部分——`....`。这是 bcrypt 使用明文密码、盐和成本生成的实际哈希。

> 注意：我在书中提到了加盐的工作原理，以便你将来了解它，即使你不需要自己实现。

另一方面，加料（peppering）并不由 bcrypt 处理，所以我们需要编写一些代码。将在用户模型中处理这一点。

```
$ atom models/users.go
```

现在我们将添加一个名为 `userPepper` 的包变量。你可以为你的字符串选择任何值，并在生产环境中使用不同的加料，而在开发环境中使用占位值。

```
// 将此添加到你的用户模型
var userPepper = "secret-random-string"
```

接下来我们需要为用户提供的密码加料。为了实现这一点，我们将使用 `+` 运算符将密码与我们的加料连接，然后对生成的字符串进行哈希。我们现在会在 `Create` 方法中处理，但我们需要将此代码移动到其他地方，以便允许用户更新他们的密码。

> 列表 10.6: 创建用户时为密码加料

```go
func (us *UserService) Create(user *User) error {
	pwBytes := []byte(user.Password + userPepper)
	hashedBytes, err := bcrypt.GenerateFromPassword(pwBytes, bcrypt.DefaultCost)
	if err != nil {
		return err
	user.PasswordHash =
```

恭喜你！你完成了哈希用户密码所需的最后部分。如果你想运行一下，请重启应用程序并注册账户。我们现在还无法验证你的账户，但那是我们的下一个任务。

注意：如果你在此之前创建了任何用户，应该重置数据库，因为它们的密码可能是无效的，我们在下一节将无法对他们进行验证。

# 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异。

完成 - book.usegolang.com/10.4.4

更改 - book.usegolang.com/10.4.4

# 10.5 验证返回的用户

我们已经在数据库中存储了用户，现在是编写我们认证系统的后半部分——用于验证用户确实是他们所身份的代码。

本章的其余部分专注于允许用户填写登录表单、解析数据并验证提供的电子邮件和密码是否正确。虽然我们最终需要一种在用户登录后记住他们的方法，我们将将其推到下一章。

### 10.5.1 创建登录模板

我们要编写的第一部分代码是登录表单。它与注册单几乎相同，有两个主要区别：

- 它 POST 到 `/login` 而不是 `/signup`。
- 我们没有用户名的输入，而是要求提供电子邮件。

我们将在 `users` 目录下创建模板。

```
$ atom views/users/login.html
```

创建文件后，我们需要用 10.7 中的代码填充它。

> 列表 10.7: 创建模板
```
(define "yield")
<div class="row">
  <div class="col-md-4 col-offset-4">
    <div class="panel panel-primary">
      <div class="panel-heading">
        <h3 class="panel-title">Welcome Back!</h3>
      </div>
      <div class="panel-body">
        {{loginForm}}
      </div>
    </div>
  </div>
</div>

(define "loginForm")
  <form action="/login" method="POST">
    <div class="form-group">
      <label for="email">Email</label>
      <input type="email" name="email" class="form-control" id="email">
    </div>
    <div class="form-group">
      <label for="password">Password</label>
      <input type="password" name="password" class="form-control" id="password" placeholder="Password">
    </div>
    <button type="submit" class="btn btn-primary">Log In</button>
  </form>
(end)
```

# 10.5.2 创建登录 action

为了渲染和解析我们的登录表单，我们需要更新用户控制器。具体来说，我们将创建一个渲染该模板的新视图，并创建一个用于在提交时处理表单的方法。

从技术上讲，登录更接近创建会话而不是修改用户，因此许多开发者会选择将这些视图和操作放在会话控制器中。虽然这种方法没有错，但我个人倾向于将这些操作放在用户控制器中，因为会话和用户联系如此紧密，除了登录或注销用户，我们不会对会话控制器做任何其他事情。

打开你的用户控制器源代码。

```
$ atom controllers/users.go
```

```go
func NewUsers(us *models.UserService) *Users {
    return &Users{
        New: views.NewView("bootstrap", "users/new"),
        Login: views.NewView("bootstrap", "users/login"),
    }
}
```

