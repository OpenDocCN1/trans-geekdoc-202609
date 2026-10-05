
# 278 第二部分：解决方案

```php
function generate_password($number)
{
    $arr = array('a', 'b', 'c', 'd', 'e', 'f', 'g',
        'h', 'i', 'j', 'k', 'l', 'm', 'n',
        'o', 'p', 'q', 'r', 's', 't', 'u',
        'v', 'w', 'x', 'y', 'z',
        'A', 'B', 'C', 'D', 'E', 'F', 'G',
        'H', 'I', 'J', 'K', 'L', 'M', 'N',
        'O', 'P', 'Q', 'R', 'S', 'T', 'U',
        'V', 'W', 'X', 'Y', 'Z',
        '1', '2', '3', '4', '5', '6',
        '7', '8', '9', '0',
        '!', '@', '#', '$', '%', '&', '*', '?',
        '<', '>', '/', '\', '|', '+', '-', '~');

    // 生成一个密码
    $pass = "";
    for($i = 0; $i < $number; $i++) {
        // 生成一个随机数组元素
        $index = rand(0, count($arr) - 1);
        $pass .= $arr[$index];
    }
    return $pass;
}
?>
```

## II.7.6. 防止文本文件在浏览器中查看

通过创建列表 II.7.11 所示的 .htaccess 文件，可以阻止文本文件在浏览器中显示。

### 列表 II.7.11. .htaccess 文件

```apache
<Files "*.txt">
    deny from all
</Files>
```

# II.7 章：授权与身份验证 279

Files 中的 *.txt 掩码禁止从所有 IP 地址查看文本文件。尽管如此，PHP 脚本仍然能够处理文本文件工作。

## II.7.7. 基于 Cookie 的授权

授权脚本的问题在于授权只发生一次；在后续所有页面中只检查带有用户名的 cookie。这使得伪造 cookie 变得非常容易，可以使用浏览器（例如 Opera，它具有 cookie 编辑功能）或通过程序化方式实现。在系统中注册一个用户（假设用户名为 barton）并通过授权程序会在客户端机器上安装一个 cookie（图 II.7.7）。

![](img/a893312ec68b8170fe567f785e95c06e_292_0.png)

图 II.7.7. 登录系统

之后，可以在 Opera 浏览器中将 cookie 的名称更改为系统中注册的任何名称（图 II.7.8）。

有许多具有 cookie 编辑功能的程序和浏览器。然而，Internet Explorer 并不是其中之一。

> 注意

这使得属于伪造 cookie 中用户名的用户（在本例中为 yandex）的所有的数据可以被攻击者访问（图 II.7.9）。

除了让攻击者能够访问其他用户的权限外，伪造的 cookie 还让获取该用户的密码变得非常简单，因为查询用户个人数据的 SQL 查询不会检查通过 cookie 发送的用户名。回想列表-II.7.12 所示的 userslist 表结构。

![](img/a893312ec68b8170fe567f785e95c06e_293_0.png)

图 II.7.8. 在 Opera 浏览器中更改 cookie 信息

![](img/a893312ec68b8170fe567f785e95c06e_293_1.png)

图 II.7.9. 访问另一个用户的数据

# II.7 章：授权与身份验证

列表 II.7.12. userslist 表的结构

```sql
CREATE TABLE userslist (
  id int(11) NOT NULL auto_increment,
  name tinytext NOT NULL,
  pass tinytext NOT NULL,
  email tinytext NOT NULL,
  url tinytext NOT NULL,
  PRIMARY KEY (id)
  TYPE=MyISAM;
```

用于显示用户密码的 SQL 注入可能列表 II.7.13 所示。

### 列表 II.7.13. 在浏览器窗口中显示密码的 SQL 注入

```sql
SELECT * FROM userslist
WHERE name = 'none'
UNION
SELECT id, name, pass, pass, url FROM userslist
WHERE name = 'yandex'
```

将用户名替换为加粗字符串将导致显示 yandex 用户的密码而不是电子邮箱（图 II.7.10）。

![](img/a893312ec68b8170fe567f785e95c06e_294_0.png)

**图 II.7.10.** 使用 SQL 注入获取用户密码

这个示例再次证明，来自客户端机器的任何数据都是不可信任的，包括服务器端使用用户据理上不应该熟悉的机制所设置的数据：一切都是可以伪造的，而且早晚会发生。外面的不分分子远比你想象的要多，种类也更多。即使你认为你的个人网站对黑客没有吸引力，而且你不需要——

> 注意

# 第二部分：解决方案

担心保护它，它早晚会被破解的，即使是出于某些初级黑客的练习。

使用浏览器进行这种侵入非常有趣，但许多用户手头没有方便使用的必要的 cookie 编辑工具。在这种情况下，可以使用套接字向服务器发送以下伪造的 HTTP 头来编辑 cookie：

Cookie: user = user_name;

在这里，用户名是用户 cookie 将接收的值。Cookie 值必须通过 `urlencode()` 函数处理，以剔除任何国家和特殊字符，这些字符在 HTTP 头中是不被允许的。使用 HTTP 头实现 SQL 注入的脚本如列表 II.7.14 所示。

### 列表 II.7.14. 使用 HTTP 头伪造 cookie

```php
<?php
$hostname = "localhost";
$path = "/test.php";
$sql = "SELECT id, name, pass, pass, url FROM userslist WHERE name = 'yandex'";

// 生成一个密码
    $pass = "";
    for($i = 0; $i < $number; $i++) {
        // 生成一个随机数组元素
        $index = rand(0, count($arr) - 1);
        $pass .= $arr[$index];
    }
    return $pass;
}
?>
```

// 建立连接
    $fp = fsockopen($hostname, 80, $errno, $errstr, 30);
if (!$fp) {
    echo $errstr;
} else {
    // 构建头部
    $headers = "GET $path HTTP/1.1\r\n";
    $headers .= "Host: $hostname\r\n";
    // 伪造 cookie
    $headers .= "Cookie=" . urlencode($user_name) . "\r\n";
    $headers .= "Connection: close\r\n";
    // 向服务器发送请求
    fwrite($fp, $headers);
    // 接收服务器的回复
    $line = "";
    while (!feof($fp)) {
      $line .= fgets($fp, 1024);
    }
    fclose($fp);
    echo $line;
}
?>
```

你应该注意列表 II.7.11 中提到的 $path。

![](img/a893312ec68b8170fe567f785e95c06e_296_0.png)

图 II.7.11. 执行 SQL

因此，将密码存储在 cookie 中是不够的；而且，用户每次尝试访问限制的服务时都应该经过授权程序。

# 284 第二部分：解决方案

# 列表 II.7.15  修改后的脚本

```php
<?php
// 如果用户成功授权，
// 输出问候
if(isset($_COOKIE['user']))
{
    // 连接数据库
    require_once("config.php");
    // 使用 escape_string() 函数处理提供的密码和登录
    // 以防止 SQL 注入

    if (!get_magic_quotes_gpc()) {
        $_COOKIE['user'] = mysql_escape_string($_COOKIE['user']);
        $_COOKIE['pass'] = mysql_escape_string($_COOKIE['pass']);
    }
    // 查询符合登录和密码标准的记录数
    $query = "SELECT COUNT(*) FROM userslist WHERE name = '$_COOKIE[user]' AND pass = '$_COOKIE[pass]''";
    $usr = mysql_query($query);
    if (!$usr) exit("授权错误!");
    // 获取记录数
    $total = mysql_result($usr,0);
    if($total > 0)
    {
        // 输出问候
        echo "Hello, "$_COOKIE['user']."<br>";
        echo "这是你的机密数据。<br>";
        // 显示用户数据
        $query = "SELECT * FROM userslist WHERE name = '$_COOKIE[user]'";
        $usr = mysql_query($query);
        if(!$usr) exit(mysql_error());
    }
}
?>
```

```<?php
// 刷新页面以重置 POST 数据
echo "<HTML><HEAD><META HTTP-EQUIV='Refresh';0; URL=";
```

```html
<form>
value = '<?php = $_COOKIE['user']; ?>'><br>
密码：<input type=password name=password value='><br>
<input type=submit value=发送>
</form>
<?php
```
