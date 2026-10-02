

```
VIEW system_users AS SELECT host,user,password FROM mysql.user;
```

```
$ mysql -uexpert_admin -pwroxadmin chapter6
mysql> SELECT * FROM system_users;

ERROR 1356 (HY000): View 'chapter6.system_users' references invalid table(s)
or column(s) or function(s) or definer/invoker of view lack rights to use them
```

你还需要更高的权限来查看视图定义的语法：

```
$ mysql -uexpert_admin -pwroxadmin chapter6

mysql> SHOW CREATE VIEW system_users;

ERROR 1142 (42000): SHOW VIEW command denied to user 'expert_admin'@'localhost'
for table 'system_users'
$ mysql -uroot -p chapter6

SHOW CREATE VIEW system_users\G
*************************** 1. row ***************************
View: system_users
Create View: CREATE ALGORITHM=UNDEFINED DEFINER=`root`@`localhost` SQL SECURITY DEFINER VIEW `chapter2`.`system_users` AS select `mysql`.`user`.`Host` AS `host`,`mysql`.`user`.`User` AS `user`,`mysql`.`user`.`Password` AS `password` from `mysql`.`user`
character_set_client: latin1
collation_connection: latin1_swedish_ci
```

## 关于视图的附加信息

以下附加要点对于有经验的开发者理解视图功能的局限性相关：

- **视图名称必须与表命名空间唯一。** 对于给定的模式，不可能存在与表同名的视图。
- **在某些情况下可以在 MySQL 中更新视图。** 主要要求是表中的给定行与对应的行之间存在一对一的关系。
- **视图通常用于数据仓库解决方案。** MySQL 通常在视图之上使用其他视图时性能不佳。可能有必要重写包含其他视图的视图以获得更优化的性能。
- **使用视图存在一些注意事项。** 最重要的点是你不能在视图中使用临时表，并且 FROM 子句中的表不能是派生表。
- **MySQL 没有物化视图的概念。** 你可以通过使用 MySQL 复制并在定义的时间停止进程来创建物化视图的假象；然而，这仅对整个 MySQL 实例可行，而非单个视图。

## 存储过程和函数

MySQL 提供存储过程和存储函数以在数据库级别封装业务功能。MySQL 将过程和函数称为 *例程*。使用存储例程的一些明显优势包括：

- 它们历史上一直被用来 *确保* 重要的业务决策在数据库级别，并且任何访问数据的应用程序都通过存储过程进行访问。当客户端应用程序支持多种编程语言时，这可能很重要。
- 它们能够在多个命令可以同时发生时减少网络往返。一个例子可能是当给定记录的数据存储在两个表的一对一关系中时。
- 可以为数据提供不同的安全访问级别，仅通过存储过程访问数据。

### 通用属性

除返回 MySQL 数据类型的存储函数外，以下属性适用于存储过程和存储函数：

- 例程可以接受固定数量的参数。
- 例程有一系列定义其使用方式和性质的特征。
- 例程有一个可执行的 MySQL 代码块。

### 参数

参数包括参数类型（*IN*、*OUT*、*INOUT*）、名称和数据类型。当未指定参数类型时，*IN* 类型为默认值。名称和数据类型是必需的。存储例程可以不带参数定义。列表 6-1 显示了一些参数示例。

```
LISTING 6-1: sp-param.sql
```sql
DELIMITER //
DROP PROCEDURE IF EXISTS sample_no_param//
CREATE PROCEDURE sample_no_param()
BEGIN
    SELECT 1 + 1;
END//

DROP PROCEDURE IF EXISTS sample_2_param//
CREATE PROCEDURE sample_2_param(param1 INT, param2 INT)
BEGIN
    SELECT param1 + param2;
END//

CREATE PROCEDURE sample_out(OUT o_param INT)
```

```
BEGIN
    SELECT 1 + 1 INTO o_param;
END//

CREATE FUNCTION sample_func(param1 INT)
RETURNS INT
BEGIN
    RETURN 1 + param1;
END//

DELIMITER;
```

以下输出显示了这些例程在各种参数声明下的执行和资源。

```
mysql> CALL sample_no_param();
```
| 1 + 1 |
|-------|
| 2 |

```
mysql> CALL sample_2_param(2,3);
```
| param1 + param2 |
|-----------------|
| 5 |

```
mysql> CALL sample_out(@param_out);
mysql> SELECT @param_out;
```
| @param_out |
|------------|
| 2 |

```
mysql> SELECT sample_func(2);
```
| sample_func(2) |
|----------------|
| 3 |

> MySQL 存储例程不支持参数的数据类型为集合或数组。存储例程也不能接受可变数量的参数，并且也不支持参数重载。

### 特征

在参数规范之后，你可以指定例程使用的数据的特征。这些特征目前仅为信息，并未强制执行：

- **LANGUAGE SQL：** 定义可使用的语言。唯一有效的值是 SQL。
- **[NOT] DETERMINISTIC：** 定义例程，通常是函数，对于给定的参数每次是否返回相同的值。默认情况下例程定义为 NOT DETERMINISTIC。
- **NO SQL：** 表示例程不包含任何 SQL 语句。
- **CONTAINS SQL：** SQL 选项的默认特征。
- **READS SQL DATA：** 表示例程仅读取数据且不修改任何数据。
- **MODIFIES SQL DATA：** 表示例程读取并修改数据。

### 存储例程逻辑

存储例程可能包含单个 SQL 语句，或在 BEGIN...END 语句块中包含多个 SQL 语句。

语句块中的关键区域有：

- 变量
- 游标
- 处理器和条件
- 流程控制
- 返回（仅存储函数）

### 变量

对于存储例程中的局部变量，你需要在 DECLARE 语句中先定义这些变量。变量可以分配默认值，可以使用 SET 命令分配值，或在 SELECT 语句中使用 INTO 语法分配：

# LISTING 6-2: sp-variables.sql

```
```sql
DELIMITER //
DROP FUNCTION IF EXISTS variable_example//
CREATE FUNCTION variable_example (seed INT)
RETURNS INT
BEGIN
    DECLARE example_int INT;
    DECLARE example_result INT;

    SET example_int:= 1;
```

```
SELECT example_int + seed INTO example_result;

RETURN example_result;
END//

DELIMITER;

SELECT variable_example(5);
```
| variable_example(5) |
|---------------------|
| 6 |

### 游标

MySQL 游标是一个只读、仅向前循环的 SELECT 查询。游标必须由在变量声明之后指定的 DECLARE 子句指定。数据通过 OPEN、FETCH 和 CLOSE 命令在游标中检索。列表 6-3 是游标的基本结构。

# LISTING 6-3: sp-cursor.sql

```
DELIMITER //
DROP FUNCTION IF EXISTS cursor_example//
CREATE PROCEDURE cursor_example ()
BEGIN
  DECLARE l_user VARCHAR(50);
  DECLARE done BOOLEAN DEFAULT FALSE;
  DECLARE cur1 CURSOR FOR SELECT user FROM mysql.user;
  DECLARE CONTINUE HANDLER FOR NOT FOUND
    SET done = TRUE;

  OPEN cur1;

  lab:
  LOOP
    FETCH cur1 INTO l_user;
    IF (done) THEN
      LEAVE lab;
    END IF;
  END LOOP;
END//

DELIMITER;
```

### 处理器和条件

如前面的游标代码所示，你可以为基于给定 MySQL 错误代码的逻辑控制声明一个 HANDLER。MySQL 参考手册定义了 HANDLER 和 CONDITION 子句的语法为：

```
DECLARE condition_name CONDITION FOR condition_value

condition_value:
```
