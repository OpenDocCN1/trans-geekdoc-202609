
## 表 6-2 FOPEN() 函数的模式

| 模式 | 含义 |
|------|---------|
| r | 仅用于只读打开；将文件指针置于文件开头。 |
| r+ | 用于读写打开；将文件指针置于文件开头。 |
| w | 仅用于写打开；将文件指针置于文件开头并将文件截断为零长度。如果文件不存在，尝试创建它。 |
| w+ | 用于读写打开；将文件指针置于文件开头并将文件截断为零长度。如果文件不存在，尝试创建它。 |
| a | 仅用于写打开；将文件指针置于文件末尾。如果文件不存在，尝试创建它。 |
| a+ | 用于读写打开；将文件指针置于文件末尾。如果文件不存在，尝试创建它。 |

请注意此函数返回一个资源标识符。如果您想从文件读取或写入文件，您需要做类似这样的操作：

//open a file and read contents into a variable
$filename="test99.txt";
$fp = fopen($filename, "r+") or
die("could not open file");
$contents = fread ($fp, filesize($filename));
//replace all occurrences of Jayson
$new_contents = str_replace("Jayson", "Jay", $contents);
//write out new file contents.
rewind($fp);
fwrite($fp, $new_contents);
//ftruncate assures there wont be extra
//characters if the resulting file is shorter
//than the original.
ftruncate($fp,ftell($fp));
fclose($fp);

### FCLOSE() 此函数关闭文件指针。

```
int fclose (int fp)
```

确保在完成文件使用后使用它。如果不使用，PHP 会为您处理，就像 `mysql_close()` 一样。

### FEOF()

此函数测试文件指针是否已到达文件末尾。

```
int feof (int fp)
```

请参阅 `fgets()` 函数以了解 `feof()` 的示例。

### FGETS()

此函数从文件指针指示的文件（通常取自 `fopen`）返回单行。

```
string fgets (int fp, int length)
```

如果您正在处理大文件，逐行将文件加载到内存中对系统来说更容易，而不是像使用 `fread()` 那样一次性加载大块数据。此函数会读取一行直到换行符。 optionally，您可以在第二个参数中指定一行内要读取的最大字节数。第二个参数传统上使用 2048，因为在许多文件系统中那是最大行长度。如今，使用更大的值是安全的。您不应该将此函数用于二进制文件。

```
$fp = fopen("/path/to/file","r");
while ($fp && !feof($fp))
{
    print fgets($fp,2048);
}
fclose($fp);
```

### FILE()

此函数逐行读取文件，每行成为数组中的一个元素。

```
array file (string filename [, int use_include_path])
```

### UMASK()

此函数设置 umask 值（如果您不知道这是什么，请参阅您的 Unix 手册页）。

```
int umask (int mask)
```

umask() 将 PHP 的 umask 设置为 mask & 0777 并返回旧的 umask。

### COPY()

此函数复制第一个参数中的文件并将其复制到第二个参数的位置。

```
int copy (string source, string dest)
```

如果复制成功，函数返回 True。如果不成功，返回 False。此函数在第 10 章中使用。

### TEMPNAM()

这会在第一个参数指示的目录中创建一个唯一的文件名。

```
string tempnam (string dir, string prefix)
```

第二个参数中的字符串前缀将被放在每个文件名之前。这可以帮助您跟踪哪些文件属于哪些脚本。

![](img/de0823012275cf4ceebdb822a56e6b71_189_0.png)

> 在 Windows 上，此函数的行为可能有点不可预测。

### DIRNAME()

此函数将返回所提供字符串的目录名。

```
string dirname (string path)
```

例如：

```
echo dirname("/www/htdocs/testwrite.txt");
```

将返回 /www/htdocs。

## 本书未使用的文件系统函数

这是一个重要主题，您应该花一些时间学习。大多数更受欢迎的文件系统命令都可以通过 PHP 使用，并且有许多用于打开、读取、写入和显示文件的命令。但是，由于本书涉及关系数据库用于数据存储，我们在这里不会介绍它们。

## 随机数生成器函数

时不时地您需要随机选择一些东西。它可能是一个单独的元素，也可能与使用 shuffle() 随机化数组或使用 array_rand() 从数组中获取随机元素有关。在任何情况下，您都需要使用 PHP 的随机数生成器函数。

请注意，随机数生成器在使用前需要播种。也就是说，它必须一开始就被赋予一个相当独特的数量。为此，正如您将看到的，microtime() 函数将非常有用。

请记住，实际上有两组随机数生成器。有标准的 rand() 和 srand()，您需要它们来为 shuffle() 和 array_rand() 播种生成器。但是，如果您只是想获取一个随机数而不与其他函数一起使用，请使用下面描述的 mt 函数——它们更快更随机

## 本书使用的随机数生成器函数

现在我们将检查一些在本书记述的应用中未使用的重要的随机数生成器函数。

### MT_SRAND()

此函数为您的随机数生成器播种。

```
void mt_srand (int seed)
```

使用以下行，您可以确保您的数字足够随机：

```
mt_srand ((double) microtime() * 1000000);
```

仅在每个脚本中播种一次随机数生成器。

### MT_RAND()

此函数返回一个随机数。您可以指定最小值和/或最大值。

```
int mt_rand ([int min [, int max]])
```

因此，要获取 1 到 100 之间的随机数，请执行以下操作：

```
mt_srand((double)microtime() * 1000000);
$number = mt_rand(1,100);
echo $number;
```

## cURL 函数

这些在第 14 章中有详细说明。cURL 是一个允许服务器使用各种协议进行通信的库。就本书中的应用程序而言，cURL 最有用的地方在于它能够与 HTTPS 通信。这是一种安全协议，用于购物车进行信用卡交易。

## 会话函数

这些在第 14 章中有详细说明。会话是维护页面之间状态的手段。请记住，HTTP，即 Web 的语言，不允许服务器在特定用户的页面请求之间记住太多东西。会话允许服务器跟踪单个用户的活动。

## HTTP 头函数

有两个至关重要的 HTTP 头函数，您都需要了解。

### HEADER()

如果您将与浏览器或其他 HTTP 服务器通信，这是要使用的函数。

```
int header (string string)
```

本质上，您可以发送 RFC 2616 (ftp://ftp.isi.edu/in-notes/rfc2616.txt) 下预期的任何头。RFC 本身就很庞大（也许是您今年会做的最枯燥的阅读）。以下是您可能会发送的常见头。

```
header("Location:http://www.php.net");
```

这不过是一个重定向：它将浏览器发送到您指定的页面。如果您一直在使用纯 HTML 和 <META type=refresh> 标签或 JavaScript 来执行重定向，您应尽可能切换到这种类型的头。它适用于所有浏览器，重定向对用户来说是完全透明的。

![](img/de0823012275cf4ceebdb822a56e6b71_191_0.png)

IMPORTANT：不，说得更重要一点。您不能在任何内容 — 任何内容 — 发送到浏览器后发送头。如果您在硬回车后发送头，将会出错。如果在打开的 <?php 标签之前有硬回车，您将收到错误。如果在包含文件中有硬回车且该文件在您的 header() 函数之前，您将收到错误。这不应该是您经常遇到的问题；您的页面应设计为在显示之前处理大部分逻辑。但是，如果您遇到无法解决的情况，请查看输出缓冲函数。

### SETCOOKIE()

这基本上是一个专门的头函数，因为 cookie 只不过是由特定的 HTTP 头设置的。

```
int setcookie (string name [, string value [, int expire [, string path [, string domain [, int secure]]]]])
```

第一个参数将是 cookie 的名称。第二个将是值。过期值应使用 time 函数设置。以下是 setcookie() 的一个相当典型的用法：

```
setcookie("id",$id_val,time()+(24*60*60),"/",".domain.com",0);
```
