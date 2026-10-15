

## 笔记

## MySQL – 存储过程：
通常，存储过程有助于提升应用程序的性能。存储过程一旦创建，就会被编译并存储在数据库中。不过，MySQL 实现存储过程的方式略有不同。MySQL 存储过程是按需编译的。编译完存储过程后，MySQL 会将其放入缓存中。

存储过程有助于减少应用程序与数据库服务器之间的通信流量，因为应用程序只需发送存储过程的名称和参数，而无需发送多条冗长的 SQL 语句。

存储过程是安全的。数据库管理员可以授予应用程序适当的权限，使其能够访问数据库中的存储过程，而无需对底层数据库表授予任何权限。

注意：不要创建过多存储过程，因为它们会占用大量内存。

### 示例

```sql
DELIMITER //
CREATE PROCEDURE myproc()
BEGIN
SELECT * FROM users where city='gurgaon';
END //
```

```
DELIMITER ;
```

```
//执行或调用过程 myproc
```

```
call myproc();
```

### 说明：
- 我们使用分隔符来指示存储过程的开始或结束。最后一条命令（DELIMITER;）将分隔符改回分号（;）。
- 我们使用 CREATE PROCEDURE 语句来创建新的存储过程。在 CREATE PROCEDURE 语句之后，我们指定存储过程的名称。并在存储过程名称后面加上括号。
- BEGIN 和 END 之间的部分称为存储过程的主体。我们在主体中编写声明式 SQL 语句以处理业务逻辑。

### 带参数的存储过程

```sql
DELIMITER //

CREATE PROCEDURE proc(IN city1 VARCHAR(50))

BEGIN

SELECT * FROM users WHERE city = city1;

END //

DELIMITER ;
```

### 执行存储过程 proc

call proc ('delhi');

### MySQL 存储过程中的循环

MySQL 提供了循环语句，允许你根据条件重复执行一段 SQL 代码块。MySQL 中有三种循环语句：WHILE、REPEAT 和 LOOP。

### WHILE 循环示例

```sql
DELIMITER $$
CREATE PROCEDURE myloop()
BEGIN
DECLARE x INT;
DECLARE str VARCHAR(255);
SET x = 1;
SET str = "";
WHILE x <= 10 DO
SET str = CONCAT(str,x,',');
SET x = x + 1;
END WHILE;
SELECT str;
END$$
```

```
DELIMITER ;
```

首先，我们重复构建 str 字符串，直到 x 变量的值大于 10。然后，我们使用 SELECT 语句显示最终的字符串。

现在让我们调用 myloop 存储过程——

```
CALL myloop();
```

**输出：** 1 2 3 4 5 6 7 8 9 10

## MYSQL – 触发器

SQL 触发器是存储在数据库中的一组 SQL 语句。每当与表关联的事件发生时（例如 insert、update 或 delete），它就会被触发。

触发器与存储过程的主要区别在于：当对表执行数据修改事件时，触发器会自动调用；而存储过程必须显式调用。

理解 SQL 触发器的优点和缺点很重要，这样你才能恰当地使用它。

### 使用 SQL 触发器的优点

SQL 触发器提供了一种检查数据完整性的替代方法。

SQL 触发器提供了一种运行定时任务的替代方法。

SQL 触发器对于审计表中数据的更改非常有用。

### 使用 SQL 触发器的缺点

SQL 触发器仅能提供扩展验证，无法取代所有验证。

SQL 触发器是在客户端应用程序不可见的情况下被调用和执行的；因此，很难弄清楚后台发生了什么。

### 触发器的两种类型

- 1. BEFORE 触发器 - BEFORE 触发器在 INSERT、DELETE 和 UPDATE 命令执行之前触发。
- 2. AFTER 触发器 - AFTER 触发器在 INSERT、DELETE 和 UPDATE 命令执行之后触发。

我们将创建一个名为 customer 的表，该表有两个列，用于在同一表中添加或删除新记录时准备日志。

- 只要添加/删除新值，表 logfile 将插入当前时间。

--DELIMITER $$ 用于避免每条行尾的 ; ，所有语句将被视为一组并持续连接，直到 DELIMITER $$ 结束

```sql
DELIMITER $$

CREATE TRIGGER trigger1 BEFORE INSERT ON users

FOR EACH ROW BEGIN

insert into logfile(lastupdate) values(now());

END$$

DELIMITER ;
```

Hirdesh Bhardwaj

## 删除触发器

```
DROP TRIGGER [IF EXISTS] [schema_name].trigger_name
```

该语句用于删除触发器。schema（数据库）名称是可选的。如果省略 schema，触发器将从默认 schema 中删除。DROP TRIGGER 在 MySQL 5.0.2 中新增。使用此语句需要拥有与触发器关联的表的 TRIGGER 权限。

## 笔记

## MySQL 事务：

事务是一组按顺序执行的数据库操作或查询，它们作为一个单一的工作单元来执行。换句话说，只有组内的每个单独操作都成功，事务才算完成。如果事务中的任何操作失败，则整个事务都将失败。

简而言之，你可以将多个 SQL 查询组合到一个组中，并将它们作为一个事务的一部分一起执行。

### 为什么数据库中需要事务：

以 ATM 机为例。我们都使用 ATM 取款和转账。如果你将取款操作分解为各个步骤，你会发现：

- 1) 验证账户详情。
- 2) 接受取款请求
- 3) 检查余额
- 4) 更新余额
- 4) 出钞

假设你的账户余额为 1000 美元，你发起一笔 900 美元的取款请求。在第四步，你的余额已更新为 900 美元，此时 ATM 机因断电而停止工作

Hirdesh Bhardwaj

```
start transaction
select balance from Account where Account_Number='9001';
select balance from Account where Account_Number='9002';
update Account set balance=balance-900 where Account_Number='9001';
update Account set balance=balance+900 where Account_Number='9002';
commit;  // 如果所有 sql 查询成功
rollback; // 如果任何 Sql 查询失败或出错
```

### 另一个示例：

```php
// 需要 php 5+ 版本，因为这是 PHP 的最新概念
// 创建表时将数据库切换为 innoDB，因为它支持 ACID
$mysqli = new mysqli("localhost", "my_user", "", "hirdesh");

/* 检查连接 */
if (mysqli_connect_errno())
{
    printf("连接失败");
    exit();
}

/* 关闭自动提交 */
$mysqli->autocommit(FALSE);
```

```
/* 插入一些值 */
$mysqli->query("INSERT INTO users VALUES ('hirdesh',
'gurgaon', 'M', 11.2)");
$mysqli->query("INSERT INTO users VALUES ('ashok',
'gurgaon', 'M', 5.2)");

/* 提交事务 */
if (!$mysqli->commit())
{
    print("事务提交失败\n");
    exit();
}
/* 删除表 */
$mysqli->query("DROP TABLE users");

/* 关闭连接 */
$mysqli->close();
?>
```

### 示例 2：

```php
// 按步骤执行的另一个示例
try {
    // 首先，让我们开始一个事务
    $db->beginTransaction();
    // 一组查询；如果其中一个失败，应该抛出异常
```

Hirdesh Bhardwaj

```php
$db->query('第一个查询');
$db->query('第二个查询');
$db->query('第三个查询');

// 如果我们到达这里，意味着没有抛出异常
// 即没有查询失败，我们可以提交事务
$db->commit();
}
catch (Exception $e)
{
    // 已抛出异常
    // 我们必须回滚事务
    $db->rollback();
}
?>
```

## 笔记

3. Web 浏览器接收到 XML 消息后，会解析该消息，以更新页面该部分的内容。

XMLHttpRequest 对象是一种名为 Ajax（异步 JavaScript 和 XML）的技术的一部分。使用 Ajax，可以通过 XMLHttpRequest API 在浏览器和服务器之间传递数据，而无需重新加载网页。

## XMLHttpRequest 对象：

为了通过 Ajax 向服务器发出请求，必须创建一个可用于不同功能形式的对象。Microsoft Internet Explorer 将该对象创建为 ActiveX 控件，而 Firefox 和 Safari 等浏览器则使用基本的 JavaScript 对象。

## 常用的 XMLHttpRequest 方法：

abort()：abort 方法用于中途停止请求。如果你只想让请求持续特定时间，可以调用 abort 方法来提前停止请求。

getAllResponseHeaders()：你可以使用此方法获取所有正在传递的 HTTP 头的完整信息。例如 - 服务器名称、日期、连接和内容类型。

open ("method","URL","async","username","pswd")：这是你用于打开与服务器上特定文件连接的方法。

