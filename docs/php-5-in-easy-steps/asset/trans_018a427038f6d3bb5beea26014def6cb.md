

# 续

Netscape 和 Mozilla 浏览器拥有非常出色的 Cookie 管理（Cookie Manager）功能，它可以让你轻松查看存储在计算机上的 cookie。这可以用于验证启动 PHP 会话后会 cookie 是否存在。

在 Mozilla 浏览器窗口中，点击 工具（Tools） > Cookie 管理（Cookie Manager） > 管理存储的 Cookie（Manage Stored Cookies），打开 Cookie 管理对话框。当启动 PHP 会话后，PHPSESSID cookie 将出现在存储的 Cookie 列表中

在找到 PHPSESSID cookie 之前，必须先启动会话 - 启动会话

此处显示的 PHPSESSID cookie 中的数据与临时目录中创建的文件匹配：

选择 PHPSESSID cookie 将在对话框的信息（Information）字段中显示其包含的数据，如图所示：

![](img/7faa63a7fa0add8f53300594ebae949f_106_0.png)

![](img/7faa63a7fa0add8f53300594ebae949f_106_1.png)

![](img/7faa63a7fa0add8f53300594ebae949f_106_2.png)

![](img/7faa63a7fa0add8f53300594ebae949f_106_3.png)

8. 数据持久化 | 105

# 启动会话

通过调用 `session_start()` 函数启动 PHP 会话。该函数首先检查是否已经启动了会话，如果当前不存在会话则启动一个。它还会通知 PHP 引擎在此页面将使用会话变量。因此，在页面开头调用 `session_start()` 是明智的。

通过 PHP 的 `$_SESSION[]` 数组引用会话变量，在方括号的引号中插入其名称。例如，`$_SESSION['count']=1` 会初始化一个值为 1 的会话变量“count”。

以下示例使用 `isset()` 函数首先检查某个特定的会话变量已存在。如果不存在，脚本将创建一个名为“count”的会话变量。在会话期间，每次访问页面，count 的值都会加 1。

```php
<?php session_start();
# 启动会话
# 初始化为 1，或在后续访问时递增
if (!isset($_SESSION['count']))
    $_SESSION['count'] = 1; 
else 
    $_SESSION['count']++;
?>
<html>
<head><title>计数访问</title></head>
<body>
<h2>你已经访问过此页面</h2>
<h2><?php echo ($_SESSION['count']); ?>
在会话中已访问过次
</h2>
</body>
</html>
```

![](img/7faa63a7fa0add8f53300594ebae949f_107_0.png)

![](img/7faa63a7fa0add8f53300594ebae949f_107_1.png)

![](img/7faa63a7fa0add8f53300594ebae949f_107_2.png)

当页面首次加载时，“count”变量的值从 0 增加到 1。该变量的名称和值存储在服务器临时目录中的关联文件中。每次重新加载页面，都会从该文件中检索值，将其递增并存储新值。

![](img/7faa63a7fa0add8f53300594ebae949f_108_0.png)

![](img/7faa63a7fa0add8f53300594ebae949f_108_1.png)

![](img/7faa63a7fa0add8f53300594ebae949f_108_2.png)

![](img/7faa63a7fa0add8f53300594ebae949f_108_3.png)

![](img/7faa63a7fa0add8f53300594ebae949f_108_4.png)

![](img/7faa63a7fa0add8f53300594ebae949f_108_5.png)

# 不使用 cookie 的会话

上一页的演示了如何使用 PHPSESSID cookie 来存储会话过程所需的唯一标识符。这似乎与直接在 cookie 中存储和检索数据的功能重复。

然而，还有另一种方法可以让唯一标识符在整个网站中可用，而不需要浏览器接受 cookie。这种方法在指向此网站其他页面的每个超链接 URL 中附加唯一标识符。

这种方法比使用 cookie 更可靠：某些用户倾向于将浏览器设置为拒绝 cookie，这会导致 PHP 脚本的预期功能无法工作。

![](img/7faa63a7fa0add8f53300594ebae949f_109_0.png)

当在 PHPSESSID cookie 中找到唯一标识符时，SID 常量为空。

PHP 有一个名为 SID 的常量，它以键值对的形式包含了唯一会话标识符的详情。此处 PHPSESSID 是键，标识符字符串是值。此值可以简单地添加到超链接的 URL 中。这种操作的语法是 URL 后接问号，然后是 SID：

```html
<a href="target.php?<?php echo $SID; ?>">链接
```

![](img/7faa63a7fa0add8f53300594ebae949f_109_1.png)

在 Netscape/Mozilla 浏览器中，通过 编辑（Edit） > 选项（Preferences） > 隐私与 Cookie（Privacy & Cookies），点击禁用 cookie。当跟随链接时，会话标识符会被发送到目标页面，使会话变量可用。

以下示例在 Windows 上使用 Mozilla 禁用 cookie 比 Internet Explorer 更容易。第一个页面启动会话，并提供一个带有 SID 作为查询字符串的另一个页面的链接。`session_id()` 函数在两个页面上都会显示 SID 的标识符部分。

![](img/7faa63a7fa0add8f53300594ebae949f_109_2.png)

session_start.php
```php
<?php session_start(); ?>
<html>
<head><title>会话启动</title></head>
<body>
<a href="next.php?<?php echo $SID; ?>">下一页</a>
<hr>
<?php session_id(); ?>
</body>
</html>
```

![](img/7faa63a7fa0add8f53300594ebae949f_10_0.png)

# 续

链接的目标页面首先调用 `session_start()` 以继续当前会话，然后增加显示在页面上的会话变量。返回第一个页面的链接附加 SID 以保持会话活跃。在两个页面之间来回会在每个页面上显示唯一标识符，并在第二个页面上显示增加的计数。

```php
<?php session_start();
if (isset($_SESSION['count'])) {
    $_SESSION['count']++;
} else {
    $_SESSION['count'] = 1;
}
?>
<html>
<head><title>会话运行</title></head>
<body>
<a href="session_start.php?<?php echo $SID; ?>">上一页</a>
<hr>
在此会话中已此处 <?php echo $_SESSION['count']; ?> 次
</body>
</html>
```
PHPSESSID = <?php echo session_id(); ?>

![](img/7faa63a7fa0add8f53300594ebae949f_10_2.png)

8. 数据持久化 | 109

# 设置会话偏好

此示例演示了如何使用名为 "font" 的会话变量跨多个页面访问用户选择的偏好。会话 ID 通过 URL 链接传递 SID常量，这样即使禁用了 cookie，也可以从任何页面访问用户的偏好。

```php
<?php session_start();
if ($_POST['font']) {
    $_SESSION['font'] = $_POST['font'];
    header("Location:prefs2.php?" . $SID); 
    exit();
}
?>
<html>
<head><title>会话偏好</title></head>
<body>
<h3>选择你偏好的字体</h3>
<form action="<?php echo $_SERVER['PHP_SELF']; ?>">
<input type="radio" name="font" value="serif"> 衬线
<input type="radio" name="font" value="sans-serif"> 无衬线
<input type="radio" name="font" value="monospace"> 等宽
<input type="radio" name="font" value="cursive"> 字体
<input type="radio" name="font" value="fantasy"> 幻想
<br>
<input type="submit" value="提交">
</form>
</body>
</html>
```

![](img/7faa63a7fa0add8f53300594ebae949f_111_0.png)

注意这些页面中的每一个都通过调用 `session_start()` 开始以便可以使用会话变量。

![](img/7faa63a7fa0add8f53300594ebae949f_111_1.png)

当带有选单单按钮提交此表单时，名为 "font" 的会话获取所选按钮的值，并进行重定向。

| 会话偏好 |
| :--- |
| 文件 编辑 视图 书签 工具 帮助 |
| 选择你偏好的字体族 |
| 衬线 无衬线 等宽 字体 幻想 |
| 提交 |
| 完成 |

![](img/7faa63a7fa0add8f53300594ebae949f_111_2.png)

# 续

```php
<?php session_start(); ?>
<html>
<head><title>会话运行</title></head>
<style type="text/css">
body { font-family:<?php echo $_SESSION['font']; ?>}
</style>
</head>
<body>
偏好的字体族是
<h3><?php echo $_SESSION['font']; ?></h3>
<a href="prefs3.php?<?php echo $SID; ?>">下一页</a>
</body>
</html>
```

![](img/7faa63a7fa0add8f53300594ebae949f_112_0.png)

prefs2.php

此示例中的第二个页面在样式表中分配 `$_SESSION['font']` 变量的值 —— 正体内容以第一个页面选择的字体显示。指向另一个页面的链接再次附加SID常量。

![](img/7faa63a7fa0add8f53300594ebae949f_112_1.png)

会话运行
偏好的字体族是等宽
下一页
http://localhost/pr...9785e129cbd515c94

![](img/7faa63a7fa0add8f53300594ebae949f_112_2.png)

prefs3.php

```php
<?php session_start(); ?>
<html>
<head><title>会话仍在运行</title></head>
<style type="text/css">
body { font-family:<?php echo $_SESSION['font']; ?>}
</style>
</head>
<body>
偏好的字体族仍然是
<h3><?php echo $_SESSION['font']; ?></h3>
<a href="prefs1.php">更改字体？</a>
</body>
</html>
```

![](img/7faa63a7fa0add8f53300594ebae949f_112_3.png)

此示例中的第三个页面在样式表中分配 `$_SESSION['font']` —— 正体内容以第一个页面选择的字体显示。返回第一个页面的链接仅允许选择不同的字体，不附加SID。

