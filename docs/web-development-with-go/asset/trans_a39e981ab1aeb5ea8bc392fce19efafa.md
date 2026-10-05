

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

退出此 `if` 语句后，我们知道 `user` 变量的 `Remember` 字段中应该有一个非空字符串值。如果它为空字符串，我们在语句内部的代码将生成一个新的记住记忆令牌（remember token），否则我们知道它已经设置了。

我们将使用记住记忆令牌创建一个 cookie，并使用 `http` 包通过传递到我们 `signIn` 方法的响应（response）来设置它。最后，如果我们执行到了这一步，说明没有任何错误，我们将返回 `nil`。

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

下一步是更新 `login` 和 `signup` 方法，以便在用户成功创建账户或登录后调用此方法。我们还将把用户重定向到 cookie 测试页面，这样我们就可以验证 cookie 是否已正确设置，而无需手动输入 URL。

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

在 `Login` 方法中，我们需要删除任何用于创建 cookie 的代码以及方法末尾的打印语句。我们不再需要手动创建 cookie 了，因为它已经由 `signIn` 方法处理了。

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

最后，重启你的服务器并尝试创建一个新账户并登录。此时，我们只想验证没有任何错误，因为在更新 cookie 测试之前，我们无法正确测试我们的记住记忆令牌 cookie。

注意：cookie 测试方法目前读取的是旧的 cookie，所以如果你奇怪为什么它与你创建或登录的任何新账户账户都不匹配，这可能就是原因。我们将在下一节中修复这个问题。

## 源代码

下面的链接包含了完整的源代码以及本节所有更改代码的差异（diff）。

已完成 - book.usegolang.com/11.8.1

变更 - book.usegolang.com/11.8.1-diff

## 11.8.2 限制页面访问

接下来，我们需要编写一些代码来限制用户尝试访问页面时的权限。长远来看，我们希望在发生这种情况时将他们重定向到登录页面，但目前我们将通过显示错误消息来这样做，以便验证我们的代码是否按预期工作。

幸运的是，我们的 cookie 测试已经包含了实现此操作所需的大半部分代码。在 `CookieTest` 方法中，我们已经处理了读取 cookie 和检查错误，因此我们想要做的第一件事是更新这些代码以读取我们创建的新记住记忆令牌。

打开用户控制器并跳转到 `CookieTest` 方法。

```bash
$ atom controllers/users.go
```

更新 `CookieTest` 方法以读取 "cookie_test" cookie 而不是 "email" cookie。

```go
func (u *Users) CookieTest(w http.ResponseWriter, r *http.Request) {
	cookie, err := r.Cookie("remember_token")
	if err != nil {
		http.Error(w, err.Error(), http.StatusInternalServerError)
		return
	}
}
```

接下来，我们将使用此 cookie 的值在数据库中搜索用户。为了做到，我们将使用用户控制器中的 `us` 字段，它是一个 `User` 实例。我们将使用在本章之前编写的用户服务中的 `ByRemember` 方法。

在获取 cookie 并检查错误后添加这段代码。简而言之，将其添加到我们刚刚写的代码下方。

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

重启服务器并尝试创建账户并登录，以验证是否设置了 cookie。

```bash
go run main.go
```

如果你想在没有设置 cookie 的情况下验证它是否工作，我们可以在无痕窗口中进行 cookie 测试。

## 源代码

下面的链接包含了完整的源代码以及本节所有更改代码的差异。

已完成 - book.usegolang.com/11.8.2

变更 - book.usegolang.com/11.8.2-diff

## 11.9 防止 cookie 受到 XSS 攻击

XSS 代表跨站脚本 [xss]，它是一种攻击类型，恶意第三方试图向 Web 应用程序注入 JavaScript 代码并像网站提供的那样运行。

例如，我可能会将用户名设置为：

```html
<script>alert("hi!");</script>
```

虽然这种用户名并不理想，但如果网站没有正确渲染，浏览器可能会解析为 HTML 并导致运行。

在这种情况下，我的用户名可能是：

```html
<script>
// 发送网络请求以让我访问所有
</script>
```

现在当你访问我的个人资料时，代码将执行并获得你所有的资源。这些可能是私人文档、私人代码或其他。重点是攻击者能够代表你发送网络请求。

## 11.9. 防止 cookie 受到 XSS 攻击

我们正在使用 `html/template` 包来缓解这个问题，因此这不太可能在我们身上发生，但始终尽可能安全。如果你不计划使用 JS 框架，或者你不打算使用 JavaScript 发网络请求，那么你真的不需要脚本访问你的 cookie，特别是身份验证 cookie。

###### 仅在需要时放宽安全性

虽然你可能为了以后决定使用 JavaScript 框架而跳过这一步，但我敦促你不要。

通常情况下，从谨慎角度考虑会更好，在绝对必要移除限制之前对 cookie 等内容尽可能多的限制。互联网上有无数例子，网站并不是因为单个漏洞而被黑客攻击，而是因为星象汇合，三个或四个单独看不足道的问题共同发生，导致了攻击者的完美风暴。

我们的应用程序不需要脚本访问 cookie，我们将限制 cookie 仅供由浏览器发起的请求，我们可以做到！如果以后发生变化，更新非常容易，你只需要更新几行代码。

我们将在用户控制器的 `signIn` 方法中进行更改，所以让我们开始打开源文件。

```bash
$ atom controllers/users.go
```

找到我们在 `signIn` 方法中构建的 cookie，并更新以包含 `HttpOnly` 字段的值为 `true`。

