
```go
const (
    host = "localhost"
    port = 5432
    user = "postgres"
    password = "your-password"
    dbname = "lenslocked_dev"
)

type User struct {
    gorm.Model
    Name string
    Email string `gorm:"not null,unique_index"`
}

func main() {
    pgInfo := fmt.Sprintf("host=%s port=%d user=%s password=%s dbname=%s sslmode=disable", "
        host, port, user, password, dbname)
    db, err := gorm.Open("postgres", pgInfo)
    if err != nil {
        panic(err)
    }
    defer db.Close()

    db.AutoMigrate(&User{})
}
```

你也可以使用 `db.AutoMigrate` 函数来更新模型。例如，如果我们为 `User` 类型添加了 `Age int` 属性，然后使用 GORM 的自动迁移（auto-migrate），我们就会在用户表中得到一个 `age` 字段。

这使得迁移数据库表变得非常简单，但它也有局限性。`AutoMigrate` 只会创建不存在的内容，所以如果你已经有一个名为 `users` 的表，它就不会删除该表并尝试创建一个新表。同样，它不会删除列或将其替换为新类型，因为这两者都有无意中删除数据的风险。相反，你需要手动处理这些类型的迁移。

## 8.4. 使用 GORM 与数据库交互

### 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异对比（diff）。

完成版 - book.usegolang.com/8.4.3

更改版 - book.usegolang.com/8.4.3-diff

### 8.4.4 使用 GORM 记录记录

在使用 GORM 时，启用日志通常非常有用，这样你可以追踪后台运行了哪些 SQL 语句。当程序运行结果不符合预期，你需要深入调查并调试时，这极其有用。

你可以通过调用 `gorm.DB` 类型提供的 `LogMode` 方法来启用 GORM 的日志。打开你的实验性 `main.go` 源文件，我们现在来启用它。

```
$ atom exp/main.go
```

`LogMode` 方法接收一个参数 - 布尔值（`true` 或 `false`）。当你想要启用日志时应为 `true`，想要禁用时应为 `false`。我们将在打开数据库连接并检查错误后的主函数中调用它。

```go
func main() {
    sqlInfo := fmt.Sprintf("host=%s port=%d user=%s " + 
        "password=%s db=%s sslmode=disable",
	host, port, user, password, dbname)
    db, err := gorm.Open("postgres", sqlInfo)
    if err != nil {
        panic(err)
    }
    defer db.Close()

    db.LogMode(true)
    db.AutoMigrate(&User{})
}
```

启用日志后，当运行 SQL 语句时，我们将开始看到类似下面的输出。

```
(/Users/jon/go/src/lenslocked.com/exp/main.go:35)
[2017-07-18 17:04:12] [6.85ms] CREATE TABLE "users" ...

(/Users/jon/go/src/lenslocked.com/exp/main.go:35)
[2017-07-18 17:04:12] [1.18ms] CREATE INDEX ...

(/Users/jon/go/src/lenslocked.com/exp/main.go:35)
[2017-07-18 17:04:12] [00ms] CREATE INDEX ...
```

只有在 SQL 语句实际执行时你才会看到这些输出，所以如果你已经创建了 `users` 表，就不会看到这些输出。如果你愿意，可以删除 `users` 表然后重新运行代码看到上面的输出。

### 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异对比。

完成版 - book.usegolang.com/8.4.4

更改版 - book.usegolang.com/8.4.4-diff

### 8.4.5 使用 GORM 创建记录

结合之前的章节，我们将编写一个程序，询问用户的姓名和电子邮件地址，然后使用这些信息在数据库中创建记录。示例 28 展示了如何使用 GORM 创建新记录。我们首先创建一个 `User` 实例并填充 `Name` 和 `Email` 属性。我们不需要设置 `gorm.Model` 提供的属性，因为它们由 GORM 自动填充。`db.Create()` 返回一个 `gorm.DB` 实例，因此我们可以检查 `Error` 以验证创建是否成功。

示例 28：使用 GORM 创建新记录

```go
name, email := // 从用户获取姓名和电子邮件
u := &User{
    Name: name,
    Email: email,
}
if err := db.Create(u).Error; err != nil {
    panic(err)
}
fmt.Printf("%+v\n", u)
```
如果我们每次运行程序都使用相同的电子邮件，最终会得到类似 `pq: duplicate key violates unique constraint "users_email"` 的错误，这意味着你正在写入数据库中已存在的电子邮件。为了解决这个问题，创建一个询问用户姓名和电子邮件的函数很好。在示例 29 中，我将之前章节的代码整合在了一起；我还提供了 `getInfo()` 函数来询问用户的姓名和电子邮件，但这里不会详细介绍其中的细节。只需注意，它每次运行程序时都会询问你的姓名和电子邮件，并使用这些值来创建新用户。

```
$ atom exp/main.go
```

### 示例 29：使用 GORM 创建动态记录

```go
package main

import (
    "bufio"
    "fmt"
    "os"
    "github.com/inzhu/gorm"
    "github.com/lib/pq"
)
const (
    host = "localhost"
    port = 5432
    user = "postgres"
    password = "your-password"
    dbname = "lenslocked_dev"
)
type User struct {
    gorm.Model
    Name string
    Email string `gorm:"not null,unique_index"`
}
func main() {
    psqlInfo := fmt.Sprintf("host=%s&port=%d&user=%s&password=%s&dbname=%s&sslmode=disable",
        host, port, user, password, dbname)
    db, err := gorm.Open("postgres", psqlInfo)
    if err != nil {
        panic(err)
    }
    defer db.Close()
    db.LogMode(true)
    db.AutoMigrate(&User{})

    name, email := getInfo()
    u := User{
        Name: name,
        Email: email,
    }
    if err = db.Create(u).Error; err != nil {
        panic(err)
    }
    fmt.Printf("%+v\n", u)
}

func getInfo() (string, string) {
    reader := bufio.NewReader(os.Stdin)
    fmt.Println("What is your name?")
    name, _ = reader.ReadString('\n')
    name = strings.TrimSpace(name)
    fmt.Println("What is your email?")
    email, _ = reader.ReadString('\n')
    email = strings.TrimSpace(email)
    return name, email
}
```

运行几次示例 29 中的代码，在数据库中创建几个用户。在下一节中，当我们开始查询查询特定用户时，将使用这些用户。

```
$ go run exp/main.go
```

### 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异对比。

完成版 - book.usegolang.com/8.4.5

更改版 - book.usegolang.com/8.4.5-diff

### 8.4.6 使用 GORM 查询单条记录

GORM 提供了多种查询记录的方法，但它们本质上只是编写 SQL 的辅助工具，所以很容易上手。

### 框 8.4. 你可能想在此处启用日志

在 8.4.4 节中，我们讨论了如何启用 GORM 日志，这会让它开始输出其尝试执行的每个 SQL 查询的信息。

在本节中启用日志是有帮助的，因为这有助于明确代码段在做什么，从而查看其生成的 SQL。因此，我建议在本节的剩余部分启用 GORM 日志，并测试每个示例以查看执行了哪些 SQL。

通常情况下，我倾向于在所有开发环境中启用此功能，这样我就可以方便地调试问题。

## 8.4. 使用 GORM 与数据库交互

```go
if db.Error != nil {
    panic(db.Error)
}
fmt.Println(u)
```

在代码列表 8.30 中，我们正在告诉 GORM，我们希望获取数据库中的第一个用户并将其存储在 `u` 对象中。通过传递一个 `user` 对象的地址，GORM 知道要查询 `users` 表，并知道将结果记录放入作为第一个参数传递的对象中。

如果发生错误，它将出现在我们的 `db` 对象上，因此在我们在使用 `user` 对象之前，需要需要检查 `db.Error` 是否有值。在接后的每个示例中，我们都会这样做，这是你在使用 GORM 时可以遵循的通用模式。它通常不返回错误，而是经常将错误附加到 `db` 对象上。

# 框 8.5. 额外的 SQL 是从哪里来的？

如果你开启了日志，你可能会问自己：“我的 SQL 查询中所有额外的 SQL 代码是从哪里来的？”我们没有在查询中写任何关于 `deleted_at` 字段为 `NULL` 的内容，也绝对没有为 SQL 查询指定顺序。

默认情况下，GORM 假设你使用 `deleted_at` 字段将记录标记为删除，而不是实际上从数据库中删除该记录。结果是，它默认会忽略任何为该字段设置了值的记录。

GORM 还会为查询设置默认顺序，以我们的我们的查询提供更多一致性。因此，当你调用 `First()` 方法时，可以放心它将始终返回 ID 的记录，除非你的查询指定了不同的顺序来排序结果。

# 列表 8.31：查询 id=1 的第一个用户

```go
var u User
id := 1

db.First(&u, id)
if db.Error != nil {
    panic(db.Error)
}
fmt.Println(u)
```

我们在列表 8.31 中的第二个示例与第一个示例非常相似，不同的是我们现在为 `First()` 方法提供了第二个参数——一个 ID。

GORM 允许我们将 ID 作为 `First()` 方法的第二个参数，这是一种查询具有特定 ID 对象的方便方法，而无需编写 `WHERE` 语句。我们最终会在代码中深入探讨这一点。

# 列表 8.32：使用 Where() 方法查询

```go
var u User
maxID := 3

db.Where("id <= ?", maxID).First(&u)
if db.Error != nil {
    panic(db.Error)
}
fmt.Println(u)
```

列表 8.32 是我们的第三个示例，演示了如何链用 `Where()` 方法和 `First()` 方法来创建一个 `WHERE` 查询。在这个示例中，我们正在寻找任何 ID 小于或等于提供的 id 的用户，在这种情况下该 id 正好是 3。

GORM 提供了许多如 `Where()` 这样的辅助方法，这些方法可以链在一起以创建更复杂的查询，你可以在 GORM 查询文档中找到它们大多数方法的示例。

## 8.4. 使用 GORM 与数据库交互

在使用这些查询时，你可能已经注意到我们使用 `?` 字符而不是像在使用 `database/sql` 包时使用的 `$1` 和 `$2`。它们的效果是相同的，但因为我们没有编号的参数，如果我们打算在查询的多个位置使用同一个参数，就需要多次包含该参数。

```go
Listing 8.33：使用已有的用户查询
```

var u User

u.Email = "jon@calhoun.io"

db.Where(u).First(&u)

if db.Error != nil {

    panic(db.Error)

}

fmt.Println(u)

```

除了用字符串查询外，你还可以通过向 `Where()` 方法传递与你正在查找的内容匹配的模型来查询。在列表 8.33 中，我们通过在 `User` 对象上设置邮箱地址，然后将该对象传递给 `Where()` 方法，来搜索邮箱地址为“jon@calhoun.io” 的用户。

这对于构建更复杂的查询非常有用，因为你可以在最终执行查询之前，让代码的不同部分设置 `user` 对象的不同属性，但有时也可能会让人困惑，因为一个你没有预料会被设置的属性可能会影响你的查询。

使用 GORM 查询还有许多其他方法，我们将在整本书中涵盖其中，但与其一次性学习所有方法，我建议你等到需要新查询时再查看 GORM 文档以确定如何创建你所需的内容。这可以让你立即开始工作，并确保你只学习你在实践中实际会用到的东西。

### 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异（diff）。

完成 - book.usegolang.com/8.4.6

更改 - book.usegolang.com/8.4.6-diff

### 8.4.7 使用 GORM 查询多条记录

使用 GORM 查询多条记录与查询单个记录几乎相同，只是我们将使用 `Find()` 方法而不是 `First()` 方法，并且我们将传递一个 `users` 的切片而不是单个用户。

列表 8.34：查询多个用户
```go

var users []User

db.Find(&users)

if db.Error != nil {

    panic(db.Error)

}

fmt.Println("Retrieved", len(users), "users.")

fmt.Println(users)

```

在底层，`Find()` 和 `First()` 的主要区别在于 `First()` 会自动在查询中添加 `LIMIT 1`，因为我们只需要一个项目。

### 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异（diff）。

完成 - book.usegolang.com/8.4.6

更改 - book.usegolang.com/8.4.6-diff

## 8.4. 使用 GORM 与数据库交互

完成 - book.usegolang.com/8.4.6

更改 - book.usegolang.com/8.4.6-diff

## 8.4.8 使用 GORM 创建相关模型

在我们学习 `database/sql` 包之前，我们创建了额外的表。在本节中，我们将使用 GORM 创建订单表。

我们需要做的第一件事是创建 `Order` 类型。

```go

type Order struct {

  gorm.Model

  UserID uint

  Amount int

  Description string

}

```

在 Go 代码中值得关注的部分是 `UserID` 是一个无符号整数。我们将编写一个函数来处理保存到数据库的数据并让它处理错误。

```go

func createOrder(db *gorm.DB, user User, amount int, desc string) {

  db.Create(&Order{

    UserID: user.ID,

    Amount: amount,

    Description: desc,

  })

  if db.Error != nil {

    panic(db.Error)

  }

}
```
