
## 8.2. 设置 POSTGRESQL

**Listing 8.3:** 使用原始 SQL 查询记录。
```sql
SELECT *
FROM users
WHERE email = 'jon@calhoun.io'
AND age > 16;
```

## 8.2.4 收集连接到 Postgres 安装所需的信息

最后，你需要收集连接数据库所需的所有信息并将其记录。具体来说，我们需要知道主机（host）、端口（port）、用户（user）、密码（password）和数据库名称。

我们将在 Go 代码中使用这些信息来连接数据库，如果信息错误，在尝试连接数据库时可能会报错。

遗憾的是，这些信息会根据你安装 Postgres 的方式而异，因此我无法确定你应该使用什么。我做的是为你提供一些常用值，你可以利用它们来帮助确定安装指南中使用了哪个值。

你首先应该寻找的是主机和端口。如果你在本地安装了 Postgres，那么主机很可能是 `localhost`，端口可能是 `5432`。

接下来是用户（又角色）。在大多数教程中，你的用户将是 `postgres`，但另一个值是你的操作系统名称。要在 Mac OS 或 Linux 上找到此项，可以在终端中运行 `id -un`。我的用户名恰好是 `jon`，你的很可能是你在设置电脑时选择的内容。

如果你发现自己正在输入类似 `psql -U <something>` 的命令，那么 `<something>` 就是你的 Postgres 用户。**-U** 标志是你使用特定用户连接 Postgres 的方式。

### Table 8.1: PostgreSQL 连接参数和值。

| 参数 | 值（你的可能与此处列出的不同） |
| :--- | :--- |
| host | localhost |
| port | 5432 |
| user | postgres |
| password | <none> |
| dbname | lenslocked_dev |

之后，我们需要你的密码。这应该是显而易见的，因为大多数教程都让你设置了自己的值，如果你没有设置，可以使用空字符串作为密码。

最后，我们需要确定数据库名称，在我们的代码中将其列为 **dbname**。对于此项，你可能在安装期间创建了数据库，或者它可能与你的 Postgres 用户相同。

如果你在教程中创建了数据库，你将再次遵循这些步骤创建一个名为 **lenslocked_dev** 或 **<yourapp_dev>** 的数据库，以便一眼看出该数据库的用途。

一旦你有了所有这些信息，就把它像表 8.1 那样的表格记录下来。我在表格中提供了我将要使用的值，但你的可能不同。只需确保在接后的 Go 代码中使用你自己表格中的数据即可。

一旦准备好所有这些，你就可以开始在 Go 中使用 PostgreSQL 并准备进入下一节了！

## 8.3. 在 Go 和原始 SQL 中 Postgres

### 8.3 使用 Go 和原始 SQL 使用 Postgres

虽然 Go 在标准库中提供了 `database/sql` 包，但我们还需要安装一个 Postgres 特有的驱动程序。为此，我们将使用 `github.com/lib/pq`，它是用 Go 编写的，并通过了 SQL 驱动程序的兼容性测试。

为此，你需要再次使用 `go get` 命令。

- Listing 8.4: 安装 lib/pq。

```
$ go get -u github.com/lib/pq
```

### 8.3.1 使用 database/sql 包连接到 Postgres

接下来，我们需要编写一些实际使用这两个包的代码。这并不是我们在最终产品中将使用的，所以我们在 4.4 节中创建的 `exp` 目录将是这些代码存放的好处。

如果你还没有 `exp/main.go` 文件，应该创建一个。你可能还需要创建 `exp` 目录。

```
$ mkdir exp # 此目录可能已经存在
$ atom exp/main.go
```

删除你实验源文件中的所有内容。我们将从头开始，不需要任何现有的代码。

我们首先想要声明我们的包并指定导入项。我们将导入 `database/sql` 包以便访问 SQL 数据库，导入 `fmt` 包用于打印到终端和格式化字符串，最后是导入 `github.com/lib/pq` 包，它实现了 `database/sql` 包使用的 Postgres 驱动程序。

### Listing 8.5: 连接到 Postgres 代码开头。

```go
package main

import (
    "database/sql"
    "fmt"

    "github.com/lib/pq"
)
```

### Box 8.2. 为什么我们要导入一个不使用的包？

初看之下，Listing 8.5 中的代码看起来可能有点不同，你可能会问自己“那个下划线是在干什么？”

发生这种情况的简短解释是，Go 不允许我们导入代码中没有直接使用的包。

这是一个问题所在，因为我们需要导入 `github.com/lib/pq` 包，以便它的 `init()` 函数被调用，从而为 `database/sql` 包注册 "postgres" 驱动。

换句话说，除非我们导入了 `github.com/lib/pq` 包，否则我们无法连接到 Postgres 数据库。我们使用下划线导入包是为了它的副作用。

换句话说，下划线告诉编译器我们并没有刻意直接使用该包，但我们需要它的初始化代码运行。
