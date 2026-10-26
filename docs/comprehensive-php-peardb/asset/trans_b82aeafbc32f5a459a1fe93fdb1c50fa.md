
|   |   | y |   |   |   |   |
|---|---|---|---|---|---|---|

所有更新查询均成功完成。

执行查询：`SELECT * from Employees\norder by last_name, first_name`

查询结果中的行数 = 7

|   | id | last_name | first_name | phone_ext | mgr_id | dept_id |
|---|---|---|---|---|---|---|
| 0 | 2 | Cox | Jeffrey | 225 | 0 | 1 |
| 1 | 3 | McNulty | Kate | 214 | 2 | 3 |
| 2 | 51 | Murphy | Jim |   | 1 | 1 |
| 3 | 1 | Schwendiman | Joe | 2204 | 2 | 3 |
| 4 | 4 | Schwendiman | Ryan | 128 | 1 | 1 |
| 5 | 58 | Schwendiman | Scott | 234 | 1 | 1 |
| 6 | 59 | Schwendiman | Taylor | 323 | 1 | 1 |

执行查询：`SELECT * from Employees\nwhere ( mgr_id = 3 )`

查询结果中的行数 = 0

执行查询：`SELECT * from Employees\nwhere ( dept_id = 2 )`

查询结果中的行数 = 0

所有删除查询均成功完成。

执行查询：`SELECT * from Employees\norder by last_name, first_name`

查询结果中的行数 = 2

|   | id | last_name | first_name | phone_ext | mgr_id | dept_id |
|---|---|---|---|---|---|---|
| 0 | 1 | Schwendiman | Joe | 2204 | 2 | 3 |
| 1 | 59 | Schwendiman | Taylor | 323 | 1 | 1 |

执行查询：SELECT * from Employees
where ( mgr_id = 3 )

查询结果中的行数 = 0

执行查询：SELECT * from Employees
where ( dept_id = 2 )

查询结果中的行数 = 0

上面显示的输出已略作重新格式化以提高可读性，但提供了所需的信息。

## MySQL

MySQL 很可能是 PHP 程序员使用最广泛的数据库。PHP 4 的所有版本均启用了对 MySQL 数据库的内置支持。对于 Windows 或类 Unix 平台，MySQL 支持通常默认开启。

本书大多数示例中都说明了 MySQL 的 DSN 格式。MySQL 数据库最常见的 DSN 格式可能为：

```
phptype://username:password@hostspec/database_name
```

*hostspec* 部分可以仅包含主机名或 IP 地址，或采用 *host:port* 格式的主机规范。

上面显示的通用测试脚本在我的 MySQL 安装（*MySQL 4.0.15-Max*）上运行没有任何问题。

### PostgreSQL

PHP 和 PEAR::DB 对 PostgreSQL 的支持非常出色。测试示例在 PostgreSQL 上仅作了微小修改后即可运行。“DROP TABLE” 命令需要针对小写表名进行修改。再次说明，我对该数据库缺乏经验可能是问题的一部分。无论如何，有经验的 PostgreSQL 用户会了解数据库的特殊情况并避免此类错误。

### Borland Interbase

Borland Interbase 在 PHP 中总体上得到支持，但我无法成功运行 PEAR 测试。

首先，**getTables()** 方法在 Interbase 的 PEAR::DB 实现中不受支持，因此代码必须重写。有一個示例脚本（随源代码提供，网址为 **http://www.intechra.net/**）名为 _code_listing_67.php_，它移除了与 **getTables()** 方法相关的行。

在使脚本通过初始的 **getTables()** 失败后，我在 select SQL 语句中遇到了一个一致的错误：

```
Running PEAR::DB test for database Borland
Interbase

Employees table successfully dropped.

Employees table successfully created.
```

7 所有数据插入成功。
9 执行查询：SELECT * from Employees order by
last_name, first_name
10

11 查询结果中的行数 = Object
13

14 执行查询：SELECT * from Employees where (
mgr_id = 3 )
15

16 PHP 遇到访问冲突 77F83AED

第 16 行的错误在每次测试运行中都会出现。出现错误后，有必要停止并重新启动 IIS。

在不妄下结论的情况下，我必须假设我的配置不适用于使用 PHP 与 Interbase。假设 PHP + Interbase 配置正常运行，我还必须假设上面的 PEAR::DB 测试将能正常工作，除了缺少 getTables() 的实现。

## Mini SQL

显然我不够聪明，无法让 Mini SQL 正常工作。我完全无法使用 Windows PHP 安装连接到基于 Linux 的远程 Mini SQL 服务器。我按照 http://www.php.net/msql 页面上的每一步操作，但均无济于事。当我改用 Linux 上的 PHP + Mini SQL 时，最终能够从 PHP 建立连接。然而，测试代码在不同的地方失败（每次运行似乎都在不同的位置失败）。

Mini SQL 主页上的许多链接已损坏（尤其是与 Windows 支持相关的链接），因此我只能对项目的总体状态做出一些假设。

我建议寻找小型数据库后端的 PHP 开发者可以试试 SQLite。我在设置它时没有任何问题，PEAR::DB 测试代码也没有任何问题。

## Microsoft SQL Server

在基于 Windows 的 PHP 安装中，Microsoft SQL Server 极其简单易于设置。为了测试，我只是安装了 PHP 网站上提供的最新 PHP 二进制文件。在以最基本级别配置 PHP 开始测试后，有必要通过编辑 *php.ini* 文件来加载 MS SQL 扩展。

只需在配置文件中删除行 *extension=php_mssql.dll* 前面的分号注释字符即可生效。

在非 Windows PHP 中配置以使用 MS SQL 数据库稍微复杂一些，但仍然可行。有关设置说明，请参阅 **http://www.php.net/mssql**。

运行后，PHP 与 MS SQL Server 配合良好，且 PEAR::DB 实现非常完整。测试脚本对 MS SQL Server 完美运行，经测试的版本为 MS SQL Server 2000（版本 8.00.760 SP3）。

## Oracle 7/8/8i

`php_fsql.dll` and configure PHP via the `php.ini` file to use FrontBase. 通用的 PEAR::DB 测试脚本第一次尝试时运行没有任何问题。

考虑到我之前没有任何 FrontBase 使用经验，这非常令人鼓舞。如果您考虑在 PHP 应用中使用 FrontBase，可以获得开发许可证，以便在部署前先测试应用，而无需承担财务承诺。

### SQLite

SQLite 是一个有趣的数据库引擎，根据最近的在线资料，从 PHP 5 版本开始将默认随 PHP 一起发布。SQLite 是一个基于文件的数据库引擎，正如其名称所示，非常轻量级。DSN 规范类似于：

```
sqlite:///c:/temp/PEAR/sqlite_employees.dat
```

上述 DSN 在 Windows 上有效，但只需适当更新路径格式即可简单地适配到其他操作系统上。

在基于 Windows 的 PHP 上安装 SQLite 轻而易举。只需从 **http://www.php.net/sqlite** 下载可用的 `php_sqlite.dll` 文件，然后从 SQLite 网站 **http://www.sqlite.org/** 下载实际的 SQLite 引擎 DLL（`sqlite.dll`）。

将 `sqlite.dll` 文件放置在 Windows 的搜索路径中（如 `system32` 目录），然后将 `php_sqlite.dll` 复制到 PHP 扩展目录。然后通过在 `php.ini` 文件中添加 `extension=php_sqlite.dll` 来启用 SQLite。

测试脚本运行没有任何错误或警告。
然而，生成了一条通知：

```
Notice: Undefined index: mode in C:\\temp\\PEAR\\php-4.3.4-Win32\\pear\\DB\\sqlite.php on line 185
```

此警告基于这样一个事实：出于某种原因，SQLite 数据库对象期望解析后的 DSN 具有名为 *mode* 的成员，而该成员不存在。也许这将在 PEAR::DB 的未来版本中添加。无论如何，如果您在典型配置的环境中运行，此通知将不会显示。然而，如果您在类 Unix 操作系统上运行 SQLite，*mode* 值指定文件模式（例如 0644），您可能希望指定它。如果您这样做，则需要编辑 DB_sqlite 实现或使用基于数组的 DSN 并直接提供 *mode* 键。

从 PHP 的角度来看，PEAR::DB 中对 SQLite 的支持对于这样一个新数据库来说出人意料地完整。在受限的托管环境中或不需要完整数据库后端的情况下，使用 SQLite 可能更受青睐。SQLite 的开销非常小，且 SQL 语言支持非常完整。

## dBase

PEAR::DB 中对 dBase 的支持极其有限。示例代码无法与 dbase 配合使用，因为接口的真正支持非常少。在 PHP 网站上稍微查看后，甚至 dBase 本身也未得到完全支持：

不支持索引或备注字段。也不支持锁定，两个并发
