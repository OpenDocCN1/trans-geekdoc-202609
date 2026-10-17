
> Web 应用程序构建为将 HTML 表单及其处理器包含在同一个文件中。然而，也可以将 HTML 表单和处理器放在不同的文件中。

## 列表 II.3.1. 上传不受数量限制的文件

```html
<form enctype='multipart/form-data' method=post>
<table>
<tr>
<td><input type="file" size="50" name="att[]" class="input"></td></td>td>
<td><input type="button" name="drop"
value="&amp;" onclick="dropFile(this);">
<input type="button" value=" + " onclick="addFile(this);"></td></td>
</tr>
</table>
<input class="button" type=submit value='Upload'>
</form>
<script language='Javascript.1' type='text/javascript'>
<!--
function dropFile(btn)
{
 if(document.getElementById)
{
    while (btn.tagName != 'TR') btn = btn.parentNode;
    btn.parentNode.removeChild(btn);
 }
}
function addFile(btn)
{
 if(document.getElementById)
{
    while (btn.tagName != 'TR') btn = btn.parentNode;
    var newTr = btn.parentNode.insertBefore(btn.cloneNode(true),
    btn.nextSibling);
    thisChildren = newTr.getElementsByTagName('td');
    for (var i = 0; i < thisChildren.length; i++)
    {
        if (thisChildren[i].className == 'files')
        thisChildren[i].innerHTML='<input size="32" name="att[]"
        class="input" type="file">';
    }
 }
n-->
</script>
<?php
// HTML 表单处理器
// 上传所有文件
for($i = 0; $i < count($_FILES['att']['name']); $i++)
{
```
```php
// 将文件从临时目录移动到
// Web 应用程序的 files 子目录
if (copy($_FILES['att']]['tmp_name'][$i])) {
    unlink("files/" . $_FILES['att']['name'][$i]);
}

} else
{
    // 删除临时目录中的文件
    unlink($_FILES['att']]['tmp_name'][$i]);
    // 修改文件的访问权限
    chmod("files/" . $_FILES['att']['name'][$i], 0644);
}
}
```
```php
// 如果 $POST 全局数组
// 不为空，则自动重新加载页面
if(!empty($_POST)) {
```
```php
echo "HTML<HEAD>
<META HTTP-EQUIV = 'Refresh' CONTENT = '0; URL = " . $_SERVER['PHP_SELF'] . '\'>
</HEAD>HTML";
}
```

`enctype` 属性决定了表单的编码方式，默认值为 `application/x-www-form-urlencoded`。为了文件上传工作，其值必须设置为 `multipart/form-data`。`enctype` 属性允许 PHP 源代码在浏览器窗口中显示时，保留其原始格式。

`copy()` 函数将文件从临时目录移动到 Web 应用程序的 `files` 子目录。`unlink()` 函数删除了临时目录中的文件。`chmod()` 修改了文件的访问权限。

如果 `$POST` 全局数组不为空，则自动重新加载页面。

# 第 II.3 章：文件操作

![](img/a893312ec68b8170fe567f785e95c06e_162_0.png)

图 II.3.1. 编辑 upload.php 文件

现在，为了清除你在入侵期间留下的痕迹，你所做的就是重新上传并运行 `upload.php` 文件：服务器上既不会留下 `upload.php` 文件留下 `1.php` 文件。

除了结构化查询语言（SQL）注入外，这是最常见的入侵技术，常见于论坛、聊天室、相册或任何允许用户向服务器上传文件的 Web 应用程序。

防止此类入侵的最佳方法是对比加载文件实施一刀切的禁止，然后只允许上传特定类型的文件。这种防御可以通过使用如列表 II.3.3 所示的脚本分析文件扩展名来实现。

### II.3.3. 保护脚本

```php
<form enctype='multipart/form-data' method=post>
<input type="file" size="32" name="filename"><br>
<input class="button" type=submit value='Upload'>
</form>
```

## 第 II 部分：解决方案

```php
<?php
// HTML 表单处理器
if(!empty($_FILES['filename']['tmp_name']))
{
    // 提取文件的扩展名
    $ext = strtolower(strrchr($_FILES['filename']['name'], "."));
    // 仅允许上传特定
    // 格式的文件
    $extensions = array(".jpg", ".gif");
    // 检查文件的扩展名是否与
    // 允许的扩展名列表匹配
    if(in_array($ext, $extensions)) {
        // 将文件保存到当前目录
        if(copy($_FILES['filename']['tmp_name'],
            $_FILES['filename']['name'])) {
            echo "File upload successful: <a href=" .
                $_FILES['filename']['name'] . ">" .
                $_FILES['filename']['name'] . "</a>";
        }
    } else {
        // 文件的扩展名不在允许列表中。
        echo "Only images can be uploaded!";
    }
}
?>
```

文件 `$file` 上传到服务器后，脚本会提取其扩展名并将其放入 `$ext` 变量中。允许上传的文件扩展名存储在 `$extensions` 数组中。如果上传文件的扩展名与 `$extensions` 数组中存储的某个匹配，则将文件从临时目录复制到目标目录。否则，文件将被忽略。

虽然可以通过更改扩展名（例如改为 `.gif`）来上传恶意脚本，但一旦上传，它就无法被执行。要执行此类扩展名的文件，必须将该扩展名与解释器关联，而这是无法实现的。

## 第 II.3 章：文件操作 151

验证上传文件的另一种方法是检查存储在 `$_FILES['filename']['type']` 数组元素中的文件类型。对于上传的图形文件，`image/gif`、`image/jpeg` 等值会被放入此数组元素中，而 `text/plain` 值则用于 PHP 和 HTML 文件。如果只允许上传图形文件，可以使用类似于列表 II.3.4 所示的脚本通过检查此数组元素来验证它们的有效性。

### II.3.4. 使用 `$_FILES['filename']['type']` 数组元素验证文件

然而，仅允许少数文件格式并不总是足够的。例如，论坛要求用户能够上传所有类型的文件。在这种情况下，必须将可执行文件的扩展名更改为无害的 .txt 扩展名。

## 第 II 部分：解决方案

此任务通过创建一个数组来存储必须更改为 .txt 扩展的文件扩展名列表完成（列表 II.3.5）。

### II.3.5. 将危险的文件扩展名更改为 .txt 扩展

```php
<form enctype='multipart/form-data' method=post>
<input type="file" size="32" name="filename"><br>
<input class="button" type="submit" value='Upload'>
</form>
<?php
// HTML 表单处理器
if(!empty($_FILES['filename']['tmp_name'])) {
    // 提取文件的扩展名
    $ext = strtolower(strrchr($_FILES['filename']['name'], ".
```

## II.3.4. 下载计数器

所有的下载计数器都基于这样一个原理：给用户的链接不是指向文件本身，而是指向一个记录下载并将文件发送给用户的脚本链接。

用于解决所提问题（计算文件下载次数）的脚本构造如下：下载文件的链接被实现为指向当前页面的链接，并将文件名作为参数传递：例如 `index.php?down=archive.zip`。脚本检查是否传递了 `down` 参数，如果是，则在 `filecount.txt` 文件中记录下载。每当页面加载时，每个存档的计数值都会从该文件中提取并显示在浏览器窗口中。通过向用户发送一个命名的 HTTP 头部（该头部包含下载存档的链接）来提供请求的文件进行下载。实际的文件下载脚本可能类似于列表 II.3.6 所示。

> 注意：在文件中存储工业和大型系统的统计信息更为方便。

### II.3.6. 文件下载计数器

```php
<?php
// 在数组中注册文件名
$file_name = array('archive1.zip', 'archive2.zip', 'archive3.zip');

// 存储统计信息的文件
$countname = "filecount.txt";
// 如果文件存在，将当前的
// 统计数据读入数组。
if (file_exists($countname)) {
    $fd = fopen($countname, "r");
    $content = fread($fd, filesize($countname));
    fclose($fd);
    // 反序列化数组
    $count = unserialize($content);
}
```
```php
}
// 如果文件不存在，则创建
// 它并将统计数据清零
else {
    // 将 $count 数组清零
    foreach ($file_name as $file) {
        $count[$file] = 0;
    }
    // 创建统计文件
    $fd = fopen($countname, "w");
    // 序列化数组
    fwrite($fd, serialize($count));
    fclose($fd);
}

// 使用 GET 方法检查是否传递了
// down 参数
if(isset($_GET['down'])) {
    // 检查 GET['down'] 是否在
    // $file_name 数组中
    if(in_array($_GET['down'], $file_name)) {
        // 记录下载
        // 递增 GET['down'] 的值
        $count[$GET['down']]++;
        // 更新计数文件
        $fd = fopen($countname, "w");
        // 序列化数组
        fwrite($fd, serialize($count));
        fclose($fd);
    }
    // 提供下载文件的链接
    header("Location: " . $_GET['down']);
}

// 显示文件的链接
```

## 第 II.3 章：文件操作 155

```php
foreach($file_name as $file) {
  echo "File <a href=" . $_SERVER['PHP_SELF'] . "?down=" . $file . ">$file</a> has been downloaded " . $count[$file] . " time(s).<br>";
} ?>
```

下载的文件名存储在 `$file_name` 数组中；当添加新的下载存档时，它会自动注册到系统中。提前注册有几个原因：首先，当通过 `down` 参数传递时，必须检查它是否允许下载。其次，处理数组比单独处理文件要容易得多。因此，存储文件下载次数的 $count 数组会自动创建。为了方便，使用 `serialize()` 函数将 $count 数组转换为字节流表示字符串，并使用 `unserialize()` 函数还原值。

> 请记住所有的头部只能在发送正文之前发送。以不同的顺序发送是不可能的；PHP 解释器将发出以下警告信息：“Warning: Cannot modify header information— already sent by。”这是因为 HTTP 先发送头部，然后发送文档内容。因此，任何到浏览器窗口的初始输出都被解释为带有预期正文的头部。如果无法在发送缓冲区之前发送内容，可以使用输出控制函数将输出放入缓冲区，并在脚本执行结束将其发送浏览器窗口。

当脚本第一次运行时，`filecount.txt` 文件不存在。它在第一次加载页面时创建。创建过程是由 $file_name 中每个文件的 0 值启动的。

## II.5. 保存文本和图形文件

浏览器只有在知道内容时才能解释文件。浏览器从服务器学习文件内容，因为每个文件都附带 HTTP 头部，告知客户端文件内容、大小以及其他服务信息（例如需要设置 cookie）。如果文件类型未知，则将以二进制流的形式发送。

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
