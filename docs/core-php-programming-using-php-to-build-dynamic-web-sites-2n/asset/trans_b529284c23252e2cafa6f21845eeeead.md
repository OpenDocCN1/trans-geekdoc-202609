
核心 PHP 编程

```php
if(chmod("data.txt", 0666))
{
    print("mode change successful");
} else {
    print("mode change unsuccessful");
}
```

# boolean chown(string filename, string user)

chown 函数用于更改指定文件的所有者。如果成功，则返回 TRUE。否则，函数返回 FALSE。在 Windows 下，此函数不执行任何操作并始终返回 TRUE。此函数类似于 chgrp 和 chmod。如果你需要知道某个文件的当前所有者，请使用 fileowner 函数。

```php
/*
 ** 将所有者更改为 leon
 */
if(chown("data.txt"
```

# closedir(integer directory_handle)

closedir 函数在用 opendir 函数打开目录后关闭它。PHP 在脚本结束时关闭目录连接，因此使用此函数并非绝对必要。

图 8-1. closedir。

IT-SC 籍 130

核心 PHP 编程

![](img/58e6a0f5d6a8a41d4645d8c07b3bf1e3_131_0.png)

- abs.php
- acos.php
- addcsslashes.php
- addslashes.php
- apache_lookup_uri.php
- apache_note.php
- array.php
- array_count_values.php
- array_flip.php
- array_keys.php
- array_merge.php
- array_multisort.php
- array_pad.php
- array_pop.php
- array_push.php
- array_reverse.php
- array_shift.php
- array_slice.php
- array_splice.php
- array_unshift.php

IT-SC 131

# boolean copy(string source, string destination)

copy 函数通过 source 参数将文件复制到 destination 参数指定的文件。这将产生两个独立的相同文件。类似的函数是 link，见下文描述。

```php
<?php
if(copy("data.txt", "/tmp/data.txt")) {
    print("data.txt copied to /tmp/");
} else {
    print("data.txt could not be copied");
}
?>
```

# float diskfreespace(string path)

diskfreespace 函数返回给定路径的可用字节数。

```php
<?php
print(diskfreespace("/"));
print(" bytes free");
?>
```

# object dir(string directory)

dir 函数创建一个目录对象，用作包含 opendir 和 closedir 的函数组的替代。返回的对象有两个属性：handle 和 path。handle 属性可以与其他目录函数（如 readdir）配合，因为它是通过 opendir 创建的。path 是创建目录对象的字符串。该对象有三个方法：read、rewind 和 close。它们的行为与 readdir、rewinddir 和 closedir 完全相同。

# boolean fclose(integer file_handle)

fclose 函数关闭文件。当文件被打开时，你会收到一个表示文件句柄的整数。该文件句柄用于在你完成使用后关闭文件。用于打开文件的函数有：fopen 和 fsockopen。要关闭管道，请使用 pclose。

```php
?>
```

# 核心 PHP 编程

```php
// 打开文件进行读取
$myfile = fopen("data.txt","r");

// 确保打开成功
if(!$myfile) {
    print("file could not be opened");
    exit;
}

while(!feof($myfile)) {
    // 从文件中读取的一行
    $myLine = fgets($myfile, 255);
    print("$myLine <BR>\n");
}

// 关闭文件
fclose($myfile);
?>
```

# boolean feof(integer file_handle)

当你从文件读取时，PHP 会保留一个指向你读取的文件中最后一个位置的指针。如果你位于文件末尾，feof 函数返回 TRUE。它通常用于 while 循环的条件部分，在该从中从头到尾读取文件。用法示例见上文 fclose 的描述。如果你需要知道你读取的精确位置，请使用 ftell 函数。

# string fgetc(integer file_handle)

fgetc 函数从文件中返回单个字符。它期望一个由 fopen、fsockopen 或 popen 返回的文件句柄。其他一些从文件读取的函数还有：fgetcsv、fgets、fread、gzgetc。

```php
<?php
// 打开文件并打印每个字符
if($myfile = fopen("data.txt", "r");
while(!feof($myfile)) {
    $myCharacter = fgetc($myfile);
    print("$myCharacter");
}
fclose($myfile);
?>
```

# array fgetcsv(integer file_handle, integer length, string separator)

fgetcsv 函数用于从文件中读取逗号分隔的数据。它需要一个由 fopen、popen 返回的有效文件句柄。还需要一个最大行长度。可选的 separator 参数指定分隔字段的字符。如果留空，则使用逗号。字段可以用双引号包围，这允许在字段中嵌入逗号和换行。

图 8-2. fgetcsv。

# 核心 PHP 编程

![](img/58e6a0f5d6a8a41d4645d8c07b3bf1e3_135_0.png)

```php
<?php
// 打开文件
if($myFile = fopen("data.csv", "r")) {
    print("<TABLE\n");

    while(!feof($myFile)) {
        print("<TR\n");

        $myField = fgetcsv($myFile, 1024);

        for($n=0; $n<count($myField); $n++) {
            print("\tTD\n");
            print($myField[$n]);
            print("</TD\n");
        }
        print("</TR\n");
    }

    fclose($myFile);
    print("</TABLE\n");
}
?>

# string fgets(integer file_handle, integer length, string ignore)

fgets 函数在各方面与 fgets 相同，只是它在返回字符串之前尝试剥离任何 HTML 标签。可选的 ignore 参数指定允许通过且保持不变的标签。它需要一个文件句柄，必须由 fopen、fsockopen 或 popen 创建。它将从文件中读取指定数量的字符。文件结束点是返回的字符串。

```php
<?php
// 打开文件并打印每个字符
if($myfile = fopen("data.txt", "r"));
while(!feof($myfile)) {
    $myLine = fgets($myfile, 255);
    print($myLine);
}
fclose($myfile);
?>
```

# string fstriptags(integer file_handle, integer length, string ignore)

fstriptags 函数在返回字符串之前尝试剥离任何 HTML 代码。可选的 ignore 参数指定允许通过的标签。如果你希望保留 HTML 但在解释它之前进行处理，可以使用 htmlentities 函数。它从文件中读取指定数量的字符。

```php
<?php
// 打开文件并打印每行，
/// 剥离锚点标签以外的 HTML
if($myFile = fopen("index.html", "r")) {
    while(!feof($myFile)) {
        $myLine = fstriptags($myFile, 1024, "<A>");
        print($myLine);
    }
    fclose($myFile);
}
?>
```

# array file(string filename)

IT-SC 籍 136

核心 PHP 编程

file 函数将整个文件作为数组返回。文件的每一行都是数组的一个独立元素。如果更方便将文件作为一个字符串进行处理，请使用 implode 函数，正如我在下面的示例中所做的那样如果你计划将文件直接发送到浏览器，请使用 readfile。

```php
<?php
// 打开文件
$myFile = file("data.txt");

// 将数组元素合并为一个字符串
$myFile = implode("", $myFile);

// 整个文件
print($myFile);
?>
```

# boolean file_exists(string filename)

file_exists 函数在指定文件存在时返回 TRUE，如果不存在则返回 FALSE。此函数是避免其他函数错误的良好方法。下面的示例在尝试将其发送到浏览器之前测试其是否存在。

```php
<?php
$filename = "data.txt";

// 如果文件存在，则打印
if(file_exists($filename))
{
    readfile($filename);
}
else
{
    print('$filename' 不存在");
}
?>
```

# integer filetime(string filename)

filetime 函数以标准时间戳返回文件的最后访问时间，即自 1970 年 1 月 1 日以秒数。如果发生错误则返回 False。如果文件被创建、写入或读取，则被认为已访问。与其他文件函数不同，filetime 在 Windows 和 UNIX 上的操作完全相同。获取与文件关联的时间戳的另外两个函数是 filectime 和 file。

