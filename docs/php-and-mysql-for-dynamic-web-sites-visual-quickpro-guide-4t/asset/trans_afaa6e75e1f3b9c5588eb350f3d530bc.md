
为了演示这些信息，我们给登录 Cookie 添加一个过期设置，使其仅持续一小时。

#### 设置 Cookie 的参数

**1.** 在文本编辑器中打开 `login.php`（参考 [脚本 12.3](#ch12.html#ch12ex03)），如果尚未打开的话。

**2.** 修改两行 `setcookie()` 代码，加入一个 60 分钟后过期的过期日期（[脚本 12.5](#ch12.html#ch12ex05)）：

```
setcookie ('user_id', $data['user_id'], time()+3600, '/', '', 0, 0);

setcookie ('first_name', $data['first_name'], time()+3600, '/', '', 0, 0);
```

将过期日期设为 `time() + 3600`（60 分钟乘以 60 秒）后，Cookie 将在设置后继续存在一小时。在进行此更改时，其他每个参数都被显式指定了。

对于最后一个参数（接受布尔值），你也可以用 0 代表 FALSE（PHP 会为你处理转换）。这样做是个好主意，因为在任何 Cookie 参数中使用 `false` 都可能导致问题。

**3.** 保存脚本，将其放入你的 Web 目录，并在 Web 浏览器中通过登录进行测试 ![Image](graphics/circle-g.jpg)。

![Image](graphics/12_figure_12_g.jpg)

![Image](graphics/circle-g.jpg)对 `setcookie()` 参数的更改（如过期日期和时间）将反映在发送给 Web 浏览器的 Cookie 中（与 ![Image](graphics/graycircle-f.jpg) 对比）。

***

提示

某些浏览器在处理未列出所有参数的 Cookie 时会有困难。显式声明每个参数——即使是空字符串——将在所有浏览器中获得更可靠的结果。

***

提示

以下是关于 Cookie 过期的一些通用准则：如果 Cookie 应在用户会话期间一直有效，则不要设置过期时间；如果 Cookie 应在用户关闭并重新打开浏览器后继续存在，则将过期时间设为几周或几个月后；如果 Cookie 可能构成安全风险，则将过期时间设为一小时或更短，以便用户离开浏览器后 Cookie 不会存在过长时间。

***

提示

出于安全目的，你可以将 Cookie 的过期时间设为 5 或 10 分钟，并在用户访问的每个新页面上重新发送该 Cookie（假设 Cookie 存在）。这样，只要用户保持活跃，Cookie 就会持续存在，但在用户最后一次操作后 5 或 10 分钟会自动失效。

***

提示

电子商务和其他涉及隐私的 Web 应用程序应对所有事务（包括 Cookie）使用 SSL（安全套接字层）连接。

***

提示

要小心由目录中的脚本创建的 Cookie。如果未指定路径，则该 Cookie 将仅对该同一目录中的其他脚本可用。

***

#### 删除 Cookie

关于使用 Cookie 最后需要了解的是如何删除一个。虽然 Cookie 会在用户关闭浏览器或达到过期日期/时间时自动过期，但通常你会想手动删除 Cookie。例如，在具有登录功能的网站中，你会希望在用户注销时删除所有 Cookie。

虽然 `setcookie()` 函数最多可接受七个参数，但实际只需要一个——Cookie 名称。如果你发送一个仅包含名称而无值的 Cookie，其效果等同于删除同名的现有 Cookie。例如，要创建 `first_name` Cookie，你可以使用这行代码：

```
setcookie('first_name', 'Tyler');
```

要删除 `first_name` Cookie，你可以编写：

```
setcookie('first_name');
```

作为额外的预防措施，你也可以设置一个过去的过期日期：

```
setcookie('first_name', '', time()-3600);
```

为了演示所有这些，我们给网站添加注销功能。注销页面的链接位于 `loggedin.php` 中。

作为一项额外功能，将修改页头文件，以便在用户登录时显示*注销*链接，在用户注销时显示*登录*链接。

#### 删除 Cookie 的步骤

**1.** 在文本编辑器或 IDE 中新建一个 PHP 文档，命名为 `logout.php`（[脚本 12.6](#ch12.html#ch12ex06)）：

```
<?php # Script 12.6 - logout.php
```

**2.** 检查 `user_id` Cookie 是否存在；如果不存在，重定向用户：

```
if (!isset($_COOKIE['user_id'])) {

  require ('includes/login_functions.inc.php');
  redirect_user();
```

**脚本 12.6.** `logout.php` 脚本删除先前建立的 Cookie。

***

```
1  <?php # Script 12.6 - logout.php
2  // This page lets the user logout.
3
4  // If no cookie is present, redirect the
    user:
5  if (!isset($_COOKIE['user_id'])) {
6
7      // Need the function:
8      require ('includes/login_functions.
        inc.php');
9      redirect_user();
10
11  } else { // Delete the cookies:
12      setcookie ('user_id', '', time()-3600,
          '/', '', 0, 0);
13      setcookie ('first_name', '',
          time()-3600, '/', '', 0, 0);
14  }
15
16  // Set the page title and include the
    HTML header:
17  $page_title = 'Logged Out!';
18  include ('includes/header.html');
19
20  // Print a customized message:
21  echo "<h1>Logged Out!</h1>
22  <p>You are now logged out, {$_COOKIE
      ['first_name']}!</p>";
23

24  include ('includes/footer.html');
25  ?>
```

***

与 `loggedin.php` 一样，如果用户尚未登录，此页面应将用户重定向到主页。尝试注销一个未登录的用户是毫无意义的！

**3.** 如果 Cookie 存在则将其删除：

```
} else {
  setcookie ('user_id', '', time()-3600, '/', '', 0, 0);
  setcookie ('first_name', '', time()-3600, '/', '', 0, 0);
}
```

如果用户已登录，这两个 Cookie 将有效地删除现有的 Cookie。除值和过期时间外，其他参数的值应与创建 Cookie 时相同。

**4.** 完成 PHP 页面的其余部分：

```
$page_title = 'Logged Out!';
include ('includes/header.html');
echo "<h1>Logged Out!</h1>
<p>You are now logged out, {$_COOKIE['first_name']}!</p>";
include ('includes/footer.html');
?>
```

该页面本身也很像 `loggedin.php` 页面。虽然你可能会觉得奇怪，明明刚在脚本中删除了 `first_name` Cookie，却仍能引用它，但考虑到这个过程，这完全讲得通：

**A.** 客户端请求此页面。

**B.** 服务器从客户端浏览器读取可用的 Cookie。

**C.** 页面运行并执行其任务（包括发送用于删除现有 Cookie 的新 Cookie）。

简而言之，当此脚本首次运行时，原始的 `first_name` Cookie 数据可供使用。此页面发送的那组 Cookie（删除用的 Cookie）对此页面不可用，因此原始值仍可使用。

**5.** 将文件保存为 `logout.php` 并放入你的 Web 目录（与 `login.php` 同一文件夹）。

#### 创建注销链接

**1.** 在文本编辑器或 IDE 中打开 `header.html`（参考 [脚本 9.1](#ch09.html#ch09ex01)）。

**2.** 将第五个也是最后一个链接修改为（[脚本 12.7](#ch12.html#ch12ex07)）：

```
<li><?php
if ( (isset($_COOKIE['user_id'])) && (basename($_SERVER['PHP_SELF']) != 'logout.php') ) {
  echo '<a href="logout.php"> Logout</a>';
} else {
  echo '<a href="login.php"> Login</a>';
}
?></li>
```

导航区不应再有永久的登录链接，而应根据 Cookie 的存在与否，在用户未登录时显示*登录*链接 ![Image](graphics/circle-h.jpg)，在用户已登录时显示*注销*链接 ![Image](graphics/circle-i.jpg)。前面的条件语句恰好能实现这一点。

![Image](graphics/12_figure_13_h.jpg)
