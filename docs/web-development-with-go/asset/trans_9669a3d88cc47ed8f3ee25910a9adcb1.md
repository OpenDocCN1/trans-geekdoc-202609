
接下来，我们需要更新现有的类型使其不再被导出。我们还需要添加一个嵌入的 `UserDB`，以便完整地实现 `UserService` 接口。读取这一行：

```go
type UserService struct {
```

将其更新为以小写字母开头，以便不再被导出。

```go
type userService struct {
    UserDB
}
```

我们还需要更新之前由 `UserService` 实现的所有方法的接收者（receiver）。最重要的是，我们需要更新 `Authenticate` 方法。

```go
// 开头的 (*UserService) 变为
// (us *userService) - 注意类型中的 u 是小写的。
func (us *userService) Authenticate(email, password string) (+User, error) {
// ... 实现部分完全没有变化。
}
```

我们的 `NewUserService` 函数现在也失效了，所以我们需要更新它，使其返回一个接口而不是特定类型的指针。我们还需要更改部分代码来构造我们返回的用户服务。这在下方的注释中进行了解释。

```go
// 此处不再返回指针！接口可以为 nil，
// 所以我们在这里不需要返回指针。不要忘记
// 更新我们删除的这一行结尾 * 字符
// 我们写的是 (UserService, error)
func NewUserService(connectionInfo string) (UserService, error) {
    ug, err := newUserGorm(connectionInfo)
    if err != nil {
      return nil, err
    }
```

## 12.3. USERSERVICE 接口

```go
// 我们还需要更新构造用户服务的方式。
// 我们不再有 UserService 类型可以构造了，
// 而是需要使用 userService 类型。
// 这仍然是一个指针，因为我们实现
// UserService 的函数使用了指针接收者。例如：
// func (u *userService) <- 这使用了指针
return &userService{
    UserDB: uValidator{
        UserDB: ug,
    },
    },
}
```

注意：很容易遗漏我们在上一个函数中更改了返回类型这一事实，但这是一个非常重要的更改。

我们的下一步可能是验证我们的 `userService` 类型是否实现了 `UserService` 接口。这可以按照我们处理 `userGorm` 类型的方法来完成。

```go
var UserService = &userService()
```

最后，我们需要对用户控制器（users controller）进行一些微调。它目前期望一个 `UserService` 的指针，但我们不再需要它是一个指针，因为它是一个接口。

打开用户控制器的源文件。

```bash
$ atom controllers/users.go
```

我们将更新 `NewUsers` 函数以及 `Users` 类型，使它们都不再期望 `UserService` 的指针。也就是说，我们将从代码中移除几个星号（*）。

## 第 12 章 数据的归一化与验证

```go
func NewUsers(us models.UserService) *Users {
    return &Users{
        NewView:  views.NewView("bootstrap", "users/new"),
        LoginView: views.NewView("bootstrap", "users/login"),
        us:        us,
    }
}

type Users struct {
    NewView   views.View
    LoginView views.View
    us        models.UserService
}
```

完成这些后，我们应该更新了 `UserService`，代码应该可以再次编译。请尝试运行你的代码以验证其运行正常。

```bash
$ go run main.go
```

## 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异（diff）。

已完成 - book.usegolang.com/12.3

查看更改 - book.usegolang.com/12.3-diff

## 12.4. 编写与组织验证代码

现在我们已经将代码分成了不同的层，准备好开始将验证代码移动到 `userValidator` 类型的方法中了。这将允许我们将这些代码与数据库交互分离开。

我们将在 `userValidator` 内部同时进行归一化和验证，因此我们经常将这一层称为“验证”层，但它实际上包含了这两项任务。正如本章前面所述，这样做是因为这两者之间的联系太紧密了。

在接下来的几个小节中，我们将开始以最直接的方法将代码移动到 `userValidator`。之后，我们将研究如何开始创建可重用的验证函数，这将使我们在在本章剩余部分中只需编写为用户所需的验证和归一化函数。

### 12.4.1 直接的方法

我们将从观察编写和组织验证代码最直接的方法开始。也就是说，我们将简单地将代码移动到 `userValidator` 类型中。

我们将在 `users` 模型中工作，所以首先打开我们的源文件。

```bash
$ atom models/users.go
```

我们将检查源码，查看 `userGorm` 方法中是否有任何看起来像归一化或验证的代码。然后，我们将这些代码移动到 `userValidator` 类型相同的方法中。

`ByID` 和 `ByEmail` 没有任何验证逻辑，所以我们可以安全地跳过它们。`ByRemember` 包含了用于哈希 remember token 的代码，我认为这属于一种归一化。我们正在将 remember token 转换为我们期望持久化到数据库的格式。

我们将此代码从 `userGorm` 的 `ByRemember` 方法移动出来，并放入与 `userValidator` 关联的新的 `ByRemember` 方法中。

## 12. 数据的归一化与验证

我们将先开始编写新代码，然后回来删除旧代码。

```go
// ByRemember 将对 remember token 进行哈希
// 并返回用户。此方法期望
// 并且我们调用下一层。
func (uv *userValidator) ByRemember(token string) (*User, error) {
    rememberHash := uv.hmac.Hash(token)
    return nil,
}
```

我们在 `userValidator` 类型上创建了一个 `ByRemember` 方法，但我们遇到了一个问题。我们的 `userValidator` 目前没有 `hmac` 字段。为了修复这个问题，我们将为 `userValidator` 添加 `hmac` 字段。

```go
type userValidator struct {
    UserDB
    hmac
}
```

我们需要确保也实例化这个字段。目前我们将在 `NewUserService` 函数内部处理它。

```go
func NewUserService(connectionInfo string) (UserService, error) {
    ug, err := newUserGorm(connectionInfo)
    if err != nil {
        return nil, err
    }
    hmac := hash.NewHMAC()
    uv := &userValidator{
        hmac: hmac,
        UserDB: ug,
    }
    return &userService{
        UserDB: uv,
    }, nil
}
```

接下来，我们需要从 `userGorm` 的 `ByRemember` 方法中移除代码。我们还需要更新参数以反映代码的实际操作。

```go
// ByRemember 根据给定的 hash 查找用户
// 并返回该用户。
func (ug *usergorm) ByRemember(hash string) (*User, error) {
	var user User
	err := ug.Where("remember_hash = ?", hash).First(&user)
	if err != nil {
		return nil, err
	}
	return &user, nil
}
```

虽然我们的代码功能是相同的，但现在当我们调用 `userService` 类型时将会发生方法链：方法将委托给 `userValidator` 方法。此时，我们的代码将通过哈希归一化 remember token，然后调用链中的下一个方法——`usergorm` 的 `ByRemember` 方法。

随着验证变得越来越复杂，这种分离将使管理代码变得容易得多。

### 12.4.2 更多验证示例

在本节中，我们将更新 `Create`、`Update` 和 `Delete` 方法，以展示更多如何将代码与数据库交互分离的示例。完成后，我们还将清理 `usergorm` 类型，因为它不再需要目前拥有的 `hmac` 字段。

我们将从 `usergorm` 的 `Create` 方法开始，它目前包含大量的验证和归一化代码。为了更新此方法，我们将在 `userValidator` 类型上创建一个新方法，其中包含所有这些逻辑，并从现有方法中移除它们。

```go
// Create 创建提供的用户并回填数据
// 如 ID、CreatedAt 和 Updated 字段。
func (uv *userValidator) Create(user *User) error {
	pwBytes := []byte(user.Password + userPwPepper)
	hashedBytes, err := bcrypt.GeneratePassword(pwBytes)
	if err != nil {
		return err
	}
	user.Password = string (hashedBytes)
	if user.Remember == "" {
		token, err := rand.RememberToken()
		if err != nil {
			return err
		}
		user.Remember = token
	}
	user.RememberHash = uv.hmac.Hash(user.Remember)
	return uv.DB.Create(user)
}

// 现在 usergorm 的版本变为...
```

