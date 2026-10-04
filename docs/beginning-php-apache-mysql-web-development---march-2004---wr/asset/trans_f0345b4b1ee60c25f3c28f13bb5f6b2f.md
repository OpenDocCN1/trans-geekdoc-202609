

# 第 12 章

trimBody 函数非常灵活。你可以将其修剪为 50 个字符（通过设置 $s_chr = "xyz" 和 $s_cnt = 999），或者修剪到第一句（设置 $s_chr = "." 和 $s_cnt = 1）。你还可以将默认值设置为你想要的任何值。

我们的下一个函数 outputStory() 接收两个参数。$article 是你想要显示的文章 ID，而 $only_snippet 是 TRUE 或 FALSE，表示是否使用你刚刚创建的 trimBody() 函数对其进行修剪。你不会向调用脚本返回结果。相反，你将结果直接发送到屏幕上。由于由于，outputStory() 应该存放在你存储故事的地方。

```
function outputStory($article, $only_snippet) {
```

为了使用 $conn 变量，你必须对其进行声明。否则，你将使用你自己的的 $conn 变量，而该变量目前不包含任何内容。你本质上是在说：“使用函数外部声明的 $conn 变量”。记住 $conn 是在 conn.php 中创建的，该文件在 outputfunctions.php 的顶部被包含。

```
global $conn;
```

如果 ID 符合预期，你将运行函数的其余部分。第一步是从数据库中获取文章以及该文章的所有数据：

```
if ($article) {
    $sql = "SELECT ar.*, user_name \
FROM cms_articles as ar \
LEFT OUTER JOIN cms_users as us \
ON ar.author_id = us.user_id *" . $article . "
WHERE ar.article_id = " . $article;"
    $result = mysql_query($sql, $conn);
```

函数的其余部分非常直观。它将从数据库检索的数据与 HTML 结合，以便格式化显示故事。然而，有几点我们需要指出：

首先，我们会注意到我们使用了刚刚创建的 trimBody() 函数，但仅当在 outputStory() 函数的第二个参数中时使用。其次，我们使用 PHP 函数 htmlspecialchars() 将文章中任何可能引起 HTML 问题的文本（如 <、>、& 等）转换为它们相应的实体等符（分别对应 &lt;、&gt;、&amp; 等）。第三，HTML 中的换行符本质上被忽略了。为了让 HTML 能够正确显示带有换行的文本，你需要为文本中的每一整行插入 <br />。PHP 提供了一个函数来执行此操作：nl2br()，我们使用了它：

```
if ($only_snippet) {
    echo nl2br(htmlspecialchars(trimBody($row['body'])));

} else {
    echo nl2br(htmlspecialchars($row['body']));
}
```

# 构建内容管理系统

最终结果是文章将按照输入时的预期在页面上显示，并在指定时对对其进行修剪。

outputFunctions() 中的最后一个函数是 showComments()。你传递文章和一个布尔值，该值决定了是否显示允许用户添加评论的链接：

```
function showComments($article, $showLink=TRUE) {
```

将 $conn 声明为全局，这样你就可以在函数内部访问它 global $conn;

你需要知道这篇文章是否已经发布。因此，从文章中获取 is_published 的值以备用：

```
$sql = 'SELECT is_published * \
FROM cms_articles * \
WHERE article_id=' . $article . \
$result = mysql_query($sql, $conn) \
or die(\'Could not look up comments: ' . mysql_error()');
```

```
$row = mysql_fetch_array($result); \
$is_published = $row['is_published'];
```

接下来，获取与此文章相关的所有评论，使用每条评论的用户名和邮箱地址：

```
$sql = 'SELECT *,usr.name,usr.e-mail \
FROM cms_comments c \
LEFT OUTER JOIN cms_users u \
ON c.user_id=u.user_id \
WHERE c.article_id=' . $article . "' \
ORDER BY c.comment_date DESC\'; \
$result = mysql_query($sql, $conn) \
or die(\'Could not look up comments: ' . mysql_error()');
```

当函数的第二个参数返回 TRUE 时，你在页面上显示一个显示为“评论”的标题，以及让用户添加自己的评论的链接（如果该用户是注册用户且文章已发布）。如果有 0 条评论，用户将看到这些内容，并且仍然可以添加新评论。

```
if ($showLink) {
echo '<h4>' . mysql_num_rows($result) . ' Comments</h4>';
if (isset($_SESSION['user_id']) && $is_published) {
echo ' / <a href="comment.php?article=' . $_GET['article'] . '\>Add one comment</a>';
}
}
echo ' </h4>\n';
}
```

正如调用 outputStory() 函数一样，我们将循环每条评论并在文章下方显示评论，最新的评论在前面。

你也会注意到 <span> 和 <div> 标签。这些标签并没有被使用，但它们允许你进行样式设置。

```php
echo "<span class=\"name\">
    htmlspecialchars($row['name']) .
    </span>\n"
echo "<div class=\"date\">
    htmlspecialchars($row['date']) .
    "</div>\n"
echo "<div class=\"content\">
    nl2br(htmlspecialchars($row['comment'])) .
    "</div>\n";
```

再次注意 htmlspecialchars() 和 nl2br() 的使用。这可以防止潜在的 XSS 攻击并确保换行符在 HTML 输出中得到保留。

