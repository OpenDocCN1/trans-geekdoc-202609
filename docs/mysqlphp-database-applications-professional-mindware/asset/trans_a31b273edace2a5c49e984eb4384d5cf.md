
（从左开始计数）被返回。如果 count 为负数，则返回最后一个分隔符右侧的所有内容（从右开始计数）。

```
SUBSTRING_INDEX(str,delim,count) (used in examples)
RETURNS: string
```
mysql> select substring_index('mysqlfunctions mysql', 'fu', 1);
| substring_index('mysqlfunctions mysql', 'fu', 1) |
|---|
| mysql |
1 row in set (0.00 sec)

mysql> select substring_index('mysqlfunctions mysql', 'fu', -1);
| substring_index('mysqlfunctions mysql', 'fu', -1) |
|---|
| nctions mysql |
1 row in set (0.00 sec)

## LTRIM

```
LTRIM(str)
RETURNS: string
```

## RTRIM

此函数返回删除尾部空格字符后的字符串 str。

```
RTRIM(str)
RETURNS: string
```

## TRIM

此函数返回删除所有 remstr 前缀和/或后缀后的字符串 str。如果未给出 BOTH、LEADING 或 TRAILING 中的任何限定符，则假定为 BOTH。如果未指定 remstr，则删除空格。

```
TRIM([[BOTH | LEADING | TRAILING] [remstr] FROM] str) (used in examples)
RETURNS: string
```

mysql> select trim(both '\n' from '\n mystring');
| trim(both '\n' from '\n mystring') |
|---|
| mystring |
1 row in set (0.00 sec)

请注意，remstr 将仅精确匹配字符的精确序列。因此，在 remstr 中放置 '\t\n\' 将仅删除制表符和换行符连续出现的情况。

## REPLACE

此函数返回将字符串 from_str 的所有出现位置替换为字符串 to_str 后的字符串 str。

```
REPLACE(str,from_str,to_str)
RETURNS: string
```

## SOUNDEX

此函数从 str 返回一个 soundex 字符串。

```
SOUNDEX(str)
RETURNS: string
```

发音“大致相同”的两个字符串应具有相同的 soundex 字符串。“标准” soundex 字符串长度为四个字符，但 SOUNDEX() 函数返回任意长度的字符串。您可以使用 SUBSTRING() 对结果进行操作以获得“标准” soundex 字符串。给定字符串中的所有非字母数字字符将被忽略。A-Z 范围之外的所有国际字母字符均被视为元音。

## SPACE

此函数返回由 N 个空格字符组成的一个字符串。

```
SPACE(N)
RETURNS: string
```

## REPEAT

此函数返回由字符串 str 重复 count 次组成的一个字符串。如果 count <= 0，则返回空字符串。如果 str 或 count 为 NULL，则返回 NULL。

```
REPEAT(str,count)
RETURNS: string
```

## REVERSE

此函数返回字符顺序颠倒后的字符串 str。

```
REVERSE(str)
RETURNS: string
```

## INSERT

此函数返回字符串 str，其中从位置 pos 开始、长度为 len 的子字符串被字符串 newstr 替换。

```
INSERT(str,pos,len,newstr)
RETURNS: string
```
mysql> select insert('mysqlfunctions', 6,2,'FU');
| insert('mysqlfunctions', 6,2,'FU') |
|---|
| mysqlFUnctions |
1 row in set (0.44 sec)

## ELT

此函数如果 N = 1 则返回 str1，如果 N = 2 则返回 str2，以此类推。如果 N 小于 1 或大于参数数量，则返回 NULL。ELT() 是 FIELD() 的补充。

```
ELT(N,str1,str2,str3,...)
RETURNS: string
```
mysql> select elt(2, 'foo', 'bar', 'foobar');
| elt(2, 'foo', 'bar', 'foobar') |
|---|
| bar |
1 row in set (0.00 sec)

## FIELD

此函数返回 str 在 str1,str2,str3,... 列表中的索引。如果未找到 str，则返回 0。FIELD() 是 ELT() 的补充。

```
FIELD(str,str1,str2,str3,...)
RETURNS: int
```
mysql> select field('foobar', 'foo', 'bar', 'foobar');
| field('foobar', 'foo', 'bar', 'foobar') |
|---|
| 3 |
1 row in set (0.01 sec)

## LCASE

此函数根据当前字符集映射（默认为 ISO-8859-1 Latin1）将字符串 str 中的所有字符更改为小写。

```
LCASE(str) or LOWER(str) (used in examples)
RETURNS: string
```

## UCASE

此函数根据当前字符集映射（默认为 ISO-8859-1 Latin1）将字符串 str 中的所有字符更改为大写。

```
UCASE(str) or UPPER(str)
RETURNS: string
```

## LOAD_FILE

此函数读取文件并以字符串形式返回文件内容。文件必须位于服务器上，并且您必须指定文件的完整路径名。文件必须对所有人可读且小于 max_allowed_packet。如果文件不存在或无法读取，则函数返回 NULL。

```
LOAD_FILE(file_name)
RETURNS: string
```

## 日期和时间函数

MySQL 提供了许多用于计算日期的函数。在所有可用的 MySQL 函数中，这些是你最有可能最频繁使用的函数。

DATE_FORMAT 函数将允许您将日期格式化为 MySQL 时间戳的形式。此外，还有几个函数可以轻松地从列中获取特定的日期信息。例如，要查找时间戳列中所有条目的星期几，您可以使用以下方法。

mysql> select dayname(created) from guestbook;
| dayname(created) |
|---|
| Sunday |
| Sunday |
| Wednesday |
| Sunday |
| Sunday |
| Wednesday |
| Wednesday |
| Wednesday |

### DAYOFWEEK

此函数返回 date 的星期几索引（1 = 星期日，2 = 星期一，... 7 = 星期六）。这些索引值对应于 ODBC 标准。

```
DAYOFWEEK(date) (used in examples)
RETURNS: int
```
mysql> select dayofweek('2001-01-01');
| dayofweek('2001-01-01') |
|---|
| 2 |
1 row in set (0.33 sec)

### WEEKDAY

此函数返回 date 的星期几索引（0 = 星期一，1 = 星期二，... 6 = 星期日）。

```
WEEKDAY(date) (used in examples)
RETURNS: int
```

### DAYOFMONTH

此函数返回 date 的月份中的日期，范围为 1 到 31。

```
DAYOFMONTH(date)
RETURNS: int
```

### DAYOFYEAR

此函数返回 date 的一年中的日期，范围为 1 到 366。

```
DAYOFYEAR(date)
RETURNS: int
```
mysql> select dayofmonth('02-01-2000');
| dayofmonth('02-01-2000') |
|---|
| 20 |
1 row in set (0.00 sec)

### MONTH

此函数返回 date 的月份，范围为 1 到 12。

```
MONTH(date)
RETURNS: int
```

### DAYNAME

此函数返回 date 的星期几的全名。

```
DAYNAME(date)
RETURNS: string
```
mysql> select dayname('10/01/2000');
| dayname('10/01/2000') |
|---|
| Wednesday |
1 row in set (0.00 sec)

### MONTHNAME

此函数返回 date 的月份的全名。

```
MONTHNAME(date)
RETURNS: string
```

### QUARTER

此函数返回 date 的年份季度，范围为 1 到 4。

```
QUARTER(date)
RETURNS: int
```

要查找在一年第二季度签署您留言簿的所有人员，您可以使用以下方法：

```
select name from guestbook where quarter(created) = 2;
```

### WEEK

使用单个参数，此函数返回 date 的周数，范围为 0 到 53。

```
WEEK(date [, first])
RETURNS: int
```

可选的第二个参数允许您指定周从星期日还是星期一开始。如果第二个参数为 0，则周从星期日开始；如果第二个参数为 1，则周从星期一开始。

### YEAR

此函数返回 date 的年份，范围为 1000 到 9999。

```
YEAR(date) (used in examples)
RETURNS: int
```

### YEARWEEK

此函数以 YYYYWW 格式返回日期的年份和周数。第二个参数的工作方式与 WEEK() 中的第二个参数完全相同。

```
YEARWEEK(date [,first])
RETURNS: int
```

### HOUR

此函数返回 time 的小时，范围为 0 到 23。

```
HOUR(time)
RETURNS: int
```

### MINUTE

此函数返回 time 的分钟，范围为 0 到 59。

```
MINUTE(time)
RETURNS: int
```
