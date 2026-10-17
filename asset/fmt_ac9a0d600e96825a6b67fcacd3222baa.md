
接下来是 `Update` 方法。如果 `remember token` 没有更新，我们就不希望更新 `remember hash`，因此在这种情况下我们需要一个 `if` 语句。我们在 `Create` 方法中不需要这个，因为在创建用户时，我们总是创建一个新的 `remember token`。

```go
func (us *UserService) Update(user *User) error {
	if user.Remember != "" {
		user.RememberHash = us.hmac.Hash(user.Remember)
	}
	return us.db.Save(user).Error
}
```

# 11.7. 在 USER SERVICE 中哈希 REM TOKENS

完成最后一次代码更改后，我们准备好开始持久化 `remember tokens` 了，但在使用它们之前，我们需要编写一个函数，允许我们根据 `remember token` 查找用户。

### 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异。

已完成 - `book.usegolang.com/11.7.4`

更改 - `book.usegolang.com/11.7.4-diff`

# 11.7.5 通过 remember token 获取用户

我们仍然在 `users` 模型中工作，所以请确保你已经打开了它。

```
$ atom models/users.go
```

我们将编写的下一段代码是 `UserService` 的一个新方法，它允许我们传入原始的 `remember token`，然后返回带有 `remember token` 的用户或错误。为了使此能够工作，我们的方法首先需要对原始 `remember token` 进行哈希处理，以便与我们在数据库中存储的内容匹配，然后查询数据库中具有 `remember token hash` 的用户。

我们已经看到过如何实现这些每一个单独的部分，所以剩下的工作就是将它们整合在一起。

```go
// ByRemember 根据给定的 remember token 查找用户
// 并返回该用户。此方法将为我们处理 token 的哈希。
```

```go
// Errors 与 ByEmail 相同。
func (us *UserService) ByRemember(token string) (*User, error) {
    var user User
    rememberHash := us.hmac.Hash(token)
    err := us.db.Where("remember_hash = ?", rememberHash).First(&user).Error
    if err != nil {
        return nil, err
    }
    return &user, nil
}
```

注意：我们在 `Where()` 方法中使用 `remember_hash` 看起来有点奇怪，`GORM` 在创建数据库表时使用 `snake case`（蛇形命名法），这确实是正确的用法。我们返回与 `ByEmail` 相同的错误，这使得 `ByRemember` 方法在未找到记录时能够轻松地返回 `ErrNotFound`。

# 11.7.6 重置我们的数据库并测试

最后一块拼图是测试。这不是传统的测试文件，但我们至少需要验证我们的代码按预期工作。

在此期间，我们还将使用 `DestructiveReset` 方法重置数据库，因为任何现有用户将没有有效的 `RememberHash` 字段，而我们还没有为此创建迁移。重置数据库并从头开始更简单。

注意：如果你忘记这样做，你可能会在日志中看到以下消息：
`pq: column "remember_hash" contains null values`

# 11.7.7 在 USER SERVICE 中哈希 REM TOKENS

与我们的数据库交互需要我们从主源文件复制一些代码到实验性文件中。具体来说，我们需要用于连接数据库的常量 `set`。我们将重构数据库连接字符串，设置一个 `user service` 实例，然后与其交互。

鉴于这些都是我们见过的或刚刚写的代码，我将先展示源代码，然后演示它。

打开你的实验性代码。

```
$ atom exp/main.go
```

然后将其内容替换为以下源码，注意你可能需要根据你的特定设置更新常量。

```go
package main
import (
	"fmt"
	"lenslocked.com/models"
)
const (
	host = "localhost"
	port = 5432
	user = "jon"
	password = "your-password"
	dbname = "lenslocked_dev"
)
func main() {
	psqlInfo := fmt.Sprintf("host=%s port=%d user=%s password=%s dbname=%s sslmode=disable",
		host, port, user, password, dbname)
	us, err := models.NewUserService(psqlInfo)
	if err != nil {
		panic(err)
	}
	defer us.Close()
	us.DestructiveReset()
	user := models.User{
		Name:     "Michael Scott",
		Email:    "michael@undflin.com",
		Password: "bestboss",
	}
	err = us.Create(&user)
	if err != nil {
		panic(err)
	}
	// 验证用户是否有 RememberHash
	fmt.Printf("%v\n", user)
	if user.Remember == "" {
		panic("Invalid remember token")
	}
	// 现在验证我们可以通过该 remember token 查找用户
	user2, err := us.ByRemember(user.Remember)
	if err != nil {
		panic(err)
	}
	fmt.Printf("%v\n", user2)
}
```

在这段代码中：

1. 重置我们的 `users` 表
2. 创建新用户并允许我们的 `user service` 设置 `remember token`
3. 验证 `remember token` 已设置，否则 `panic`
4. 通过 `remember token` 搜索用户，以验证 `ByRemember` 方法有效且我们的 `remember token` 已正确持久化

你可以通过运行以下命令来自己测试：

```
$ go run exp/main.go
```

### 源代码

下面的链接包含了完整的源代码以及本节所有更改代码的差异。

- 已完成 - `book.usegolang.com/11.7.6`
- 更改 - `book.usegolang.com/11.7.6-diff`

# 11.8 记住用户

在本节中，我们将如何使用 `cookie` 在请求之间记住用户是谁，以及如何使用这些信息在用户未登录时限制其访问页面。

我们将从编写一个允许我们“登录”用户的方法开始。换句话说，如果原始 `token` 不可用，它将生成一个新的 `remember token`，使用 `remember token` 更新用户账户，最后将 `remember token` 存储在 `cookie` 中，以便我们在后续请求中知道该用户。我们将在创建新账户或登录时调用此方法。

之后，我们将修改 `cookie` 测试函数，使其查找此 `cookie`，如果用户未登录则将其重定向到登录页面，否则将打印用户的账户信息以证明我们现在可以访问该用户。

# 11.8.1 在 cookie 中存储 remember tokens

`signIn` 方法将是 `users controller` 的一部分，因为我们在用户登录和创建账户时会使用它。

```
$ atom controllers/users.go
```

我们的 `signIn` 方法需要提供两个参数：当前的 `NextResponse`，以及我们想要登录的用户。我们需要用户来更新他们的 `remember token`，我们需要 `response writer` 来设置用户的 `cookie`。

```go
// signIn 用于通过 cookie 登录给定的用户
func (u *Users) signIn(w http.ResponseWriter, user *models.User) error {
  // TODO: Implement this
}
```

虽然不太可能，但在尝试用新的 `remember token` 更新用户时可能会遇到错误，因此当错误发生时我们需要返回这些错误，这就是返回 `error` 类型的原因。

我们的实现将从检查是否设置了原始 `remember token` 开始。如果没有设置，我们没有办法反转哈希值，因此我们将生成一个新的 `remember token`。否则，我们将使用已经为用户设置的 `remember token`。

当我们生成 `remember token` 时，我们还想使用 `user service` 更新用户，因此我们还将调用 `Update` 方法并返回任何存在的错误。

## 11.8. 记住用户

```go
return err
}
user.Remember = token
err = u.us.Update(user)
if err != nil {
    return err
}
```

退出此 `if` 语句后，我们知道 `user` 变量的 `Remember` 字段中应该有一个非空字符串值。如果它为空字符串，我们在语句内部的代码将生成一个新的记住记忆令牌（`remember token`），否则我们知道它已经设置了。

我们将使用记住记忆令牌创建一个 `cookie`，并使用 `http` 包通过传递到我们 `signIn` 方法的响应（`response`）来设置它。最后，如果我们执行到了这一步，说明没有任何错误，我们将返回 `nil`。

```go
cookie := http.Cookie{
Name: "remember_token",
Value: user.Remember,
}
http.SetCookie(w, &cookie)
return nil
```

将所有内容整合在一起，我们得到了列表 11 所示的方法。

```
Listing 11.2: 完整的 signIn 方法
// signIn 用于通过 cookie 登录指定的用户
func (u *Users) signIn(w http.ResponseWriter,
user *models.User) error {
if user.Remember == "" {
    token, err := rand.RememberToken()
    if err != nil {
        return err
    }
    user.Remember = token
    err = u.us.Update(user)
}
if err != nil {
    return err
}
cookie := http.Cookie{
    Name: "remember_token",
    Value: user.Remember,
}
http.SetCookie(w, &cookie)
return nil
}
}
```

下一步是更新 `login` 和 `signup` 方法，以便在用户成功创建账户或登录后调用此方法。我们还将把用户重定向到 `cookie` 测试页面，这样我们就可以验证 `cookie` 是否已正确设置，而无需手动输入 URL。

更新 `Create` 方法比较简单，我们只需要添加一些新代码并删除方法末尾的 `fmt.Fprintln`。

```go
func (u *Users) Create(w http.ResponseWriter, r *http.Request) {
    // ... 这部分代码保持不变
    // 删除此行：
    // fmt.Fprintln(w, "User is", user)
    // 在 Create 方法末尾添加以下代码
    err := u.SignIn(w, &cookie)
    if err != nil {
        // 临时返回错误消息以供调试
        http.Error(w, err.Error(), http.StatusInternalServerError)
        return
    }
    // 重定向到 cookie 测试页面以测试 cookie
    http.Redirect(w, r, "/cookietest", http.StatusFound)
}
```

在 `Login` 方法中，我们需要删除任何用于创建 `cookie` 的代码以及方法末尾的打印语句。我们不再需要手动创建 `cookie` 了，因为它已经由 `signIn` 方法处理了。

## 11.8. 记住用户

```go
func (u *Users) Login(w http.ResponseWriter, r *http.Request) {
  // ... 大部分代码保持不变
  // 删除这段代码
  // cookie := http.Cookie{
    // Name: "email",
    // Value: user.Email,
  // }
  // http.SetCookie(w, &cookie)
  // fmt.Println(w, user)
  // 在方法末尾添加这段代码
  err := u.SignIn(w, user)
  if err != nil {
    http.Error(w, err.Error(), http.StatusInternalServerError)
    return
  }
  http.Redirect(w, r, "/cookietest", http.StatusFound)
}
```

最后，重启你的服务器并尝试创建一个新账户并登录。此时，我们只想验证没有任何错误，因为在更新 `cookie` 测试之前，我们无法正确测试我们的记住记忆令牌 `cookie`。

注意：`cookie` 测试方法目前读取的是旧的 `cookie`，所以如果你奇怪为什么它与你创建或登录的任何新账户账户都不匹配，这可能就是原因。我们将在下一节中修复这个问题。

### 源代码

下面的链接包含了完整的源代码以及本节所有更改代码的差异（`diff`）。

已完成 - `book.usegolang.com/11.8.1`

变更 - `book.usegolang.com/11.8.1-diff`

## 11.8.2 限制页面访问

接下来，我们需要编写一些代码来限制用户尝试访问页面时的权限。长远来看，我们希望在发生这种情况时将他们重定向到登录页面，但目前我们将通过显示错误消息来这样做，以便验证我们的代码是否按预期工作。

幸运的是，我们的 `cookie` 测试已经包含了实现此操作所需的大半部分代码。在 `CookieTest` 方法中，我们已经处理了读取 `cookie` 和检查错误，因此我们想要做的第一件事是更新这些代码以读取我们创建的新记住记忆令牌。

打开用户控制器并跳转到 `CookieTest` 方法。

```bash
$ atom controllers/users.go
```

更新 `CookieTest` 方法以读取 `"cookie_test"` `cookie` 而不是 `"email"` `cookie`。

```go
func (u *Users) CookieTest(w http.ResponseWriter, r *http.Request) {
	cookie, err := r.Cookie("remember_token")
	if err != nil {
		http.Error(w, err.Error(), http.StatusInternalServerError)
		return
	}
}
```

接下来，我们将使用此 `cookie` 的值在数据库中搜索用户。为了做到，我们将使用用户控制器中的 `us` 字段，它是一个 `User` 实例。我们将使用在本章之前编写的用户服务中的 `ByRemember` 方法。

在获取 `cookie` 并检查错误后添加这段代码。简而言之，将其添加到我们刚刚写的代码下方。

## 11.8. 记住用户

```go
user, err := u.us.ByRemember(cookie.Value)
if err != nil {
    http.Error(w, err.Error(), http.StatusInternalServerError)
    return
}
fmt.Println(n, user)
```

如果 `ByRemember` 方法出现错误，我们将我们从数据库获取了用户，以确保它们是正确的。

如果发生错误，我们将输出错误消息。在生产环境中，这种信息可能包含敏感信息。理想情况下，我们应该将他们重定向到登录页面。

重启服务器并尝试创建账户并登录，以验证是否设置了 `cookie`。

```bash
go run main.go
```
