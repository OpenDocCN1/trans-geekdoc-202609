
如果用户**已登录**，将使用`CONVERT_TZ()`函数将存储在`posted_on`中的值从UTC转换为用户选择的时区。详见[第6章](#ch06.html#ch06)。请注意，使用此函数要求MySQL安装包含时区列表（详见[第6章](#ch06.html#ch06)）。

**3. 定义并执行查询：**

```php
$q = "SELECT t.thread_id, t.subject, username, COUNT(post_id) - 1 AS responses, MAX(DATE_FORMAT($last, '%e-%b-%y %l:%i %p')) AS last, MIN(DATE_FORMAT($first, '%e-%b-%y  %l:%i %p')) AS first FROM threads AS t INNER JOIN posts AS p USING (thread_id) INNER JOIN users AS u ON t.user_id = u.user_id WHERE t.lang_id = {$_SESSION['lid']} GROUP BY (p.thread_id) ORDER BY last DESC";

$r = mysqli_query($dbc, $q);

if (mysqli_num_rows($r) > 0) {
```

该查询需要返回六项内容：每个主题的ID和主题（来自`threads`表）、发布主题的用户名（来自`users`）、每个主题的回复数、主题创建日期以及主题最后回复日期（均来自`posts`表）。

该查询的整体结构是使用`thread_id`列将`threads`和`posts`表连接（该列在两表中相同）。然后将结果使用`user_id`列与`users`表连接。

至于选定的值，使用了三个聚合函数（见[第7章](#ch07.html#ch07)）：`COUNT()`、`MIN()`和`MAX()`。每个函数均应用于`posts`表中的一列，因此查询包含`GROUP BY (p.thread_id)`子句。`MIN()`和`MAX()`用于返回最早（原始帖子）和最晚的日期。两者都将显示在论坛页面上（见图![Image](graphics/graycircle-a.jpg)）。最晚日期还用于对结果排序，使最近的活动始终排在最前。`COUNT()`函数用于统计给定主题中的帖子数。由于原始帖子也在`posts`表中，它也会被计入`COUNT()`，因此要从该值中减去1。

最后，使用别名使查询编写更简短，并使在PHP脚本中使用结果更容易。如果您对该查询返回的内容感到困惑，请使用mysql客户端![Image](graphics/circle-b.jpg)或phpMyAdmin执行它。

![Image](graphics/17_figure_19_b.jpg)

![Image](graphics/circle-b.jpg)在mysql客户端中运行复杂查询的结果。

**4. 创建结果表：**

```php
echo '<table width="100%" border="0" cellspacing="2" cellpadding="2" align="center">
  <tr>
    <td align="left" width="50%"> <em>' . $words['subject'] . '</em>:</td>
    <td align="left" width="20%"><em>' . $words['posted_by'] . '</em>:</td>
    <td align="center" width="10%"><em>' . $words['posted_on'] . '</em>:</td>
    <td align="center" width="10%"><em>' . $words['replies'] . '</em>:</td>
    <td align="center" width="10%"><em>' . $words['latest_reply'] . '</em>:</td>
  </tr>';
```

与头部文件中的某些项目一样，此HTML页面中列的标题将使用特定语言的术语。

**5. 获取并打印每条返回的记录：**

```php
while ($row = mysqli_fetch_array($r, MYSQLI_ASSOC)) {
  echo '<tr>
      <td align="left"><a href="read.php?tid=' . $row['thread_id'] . '">' . $row['subject'] . '</a></td>
      <td align="left">' . $row['username'] . '</td>
      <td align="center">' . $row['first'] . '</td>
      <td align="center">' . $row['responses'] . '</td>
      <td align="center">' . $row['last'] . '</td>
    </tr>';
}
```

这段代码相当简单，书中有许多类似的示例。主题的主题链接到`read.php`，在URL中传递该主题的ID。

**6. 完成页面：**

```php
  echo '</table>';
} else {
  echo '<p>There are currently no messages in this forum.</p>';
}

include ('includes/footer.html');
?>
```

此`else`子句适用于查询无结果返回的情况。实际上，此消息也应使用用户选择的语言。为简洁起见，此处省略了该功能。要完全实现此功能，请在`words`表中创建另一列，并为每种语言存储该文本的翻译版本。

**7. 将文件保存为`forum.php`，放入Web目录，并在Web浏览器中测试![Image](graphics/circle-c.jpg)。**

![Image](graphics/17_figure_20_c.jpg)

![Image](graphics/circle-c.jpg)`forum.php`页面，以另一种语言查看（对比![Image](graphics/graycircle-a.jpg)）。

***

**提示**

如果运行此脚本时日期和时间无值，很可能是因为您的MySQL安装未更新完整的时区列表。

***

***

**提示**

正如本章介绍所述，本示例省略了所有错误处理。如果查询有问题，请应用[第8章](#ch08.html#ch08)“[错误处理与调试](#ch08.html#ch08)”中概述的调试技术。

***

### 创建主题页面

接下来是查看主题中所有消息的页面![Image](graphics/circle-a.jpg)。通过单击`forum.php`中的链接访问此页面![Image](graphics/circle-b.jpg)。得益于简化的数据库结构，此脚本使用的查询并不复杂（若使用[第6章](#ch06.html#ch06)的数据库设计，此页面将复杂得多）。该页面只需确保接收到有效的主题ID，显示每条消息，并显示供用户添加回复的表单。

![Image](graphics/17_figure_21_a.jpg)

![Image](graphics/circle-a.jpg)`read.php`页面显示主题中的每条消息。

![Image](graphics/17_figure_22_b.jpg)

![Image](graphics/circle-b.jpg)`forum.php`部分源代码显示如何在URL中将主题ID传递给`read.php`。

#### 创建 `read.php`

**1. 在文本编辑器或IDE中开始新建PHP文档，命名为`read.php`（**[脚本17.5](#ch17.html#ch17ex05)**）：**

```php
<?php # Script 17.5 - read.php
include ('includes/header.html');
```

**2. 开始验证主题ID：**

```php
$tid = FALSE;
if (isset($_GET['tid']) && filter_var($_GET['tid'], FILTER_VALIDATE_INT, array('min_range' => 1))) {
  $tid = $_GET['tid'];
```

首先，定义一个标志变量为`FALSE`，意为：证明主题ID有效，这是该脚本最重要的方面。接着，检查主题ID是否通过URL传递，且是否为大于1的整数。这是使用Filter扩展完成的（见[第13章](#ch13.html#ch13)）。最后，将传递给页面的值赋给`$tid`变量，使其不再为`FALSE`值。

如果您的PHP版本不支持Filter扩展，则需将`$_GET['tid']`转型为整数，再确认其值大于1（如[第13章](#ch13.html#ch13)所示）。

**脚本17.5.** `read.php`页面按发布日期升序显示主题中的所有消息。页面顶部显示主题主题，底部包含添加回复的表单。

***

```php
1  <?php # Script 17.5 - read.php
2  // This page shows the messages in a thread.
3  include ('includes/header.html');
4
5  // Check for a thread ID...
6  $tid = FALSE;
7  if (isset($_GET['tid']) && filter_var($_GET['tid'], FILTER_VALIDATE_INT, array('min_range' => 1))) {
8
9      // Create a shorthand version of the thread ID:
10     $tid = $_GET['tid'];
11
12     // Convert the date if the user is logged in:
13     if (isset($_SESSION['user_tz'])) {
14         $posted = "CONVERT_TZ(p.posted_on, 'UTC', '{$_SESSION['user_tz']}')";
```
