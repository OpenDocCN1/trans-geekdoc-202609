
# 使用数据库

## 介绍

在本章节中，你将：

*   创建数据库及其结构。

*   向数据库写入数据。

*   从数据库读取数据。

## 选择 sqlite 驱动

要连接 sqlite 数据库，我们有几个库可供选择。这些库将为你提供必要的 sqlite 驱动，以便成功连接到你的数据库。以下是一些常见的库：

*   SQLite (使用 cgo)：[https://github.com/mattn/go-sqlite3](https://github.com/mattn/go-sqlite3) [*]
*   SQLite (使用 cgo)：[https://github.com/gwenn/gosqlite](https://github.com/gwenn/gosqlite) - 支持 SQLite 动态数据类型
*   SQLite (使用 cgo)：[https://github.com/mxk/go-sqlite](https://github.com/mxk/go-sqlite)
*   SQLite: (使用 cgo)：[https://github.com/rsc/sqlite](https://github.com/rsc/sqlite)
*   SQLite: (纯 go)：[https://modernc.org/sqlite](https://modernc.org/sqlite)

参考此链接查看其他数据库的库：

*   [https://github.com/golang/go/wiki/SQLDrivers](https://github.com/golang/go/wiki/SQLDrivers)

## 使用 sqlite3 从控制台

要使用控制台与你的数据库工作，使用 sqlite3 是有益的。请参阅官方 [下载页面](https://www.sqlite.org/download.html) 获取 sqlite，并确保选择适用于你操作系统的可执行文件。安装 sqlite 将提供一个可执行文件。

使用可执行文件，你可以：

*   创建数据库。

*   运行 SQL 命令。

*   运行其他由可执行文件支持的命令。

### 创建数据库

要创建数据库，你需要指定数据库名称，例如：

```
1 sqlite3 activities.db
```

前面的命令将在名为“activities.db”的文件中创建一个数据库。

> 同时，这也会启动一个 shell，你可以在其中执行 SQL 命令和 sqlite3 支持的其他命令。

### 运行 SQL 命令

在 shell 中运行 SQL 命令时，输入 SQL 并以分号 `;` 结尾。

```
1 CREATE TABLE `person` (
2         `uid` INTEGER PRIMARY KEY AUTOINCREMENT,
3         `name` VARCHAR(64) NULL,
4         `lastname` VARCHAR(64) NULL,
5         `created` DATE NULL
6     );
```

### 退出 shell

完成工作后，你可以通过输入 `.exit` 来退出 shell：

```
1 .exit
```

## 通过 Go 与数据库通信

要通过 Go 与数据库通信，需要按以下步骤操作：

1.  **创建项目**。你需要创建一个项目，以便导入包含你 sqlite 驱动的 Go 包。通过运行 `go mod init` 创建项目。以下是一个示例：

    ```
    1 go mod init "example-project"
    ```

2.  **添加导入**。一旦你拥有所需的包，需要在导入部分引用它们：

    ```
    1 import (
    2   "database/sql"
    3   _ "github.com/mattn/go-sqlite3"
    4  )
    ```

    上面，我们使用了两个包，“database/sql”提供运行查询和语句的接口，“github.com/mattn/go-sqlite3”包含驱动，使我们能够连接到数据库。

3.  **建立连接**。要连接到数据库，你需要调用 `sql` 实例上的 `Open()` 函数，如下所示：

    ```
    1 db, err := sql.Open("sqlite3", "./mydb.db")
    ```

    在前面的命令中，我们首先指定数据库类型，然后在第二个参数中指定数据库名称及其位置。我们会得到一个 `*sql.DB` 类型的数据库实例。

4.  **运行查询**。此时，我们可以自由运行查询。你使用 `Query()` 函数，并给出一个 SQL 语句，例如：

    ```
    1 rows, err := db.Query("SELECT * FROM person")   
    ```

    要遍历结果，你可以使用类似下面的 for 循环：

