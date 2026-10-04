

# 第 12 章

然后你就完成了。

```php
<?php require_once 'footer.php'; ?>
```

# comment.php

下一页是 comment.php。包含必要的文件：

```php
<?php
require_once 'comment.php';
require_once 'outputfunctions.php';
require_once 'header.php';
```

然后在在页面顶部显示相应的文章：

```php
outputStory($_GET['article']);
```

然后添加页面标题：

```php
?
<h1>添加评论</h1>
```

使用简单的文本区域来添加新评论：

```php
<form method="post" action="transact-article.php">

<p>
评论: <br />
<textarea id="comment" name="comment" rows="10" cols="60"></textarea>
</p>
```

下一部分将提交按钮和用于文章 ID 的隐藏字段分开。这是为了将文章 ID 发送到下一页：

```php
<p>
<input type="submit" class="submit" name="action"
value="提交评论" />
<input type="hidden" name="article"
value="<?php echo $_GET['article']; ?>" />
</p>
```

在页面上显示此文章的所有当前评论：

```php
</form>

<?php
showComments($_GET['article'],FALSE);
```

就是这样！它们变得越来越简单了，不是吗？和我们继续下去——只有几个短小的章节了。

# 构建内容管理系统

# search.php

接下来，开始 search.php。

```php
require_once 'footer.php';
?>
```

包含必要的文件：

```php
<?php
require_once 'conn.php';
require_once 'outputfunctions.php';
require_once 'header.php';
```

只要你有关键词，就可以进行搜索。在在下面的 SQL 语句中，你会注意到 `MATCH` 和 `AGAINST` 关键字。这是用于在这些字段中进行文本搜索的语法。它们必须是全文索引字段才能执行此类搜索。访问 www.mysql.com/doc/en/fulltext_html 了解有关全文索引的更多信息。

```php
$result = NULL;
if (isset($_GET['keywords'])) {
  $sql = "SELECT article_id FROM cms_articles *
  WHERE MATCH (title,body) \
  AGAINST ('*" . $_GET['keywords'] . '\*\') \
  ORDER BY MATCH (title,body) \
  AGAINST ('*" . $_GET['keywords'] . '\*\') DESC";
```

```php
$result = mysql_query($sql, $conn)
or die("无法执行搜索: " . $mysql_error());
```

如果你没有找到匹配项，那么：

```php
echo "<h1>搜索结果</h1>";

if (!$result || mysql_num_rows($result)) {
  echo "<p>未找到匹配搜索术的文章。</p>";
}
```

否则，循环结果并作为片段显示在屏幕上：

```php
} else {
  while ($row = mysql_fetch_array($result)) {
    outputStory($row['article_id'],TRUE);
  }
}
```

让我们继续到 index.php：

```php
require_once 'footer.php';
?>
```

# 第 12 章

包含标准文件：

```php
<?php
require_once 'conn.php';
require_once 'outputfunctions.php';
require_once 'header.php';
```

获取所有已发布的文章，按发布时间倒序排列：

```php
$sql = "SELECT article_id FROM cms_articles WHERE is_published=1 ORDER BY date_published DESC";
```

```php
$result = mysql_query($sql, $conn);
```

如果没有发布的文章，让用户知道。当然，这是可选的。如果这是某个较大页面的一部分（例如门户页面），你可能只是想在文章列表的位置放置一些内容。

```php
if (mysql_num_rows($result) == 0) {
  echo "<br/>";
  echo " 目前没有可查看的文章。";
}
```

遍历获取的每个文章 ID，并在页面上显示（修剪过的）文章：

```php
} else {
while ($row = mysql_fetch_array($result)) {
  outputStory($row['article_id'],TRUE);
}
```

然后你可以在之后进行清理：

```php
require_once 'footer.php';
?>
```

# forgotpass.php 和 viewarticle.php

下一页 viewarticle.php 是另一个带有头部、页脚和 HTML 的简单表单。它仅用于向用户发送电子邮件以提醒他或她密码。

最后的一页 viewarticle.php 非常短，但它完美地说明了包含文件和函数的本质。

如你所见，viewarticle.php 没有直接显示内容。它只是包含了必要的文件以及两个显示文章和所有评论的函数。

```php
<?php
require_once 'conn.php';
require_once 'outputfunctions.php';
require_once 'header.php';

outputStory($_GET['article']);
```

# 构建内容管理系统

```php
showComments($_GET['article'],TRUE);

require_once 'footer.php';
?>
```

你可能会注意到，当 viewarticle.php 没有传递参数时，你只会得到一个包含标题、搜索和菜单（全部在 header.php 中）的页面。其余是空的。如果这是你想要的结果那就没问题。如果 $_GET['article'] 为空，你可能只想将用户重定向回首页。如果是这样，不要忘记在 header.php 之前包含 http.php。你可能注意到我们漏掉了 login.php 和 forgotpass.php。它们是重要的页面，当然，但大部分是 HTML。header.php 和 footer.php 的包含是唯一的 PHP。我们相信你可以理解这两个页面是如何运作的。

# 总结

嗯，如果你以前觉得写作困难，现在可能了。我们希望这个应用程序让你对如何构建它有一些见解。

# 13

# 邮件列表

啊，是的。邮件列表。这两个简单的词从未意味着过伤害。直到几年前，有人决定将它们放在一起，垃圾邮件就诞生了。当然，邮件列表用于不仅仅是垃圾邮件。毕竟，如果你的名字和地址不在列表中，你怎么收到杂志呢？这和 PHP 有什么关系？在电子邮件和你的网站世界，这是你与所有用户通信的完美方式！

具体来说我们将讨论：

- 管理邮件列表
- 创建邮件列表
- 垃圾邮件
- 订阅（Opt-in）和退出（Opt-out）

那么，你准备好学习如何垃圾你的网站用户了吗？我们希望没有，因为那不是我们要做的。是的，我们将使用邮件列表。而且，我们将发送“群发”电子邮件。然而，我们将负责负责的，只向那些同意接收的人发送电子邮件。对吧？让我们开始吧。

# 首先要做

在创建邮件列表之前，你必须有你打算发送给接收者的东西。思维过程通常是这样的：你决定你有一些想要与用户分享的信息。这是一封通讯邮件、下次漫画展的信息或他们可能想知道的网站更新。你格式化想要分享的信息，使用纯文本或 HTML。你尝试弄清楚如何将这些信息发送给网站成员。如果你能弄清楚如何发送，你就希望你的用户能够阅读并欣赏你发送的各种类型的电子邮件。

