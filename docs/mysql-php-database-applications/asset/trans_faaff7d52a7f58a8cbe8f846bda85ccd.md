

| 指标 | 含义 |
| :--- | :--- |
| l (lowercase l) | 星期几，文本形式，全称；例如，Friday |
| L | 是否为闰年的布尔值；0 或 1 |
| m | 月份；01 到 12 |
| M | 月份，文本形式，三个字母；例如，Jan |
| n | 月份，不带前导零；1 到 12 |
| s | 秒；00 到 59 |
| S | 英语序数词后缀，文本形式，两个字符；例如，th、nd |
| t | 指定月份的天数；28 到 31 |
| T | 本机的时区设置；例如，MDT |
| U | 自纪元（1970 年 1 月 1 日午夜）以来的秒数 |
| w | 星期几，数字形式；0（星期日）到 6（星期六） |
| Y | 年份，四位数字；例如，1999 |
| y | 年份，两位数字；例如，99 |
| z | 一年中的第几天；0 到 365 |
| Z | 时区偏移量（秒）；-43200 到 43200 |

例如，如果你想以“June 5, 2003 4:22 pm”的格式打印日期，这行代码就能搞定：

```
echo date("F d, Y g:i a");
```

MKTIME() 该函数最适合用于计算有效日期。

```
int mktime (int hour, int minute, int second, int month, int day,
int year [, int is_dst])
```

例如，假设你有一个表单用于收集日期——可能是当前月、日和年。你想计算并设置一个截止日期，正好是从提交日期起 30 天后。

```
$year = 2003;
$month = 5;
$day = 24;
echo date("l F d, Y", mktime(0,0,0,$month,$day+30, $year) );
```

这将输出 2000 年 5 月 24 日后的 30 天，并打印出 2000 年 6 月 23 日星期五。

请记住，此函数允许你对日期进行加减运算，而无需担心 PHP 会返回虚假结果。在前面的示例中，你可以从月份值 5 中减去 6，PHP 将返回一个有意义的日期。你可以添加或减去任意数量的年、月或日，而无需担心 PHP 会返回错误结果。例如，以下是获取 1999 年最后一天日期信息的完全可接受的方法：

```
$year = 2000;
$month = 1;
$day = 1;
echo date("l F d, Y", mktime(0,0,0,$month,$day-1, $year) );
```

这段代码会告知你，1999 年 12 月 31 日是星期五。

请注意，上述代码首先计算 mktime() 指示日期的时间戳，然后使用 date 函数将其打印出来。

如果从右侧省略参数，则这些参数将从当前时间戳中获取。因此，要打印五小时后的日期和时间，可以使用以下代码：

```
echo date("l F d, Y g:i a", mktime( date('H')+5 ) );
```

请注意此处的函数嵌套。从最内层函数开始，date('H') 返回当前小时（24 小时格式）。然后加上 5，计算五小时后的时间戳。接着使用指定字符串对时间戳进行格式化。

TIME() 该函数以自 Unix 纪元以来的秒数返回当前时间。Unix 纪元是 Unix 术语中的时间起点，即时间戳为 0 的时刻。它被任意定义为 1970 年 1 月 1 日 00:00:00 GMT。

```
int time(void);
```

MICROTIME() 该函数返回字符串 "msec sec"，其中 sec 是自 Unix 纪元（1970 年 1 月 1 日 00:00:00 GMT）以来的秒数，msec 是微秒部分。

```
string microtime(void);
```

此函数仅在支持 gettimeofday() 系统调用的操作系统上可用。

返回的字符串类似于 0.12082400 969034581。你可以相当肯定，此函数永远不会返回两次相同的数字。它常用于为随机数生成器播种。

## 本书未使用的日期/时间函数

其他一些时间/日期函数可能对你有用。其中包括几个用于打印当前日期和时间的函数。如果你需要了解此处未讨论的特定内容，请参阅手册：http://www.php.net/manual/ref.datetime.html。

## 文件系统函数

PHP 提供了一整套函数，使你能够操作宿主计算机上的文件和目录。在编写本书的应用程序过程中，我们只遇到一次需要向文件系统写入或从中读取文件的情况：在目录和购物车应用程序中，当我们需要为用户提供存储已上传图像的功能时。但是，如果你经常使用 PHP，毫无疑问你需要熟悉这些函数。作为介绍，我们可以说，PHP 的目录和文件系统函数非常出色。PHP 开发人员出色地完成了工作，使得在本地系统或互联网上的其他地方处理文件变得轻而易举。举个快速的例子，编写以下脚本大约花了两分钟，它将从一个出于法律原因不予说明的网站抓取股票报价。

```php
$farray = file("http://domain.com/stockquote?symbols=ORCL", "r");
foreach ($farray as $value)
{
    if (ereg("last:.*$", $value) )
    {
        $value = strip_tags($value);
        break;
    }
}
```

这段简短的脚本会抓取整个页面，并将每一行分配给 $farray 中的一个元素。然后我们遍历数组，查找字符串 "last"。在我们测试的网站上，单词 "last" 表示最近的报价。我们所要做的就是剥离 HTML 标签，就得到了所需的所有信息。如果我们愿意，还可以进行更多的字符串处理，以我们喜欢的方式格式化信息。

## 本书使用的文件系统函数

如果你想查看这些函数的用法，请参阅第 12 章和第 14 章。

### FOPEN()

该函数为第一个参数中指示的文件或 URL 打开一个文件指针。（该指针非常类似于 mysql_connect() 返回的结果标识符。）

```
int fopen (string filename, string mode [, int use_include_path])
```

mode 参数决定你可以对文件执行的操作。表 6-2 显示了可用的模式。

| 模式 | 含义 |
| :--- | :--- |
| r | 仅打开以供读取；将文件指针放置在文件开头。 |
| r+ | 打开以供读写；将文件指针放置在文件开头。 |
| w | 仅打开以供写入；将文件指针放置在文件开头并将文件截断为零长度。如果文件不存在，则尝试创建它。 |
| w+ | 打开以供读写；将文件指针放置在文件开头并将文件截断为零长度。如果文件不存在，则尝试创建它。 |
| a | 仅打开以供写入；将文件指针放置在文件末尾。如果文件不存在，则尝试创建它。 |
| a+ | 打开以供读写；将文件指针放置在文件末尾。如果文件不存在，则尝试创建它。 |

请注意，此函数返回一个资源标识符。如果你希望从文件读取或写入文件，需要执行类似以下操作：

```
//open a file and read contents into a variable
$filename="test99.txt";
$fp = fopen($filename, "r+") or
    die("could not open $filename");
$contents = fread ($fp, filesize($filename));
//replace all occurences of Jayson
$new_contents = str_replace("Jayson", "Jay", $contents);
//write out new file contents.
```

```
rewind($fp);
fwrite($fp, $new_contents);
//ftruncate assures there won't be extra
//characters if the resulting file is shorter
//than the original.
ftruncate($fp, ftell($fp));
fclose($fp);
```

### FCLOSE()

该函数关闭文件指针。

```
int fclose (int fp)
```

在处理完文件后，使用它是一种良好的编程习惯。如果不使用，PHP 会为你完成，就像 mysql_close() 一样。

### FWRITE()

```
int fwrite (int fp, string string [, int length])
```

fwrite() 将字符串参数的值写入文件指针指示的文件。如果遇到错误，该函数返回 -1；否则返回成功写入的字节数。

### FREAD()

```
string fread (int fp, int length)
```

fread() 读取第一个参数给出的文件指针的第二个参数给出的字节数，或直到文件末尾，以先到者为准。

### FEOF()

该函数测试文件指针是否已到达文件末尾。

```
bool feof (int fp)
```

有关 feof() 的示例，请参见 fgets() 函数。

### FGETS()

该函数返回文件指针指示的文件中的一行（通常来自 fopen()）。如果你正在处理大文件，一次将文件加载到内存一行一行地，而不是像 fread() 那样一次性读取大块，对系统更友好。

```
string fgets (int fp, int length)
```

