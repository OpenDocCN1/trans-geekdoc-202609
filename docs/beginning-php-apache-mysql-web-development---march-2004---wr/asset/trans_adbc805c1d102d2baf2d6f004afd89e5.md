

# URL 中的特殊字符

如果变量值中包含空格、安培符号或其他特殊字符，通过 URL 传递变量就会产生一个有趣的问题。幸运的是，有特殊字符的替代方案，可以保持变量值的完整性。在通过 URL 传递这些值时，有一个特殊的函数叫做 urlencode()。如果你想将你最喜欢的电影从《条纹军》（Stripes）改为《布莱恩的生活》（Life of Brian），你将使用 urlencode() 对值进行编码并插入正确的 HTML 特殊字符。

要尝试此操作，请执行以下步骤：

- 1. 在你的 movie.php 文件中添加以下行：
`$myfavmovieurlencode = urlencode("Life of Brian");`

- 2. 修改此行：
`echo "<a href='http://localhost/movies.php?favmovie=$myfavmovie'>";`

- 3. 保存文件并在浏览器中重新打开。现在点击链接将显示图 2-8 所示的页面。

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_73_0.png)

图 2-8

# 第 2 章

# 通过 Session 传递

如之前提到的，如果信息不是特别敏感，或者它是相对静态的，并且没有用户从之前保存的页面调出旧信息的危险，那么通过 URL 传递值是可以的。然而，如果你正在传输用户名或密码，或者地址和电话号码等个人信息，有更好的方法可以在保持私密性的同时传递信息。

# 什么是 Session？

Session 基本上是一组临时变量，它们只存在到浏览器关闭为止（除非你在 php.ini 文件中设置了它，那是另一个故事了）。Session 信息示例包括 session ID 以及授权人员是否登录网站。这些信息被临时存储，以便你的 PHP 程序在需要时随时引用。

每个 session 都被分配一个唯一的 ID，将所有当前信息保持在一起。你的 session ID 可以通过 URL 传递，也可以通过使用 cookie 使用。出于安全考虑，最好通过 cookie 传递 session ID，这样它可以对肉眼不可见；如果没有启用 cookie，备用方法是通过 URL。

这是在你的 php.ini 文件中确定的。如果你想强制用户通过 cookie 传递变量（而不是允许备用方案），你可以在文件中设置以下行：

```
session.use_only_cookies = 1
```

要启动 session，请使用函数 session_start()。由于我们将 register_globals 设置为 "off"，所以你不应该使用在其他 PHP 脚本中看到的 session_register() 函数。在使用之前，请确保你的 php.ini 文件已修改，并在网站中显示有效路径 session.save_path 变量，如第 1 章所述。

首先，你需要决定在 session 中存储哪些信息。存储在数据库中的任何内容都可以通过你的 session 信息检索并临时存储。通常，它是用户名和登录信息等内容，也可以是用户某些时候设置的偏。SID（session ID）将存储在 session 数组中。

# 尝试传递访问者的用户名

假设你想在第一页和第二页之间传递访问者的用户名以及他/她是否真实登录了网站。由于在本章的晚些部分才会讨论表单的使用，我们现在先获取它。

遵循以下步骤：

- 修改你的 motel.php 文件以包含以下行（加粗显示）。

```php
<?php
session_start();
$_SESSION['username'] = "Joe12345";
$_SESSION['autuser'] = 1;
```

# 创建 PHP 页面

```php
<?php
<HTML>
<HEAD>
<TITLE>寻找我最喜欢的电影！</TITLE>
</HEAD>
<body
<?php
$favmovie = urlencode('Life of Brian');
echo '<a href="http://localhost/moviesite.php?favmovie=$favmovie">';
echo '点击此处查看我最喜欢的电影信息！';
echo '</a>';
?>
</body>
</HTML>
```

2. 现在保存你的 moviel.php 文件。

3. 打开 moviesite.php 进行以下更改（加粗显示）。

```php
<?php
session_start();
//检查用户是否已使用有效密码登录
if ($_SESSION['autuser'] != 1) {
echo '抱歉，你没有权限查看此页面，你这个失败者！';
exit();
}
?>
<HTML>
<HEAD>
<TITLE>我的电影网站 - <?php echo $_REQUEST['favmovie'] ?></TITLE>
</HEAD>
<body>
<?php
echo "欢迎来到我们的网站，* ";
echo $_SESSION['username'];
echo "<br>";
echo "我最喜欢的电影是 ";
echo $_REQUEST['favmovie'];
echo "<br>";
$smovate = 5;
echo "这部电影的评分是：";
echo $smovate;
?>
?>
```

4. 点击 moviel.php 中的链接，你应该看到图 2-9 所示的 moviesite.php。

# 第 2 章

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_76_0.png)

图 2-9

# 工作原理

有几点需要注意：

- Session 单独存储信息持续到浏览器关闭。就像一个掉电就会丢失高分数的视频游戏，一旦浏览器关闭，所有 session 信息都会丢失。
- 另一方面，Cookie 可以在人的计算机上生存直到开发者认为时间足够为止。正因为这种持久性，Cookie 非常适合存储用户名或语言偏好。这些是用户每次访问你的网站时不需要重复的信息。

我们之前提到过 session 单独存储的时间很短。然而，如果我们结合使用 cookie，我们就可以更改此限制。如果你的 session 使用 cookie，你可以通过 php.ini 中的 session.cookie_lifetime 配置将 cookie 的寿命设置得比浏览器长。但请记住，不仅 session 信息会存储在人的计算机上；session ID 将被存储，并在以后引起问题。

# 什么是 Cookie？

Cookie 是存储在你的计算机上的微小信息。虽然 Cookie 主要用于存储用户名，但它们也存在安全风险。有关 Cookie 的更多信息，鼓励你访问 W3 安全网站 www.w3.org/Security/faq。

要设置 cookie，请使用相应的 setcookie() 函数。在设置 cookie 时，你可以确定以下信息：

- Cookie 名称（强制性）。
- Cookie 值（例如用户名）。
- Cookie 过期的秒数。（基于 Unix 时间戳，你可以使用以下语法设置：time()+60*60*24*365 可让 cookie 保存一年。这是可选的，但如果不设置，cookie 将浏览器关闭时过期。）
- 路径（保存 cookie 的目录——通常足够；这是可选的）。
- 域名（可以访问此 cookie 的域名——这是可选的）。
- Cookie 是否必须通过安全连接进行访问（默认为 0；启用此功能将其设置为 1）。

