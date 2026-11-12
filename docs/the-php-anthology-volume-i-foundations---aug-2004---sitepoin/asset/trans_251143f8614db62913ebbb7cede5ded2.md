

## 如何获取本地文件的信息？

PHP 自带一系列函数，可帮助你获取文件信息。例如，我们可以检查文件是否存在，并获取其大小：

```
<?php
// Function to convert a size to bytes to large units
function fileSizeUnit($size)
{
    if ($size >= 1073741824) {
        $size = number_format(($size / 1073741824), 2);
        $unit = 'GB';
    } else if ($size >= 1048576) {
        $size = number_format(($size / 1048576), 2);
        $unit = 'MB';
    } else if ($size >= 1024) {
        $size = number_format(($size / 1024), 2);
        $unit = 'KB';
    } else if ($size >= 0) {
        $unit = 'B';
    } else {
        $size = '0';
        $unit = 'B';
    }

    return array('size' => $size, 'unit' => $unit);
}

$file = 'demo/writeSecureScripts.html';
// Does the file exist
if (file_exists($file)) {
    echo 'Yep: ' . $file . ' exists.<br />';
} else {
    die('Where has: ' . $file . ' gone!<br />');
}

// Use a more convenient file size
$size = fileSizeUnit(filesize($file));

// Display the result
echo 'It\'s ' . $size['size'] . '' . $size['unit'] .
' in size.<br />';
?>
```

我们开头使用的 fileSizeUnit 函数有助于让 PHP 的 filesize 函数返回的结果更易读。

这里是输出：

```
Yep: demo/writeSecureScripts.html exists.
It's 16.28 KB in size.
```

PHP 还能提供许多其他文件信息片段：

```
<?php
$file = 'demo/writeSecureScripts.html';

// Is it a file? Could be is_dir() for directory
if (is_file($file)) {
    echo 'Yep: ' . $file . ' is a file<br />';
}

// Is it readable
if (is_readable($file)) {
    echo $file . ' can be read<br />';
}

// Is it writable
if (is_writable($file)) {
    echo $file . ' can be written to<br />';
}

// When was it last modified?
$Modified = date("D d M g:i:s", filemtime($file));
echo $file . ' last modified at ' . $Modified . '<br />';

// When was it last accessed?
$Accessed = date("D d M g:i:s", fileatime($file));
echo $file . ' last accessed at ' . $Accessed . '<br />';
?>
```

这里是输出：

```
Yep: demo/writeSecureScripts.html is a file
demo/writeSecureScripts.html can be read
demo/writeSecureScripts.html can be written to
demo/writeSecureScripts.html last modified at Sun 09 Mar 12:08:02
demo/writeSecureScripts.html last accessed at Sun 09 Mar 2:35:47
```

## 清除文件统计缓存

PHP 会缓存文件信息函数的结果以提高性能。不过，有时有必要清除该缓存；这可以通过 clearstatcache 函数来实现。

## 如何使用 PHP 读取目录？

特别是对于基于 Web 的文件管理器，使用 PHP 浏览目录内容非常方便。这有两种基本方法；涉及的 PHP 函数在 PHP 手册[5]中有说明。

```
<?php
// Open the current directory
$location = './';
// Open current directory
$dp = opendir($location);
// Loop through the directory
while ($entry = readdir($dp)) {
    // If $entry is a directory....
    if (is_dir($location . $entry)) {
        echo '[Dir] ' . $entry . '<br />';
    } else if (is_file($location . $entry)) {
        echo '[File] ' . $entry . '<br />';
    }
}
// Close it again!
closedir($dp);
?>
```

[5] http://www.php.net/dir

这里是输出：

```
[Dir] .
[Dir] ..
[File] 1.php
[File] 10.php
[File] 11.php
[File] 12.php
[File] 13.php
[File] 14.php
[File] 15.php
[File] 16.php
[File] 17.php
[File] 18.php
[File] 19.php
[File] 2.php
[File] 3.php
[File] 4.php
[File] 5.php
[File] 6.php
[File] 7.php
[File] 8.php
[File] 9.php
[Dir] demo
[File] extensions.ini
[Dir] ftploads
[File] sample.zip
```

另一种方法是使用内置于 PHP 的“伪”类 dir 函数。在用法上，它几乎完全相同：

```
File: 12.php
<?php
// Specify current directory
$location = './';
// Open current directory
$dir = dir($location);
// Loop through the directory
while ($entry = $dir->read()) {
// If $entry is a directory...
if (is_dir($location . $entry)) {
echo '|Dir| ' . $entry . '<br />';
}
// If $entry is a file...
} else if (is_file($location . $entry)) {
echo '[File] ' . $entry . '<br />';
}
}
// Close it again!
$dir->close();
?>
```

选择哪种纯粹是个人偏好问题。

## 如何在线显示 PHP 源代码？

有时你可能想显示某个文件的源代码，例如在为他人发布代码时。不过，以这种方式操作时必须极其谨慎——你可能会不经意间泄露比预期更多的信息，例如数据库用户名和密码。

需要指出，我这里并不主张出于安全考虑而隐藏代码。代码应该从一开始就编写得安全。为了防止他人发现其中的漏洞而隐藏代码，是走向灾难的配方；最终，有人会发现你隐藏了什么，而且更糟糕的是，你很可能会对他们正在利用你的安全漏洞一无所知。

PHP 提供了一个名为 highlight_string 的非常方便的函数来显示代码，它使用 php.ini 中定义的格式以美观的方式显示 PHP 代码。与此函数配套的 highlight_file 让事情变得更加简单，只需传递一个文件名即可显示。

下面是一个显示目录中所选文件源代码的脚本：

```
<?php
// Define an array of allowed files - VERY IMPORTANT!
$allowed = array('3.php', '4.php', '6.php', '10.php');

// If it's an allowed file, display it.
if (isset($_GET['view']) && in_array($_GET['view'], $allowed)) {
    highlight_file($_GET['view']);
} else {
    // Specify current directory
    $location = './';
// Open current directory
$dir = dir($location);

// Loop through the directory
while ($entry = $dir->read()) {
    // Show allowed files only
    if (in_array($entry, $allowed)) {
        echo '<a href="' . $_SERVER['PHP_SELF'] .
        '?view=' . $entry . '">' . $entry . "</a><br />\n";
    }
}

// Close it again!
$dir->close();
}
?>
```

请注意，无论在显示目录内容还是单个文件源代码时，我都非常小心地只允许访问指定文件。上面的示例应该能让你了解在 PHP 中构建文件管理系统是多么容易。

精美呈现的脚本如图 4.4 所示。亲自试一下，看看各种 PHP 语法片段的彩色高亮效果！

## 图 4.4. 返回源代码

```
<?php
$file = 'demo/writeSecureScripts.html';

// Is it a file? Could be is_dir() for directory
if ( is_file ( $file ) )
   echo ( 'Yep: '.$file.' is a file<br />' );

// Is it readable
if ( is_readable ( $file ) )
   echo ( $file.' can be read<br />' );

// Is it writeable
if ( is_writeable ( $file ) )
   echo ( $file.' can be written to<br />' );

// When was it last modified?
$modified = date ( "D d M g:i:s",filemtime($file) );
echo ( $file.' last modified at '.$modified.'<br />' );

// When was it last accessed?
$accessed = date ( "D d M g:i:s",fileatime($file) );
echo ( $file.' last accessed at '.$accessed.'<br />' );
?>
```

在 PHP 4.2.0 或更高版本中，如果向 highlight_string 或 highlight_file 传递第二个参数 TRUE，则它将把结果作为字符串返回，而不是直接显示文件。

## 如何将配置信息存储在文件中？

某些在整个网站中反复使用的信息，例如数据库连接设置，最好存储在单个文件中。如果需要将代码迁移到另一个网站，你只需修改一次设置，而不是成百上千次。实现这一点的最简单方法是在包含文件中创建变量，然后在代码中包含该文件。但有时编辑 PHP

