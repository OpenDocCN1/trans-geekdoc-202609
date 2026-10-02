
SQLSTATE [VALUE] sqlstate_value
| mysql_error_code

DECLARE handler_type HANDLER FOR condition_value[..] sp_statement

handler_type:
CONTINUE
| EXIT
| UNDO

condition_value:
SQLSTATE [VALUE] sqlstate_value
| condition_name
| SQLWARNING
| NOT FOUND
| SQLEXCEPTION
| mysql_error_code

## 流程控制

MySQL 提供了多种用于管理程序流程的构造。大多数对软件开发者来说都很熟悉。

- `IF . THEN . ELSEIF THEN . ELSE . END IF`
- `CASE . WHEN . THEN . ELSE . END CASE`
- `LOOP . END LOOP`
- `REPEAT . UNTIL . END REPEAT`
- `WHILE . DO . END WHILE`
- `LEAVE`
- `ITERATE (similar to a loop continue)`

值得注意的是，最明显的遗漏是 FOR 循环。

## 使用存储过程权限和元数据

要实现存储过程，您需要为创建和管理过程以及用户执行过程提供额外的用户权限。对于您的 DBA 用户，CREATE ROUTINE 和 ALTER ROUTINE 权限对于管理对象是必要的。对于读写用户和只读用户，需要 EXECUTE 权限。

MySQL 在 mysql.proc 和 mysql.procs_priv 表中提供有关过程的信息。信息也可在 INFORMATION_SCHEMA.ROUTINES 表中获得。有多个 SHOW 命令可提供各种信息：

- `SHOW PROCEDURE STATUS`
- `SHOW FUNCTION STATUS`

- `SHOW CREATE PROCEDURE`
- `SHOW CREATE FUNCTION`

以下命令是扩展，仅在启用调试支持的 MySQL 服务器安装中可用。

- `SHOW PROCEDURE CODE`
- `SHOW FUNCTION CODE`

MySQL 的 INFORMATION_SCHEMA 不包括过程与所使用表之间的交叉引用。

## 扩展存储过程

尽管列出了一些限制，位于 http://mysql-sr-lib.sourceforge.net/ 的 MySQL 存储过程库可以为在其他存储数据库语言中可能找到的功能提供一些可行的解决方案，例如：

- Globals
- Arrays
- Named parameters
- "for each" loops
- Syntax helpers
- Testing

## 存储过程的缺点

存储过程未预编译以实现优化操作。存储过程在每个连接的基础上接收并重新解析。当由 PHP 等语言使用时，开销并不会带来您在使用其他 RDBMS 产品中的存储过程时可能获得的潜在速度提升。

存储过程不会由于模式更改而自动标记为无效。这要求存储过程的首次重新执行失败以确定无效语法。不幸的是，在不影响生产数据的情况下在生产环境中测试这一点可能很困难。

存储过程最缺少的功能是没有 SQL 标准 SIGNAL 语法。这类似于其他 RDBMS 产品中的 RAISE 语法，该语法为开发人员提供了使用存储过程管理数据库和应用程序逻辑异常的机会。

## 用户定义函数

MySQL 提供了在数据库中包含业务功能的第三种方式。这是一个用户定义函数（UDF），它是用 C 语言编写并编译的代码。这些函数使用非常受限的返回值的集合，但可以为现有外部代码提供接口。

memcached 函数是用户定义函数的良好示例。请查看 https://launchpad.net/memcached-udfs。

## 触发器

触发器，顾名思义，基于某个 DML 语句被触发或执行而执行操作。MySQL 触发器可以在六个不同的集成点定义：

- BEFORE INSERT
- AFTER INSERT
- BEFORE UPDATE
- AFTER UPDATE
- BEFORE DELETE
- AFTER DELETE

此功能与更传统的数据库关系一致。您会注意到 REPLACE 没有触发器。这将在后面更详细地讨论。MySQL 不提供对其他事件的触发器，例如系统启动或关闭，或 ALTER 命令。例如，MySQL 触发器有许多限制：

- 每个先前定义的六个点只能指定一个触发器。例如，其他数据库允许您指定多个触发器，例如同一表的两个 AFTER INSERT 触发器。
- 触发器只能按 FOR EACH ROW 实现；没有按语句级别的功能。
- 没有 instead of 触发器语法。
- 没有 when 子句限制。

以下示例展示了如何使用触发器为给定表的数据更改生成审计跟踪。列表 6-4 显示了以下示例的先决条件表。

### LISTING 6-4: trigger-tables.sql

```
USE chapter6;
DROP TABLE IF EXISTS trigger_test;
CREATE TABLE trigger_test (
  id INT UNSIGNED NOT NULL AUTO_INCREMENT,
  val VARCHAR(10) NOT NULL,
  PRIMARY KEY(id)
) ENGINE=InnoDB DEFAULT CHARSET latin1;

DROP TABLE IF EXISTS logger;
CREATE TABLE logger (
  action ENUM ('Insert','Update','Delete') NOT NULL,
  occurred TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
  id INT UNSIGNED NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET latin1;
```

### 无触发器

默认情况下，如果未定义触发器，则基于 INSERT 语句不会记录任何信息：

```
INSERT INTO trigger_test (id,val) VALUES (NULL, 'a');
SELECT * FROM logger;

Empty set (0.01 sec)
```

### 触发器语法

触发器的语法相当简单。它由四个部分组成：

```
1: CREATE TRIGGER <trigger_name>
2: BEFORE|AFTER INSERT|UPDATE|DELETE ON <table>
3: FOR EACH ROW
4: <sql statement(s)>
```

- CREATE TRIGGER <trigger_name>：定义触发器的名称。
- BEFORE|AFTER INSERT|UPDATE|DELETE ON <table>：定义触发器关联的表以及该触发器何时执行。
- FOR EACH ROW：是必需的语法，表示触发器针对执行的查询的每一行触发。没有用于触发器仅针对语句触发的伴随语法。
- <sql statement(s)>：指定要执行的语句。

### 插入触发器

列表 6-5 演示了 BEFORE|AFTER INSERT 语法。

### LISTING 6-5: insert-triggers.sql

```
DELIMITER $$
DROP TRIGGER IF EXISTS trigger_test_bri$$
CREATE TRIGGER trigger_test_bri
BEFORE INSERT ON trigger_test
FOR EACH ROW
    INSERT INTO logger(action,occurred,id) VALUES('Insert',NOW(),NEW.id);
$$
DROP TRIGGER IF EXISTS trigger_test_ari$$
CREATE TRIGGER trigger_test_ari
AFTER INSERT ON trigger_test
FOR EACH ROW
    INSERT INTO logger(action,occurred,id) VALUES('Insert',NOW(),NEW.id);
$$
DELIMITER;
```

TRIGGER 语法引入了 NEW 和 OLD 上下文。它们代表执行语句之前和之后的数据行的值。

例如，将新行插入示例表：

```
INSERT INTO trigger_test (id,val) VALUES (NULL, 'b');
SELECT * FROM trigger_test;
```

| id | val |
|----|-----|
| 1 | a |
| 2 | b |

```
SELECT * FROM logger;
```

| action | occurred | id |
|---|---|---|
| Insert | 2009-09-20 23:41:01 | 0 |
| Insert | 2009-09-20 23:41:01 | 2 |

您会看到 logger 表中有两行，以反映 before 和 after 插入触发器的触发。INSERT 语句发生之前 id 的 AUTO_INCREMENT 值尚未定义，而在 INSERT 语句之后该值被定义。

### 更新触发器

现在尝试添加 BEFORE|AFTER UPDATE 触发器并测试如列表 6-6 所示的 UPDATE 语法：

### LISTING 6-6: update-triggers.sql

```
DELIMITER $$
DROP TRIGGER IF EXISTS trigger_test_bru$$
CREATE TRIGGER trigger_test_bru
BEFORE UPDATE ON trigger_test
FOR EACH ROW
  INSERT INTO logger(action,occurred,id) VALUES('Update',NOW(),OLD.id);
$$
DROP TRIGGER IF EXISTS trigger_test_aru$$
CREATE TRIGGER trigger_test_aru
AFTER UPDATE ON trigger_test
FOR EACH ROW
  INSERT INTO logger(action,occurred,id) VALUES('Update',NOW(),NEW.id);
$$
DELIMITER;
```

对于此示例，您更新多个现有行以展示 FOR EACH ROW 语法的用法：

```
INSERT INTO trigger_test (id,val) VALUES (NULL, 'b');
UPDATE trigger_test SET id = id + 10 WHERE val = 'b';

SELECT * FROM trigger_test;
+----+------+
| id | val |
