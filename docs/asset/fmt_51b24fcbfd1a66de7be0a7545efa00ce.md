
<FORM METHOD="POST" ACTION="<?php print(\$PHP_SELF); ?>">

  条目日期: <INPUT TYPE=TEXT NAME="LogDate" SIZE=10 VALUE="<?php print(\$LogDate); ?>"><BR>

  条目文本: <TEXTAREA NAME="LogText" COLS=75 ROWS=10><?php print(\$LogText); ?></TEXTAREA><BR>

  <INPUT TYPE=HIDDEN NAME="LogID" VALUE="<?php echo $LogID; ?>">

  <INPUT TYPE=HIDDEN NAME="stage" VALUE=2>

  <INPUT TYPE=SUBMIT>

</FORM>

```php
} elseif($stage == 2) {

  /* 打开到数据库连接 */
  mysql_connect("localhost", "phpuser", "sesame") or
  die("Failure to communicate with database");
  mysql_select_db("phpbook");

  /* 插入值 */
  $query = "UPDATE weblog SET LogDate = \$LogDate, LogText = \$LogID";
  $result = mysql_query($query);

  if($result == 0) {
    print("We have a problem.\n");
  } else {
    print("Edit complete.\n");
  }
}
?>

<FORM METHOD="POST" ACTION="<?php print(\$PHP_SELF);?>">

想编辑另一个条目吗？输入日期 (YYYY-MM-DD):<INPUT TYPE=TEXT NAME="LogDate" SIZE=10><BR><INPUT TYPE=HIDDEN NAME="stage" VALUE=1><INPUT TYPE=SUBMIT>

<?php
?>
</body>
</html>
```

在显示 `TEXTAREA` 和 `TEXT` 时，你可能需要使用 `stripslashes` 函数，如果值可能包含单引号。注意像 `O'Malley` 这样带有撇号的名字。

# CHECKBOX

`CHECKBOX` 只有一个可能的输入值：选中（checked）或未选中（unchecked）。然而，复选框经常成组用于传递更复杂的含义。尽管它们很少从数据库预填充（这需要涉及数据库），但如图 20-4 所示是可以实现的。

![](img/5b1cb1f01df587629b183371400fc04a_14_0.png)

图 20-4：预填充的复选框

```html
<HTML>
<HEAD>
<TITLE>Semi-sleazy opt-in form</TITLE>
</HEAD>
<body>
<?php
if(!isset($stage))
{
?>
<FORM METHOD="POST" ACTION="<?php print(\$PHP_SELF); ?>">
<INPUT TYPE=CHECKBOX NAME="OptOut" VALUE="On"><BR>
<FONT SIZE=2>请给我发送大量邮件!</FONT><BR>
<FONT SIZE=2>通过取消勾选此复选框退出</FONT><BR>
<INPUT TYPE=HIDDEN NAME="stage" VALUE=1>
<INPUT TYPE=SUBMIT>
</FORM>
<?php
}
else($stage == 1 && isset($OptOut)) {
  /* 打开到数据库连接 */
  mysql_connect("localhost", "phpuser", "sesame") or die("Failure to communicate database");
  mysql_select_db("phpbook");

  /* 在这种情况下将值更新为 Null */
  $query = "UPDATE checkbox SetValue = NULL WHERE BoxName ='OptOut'";
  $result = mysql_query($query);
  print("You have been removed from our mailing list.");
}
?>
</body>
</html>
```

# RADIO 数据元素允许标识符和值之间存在一对多的关系。换句话说，它们有多个值，但只有一个可以被显示或选中。在功能上，它们与复选框相似。它们最适用于少于 10 个的选项组，且需要两个单词来标识。

# SELECT 元素可能是最有趣的。它可以处理最大数量的选项，并且允许用户通过数组向数据库传递多个选项。在图 20-5 中，我们使用了带有多个选项的 `SELECT` 元素。在 PHP 中，通过在 HTML 表单中声明 `MULTIPLE` 属性并将 `SELECT` 命名为类似 `val[]` 的形式来实现——这会告诉 PHP 它正在处理一个数组而不是单个变量，并会相应地构造数组。当数组到达表单处理器时，你需要像解引用一样通过列出数组内容来处理值。

![](img/5b1cb1f01df587629b183371400fc04a_416_0.png)

图 20-5：多选的预填充下拉框

```html
<HTML>
<HEAD>
<TITLE>Presidential contest</TITLE>
</HEAD>
<BODY>
<P>哪位总统最有权？在按住 "Control"、"Alt" 或 Command 键点击鼠标，从列表中选择多个名字。</P>
<FORM METHOD="POST" ACTION="sidebars.php">
<SELECT NAME="Id[]" SIZE=10 MULTIPLE>
<?php
/* 打开到数据库连接 */
mysql_connect("localhost", "phpuser", "sesame") or
die("<OPTION>Database error!</OPTION></SELECT>);
mysql_select_db("phpbook");
```

```php
/* 下载总统列表 */
$query = "SELECT ID,Name FROM presidents ORDER By Name";
$result = mysql_query($query);
while($president) {
    print("<OPTION VALUE=\"$president[0]\">$president[1]\n");
}
?>
</SELECT>
<P>您的电子邮件：<INPUT TYPE=TEXT NAME="email" SIZE=25></P>
<INPUT TYPE=SUBMIT>
</FORM>
</body>
</html>
```

```php
sidebars.php
<HTML>
<body>
<?php
while(list($key, $val) = each($PresID)) {
    $query = "INSERT INTO votes (ID, PresID, email) VALUES(NULL,$val, 'email');\n";
    $result = mysql_query($query);
}
print("感谢投票！我们将在总统日向我们侧边栏内容的获胜者发送邮件.");
?>
</body>
</html>
```

# 依赖查询的表单

复杂复合类型的表单是一种自提交的表单，具有多个不同的 `FORM` 元素，所有元素都由单个脚本显示或处理。在这种情况下，通常需要编写稍微复杂的代码来涵盖所有可能性。

例如，这里是输入书籍评论的系列表单之一。一个书籍条目已经完成，现在正在将作者与书籍关联。

```html
<HTML>
<HEAD>
<TITLE>Book review: author</TITLE>
</HEAD>
<body>
<?php
if($stage == 1) {
    /* 打开连接 */
    mysql_connect("localhost", "phpuser", "sesame") or die("Can establish connection.");
    mysql_select_db("phpbook");

    /* 与已有的作者关联书籍 */
    $query1 = "INSERT INTO author_book (ID, authorID, bookID) VALUES(NULL,$authorID,$bookID)";
    $result1 = mysql_query($query1);
} elseif($stage == 2 && STRLEN($firstname) > 0) {
    /* 打开连接 */
    mysql_connect("localhost", "phpuser", "sesame") or die("Can establish connection.");
    mysql_select_db("phpbook");

    /* 新作者必须进入数据库，然后关联书籍 */
    $query1 = "INSERT INTO author (ID, firstname, lastname) VALUES(NULL,'$firstname','$lastname)";
    $result1 = mysql_query($query1);
    $authorID = mysql_insert_id($result1);
    $query2 = "INSERT INTO author_book (ID, authorID, bookID) VALUES(NULL,$authorID,$bookID)";
    $result2 = mysql_query($query2);
}
?>
<P>该作者在字母列表中吗？如果是，选择他/她并点击“选择”按钮。如果不是，请填写下面的表单。</P>
```

```php
<?php
/* 打开到数据库连接 */
mysql_connect("localhost", "phpuser", "sesame") or die("Can establish connection.");
mysql_select_db("phpbook");

/* 获取之前的作者 */
$query = "SELECT ID,lastname, firstname FROM author ORDER BY Name";
$result = mysql_query($query);
?>
<SELECT SIZE=1 NAME="$authorID">
<?php
/* 循环将当前作者输出到选择列表 */
while($authorname = mysql_fetch_array($result))
{
    print("<OPTION VALUE=\"$authorname[0]\">$authorname[1]\n");
}
?>
</SELECT>
<P>您的电子邮件：<INPUT TYPE=TEXT NAME="email" SIZE=25></P>
<INPUT TYPE=SUBMIT>
</FORM>
</body>
</html>
```

# 388 第二部分 + PHP 与数据库

```php
print("<OPTION VALUE=\"$authorname[0]\">$$authorname[1]");
```

## 总结

PHP 是一个功能极其强大的表单处理工具，特别是在配合数据库使用时。你可以使用 PHP 从数据库存储的数据中生成表单值，当然，你也可以将表单生成的数据存储在数据库中。

为了让你的 HTML 表单能够与 PHP 顺畅运行，你需要遵循几个简单的规则。首先，最重要的是，请记住始终为每一个表单元素命名——HTML 标准本身并不要求这样做，但 PHP 要求这样做，因为这些元素在表单处理程序中将作为变量名。一个主意是让表单元素的名称与对应的数据库字段名相同，这样它们更容易匹配。PHP 还允许你清晰地使用隐藏输入（hidden inputs）以及多个 `SELECT` 选项，这些选项元素名称应使用方括号（表示数组）来加以区分。

在 PHP 中，你可以选择使用独立的表单和 PHP 处理程序；也可以将两者合并在同一个 PHP 脚本中。后者的方案可能更强大，但处理起来也更困难。你需要在表单内设置一个变量来指示条目是否已提交；大部分 PHP 逻辑将位于 HTML 显示之前。

通过 PHP，你甚至可以在一个页面上拥有多个由同一个 PHP 脚本处理的表单。当然，每个表单都可以从数据库提取的数据中组装。这让你在表单使用上享受最大的灵活性，尽管你需要小心多个部分之间略微复杂的结构和逻辑。

# 博客 (Weblogs)

小型独立 PHP 应用程序（如投票和公告板）都非常不错；但完整的内容网站才是 PHP 真正大放异彩的地方。在这里提供开发最简单类型独立站点——博客（Weblog）的完整内容站点说明。

## 为什么选择博客？

个人博客是最简单的动态网站。它可以被看作个人主页的动态版本：按时间顺序和随性组织的内容网站，而不是根据特定业务或领域的需求来组织。大多数博客并不在涵盖新闻或产生艺术品库的意义上创建所有自己的内容；它们存在更多是为了对他人的内容和当天的事件进行评论。在该类博客的高端，像 Slashdot 这样的公共博客已成为在线社区讨论共同兴趣的极流行聚集地。

如果你是服务器端脚本的新手，我们鼓励你立即开始一个个人博客作为你的第一个项目。没有什么比运行你自己的真实的完整网站更能帮助你快速学习了，在其中你可以根据语境尝试各种新技术和想法。特别是由于 PHP 和其他开源技术增长和变化如此迅速，拥有一个现成的可以涂鸦的测试床是至关重要的。

对于那些在更严肃背景下使用 PHP 的人来说，博客也很有趣，因此值得值得。没有什么快乐能比通过博客进行智力辩论、争论或浪漫故事了。忘记电影、流行音乐和电视吧——博客是时代真正的媒介，宝贝！

## 本章内容

- 为什么选择博客？
- 制作一个简单的博客
- 添加一个 HTTP 入口系统
- 添加数据库
- 修改与添加

## 最简单的博客

最简单的博客只是一个模板和一些包含的文本文件。它仅限于本地开发——换句话说，你无法在以受信任用户身份登录 PHP 服务器时，通过编写文本文件通过 HTTP 发布条目。你将无法分配不同层级的权限，因此这种风格的博客最适合纯个人的单作者站点。

你可能在问自己，这有什么意义？我们的意图是在添加基于表单的文件写入和数据库连接之前（我们将在接下来两个部分完成这些），布局代码并展示 PHP 部分是如何工作的。基于文件的数据存储与数据库的对比也将证明为什么后者是一个如此好的主意。此外，你也可以将这种设计用于纯个人日记，你想在本地的浏览器窗口中阅读它，但并没有实际上将其发布到互联网。

> 我们不建议在公共网站上直接这样使用“最简单的博客”设计，使用包含文件的 GET 风格 URL 可能会带来安全风险。对于公共站点，你真的需要使用数据库来存储数据。

我们决定使用最基本的导航方式，即手动维护的“下一页”（Next）和“上一页”（Previous）文本链接。这让你拥有最大的灵活性来决定更改首页的频率——我们会每天更改，但根据你写的内容多少，你可能更倾向于每周、每月或不定期更改。我们还会包含一个左侧导航栏，其中有独立页面的链接，如“关于我”和“喜爱的物”。

图 21-1 显示了一个完成的博客页面。它由这些文件组装：

- `weblog.php`: 页面模板
- `2000101.txt`, `2000102.txt` 等: 博客条目（每日更改）
- `not_day.txt`: 无内容日的默认消息
- `faves.php`, `links.php`, `about.php`: 静态页面（很少更改）
- `navbar.php`: 每个页面上的导航栏
- `style.inc`: 内部样式表

你可以从我们的网站获取所有这些页面的代码（在此处 21-1 到 21-6 所示）。你必须将 `weblog.php` 中的变量 `$first_date` 修改为你第一条条目的日期，否则你可能会启动一个耗尽所有内存的无限循环！

图 21-1: 博客页面

img/5cb01df58762140

# Listing 21-1: 博客模板 (weblog.php)

```php
<?php
/* 修改为你第一条条目的日期 */
$first_date = 2000101;

/* 默认日期 */
$date = date("Ymd");

/* 通过 GET 传递的日期 */
if(isset($_GET['date'])) {
    $date = $_GET['date'];
}
?>
print("<OPTION VALUE=\"$authorname[0]\">$$authorname[1]");
```

# Listing 21-1: 主博客页面 (weblog.php)

```html
<!DOCTYPE html>
<html>
<head>
    <title>My Blog</title>
    <?php include("style.inc"); ?>
</head>
<body>
    <?php include("navbar.php"); ?>
    <h1>My Blog</h1>
    <?php
    // 简单的显示逻辑
    $file = $date . ".txt";
    if (file_exists($file)) {
        include($file);
    } else {
        include("not_day.txt");
    }
    ?>
</body>
</html>
```

# Listing 21-2: 内部样式 (style.inc)
