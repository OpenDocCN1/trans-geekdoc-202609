
## MySQL UNION

UNION 语句用于将一个以上 SELECT 语句的结果合并为一个 SQL 查询的结果。对于有效的 UNION 语句，所有 SELECT 语句必须具有相同数量的列，并且这些列在每个 SELECT 语句中必须是相同的数据类型。MySQL 支持 UNION 和 UNION ALL 构造来连接 SELECT 结果。

在学习使用 UNION 时，可以先考虑编写单独的 SELECT 语句。UNION 语句中的所有单独 SELECT 语句都是有效的 SELECT 语句，除了 ORDER BY 子句，只能在 UNION 语句中定义一次，用于对所有合并查询的结果进行排序。列表 1-28 显示了一个示例。

### LISTING 1-28: union.sql
```sql
SELECT f.country
FROM  flags f
INNER JOIN colors c USING (color)
WHERE c.is_dark = 'yes'
UNION
SELECT f.country
FROM  flags f
INNER JOIN colors c USING (color)
WHERE c.is_primary = 'yes';
```

| country |
|---------|
| Australia |
| Sweden |
| USA |
| Canada |
| Japan |

UNION 还支持额外的关键字 ALL 或 DISTINCT。默认情况下，UNION 语法返回所有 SELECT 集合的唯一行集，并删除任何重复项。然而，ALL 语法返回每个 SELECT 语句组合的所有行，而 DISTINCT 语法返回每个 SELECT 的所有 DISTINCT 行。列表 1-29 显示了此示例。

### LISTING 1-29: union-all.sql
```sql
SELECT f.country, 'Dark'
FROM  flags f
INNER JOIN colors c USING (color)
WHERE c.is_dark = 'yes'
UNION ALL
SELECT f.country, 'Primary'
FROM  flags f
INNER JOIN colors c USING (color)
WHERE c.is_primary = 'yes';
```

| country | Dark |
|---|---|
| Australia | Dark |
| Sweden | Dark |
| USA | Dark |
| Australia | Primary |
| Sweden | Primary |
| USA | Primary |
| Australia | Primary |
| Canada | Primary |
| Japan | Primary |
| USA | Primary |
| Australia | Primary |
| Canada | Primary |
| Japan | Primary |
| USA | Primary |

在列表 1-30 中，您将看到使用 DISTINCT 关键字得到的不同结果集。

可在 Wrox.com 上下载

### LISTING 1-30: union-distinct.sql
```sql
SELECT f.country, 'Dark'
FROM flags f
INNER JOIN colors c USING (color)
WHERE c.is_dark = 'yes'
UNION DISTINCT
SELECT f.country, 'Primary'
FROM flags f
INNER JOIN colors c USING (color)
WHERE c.is_primary = 'yes';
```

| country | Dark |
|---|---|
| Australia | Dark |
| Sweden | Dark |
| USA | Dark |
| Australia | Primary |
| Sweden | Primary |
| USA | Primary |
| Canada | Primary |
| Japan | Primary |

> MySQL 不支持 INTERSECT 或 MINUS 语法，这些是可在其他关系数据库产品中找到的额外 UNION 相关构造。请参阅 http://dev.mysql.com/doc/refman/5.1/en/union.html 获取更多信息。

## MySQL 查询中的 GROUP BY

GROUP BY 语法允许对所选行进行聚合并使用标量函数。在 MySQL 中，可以在没有 GROUP BY 的情况下使用标量函数，并产生可能被视为不一致的结果。列表 1-31 显示了一个示例。

### LISTING 1-31: count-no-group.sql
```sql
SELECT country, COUNT(*)
FROM   flags;
```

| country | COUNT(*) |
|---|---|
| Australia | 12 |

MySQL 提供了预期的 ANSI SQL 语法，要求使用 sql_mode 使 GROUP BY 语句包含所有非标量函数列。列表 1-32 显示了此示例。

### LISTING 1-32: count-group.sql
```sql
SET SESSION sql_mode=ONLY_FULL_GROUP_BY;

SELECT country, COUNT(*)
FROM   flags;
```
ERROR 1140 (42000): Mixing of GROUP columns (MIN(),MAX(),COUNT(),...) with no GROUP columns is illegal if there is no GROUP BY clause

```sql
SELECT country, COUNT(*) AS color_count
FROM   flags
GROUP BY country;
```

| country | color_count |
|---|---|
| Australia | 3 |
| Canada | 2 |
| Japan | 2 |
| Sweden | 2 |
| USA | 3 |

存在一个不返回数值值的标量函数；这就是列表 1-33 中显示的 GROUP_CONCAT() 函数。

### LISTING 1-33: count-group-concat.sql
```sql
SELECT country, GROUP_CONCAT(color) AS colors
FROM   flags
GROUP BY country;
```

| country | colors |
|---|---|
| Australia | Blue,Red,White |
| Canada | Red,White |
| Japan | Red,White |
| Sweden | Blue,Yellow |
| USA | Blue,Red,White |

```sql
SELECT country, GROUP_CONCAT(color) AS colors, COUNT(*) AS color_count
FROM flags
GROUP BY country;
```

| country | colors | color_count |
|---|---|
| Australia | Blue,Red,White | 3 |
| Canada | Red,White | 2 |
| Japan | Red,White | 2 |
| Sweden | Blue,Yellow | 2 |
| USA | Blue,Red,White | 3 |

5 rows in set (0.00 sec)

### WITH ROLLUP

GROUP BY 语法的特性是额外的关键字 WITH ROLLUP。使用此语法，返回的行包括每个 GROUP BY 列的聚合行。这由 NULL 表示。列表 1-34 中的输出显示了单列和双列示例：

### LISTING 1-34: count-with-rollup.sql
```sql
SELECT country, COUNT(*) AS color_count
FROM flags
GROUP BY country WITH ROLLUP;
```

| country | color_count |
|---|---|
| Australia | 3 |
| Canada | 2 |
| Japan | 2 |
| Sweden | 2 |
| USA | 3 |
| NULL | 12 |

```sql
SELECT c.color, c.is_dark, COUNT(*)
FROM colors c, flags f
WHERE c.color = f.color
GROUP BY c.color, c.is_dark WITH ROLLUP;
```

| color | is_dark | COUNT(*) |
|---|---|---|
| Blue | yes | 3 |
| Blue | NULL | 3 |
| Red | no | 4 |
| Red | NULL | 4 |
| White | no | 4 |
| White | NULL | 4 |
| NULL | NULL | 11 |

### HAVING

为了限制使用 GROUP BY 对任何标量函数返回的聚合行列表，您使用 HAVING 子句来定义条件，而不是 WHERE 子句。列表 1-35 显示了一个示例。

### LISTING 1-35: having.sql
```sql
SELECT country, GROUP_CONCAT(color) AS colors
FROM flags
GROUP BY country
HAVING COUNT(*) = 2;
```

| country | colors |
|---|---|
| Canada | Red,White |
| Japan | Red,White |
| Sweden | Blue,Yellow |

您可以像前面的示例所示使用在 SELECT 子句中未定义的标量函数。与 ORDER BY 不同，您必须指定列的名称；数字列顺序不是允许的语法。

## MySQL 中的逻辑运算和流程控制

MySQL 对任何逻辑都有三种状态：TRUE、FALSE 或 NULL：

```sql
mysql> SELECT TRUE,FALSE,NULL;
```

| TRUE | FALSE | NULL |
|---|---|---|
| 1 | 0 | NULL |

诸如 =, <=>, IS, IS NOT, IN, ISNULL 等比较操作将导致这三种状态之一：

```sql
mysql> SELECT 'A' IS NOT NULL, 'A' IS NULL, NULL = NULL, NULL IS NULL;
```

| 'A' IS NOT NULL | 'A' IS NULL | NULL = NULL | NULL IS NULL |
|---|---|---|---|
| 1 | 0 | NULL | 1 |

MySQL 对 TRUE 状态始终返回 1，任何非零值都计算为 TRUE。

```sql
mysql> SELECT 5 IS TRUE, 0 IS FALSE, 10 IS NOT NULL;
```

| 5 IS TRUE | 0 IS FALSE | 10 IS NOT NULL |
|---|---|---|
| 1 | 1 | 1 |

### 逻辑运算符

MySQL 有四个逻辑控制运算符：AND、OR、NOT 和 XOR。其中三个运算符也有简写表示：&&（AND）、||（OR）、!（NOT）。这些简写表示不应与位运算符混淆，后者是单个字符 & 和 |。

```sql
mysql> SELECT TRUE AND TRUE, TRUE AND FALSE, TRUE AND NULL, NULL AND NULL;
```

| TRUE AND TRUE | TRUE AND FALSE | TRUE AND NULL | NULL AND NULL |
|---|---|---|---|
| 1 | 0 | NULL | NULL |

```sql
mysql> SELECT TRUE OR TRUE, TRUE OR FALSE, TRUE OR NULL, NULL OR NULL;
```

| TRUE OR TRUE | TRUE OR FALSE | TRUE OR NULL | NULL OR NULL |
|---|---|---|---|
| 1 | 1 | 1 | NULL |

```sql
mysql> SELECT TRUE XOR TRUE, TRUE XOR FALSE, TRUE XOR NULL, NULL XOR NULL;
```

| TRUE XOR TRUE | TRUE XOR FALSE | TRUE XOR NULL | NULL XOR NULL |
|---|---|---|---|
| 0 | 1 | NULL | NULL |

与 AND、OR 和 XOR 不同，NOT 运算符不计算两个值；它只是返回提供值的逆值：

```sql
mysql> SELECT NOT TRUE, NOT FALSE, NOT NULL;
```

| NOT TRUE | NOT FALSE | NOT NULL |
|---|---|---|
| 0 | 1 | NULL |

您可以使用 sql_mode=PIPES_AS_CONCAT 更改 MySQL 的 || 简写运算符，这将导致如列表 1-36 所示的意外结果。
