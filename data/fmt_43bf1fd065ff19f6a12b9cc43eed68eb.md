
MINGW64:/HOME/code/go/src/github.com/marklewin/go-web-succinct...

simplew@LAPTOP-QVFESMV9 MINGW64 --code/go/src/github.com/marklewin/go-web-succinct

ly/ch03/connect-db (master)

$ go run main

2017/02/06 18:05:59 Connected.

simplew@LAPTOP-QVFESMV9 MINGW64 --code/go/src/github.com/marklewin/go-web-succinct

ly/ch03/connect-db (master)

$ _

```
图 12：验证与数据库的连接

现在我们可以连接到 "world" 数据库，并对其执行查询并将结果返回给用户了。但首先，让我们检查 `sql.DB`。

注意上一个代码示例，我们正在使用包含 `sql.DB` 的 `database` 变量来访问数据库。

`sql.DB` 并不是数据库——数据库存储在 `dbConn` 中——相反，它是 `database/sql` 程序包对数据库的抽象。在我们的示例中，它指的是 MySQL 数据库，但由于我们可以使用 `database/sql` 与许多不同的数据源进行交互，它也可以很容易是本地文件或某些进程内数据存储（如 `memcache`）。

`sql.DB` 会代表你处理很多工作，包括数据库连接的打开、关闭和池化。

除非你的应用程序需要，否则不要反复打开和关闭数据库。`sql.DB` 对象被设计为长生命周期，你与数据库的所有交互都将通过 `sql.DB` 完成。但是，你必须确保在完成使用后通过 `sql.DB.Close` 关闭连接，以便它们可以返回池中。

> 提示：如果你需要给短生命周期的函数访问 `sql.DB`，请将其作为参数传递给函数，而不是在函数内部创建新连接。

我们操之过急了。我们还没有对数据库做过任何操作。

让我们现在纠正这一点。

以下代码根据用户在浏览器 http://localhost:8999/ 地址栏中输入的任何内容，查询 "world" 数据库的 City 表。

```go
package main

import (
    "database/sql"
    "fmt"
    "log"
    "net/http"
    "github.com/go-sql-driver/mysql"
)

type City struct {
    Name string
    CountryCode string
    Population int
}

var database *sql.DB

func main() {
    db, err := sql.Open("mysql",
        "root:password@tcp(127.0.0.1:3306)/world")
    if err != nil {
        log.Println("Could not connect!")
    }
    database = db
    log.Println("Connected.")
    http.HandleFunc("/%s", showCity)
    http.ListenAndServe(":8999", nil)
}

func showCity(w http.ResponseWriter, r *http.Request) {
    city := &City{}
    queryParam := "%s" + r.URL.Path[1:] + "%s"
    rows, err := database.Query("SELECT Name, CountryCode, Population FROM city WHERE Name LIKE ?", queryParam)
    if err != nil {
        log.Fatal(err)
    }
    defer rows.Close()
```
```go
for rows.Next() {
    err := rows.Scan(&city.Name, &city.CountryCode,
        city.Population)
    if err != nil {
        log.Fatal(err)
    }
    fmt.Fprintf(w, "%s (%s): %d\n", city.Name,
        city.CountryCode, city.Population)
}
err = rows.Err()
if err != nil {
    log.Fatal(err)
}
```

这里是我们用于 City 表行的 Go 结构体：

```go
type City struct {
    Name string
    CountryCode string
    District string
    Population uint32
}
```

接下来，让我们定义一个变量，在连接数据库时用于存储数据库的句柄：

```go
var database *sql.DB
```

最后，我们准备好连接到数据库了。我们通过序列化服务器主机、端口号、初始数据库和密码字符串来构建连接字符串。

接下来，我们尝试通过调用 `database/sql.Open` 方法来连接，传入驱动类型和连接字符串：

```go
dbConn := fmt.Sprintf("%s:%s@tcp(%s)/%s", dbUser, dbPass, dbHost, dbDatabase)
db, err := sql.Open("mysql", dbConn)
```

这会返回一个 `sql.DB` 实例。

完整的代码位于代码列表 7 中。

```go
package main

import (
    "database/sql"
    "log"
    _ "github.com/go-sql-driver/mysql"
)

var database *sql.DB

func main() {
    db, err := sql.Open("mysql", "root:password@tcp(127.0.0.1:3306)/world")
    if err != nil {
        log.Println("Could not connect!")
    }
    database = db
    log.Println("Connected.")
}
```

如果一切进展顺利，我们应该在终端提示符处收到一条消息，告诉我们现在已连接到 MySQL 服务器。

```
MINGW64:/HOME/code/go/src/github.com/marklewin/go-web-succinct...

simplew@LAPTOP-QVFESMV9 MINGW64 --code/go/src/github.com/marklewin/go-web-succinct

ly/ch03/connect-db (master)

$ go run main

2017/02/06 18:05:59 Connected.

simplew@LAPTOP-QVFESMV9 MINGW64 --code/go/src/github.com/marklewin/go-web-succinct

ly/ch03/connect-db (master)

$ _
```

图 12：验证与数据库的连接

现在我们可以连接到 "world" 数据库，并对其执行查询并将结果返回给用户了。但首先，让我们检查 `sql.DB`。

注意上一个代码示例，我们正在使用包含 `sql.DB` 的 `database` 变量来访问数据库。

`sql.DB` 并不是数据库——数据库存储在 `dbConn` 中——相反，它是 `database/sql` 包对数据库的抽象。在我们的示例中，它指的是 MySQL 数据库，但由于我们可以使用 `database/sql` 与许多不同的数据源进行交互，它也可以很容易是本地文件或某些进程内数据存储（如 `memcache`）。

`sql.DB` 会代表你处理很多工作，包括数据库连接的打开、关闭和池化。

除非你的应用程序需要，否则不要反复打开和关闭数据库。`sql.DB` 对象被设计为长生命周期，你与数据库的所有交互都将通过 `sql.DB` 完成。但是，你必须确保在完成使用后通过 `sql.DB.Close` 关闭连接，以便它们可以返回池中。

> 提示：如果你需要给短生命期的函数访问 `sql.DB`，请将其作为参数传递给函数，而不是在函数内部创建新连接。

我们操之过急了。我们还没有对数据库做过任何操作。

让我们现在纠正这一点。

以下代码根据用户在浏览器地址栏 http://localhost:8999/ 后输入的任何内容，查询 "world" 数据库的 City 表。

```go
package main

import (
    "database/sql"
    "fmt"
    "log"
    "net/http"
    "github.com/go-sql-driver/mysql"
)

type City struct {
    Name string
    CountryCode string
    Population int
}

var database *sql.DB

func main() {
    db, err := sql.Open("mysql",
        "root:password@tcp(127.0.0.1:3306)/world")
    if err != nil {
        log.Println("Could not connect!")
    }
    database = db
    log.Println("Connected.")
    http.HandleFunc("/%s", showCity)
    http.ListenAndServe(":8999", nil)
}

func showCity(w http.ResponseWriter, r *http.Request) {
    city := &City{}
    queryParam := "%s" + r.URL.Path[1:] + "%s"
    rows, err := database.Query("SELECT Name, CountryCode, Population FROM city WHERE Name LIKE ?", queryParam)
    if err != nil {
        log.Fatal(err)
    }
    defer rows.Close()
```
```go
for rows.Next() {
    err := rows.Scan(&city.Name, &city.CountryCode,
        city.Population)
    if err != nil {
        log.Fatal(err)
    }
    fmt.Fprintf(w, "%s (%s): %d\n", city.Name,
        city.CountryCode, city.Population)
}
err = rows.Err()
if err != nil {
    log.Fatal(err)
}
```

除了 `{{.Name}}` 条目外，其他一切看起来都很熟悉。对于 Go 模板来说，这是一个变量。它包含在双大括号内，其名称 `Name` 前面有一个点。

点表示变量的作用域或上下文。在我们的案例中，`Name` 变量指的是 `Person` 结构体的 `Name` 字段，当你看到我们在程序逻辑中使用的定义时，这一点显而易见：

```go
type Person struct {
  Name string
}
```

我们可以传递一个 `Person` 结构体来填充模板变量，它将提取 `Name` 字段并将其替换模板中的变量定义。

注意，你在模板中引用的任何字段必须是导出的。也就是说，它们必须以大写字母开头。未导出的字段会导致问题，正如我们稍后看到的。

代码列表 11 显示了完整的程序代码。

## 代码列表 11：使用模板

```go
package main

import (
  "log"
  "net/http"
  "text/template"
)

type Person struct {
  Name string
}

func main() {
  http.HandleFunc("/", handler)
  err := http.ListenAndServe(":8999", nil)
  if err != nil {
    log.Fatal("ListenAndServe: ", err)
  }
}
```

这里唯一值得注意的代码是在 `handler` 函数中，当用户访问 http://localhost:8999 我们的 Web 应用程序根目录时会被调用。

`Handler` 创建了一个 `Person` 类型的变量 `p` 并将 "John Smith" 赋值给它的 `Name` 字段。然后我们使用 `template.ParseFiles`，传入模板文件名并将结果赋值给变量 `t`。

解析模板文件后，接接我们需要执行合并，我们通过调用 `Execute` 来实现，它将 `http.ResponseWriter` 和我们想要与模板合并的数据项作为参数传递。

当我们在浏览器中启动应用程序时，得到了图 15。

![](img/cdabbe899d95a91197e7ec37cc1c8048_39_0.png)

图 15：我们简单模板的输出

## 使用模板重构数据访问应用程序

让我们新学到的 Go 模板知识派上用场。首先，我们需要理解模板的许多功能之一——遍历结果集的能力，然后对其中的每个结果应用适当的格式化。

为了实现这一点，我们必须使用 `{{range}} ... {{end}}` 结构。我们将使用以下模板来构建我们的表格。`{{range}}` 和 `{{end}}` 之间的所有内容将为传入的对象的每个成员重复一次。

代码列表 12：“Cities”数据库应用程序的模板

```html
<html
<head>
<title>City Search</title>
</head>
<body>
```
