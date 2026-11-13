

```
mysql> select trim(both '\n' from '\n mystring');
```

| trim(both '\n' from '\n mystring') |
|------------------------------------|
| mystring                           |

1 行已在结果集中 (0.00 秒)

请注意，remstr 将精确匹配完全相同的字符序列。因此，在前面示例中将 \t\n\n 放入 remstr 参数中，仅删除制表符和换行符连续出现的情况。

### REPLACE

此函数返回字符串 str，其中所有 from_str 出现的位置都被替换为 to_str：

```
REPLACE(str,from_str,to_str)
RETURNS: string
```

### SOUNDEX

此函数从 str 返回一个 soundex 字符串：

```
SOUNDEX(str)
RETURNS: string
```

在英语中发音“差不多相同”的两个字符串应当具有相同的 soundex 字符串。“标准”soundex 字符串长度为四个字符，但 SOUNDEX() 函数返回任意长度的字符串。您可以在结果上使用 SUBSTRING() 来获取“标准”soundex 字符串。给定字符串中所有非字母数字字符均被忽略。A–Z 范围之外的所有国际字母字符均被视为元音。

```
mysql> select soundex('functions'), soundex('junctions'),
soundex('fiction');
```

| soundex('functions') | soundex('junctions') | soundex('fiction') |
|----------------------|----------------------|--------------------|
| F52352               | J52352               | F235               |

1 行已在结果集中 (0.00 秒)

### SPACE

此函数返回由 N 个空格字符组成的字符串：

```
SPACE(N)
RETURNS: string
```

### REPEAT

此函数返回由字符串 str 重复 count 次组成的字符串。如果 count 小于或等于 0，则返回空字符串。如果 str 或 count 为 NULL，则返回 NULL。

```
REPEAT(str, count)
RETURNS: string
```

```
mysql> select repeat('foo', 10);
```

| repeat('foo', 10) |
|-------------------|
| foofoofoofoofoofoofoofoofoofoo |

### REVERSE

此函数返回字符串 str，其中字符顺序被反转：

```
REVERSE(str)
RETURNS: string
```

### INSERT

此函数返回字符串 str，其中从位置 pos 开始的长度为 len 的子字符串被替换为字符串 newstr：

```
INSERT(str, pos, len, newstr)
RETURNS: string
```

```
mysql> select insert('mysqlfunctions', 6, 2, 'FU');
```

| insert('mysqlfunctions', 6, 2, 'FU') |
|--------------------------------------|
| mysqlFUunctions                      |

1 行已在结果集中 (0.44 秒)

### ELT

如果 N 等于 1，此函数返回 str1；如果 N 等于 2，则返回 str2，依此类推。如果 N 小于 1 或大于参数个数，则返回 NULL。ELT() 是 FIELD() 的补足函数。

```
ELT(N,str1,str2,str3,...)
RETURNS: string
```

```
mysql> select elt(2, 'foo', 'bar', 'foobar');
```

| elt(2, 'foo', 'bar', 'foobar') |
|--------------------------------|
| bar                            |

1 行已在结果集中 (0.00 秒)

### FIELD

此函数返回 str 在 str1、str2、str3、... 列表中的索引。如果未找到 str，则返回 0。FIELD() 是 ELT() 的补足函数。

```
FIELD(str,str1,str2,str3,...)
RETURNS: int
```

```
mysql> select field('foobar', 'foo', 'bar', 'foobar');
```

| field('foobar', 'foo', 'bar', 'foobar') |
|-----------------------------------------|
| 3                                       |

1 行已在结果集中 (0.01 秒)

### LCASE

此函数返回字符串 str，其中所有字符根据当前字符集映射更改为小写（默认值为 ISO-8859-1 Latin1）：

```
LCASE(str) or LOWER(str) (used in examples)
RETURNS: string
```

### UCASE

此函数返回字符串 str，其中所有字符根据当前字符集映射更改为大写（默认值为 ISO-8859-1 Latin1）：

```
UCASE(str) or UPPER(str)
RETURNS: string
```

## 日期和时间函数

MySQL 提供了许多用于计算日期的函数。在所有可用的 MySQL 函数中，以下是您可能最常使用的函数。

DATE_FORMAT 函数可让您将日期格式化为 MySQL 时间戳形式。此外，还有几个函数可让您轻松从列中获取特定日期信息。例如，要查找时间戳列中所有条目的星期几，可以使用以下代码：

```
mysql> select dayname(created) from guestbook;
```

| dayname(created) |
|------------------|
| Sunday           |
| Sunday           |
| Wednesday        |
| Sunday           |
| Sunday           |
| Wednesday        |
| Wednesday        |
| Wednesday        |

### DAYOFWEEK

此函数返回日期的星期索引（1 代表星期日，2 代表星期一，依此类推，直到 7 代表星期六）。这些索引值对应于 ODBC 标准。如果向日期函数提供无效日期，则它们返回 null。

```
DAYOFWEEK(date) (used in examples)
RETURNS: int
```

```
mysql> select dayofweek('2001-01-01');
```

| dayofweek('2001-01-01') |
|-------------------------|
| 2                       |

1 行已在结果集中 (0.33 秒)

### WEEKDAY

此函数返回日期的星期索引（0 代表星期一，1 代表星期二，依此类推，直到 6 代表星期日）：

```
WEEKDAY(date) (used in examples)
RETURNS: int
```

### DAYOFMONTH

此函数返回日期的月份中的天数，范围为 1 到 31：

```
DAYOFMONTH(date)
RETURNS: int
```

### DAYOFYEAR

此函数返回日期的年份中的天数，范围为 1 到 366：

```
DAYOFYEAR(date)
RETURNS: int
```

```
mysql> select dayofmonth('02-01-2000');
```

| dayofmonth('02-01-2000') |
|--------------------------|
| 20                       |

1 行已在结果集中 (0.00 秒)

### MONTH

此函数返回日期的月份，范围为 1 到 12：

```
MONTH(date)
RETURNS: int
```

### DAYNAME

此函数返回日期的完整星期名：

```
DAYNAME(date)
RETURNS: string
```

```
mysql> select dayname('10/01/2000');
```

| dayname('10/01/2000') |
|-----------------------|
| Wednesday             |

1 行已在结果集中 (0.00 秒)

### MONTHNAME

此函数返回日期的完整英文月份名：

```
MONTHNAME(date)
RETURNS: string
```

### QUARTER

此函数返回日期的季度，范围为 1 到 4：

```
QUARTER(date)
RETURNS: int
```

要查找当年第二季度在您的留言簿中签名的所有人，可以使用以下命令：

```
select name from guestbook WHERE quarter(created) = 2;
```

### WEEK

只有一个参数时，此函数返回日期的周数，范围为 0 到 53：

```
WEEK(date [, first])
RETURNS: int
```

可选的第二个参数允许您指定周是从星期日还是星期一开始。如果第二个参数为 0，则周从星期日开始；如果为 1，则周从星期一开始。

### YEAR

此函数返回日期的年份，范围为 1000 到 9999：

```
YEAR(date) (used in examples)
RETURNS: int
```

### YEARWEEK

此函数以 YYYYWW 格式返回日期的年份和周数。第二个参数的作用与 WEEK() 中的第二个参数完全相同。

```
YEARWEEK(date [,first])
RETURNS: int
```

### HOUR

此函数返回时间的小时，范围为 0 到 23：

```
HOUR(time)
RETURNS: int
```

### MINUTE

此函数返回时间的分钟，范围为 0 到 59：

```
MINUTE(time)
RETURNS: int
```

### SECOND

此函数返回时间的秒，范围为 0 到 59：

```
SECOND(time)
RETURNS: int
```

### PERIOD_ADD

此函数向周期 P（格式为 YYMM 或 YYYYMM）添加 N 个月，并返回格式为 YYYYMM 的值：

```
PERIOD_ADD(P,N)
RETURNS: int
```

请注意，周期参数 P 不是日期值。

