

### RIGHT(str, len)

返回 str 最右侧的 len 个字符。如果 str 短于 len 个字符，则直接返回 str，不会额外填充。

### SUBSTRING(str, pos, len)
SUBSTRING(str FROM pos FOR len)
MID(str, pos, len)

从 str 的位置 pos 开始（1 表示第一个字符），返回长度最多为 len 个字符的字符串。SUBSTRING 的第二种形式是 ANSI 标准。

### SUBSTRING(str, pos)
SUBSTRING(str FROM pos)

返回从 str 的位置 pos 开始（1 表示第一个字符）一直到 str 结尾的字符串。

### SUBSTRING_INDEX(str, delim, count)

MySQL 会在 str 中数出 count 次 delim 出现的次数，然后从该位置开始截取子字符串。如果 count 为正，MySQL 从字符串开头向右计数，然后截取到（但不包含）该最后一个分隔符的子字符串。如果 count 为负，MySQL 从字符串末尾向左计数，然后截取从该最后一个分隔符之后开始、一直到 str 结尾的子字符串。

### LTRIM(str)

返回去除 str 前导空白字符后的结果。

### RTRIM(str)

返回去除 str 尾部空白字符后的结果。

### TRIM([[BOTH | LEADING | TRAILING] [remstr] FROM] str)

返回 str，其中从字符串开头（LEADING）、结尾（TRAILING）或两端（BOTH，默认）删除了空白字符（默认）或字符串 remstr 的所有出现项。

### SOUNDEX(str)

生成一个表示 str 大声读出来时的发音的字符串。发音相似的单词应具有相同的 'soundex 字符串'。

```
E.g.:
SOUNDEX("tire") = "T600"
SOUNDEX("tyre") = "T600"
SOUNDEX("terror") = "T600"
SOUNDEX("tyrannosaur") = "T6526"
```

### SPACE(num)

返回由 num 个空格字符组成的字符串。

### REPLACE(str, from_str, to_str)

返回将 str 中所有 from_str 出现项替换为 to_str 后的结果。

### REPEAT(str, count)

返回由 str 重复 count 次组成的字符串；如果 count <= 0，返回空字符串；如果任一参数为 NULL，返回 NULL。

### REVERSE(str)

返回 str 的逆序拼写。

### INSERT(str, pos, len, newstr)

获取 str，删除从位置 pos（字符串中 1 表示第一个字符）开始、长度为 len 的子字符串，然后在该位置插入 newstr。如果 len = 0，则直接在位置 pos 插入 newstr。

### ELT(N, str1, str2, str3, ...)

返回第 N 个字符串参数（N=1 时为 str1，N=2 时为 str2，以此类推）；如果给定 N 没有对应参数，则返回 NULL。

### FIELD(str, str1, str2, str3, ...)

返回 str 在随后的参数列表中的位置（str = str1 时为 1，str = str2 时为 2，以此类推）。

### FIND_IN_SET(str, strlist)

当 strlist 为 "string1,string2,string3,..." 形式的字符串列表时，此函数返回 str 在该列表中的索引；如果 str 不在列表中，则返回 0。此函数非常适合（且已针对其优化）用于确定 str 是否在类型为 SET 的列中被选中（参见第 218 页）。

### MAKE_SET(bits, str1, str2, ...)

使用与数值 bits 中设置的位对应的字符串参数（str1、str2 等），返回 "string1,string2,string3,..." 形式的字符串列表。例如，如果 bits = 10（二进制 1010），则位 2（2）和 4（8）被设置，因此 MAKE_SET 的输出将为 "str2,str4"。

### EXPORT_SET(bits, on_str, off_str, [separator, [number_of_bits]])

返回一个字符串表示，指示 bits 中哪些位被设置，哪些位未被设置。已设置的位由 on_str 字符串表示，未设置的位由 off_str 字符串表示。默认情况下，这些位表示以逗号分隔，但可选的 separator 字符串允许您自定义分隔符。默认情况下，最多读取 64 位；不过，number_of_bits 允许您指定读取较少的位数。

E.g.:

```
EXPORT_SET(10,'Y','N','',',',6) = "N,Y,N,Y,N,N"
```

### LCASE(str)
LOWER(str)

返回所有字母均为小写的 str。

### UCASE(str)
UPPER(str)

返回所有字母均为大写的 str。

### LOAD_FILE(filename)

返回 filename 指定的文件（MySQL 可读取的文件的绝对路径）的内容。您的 MySQL 用户还应具有文件权限。

## 日期和时间函数

### DAYOFWEEK(date)

根据 ODBC 标准，返回 date 的星期几，形式为整数（1 = 星期日，2 = 星期一，3 = 星期二，... 7 = 星期六）。

### WEEKDAY(date)

返回 date 的星期几，形式为整数（0 = 星期一，1 = 星期二，2 = 星期三，... 6 = 星期日）。

### DAYOFMONTH(date)

返回 date 的一个月中的第几天（从 1 到 31）。

### DAYOFYEAR(date)

返回 date 的一年中的第几天（从 1 到 366 - 别忘了闰年！）。

### MONTH(date)

返回 date 的月份（从 1，一月，到 12，十二月）。

### DAYNAME(date)

返回 date 的星期名称（例如 "Tuesday"）。

### MONTHNAME(date)

返回 date 的月份名称（例如 "April"）。

### QUARTER(date)

返回 date 所在的年份季度。
E.g.:
QUARTER("2001-04-12") = 2

### WEEK(date)
WEEK(date, first)

返回 date 所在的一年中的第几周（从 1 到 53），默认假设一周的第一天是星期日（如果未指定 first 或 first 为 0），或星期一（如果 first 为 1）。

### YEAR(date)

返回 date 的年份（从 1000 到 9999）。

### YEARWEEK(date)
YEARWEEK(date, first)

以 YYYYWW 形式返回 date 的年份和周数。请注意，一年的第一天或最后一两天通常可能分别属于前一年或后一年的一周。
E.g.:
YEARWEEK("2001-12-31") = 200201

### HOUR(time)

返回 time 的小时（从 0 到 23）。

### MINUTE(time)

返回 time 的分钟（从 0 到 59）。

### SECOND(time)

返回 time 的秒（从 0 到 59）。

### PERIOD_ADD(period, num_months)

向 period（格式为 YYMM 或 YYYYMM）添加 num_months 个月，并以 YYYYMM 形式返回结果。

### PERIOD_DIFF(period1, period2)

返回 period1 和 period2（均应指定为 YYMM 或 YYYYMM）之间的月份数。

### DATE_ADD(date, INTERVAL expr time)
DATE_SUB(date, INTERVAL expr time)
ADDDATE(date, INTERVAL expr time)
SUBDATE(date, INTERVAL expr time)

返回将指定的时间间隔添加到 date（DATE 或 DATETIME 值）中或从中减去的结果。
DATE_ADD 与 ADDDATE 相同，DATE_SUB 与 SUBDATE 相同。expr 指定要添加或减去的间隔，如果要指定负间隔，则可以为负值；time 指定 expr 的格式，如表 2 所示。

如果 date 和 expr 仅涉及日期值，则结果将为 DATE 值；否则，此函数将返回 DATETIME 值。

### 表 2 -- 日期加法/减法函数的间隔类型

| 类型 | expr 的格式 |
| --- | --- |
| SECOND | 秒 |
| MINUTE | 分钟 |
| HOUR | 小时 |
| DAY | 天 |
| MONTH | 月 |
| YEAR | 年 |
| MINUTE_SECOND | "minutes:seconds" |
| HOUR_MINUTE | "hours:minutes" |
| DAY_HOUR | "days hours" |
| YEAR_MONTH | "years-months" |
| HOUR_SECOND | "hours:minutes:seconds" |
| DAY_MINUTE | "days hours:minutes" |
| DAY_SECOND | "days hours:minutes:seconds" |

### TO_DAYS(date)

将 date 转换为自公元元年以来的天数。这允许您计算日期差（即 TO_DAYS(date1) - TO_DAYS(date2) = 天数差）。

### FROM_DAYS(days)

给定自公元元年以来的天数（由 TO_DAYS 生成），返回一个日期。

### DATE_FORMAT(date, format)

获取日期或时间值 date，并根据格式字符串 format 对其进行格式化，该字符串可包含表 3 中显示的任何符号作为占位符。

### 表 3 - DATE_FORMAT() 符号（示例：2001-01-01 01:00:00）

| 符号 | 显示内容 | 示例 |
| --- | --- | --- |
| %M | 月份名称 | January |
| %W | 星期名称 | Monday |
| %D | 带英文后缀的日期 | 1st |
| %Y | 年份，数字，4 位 | 2001 |
| %y | 年份，数字，2 位 | 01 |
| %X | 周的年份（周日为一周的第一天），4 位（与 %V 连用） | 2001 |
| %x | 类似 %X，周一为一周的第一天（%v） | 2001 |
| %a | 缩写的星期名称 | Mon |
| %d | 一个月中的日期 | 01 |
| %e | 一个月中的日期 | 1 |
| %m | 一年中的月份，数字 | 01 |
| %c | 一年中的月份，数字 | 1 |
| %b | 缩写的月份名称 | Jan |
| %j | 一年中的天数 | 001 |
| %H | 一天中的小时（24 小时制，00-23） | 01 |
| %k | 一天中的小时（24 小时制，0-23） | 1 |
| %h | 一天中的小时（12 小时制，01-12） | 01 |
| %I | 一天中的小时（12 小时制，01-12） | 01 |
| %l | 一天中的小时（12 小时制，1-12） | 1 |
| %i | 分钟 | 00 |
| %r | 时间，12 小时制（hh:mm:ss AM/PM） | 01:00:00 AM |
| %T | 时间，24 小时制（hh:mm:ss） | 01:00:00 |
| %S | 秒 | 00 |
| %s | 秒 | 00 |
| %p | AM 或 PM | AM |
| %w | 一周中的天数，数字（0=星期日） | 1 |
| %U | 周（00-53），周日为一周的第一天 | 01 |
| %u | 周（00-53），周一为一周的第一天 | 01 |
| %V | 周（1-53），周日为一周的第一天（%X） | 01 |
| %v | 周（1-53），周一为一周的第一天（%x） | 01 |
| %% | 实际的百分号 | % |

