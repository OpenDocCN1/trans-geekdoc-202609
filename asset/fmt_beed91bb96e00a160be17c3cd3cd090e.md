
## BIN

此函数返回 N 的二进制值的字符串表示，其中 N 是一个长整数（BIGINT）。它等同于 `CONV(N,10,2)`。如果 N 为 NULL，则返回 NULL。

`BIN(N)`
RETURNS: string

## OCT

此函数返回 N 的八进制值的字符串表示，其中 N 是一个长整数（BIGINT）。它等同于 `CONV(N,10,8)`。如果 N 为 NULL，则返回 NULL。

`OCT(N)`
RETURNS: string

## HEX

此函数返回 N 的十六进制值的字符串表示，其中 N 是一个长整数（BIGINT）。它等同于 `CONV(N,10,16)`。如果 N 为 NULL，则返回 NULL。

`HEX(N)`
RETURNS: string

## CHAR

此函数将参数解释为整数，并返回一个由这些整数的 ASCII 代码值组成的字符串。NULL 值会被跳过。

### Appendix I: MySQL Function Reference

`CHAR(N....)`
RETURNS: string

## CONCAT

此函数返回参数拼接后的结果字符串。如果任何参数为 NULL，则返回 NULL。`CONCAT` 可以有两个两个参数。数字参数会被转换为等效的字符串形式。

`CONCAT(str1,str2,...)` (used in examples)
RETURNS: string

此函数用于下面的示例，在查询的 where 子句中为列添加通配符字符。

```sql
select 1 from blocked_domains
where '$REMOTE_HOST' like concat('%',domain)
and release_dt is null
```

## LENGTH

此函数返回字符串 `str` 的长度。注意对于 `CHAR_LENGTH()`，多字节字符只被计算一次。

`LENGTH(str)`

or

`CHAR_LENGTH(str)`
RETURNS: int

```sql
mysql select length('mysql functions');
+--------------------------------------+
| length('mysql functions') |
+--------------------------------------+
| 16 |
+--------------------------------------+
```

## LOCATE

此函数返回子字符串在 `str` 中第一次出现的位置。如果未找到子字符串，则返回 0。

```
LOCATE(substr,str[,pos])
RETURNS: int
```

## INSTR

此函数返回子字符串在 `str` 中第一次出现的位置。它与 `LOCATE()` 相同，只是参数交换了位置，且不允许使用 `pos` 参数指定搜索位置。

## LPAD

此函数返回字符串 `str`，左侧填充字符串 `padstr` 直到长度达到 `len` 个字符。

```
LPAD(str,len,padstr)
RETURNS: string
```

## RPAD

此函数返回字符串 `str`，右侧填充字符串 `padstr` 直到长度达到 `len` 个字符。

```
RPAD(str,len,padstr)
RETURNS: string
```

## LEFT

此函数返回 `str` 从左侧的 `len` 个字符。

```
LEFT(str,len)
RETURNS: string
```

## RIGHT

此函数返回 `str` 从右侧的 `len` 个字符。

```
RIGHT(str,len)
RETURNS: string
```

## SUBSTRING

此函数返回 `str` 中从 `pos` 开始、长度 `len` 个字符的子字符串。使用 FROM 的变体形式是 ANSI SQL92 语法。

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

此函数返回 `str` 中出现 `count` 次分隔符后的子字符串。如果 `count` 为正数，则返回最后一个分隔符（从左侧计数）左侧的内容。如果 `count` 为负数，则返回最后一个分隔符（从右侧计数）右侧的内容。

```
SUBSTRING_INDEX(str,delim,count) (used in examples)
RETURNS: string
```

## LTRIM

此函数返回移除头部空格的字符串 `str`。

```
LTRIM(str)
RETURNS: string
```

## RTRIM

此函数返回移除末尾空格的字符串 `str`。

```
RTRIM(str)
RETURNS: string
```

## TRIM

此函数返回移除所有 `remstr` 前缀和字符串字符串。如果没有指定 BOTH、LEADING 或 TRAILING，默认为 BOTH。如果未指定 `remstr`，则移除空格。

```
TRIM([[BOTH | LEADING | TRAILING][remstr] FROM) str) (used in examples)
RETURNS: string
```

# 录 I：MySQL 函数参考

```
| trim(both '\n' from '\n mystring') |
+--------------------------------+
|    mystring                    |
+--------------------------------+
1 row in set (0.00 sec)
```

注意 `remstr` 仅匹配精确的字符序列。因此，在 `remstr` 中放入 `\n` 只会制表符和换行符连续出现的情况。

## REPLACE

此函数返回字符串 `str`，并将其中所有的字符串 `from_str` 替换为字符串 `to_str`。

```
REPLACE(str,from_str,to_str)
RETURNS: string
```

## SOUNDEX

此函数根据 `str` 返回一个 soundex 字符串。

```
SOUNDEX(str)
RETURNS: string
```

两个听起来“相似”的字符串应该具有相同的 soundex 字符串。“标准” soundex 字符串长度为四个字符，但 `SOUNDEX()` 函数返回一个任意长度的字符串。你可以使用 `SUBSTRING()` 来获取“标准”的 soundex 字符串。给定字符串中的非字母数字字符都会被忽略。所有 A-Z 范围之外的国际字母均被视为元音。

## SPACE

此函数返回一个由 N 个空格字符组成的字符串。

```
SPACE(N)
RETURNS: string
```

## REPEAT

此函数返回一个由 `str` 重复 `count` 次组成的字符串。如果 `count <= 0`，则返回空字符串。如果 `str` 或 `count` 为 `NULL`，则返回 `NULL`。

```
REPEAT(str,count)
RETURNS: string
```

## REVERSE

此函数返回字符顺序反后的字符串 `str`。

```
REVERSE(str)
RETURNS: string
```

## INSERT

此函数返回字符串 `str`，其中从位置 `pos` 开始且长度为 `len` 的子字符串被替换为字符串 `newstr`。

```
INSERT(str,pos,len,newstr)
RETURNS: string
```

```sql
mysql> select insert('mysqlfunctions', 6.2,'FU');
+------------------------------------------------+
| insert('mysqlfunctions', 6.2,'FU') |
+------------------------------------------------+
| mysqlFunctions                               |
+------------------------------------------------+
1 row in set (0.04 sec)
```

## ELT

此函数当 `N = 1` 时返回 `str1`，当 `N = 2` 时返回 `str2`，依此类推。如果 `N` 小于 1 或大于参数数量，则返回 `NULL`。`ELT()` 是 `FIELD` 的互补函数。

```
ELT(N,str1,str2,str3,...)
RETURNS: string
```

```sql
mysql> select elt(2,'foo','bar','foobar');
+------------------------------------------------+
| elt(2,'foo','bar','foobar')                     |
+------------------------------------------------+
| bar                                            |
+------------------------------------------------+
1 row in set (0.00 sec)
```

## FIELD

此函数返回 `str` 在 `str1,str2,str3,...` 列表中的索引。如果未找到 `str`，则返回 0。`FIELD()` 是 `ELT` 的互补函数。

```
FIELD(str,str1,str2,str3,...)
RETURNS: int
```

```sql
mysql> select field('foobar','foo','bar','foobar');
+--------------------------------------+
| field('foobar', 'foo', 'bar', 'foobar') |
+--------------------------------------+
|                                      3 |
+--------------------------------------+
1 row in set (0.01 sec)
```

## LCASE

此函数根据当前字符集映射将字符串中的所有字符更改为小写（默认为 ISO-8859-1 Latin1）。

```
LCASE(str) or LOWER(str) (used in examples)
RETURNS: string
```

## UCASE

此函数根据当前字符集映射将字符串中的所有字符更改为大写（默认为 ISO-8859-1 Latin1）。

```
UCASE(str) or UPPER(str)
RETURNS: string
```

## LOAD_FILE

此函数读取文件并将文件内容作为字符串返回。该文件必须位于服务器上，且你必须指定文件的完整路径。文件必须对所有人可读且小于 `max_allowed_packet`。如果文件不存在或无法读取，该函数返回 `NULL`。

```
LOAD_FILE(file_name)
RETURNS: string
```

## 日期时间函数

MySQL 提供了许多计算日期的函数。在所有可用的 MySQL 函数中，这些是你最可能使用的。

`DATE_FORMAT` 函数允许你将日期格式化为 MySQL 时间戳的形式。此外，还有几个函数可以让你从列中获取特定的日期信息。例如，要查找时间戳列中所有条目的星期，可以使用以下语句。

```sql
mysql> select dayname(created) from guestbook;
+--------------------------------+
| dayname(created) |
+--------------------------------
| Sunday |
| Sunday |
| Wednesday |
| Sunday |
| Sunday |
| Wednesday |
| Wednesday |
| Wednesday |
```

## DAYOFWEEK

此函数返回日期的星期索引（1 = 日，2 = 周一，... 7 = 星期六）。这些值对应于 ODBC 标准。

```
DAYOFWEEK(date) (used in examples)
RETURNS: int
```

```sql
mysql> select dayofweek('2001-01');
+--------------------------+
| dayofweek('2001-01') |
+--------------------------+
| 1 |
+--------------------------+
1 row in set (0.00 sec)
```

## WEEKDAY

此函数返回星期几索引（0 = 周一，1 = 周二，... 6 = 周日）。

```
WEEKDAY(date) (used in examples)
RETURNS: int
```

## DAYOFMONTH

此函数返回日期的几，范围为 1 到 31。

```
DAYOFMONTH(date)
RETURNS: int
```

## DAYOFYEAR

此函数返回一年中的第几天，范围为 1 到 366。

```
DAYOFYEAR(date)
RETURNS: int
```

## MONTH

此函数返回日期的月份，范围为 1 到 12。

```
MONTH(date)
RETURNS: int
```

## QUARTER

此函数返回季度，范围为 1 到 4。

```
QUARTER(date)
RETURNS: int
```

## DAYNAME

此函数返回日期的星期全称。

```
DAYNAME(date)
RETURNS: string
```

```sql
mysql> select dayname('2001-01');
+--------------------------+
| dayname('2001-01') |
+--------------------------+
| Monday |
+--------------------------+
1 row in set (0.00 sec)
```

## MONTHNAME

此函数返回日期的月份全称。

```
MONTHNAME(date)
RETURNS: string
```

```sql
mysql> select monthname('2001-01');
+--------------------------+
| monthname('2001-01') |
+--------------------------+
| January |
+--------------------------+
1 row in set (0.00 sec)
```

## DATE_FORMAT

此函数按照指定的格式返回日期。

```
DATE_FORMAT(date,format)
RETURNS: string
```

```sql
mysql> select date_format('2001-01-01', '%Y-%m-%d');
+-----------------------------+
| date_format('2001-01-01','%Y-%m-%d') |
+-----------------------------+
| 2001-01-01 |
+-----------------------------+
1 row in set (0.00 sec)
```

## TIMESTAMP

此函数返回当前时间戳或转换为时间戳的表达式。

```
TIMESTAMP()
RETURNS: datetime

TIMESTAMP(expr)
RETURNS: datetime
```

## TIMEDIFF

此函数返回两个时间表达式之间的时间差。

```
TIMEDIFF(expr1,expr2)
RETURNS: time
```

## DATEDIFF

此函数返回两个日期之间的天数。

```
DATEDIFF(expr1,expr2)
RETURNS: int
```

## TIMESTAMP_ADD

此函数向 datetime 表达式增加时间间隔。

```
TIMESTAMP_ADD(expr,expr_interval)
RETURNS: datetime
```

## TIMESTAMP_SUB

此函数从 datetime 表达式减去一个时间间隔。

```
TIMESTAMP_SUB(expr,expr_interval)
RETURNS: datetime
```

574 第 V 部分：附录

## DATE_ADD

这些函数执行日期算术。它们是 MySQL 3.22 的新功能。

```
DATE_ADD(date,INTERVAL expr type)
```

或
```
DATE_SUB(date,INTERVAL expr type)
```

或
```
ADDDATE(date,INTERVAL expr type)
```

`SUBDATE(date,INTERVAL)` (在示例中使用)

返回: date
