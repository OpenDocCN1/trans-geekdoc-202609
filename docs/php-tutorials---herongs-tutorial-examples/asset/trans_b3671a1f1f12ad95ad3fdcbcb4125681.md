

# PHP 文件操作函数参考

## 文件指针操作函数

*   `fseek($file, $offset)` - 此“文件查找”函数将 `$file` 移动到实际文件中的 `$offset` 位置。
*   `rewind($file)` - 此“倒带”函数将 `$file` 位置重置为实际文件的开头。
*   `flock($file, $locker)` - 此“文件锁定”函数在 `$file` 上应用锁。支持 4 种锁类型：`LOCK_SH`、`LOCK_EX`、`LOCK_UN` 和 `LOCK_NB`。
*   `fstat($file)` - 此“文件统计”函数返回一个包含 `$file` 统计信息的数组。返回的数组包含的元素键有：`dev`、`ino`、`mode`、`nlink`、`uid`、`gid`、`rdev`、`size`、`atime`、`mtime`、`ctime`、`blksize` 和 `blocks`。
*   `fgetc($file)` - 此“文件获取字符”函数读取 1 字节并将其作为字符串返回。

详见下一节的 PHP 示例脚本。

---

# File_Input_Output_Test.php - 文件输入/输出示例

本节提供了一个教程示例脚本，演示如何使用 `fopen()`、`fread()`、`fwrite()` 和 `fclose()` 等文件输入输出函数。该示例脚本以二进制模式复制任意文件。

为了演示上一节描述的文件测试函数的用法，编写了以下简单脚本：

```php
<?php
#  File_Input_Output_Test.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   if (count($argv) > 1) {
      $path = $argv[1];
   } else {
      print("\n Please specify a file path name.\n");
      exit();
   }

   if (file_exists($path)) {
      print("\n Good. $path does exists!.\n");

      if (is_file($path)) {
         print("\n Very good. $path is a file.\n");

         print("\n Starting to copy $path to $path.bck...\n");
         $input = fopen($path, "rb"); # For binary read
         $output = fopen($path . ".bck", "wb"); # For binary write
         $inCount = 0;
         $outCount = 0;
         while (!feof($input)) {
            $buffer = fread($input, 1024);
            $inCount += strlen($buffer);
            $outCount += fwrite($output, $buffer);
         }
         fclose($input);
         fclose($output);

         print("   # of bytes read: $inCount\n");
         print("   # of bytes write: $outCount\n");
      } else {
         print("\n Too bad. $path is not a file.\n");
         exit();
      }
   } else {
      print("\n Bad. $path does not exists!.\n");
      exit();
   }
?>
```

如果使用不同的路径名运行此示例脚本，应得到如下输出：

```
herong> \php\php File_Input_Output_Test.php \php\php.exe

 Good. \php\php.exe does exists!.

 Very good. \php\php.exe is a file.

 Starting to copy \php\php.exe to \php\php.exe.bck...
   # of bytes read: 32821
   # of bytes write: 32821


herong> \php\php File_Input_Output_Test.php \php

 Good. \php does exists!.

 Too bad. \php is not a file.
```

---

# readfile() 和特殊文件处理函数

本节介绍一些特殊的文件处理函数。`readfile()` 将文件复制到标准输出。`fgetss()` 读取一行并移除标签。`tmpfile()` 打开一个临时文件。`file()` 将文件读入数组。

PHP 还提供了许多其他内置函数来执行特殊的文件输入和输出任务：

*   `file_get_contents($path)` - 此“文件获取内容”函数将指定文件的全部内容作为字符串返回。
*   `file_put_contents($path, $data)` - 此“文件写入内容”函数将指定数据写入指定文件。
*   `file($path)` - 此“文件”函数将指定文件的全部内容作为数组返回。数组中的每个元素代表文件中的一行。
*   `readfile($path)` - 此“读取文件”函数读取文件的全部内容并写入标准输出。
*   `fpassthru($file)` - 此“文件直通”函数从 `$file` 读取剩余数据并写入标准输出。
*   `fgetss($file)` - 此“文件获取字符串剥离”函数从 `$file` 读取一行，并返回去除 HTML 和 PHP 标签后的字符串。
*   `fgetcsv($file)` - 此“文件获取 CSV”函数从 `$file` 读取一行，并通过按 CSV 格式解析将其作为数组元素返回。
*   `fputcsv($file, $array)` - 此“文件写入 CSV”函数将 `$array` 中的元素以 CSV 格式写入 `$file`。
*   `tmpfile()` - 此“临时文件”函数以读写（`w+`）模式打开一个临时文件并返回文件资源句柄。当其文件资源句柄关闭时，此临时文件将被删除。
*   `tempnam($path, $prefix)` - 此“临时名称”函数在 `$path` 中创建一个带有 `$prefix` 前缀的临时文件名。

---

# ShowPhoto.php - 简单幻灯片展示脚本

本节提供了一个教程示例，演示如何以幻灯片格式显示目录中的图像文件。使用 `getimagesize()` 函数从图像文件中检索图像尺寸。

另一个用于图像文件管理的实用函数是“获取图像尺寸”函数 `getimagesize($path)`，它返回存储在 `$path` 位置的文件中的图像的大小和其他信息。

为了演示如何使用 `getimagesize()` 函数，编写了以下示例脚本：

```php
<?php
#  PhotoShow.php
#- Copyright 2009-2015 (c) HerongYang.com. All Rights Reserved.
#
#- Get the photo file name
   $i = intval($_GET['i']);
   $c = 0;
   $p = "";
   if ($d = opendir(".")) {
      while (($f = readdir($d)) != false) {
         if (preg_match('/.jpg$/', $f)) {
            if ($i == $c) {
               $p = $f;
            }
            $c++;
         }
      }
      closedir($d);
    }

#- Build the page
   $h = fopen("header.html", "r");
   $s = fread($h, filesize("header.html"));
   fclose($h);
   print "$s\n";

   if (strlen($p) > 0) {
      $i1 = ($i + $c - 1) % $c;
      $i2 = ($i + $c + 1) % $c;
      list($width, $height, $type, $attr) = getimagesize($p);
      if ($width > 700) {
         $width = $width / 2;
         $height = $height / 2;
      }
      print "<center><a href=\"ShowPhoto.php?i=$i1\"><=</a>&nbsp;"
         . "<a href=\"ShowPhoto.php?i=$i2\">=></a></center>\n"
         . "<center><img src=\"$p\" border=\"1\" width=\"$width\" "
         . "height=\"$height\"></center><br\>\n"
         . "<center><a href=\"ShowPhoto.php?i=$i1\"><=</a>&nbsp;"
         . "<a href=\"ShowPhoto.php?i=$i2\">=></a></center>\n";
   } else {
      print "<p>Wrong URL. Please go back to the home page.</p>\n";
   }

   $h = fopen("footer.html", "r");
   $s = fread($h, filesize("footer.html"));
   fclose($h);
   print "$s\n";
?>
```

此脚本将显示存储在目录中的图像文件，一次显示一张，如同幻灯片放映。

请尝试运行。它非常易于使用。您可以轻松地对其进行自定义以满足您的需求。

---

# SOAP 扩展函数与调用 Web Services

本章提供关于 SOAP 扩展函数的教程示例和说明。主题包括 PHP 的 SOAP 实现、SOAP 扩展库、SOAP 客户端函数、使用和不使用 WSDL 标准调用 Web Services、用于转储 SOAP 通信详细调试信息的示例脚本。

## 章节导航

*   [PHP Implementations of SOAP](#part0147.xhtml)
*   [Turning on the Default SOAP Extension](#part0148.xhtml)
*   [Hello_There.php - First Example of SOAP](#part0149.xhtml)
*   [SoapClient - SOAP Client Class and Functions](#part0150.xhtml)
*   [Hello_There_Dump.php - Debugging SOAP Messages](#part0151.xhtml)
*   [What Is WSDL](#part0152.xhtml)
*   [Using SOAP Extension in non-WSDL Mode](#part0153.xhtml)

## 核心要点

*   似乎有 3 种流行的 PHP SOAP 实现：PEAR SOAP、NuSOAP 和 PHP Group SOAP Extension。
*   PHP Group SOAP Extension 5.0.4 似乎支持 SOAP 1.2。但它默认使用 SOAP 1.1。

