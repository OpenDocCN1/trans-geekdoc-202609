
现在在 Web 浏览器中打开上述 HTML 文件。你应该会看到网页上显示了一些文本，透明图像悬浮在文本上方。

![Display Transparent Image over Text](img/image00232.jpeg)

透明图像悬浮于文本之上

---

## GD 库 - 填充透明图像

本节提供了一个教程示例，说明如何使用 GD 库函数通过填充透明背景来扩展图像。

如果你想使用 GD 库通过透明背景来填充图像，请记住以下几点：

1. 为图像的背景选择一种颜色。确保此背景颜色不用于绘制图像上的任何图形元素。
2. 创建一个具有原始图像填充后尺寸的新图像。
3. 使用 `imagefilledrectangle()` 用背景颜色填充新图像。
4. 使用 `imagecopy()` 将原始图像复制到新图像。原始图像的透明背景颜色不会被复制。
5. 使用 `imagecolortransparent()` 将新图像的背景颜色设置为透明。
6. 以支持透明背景的格式（如 GIF 或 PNG）保存新图像。

下面是一个 PHP 脚本，它在透明背景图像的四边各填充 10% 进行扩展。

## PHP 教程 - Herong 的教程示例

### 管理 ZIP 归档文件

本章提供了关于管理 ZIP 归档文件的教程示例和说明。主题包括 `ZipArchive` 类简介；创建新的 ZIP 归档；从 ZIP 归档中提取文件；在 ZIP 归档内创建目录结构；使用动态数据在临时文件中创建 ZIP 归档以供下载。

#### ZipArchive 类

#### 创建新的 ZIP 归档

#### 从 ZIP 归档中提取文件

### 创建带目录的 ZIP 归档

#### 创建用于下载的 ZIP 归档

#### 要点

*   使用 `ZipArchive` 类通过 PHP 脚本管理 ZIP 归档。
*   使用 `$zip = new ZipArchive;` 创建 `ZipArchive` 类的实例。
*   使用 `$zip->open($zip_path_name, ZipArchive::CREATE);` 创建 ZIP 归档。
*   使用 `$zip->addFile($file);` 向 ZIP 归档添加文件。
*   使用 `$zip->extractTo($destination, $file);` 从 ZIP 归档中提取文件。
*   使用 `$zip->addEmptyDir($dir_path);` 在 ZIP 归档内创建目录。
*   使用 `$zip->addFile($file, $dir_path);` 将文件添加到 ZIP 归档内的指定目录中。
*   使用 `$tmpDir = sys_get_temp_dir();` 访问系统临时目录。
*   使用 `$tmpFile = tempnam($tmpDir, $prefix);` 获取临时文件名。
*   使用 `$zip->open($tmpFile, ZipArchive::CREATE);` 在临时文件中创建 ZIP 归档。
*   使用 `$zip->addFromString($fileName, $data);` 将动态数据作为文件添加到 ZIP 归档中。

#### ZipArchive 类

本节简要介绍 `ZipArchive` 类，该类提供创建新的 ZIP 归档、从现有 ZIP 归档中提取文件以及其他功能。

**什么是 ZipArchive 类？** - `ZipArchive` 是一个内置的 PHP 类，它提供创建新的 ZIP 归档、从现有 ZIP 归档中提取文件以及其他功能。

以下是 `ZipArchive` 类提供的一些主要方法列表：

*   `$zip = $zip = new ZipArchive`：创建 `ZipArchive` 类的实例作为 `$zip`。
*   `$zip->open()`：将给定的 ZIP 归档关联到 `$zip`。可提供选项标志以创建新归档或更新/提取现有 ZIP 归档。
*   `$zip->close()`：关闭关联的 ZIP 归档。
*   `$zip->addFile()`：将给定文件添加到关联的 ZIP 归档中。
*   `$zip->addFromString()`：将给定字符串作为文件添加到关联的 ZIP 归档中。
*   `$zip->addEmptyDir()`：将给定路径名作为空目录添加到关联的 ZIP 归档中。
*   `$zip->addPattern()`：从给定目录添加与正则表达式模式匹配的文件。该操作不递归。模式仅针对文件名进行匹配。
*   `$zip->extractTo()`：将完整归档或给定文件提取到指定目标位置。
*   `$zip->deleteName()`：使用其名称删除关联归档中的条目。
*   `$zip->setPassword`：为关联的归档设置密码。

#### 创建新的 ZIP 归档

本节提供了一个教程示例，说明如何使用 `ZipArchive` 类创建新的 ZIP 归档并向其中添加文件。

创建新 ZIP 归档的最佳方法是在 `$zip->open()` 方法中使用 `ZipArchive::CREATE` 标志。例如，以下代码将创建一个新的空 ZIP 归档（如果 `/tmp/test.zip` 不存在）。如果 `/tmp/test.zip` 存在，它将被打开以添加新条目或提取条目。仅当 `/tmp/test.zip` 存在且不是 ZIP 文件时才会失败。

```php
$zip = new ZipArchive;
$zip->open('/tmp/test.zip', ZipArchive::CREATE);
```

下面是一个创建新 ZIP 归档并向其中添加一些文件的示例脚本。

```php
<?php
#### zip-create-new.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.

  $zip = new ZipArchive;
  echo "Creating test.zip:\n";
  $rc = $zip->open('/tmp/test.zip', ZipArchive::CREATE);
  if ($rc === TRUE) {
    echo "   test.zip opened\n";

    $file = 'dot.gif';
    if ($zip->addFile($file) === TRUE) {
      echo "   $file added\n";
    } else {
      echo "   Failed to add $file.\n";
    }

    $file = 'zip-create-new.php';
    if ($zip->addFile($file) === TRUE) {
      echo "   $file added\n";
    } else {
      echo "   Failed to add $file.\n";
    }

    $file = 'junk.jnk';
    if ($zip->addFile($file) === TRUE) {
      echo "   $file added\n";
    } else {
      echo "   Failed to add $file.\n";
    }

    $zip->close();
  } else {
    echo "   Failed to create test.zip with error: $rc\n";
  }
?>
```

让我们试一下：

```
herong$ php zip-create-new.php
Creating test.zip:
   test.zip opened
   dot.gif added
   zip-create-new.php added
   Failed to add junk.jnk.

herong$ unzip -l /tmp/test.zip
Archive:  /tmp/test.zip
  Length      Date    Time    Name
---------  ---------- -----   ----
       43  03-01-2020 14:15   dot.gif
      815  03-01-2020 15:17   zip-create-new.php
---------                     -------
      858                     2 files
```

#### 从 ZIP 归档中提取文件

本节提供了一个教程示例，说明如何使用 `ZipArchive` 类打开现有的 ZIP 归档并从中提取文件。

从 ZIP 归档中提取文件最简单的方法是使用 `$zip->extractTo()` 方法。例如，以下代码将 `dot.gif` 从 `/tmp/test.zip` 提取到 `/tmp` 目录中。

```php
$zip = new ZipArchive;
$zip->open('/tmp/test.zip');
$zip->extractTo('/tmp', 'dot.gif');
```

下面是一个打开现有 ZIP 归档并从中提取文件的示例脚本。

```php
<?php
#### zip-extract-file.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.

  $zip = new ZipArchive;
  echo "Opening test.zip:\n";
  $rc = $zip->open('/tmp/test.zip', ZipArchive::CREATE);
  if ($rc === TRUE) {
    echo "   test.zip opened\n";

    $file = 'dot.gif';
    if ($zip->extractTo('.', $file) === TRUE) {
      echo "   $file extracted\n";
    } else {
      echo "   Failed to extract $file.\n";
    }

    mkdir('./tmp');
    if ($zip->extractTo('./tmp') === TRUE) {
      echo "   All files extracted\n";
    } else {
      echo "   Failed to extract all files.\n";
    }

    $zip->close();
  } else {
    echo "   Failed to open test.zip with error: $rc\n";
  }
?>
```

让我们试一下：

### 创建包含目录的 ZIP 归档

本节提供了一个教程示例，介绍如何使用 `ZipArchive` 类创建包含目录的 ZIP 归档，并向该目录添加文件。

如果你想在 ZIP 归档内部创建目录结构，以便将文件添加到归档中的不同位置，你需要使用 `ZipArchive` 类的两个方法：

1. 使用 `addEmptyDir()` 方法在 ZIP 归档内创建目录。例如，以下代码创建一个目录和一个子目录。

```php
$zip->addEmptyDir('src');
$zip->addEmptyDir('src/gif');
```

2. 使用 `addFile()` 方法通过本地路径名将文件添加到归档。例如，以下代码将 `dot.gif` 添加到归档中的 `src/gif` 子目录。

```php
$zip->addFile('dot.gif', 'src/gif/dot.gif');
```

下面是一个示例脚本，它创建一个包含目录的新 ZIP 归档，并向归档中的该目录添加一些文件。

```php
<?php
#### zip-with-directory.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.

  $zip = new ZipArchive;
  echo "Creating test.zip:\n";
  $rc = $zip->open('/tmp/test.zip', ZipArchive::CREATE);
  if ($rc === TRUE) {
    echo "   test.zip opened\n";

    $dir = "srcDir";
    if ($zip->addEmptyDir($dir) === TRUE) {
      echo "   $dir added\n";
    } else {
      echo "   Failed to add $dir.\n";
    }

    $file = 'dot.gif';
    if ($zip->addFile($file, "$dir/$file") === TRUE) {
      echo "   $file added\n";
    } else {
      echo "   Failed to add $file.\n";
    }

    $file = 'zip-create-new.php';
    if ($zip->addFile($file, "$dir/$file") === TRUE) {
      echo "   $file added\n";
    } else {
      echo "   Failed to add $file.\n";
    }

    $zip->close();
  } else {
    echo "   Failed to create test.zip with error: $rc\n";
  }
?>
```

让我们试一下：

```
herong$ php zip-with-directory.php
Creating test.zip:
   test.zip opened
   srcDir added
   dot.gif added
   zip-create-new.php added

herong$ unzip -l /tmp/test.zip
Archive:  /tmp/test.zip
  Length      Date    Time    Name
---------  ---------- -----   ----
        0  06-04-2020 15:53   srcDir/
       43  06-04-2020 15:37   srcDir/dot.gif
      815  06-04-2020 15:17   srcDir/zip-create-new.php
---------                     -------
      858                     3 files
```

#### 创建用于下载的 ZIP 归档

本节提供了一个教程示例，介绍如何使用 `ZipArchive` 类在临时文件中创建包含动态数据的 ZIP 归档，并将其作为下载发送给 Web 浏览器。

如果你有来自数据库的数据项供用户从 Web 服务器下载，你可能希望即时将它们打包成 ZIP，以便用户可以在单个 ZIP 文件中下载它们。

当然，最好的选择是从内存中检索数据库中的数据项，在内存中将它们压缩成 ZIP，并将 ZIP 发送给用户的浏览器，而无需在 Web 服务器上创建任何物理文件。然而，`ZipArchive` 类不支持将 ZIP 归档作为文件句柄或管道处理，因此这是不可行的。

次选方案是从内存中检索数据库中的数据项，将它们压缩到一个临时文件中，发送给用户的浏览器后立即将其删除。这可以通过以下步骤完成：

1. 在系统临时目录中创建一个唯一的文件名作为 ZIP 文件名：

```php
$tmpDir = sys_get_temp_dir();
$zipFile = tempnam($tmpDir, "ZIP"); # ZIP 是临时名称的前缀
```

2. 打开临时文件和 ZIP 归档：

```php
$zip->open($zipFile, ZipArchive::CREATE);
```

3. 从数据库检索数据项并遍历每一项。

4. 为每一项创建一个唯一的名称，并将项数据作为字符串添加到 ZIP 归档中。

```php
$itemData = ...; # 基于数据库中的数据
$itemName = ...; # 基于数据库中的记录 ID
$zip->addFromString("$itemName", $itemData);
```

5. 关闭 ZIP 归档，从临时文件读回 ZIP 数据，并立即删除它。

```php
$zip->close();
$zipData = file_get_contents($zipFile);
unlink($zipFile);
```

6. 将 ZIP 数据发送给 Web 浏览器。

下面是一个示例脚本，它在临时文件中创建一个包含动态数据项的新 ZIP 归档。然后将 ZIP 归档推送到客户端浏览器。
