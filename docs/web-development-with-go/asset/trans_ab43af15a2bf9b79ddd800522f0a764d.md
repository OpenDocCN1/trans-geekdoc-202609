

## 第 9 章：创建用户模型

如果你还记得之前的内容，`gorm.Model` 类型将为我们包含 `id`、`created_at`、`updated_at` 和 `deleted_at` 字段，因此我们现在只需要手动清理字段是 `Name` 和 `Email`。

我们还将为 `Email` 字段添加一个标签，让 GORM 知道我们不希望此字段为空，并且我们希望通过唯一约束对其进行索引。这将确保我们所有的用户都有邮箱地址，并且没有两个用户共享同一个邮箱地址。

列表 9.2：创建 User 类型
```go
package models

import "github.com/jinzhu/gorm"

type User struct {
	gorm.Model
	Name string
	Email string `gorm:"not null;unique_index"`
}
```

现在我们已经有了一个数据类型，让我们来看看如何编写代码来让与数据库的交互变得更容易。

# 源代码

下面的链接包含了完成后的源代码以及本节中所有更改代码的差异（diff）。

- 完成版 - book.usegolang.com/9.1
- 更改版 - book.usegolang.com/9.1-diff

## 9.2. 创建 UserService 接口并查询用户

在第 8.4.5 节中，我们探索了使用 GORM 向 SQL 数据库写入记录，但为了简单起见，我们当时省略了很多细节。结果，我们能够直接与 `gorm.DB` 对象交互，并演示了如何使用 GORM 与数据库交互，但在大多数应用程序中，我们并不希望直接与 GORM 交互。

首先，我们最终可能想要将应用程序更改为使用 `database/sql` 包，或者完全使用另一个数据库。如果我们将 `gorm.DB` 对象散布在所有代码中，将来想要更改将非常困难。此外，在不设置真实数据库的情况下，测试我们的应用程序也将非常困难，而且我们会产生大量的重复代码。

我们并不是在代码的处处使用 GORM，而是要编写一个抽象层，定义我们的控制器将使用哪些方法，但隐藏这些实现细节。这将允许我们在将来更改数据库的实现细节，而无需更新任何控制器或视图代码。

> 框 9.2 什么是抽象层？

在编程中，抽象层是隐藏实现细节的一种方式。

以车辆为例——当你脚踩油门时，预期是引擎将为车轮提供动力，你的车会移动。这些具体的实现细节是无关的。你不在乎你的车是电动的、汽油的还是混合动力；只要油门仍然能让引擎提供动力并加速车辆，你就应该仍然能够驾驶它。

编程中的抽象层非常相似。你的大部分代码实际上并关心数据是如何保存的，或者正在使用什么数据库。唯一重要的是它调用了预期的 `Save` 函数，并且它提供的数据将被保存。通过这种方式编写代码，我们可以避免一次性编写所有内容，而是一次一次编写更多模块化的部分。

我们用户数据库的抽象层将被称为 `UserService`，它将是一个提供查询、创建和更新用户方法的类型。我们知道这一层需要访问 `gorm` 指针，所以我们可以从这里开始定义它。

```
$ atom models/users.go

type UserService struct {
  db *gorm.DB
}
```

我们知道需要用 GORM 打开数据库的连接，因此我们的下一步是编写一个函数来执行此操作，然后返回一个 `UserService` 对象。在编写创建类型代码时，我通常将函数命名为 `NewXXX`，其中 "XXX" 是它实例化的类型，所以我们将把新函数命名为 `NewUserService`。

在这个函数内部，我们将编写与上章节中用 GORM 连接数据库时编写的代码几乎相同的代码，但我们期望最终用户传递一个字符串来定义我们应该如何连接到数据库。我们还需要在导入中添加 Postgres 方言（dialect）。即使你使用自动导入工具，也需要执行这些，因为这个包没有被直接使用，但它为我们加载了 Postgres 驱动程序。

```
import (
"github.com/jinzhu/gorm"
"github.com/jinzhu/gorm/dialects/postgres"
)
// ..
func NewUserService(connectionInfo string) (*UserService, error) {
	db, err := gorm.Open("postgres", connectionInfo)
	if err != nil {
		return nil, err
	}
	db.LogMode(true)
	return &UserService{
		db: db,
	}, nil
}
```

> 框 9.3 为什么我们没有使用 `defer db.Close()`？

延迟函数调用在函数退出时执行，所以如果我们在 `NewUserService` 函数内部延迟（defer）关闭 DB，将导致在返回新的用户服务之前直接关闭数据库连接。如果没有活跃的数据库连接，我们的用户服务将变得毫无用处，所以这可能是一个坏主意。

由于我们没有在打开数据库连接时立即关闭它，我们将添加一个方法在完成工作后关闭连接。

```go
// 关闭数据库连接
func (us *UserService) Close() error {
	return us.db.Close()
}
```

最后，我们将为服务添加两个方法。第一个是允许我们通过 ID 获取用户的方法。第二个是用于销毁用户的函数。我们将第一个命名为 `ByID`，第二个命名为 `Delete`。

在未找到用户的情况下，我们将返回一个自定义错误。我们将这个错误命名为 `ErrNotFound`。虽然我们技术上可以直接返回这个错误，但那样控制器就需要知道这个特定的 GORM 错误。相反，我们选择返回自己的 `ErrNotFound`，这样模型包的用户就不了解 GORM。

```go
import (
    "errors"

    "github.com/jinzhu/gorm"
    "github.com/jinzhu/gorm/dialects/postgres"
)

var (
    // 当找不到资源时返回 ErrNotFound
    ErrNotFound = errors.New("models: resource not found")
)

// ByID 根据提供的 ID 查找用户。
// 如果找到了用户，我们将返回该用户的指针。
// 如果没有找到用户，我们将返回 ErrNotFound。
func (us *UserService) ByID(id uint) (*User, error) {
	var user User
	err := us.db.Where("id = ?", id).First(&user).Error
	switch err {
		case nil:
			return &user, nil
		case gorm.ErrNotFound:
			return nil, ErrNotFound
		case default:
			return nil, err
	}
}
```

这里的很多代码看起来很熟悉。例如，我们在上一节在 GORM 数据库连接上使用了 `Where` 方法。上一节可能没有做的是访问 `gorm.DB` 对象的 `Error` 字段，而 GORM 查询期间遇到的任何错误都存放在那里。我们这样做是为了确保捕获查询数据库时发生的任何错误。

一旦我们获取了错误，就会编写一个 `switch` 语句，根据错误尝试确定返回什么内容。如果没有错误值，它将是 `nil`，所以我们可以简单地返回查询的用户指针。相反，如果存在我们不希望返回的错误，我们将转而返回一个错误。

在这种情况下，我们首先查找 GORM 的 `ErrRecordNotFound`，这表示我们的查询执行正确，但我们没有根据提供的查询找到用户。虽然我们技术上可以直接返回这个错误，但那样控制器就需要知道这个特定的 GORM 错误。相反，我们选择返回自己的 `ErrNotFound` 错误，这样模型包的用户就不了解 GORM。

