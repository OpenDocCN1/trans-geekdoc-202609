

## 10.5. 认证回归用户

```go
type LoginView struct {
	views.View
}

type NewView struct {
	views.View
}

type Users struct {
	LoginView
	NewView
	us      *models.UserService
}
```

之后，我们需要创建一个操作（action）来在表单提交时解析它。这个过程与创建 **Create** 方法和 **SignupForm** 类型的过程非常相似，在这种情况下，我们将编写用于解析登录表单的代码。

```go
type LoginForm struct {
	Email    string `schema:"email"`
	Password string `schema:"password"`
}

// Login 用于在用户尝试
// 作为现有用户登录（通过邮箱和密码）时处理登录表单。

// POST /login
func (u *Users) Login(w http.ResponseWriter, r *http.Request) {
	form := LoginForm()
	if err := parseForm(r, &form); err != nil {
		panic(err)
	}
	// 我们最终将执行一些操作来检查
	// 提供的信息是否正确
}
```

在下一节中，我们将通过调用用户服务的 **Authenticate** 方法并验证提供的信息是否有效来完成 **Login** 方法，但目前我们先在这里留一个注释。

在此期间，我们需要更新路由器，以告知它我们为 Web 应用程序添加的新页面。

## 第 10 章：构建认证系统

```bash
$ atom main.go

func main() {
	// ... 以上部分没有变化
	r.HandleFunc("/signup", userC.New).Methods("GET")
	r.HandleFunc("/signup", userC.Create).Methods("POST")
	// 路由使用的是 Handle 函数，而不是 HandleFunc
	r.Handle("/login", userC.Login).Methods("GET")
	r.HandleFunc("/login", userC.Login).Methods("POST")
	// ... 以下部分没有变化
}
```

最后，我们将更新导航栏模板，以添加一个链到登录页的链接。

```bash
$ atom views/layouts/navbar.gohtml
```

```html
<!-- 找到 navbar-right 部分并添加登录链接 -->
<ul class="nav navbar-nav navbar-right">
  <li><a href="/login">登录</a></li>
  <li><a href="/signup">注册</a></li>
</ul>
```

通过这些更改，我们已经完成了添加登录页的工作，并准备好为我们的用户服务实现 Authenticate 方法。

# 源代码

下面的链接包含了完成后的源代码以及本节中所有更改代码的差异（diff）。

- 已完成 - book.usegolang.com/10.5.2 
- 更改内容 - book.usegolang.com/10.5.2-diff

## 10.5. 认证回归用户

### 10.5.3 实现 Authenticate 方法

我们的 authenticate 方法将只做一件事——接收邮箱地址和密码，然后返回一个匹配该信息的用户，或者一个解释为什么无法找到匹配项的错误。它**不会**负责创建会话、修改 cookie 或任何类似的操作。这些责任将由调用 authenticate 方法的代码承担。

我们将在用户模型的源文件中编写此方法。

```bash
$ atom models/users.go
```

我们将从定义一个新错误开始。我们已经有了一个当找不到资源时返回的错误，所以如果提供了无效的邮箱地址，我们可以返回该错误，但我们仍然没有任何与提供的密码无效时相关的错误。

```go
var (
	// 保持现有的错误不变

	// ErrInvalidPassword 在尝试认证用户时
	// 使用了无效密码时返回的错误。
	ErrInvalidPassword = errors.New(
		"models: incorrect password provided",
	)
)
```

现在我们至少有两个可以返回的潜在错误：ErrNotFound 和 ErrInvalidPassword。让我们使用它们来写一个注释，描述 Authenticate 方法将如何工作。

```go
// Authenticate 可用于通过提供的
// 邮箱地址和密码认证用户。
// 如果提供的邮箱地址无效，它将返回
// nil, ErrNotFound
// 如果提供的密码无效，它将返回
// nil, ErrInvalidPassword
// 如果邮箱和密码都有效，它将返回
// user, nil
// 否则如果遇到其他错误，它将返回
// nil, error
func (us *UserService) Authenticate(
	email, password string) (*User, error) {
	// 我们稍后会实现它
	return nil, nil
}
```

在除最后一种情况以外的每情况下，我们将返回一个由 models 包定义的错误。这很重要，因为除了最后一种之外的所有情况都是我们应该能够处理错误并向终端用户渲染适当错误消息的用，但在最后一种情况下，我们可能无法为终端用户渲染有用的错误，而是需要通过交互查看我们的 Web 应用程序出了什么问题。例如，它可能因为数据库崩溃而发生错误。

现在我们已经对 Authenticate 方法要执行的操作有了大致的了解，我们将实现它。我们首先开始通过提供的邮箱地址查找用户。

```go
foundUser, err := us.ByEmail(email)
if err != nil {
    return nil, err
}
```

如果你还记得之前的内容，当通过邮箱地址找不到用户时，我们的 ByEmail 方法将返回 ErrNotFound 错误，所以我们不需要在代码中实际检查该错误。我们只需要返回 ByEmail 方法返回的任何错误即可。

假设我们无问题地检索到了用户，我们的下一步是检查提供的密码是否正确。我们将使用 bcrypt 来解密这个密码，并使用它的 `CompareHashAndPassword` 函数。

> ^4https://godoc.golang.org/x/crypto/bcrypt#CompareHashAndPassword

## 10.5. 认证回归用户

比较哈希和密码的函数接受两个参数——哈希值和明文密码。这两个者都需要字节切片（byte slices）而不是字符串，因此我们需要将我们的字符串转换为字节切片。我们还需要在明文密码中添加盐（pepper），因为存储在数据库中的哈希密码在哈希化之前已经添加了它。

`CompareHashAndPassword` 函数如果密码由于任何原因不匹配，将返回一个错误，所以我们需要捕获它的返回值。

一旦我们比较了密码：

```go
err = bcrypt.CompareHashAndPassword(
    []byte(foundUser.PasswordHash),
    []byte(password+userPepper))
```

一旦我们比较了密码，我们需要检查错误以确定发生了什么。我们关心的三种情况：

1. 如果错误为 nil，意味着密码正确。
2. 如果错误是 bcrypt 包提供的 `ErrMatchedHashAndPassword` 错误，说明我们尝试的密码是不正确的。这**并不意味着**发生了某些问题。
3. 任何其他错误表示发生了问题。这可能意味着我们拥有的哈希密码由于某种原因损坏了，本不应该发生，但如果发生了，我们将返回该错误。

这三种情况可以用下面的 switch 语句表示：

```go
switch err {
case nil:
    return foundUser, nil
case bcrypt.ErrMatchedHashAndPassword:
    return nil, ErrInvalidPassword
default:
    return nil, err
}
```

> ⁵https://godoc.org/golang.org/x/crypto/bcrypt#pkg-variables

将这一切整合在一起，我们得到了如列表 10.8 所示的实现。为了简洁，我没有在列表中显示注释，但你应该保留我们在本节之前编写的注释。

# 列表 10.8：完整实现的 Authenticate 方法。

```go
func (us *UserService) Authenticate(email, password string) (*User, error) {
	foundUser, err := us.ByEmail(email)
	if err != nil {
		return nil, err
	}

	err = bcrypt.CompareHashAndPassword(
		[]byte(foundUser.PasswordHash),
		[]byte(password+userPepper))
	switch err {
	case nil:
		return foundUser, nil
	case bcrypt.ErrMatchedHashAndPassword:
		return nil, ErrInvalidPassword
	default:
		return nil, err
	}
}
```

就是这样！我们准备好在用户控制器的登录操作中使用 authenticate 方法了。

