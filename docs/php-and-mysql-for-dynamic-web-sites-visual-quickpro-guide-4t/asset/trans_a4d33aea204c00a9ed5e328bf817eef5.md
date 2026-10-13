

## 时区与 MySQL

[第 5 章](#ch05.html#ch05) 讨论了如何使用 `NOW()` 和其他与日期、时间相关的函数。该章解释了这些函数反映的是服务器上的时间。因此，使用这些函数存储在数据库中的值也是在存储服务器的时间。这听起来可能不是个问题，但假设你将网站从一台服务器迁移到另一台：你导出所有数据，导入到另一台服务器，一切似乎都很正常……除非这两台服务器位于不同的时区，在这种情况下，所有的日期在技术上都会变得不准确。对于某些网站，这种变化可能无关紧要，但如果你的网站提供付费会员服务呢？这意味着某些人的会员资格可能会提前几小时过期，而另一些人的则会晚几小时过期！归根结底，数据库的目标是可靠地存储信息。

解决这一特定问题的方法是以时区中立的方式存储日期和时间。要做到这一点，需要用到所谓的 UTC（*协调世界时*，是的，其缩写与术语并不完全匹配）。UTC 与格林威治标准时间 (GMT) 一样，提供了一个通用的原点，世界上所有的时间都可以表示为 UTC 加上或减去若干小时和分钟（**[表 6.8](#ch06.html#ch06table08)**）。

**表 6.8. UTC 偏移量**

![Image](graphics/06tab08.jpg)

幸运的是，你不必知道这些数值，也不必执行任何计算来确定服务器的 UTC。相反，`UTC_DATE()` 函数返回 UTC 日期；`UTC_TIME()` 返回当前 UTC 时间；`UTC_TIMESTAMP()` 返回当前日期和时间。

一旦你存储了 UTC 时间，就可以检索经过调整以反映服务器或用户位置的时间。要将日期和时间从一个时区转换为另一个时区，请使用 `CONVERT_TZ()` ![Image](graphics/circle-a.jpg)：

```
CONVERT_TZ(dt, from, to)
```

![Image](graphics/06_figure_20_a.jpg)

![Image](graphics/circle-a.jpg) 将当前 UTC 日期和时间转换为美国东部夏令时间 (EDT)。

第一个参数是日期和时间值，例如函数的结果或存储在列中的值。第二个和第三个参数是命名的时区。要使用此函数，时区列表必须已存储在 MySQL 中，你的安装可能满足也可能不满足此条件（请参阅侧栏）。如果你看到 `NULL` 结果 ![Image](graphics/circle-b.jpg)，请查阅 MySQL 手册，了解如何在服务器上安装时区。

![Image](graphics/06_figure_21_b.jpg)

![Image](graphics/circle-b.jpg) 如果 `CONVERT_TZ()` 函数引用了无效的时区，或者时区未在 MySQL 中安装（此处即为这种情况），它将返回 `NULL`。

要使用这些信息，让我们开始填充 *forums* 数据库，使用 UTC 记录消息发布的日期和时间。

***

### 在 MySQL 中使用时区

MySQL 不一定会默认安装时区支持。为了使用命名时区，*mysql* 数据库中的五个表必须被填充数据。虽然 MySQL 可能不会自动为你完成此操作，但它提供了相关工具供你自行操作。

此过程的复杂程度刚好使得本书没有足够的篇幅来讨论它（无法涵盖所有可能的情况、操作系统等）。但你可以通过在 MySQL 手册中查找“服务器时区支持”来找到说明。

如果你继续在 MySQL 中使用时区，还需要保持 *mysql* 数据库中的此信息处于最新状态。特别是关于何时以及如何实行夏令时的时区规则，变化频繁。同样，MySQL 手册中也有更新时区的说明。

***

### 使用 UTC

**1.** 使用你喜欢的任何客户端访问 *forums* 数据库。

与前一章一样，本章也将在所有示例中使用 mysql 客户端。你也可以使用 phpMyAdmin 或其他工具作为 MySQL 的界面。

**2.** 如有必要，将编码更改为 UTF-8 ![Image](graphics/circle-c.jpg)：

```
CHARSET utf8;
```

![Image](graphics/06_figure_22_c.jpg)

![Image](graphics/circle-c.jpg) 用于与 MySQL 通信的字符集应与数据库中使用的字符集匹配。

由于数据库使用 UTF-8 作为其字符集，与数据库的通信应使用相同的字符集。上一行命令（在本章前一节中已解释）正是执行此操作。请注意，仅当使用 mysql 客户端时才需要执行此操作。此外，如果你未使用 UTF-8，请相应地更改命令。

**3.** 向 *forums* 表添加一些新记录 ![Image](graphics/circle-d.jpg)：

```
INSERT INTO forums (name) VALUES
('MySQL'), ('PHP'), ('Sports'),
('HTML'), ('CSS'), ('Kindling');
```

![Image](graphics/06_figure_23_d.jpg)

![Image](graphics/circle-d.jpg) 向 *forums* 表添加记录。

由于 *messages* 表依赖于从 *forums* 和 *users* 表检索的值，因此必须先填充这两个表。使用此 `INSERT` 命令，只需为 *name* 列提供值（表的 *forum_id* 列将由 MySQL 自动分配自增整数）。

**4.** 向 *users* 表添加一些记录 ![Image](graphics/circle-e.jpg)：

```
INSERT INTO users (username, pass,
first_name, last_name, email) VALUES
('troutster', SHA1('mypass'),
'Larry', 'Ullman', 'lu@example.com'),
('funny man', SHA1('monkey'),
'David', 'Brent', 'db@example.com'),
('Gareth', SHA1('asstmgr'), 'Gareth',
'Keenan', 'gk@example.com');
```

![Image](graphics/06_figure_24_e.jpg)

![Image](graphics/circle-e.jpg) 向 *users* 表添加记录。

如果你对此处的 `INSERT` 语法或 `SHA1()` 函数的用法有任何疑问，请参阅 [第 5 章](#ch05.html#ch05)。

**5.** 向 *messages* 表添加新记录 ![Image](graphics/circle-f.jpg)：

```
SELECT * FROM forums;
SELECT user_id, username FROM users;
INSERT INTO messages (parent_id, forum_id, user_id, subject, body, date_entered) VALUES
(0, 1, 1, 'Question about normalization.', 'I''m confused about normalization. For the second normal form (2NF), I read...', UTC_TIMESTAMP()),
(0, 1, 2, 'Database Design', 'I''m creating a new database and am having problems with the structure. How many tables should I have?...', UTC_TIMESTAMP()),
(2, 1, 2, 'Database Design', 'The number of tables your database includes...', UTC_TIMESTAMP()),
(0, 1, 3, 'Database Design', 'Okay, thanks!', UTC_TIMESTAMP()),
(0, 2, 3, 'PHP Errors', 'I''m using the scripts from Chapter 3 and I can''t get the first calculator example to work. When I submit the form...', UTC_TIMESTAMP());
```

![Image](graphics/06_figure_25_f.jpg)

