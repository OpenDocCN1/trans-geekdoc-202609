

```
</ul>
</div>
<div class="page">
<div class="content">
```

- 3. 创建一个名为 header.html 的新文件并存储在 includes 目录中。
- 4. 粘贴复制的代码。
- 5. 保存文件。

## 为标题添加动态功能

下一系列步骤将在 HTML 模板中嵌入 PHP，以向 HTML 模板添加动态功能。对于任何可能因页面而异或否则不会是静态的内容，你都需要这样做。对于标题文件，有两个区域应该是动态的：页面标题和顶部导航链接的高亮显示（参见图 3.7 中的第一个选项卡）。

- 1. 在 header.html 中，使用 if-else 子句定义页面标题：

```
<title><?php if (isset($page_title)) {
echo $page_title;
} else {
echo 'Knowledge is Power: And It Pays to Know';
}
?></title>
```

页面标题显示在浏览器窗口顶部、书签和浏览器历史记录中；它应该因页面而异。名为 $page_title 的变量将可供标题文件用于表示该值。然而，规范的编程指出你不应该假设该变量存在。因此，此代码首先检查该变量是否已设置（即是否有值）。如果已设置，该值将作为页面标题打印。如果 $page_title 未设置，将使用默认标题。

- 2. 删除构成顶部导航选项卡的列表项（位于 MENU 注释的开始和结束之间）。

当前查看页面的导航选项卡应用了特定的 CSS 类，这会改变其外观。你可以使用 JavaScript 创建此效果，但为了轻松实现所有浏览器兼容性，我将使用 PHP 实现。

- 3. 替代列表项，开始一个 PHP 代码块：

```php
<?php
```

- 4. 创建一个页面数组：

```php
$pages = array(
    'Home' => 'index.php',
    'About' => 'about.php',
    'Contact' => 'contact.php',
    'Register' => 'register.php'
);
```

此数组表示主导航项。每个元素的键是在选项卡上显示的文本。每个元素的值是相应的页面（即该选项卡将链接到的页面）。

> > 标题和页脚中链接的一些页面实际上不会在这本书中创建，但必要时你可以轻松创建它们。

- 5. 确定当前正在查看哪个页面：

```php
$this_page = basename($_SERVER['PHP_SELF']);
```

为了动态为当前页面应用类，脚本需要知道当前页面是什么，这恰好是 PHP 赋给 $_SERVER['PHP_SELF'] 的值。如果用户正在查看 http://www.example.com/dir/file.php，则 $_SERVER['PHP_SELF'] 将具有 /dir/file.php 的值。为了获取其中的 file.php 部分，应用 basename() 函数。

- 6. 遍历每个页面：

```php
foreach ($pages as $k => $v) {
    echo '<li>';
}
```

此循环将针对数组中的每个项运行一次。在循环中，$k 和 $v 值可用于创建导航选项卡。循环中的第一行代码开始一个新的 HTML 列表项。

> > 我通常建议程序员对所有条件语句使用花括号。当你不这样做时，例如当我在本书中节省空间时，请将整个结构放在一行上以保持清晰，如步骤 7 所示。

- 7. 如果是当前页面，添加类：

```php
if ($this_page == $k) echo ' class="selected"';
```

当前页面需要使用 HTML：<li class="selected">。此代码将实现这一点。

- 8. 完成步骤 6 中开始的列表项：

```php
echo '><a href="' . $v . '"><span>' . $k . '</span></a></li>';
```

首先关闭开头的 <li> 标签。然后创建指向特定页面（由 $v 表示）的链接。接下来，在 <span> 标签内写入显示文本，并完成链接和列表项标签。echo 语句

提示
让你的 PHP 代码创建整洁的 HTML 输出，以防你需要检查它。

在下一行结束，以便在页面的 HTML 源代码中添加一个换行符（图 3.10）。

```
<!-- MENU -->
<li class="selected"><a href="index.php"><span>Home</span></a></li>
<li><a href="about.php"><span>About</span></a></li>
<li><a href="contact.php"><span>Contact</span></a></li>
<li><a href="register.php"><span>Register</span></a></li>
<!-- END MENU -->
```

图 3.10

- 9. 完成 foreach 循环和 PHP 代码块：

```php
} // End of FOREACH loop.
?>
```

为了清楚起见，此结束 PHP 标签是必需的，因为它关闭了嵌入在较大 HTML 主体中的 PHP 块。

- 10. 保存文件。

标题部分就到这里。

## 创建页脚

页脚在特定于页面的内容之后接管。它创建侧边栏项和页脚（例如版权和其他三级链接），并完成 HTML 页面。

- 1. 在文本编辑器或 IDE 中打开设计好的模板文件，如果尚未打开的话。

- 2. 从模板文件复制所有 HTML，从特定于页面的内容到结尾，如下所示：

```
</div>
<div class="sidebar">
<!-- SIDEBAR -->
<div class="title">
<h4>Manage Your Account</h4>
</div>
<ul>
<li><a href="renew.php" title="Renew Your Account">Renew Account</a></li>
<li><a href="change_password.php" title="Change Your Password">Change Password</a></li>
<li><a href="favorites.php" title="View Your Favorite Pages">Favorites</a></li>
<li><a href="recommendations.php" title="View Your Recommendations">Recommendations</a></li>
<li><a href="logout.php" title="Logout">Logout</a></li>
</ul>
<div class="title">
<h4>Content</h4>
</div>
<ul>
<li><a href="category.php?id=3" title="Common Attacks">Common Attacks</a></li>
<li><a href="category.php?id=5" title="Database Security">Database Security</a></li>
<li><a href="category.php?id=1" title="General Web Security">General Web Security</a></li>
<li><a href="category.php?id=4" title="JavaScript Security">JavaScript Security</a></li>
<li><a href="category.php?id=2" title="PHP Security">PHP Security</a></li>
<li><a href="pdfs.php" title="PDF Guides">PDF Guides</a></li>
</ul>
<!-- END SIDEBAR -->
</div>
<div class="footer">
<p><a href="site_map.php" title="Site Map">Site Map</a> | <a href="policies.php" title="Site Policies">Policies</a> &nbsp;&nbsp; &copy; Knowledge is Power | Design by <a href="http://www.spyka.net">spyka webmaster</a></p>
</div>
<!-- END PAGE -->
</div>
</body>
</html>
```

这是已登录的非管理员用户的页脚代码。在下一系列步骤中，将更改其他两种可能情况的代码（未登录的访问者和已登录的管理员）。

- 3. 创建一个名为 footer.html 的新文件并存储在 includes 目录中。

- 4. 粘贴复制的代码。

- 5. 保存文件。

### 为页脚添加动态功能

现在你需要对页脚文件做与标题文件相同的事：使用 PHP 动态生成一些 HTML。需要做两项更改。首先，如果用户未登录，侧边栏应显示登录表单；如果已登录，应显示帐户链接；如果已登录且是管理员，还应显示管理链接。其次，你可以动态从数据库获取类别列表。

- 1. 在 footer.html 中，使用 if-else 条件语句替代“管理您的帐户”链接：

```php
<?php
if (isset($_SESSION['user_id'])) {
```

如果 $_SESSION['user_id'] 已设置，页面将知道用户已登录。

- 2. 使用 PHP 重新创建“管理您的帐户”链接：

```php
echo '<div class="title">'
<h4>Manage Your Account</h4>
</div>
<ul>
<li><a href="renew.php" title="Renew Your Account">Renew Account</a></li>
<li><a href="change_password.php" title="Change Your Password">Change Password</a></li>
<li><a href="favorites.php" title="View Your Favorite Pages">Favorites</a></li>
<li><a href="recommendations.php" title="View Your Recommendations">Recommendations</a></li>
<li><a href="logout.php" title="Logout">Logout</a></li>
</ul>
';
```

此 PHP 代码创建与原始模板相同的链接。其中两个链接页面将在后续章节中创建。结束单引号单独占一行，以便在 HTML 源代码中创建一个换行符。

