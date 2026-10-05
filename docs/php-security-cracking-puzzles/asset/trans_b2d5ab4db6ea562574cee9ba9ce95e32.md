

## 第 II.3 节：与文件操作

## 列表 II.3.37. 删除当前目录下的文件

为了防止此类情况发生，必须将角括号转换为 HTML 实体（例如将 `<` 转换为 `&lt;` 将 `>` 转换为 `&gt;`），可以使用 `htmlspecialchars()` 函数来实现（列表 II.3.38）。

## 列表 II.3.38. 过滤用户输入

```php
<?php
// 表单处理器
if(empty($_POST['name']) && empty($_POST['msg']))
{
    $_POST['name'] = htmlspecialchars($_POST['name']);
    $_POST['msg'] = htmlspecialchars($_POST['msg']);
    $Smsg = "<tr><td>".$$_POST['name']."</td></tr>\n";
    $Smsg .= "<tr><td>".$$_POST['msg']."</td></tr>\n";
}
// 打开文件并添加新记录
$fd = fopen("msg.txt", "a");
if($fd)
{
    fwrite($fd,$Smsg);
    fclose($fd);
}
// 输出已添加到文本文件的消息
echo "<table>";

?>
```

186 页 第二部分：解决方案

如果实施了此项保护措施，在消息正文中输入 JavaScript 或 PHP 脚本将只会作为普通文本显示在浏览器窗口中（图 II.3.3）。

![](img/a893312ec68b8170fe567f785e95c06e_199_0.png)

图 II.3.3. 将角括号转换为其 HTML 实体

## 第 II.4 节：MySQL 与 SQL 注入

![](img/a893312ec68b8170fe567f785e95c06e_200_0.png)

### II.4.1. 注册新用户系统

组织注册系统涉及为用户提供一个 HTML 表单以输入所需信息。输入信息后，将检查其是否符合要求。最后，检查给定的用户名是否已被占用，如果未被，则将新用户添加到数据库。列表 II.4.1 显示了一个用于执行所有这些过程的脚本示例。

列表 II.4.1. 在数据库中注册新用户

```html
<table>
<form method="post">
<tr><<td>>Name:</td><td><input type="text" name="name"></td></tr>
<tr><<td>>Password:</td><td><input type="password" name="pass"></td></tr>
<tr><<td>>Confirm password:</td><td><input type="password" name="pass_again"></td></tr>
<tr><<td>>email:</td><td><input type="text" name="email"></td></tr>
<tr><<td>>URL:</td><td><input type="text" name="url"></td></tr>
<tr><td></td><td><input type="submit" value='Register'></td></tr>
</form>
</table>
```

```php
<?php
// HTML 表单处理器

//////////////////////////////////////////////////////////////////////
// 数据验证块
//////////////////////////////////////////////////////////////////////
// 去除多余空格
$_POST['name'] = trim($_POST['name']);
$_POST['pass'] = trim($_POST['pass']);
$_POST['pass_again'] = trim($_POST['pass_again']);
// 检查 $_POST 数组是否为空
if(empty($_POST['name'])) exit();
// 检查必需字段是否正确填写
if(empty($_POST['name'])) exit(' "Name" 字段未填写!');
if(empty($_POST['pass'])) exit('两个 "Password" 字段都必须填写!');
if(empty($_POST['pass_again'])) exit('两个 "Password" 字段都必须填写!');
if($_POST['pass'] != $_POST['pass_again']) exit('密码不匹配！');
// 如果提供了电子邮箱地址，检查其格式
if(empty($_POST['email'])) {
    if(!preg_match('/^[0-9a-z._%+-]+@[0-9a-z._-]+\.[a-z]{2,6}$/i', $_POST['email'])) {
        exit(' "email" 地址格式必须符合 somebody@somewhere.com 格式。');
    }
}
// 如果服务器未开启魔幻引用（magic quotes）
// 使用 mysql_escape_string() 函数处理输入数据
if (!get_magic_quotes_gpc()) {
    $_POST['name'] = mysql_escape_string($_POST['name']);
    $_POST['pass'] = mysql_escape_string($_POST['pass']);
    $_POST['email'] = mysql_escape_string($_POST['email']);
    $_POST['url'] = mysql_escape_string($_POST['url']);
}
```

## 第 II.4 节：MySQL 与 SQL 注入

```php
//////////////////////////////////////////////////////////////////////
// 检查用户名是否已占用的块
//////////////////////////////////////////////////////////////////////
// 连接数据库
require_once("config.php");
// 检查提供的
// 名称是否已在使用
$query = "SELECT COUNT(*) FROM userslist WHERE name = '" . $_POST['name'] . "';";
$usr = mysql_query($query);
if(!$usr) exit("错误 - " . mysql_error());
$total = mysql_result($usr, 0);
if ($total > 0) { exit("该用户名已被占用"); }
//////////////////////////////////////////////////////////////////////
// 插入新用户
//////////////////////////////////////////////////////////////////////
// 构造 SQL 查询
$query = "INSERT INTO userslist
    VALUES (NULL,
    '" . $_POST['name'] . "',
    '" . $_POST['pass'] . "',
    '" . $_POST['email'] . "',
    '" . $_POST['url'] . "')";
// 执行查询
if(mysql_query($query)) {
    // 注册成功
    echo "注册成功！";
} else {
    // 输出错误
    exit("注册失败: " . mysql_error());
}
```

