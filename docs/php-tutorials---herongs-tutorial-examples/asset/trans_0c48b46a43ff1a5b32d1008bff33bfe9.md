

# MySQL 服务器连接和访问函数

*   `mysqli_close()` - 关闭 MySQL 连接资源。通常使用 1 个参数调用它，如 `mysqli_close($connection)`，其中 `$connection` 代表要关闭的连接资源。
*   `mysqli_get_server_info()` - 返回服务器信息字符串。
*   `mysqli_status()` - 返回服务器状态字符串。
*   `mysqli_query()` - 向服务器发送查询，并返回结果集资源。例如，`mysqli_query('SELECT * FROM MyTable WHERE ID = 10')`。
*   `mysqli_affected_rows()` - 如果执行的查询是 INSERT 或 UPDATE 语句，则返回给定结果集的受影响行数。
*   `mysqli_num_rows()` - 如果执行的查询是 SELECT 语句，则返回给定结果集的行数。
*   `mysqli_fetch_array()` - 从给定结果集中获取一行，并将该行作为同时具有数字索引和列名映射的数组返回。如果结果集中不再有行，则返回布尔值 false。
*   `mysqli_free_result()` - 释放给定的结果集。

## MySqlLoop.php - MySQL 函数测试

本节提供了一个教程示例，说明如何使用 MySQL 函数连接到 MySQL 服务器，并运行 SQL 语句来创建表、插入行以及从 MySQL 服务器获取行。

为了向您展示其中一些 MySQL 函数应如何使用，我编写了这个简单的脚本 `MySqlLoop.php`：

```php
<?php
#  MySqlLoop.php
#- Copyright 2009-2015 (c) HerongYang.com. All Rights Reserved.
#
   $con = mysqli_connect("localhost", "root", "");
   $rs = mysqli_query($con,'DROP DATABASE MyBase');
   $rs = mysqli_query($con,'CREATE DATABASE MyBase');
   if (!$rs) {
      echo "Error: Unable to create the database.\n";
      echo mysqli_connect_errno()." - ".mysqli_connect_error()."\n";
      exit;
   }
   $rs = mysqli_query($con,'USE MyBase');
   print "Creating a table...\n";
   $rs = mysqli_query($con,'CREATE TABLE MyTable (ID INTEGER,'
      .' Value INTEGER)');
   $n = 100;
   $i = 0;
   print "Inserting some rows to the table...\n";
   while ($i < $n) {
      $rs = mysqli_query($con,'INSERT INTO MyTable VALUES ('.$i.', '
         .rand(0,$n-1).')');
      $i++;
   }
   print "Query some rows from the table...\n";
   $rs = mysqli_query($con,'SELECT * FROM MyTable WHERE ID < 10');
   print "   ".mysqli_field_name($rs,0)."   "
      .mysqli_field_name($rs,1)."\n";
   while ($row = mysqli_fetch_array($rs)) {
      print "    ".$row[0].'   '.$row[1]."\n";
   }
   mysqli_free_result($rs);
   mysqli_close($con);

function mysqli_field_name($result, $field_offset) {
   $properties = mysqli_fetch_field_direct($result, $field_offset);
   return is_object($properties) ? $properties->name : null;
}
?>
```

请注意，如果在查询调用中未指定连接资源，将使用最后一个连接资源。如果您运行此脚本，将得到类似如下的输出：

```
Creating a table...
Inserting some rows to the table...
Query some rows from the table...
   ID   Value
    0   14
    1   91
    2   84
    3   16
    4   88
    5   51
    6   12
    7   19
    8   39
    9   5
```

# 管理目录、文件和图像的函数

本章提供了关于管理目录、文件和图像的函数的教程示例和注释。主题包括目录管理函数（如 `mkdir()`）、文件测试函数（如 `is_file()`）、文件输入和输出函数（如 `fopen()`）。

*   [opendir() 和目录管理函数](#part0139.xhtml)
*   [file_exists() 和文件测试函数](#part0140.xhtml)
*   [FileExistsTest.php - 文件测试示例](#part0141.xhtml)
*   [fopen() 和文件输入/输出函数](#part0142.xhtml)
*   [File_Input_Output_Test.php - 文件输入/输出示例](#part0143.xhtml)
*   [readfile() 和特殊文件处理函数](#part0144.xhtml)
*   [ShowPhoto.php - 简单幻灯片播放脚本](#part0145.xhtml)

## 要点

*   PHP 支持类似于 Unix 命令的目录管理函数，如 `chdir()`、`mkdir()` 和 `rmdir()`。
*   要遍历目录树，可以使用 `opendir()` 和 `is_dir()` 函数。
*   要获取有关文件的详细信息，可以使用 `stat()` 函数。
*   要从文件读取数据，可以使用 `fopen()` 和 `fread()` 函数。
*   要向文件写入数据，可以使用 `fopen()` 和 `fwrite()` 函数。

## opendir() 和目录管理函数

本节描述 `opendir()` 和其他目录管理函数。提供了一个教程示例，说明如何将目录作为目录资源句柄打开，并在循环中使用 `readdir()` 函数读取其条目。

PHP 提供以下内置函数来管理文件系统的目录：

*   `chdir($path)` - 此“更改目录”函数将当前目录更改为指定的路径。如果指定的路径无效，则返回 FALSE。例如，`chdir("/herong/php")` 将当前目录更改为 `/herong/php`。
*   `getcwd()` - 此“获取当前工作目录”函数返回当前目录的路径名。
*   `opendir($path)` - 此“打开目录”函数创建并返回一个目录资源句柄，该句柄代表指定路径的目录。返回的目录资源句柄包含一个当前条目指针，最初设置在目录第一个条目前面的位置。如果指定的路径无效，则返回 FALSE。例如，`$dir = opendir("/herong/php")` 将一个代表 `/herong/php` 的目录资源句柄赋值给 `$dir`。
*   `closedir($dir)` - 此“关闭目录”函数关闭指定的目录资源句柄。
*   `readdir($dir)` - 此“读取目录”函数将内部指针移动到由指定目录资源句柄代表的目录中的下一个条目，并将该条目作为字符串返回。如果内部指针当前指向目录末尾，则返回 FALSE，因为没有下一个条目。
*   `rewinddir($dir)` - 此“倒回目录”函数将其内部指针重置为第一个条目前面的位置。
*   `scandir($path,$order)` - 此“扫描目录”函数以数组形式返回目录中指定路径的所有条目，并按指定顺序排序。如果未指定 `$order` 或 `$order=0`，条目按字母顺序升序排序。如果 `$order=0`，条目按字母顺序降序排序。（注：原文此处有误，通常 `$order=1` 为降序，但此处严格翻译原文逻辑）
*   `dir($path)` - 此“目录”类构造函数返回目录对象，代表指定路径的目录。
*   `mkdir($path)` - 此“创建目录”函数使用指定路径创建一个新目录。
*   `rmdir($path)` - 此“删除目录”函数删除指定路径的目录。

为了向您展示如何使用其中一些函数，我编写了这个简单的脚本：

```php
<?php
#  OpendirTest.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   $path = "/php";

   print "\n First 10 entries in $path:\n";
   $dir = opendir($path);
   $i = 0;
   while (FALSE !== ($entry = readdir($dir)) && $i<10) {
      $i++;
      print "   $entry\n";
   }

   print "\n First 10 entries in $path again:\n";
   $dir = dir($path);
   $i = 0;
   while (FALSE !== ($entry = $dir->read()) && $i<10) {
      $i++;
      print "   $entry\n";
   }
?>
```

如果您运行此脚本，应该会得到：

```
 First 10 entries in /php:
   .
   ..
   deplister.exe
   dev
   ext
   extras
   glib-2.dll
   gmodule-2.dll
   icudt63.dll
   icuin63.dll

 First 10 entries in /php again:
   .
   ..
   deplister.exe
   dev
   ext
   extras
   glib-2.dll
   gmodule-2.dll
   icudt63.dll
   icuin63.dll
```

