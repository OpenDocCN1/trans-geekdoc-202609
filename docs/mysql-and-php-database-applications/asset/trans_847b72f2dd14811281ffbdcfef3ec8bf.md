

如果指定了整数参数 N，则它被用作种子值。你不能在 'order by' 子句中使用带有 RAND() 值的列，因为排序会对该列进行多次评估。但在 MySQL 3.23 中，你可以这样做：`select * from table_name order rand()`。这对于获取随机样本非常有用。请注意，WHERE 子句中的 RAND() 会在每次执行 WHERE 子句时被重新评估。

## LEAST

当带有两个或多个参数时，此函数返回最小（最小值）参数。

```
LEAST(X,Y,....)
RETURNS: type of X
mys> select least(2,7,9,1)
+----------------+
| least(2,7,9,1) |
+----------------+
|                1 |
+----------------+
1 row in set (0.00 sec)
```

## GREATEST

GREATEST 返回最大的（最大值）参数。在 MySQL 3.22.5 之前的版本中，你可以使用 MAX() 代替 GREATEST。

``````
GREATEST(X,Y,....)
RETURNS: type of X
mys> select greatest(2,7,9,1)
+----------------+
| greatest(2,7,9,1) |
+----------------+
|                9 |
+----------------+
1 row in set (0.00 sec)
```

## DEGREES

此返回将参数 X 从弧度转换为度。

```
DEGREES(X)
RETURNS: float
```

## RADIANS

此返回将参数 X 从度转换为弧度。

## String Functions

如果结果的长度大于 `max_allowed_packet` 服务器参数，MySQL 的字符串函数将返回 NULL。可以通过如下命令启动 MySQL 来设置此参数：

```
safe_mysqld -O max_allowed_packet=16M
```

对于操作字符串位置的函数，第一个位置从 1 开始。

## ASCII

返回字符串 str 最左侧字符的 ASCII 代码值。如果 str 是空字符串，则返回 0。如果 str 为 NULL，则返回 NULL。

```
ASCII(str)
RETURNS: int
mysql> select ascii('\n');
+----------------+
| ascii('\n') |
+----------------+
|      10       |
+----------------+
1 row set in (0.00 sec)
```

## ORD

如果字符串 str的最左侧字符是多字节字符，此函数通过返回格式为如下的代码来返回多字节字符的代码：((第一个字节 ASCII 代码)*256+(第二个 ASCII 代码)*25+第三字节 ASCII 代码...)。如果最左侧字符不是多字节字符，ORD 返回的值与类似的 ASCII() 函数相同。

```
ORD(str)
RETURNS: int
```

## CONV

此函数在不同的数字进制之间转换数字。

```
CONV(N,from_base,to_base)
RETURNS: string
```

它返回数字 N 的字符串表示，该数字从进制 `from_base` 转换为 `to_base`。如果任何参数为 NULL，则返回 NULL。参数 N 被解释为整数，可以指定为整数或字符串。最小进制为 2，最大进制为 36。如果 `to_base` 是负数，则 N 被视为符号数；否则，N 被视为无符号。CONV 以 64 位精度工作。

```
mysql> select conv(3,10,2);
+-------------+
| conv(3,10,2) |
+-------------+
| 11          |
```

## BIN

此函数返回 N 的二进制值的字符串表示，其中 N 是一个长整数（BIGINT）。它等同于 `CONV(N,10,2)`。如果 N 为 NULL，则返回 NULL。

BIN(N)
RETURNS: string

## OCT

此函数返回 N 的八进制值的字符串表示，其中 N 是一个长整数（BIGINT）。它等同于 `CONV(N,10,8)`。如果 N 为 NULL，则返回 NULL。

OCT(N)
RETURNS: string

## HEX

此函数返回 N 的十六进制值的字符串表示，其中 N 是一个长整数（BIGINT）。它等同于 `CONV(N,10,16)`。如果 N 为 NULL，则返回 NULL。

HEX(N)
RETURNS: string

## CHAR

此函数将参数解释为整数，并返回一个由这些整数的 ASCII 代码值组成的字符串。NULL 值会被跳过。

## Appendix I: MySQL Function Reference

CHAR(N....)
RETURNS: string

## CONCAT

此函数返回参数拼接后的结果字符串。如果任何参数为 NULL，则返回 NULL。CONCAT 可以有两个两个参数。数字参数会被转换为等效的字符串形式。

CONCAT(str1,str2,...) (used in examples)
RETURNS: string

此函数用于下面的示例，在查询的 where 子句中为列添加通配符字符。

```
select 1 from blocked_domains
where '$REMOTE_HOST' like concat('%',domain)
and release_dt is null
```

## LENGTH

此函数返回字符串 str 的长度。注意对于 `CHAR_LENGTH()`，多字节字符只被计算一次。

LENGTH(str)

or

CHAR_LENGTH(str)
RETURNS: int
mysql select length('mysql functions');

+--------------------------------------+
| length('mysql functions') |
+--------------------------------------+
| 16 |
+--------------------------------------+

## LOCATE

此函数返回子字符串在 str 中第一次出现的位置。如果未找到子字符串，则返回 0。

```
LOCATE(substr,str[,pos])
RETURNS: int
```

## INSTR

此函数返回子字符串在 str 中第一次出现的位置。它与 LOCATE() 相同，只是参数交换了位置，且不允许使用 pos 参数指定搜索位置。

## LPAD

此函数返回字符串 str，左侧填充字符串 padstr 直到长度达到 len 个字符。

```
LPAD(str,len,padstr)
RETURNS: string
```

## RPAD

此函数返回字符串 str，右侧填充字符串 padstr 直到长度达到 len 个字符。

```
RPAD(str,len,padstr)
RETURNS: string
```

## LEFT

此函数返回 str 从左侧的 len 个字符。

```
LEFT(str,len)
RETURNS: string
```

## RIGHT

此函数返回 str 从右侧的 len 个字符。

```
RIGHT(str,len)
RETURNS: string
```

## SUBSTRING

此函数返回 str 中从 pos 开始、长度 len 个字符的子字符串。使用 FROM 的变体形式是 ANSI SQL92 语法。

```
SUBSTRING(str,pos[,len])
```

or

```
SUBSTRING(str FROM pos FOR len)
```

or

```
MID(str,pos,len) (used in examples)
RETURNS: string
```

## SUBSTRING_INDEX

此函数返回 str 中出现 count 次分隔符后的子字符串。如果 count 为正数，则返回最后一个分隔符（从左侧计数）左侧的内容。如果 count 为负数，则返回最后一个分隔符（从右侧计数）右侧的内容。

```
SUBSTRING_INDEX(str,delim,count) (used in examples)
RETURNS: string
```

## LTRIM

此函数返回移除头部空格的字符串 str。

```
LTRIM(str)
RETURNS: string
```

## RTRIM

此函数返回移除末尾空格的字符串 str。

```
RTRIM(str)
RETURNS: string
```

## TRIM

此函数返回移除所有 remstr 前缀和字符串字符串。如果没有指定 BOTH、LEADING 或 TRAILING，默认为 BOTH。如果未指定 remstr，则移除空格。

```
TRIM([[BOTH | LEADING | TRAILING][remstr] FROM) str) (used in examples)
RETURNS: string
```

