
## 表 6.1 PHP 文件函数的文件模式

| 模式 | 描述 |
|------|-------------|
| a | 打开文件以追加（写入）数据；如果不存在则创建 |
| a+ | 与模式 a 相同，但额外具有对文件的读取权限 |
| r | 打开文件以读取数据 |
| r+ | 与模式 r 相同，但额外具有写入权限 |
| w | 打开文件以写入数据，擦除其内容；如果不存在则创建 |
| w+ | 与模式 w 相同，但额外具有读取权限 |
| x | 创建文件以写入数据；如果已存在则发送 E_WARNING |
| x+ | 与模式 x 相同，但额外具有读取权限 |

因此修饰符 + 总是为文件模式添加缺少的读取或写入访问权限。还有其他修饰符。自 PHP 4.3.2 起，PHP 在判断文件是文本文件还是二进制文件方面做得非常好，并能适当转换奇怪的字符。如果你要在文件模式后追加 b，你将强制 PHP 以二进制文件方式打开文件；例如，文件模式 rb 以二进制模式打开文件进行读取。

还有一个特殊的修饰符可能对 Windows 用户有用：t。如果将其追加到文件模式，所有 \n 换行符将被转换为 \r\n，正如 Windows 应用程序所期望的那样。

## 打开和关闭文件

fopen() 返回文件句柄，如果打开文件失败则返回 false。然而，你应该使用 @ 字符抑制任何潜在的错误信息，或在 PHP 5 中使用 try-catch 块。

一旦文件不再使用，就应该关闭它。PHP 在脚本终止时会自动关闭所有打开的文件；然而，为了尽可能高效地使用系统资源，应尽早关闭文件以释放内存并加快系统速度。为此，使用 fclose() 并提供文件句柄作为参数。

本段开头的代码同时使用了 fopen() 和 fclose()。

运行脚本后，会创建一个名为 file.txt 的文件。

> **注意**
> 
> 为了使本章（以及本章中的其他示例）正常工作，你必须确保 PHP 脚本具有访问文件的适当权限。通常，Apache 在特殊用户 ID 0（UNIX/Linux）下运行，或在普通用户账户（Windows）下运行。使用 chmod 相应地设置访问权限。
> 
> Microsoft IIS（Internet Information Services）在名为 IUSR_<name of machine> 的特殊访客账户下运行 PHP 脚本。你可以使用图 6.1 所示的图形用户界面来调整文件或目录的访问设置。

### 提示

为了避免在尝试访问不存在的文件时出现任何错误，你可以使用 file_exists() 函数，该函数会返回给定文件名是否存在。

```
if (file_exists('file.txt')) {
  // ...
}
```

![](img/1e6d362f187af50011d2666ddaa68739_178_0.png)

图 6.1 允许 IIS 用户访问文件或目录。

## 从文件读取

```
echo file_get_contents('file.txt');
```

要从文件读取数据，PHP 提供了几种可能性。最简单的方法可能是将数据一次性全部读入然后输出给用户。

自 PHP 4.3.0 起可用的 file_get_contents() 函数以字符串形式返回文件（或流）的内容，以便进一步处理。前面的代码读取名为 file.txt 的文件并打印其内容。该函数是二进制安全的，因此不需要（或不能）使用文件模式。

file() 函数的工作方式与 file_get_contents() 相同，但以数组形式返回文件内容：每个元素是文件中的一行（包括换行符）。以下代码将此数组转换为字符串并发送到浏览器。implode() 函数将数组元素粘合在一起（参见第 2 章“使用数组”）。

```
<?php
    echo implode('', file('file.txt'));
?>
```

更简短的方法是使用 readfile()，它会直接将文件内容发送到浏览器。为了在发送前处理数据，必须使用输出缓冲。以下列表将特殊超文本标记语言（HTML）字符转换并在换行处使用 <br> 元素，以便在浏览器中显示文件的原始内容。

```php
<?php
ob_start();
readfile('text.txt');
$data = ob_get_contents();
ob_end_flush();
echo nl2br(htmlspecialchars($data));
?>
```

*使用输出缓冲将文件内容发送到浏览器（readfile.php）*

为了获得最大灵活性，可以使用手动方式；然而，对于文本文件，这通常不是必需的。使用 fopen() 打开文件，然后只要返回数据就调用 fgets()（这里使用 while 循环很方便）并输出数据。fgets() 返回其第二个参数提供的字符数，但最多为当前行末尾的所有字符。

```php
<?php
$fp = fopen('file.txt', 'r');
while (!feof($fp)) {
    $line = fgets($fp, 4096);
    echo $line;
}
fclose($fp);
?>
```

*逐行将文件内容发送到浏览器（readfile-linebyline.php）*

## 写入文件

```php
file_put_contents('file.txt',
    "-> This text file contains\nsome random text.
<-");
```

写入文件与从文件中读取一样简单——如果你使用的是 PHP 5 或更高版本。然后，file_put_contents() 函数直接将数据写入文件，并且是二进制安全的。调用函数后，文件将被关闭。代码将数据写入文件。

```
<?php
    file_put_contents('file.txt',
        "-> This text file contains\nsome random text.
        <-");
    echo 'File written.';
?>
```

将数据写入文件（file_put_contents.php）

然而，前面的代码会覆盖现有文件。如果你想追加数据（因此模拟文件模式 a），你首先必须读取文件的数据。

```
<?php
    function file_append_contents($filename, $data) {
        $olddata = @file_get_contents($filename);
        return file_put_contents($filename, 
            "$olddata$data");
    }

    file_append_contents('file.txt',
        "\n-> This text file contains\neven more random text. <-");
    echo 'Data appended to file';
?>
```

向文件追加数据（file_append_contents.php）

### 提示

提供第三个参数给 file_put_contents() 以追加数据而不是覆盖文件甚至更简单：

```
file_put_contents($filename, $data, FILE_APPEND);
```

然而，当使用低于 5.0.0 的 PHP 版本时，所有这些都会失败，因为 file_put_contents() 函数在早期版本中不存在。然而，可以为旧版 PHP 模拟 file_put_contents() 的行为。这与使用 fopen()、fgets() 和 fclose() 从文件读取的方式类似。对于写入，只需要一个额外的函数：fwrite() 将数据写入文件句柄。以下代码实现了这种方法。使用 function_exists()，你可以检查 file_put_contents() 函数是否已存在。如果不存在，你可以编写它。

```
<?php
if (!function_exists('file_put_contents')) {
    function file_put_contents($filename, $content)
    {
        if ($fp = @fopen($filename, 'w')) {
            $result = fwrite($fp, $content);
            fclose($fp);
            return $result;
        } else {
            return false;
        }
    }
}
```

```
file_put_contents('file.txt',
    "\n-> This text file contains\nsome random text. <-" );
echo 'Data written to file.';
?>
```

*使用 file_put_contents() 兼容所有相关 PHP 版本（file_put_contents_compatible.php）*

## 锁定文件

```
flock($fp, LOCK_UN);
```

在读取和写入文件时，你必须考虑并发。如果两个进程同时尝试访问文件怎么办？为了避免一个进程写入而另一个进程读取时出现问题，你必须锁定文件。这是通过 PHP 函数 flock() 完成的。

```
<?php
    if (!function_exists('file_put_contents')) {
        function file_put_contents($filename, $content)
        {
            if ($fp = @fopen($filename, 'w') && flock($fp, LOCK_EX)) {
                $result = fwrite($fp, $content);
                flock($fp, LOCK_UN);
                fclose($fp);
                return $result;
            } else {
                return false;
            }
        }
    }
?>
```
