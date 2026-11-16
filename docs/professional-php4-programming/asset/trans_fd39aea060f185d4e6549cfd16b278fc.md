
此函数打开一个持久连接。此函数与 odbc_connect() 的主要区别在于，使用相同连接参数打开的连接会复用现有连接，而不是打开新连接。这有助于提升性能，因为无需承担重新打开连接的开销。与 odbc_connect() 的另一个行为差异是，脚本退出时连接不会自动关闭。另外，当 PHP 作为 CGI 模块安装时，odbc_pconnect() 不起作用，反而表现得像 odbc_connect()。

## 处理元数据

元数据，简单来说，就是关于数据的数据。在 PHP 数据库编程的上下文中，我们使用元数据来获取有关数据库状态、表和行的构造方式以及可能存在的任何错误条件的信息。这些信息非常有用：它不仅可以帮助你调试应用程序，还可以让你编写在实时操作数据库状态的应用程序。

### odbc_error() 和 odbc_errormsg()

```
string odbc_error([int connection_id])
string odbc_errormsg([int connection_id])
```

手册中将 odbc_error() 定义为返回 ODBC 错误代码，这是对错误条件的有时难以理解的引用。在实际使用中，odbc_error() 和 odbc_errormsg() 通常都返回相同的信息，包括 ODBC 错误状态和错误消息。connection_id 参数是可选的，如果省略，该函数将返回任何连接的最后错误状态。如果没有活动错误条件，将返回空字符串。

### odbc_field_name()

```
string odbc_field_name(int result_id, int field_number)
```

此函数接受列（字段）编号，并返回该位置的字段名（字段编号从 1 开始）：

```
$fieldname = odbc_field_name($result_id, $field_number);
```

### odbc_field_num()

```
int odbc_field_num(int result_id, string field_name)
```

这是 odbc_field_name() 的相反操作，接受列名并返回编号（字段编号从 1 开始）：

```
$fieldnum = odbc_field_num($result_id, 'myfield');
```

### odbc_field_type()

```
string odbc_field_type(int result_id, int field_number)
```

此函数接受列编号，并返回该列的数据类型（字段编号从 1 开始）：

```
$data_type = odbc_field_type($result_id, $field_number);
```

### odbc_field_len() 和 odbc_field_precision()

```
int odbc_field_len(int result_id, int field_number)
string odbc_field_precision(int result_id, int field_number)
```

这些函数是同义词；两者都接受列编号，并返回该列的长度或精度（字段编号从 1 开始）：

```
$length = odbc_field_len($result_id, $field_number);
```

精度是指为该列定义的数据类型的长度，例如 VARCHAR(255) 的精度为 255。

### odbc_tables()

```
int odbc_tables(int connection_id [, string qualifier [, string owner [, string name [, string types]]]])
```

此函数接受连接 ID，并返回一个结果标识符，其中包含与传递参数对应的表，包括目录（qualifier）、所有者和名称。

结果集包含以下列：

- 表限定符
- 表所有者
- 表名
- 表类型
- 备注

结果集按 TABLE_TYPE、TABLE_QUALIFIER、TABLE_OWNER 和 TABLE_NAME 排序。

owner 和 name 参数可以传入通配符：'%' 匹配多个字符，'_' 匹配单个字符。

### odbc_columns()

```
int odbc_columns(int connection_id [, string qualifier [, string owner [, string table_name [, string column_name]]]])
```

与 odbc_tables() 类似，此函数接受连接 ID，并返回一个结果标识符，其中包含与传递参数对应的列。

结果集包含以下列：

- 表限定符
- 表所有者
- 表名
- 列名
- 数据类型
- 类型名
- 精度
- 长度
- 小数位数
- 基数
- 可为空
- 备注

结果集按 TABLE_QUALIFIER、TABLE_OWNER 和 TABLE_NAME 排序。

owner、table_name 和 column_name 参数可以传入通配符：'%' 匹配多个字符，'_' 匹配单个字符。

### odbc_primarykeys()

```
int odbc_primarykeys(int connection_id, string qualifier,
string owner, string table)
```

与上述两个函数类似，odbc_primarykeys() 返回构成表主键的列名，或者在失败时返回 ODBC 结果标识符或 false。结果集包含以下列：

- 表限定符
- 表所有者
- 表名
- 列名
- 键序列
- 主键名

## 操作事务

事务是一系列 SQL 语句，你希望它们要么全部发生，要么都不发生，但绝不会部分发生。起初这可能听起来违反直觉，直到你考虑金融交易之类的事情。例如，以 ATM 取款为例。会有取款请求、发放许可，随后向你的账户扣款。虽然在发放许可后、更新账户之前，如果断电导致应用程序崩溃可能会让你高兴，但这不可能发生，因为该应用程序的业务规则使用事务来确保所有步骤或没有任何步骤发生。

其工作原理很简单；以下是伪代码示例：

```
Begin the transaction by turning off auto-commit.
Run a SQL statement and check for errors.
Repeat the above for all SQL statements that are relevant.
If any steps failed, abort the transaction (rollback).
If all successful commit the transaction (commit).
```

### odbc_autocommit()

```
int odbc_autocommit(int connection_id [, int OnOff])
```

此函数用于查询和设置特定连接 ID 的自动提交行为。在某些数据库中，提交 SQL 语句是必需的，并且也用于事务。通常，INSERT、UPDATE 或 DELETE 语句在提交前可能会被“回滚”。关闭此行为允许运行多个语句并测试其成功与否，或在事务中中止：

```
odbc_autocommit($connection_id, 0);
```

如果省略 OnOff 参数，则返回当前状态，例如 true 表示开启，false 表示关闭（或返回错误）。指定该参数可设置行为。默认情况下，自动提交处于开启状态。

### odbc_commit()

```
int odbc_commit(int connection_id)
```

此函数以连接 ID 作为参数，并提交该连接上的所有挂起事务。

### odbc_rollback()

```
int odbc_rollback(int connection_id)
```

此函数回滚指定连接 ID 上的所有挂起语句，从而使事务作废。

## 检索数据和游标

ODBC 有四种执行 SQL 语句的方式。即直接执行、预处理执行、存储过程和目录调用。我们在之前的“处理元数据”部分中见过操作存储过程和目录调用的 PHP 函数示例。接下来的两组函数将处理不同的可移植 SQL 执行方法。

### odbc_prepare() 和 odbc_execute()

```
int odbc_prepare(int connection_id, string query_string)
int odbc_execute(int result_id [, array parameters_array])
```

这两个函数配合使用，分两步执行 SQL 语句。

首先，SQL 解析器为执行准备 SQL 语句，这包括解析和编译阶段，然后使用 odbc_execute() 来完成执行。如果该语句需要执行多次，这尤其有用，可以带来巨大的性能优势。它还非常适合绑定参数，或者在相同的 SQL 语句包含变量且变量值会变化时多次执行的情况。

