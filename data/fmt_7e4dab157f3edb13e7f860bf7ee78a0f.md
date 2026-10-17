
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

## 12.3. UserService 接口

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

### 源代码

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

## 12.4. 编写与组织验证代码

```go
func (ug *userGorm) Create(user *User) error {
  return ug.db.Create(user).Error
}
```

我们在这里做的几乎所有的工作都是在移动代码，但这没关系。
这正在帮助我们达到一个代码被恰善拆分的程度。

> 框图 12.7：userGorm 的 Create 方法现在变得非常简单了

值得注意的是，在我们进行这些更改时，提取出 userGorm 方法是如此简单，这很重要，而且随着后续的进行，它可能会变得更简单。除了让我们的代码更易管理和测试之外，这意味着我们还可以很容易地将数据库实现替换为另一个。例如，如果我们决定使用标准库带的 `database/sql` 包来代替 GORM，我们只需要将相对简单的 `userGorm` 类型替换为新类型，而我们剩余的所有代码 - 验证、归一化等 - 都将保持不变。

这就是为什么我说，你可以轻松地将本课程中使用的所有 GORM 代码替换为标准库；一旦我们清理了模型包，这样做仅涉及更改代码中非常微小的部分。

接下来是 `Update` 方法。这将非常相似；我们将创建一个带有 `userValidator` 接收者的新 `Update` 方法，然后将我们的验证代码移动到那里。

```go
// Update 如果提供了 remember token，则将对其进行哈希处理。
func (uv *userValidator) Update(user *User) error {
  if user.Remember != ""
    user.RememberHash = uv.hmac.Hash(user.Remember)
  }
}
```

```go
return uv.UserDB.Update(user)
func (ug *userGorm) Update(user *User) error {
    return ug.db.Save(user).Error
}
```

最后是 `Delete` 方法，工作流与之前相同。

```go
// 根据提供的 ID 删除用户
func (uv *userValidator) Delete(id uint) error {
    if id == 0 {
        return ErrInvalidID
    }
    return uv.UserDB.Delete(id)
}
func (ug *userGorm) Delete(id uint) error {
    user := User(Model: gorm.Model(ID: id))
    return ug.db.Delete(user).Error
}
```

既然我们已经从 `user-Gorm` 代码中移除了所有对 `hmac` 字段的引用，我们不再需要这个字段了。我们将更新代码移除它，因为它不再被使用。虽然这对于让我们的代码通过编译不是绝对必要的，但在开发过程中进行这样的清理工作是一个好主意。

首先，我们需要从 `userGorm` 的类型声明中删除该字段。

```go
type userGorm struct {
    db *gorm.DB
}
```

接下来，我们需要更新 `newUserGorm` 函数，并移除任何用于设置 `hmac` 字段的代码。

```go
func newUserGorm(connectionInfo string) (*userGorm, error) {
	db, err := gorm.Open("postgres", connectionInfo)
	if err != nil {
		return nil, err
	}
	db.LogMode(true)
	return userGorm(
		db,
	), nil
}
```

至此，我们简单的验证设置就完成了。我们现在准备好查看如何创建可重用的验证器，但首先让我们确保我们的代码正确编译并按预期运行。重启你的服务器并测试几个页面以确保功能正常。为了安全起见，请尝试重新登录。

```bash
$ go main.go
```

### 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异。

已完成 - book.usegolang.com/12.4.2

更改 - book.usegolang.com/12.4.2-diff

## 12.4.3 可重用验证

我们可以继续像在最后两个部分那样创建验证，但随着时间的推移，这将导致大量的重复代码和大量的错误检查。查看 `Create` 方法示例；如果我们想让用户能够更新密码，那么 `Create` 方法中的代码就需要复制过去，以便我们能够正确地对他们的新密码进行哈希。

我们不想反复重复自己，所以更好的方法是将这些验证和归一化拆解为可重用的函数。顺便说，为我们所有的验证函数定义单一的格式也会帮助，这样我们可以一次性运行它们，并在任何验证返回错误时立即停止，因为错误意味着我们无法继续执行该操作。

让我们从创建一个可重用的方法开始，允许我们使用 `bcrypt` 对用户密码进行哈希。这段代码与 `userValidator` 的 `Create` 方法中已有的大部分相同，但移动到了它自己的方法中。

```go
// bcryptPassword 使用应用范围内的盐和 bcrypt 对用户密码
// 进行哈希，bcrypt 会为我们处理加盐。
func (u *userValidator) bcryptPassword(user *User) error {
	pwBytes := []byte(user.Password + pwPepper)
	hashedBytes, err := bcrypt.GenerateFromPassword(pwBytes, bcrypt.DefaultCost)
	if err != nil {
		return err
	}
	user.PasswordHash = string(hashedBytes)
	return nil
}
```

## 第 12 章，数据的归一化与验证

## 12.4. 编写与组织验证代码

```go
type userValFn func(*User) error
```

函数类型与结构类型相似，区别在于它们定义了一个接收 `User` 并返回错误的函数。有什么意义？我们为什么想要为验证函数定义统一格式？使用这种方法的用处是，我们现在可以定义一个运行所有验证并返回任何错误的函数。

```go
func runUserFns(user *User, fns ...userValFn) error {
  for _, fn := range fns {
    if err := fn(user); err != nil {
      return err
    }
  }
  return nil
}
```
