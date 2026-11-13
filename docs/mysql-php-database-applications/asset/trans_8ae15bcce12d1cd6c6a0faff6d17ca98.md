

提示：MySQL 倾向于将日期作为字符串接收，因此 000601 比类似的整数更好的选择。对日期值使用字符串可能会让你避免以后遇到一些错误。

从日期和时间列中提取信息可能是一项挑战。MySQL 提供了许多有助于操作这些列的函数。

## date

用法：date
date 列类型以 YYYY-MM-DD 格式存储值。它允许的值范围在 1000-01-01 到 9999-12-31 之间。

## datetime

用法：datetime [null | not null] [default]
datetime 类型以 YYYY-MM-DD HH:MM:SS 格式存储值。它允许的值范围在 1000-01-01 00:00:00 到 9999-12-31 23:59:59 之间。

## timestamp

用法：timestamp(size)
这是一个方便的列类型，它会自动记录行最近一次更改的时间，无论是插入还是更新。Size 可以定义为 2 到 14 之间的任何数字。表 2-3 显示了每个列大小存储的值。默认值为 14。请记住，如果有多个 'Timestamp' 字段，只有第一个字段会自动更改。timestamp 字段以后可以通过显式将其赋值为 NULL 来强制更新。

| 大小 | 格式 |
|------|--------|
| 2 | YY |
| 4 | YYYYMM |
| 6 | YYYYMMDD |
| 8 | YYYYMMDD |
| 10 | YYYYMMDDHHMM |
| 12 | YYYYMMDDHHMMSS |
| 14 | YYYYMMDDHHMMSS |

## time

用法：time

此类型以 HH:MM:SS 格式存储时间，值范围从 -838:59:59 到 838:59:59。值范围之大的原因是 time 列类型可用于存储涉及时间的数学方程的结果。

## year

用法：year[(2|4)]

在这个后 Y2K 时代，很难想象你会想要以两位数格式存储年份，但你可以。在两位数格式中，允许的日期是 1970 到 2069 之间（包含）的数字。数字 70–99 前面加 19，01–69 前面加 20。

四位数年份格式允许的值范围是 1901 到 2155。

## 创建索引

MySQL 可以在任何列上创建索引。任何标准表最多可有 16 个索引列。（MyISAM 表默认支持 32 个索引，并可配置为支持 64 个。）基本语法如下：

```
index [index_name] (indexed_column)
```

> 尽管索引名称是可选的，但你应始终为索引命名。如果你想使用 SQL alter 语句删除或更改索引，这将非常重要。如果你不指定名称，MySQL 将基于索引中的第一列来命名索引。

创建索引的另一种方法是将列声明为主键。请注意，任何 auto_increment 列都必须定义为唯一索引的一部分，并且通常（但不一定）是表的主键。在以下代码中，id_col 列已建立索引：

```
create table my_table (
  id_col int unsigned auto_increment primary key,
  another_col text
);
```

主键也可以像其他索引一样，在列定义之后声明，如以下代码所示：

```
create table my_table (
 id_col int unsigned not null auto_increment,
 another_col text,
 primary key(id_col)
);
```

索引可以跨多个列。如果查询在搜索中联合使用两个列，你可以使用此语句创建一个覆盖这两个列的索引：

```
create table mytable(
 id_col int unsigned not null,
 another_col char(200) not null,
 index dual_col_index(id_col, another_col)
);
```

前面的索引将用于以 id_col 开始且可以包含 another_col 的搜索。此类索引从左到右工作。因此，此索引将用于仅在 id_col 上的搜索。但是，它不会用于另一个列上的搜索。

你也可以仅对列的一部分创建索引。对于 char、varchar 和 blob 列，你可以创建列初始部分的索引。语法如下：

```
index index_name (column_name(column_length))
```

例如：

```
create table my_table(
 char_column char (255) not null,
 text_column text not null,
 index index_on_char (char_column(20)),
 index index_on_text (text_column(200))
);
```

索引还可以通过使用 unique 约束来确保表中每个行都存在唯一值，如下所示。

```
create table my_table(
 char_column char (255) not null,
 text_column text not null,
 unique index index_on_char (char_column)
);
```

## 表类型

MySQL 提供多种表类型：MyISAM、BDB、InnoDB 和 Heap。默认表类型是 MyISAM。声明表类型的语法如下：

```
create table table_name (
    column_name column_type column_attributes
)type=table_type
```

在第 1 章中，我们讨论了事务及其概念对关系型数据库和围绕关系型数据库构建的应用程序的重要性。很长一段时间内，MySQL 不支持事务，许多人将这一缺失视为一个致命缺陷。很多开发者因此不愿使用 MySQL。

但情况不再如此：MySQL 确实支持完整的 ACID 事务（有关 ACID 的定义见第 1 章）。但是，为了使用事务，你需要使用支持该功能的表类型。以下关于 MySQL 中可用表类型的讨论非常重要。请务必仔细阅读，并通过定期查阅 MySQL 在线手册来跟进 MySQL 表类型的变化。如果你对 MySQL 表类型有进一步的问题，应查阅在线手册以获取最新信息。

### MyISAM

在大多数安装中，MyISAM 是默认的 MySQL 表类型。在几个版本之前，它是 MySQL 中唯一可用的表类型。MyISAM 表速度极快且稳定；但是，它们不支持事务。它们仅提供表级数据锁定。

MyISAM 表针对使用 `select` 语句检索数据的速度进行了优化。由于这种优化以及缺乏事务支持，MyISAM 表最适合那些运行 `select` 操作的频率远高于运行 `update` 或 `delete` 操作的表。

例如，如果你正在创建一个购物车（如在第 14 章中所做），你可能有一个或两个专门用于产品目录的表，以及其他专门用于记录用户信息和订单的表。保存目录信息（商店中可用的商品）的表可能不会频繁更改——最多一天几次。而且如果你的店铺运营良好，当用户浏览你提供的商品时，这些数据会被频繁查询。MyISAM 表非常适合用于此目的的表。存储购物车数据和记录销售信息的表将受到 `insert` 和 `update` 查询的影响，远高于受到 `select` 查询的影响。对于这类表，你最好使用事务性表类型之一：InnoDB、Gemini 或 BerkeleyDB。

在几乎所有系统上，MyISAM 都是默认表类型。你可以运行任何有效的 `create` 语句，即使在 create 语句中不包含 type 属性，MySQL 也会创建一个 MyISAM 表。但是，如果你想更加谨慎，可以在语句中包含 type=myisam，如下所示：

```
create table mytable(
    col1 int,
    col2 text
) type=myisam;
```

### InnoDB 表

InnoDB 表提供完整的 ACID 事务支持（有关 ACID 的定义见第 1 章）和行级锁定。尽管 MySQL 中还有其他事务性表类型可用，但 InnoDB 可能是本书大多数读者决定使用的事务性表类型。MySQL AB（维护 MySQL 软件包的公司，在其标准分发中捆绑 InnoDB 表，并与 Innobase (www.innobase.com) 密切合作，以确保这些表与 MySQL 配合良好）。

如果你将应用程序托管在 ISP 上，则在为这些表编写应用程序之前，请确保主机支持 InnoDB 表。你可以通过运行以下查询来检查这些表是否可用：show variables like 'have%'。

| 变量名 | 值 |
|---------------|-------|
| have_bdb | NO |
| have_innodb | YES |
| have_isam | YES |
| have_raid | NO |
| have_symlink | YES |
| have_openssl | NO |

6 rows in set (0.30 sec)

正如你从前面的输出中可以看到的，have_innodb 的值为 YES。如果你或你的 ISP 系统上的值为 NO，则 InnoDB 表不可用。

创建 InnoDB 表，请在 create 语句中添加 type=innodb，如下所示：

```
create table mytable(
    col1 int,
    col2 text
) type=innodb;
```

