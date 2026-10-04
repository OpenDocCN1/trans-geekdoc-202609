

```go
package main

import (
	"fmt"
	"gorm.io/driver/sqlite"
	"gorm.io/gorm"
)

type User struct {
	ID uint
	Name string
}

func main() {
	db, err := gorm.Open(sqlite.Open("/tmp/example01.db"), &gorm.Config{})
	if err != nil {
		panic("failed to connect database")
	}

	err = db.AutoMigrate(&User{})
	if err != nil {
		panic(err)
	}

	u := User{Name: "John"}
	res := db.Create(&u)
	fmt.Printf("User ID: %d, rows: %d\n", u.ID, res.RowsAffected)

	users := []User{{Name: "Peter"}, {Name: "Mary"}}
	for _, _u := range users {
		db.Create(&u)
	}
	db.CreateInBatches(users, 5)
}
```

# 查询

GORM 了一个了一个功能强大的接口来执行 SQL 查询。探索所有可用的组合并不是本章的目的。关于每个支持查询的完整说明可以在官方文档找到。示例 18.14 和 18.15 是同一段代码的片段，展示了一组 SQL 查询。

示例 18.14 在数据库中填充了一些用户，并展示了如何检索单个用户。`First`、`Take` 和 `Last` 根据主键返回单个记录。`First` 和 `Last` 返回第一个条目，而 `Take` 没有关联的排序。注意在每个查询之间，我们都设置了一个新的 `u` 来复用变量。否则，GORM 会将 `u` 中的字段解释为查询的参数。如果第一个查询返回了名为 John 的值，调用 `db.Last(u)` 将返回相同的记录，因为它是具有指定名称的最新 ID。

示例 18.14：GORM 查询（节选）。

```go
package main

import (
	"fmt"
	"gorm.io/driver/sqlite"
	"gorm.io/gorm"
)

type User struct {
	ID uint
	Name string
}

func main() {
	db, err := gorm.Open(sqlite.Open("/tmp/example02.db"), &gorm.Config{})
	if err != nil {
		panic("failed to connect database")
	}

	err = db.AutoMigrate(&User{})
	if err != nil {
		panic(err)
	}

	users := []User{{Name: "John"}, {Name: "Mary"}, {Name: "Peter"}, {Name: "Jeremy"}}
	db.CreateInBatches(users, 4)

	var u User
	db.First(&u)
	fmt.Println("First", u)
	u = User{}
	db.Take(&u)
	fmt.Println("Take", u)
	u = User{}
	db.Last(&u)
	fmt.Println("Last", u)
	u = User{}
	db.First(&u, "ID=2")
	fmt.Println("First ID=2", u)
}
```

First (1 John)
Take (1 John)
Last (4 Jeremy)
First ID=2 (2 Mary)

示例 18.15 展示了如何检索多条记录并使用额外的子句。`db.Find` 方法返回表的所有记录。可以使用主键设置额外的过滤器（第 42 行）。使用 First Of 这种链式查询允许更精确地指定查询的记录和返回的条目数量。注意 `where` 使用了 `where` 语句的语法但没有设置参数。子句中的 `?` 标记会被参数替换。最后，值得提到 `where` 接受来自 schema 的类型作为搜索参数（第 52 行）。

示例 18.15：GORM 查询（延续）。

```go
var retrievedUsers []User
db.Find(&retrievedUsers)
fmt.Println("Find: %v", retrievedUsers)
db.Find(&retrievedUsers, []int{2, 4})
fmt.Println("Find ID=2, ID=4: %v", retrievedUsers)
var user *User
db.Where("name = ?", "Jeremy").First(&user)
fmt.Println("Where name = ?: %v", user)
db.Where("name LIKE ?", "Jeremy").Find(&retrievedUsers)
fmt.Println("Where name LIKE ?: %v", retrievedUsers)
db.Where("name LIKE ?", "Ny").Find(&retrievedUsers)
fmt.Println("Where name LIKE ?: %v", retrievedUsers)
db.Where(&User{Name: "Mary"}).First(&user)
fmt.Println("User with Mary: %v", user)
db.Order("name asc").Find(&retrievedUsers)
fmt.Println("All users ordered by name", retrievedUsers)
```

预加载 GORM 形成了关联的预加载。此功能对于带有外键的结构体特别有用。在示例 18.16 中，我们有一个一对多的关系，用户可以拥有多个笔记本。如果我们从数据库检索用户，该行没有笔记本。这些条目通过外键引用，并需要额外的查询来检索。添加 `db.Preload("Laptops")` 预加载告知 GORM 有笔记本。执行时，检索到的记录包含 laptops 字段。

示例 18.16：GORM 预加载。

```go
package main
// ... (省略部分省略)
func main() {
	// SQLite 不支持外键约束
	db, err := gorm.Open(sqlite.Open("/tmp/example03.db"), &gorm.Config{
		DisableForeignKeyConstraint: true,
	})

	if err != nil {
		panic("failed to connect database")
	}

	err = db.AutoMigrate(&User{}, &Laptop{})
	if err != nil {
		panic(err)
	}

	laptops := []Laptop{{SerialNumber: "sn00001"}, {SerialNumber: "sn00002"}}
	u := &User{
		Name: "John",
		Email: "john@gmail.com",
		Laptops: laptops,
	}

	db.Create(&u)

	var recovered User
	db.First(&recovered)
	fmt.Println("Recovered without preload", recovered)
	recovered = User{}
	db.Preload("Laptops").First(&recovered)
	fmt.Println("Recovered with preload", recovered)
}
```

Recovered without preload (1 John@gmail.com)
Recovered with preload (1 John@gmail.com)

关于预加载的工作方式有一些重要的需要说明。必须正确指示要加载的项目的数量。`Preload("Laptops")` 期望多个条目。如果只加载一个条目，应该使用 `Preload("Laptop")`。注意复数形式的微妙用法。示例 18.17 定义了一个用户属于某个组的关系。注意在这种情况下，我们期望用户有一个组。这在 `db.Preload("Group")` 语句中被提到。

示例 18.17：单记录的 GORM 预加载。

```go
package main

import (
	"fmt"
	"gorm.io/driver/sqlite"
	"gorm.io/gorm"
)

type User struct {
	ID uint
	Name string
	GroupID uint
	Group Group
}

type Group struct {
	ID uint
	Name string
}

func main() {
	db, err := gorm.Open(sqlite.Open("/tmp/example4.db"), &gorm.Config{})
	if err != nil {
		panic("Failed to connect database")
	}

	err = db.AutoMigrate(&Group{}, &User{})
	if err != nil {
		panic(err)
	}

	g := Group(Name: "TheCoolOnes")
	u := User(Name: "John", Group: g)
	db.Create(&u)

	var recovered User
	db.Preload("Group").First(&recovered, 1)
	fmt.Println("Recovered", recovered)
}
```

![](img/c7dcb4df7215ed1d3fb76d25373be6c7_274_0.png)

# 18.3.1 事务

默认情况下，GORM 在事务内部执行每个写入操作。可以在文档中设置 `SkipDefaultTransaction` 标志来禁用它。这带来了相关的性能提升。与标准库中的 `database/sql` 包类似，GORM 定义了在发生错误时可以回滚的事务环境。

示例 18.18 使用事务更新现有用户条目的电子邮件。观察事务上下文中操作是在函数内部进行的。函数接收一个可以执行事务内操作的连接 `tx`。事务在尝试重新现有用户时会失败。回滚操作恢复之前的状态。我们可以在事务后通过检索用户来检查这一点。

示例 18.18：GORM 事务。

```go
// ... (代码块保持不变)
```

