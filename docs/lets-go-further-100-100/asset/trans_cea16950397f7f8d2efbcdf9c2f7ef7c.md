
第5章

## 数据库设置与配置

在本书的下一部分，我们将继续推进项目构建，并设置一个 SQL 数据库来持久化存储我们的电影数据。

与第一本 *Let's Go* 书（我们在其中使用 MySQL 作为数据库）不同，这次我们将使用 PostgreSQL。它是开源的、非常可靠，并拥有一些有用的现代特性——包括对数组和 JSON 数据类型、全文搜索以及地理空间查询的支持。在构建过程中，我们将使用其中一些现代 PostgreSQL 特性。

在本节中，你将学习：

- 如何在本地机器上安装和设置 PostgreSQL。
- 如何使用 `psql` 交互工具创建数据库、PostgreSQL 扩展和用户账户。
- 如何在 Go 中初始化数据库连接池并配置其设置以提高性能和稳定性。

安装期间，你的计算机上应该也已经创建了一个名为 `postgres` 的*操作系统*用户。在基于 Unix 的系统上，你可以通过检查 `/etc/passwd` 文件来确认这一点，如下所示：

```
$ cat /etc/passwd | grep 'postgres'
postgres:x:127:134:PostgreSQL administrator,,,:/var/lib/postgresql:/bin/bash
```

这很重要，因为默认情况下，PostgreSQL 对来自本地机器的任何连接使用一种称为*对等认证*的认证方案。对等认证意味着，如果当前操作系统用户的用户名与有效的 PostgreSQL 用户用户名匹配，他们就可以作为该用户登录 PostgreSQL，而无需进一步认证。整个过程不涉及密码。

因此，如果我们切换到名为 `postgres` 的*操作系统*用户，我们就应该能够使用 `psql` 连接 PostgreSQL，而无需任何进一步认证。事实上，你可以通过以下命令一步完成这两件事：

```
$ sudo -u postgres psql
psql (13.1 (Ubuntu 13.1-1.pgdg20.04+1))
Type "help" for help.

postgres=#
```

**提示：** 在 PostgreSQL 中，`\` 字符表示一个*元命令*。其他一些有用的元命令包括 `\l` 用于列出所有数据库，`\dt` 用于列出表，`\du` 用于列出用户。你还可以运行 `\?` 查看所有可用元命令的完整列表。

现在我们已经创建了 `greenlight` 数据库并连接到了它，还有几项任务需要完成。

第一个任务是创建一个新的 `greenlight` 用户，该用户没有超级用户权限，我们可以使用它来执行 SQL 迁移并从 Go 应用程序连接到数据库。我们希望将这个新用户设置为使用*基于密码*的认证，而不是对等认证。

PostgreSQL 还有*扩展*的概念，这些扩展在标准功能之上增加了额外的特性。随 PostgreSQL 一起提供的扩展列表可以在此处找到，还有一些其他扩展你可以单独下载。

在这个项目中，我们将使用 `citext` 扩展。它为 PostgreSQL 添加了一种不区分大小写的字符串类型，我们将在本书后面使用它来存储用户电子邮件地址。需要注意，扩展只能由*超级用户*添加到*特定数据库*中。

请继续运行以下命令，创建一个带特定密码的新 `greenlight` 用户，并将 `citext` 扩展添加到我们的数据库中：

```
greenlight=# CREATE ROLE greenlight WITH LOGIN PASSWORD 'pa55word';
CREATE ROLE
greenlight=# CREATE EXTENSION IF NOT EXISTS citext;
CREATE EXTENSION
```

> **重要：** 如果你在跟着操作，请务必记住你为 `greenlight` 用户设置的密码。你在接下来的步骤中会用到它。

成功完成后，你可以输入 `exit` 或 `\q` 关闭基于终端的界面，并恢复为正常的操作系统用户。

```
greenlight=# exit
```

### 以新用户身份连接

在继续之前，让我们先证明一切设置正确，尝试以 `greenlight` 用户身份连接到 `greenlight` 数据库。当系统提示时，输入你在上述步骤中设置的密码。

```
$ psql --host=localhost --dbname=greenlight --username=greenlight
Password for user greenlight:
psql (13.1 (Ubuntu 13.1-1.pgdg20.04+1))
SSL connection (protocol: TLSv1.3, cipher: TLS_AES_256_GCM_SHA384, bits: 256,
compression: off)
Type "help" for help.

greenlight=> SELECT current_user;
 current_user
-------------
 greenlight
(1 row)

greenlight=> exit
```

太好了！这确认了我们的数据库和带有密码凭据的新 greenlight 用户工作正常，我们能够以该用户身份毫无问题地执行 SQL 语句。

## 补充信息

### 优化 PostgreSQL 设置

PostgreSQL 自带的默认设置相当保守，你通常可以通过调整 `postgresql.conf` 文件中的值来提高数据库的性能。

你可以通过以下 SQL 查询检查你的 `postgresql.conf` 文件所在位置：

```
$ sudo -u postgres psql -c 'SHOW config_file;'
        config_file
------------------------------------
/etc/postgresql/13/main/postgresql.conf
(1 row)
```

这篇文章很好地介绍了 PostgreSQL 的一些最重要设置，并指导了哪些值可以作为合理的起始点。如果你对优化 PostgreSQL 感兴趣，我建议你读一读这篇文章。

或者，你可以使用这个基于 Web 的工具，根据你可用的系统硬件生成建议值。这个工具的一个好功能是，它还会输出 `ALTER SYSTEM` SQL 语句，你可以对数据库运行这些语句来更改设置，而无需手动修改 `postgresql.conf` 文件。

## 连接到 PostgreSQL

好的，现在我们的新 `greenlight` 数据库已经设置好了，让我们看看如何从 Go 应用程序连接到它。

你可能还记得 *Let's Go* 中的内容，要使用 SQL 数据库，我们需要使用一个*数据库驱动*作为 Go 与数据库本身之间的“中间人”。你可以在 Go wiki 中找到 PostgreSQL 可用驱动列表，但在我们的项目中，我们将选择流行、可靠且成熟的 `pq` 包。

如果你在跟着本书编码，那么请使用 `go get` 下载 `pq` 的 `v1.10.0` 版本，如下所示：

```
$ go get github.com/lib/pq@v1.10.0
go: downloading github.com/lib/pq v1.10.0
go get: added github.com/lib/pq v1.10.0
```

要连接数据库，我们还需要一个*数据源名称*（DSN），它基本上是一个包含必要连接参数字符串。DSN 的确切格式取决于你使用的数据库驱动（应该在驱动文档中描述），但使用 `pq` 时，你应该能够使用以下 DSN 以 `greenlight` 用户身份连接到本地 `greenlight` 数据库：

```
postgres://greenlight:pa55word@localhost/greenlight
```

### 建立连接池

我们将用于从 Go 应用程序连接到 `greenlight` 数据库的代码与第一本 *Let's Go* 书中的几乎完全相同。因此我们不会赘述细节，希望这一切都会让人感到非常熟悉。

在高层次上：

- 我们希望 DSN 在运行时是可配置的，因此我们会通过命令行标志将其传递给应用程序，而不是硬编码。为了在开发期间简化，我们将使用上面的 DSN 作为该标志的默认值。
- 在我们的 `cmd/api/main.go` 文件中，我们将创建一个新的 `openDB()` 辅助函数。在这个辅助函数中，我们将使用 `sql.Open()` 函数建立一个新的 `sql.DB` 连接池，然后——因为到数据库的连接是按需惰性建立的，仅在首次需要时建立——我们还需要使用 `db.PingContext()` 方法来真正创建一个连接并验证一切设置正确。

让我们回到 `cmd/api/main.go` 文件并按如下方式更新它：

```
File: cmd/api/main.go
```

