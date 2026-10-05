

## 12.2. USERDB 接口

```go
db *gorm.DB
hhmac hash.HMAC
}
```

我们知道需要一个 `gorm.DB` 来与数据库进行交互，我也知道我们暂时需要 `hmac` 字段，所以我们现在将这两者都加上。一旦我们完成了验证代码，最终我们将会会对这段代码进行一些微调。

接下来，我们将更新代码，使得之前作为 `UserService` 一实现的全部 `UserDB` 方法都改为改用 `userGorm` 类型实现。为了实现这一点，我们将把每个现有方法的接收者（receiver）从 `UserService` 改为 `userGorm`。

## 框 12.6. 什么是接收者？

接收者是位于方法名称之前的参数。例如，在下面的代码中，接收者的类型为 `Dog`，并赋值给变量 `d`。

```go
type Dog struct { }
func (d Dog) Bark() {
	fmt.Println("woof!")
}
```

我们将从 `ByID` 方法开始，它目前的内容如下：

```go
func (us *UserService) ByID(id uint) (*User, error) {
```

## 第 12 章 数据的规范化与验证

现在，它以 `UserService` 指针作为接收者类型。我们将将其更新为指向 `UserGorm` 的指针。在下方的代码段中，我还将接收者变量从 `us` 重名为 `ug`，并更新了方法中的代码以匹配此更改，但你并不为了让代码运行而必须进行此更改。

```go
func (ug *UserGorm) ByID(id uint) (*User, error) {
    var user User
    db := ug.db.Where("id = ?",
```

我们将继续对目前由 `UserService` 类型实现并由 `UserDB` 接口定义的其余方法执行类似的修改。也就是说，我们需要更新以下方法：

- ByEmail
- ByRemember
- Create
- Update
- Delete
- Close
- DestructiveReset
- AutoMigrate

## 12.2. USERDB 接口

我们**不需要**更新 `Authenticate` 方法，所以请务必保持该方法不变。

我不会在书中展示每一个这些更改的代码片段，但处理过程与我们对 `ByID` 方法所做的相同。只需找到接收者并将其更新为 `userGorm` 类型而不是 `UserService` 类型即可。

如果你想双检你的代码，我建议参考本节末尾提供的源代码差异（diff）。

一旦你完成了所有更新，`userGorm` 现在应该已经实现了 `UserDB` 接口。我们可以通过向源码中添加以下内容来验证这一点：

```go
var _UserDB = &userGorm()
```

我们将此变量命名为 `_` 是因为我们不会使用它，而且我们不希望编译器对我们创建一个未使用的变量报错。然后，我们将此变量的类型设置为 `UserDB`，并将指向 `userGorm` 的指针赋值为值。假设我们的 `userGorm` 实现了 `UserDB` 接口，这段代码将正确编译。如果 `userGorm` 没有实现 `UserDB` 接口，我们在尝试编译代码时将得到错误。

> 注意：许多开发者可能会认为这实际上是一个测试，应该存储在测试文件中，但我经常发现，在源码中包含这样一个简单的验证是有用的，因为如果这种情况不再成立，它将不可避免地在某处导致编译错误。

我们将编写的下一个代码是一个用于实例化 `userGorm` 实例的函数。这与我们现有的 `NewUserService` 函数几乎完全相同，所以你可能会从那里复制代码作为起点。我们大部分时候只需要修改函数名和返回值。

## 第 12 章 数据的规范化与验证

```go
func newUserGorm(connectionInfo string) (*userGorm, error) {
  db, err := gorm.Open("postgres", connectionInfo)
  if err != nil {
    return nil, err
  }
  db.LogMode(true)
  hmac := hash.NewHMAC(hmacSecretKey)
  return &userGorm{
    db: db,
    hmac: hmac,
  }, nil
}
```

在部署之前，我们将进一步清理这段代码，但目前这样就可以了了。同样重要的一点是，我们也不导出这个函数，因为我们不希望 `models` 包之外的代码使用此函数实例化 `userGorm` 实例，即使 `userGorm` 类型没有导出，这仍然是可能的。

接下来，我们将更新 `UserService` 类型和 `NewUserService` 函数，包含一个嵌入的 `UserDB` 字段，该字段将由 `userGorm` 类型实现。我们可以利用刚刚写的 `newUserGorm` 函数来让事情变得简单一点。

```go
func NewUserService(connectionInfo string) (*UserService, error) {
  ug, err := newUserGorm(connectionInfo)
  if err != nil {
    return nil, err
  }
  return &UserService{
    UserDB: ug,
  }, nil
}
```

```go
type UserService struct {
  UserDB
}
```

现在，我们的 `UserService` 仍然拥有之前相同的方法，但大部分实现已经交给了嵌入的 `UserDB`。`UserService` 仅负责实现 `Authenticate` 方法。

## 12.2. USERDB 接口

我们在本节的最后一步是添加第三层也是最终的层——验证层。这一步目前不会做很多，但当我们开始添加验证代码时，我们需要一个地方。它的代码与我们之前讨论的 `UserDB` 非常相似，但它是未导出的类型，命名为 `userValidator`。

```go
// userValidator 是我们的验证层
type userValidator struct {
  UserDB
}
```

当我们开始向该接口填充方法时，我们将填充验证层，然后编写许多新的验证器和规范化器来将数据转换为数据库期望的格式。例如：

```go
func (uv *userValidator) ByID(id uint) (*User, error) {
  // 验证 ID
  if id < 0 {
    return nil, errors.New("Invalid ID")
  }
  // 如果有效，调用 UserDB
  return uv.UserDB.ByID(id)
}
```

> 注意：你不需要将此命名为 `userService`，可以命名为任何内容。我们只是为了明确它实现了什么接口。

我们的最后一步是更新 `NewUserService` 函数以变为 `userValidator`。

```go
func NewUserService(connectionInfo string) (*UserService, error) {
	ug, err := newUserGorm(connectionInfo)
	if err != nil {
		return nil, err
	}
	return &UserService{
		UserDB: userValidator{
			UserDB: ug,
		},
	}, nil
}
```

有了这些更改，我们现在准备好开始填充接口并编写代码。

