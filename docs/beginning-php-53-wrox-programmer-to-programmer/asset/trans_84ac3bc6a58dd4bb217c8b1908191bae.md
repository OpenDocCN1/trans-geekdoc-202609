

# 第 11 章：文件与目录目录操作

## 构建一个文本编辑器

在你已经掌握了 PHP 文件和目录处理的基础知识后，是时候创建一个简单的基于 Web 的文本编辑器应用程序了。该编辑器将显示指定文件夹中的文本文件列表，允许用户通过点击文件名来编辑文件。编辑页面将直接在 HTML 文本区域字段中显示文件内容，并带有保存或取消编辑的按钮。

用户还可以创建新的文本文件进行操作。为了简单起见，编辑器将仅处理扩展名为 `.txt` 的文本文件。

以下是文本编辑器的代码。将其保存为 `text_editor.php` 到你的文档根目录中：

```php
<?php

define("PATH_TO_FILES", "/home/matt/sandbox/");

if (isset($_POST['saveFile'])) {
    saveFile();
} elseif (isset($_GET['filename'])) {
    displayEditForm();
} elseif (isset($_POST['createFile'])) {
    createFile();
} else {
    displayFileList();
}

function displayFileList($message="") {
    displayPageHeader();
    if (!file_exists(PATH_TO_FILES)) die("Directory not found");
    if (($dir = dir(PATH_TO_FILES))) die("Can't open directory");
}
?>
<?php if ($message) echo '<p class="error">' . $message . '</p>'; ?>
<h2>选择一个要编辑的文件：</h2>
<table cellspacing="0" border="0" style="width: 40em; border: 1px solid #666">
    <tr>
        <td>$filename</td>
        <td>$Size (bytes)</td>
        <td>$Last Modified</td>
    </tr>
<?php
while ($filename = $dir->read()) {
    $filepath = PATH_TO_FILES . '/' . $filename;
    if ($filename != "" && $filename != ".." && !is_dir($filepath) &&
        strchr($filename, ".txt") == ".txt") {
        echo '<<tr><td><a href="text_editor.php?filename=' . urlencode($filename) . '">' . $filename . '</a></td>';
        echo '<td>' . filesize($filepath) . '</td>';
        echo '<td>' . date("M j, Y H:i:s", filetime($filepath)) . '</td></tr>';
    }
}
$dir->close();
?>
</table>

### 第三部分：PHP  实战练习

<h2>...或创建一个新文件：</h2>
<form action="text_editor.php" method="post" style="width: 20em;">
<label for="filename">filename</label>
<input type="file" name="filename"><div style="float: right; width: 7%; margin-top: 0.7em;">.txt</div>
<input type="text" name="$filename" id="filename" style="width: 50%;" />
<div style="clear: both;">
<input type="submit" name="createFile" value="Create File" />
</div>
</form>
```php
<?php
function displayEditForm($filename) {
  if ($filename) $filename = basename($_GET["filename"]);
  if (!$filename) die("Invalid filename");
  $filepath = PATH_TO_FILES . "/$filename";
  if (!file_exists($filepath)) die("File not found");
  displayHeader();
}
?>
<h2>编辑 $filename</h2>
<form action="text_editor.php" method="post" style="width: 40em;">
<input type="hidden" name="filename" value="<?php echo $filename ?>" />
<textarea name="fileContents" rows="20" cols="80" style="width: 100%;"><?php echo htmlspecialchars(file_get_contents($filepath)); ?></textarea>
<div style="clear: both;">
<input type="submit" name="saveFile" value="Save File" />
<input type="submit" name="cancel" value="Cancel" style="margin-right: 20px;" />
</div>
</form>
```
<?php
function saveFile() {
  $filename = basename($_POST["filename"]);
  $filepath = PATH_TO_FILES . "/$filename";
  if (file_exists($filepath)) {
    if (file_put_contents($filepath, $_POST["fileContents"]) === false) {
        die("Couldn't save file");
    }
    displayFileList();
  } else {
    die("File not found");
  }
}

function createFile() {
    $filename = basename($_POST["filename"]);
    $filename = preg_replace("/[A-Za-z0-9]/", "", $filename);

    if (!$filename) {
        displayFileList("Invalid filename - please try again");
        return;
    }

    $filename .= ".txt";
    $filepath = PATH_TO_FILES . "$filename";
    if (file_exists($filepath)) {
        displayFileList("The $filename already exists!");
    } else {
        if (file_put_contents($filepath, "") === false) {
            die("Couldn't create file");
        }
        chmod($filepath, 0666);
        displayEditForm($filename);
}

function displayPageHeader() {
?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en">
<head>
    <title>Simple editor</title>
    <link rel="stylesheet" type="text/css" href="common.css" />
    <style type="text/css">
        .error { background: #d33; color: white; padding: 0.2em; }
        th { text-align: left; background-color: #999; }
    </style>
</head>
<body>
<h1>Simple editor</h1>
```

## 测试编辑器

要测试你的文本编辑器，首先在 Web 服务器硬盘上创建一个文件夹来存储文本文件。赋予 Web 服务器在该文件夹中创建文件的权限。在 Linux 和 Mac OS X 上，你可以打开终端窗口，然后切换到父目录并对文本文件夹使用 `chmod` 命令。例如，如果你的文本文件夹是 `/home/matt/sandbox`，你可以输入：

```
$ cd /home/matt
$ chmod 777 sandbox
```

如果你运行的是 Windows 服务器，请参考章节早前的“更改权限”部分了解如何更改权限。不过，在 Windows 上可能不需要更改权限即可运行脚本。

一旦你创建了文本文件文件夹并授予了适当权限，你需要告诉脚本新文件夹的位置。为此，请在脚本顶部设置 `PATH_TO_FILES` 常量：

```php
define( "PATH_TO_FILES", "/home/matt/sandbox" );
```

现在，一切就绪了。在浏览器中打开文本编辑器的 URL，你将看到类似图 11-4 的页面（尽管此阶段不会列出任何文件）。在文本框中输入带有 `.txt` 扩展的新文件名，然后点击“Create File”。你会看到如图 11-5 所示的表单出现；输入文本并点击 File Save 将将更改保存到新文件中。然后你可以点击列表中的文件名再次编辑该文件。

