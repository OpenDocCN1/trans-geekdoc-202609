

# 156 第二部分：解决方案

HTTP 头部将在 II.10 节中进行详细讨论。

开发一个用于存储文本和图形文件的脚本的问题可以通过 HTTP 头部解决，如列表 II.3.7 所示。

## 列表 II.3.7. 用于保存文本和图形文件的脚本

脚本通过 GET 参数接收文件名，例如 `index.php?down=file.txt`。要保存的文件名由 `filename` 属性决定，并通过第一个 HTTP 头部指定。在脚本中，`filename` 参数与文件名相同，但可以使用任何名称。第二个 HTTP 头部告诉浏览器该文件是二进制文件，不应被解释。第三行使用 `file_get_contents()` 函数提取通过 `$_GET['down']` 参数发送的文件内容并在浏览器窗口中显示它们。

重要的一点是，在输出文件内容后，不要通过 `echo` 语句或直接输出向流输出任何其他内容；否则所有内容都将追加到文件中。这包括关闭 `?>` 标签后可能存在的空格和换行符。

## II.3.6. 确定文件大小

可以使用 `filesize()` 函数确定文件大小，该函数接受文件名作为参数，并根据文件的大小返回字节、千字节或兆字节的大小。可以通过如列表 II.3.8 所示的脚本确定大小。

## 第 II.3 节：文件操作 157

## 列表 II.3.8. 确定文件大小的函数

```php
<?php
echo filesize($_GET['name']);
// 一个确定文件大小的函数
function getfilesize($filename)
{
    // 检查文件是否存在
    if(!file_exists($filename)) return "No such file";
    // 确定文件的大小
    $filesize = filesize($filename);
    // 如果文件大于 1024 字节，
    // 计算千字节大小
    if($filesize > 1024)
    {
        $filesize = (float) ($filesize/1024);
        // 如果文件大于 1024 KB，
        // 计算兆字节大小
        if($filesize > 1024)
        {
            $filesize = (float) ($filesize/1024);
            // 保留第一位小数
            $filesize = round($filesize, 1);
            return $filesize." MB";
        }
        else
        {
            // 保留第一位小数
            $filesize = round($filesize, 1);
            return $filesize." KB";
        }
    }
    else
    {
        return $filesize." byte";
    }
}?>
```

脚本获取文件名作为参数，首先检查 `filesize()` 函数返回的文件大小是否大于 1 KB，然后检查它是否大于 1 MB。在每情况下，都会返回相应单位下的文件大小。

## II.3.7. 确定文件中的行数

计算行的最简单解决方案是使用 `file()` 函数。该函数接受文件名作为参数并返回一个数组，数组中的每个元素包含文件的一行。剩余的任务是计算返回数组中的元素数量。解决该问题的脚本如列表 II.3.9 所示。

## 列表 II.3.9. 确定文件的行数

```php
<?php
echo getlinecount($_GET['name']);

function getlinecount($filename)
{
    // 检查文件是否存在
    if(!$file_exists($filename)) return "No such file!";
    // 使用 file() 函数将文件
    // 分成单独的行
    $filearr = file($filename);
    // 计算并返回文件的行数
    return count($filearr);
}
?>
```

## II.3.8. 反转文件中的行顺序

与上一个示例一样，行顺序问题可以使用 `file()` 函数将文件拆分为单独的行来解决。可以使用 `array_reverse()` 函数反转获取数组中的行顺序。最后，使用 `implode()` 函数将数组转换为字符串，然后写入文件（列表 II.3.10）。

## 第 II.3 节：文件操作 159

## 列表 II.3.10. 反转文件的行顺序

```php
<?php
// 使用 file() 函数将文件
// 分成单独的行
$Arr = file("text.txt");
// 反转数组顺序
$Arr = array_reverse($Arr);
// 将数组转换为字符串并
// 重写 text.txt 文件的内容
$fd = fopen("text.txt", "w");
if ($fd) {
    fwrite($fd, implode("", $Arr));
    fclose($fd);
}
?>
```

## II.3.9. 列出文件和子目录

遍历目录及其子目录的最佳方法是递归进入目录树。可以使用 `scan_dir()` 脚本（列表 II.3.11）完成，它可以提取当前目录的内容并显示文件和子目录的名称。如果函数遇到子目录，将递归地调用自身并将子目录作为参数传递。

列出文件和子目录。

## 列表 II.3.11. 列出文件和子目录

```php
<?php
///////////////////////////////////////
// 一个进入目录树的递归函数
///////////////////////////////////////
function scan_dir($dirname)
{
    // 打开当前目录
    $dir = opendir($dirname);
```

第二部分：解决方案

$dirname = ".";
// 调用递归处理根目录
// 子目录的函数
scan_dir($dirname);

在遍历目录时，必须排除 .（当前目录）和 ..（父目录）以防止死循环。

## II.3.10. 统计文件

统计文件的问题也使用递归下降技术解决（列表 II.3.12）。然而，只有当当前项是目录时才会显示信息。目录中的文件使用 `filesize()` 函数计数。

第 II.3 节：文件操作

## 列表 II.3.12. 统计目录中的文件

```php
<?php
////////////////////////////////////////////////
// 一个进入目录树的递归函数
////////////////////////////////////////////////
function scan_dir($dirname)
{
    // 打开当前目录
    $dir = opendir($dirname);
    // 循环读取当前目录
    while (($file = readdir($dir)) != false)
    {
        // 检查变量 $file 是否等于
        // 当前或上级目录
        if($file != "." && $file != "..")
        {
            // 如果当前项是目录，
            // 调用 scan_dir() 函数
            if(is_dir($dirname."/"$file))
            {
                echo $dirname."/"$file." - ";
                file_count($dirname."/"$file)."<br>";
                scan_dir($dirname."/"$file);
            }
        }
    }
    // 关闭目录
    closedir($dir);
}
////////////////////////////////////////////////
// 一个统计目录中文件的函数
////////////////////////////////////////////////
function file_count($dirname)
{
    // 计数器变量
    $count = 0;
    // 打开当前目录
    $dir = opendir($dirname);
    // 循环读取目录内容
    while($file = readdir($dir))
    {
      // 如果当前项是文件，则计数
      if(is_file($dirname."/"$file)) ++$count;
    }
    // 关闭目录
    closedir($dir);
    return $count;
}
```

162 第二部分：解决方案

## II.3.11. 统计项目文件的行数

项目文件的行数通过递归遍历项目目录，并统计扩展名与 `$extensions` 数组中指定的扩展匹配的文件行数（列表 II.3.13）。该数组被声明为全局变量，因此你不需要通过 `scan_dir()` 递归函数的参数传递它的引用。此外，还声明了存储当前行数的 `$count` 变量。

## 列表 II.3.13. 统计项目文件的行数

```php
<?php
///////////////////////////////////////
// 一个进入目录树的递归函数
///////////////////////////////////////
function scan_dir($dirname)
{
  // 声明全局替换变量
  GLOBAL $extensions, $count;
```

