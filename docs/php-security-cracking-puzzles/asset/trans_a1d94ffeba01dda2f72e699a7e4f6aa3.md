

# 列表 II.5.5. session.php 文件

```php
<?php
// 开启会
function open($save_path, $session_name)
{
    // MySQL 服务器的网络地址
    $dblocation = "localhost";
    // 数据库名称
    $dbname = "boo";
    // 数据库用户
    $dbuser = "root";
    // 用户密码
    $dbpasswd = "";
    // 建立数据库连接
    $dbcnx = mysql_connect($dblocation, $dbuser, $dbpassword);
    if (!$dbcnx) exit(
        ("很遗憾，MySQL 服务器可用：".mysql_error());
    );
    // 选择数据库
    if (!$mysql_select_db($dbname, $dbcnx))
    exit("很遗憾，数据库不可：".mysql_error());

    return true;
}

function close()
{
    // 关闭数据库连接
    mysql_close();

    return true;
}

function read($id)
{
    // 读取 session 值
    $query = "SELECT * FROM session WHERE session = '$id'";
    $ses = mysql_query($query);
    if(!$ses) exit(mysql_error());
    $session = mysql_fetch_array($ses);
    // 返回存入 session 的
    return $session['value'];
}

function write($id, $sess_data)
{
    // 检查此名称的 session
    // 是否已注册
    $query = "SELECT COUNT(*) FROM session WHERE session = '$id'";
    $ses = mysql_query($query);
    if(!$ses) exit(mysql_error());
    if(mysql_result($ses, 0) > 0)
    {
        // 这是第一次尝试访问 session；因此；
        // 有必要在数据库中注册此 session
        $query = "INSERT INTO session
        VALUES (NULL, '$id', NOW(), '$sess_data')";
        $ses = mysql_query($query);
        if(!$ses) exit(mysql_error());
        return true;
    }
}

function destroy($id)
{
    // 删除标识符为 $id 的 session
    $query = "DELETE FROM session WHERE session = '$id'";
    if(!mysql_query($query)) exit(mysql_error());
    return true;
}

function gc($maxlifetime) {
  // “清理垃圾，
  // 或者删除旧记录
  $query = "DELETE FROM session"
  WHERE putdate < NOW() - INTERVAL 20 MINUTE;
  if(!mysql_query($query)) exit(mysql_error());
  return true;
}

session_set_save_handler("open",
"close",
"read",
"write",
"destroy",
"gc");
```

列表 II.5.5 中的文件必须被包含，而不是调用 `session_start()` 函数，如 `index.php` 文件所示（列表 II.5.6）。

# 列表 II.5.6. 使用自定义 session 机制 (index.php)

```php
<?php
include "session.php";
$_SESSION['name'] = "cheops";
?>
<a href="index.php">跳转到另一个页面</a>
```

访问 index.php 文件后，session 表将包含一条记录，其显示可能如列表 II.5.7 所示。

# 列表 II.5.7. session 表中的示例记录

```sql
INSERT INTO session VALUES (1,
  '2de41d571ff0486aeced069309723000',
  '2005-10-28 00:37:35',
  'name|s:6:"cheops";');
```

当页面被访问时，更新字段会不断刷新。通常情况下，使用这种机制与使用存储在文件中普通 session 机制没有区别。index1.php 文件（列表 II.5.8）演示了这一点。

# 列表 II.5.8. index1.php 文件

```php
<?php
include "session.php";
echo "Hello, " .$_SESSION['name'] ."<br>";
?>
<a href="index.php">跳转到另一个页面</a>
```

index1.php 文件脚本产生的结果（见列表 II.5.1）呈在所示。

![](img/a893312ec68b8170fe567f785e95c06e_250_0.png)

图 II.5.1. 使用自定义 session 机制显示欢迎字符串

本节介绍的 session 机制非常有用，因为它在任何时候都提供了访客者列表。此外，可以根据需要自定义 session 表。例如，可以为互联网协议 (IP) 地址、用户状态或由该用户处理的文档添加辅助字段。

## II.5.3. 使用 Session 保护 HTML 表单

如果文档正在使用中，可以拒绝尝试访问它的第二个用户进行访问请求，从而确保数据的一致性和完整性。换句话说，自定义 session 机制有很多应用领域。

当需要保护你网站上的服务免受第三方服务器的访问时，通常必须对 HTML 表单保护。为了实现这一点，有必要将 HTML 表单与 session 关联起来。在 index.php 文件中使用 `session_id()` 函数获取 SID 后，有必要将其放入需要保护的表单的隐藏表单字段中（列表 II.5.9）。

列表 II.5.9. 修正后的 index.php 文件版本

```php
<?php
// 初始化会
session_start();
?>
<table>
<form action=2.php method=post>
<input type=hidden name=session_id value='<?php session_id(); ?>'>
<tr>
<td>姓名：</td>
<td><input type="text" name=name></td>
</tr>
<tr>
<td>密码：</td>
<td><input type="password" name=pass></td>
</tr>
<tr>
<td>&nbsp;</td>
<td><input type="submit" value='进入'></</td>>
</tr>
</form>
</table>
```

此后，HTML 表单会检查从 HTML 表单中获取的 SID 是否与当前值匹配。

## 第 II.5 节：Sessions 和 Cookies

如果连接已建立，可以拒绝尝试访问它的第二个用户进行访问请求，从而确保数据的一致性和完整性。换句话说，自定义 session 机制有很多应用领域。

当需要保护你网站上的服务免受第三方服务器的访问时，通常必须对 HTML 表单保护。为了实现这一点，有必要将 HTML 表单与 session 关联起来。在 index.php 文件中使用 `session_id()` 函数获取 SID 后，有必要将其放入需要保护的表单的隐藏表单字段中（列表 II.5.9）。

如果连接已建立，可以拒绝尝试访问它的第二个用户进行访问请求，从而确保数据的一致性和完整性。换句话说，自定义 session 机制有很多应用领域。

当需要保护你网站上的服务免受第三方服务器的访问时，通常必须对 HTML 表单保护。为了实现这一点，有必要将 HTML 表单与 session 关联起来。在 index.php 文件中使用 `session_id()` 函数获取 SID 后，有必要将其放入需要保护的表单的隐藏表单字段中（列表 II.5.9）。

如果连接已建立，可以拒绝尝试访问它的第二个用户进行访问请求，从而确保数据的一致性和完整性。换句话说，自定义 session 机制有很多应用领域。

当需要保护你网站上的服务免受第三方服务器的访问时，通常必须对 HTML 表单保护。为了实现这一点，有必要将 HTML 表单与 session 关联起来。在 index.php 文件中使用 `session_id()` 函数获取 SID 后，有必要将其放入需要保护的表单的隐藏表单字段中（列表 II.5.9）。

如果连接已建立，可以拒绝尝试访问它的第二个用户进行访问请求，从而确保数据的一致性和完整性。换句话说，自定义 session 机制有很多应用领域。

当需要保护你网站上的服务免受第三方服务器的访问时，通常必须对 HTML 表单保护。为了实现这一点，有必要将 HTML 表单与 session 关联起来。在 index.php 文件中使用 `session_id()` 函数获取 SID 后，有必要将其放入需要保护的表单的隐藏表单字段中（列表 II.5.9）。

如果连接已建立，可以拒绝尝试访问它的第二个用户进行访问请求，从而确保数据的一致性和完整性。换句话说，自定义 session 机制有很多应用领域。

当需要保护你网站上的服务免受第三方服务器的访问时，通常必须对 HTML 表单保护。为了实现这一点，有必要将 HTML 表单与 session 关联起来。在 index.php 文件中使用 `session_id()` 函数获取 SID 后，有必要将其放入需要保护的表单的隐藏表单字段中（列表 II.5.9）。

如果连接已建立，可以拒绝尝试访问它的第二个用户进行访问请求，从而确保数据的一致性和完整性。换句话说，自定义 session 机制有很多应用领域。

当需要保护你网站上的服务免受第三方服务器的访问时，通常必须对 HTML 表单保护。为了实现这一点，有必要将 HTML 表单与 session 关联起来。在 index.php 文件中使用 `session_id()` 函数获取 SID 后，有必要将其放入需要保护的表单的隐藏表单字段中（列表 II.5.9）。

如果连接已建立，可以拒绝尝试访问它的第二个用户进行访问请求，从而确保数据的一致性和完整性。换句话说，自定义 session 机制有很多应用领域。

如果连接已建立，可以拒绝尝试访问它的第二个用户进行访问请求，从而确保数据的一致性和完整性。

它 检查从 HTML 表单中获取的 SID 是否与当前值匹配。

[此处省略重复文本的翻译逻辑]

## II.5.4. 确定 Cookie 状态

*不匹配*当前值。

## II.5.5. 伪造 Cookie

为了伪造 cookie，脚本发送以下 HTTP 请求头：

```
Cookie: name1 = value1; name2 = value2; ...
```

在这里，name1、name2 等是 cookie 名称；value1、value2 等是它们的值。

# 列表 II.5.12. 伪造 cookie 的脚本

```php
<?php
$hostname = "localhost";
$path = "/test/1.php";

// 建立通过 $hostname 参数的连接
$fp = fsockopen($hostname, 80, $errno, $errstr, 30);
// 检查连接是否成功建立
if (!$fp) echo $errstr.<br />\n";
else {
    // 构造传递给服务器的 HTTP头
    $headers = "GET $path HTTP/1.1\r\n";
    $headers .= "Host: $hostname\r\n";
    // 伪造 cookie
    $headers .= "Cookie: name=cheops; admin=1\r\n";
    $headers .= "Connection: Close\r\n\r\n";
    // 向服务器发送 HTTP 查询
    fwrite($fp, $headers);
    // 发送以下响应：while (!feof($fp)) {
        $line = fgets($fp, 1024);
    }
    fclose($fp);
    echo $line;
}
?>
```

