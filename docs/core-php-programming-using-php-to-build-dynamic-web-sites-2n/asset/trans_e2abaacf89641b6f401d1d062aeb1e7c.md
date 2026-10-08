

## integer filetime(string filename)

在 UNIX 上运行时，filetime 返回文件最后更改的时间，采用标准时间戳格式（即自 1970 年 1 月 1 日以来的秒数）。如果文件被创建、写入或权限被更改，则认为该文件已更改。在 Windows 上运行时，filetime 返回文件更改的时间。如果发生错误，则返回 FALSE。

另外两个获取文件相关时间戳的函数是 filetime 和 fileat。

## integer filegroup(string filename)

filegroup 函数返回给定文件的组标识，如果发生错误则返回 FALSE。此函数在 Windows 下始终返回 FALSE。其他返回文件信息的函数有 file-inode、fileowner 和 fileperms。要更改文件的所属组，请使用 chgrp。

```php
<?php print(filegroup("data.txt")); ?>
```

## integer fileinode(string filename)

fileinode 函数返回给定文件的 inode，如果出错则返回 FALSE。此函数在 Windows 下始终返回 FALSE。类似的函数有 filegroup、fileowner 和 fileperms。

```php
<?php ?>
```

## 核心 PHP 编程

```php
<?php
print(fileinode("data.txt"));
?>
```

## integer filetime(string filename)

filetime 函数返回文件最后修改的时间，采用标准时间戳格式（即自 1970 年 1 月 1 日以来的秒数）。如果出错则返回 FALSE。当文件被编辑或内容发生变化时，认为文件已修改。此函数在任何操作系统下的操作都是相同的。还有两个与文件时间戳相关的函数：fileat 和 filectime。

```php
<?php
$LastMod = filetime("data.txt");
print("Last modification was ");
print(date("l F d, Y", $LastMod));
?>
```

## integer fileowner(string filename)

fileowner 函数返回所有者的用户标识，如果出错则返回 false。此函数在 Windows 下始终返回 FALSE。如果你需要更改文件的所有者，可以使用 chown。获取文件信息的类似函数有 filegroup、fileinode 和 fileperms。

```php
<?php
print(fileowner("data.txt"));
?>
```

## integer fileperms(string filename)

fileperms 函数返回给定文件的权限数字，出错返回 false。如果你在使用 UNIX，可能希望参考 stat 系统函数的帮助页。你可能会惊讶地发现这个数字是以八进制表示的（这是惯例），由六位组成。前三位提供的信息实际上并不指向读/写/执行权限。你可能希望像示例中那样，通过执行逻辑 AND 操作来过滤掉信息。如果你需要更改文件的模式，请使用 chmod 函数。

```php
<?php
printf("%o", (fileperms("data.txt") & 0777));
?>
```

## integer filesize(string filename)

filesize 函数返回给定文件的大小（字节）。

```php
<?php
print(filesize("data.txt"));
?>
```

## string filetype(string filename)

filetype 函数以描述性字符串的形式返回给定文件的类型。可能的值包括 block、char、dir、fifo、file、link 和 unknown。此函数是 C 语言 stat 函数的接口，该函数的帮助页可能有助于理解不同的文件类型。

```php
<?php
print(filetype("data.txt"));
?>
```

## boolean flock(integer file_handle, integer mode)

使用 flock 临时限制对文件的访问。PHP 使用自己的锁定系统，该系统跨多个平台工作。然而，所有进程必须使用相同的锁定系统，因此文件将会被 PHP 脚本锁定，但可能不会被其他进程锁定。

file_handle 参数必须由 fopen 返回的整数。mode 参数决定你获取的是一个允许他人读取文件的锁 (1)，获取一个不允许他人读取文件的锁 (2)，或者是释放锁 (3)。在获取锁时，进程可能会阻塞（lock）。也就是说，如果文件已被锁定，它将等待到获取锁后继续执行。如果你愿意，可以关闭模式 5 和 6。表 8.5 在表格中列出了这些模式。

| 表 8.5. flock 模式 | |
| :--- | :--- |
| 模式 | 允许的操作 |
| 1 | 允许读取 |
| 2 | 不允许读取 |
| 3 | 释放锁 |
| 5 | 共享锁 |
| 6 | 排他锁 |

## 核心 PHP 编程

```php
<?php
$fp = fopen("data.txt", "r");
flock($fp, LOCK_SH); // 锁定共享锁
echo "Hello World!";
flock($fp, LOCK_UN); // 释放锁
fclose($fp);

$fp = fopen("data.txt", "w+");
if (flock($fp, LOCK_EX | LOCK_NB)) { // 锁定排他锁
    fwrite($fp, "Hello World!");
    fflush($fp); // 在释放锁前刷新输出
    flock($fp, LOCK_UN); // 释放锁
} else {
    echo "File could not be locked";
}
fclose($fp);
?>
```
