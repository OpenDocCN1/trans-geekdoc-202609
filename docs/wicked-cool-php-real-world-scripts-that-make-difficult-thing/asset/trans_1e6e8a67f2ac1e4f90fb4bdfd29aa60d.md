

现在，当用户添加评论时，我们该怎么办？

## 添加评论

向条目添加评论的脚本 blog_comment.php 是本系统中唯一没有模板的脚本，因为它不显示任何内容。还记得前一节中提到的，它接受三个参数：ID、comment 和 name，分别对应条目 ID、评论内容和发表评论的人的姓名。第一步是确保条目 ID 有效：

```php
<?php
require_once("blog_config.php");

$ID = intval($_REQUEST["ID"]);
/* Look up the blog posting; make sure it’s real. */
$query = "SELECT title FROM blog_entries WHERE ID = $ID";
$result = mysql_query($query, $connection) or die(mysql_error());
if (mysql_num_rows($result) != 1) {
	header("Location: blog_index.php");
	exit;
}
```

然后，通过删除其中的所有 HTML 来清理评论和姓名。如果清理完之后仍有内容剩余，我们将其插入 blog_comments 表中：

```php
$name = mysql_escape_string(strip_tags($_REQUEST["name"]));
$comment = mysql_escape_string(strip_tags($_REQUEST["comment"]));
$comment = nl2br($comment);

if (!empty($name) && !empty($comment)) {
	$query = "INSERT INTO blog_comments
		(ID, comment, name)
		VALUES ($ID, '$comment', '$name')";
	mysql_query($query, $connection) or die(mysql_error());
}
```

完成后，我们将用户发送回博客条目页面来结束操作，该页面现在（理论上）包含了用户自己的两 cents（看法）：

```php
header("Location: blog_display.php?ID=$ID");
?>
```

我们的博客系统现在缺少的唯一东西就是一个索引页面。

## 创建博客索引

显示最新博客条目的问候页面与博客条目页面相似，因为它使用了 Smarty {section} 功能来减少迭代混乱。

让我们来看看 templates/blog_index.tpl 文件，它以这个标准的头部信息开始：

```html
<html><head>
<title>{$title}</title>
{literal}
<style>
table.entries {
font-size: 12px;
}
table.entries td {
padding-bottom: 7px;
}
.headline {
font-size: 14px;
font-weight: bold;
}
</style>
{/literal}
</head>
<body>
<a href="blog_index.php">my blog</a>
```

如果需要，博客索引将能够按类别显示条目。下一部分会在存在类别时显示当前类别：

```html
{if $category}
<br />
Category: {$category}
{/if}
```

现在我们使用 {section} 遍历 $blog_items 变量，这是一个数组的数组，每个数组包含关于博客条目的信息：

```html
<br />
<table class="entries">
{section name=i loop=$blog_items}
<tr><td>
<span class="headline">
<a href="blog_display.php?ID={$blog_items[i].ID}">{$blog_items[i].title}</a>
</span>
</br>
{$blog_items[i].date}<br />
{$blog_items[i].teaser}<br />
Category: <a href="blog_index.php?category={$blog_items[i].category_parm}">{$blog_items[i].category}</a>
</td></tr>
{/section}
</table>
</body>
</html>
```

blog_index.php 脚本首先检查 category 参数。如果存在该参数，索引应仅显示该类别的条目。为此，创建一个 SQL WHERE 子句来限制你很快将看到的查询，但请确保先清理输入参数。如果没有类别，则将其变量设置为空字符串。

```php
<?php
require_once("blog_config.php");

if ($_REQUEST["category"]) {
  $category = mysql_escape_string($_REQUEST["category"]);
  $where_clause = "WHERE category = '$category'";
  $smarty->assign("category", $category);
} else {
  $where_clause = "";
  $smarty->assign("category", "");
}
```

按如下方式构建并运行 SQL 查询：

```php
$sql = "SELECT title, category, teaser,
             UNIX_TIMESTAMP(entry_time) AS entry_time, ID
             FROM blog_entries
             $where_clause
             ORDER BY entry_time DESC
             LIMIT 0, 20";
$result = @mysql_query($sql, $connection) or die (mysql_error());
if (mysql_num_rows($result) == 0) {
  die('No entries in this blog.');
}
```

假设查询成功，你可以直接构建要分配给 $blog_items Smarty 变量的数组：

```php
$items = array();
while ($row = mysql_fetch_array($result)) {
  $items[] = array(
  "ID"       => $row["ID"],
  "date"     => date("F dS Y, h:ia", $row['entry_time']),
  "title"    => $row['title'],
  "teaser"   => $row["teaser"],
  "category" => $row["category"],
  "category_parm" => urlencode($row["category"]),
  );
}
$smarty->assign("blog_items", $items);
```

最后，分配标题并显示模板（有关最终结果，请参见图 12-8）：

```php
$smarty->assign("title", "blog: index");
$smarty->display("blog_index.tpl");
?>
```

![](img/19183d2b75bf6b509317c631c0e7b817_196_0.png)

图 12-8：博客条目索引

## 脚本黑客技巧

博客生来就是为了被修改扩展。你可以向这个系统添加许多功能，所有这些功能都建立在或扩展你的 PHP 知识之上。以下是几个示例想法：

- **存档** 一旦条目超过几条，你就需要按页面拆分索引。“第 3 条：创建上一页/下一页链接”第 7 页可以帮助你实现这一点。
- **RSS 源** 将你从“第 3 条：构建 Web 服务”第 151 页中了解到的创建 Web 服务的知识应用到这个系统，你就实现了博客的订阅。
- **登录和管理** 目前，任何人都可以向博客添加条目。你可以通过要求登录后才能添加条目来防止这种情况。此外，你可以通过向博客表中添加用户名来添加多个博客。
- **评论 CAPTCHA** 如果你有一个博客，你就会遇到垃圾评论。你可以使用“第 66 条：创建 CAPTCHA（安全）图像”第 129 页中的脚本，或使用 Akismet 来消除它们。

无论你做什么，都要享受其中的乐趣！

## 附录

本书中的几个脚本引用了一个 product_info 表，其中包含假设商店的库存详细信息。以下是表定义：

```sql
CREATE TABLE `product_info` (
`product_name` varchar(50) default NULL,
`product_id` int(10) default NULL,
`category` enum('shoes','gloves','hats') default NULL,
`price` double default NULL,
PRIMARY KEY (`product_id`)
);
```

一旦建立了表，你可能希望提供一些示例数据：

```sql
INSERT INTO `product_info` VALUES ('Cowboy Boots',12,'shoes',19.99);
INSERT INTO `product_info` VALUES ('Slippers',17,'shoes',9.99);
INSERT INTO `product_info` VALUES ('Snowboarding Boots',15,'shoes',89.99);
INSERT INTO `product_info` VALUES ('Flip-Flops',19,'shoes',2.99);
INSERT INTO `product_info` VALUES ('Baseball',20,'hats',12.79);
```

请注意，尽管 product_id 字段中的数字有些任意，但每一行必须是唯一的。

## 索引

### 符号

- . = 追加运算符，95
- ?!= 分组修饰符，80
- ?! 分组修饰符，80
- <? 标记，2
- *（星号），71
- @（at 符号），57
- \（反斜杠），71, 74, 87
- [ ]（方括号），48, 71
- ^（插入符号），70, 71
- :（冒号），26
- { }（花括号），71
- -（连字符/破折号），71
- $（美元符号），15–16, 70
- ==（双等号），64
- "（双引号）
  - 转义，26
  - 查找，46
  - Magic Quotes，26
  - 字符串与，70
- =（等号），20, 64
- （）（圆括号），71
- .（句点），70, 71
- |（管道符号），70, 71
- +（加号），71
- ?（问号），71
- ;（分号），20, 26, 121
- '（单引号）
  - 错误与，23
  - 转义，26
  - 字符串与，70
- /（斜杠），70
- ===（三重等号），64

### A

- $a 数组，13
- 访问控制，26–27
- 访问密钥 ID，149–150
- AddAddress() 方法，122
- AddAttachment() 函数，122–123
- AddChild() 方法，152
- 插件。另见：扩展；库
- AddStringAttachment() 方法，123
- AJAX，162
- allow_url_fopen() 函数，35, 95
- allow_url_include 参数，35
- Amazon.com，149–151
- 锚标签，72, 75–77
- 存档，tar，30
- array_multisort() 函数，13
- 数组。另请参见：特定数组
  - 转换为字符串，12
  - 转换为变量，12–13
  - Cookie 与，107
  - 错误，23
  - $_FILES，47
  - $_GET，47
  - 将表单变量导入其中，48–50
  - 匹配，72–73
  - 多维数组，11, 13–14
  - $_POST，47
  - 打印内容，11, 73, 145–146
  - $_REQUEST，47
  - 序列化，12–13
  - 排序，13–14
  - 查看内容，11
- assign() 方法，16
- Associates Web 服务，149–151

