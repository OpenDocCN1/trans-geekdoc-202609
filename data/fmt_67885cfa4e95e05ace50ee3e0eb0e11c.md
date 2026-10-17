
```php
#
# get()
#
# this function simply gets an array containing the result
# set of the query that utilizes the db_bytes() UDF
#
# ARGUMENTS
# optional schema_name, used in the where clause of the query
#
# RETURNS
# array containing the result set of the query
#
public function get($schema_name = null)
{
    # the main query
    $query= <<<EOQUERY
SELECT table_schema,
    count(*) AS num_tables,
    db_bytes(table_schema) AS bytes
FROM information_schema.tables
EOQUERY;

    # if schema_name set, append WHERE clause to query
    if (isset($schema_name)) {
        $query .= ' WHERE table_schema = ?';
    }
    # append GROUP BY and ORDER BY
    $query .= ' GROUP BY table_schema ORDER BY table_schema';

    # initialize the statement
    $stmt= $this->mysqli->stmt_init();

    # prepare the query
    if ($stmt->prepare($query)) {
        # bind the single placeholder if $schema_name set
        if (isset($schema_name)) {
            $stmt->bind_param("s", $schema_name);
        }
    }

    # execute the statement
    $stmt->execute();

    # obtain the fields to bind to
    $this->get_fields($stmt);

    # set an array to bind to for the result set
    call_user_func_array(array($stmt, 'bind_result'), $this->_fields);

    # fetch all the rows
    $this->fetchall_hash_result($stmt);

    # close the statement
    $stmt->close();

    return $this->_hash_result;
}
```

`get_fields()` 私有方法获取在私有类成员 `_fields` 中准备的查询的字段名称。其主要目的是为获取结果集创建用于绑定输出参数的关联数组。

```
#
# get_fields()
# a method to obtain field names, storing in class member
# _fields
#
# ARGS
# $stmt--prepared statement
#
private function get_fields(&$stmt) {
    $metadata= $stmt->result_metadata();
    while ($field = $metadata->fetch_field()) {
        $this->_fields[] = &$this->_row[$field->name];
    }
    $metadata->close();
}
```

`fetchall_hash_result()` 方法用于构建包含查询结果的关联数组，存储在类成员 `_hash_result` 中。这是当使用 `Schemas` 类调用 `get()` 时必然返回给程序的数组。

```
#
# fetchall_hash_result()
# a method to obtain the result of the executed prepared statement
# storing the result as a hash/associative array the class member
# _hash_result
#
# ARGS
# $stmt--prepared statement
#
private function fetchall_hash_result(&$stmt) {
    call_user_func_array(array($stmt, 'bind_result'), $this->_fields);

    while ($stmt->fetch()) {
        foreach($this->_row as $field => $val) {
            $tmp_ar[$field]= $val;
        }
        $this->_hash_result[] = $tmp_ar;
    }
}
```

最后，客户端程序实例化并使用此类，它只是实例化一个 `Schemas` 对象并调用 `$schemas->get()` 来获取包含模式列表结果集的关联数组：

```
require("Schemas.php");

$schemas= new Schemas();

$result= $schemas->get();
print_r($result);
```

有了它，你现在就有了满足打印出所有模式、每个模式的表数量和字节大小的任务需求的手段。

## 其他 UDF SQL 语句

你已经看到如何通过使用 SQL 语句为 UDF 生成参数来聚合对 UDF `get_bytes()` 的调用。还有其他可与 UDF 一起使用的有用 SQL 语句。

你可以指定一个 UDF 调用作为在 `INSERT` 语句中插入值的手段：

```
mysql> INSERT INTO schema_sizes (schema_name, size)
  -> VALUES ('test', db_bytes('test'));
Query OK, 1 row affected (0.01 sec)

mysql> select * from schema_sizes;
```

| id | 模式名称 | 大小 |

|----|-------------|------|

| 1 | test | 583855 |

另一个查询执行有用的更新并将用户定义变量设置为正在更新的值：

```
mysql> UPDATE schema_sizes SET size= @size:= db_bytes('test')
  -> WHERE schema_name='test';
Query OK, 0 rows affected (0.00 sec)
Rows matched: 1  Changed: 0  Warnings: 0

mysql> select @size;
```

| @size |

|-------|

| 583855 |

在此示例中，`UPDATE` 语句同时更新 `schema_sizes` 表的 `size` 列，并将用户定义变量 `@size` 设置为 `size` 列被更新到的值。这是一种同时更新和读取值的方法，可能非常有用。

你可以在几乎任何 SQL 语句中使用 UDF，所以你能做什么的唯一限制就是你的想象力！

## 调试 UDF

当你开发 UDF 时，你很可能会在代码中遇到错误。这是必然的。UDF API 使用起来相当容易，但你会遇到一些需要使用调试器来帮助理清问题的情况。本节简要介绍如何调试你的 UDF，以及如何通常与 MySQL 一起使用调试器。在此演示中，使用了 `gdb`，即 GNU 调试器。

比如说，你正在运行你的 UDF，并看到以下结果：

```
mysql> select db_bytes(name) from sch;
ERROR 2013 (HY000): Lost connection to MySQL server during query
```

这是因为作者在 `db_bytes_init()` 中添加了以下内容，以说明本章前面提到的一个观点：

```
/* test block for debugging */
if (strcmp("test", args->args[0])) {
  fprintf(stderr, "matches: %s\n", args->args[0]);
}
```

其要点是，如果你在 `SELECT` 语句中使用 UDF 并为 UDF 提供列名作为参数，则 `args->args[0]` 的值将为 `NULL`。如果你尝试使用 `args->args[0]`，你将得到一个段错误。这提供了一个使用调试器 `gdb` 的充分理由。

### 将 gdb 附加到已运行的进程

你可以从调试器运行 MySQL，也可以附加到已运行的进程。在此演示中，你将 `gdb` 附加到正在运行的进程。要附加到正在运行的 MySQL 进程，你需要找出其进程 ID：

```
ps auxww|grep mysqld|grep -v mysqld_safe|grep -v grep
mysql  17629 0.4  4.1 1412436 164476 pts/4  Sl  22:48   0:03
/usr/sbin/mysqld
--basedir=/usr
--datadir=/var/lib/mysql
--user=mysql
--pid-file=/var/run/mysqld/mysqld.pid
--skip-external-locking
--port=3306
--socket=/var/run/mysqld/mysqld.sock
```

如你所见，进程 ID（PID）为 `17629`。请按以下步骤操作：

- 1. 因为 `mysqld` 以 `mysql` 用户运行，所以你需要以 `root` 身份运行 `gdb`：

    `sudo gdb /usr/sbin/mysqld 17629`

- 2. 你将看到大量输出显示各种 MySQL 线程，然后到达提示符：

    `Reading symbols from /usr/lib/db_bytes.so.done.`

    `Loaded symbols for /usr/lib/db_bytes.so`

    `0x00007F267de42db2 in select () from /lib/libc.so.6`

    `(gdb)`

- 3. 通过输入命令 `continue` 告诉调试器“继续”程序执行：

    `(gdb) continue`

    `Continuing.`

- 4. 在另一个连接到 MySQL 的终端中，运行有问题的语句：

```
mysql> select db_bytes(name) from sch;
ERROR 2006 (HY000): MySQL server has gone away
```

- 5. 回到 `gdb` 的终端窗口：

```
Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0x41891950 (LWP 17662)]
0x00007f2633820bbe in db_bytes_init (initid=0x53e4500, args=0x53e44c8,
    message=<value optimized out>) at db_bytes.c:91
91     if (strcmp("test", args->args[0])) {
(gdb)
```

- 6. 显示了一个段错误！你已经知道这段代码会造成问题，但 `gdb` 验证了这一点。你也可以运行回溯：

```
(gdb) backtrace
#0  0x00007f2633820bbe in db_bytes_init (initid=0x53e4500, args=0x53e44c8,
    message=<value optimized out>) at db_bytes.c:91
#1  0x0000000000566fba in udf_handler::fix_fields ()
#2  0x00000000005704fd in Item_udf_func::fix_fields ()
#3  0x0000000000609407 in setup_fields ()
#4  0x0000000000624a32 in JOIN::prepare ()
#5  0x0000000000632216 in mysql_select ()
#6  0x0000000000632603 in handle_select ()
#7  0x0000000000052dd7 in mysql_execute_command ()
#8  0x000000000005e5beb in mysql_parse ()
#9  0x000000000005e695 in dispatch_command ()
#10 0x000000000005e7d6 in do_command ()
#11 0x000000000005e7d7e in handle_one_connection ()
#12 0x00007f267ecc53f7 in start_thread () from /lib/libpthread.so.0
#13 0x00007f267de49b3d in clone () from /lib/libc.so.6
```

- 7. 你可以清楚地看到问题所在——在第零帧，`db_bytes_init`。如果使用命令 `frame 0` 切换到第零帧，你将看到导致段错误的代码行，并且可以通过打印 `args->args` 来验证导致段错误的原因。程序因尝试对 `NULL` 值执行 `strcmp()` 而段错误：

```
(gdb) frame 0
#0  0x00007f1e29eb4bbe in db_bytes_init (initid=0x53e62c0, args=0x53e6288,
    message=<value optimized out>) at db_bytes.c:91
91     if (strcmp("test", args->args[0])) {
(gdb) print *args->args
$2 = 0x0
```

### 设置断点并逐步执行代码

现在你知道了哪个函数有问题，你也可以为 `db_bytes_init()` 设置断点，并从该断点逐步执行直到有问题的代码行。操作方法如下：

- 1. 当然你需要重启 MySQL，如果你使用的是 `mysqld_safe`，则会自动完成；不过你需要查看进程列表以找出新的进程 ID。现在设置断点：

```
(gdb) break db_bytes_init
Breakpoint 1 at 0x7f424da2db40: file db_bytes.c, line 66.
```

`(gdb) continue`

`Continuing.`

- 2. 在另一个终端中，重新运行导致错误的 SQL 语句：

```
mysql> select db_bytes(name) from sch;
ERROR 2006 (HY000): MySQL server has gone away
No connection. Trying to reconnect.
Connection id: 125
Current database: test
```

- 3. 该命令会在此处挂起，因为调试器已在您之前设置的断点 `db_bytes_init()` 处停止了执行。回到调试器终端窗口，您将看到：

```
[Switching to Thread 0x41cf6950 (LWP 18597)]

Breakpoint 1, db_bytes_init (initid=0x53f7610, args=0x53f75d8, message=0x53eb6ad "")
    at db_bytes.c:66
{
```

- 4. 您需要通过输入 `gdb` 命令 `step`（或仅字母 `s`）逐步执行 `db_bytes_init()`：

```
(gdb) step
if (args->arg_count != 1 || args->arg_type[0] !=
STRING_RESULT)
(gdb) step
66  {
(gdb) s
if (args->arg_count != 1 || args->arg_type[0] !=
STRING_RESULT)
(gdb) s
total_bytes = malloc(sizeof(char) * 12);
```

- 5. 接下来您逐步执行到包含错误代码块的行。您可以打印 `args->args` 来查看其值，在本例中为 `NULL`（`0x0`）：

```
(gdb) s
91      if (strcmp("test", args->args[0])) {
(gdb) print *args->args
$1 = 0x0
```

- 6. 下一步将导致段错误：

```
(gdb) s

Program received signal SIGSEGV, Segmentation fault.
0x00007f424da2dbbe in db_bytes_init (initid=0x53f7610, args=0x53f75d8, message=<value optimized out>) at db_bytes.c:91
91      if (strcmp("test", args->args[0])) {
```

## 处理字面值

因此，您现在知道 `bug` 在哪里。如果您对 `db_bytes()` 使用字面值作为参数会怎样？请按照以下步骤操作：
