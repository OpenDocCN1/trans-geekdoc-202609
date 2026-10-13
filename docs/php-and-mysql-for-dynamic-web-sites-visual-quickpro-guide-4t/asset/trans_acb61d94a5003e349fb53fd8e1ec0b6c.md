

虽然不太可能，但 `$_SESSION['lid']` 可能不等同于 `words` 表中的任何记录。在这种情况下，查询将返回零条记录（但不会报错地运行）。因此，现在必须检索默认语言的词汇。请注意，这段代码块和步骤 5 中的代码都没有实际获取返回的记录。这将在第 7 步中针对两个潜在查询进行。

### 7. 将检索到的词汇获取到数组中，释放资源，并关闭 PHP 部分：

```php
$words = mysqli_fetch_array($r, MYSQLI_ASSOC);

mysqli_free_result($r);

?>
```

在此之后，`$words` 数组代表用户所选语言（或默认语言）中的所有导航和通用元素。

调用 `mysqli_free_result()` 并非必要，但能使编程更加规范。

### 8. 开始 HTML 页面：

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
  <meta http-equiv="content-type" content="text/html; charset=utf-8" />
  <title><?php echo $words['title']; ?></title>
```

请注意，编码也在 `META` 标签中指定了，尽管 PHP 的 `header()` 调用已经标识了编码。这只是为了严谨起见。

正如所写的页头文件，它使用 `$words` 数组中的一个值作为每个页面的标题（即，对于所选语言中的每个页面，页面标题将始终相同）。您可以轻松修改此代码，使页面标题成为语言词汇与特定页面变量的组合，例如第 3 章和后续示例中使用的 `$page_title`。

### 9. 添加 CSS：

```css
<style type="text/css" media="screen">
body { background-color: #ffffff; }
.content {
  background-color: #f5f5f5;
  padding-top: 10px; padding-right: 10px; padding-bottom: 10px; padding-left: 10px;
  margin-top: 10px; margin-right: 10px; margin-bottom: 10px; margin-left: 10px;
}
  a.navlink:link { color: #003366; text-decoration: none; }
  a.navlink:visited { color: #003366; text-decoration: none; }
  a.navlink:hover { color: #cccccc; text-decoration: none; }
  .title {
    font-size: 24px; font-weight: normal; color: #ffffff;
    margin-top: 5px; margin-bottom: 5px; margin-left: 20px;
    padding-top: 5px; padding-bottom: 5px; padding-left: 20px;
  }
</style>
```

这都是从我以前在某处找到的一个模板中获取的。它为网站增加了一点装饰。

### 10. 完成 HTML 头部并开始页面主体：

```html
</head>
<body>
<table width="90%" border="0" cellspacing="10" cellpadding="0" align="center">
<tr>
  <td colspan="2" bgcolor= "#003366" align="center"> <p class="title"><?php echo $words['title']; ?></p></td>
</tr>
<tr>
  <td valign="top" nowrap= "nowrap" width="10%"><b>
```

页面本身使用表格进行布局，第一行显示页面标题，下一行左侧包含导航链接，右侧包含特定页面内容，最后一行包含版权信息 ![Image](graphics/circle-d.jpg)。您将在代码中看到页面标题也将是特定语言的。

![Image](graphics/17_figure_16_d.jpg)

![Image](graphics/circle-d.jpg)页面布局显示主 HTML 表格的行和列。

### 11. 开始显示链接：

```php
<?php
echo '<a href="index.php" class="navlink">' . $words['home'] . '</a><br />
<a href="forum.php" class="navlink">' . $words['forum_home'] . '</a><br />';
```

无论用户是否登录，以及无论他们当前正在查看哪个页面，前两个链接将始终出现。对于每个链接，链接文本本身将是特定语言的。

### 12. 如果用户已登录，显示“新主题”和注销链接：

```php
if (isset($_SESSION['user_id'])) {
  if (basename($_SERVER['PHP_SELF']) == 'forum.php') {
    echo '<a href="post.php" class="navlink">' . $words['new_thread'] . '</a><br />';
  }
  echo '<a href="logout.php" class="navlink">' . $words['logout'] . '</a><br />';
```

通过检查 `$_SESSION['user_id']` 变量是否存在来确认用户的登录状态。如果已设置，则可以创建注销链接。在此之前，会检查这是否为 `forum.php` 页面。如果是，则创建一个开始新主题的链接（用户只有在论坛页面上才能创建新主题；您不会希望他们在其他页面（如主页）上创建新主题，因为不清楚该主题应发布到哪个论坛）。使用 `basename()` 函数检查当前页面的代码首次出现在第 12 章“Cookies 和 Session”中。

### 13. 显示未登录用户的链接：

```php
} else {
  echo '<a href="register.php" class="navlink">' . $words['register'] . '</a><br />
  <a href="login.php" class= "navlink">' . $words['login'] . '</a><br />';
}
```

如果用户未登录，则提供注册和登录的链接。

### 14. 开始一个用于选择语言的表单：

```php
echo '</b><p><form action="forum.php" method="get">
<select name="lid">
<option value="0">' . $words['language'] . '</option>
';
```

用户可以通过下拉菜单 ![Image](graphics/circle-e.jpg) 选择一种语言（这同时也是一个论坛）。菜单中的第一个值将是用户默认语言中的“language”一词。选择菜单的 `name` 为 *lid*（*language ID* 的缩写），其 `action` 属性指向 `forum.php`。当用户提交这个简单的表单时，他们将被带到其选择的论坛。

![Image](graphics/17_figure_17_e.jpg)

![Image](graphics/circle-e.jpg)语言下拉菜单，每个选项均以其原生语言显示。

### 15. 从数据库检索每种语言，并将每种语言添加到菜单中：

```php
$q = "SELECT lang_id, lang FROM languages ORDER BY lang_eng ASC";
$r = mysqli_query($dbc, $q);
if (mysqli_num_rows($r) > 0) {
  while ($menu_row = mysqli_fetch_array($r, MYSQLI_NUM)) {
    echo "<option value=\"$menu_row[0]\">$menu_row[1] </option>\n";
  }
}
mysqli_free_result($r);
```

此查询从 `languages` 表中检索语言和语言 ID。每一种都作为一个选项添加到选择菜单中。

同样，调用 `mysqli_free_result()` 并非必需，但这样做有助于减少 Bug 并提高性能。特别是当您的页面运行多个 `SELECT` 查询时，`mysqli_free_result()` 可以帮助避免 PHP 和 MySQL 之间的混淆问题。

### 16. 完成表单和 PHP 页面：

```php
echo '</select><br />
<input name="submit" type="submit" value="' . $words['submit'] . '" />
</form></p>
    </td>
    <td valign="top" class="content">';
?>
```

### 17. 将文件保存为 `header.html`。

尽管它包含相当数量的 PHP 代码，但该脚本仍将使用 `.html` 扩展名（我倾向于将其用于模板文件）。请确保文件以 UTF-8 编码保存。

### 18. 在文本编辑器或 IDE 中创建一个新文档，命名为 `footer.html`（脚本 17.2）：

```html
<!-- Script 17.2 - footer.html -->
```

### 19. 完成 HTML 页面：

```html
    </td>
  </tr>
  <tr>
    <td colspan="2" align="center">&copy; 2011 Larry Ullman</td>
  </tr>
</table>
</body>
</html>
```

### 20. 将文件保存为 `footer.html`。

同样，请确保文件以 UTF-8 编码保存。

### 21. 将这两个文件放置在您的 Web 目录中，位于一个名为 `includes` 的文件夹内。

**脚本 17.2.** 页脚文件完成 HTML 页面。

---

1   `<!-- Script 17.2 - footer.html -->`
2     `</td>`
3      `</tr>`
4
5      `<tr>`
6      `<td colspan="2" align="center">&copy;`

