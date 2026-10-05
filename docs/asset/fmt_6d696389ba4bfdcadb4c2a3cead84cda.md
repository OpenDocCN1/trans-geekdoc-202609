
假设我们不是单独地显示`city`和`country`，而是想以表格化的形式将它们匹配起来。在这种情况下，我们打印内容的结构与最方便的查询结构不同。

通常情况下，如果你发现自己正受到查询性能缓慢的困扰，你可能想要调查数据库提供的优化方案。

我们可以轻松地编写一个连接这些表的`SELECT`语句：

```sql
select country.continent, country.countryname,
city.city
from country, city
where city.countryID = country.ID
order by continent, countryname, city
```

现在，这应该是使用我们的查询显示函数的好地方——我们只需要将前面的语句作为字符串插入，我们就能打印出匹配了大洲和国家的城市表格。然而，如果我们这样做，我们将为每个城市看到一个独立的 HTML 行，而大洲和国家每次都会打印一次——例如，我们会看到“北美洲”被打印多次。

## 多次查询示例

如果我们想为每个国家只打印一个 HTML 行，我们可以对国家进行查询，然后在遍历每个国家行的循环中，再对相关的城市进行另一次查询。使用这种策略编写的函数位于列表 19-3。

# 第 19 章 + 在表格中显示查询 367

## 列表 19-3：使用多次查询的显示

继续

## 列表 19-3（续）

```
print("</TABLE\n");
?>
<HTML>
<HEAD>
<TITLE>按国家划分城市</TITLE>
</HEAD>
<BODY>
<?php
display_cities($global_dbh);
?>
</BODY>
</HTML>
```

这种策略简单得迷人：有一个外层循环，使用一次查询遍历所有国家，保存每个国家的名字和每个国家行的主键`ID`字段。然后对于每个国家，使用`ID`字段查找属于该国家的所有城市。注意在内部查询中嵌入`$countryid`变量的技巧——发送的查询字符串在国家循环的每次迭代中都是不同的。

简单吗？是的。高效吗？可能不高。这段代码为每个国家执行一次单独的城市查询。如果数据库中有 500 个国家，此函数将执行 501 次单独数据库查询（额外的一个是包裹的国家查询）。具体表现取决于你特定的数据库解析查询和规划检索查询的效率，但这些查询的总和时间肯定比我们在本节开始时的简单查询要耗得多。

## 一个复杂的打印示例

现在让我们解决完全相同的问题，但使用不同的策略。与其使用多次查询，不如执行单个查询并选择性地打印结果行，使得每个 HTML 表格行对应于一个数据库行（参见列表 19-4）。浏览器显示结果与之前的示例完全相同。

## 列表 19-4：使用单次查询的复杂显示

```php
<?php
include("/home/phpbook/phpbook-vars.inc");
/* 为此页面打开单个数据库连接 */
$global_dbh = mysqli_connect($hostname,$username,$password);
mysql_select_db($db,$global_dbh);
function display_cities($db_connection)
/* 打印国家及其城市的表格。
每个国家选择性地打印一个 HTML 表格行 */
$query = "select country.id,
country.continent, country.countryname,
city.classname
from country, city
where country.id = city.countryID
order by country.continent,
country.countryname,
city.classname";
$result_id =
mysql_query($query,$db_connection)
or die(mysql_error($query));
/* 开始表格，打印硬编码头 */
print("<TABLE BORDER1>\n");
print("<TH>Continent</TH><TH>Country</TH>");
print("<TH>Cities</TH></TR>");

/* 初始化“上一个”国家的 id。
我们依赖于 Country.ID 从 1 开始编号的事实，因此上一个 ID 值为 0 表示当前国家是第一个 */
$old_country_id = 0;
/* 遍历结果行（每个城市一个） */
while ($row_array = mysql_fetch_row($result_id))
{
$country_id = $row_array[0];
/* 如果我们有一个新国家 */
if ($country_id != $old_country_id)
{
```

## 列表 19-4（续）

```
/* 设置国家信息 */
$continent = $row_array[1];
$country_name = $row_array[2];

/* 如果有上一个国家
关闭城市数据和国家行 */
if ($old_country_id != 0)
print("</TD></TR>\n");

/* 为新国家开始一行
```

这段代码很有技巧，尽管它是按顺序遍历结果行的，并且它打印的所有内容都是从当前行获取的，但它只在值发生变化时才打印国家（大陆仍然会被重复地打印）。国家的变化通过监控国家行的`ID`字段来检测。国家的变化也是打印用于关闭上一个表格行并开始新一行的 HTML 的信号。最后，代码必须处理打印启动第一行和结束最后一行所需的 HTML。

# 第 19 章 + 在表格中显示查询

## 创建示例表格

现在我们将向你展示创建示例表格的 PHP 代码（如列表 19-5所示），这不是一个特例，而是与 MySQL 交互的模式。

## 列表 19-5：创建示例表格

```php
<?php

include("/home/phpbook/phpbook-vars.inc");

$global_dbh = mysqli_connect($hostname,$username,$password);

mysql_select_db($db,$global_dbh);

function display_cities($db_connection)

/* 打印国家及其城市的表格。

每个国家选择性地打印一个 HTML 表格行 */

$query = "select country.id,

country.continent, country.countryname,

city.classname

from country, city

where country.id = city.countryID

order by country.continent,

country.countryname,

city.classname";

$result_id =

mysql_query($query,$db_connection)

or die(mysql_error($query));

/* 开始表格，打印硬编码头 */

print("<TABLE BORDER1>\n");

print("<TH>Continent</TH><TH>Country</TH>");

print("<TH>Cities</TH></TR>");

/* 初始化“上一个”国家的 id。

我们依赖于 Country.ID 从 1 开始编号的事实，因此上一个 ID 值为 0 表示当前国家

是第一个 */

$old_country_id = 0;

/* 遍历结果行（每个城市一个） */

while ($row_array = mysql_fetch_row($result_id))

{

$country_id = $row_array[0];

/* 如果我们有一个新国家 */

if ($country_id != $old_country_id)

{

/* 设置国家信息 */

$continent = $row_array[1];

$country_name = $row_array[2];

/* 如果有上一个国家

关闭城市数据和国家行 */

if ($old_country_id != 0)

print("</TD></TR>\n");

/* 为新国家开始一行

```

## 创建示例表格

现在我们将向你展示创建示例表格的 PHP 代码（如列表 19-5 所示），这不是一个特例，而是与 MySQL 交互的模式。

## 从查询构建表单

表单处理是 PHP 最强大的特性之一。使用 HTML 构建用于输入数据的表单，使用 PHP 处理数据，以及使用数据库服务器存储数据，这种组合是各种极其实用的 Web 任务的核心。

## HTML 表单

你已经掌握了制作良好的供 PHP 和数据库处理的表单所需的大部分知识。但有几个关于 PHP 特有的点需要注意。

- 始终为每个数据输入元素（`INPUT`、`SELECT`、`TEXTAREA` 等）使用`NAME`。`NAME`属性将成为 PHP 变量名。如果你的“所见即所得”（WYSIWYG）编辑器不允许你这样做，你就需要记住手动添加这些`NAME`属性。
- `NAME`并不与对应的数据库字段名相同，但通常是一个好主意。
- 你可以（也应该）指定一个`VALUE`，而不是让 PHP 使用默认值。如果可能，考虑用数值值代替文本值，因为数据库匹配字符串的速度比匹配整数慢得多。
- 记得可以使用`HIDDEN`数据输入元素从表单（或页面）传递隐藏变量。
- 记得可以在数组中传递多个变量，但你需要告知用户存在这种可能性。

## 第 20 章

## 本章内容

- 静态 HTML 表单
- 自提交（Self-submission）
- 表单处理
- 依赖变量的表单
- 依赖查询的表单

## 自提交

HTML 表单基本上只是一个漂亮的外壳，是用于将变量传递给服务器的简单方法之上的图形化设备。除了将数据交给用功能更全编程语言编写的表单处理脚本外，它实际上做不了。

然而，在 PHP 中，如果你愿意，可以将表单和表单处理器合并在一个脚本中。事实上，PHP 让自提交过程变得极其简单且实用，以至于你可能会发现自己更倾向于这种“表单+处理器”分离的方法。

自提交并不是一种性恋癖行为。它仅仅指的是将一个或多个表单和表单处理器合并在单个脚本中，使用 HTML `FORM` 标准将数据一次或多次提交给该脚本。自提交通过最简单的手段实现：在标签中将自身指定为`ACTION`目标，如下：

```php
<FORM METHOD="POST" ACTION="myself.php">
```

或者，使用 PHP 独有的内置功能：

```php
<FORM METHOD="POST" ACTION="<?php print(\$PHP_SELF); ?>">
```

虽然你始终可以选择只使用文件名，但在 UNIX 系统中内置的`$PHP_SELF`变量更优。这样，即使你重命名或移动了文件（不用说，移动到启用 PHP 的目录），该文件将继续被正确处理。另一方面，也有报告说此预定义变量在 Windows 上存在问题。

自提交的巨大优势在于，它让你能够在 HTML 表单中构建更多的程序逻辑。例如，你可能根据请求的来源链接略有不同的表单。我们都曾因 HTML 表单只能有一个`ACTION`属性而感到沮丧——这意味着每个表单只能将数据发送给一个表单处理器。通过 PHP，你可以根据用户报告的偏好来处理处理表单。

要配合控件使用自提交，你需要采用更具程序化的 PHP 编写风格——我们在第 14 章中称之为“高级”或“中级”样式。初学者可能会发现这比在 HTML 功能（表单显示）和 PHP 功能（表单处理）之间进行清晰划分更困难。

## 第 20 章 从查询构建表单 377

20-21 显示了分支表单的最简单示例，在这种情况下自提交会非常有用。

![](img/5b1cb1f01df587629b183371400fc04a_408_0.png)

20-21: 一个潜在的自提交表单

```html
<HTML>
<BODY>
<P>感谢使用我们的在线服务系统。请从以下选项中选择：</P>
<FORM METHOD="POST" ACTION="formhandler.php">
<INPUT TYPE=RADIO NAME="userlevel" VALUE=1>我用过这个系统，喜欢更简洁的文档。<BR>
<INPUT TYPE=RADIO NAME="userlevel" VALUE=2>我没用过这个系统，喜欢更详细的文档。<BR>
<INPUT TYPE=SUBMIT>
</FORM>
</BODY>
</HTML>
```

显然在这个表单中，你希望根据用户选择的选项跳转到“新手”或“专家”页面。在 PHP 4 中，你可以编写脚本来处理这两个选项，但仅仅为了两个不同的 HTML 页面而启动整个新进程可能有些浪费。自提交的速度与纯 HTML 请求一样；可能比数据发送到独立的 PHP 处理器更快。

## 处理表单提交

如果表单和处理器是两个页面，那么 PHP 中的表单提交是非常简单的。20-2 显示了一个向数据库插入数据的基础表单和匹配处理器。

![](img/5b1cb1f01df587629b183371400fc04a_409_0.png)

20-2 显示了一个向数据库插入数据的基础表单和匹配处理器。

```html
<HTML>
<HEAD>
<TITLE>电子邮件表单</TITLE>
</HEAD>
<BODY>
<P>请填写以下内容提交您的头衔、姓名和电子邮件。</P>
<FORM METHOD="POST" ACTION="self.php">
头衔：<INPUT TYPE=RADIO NAME="Title" VALUE=1>先生。<BR>
<INPUT TYPE=RADIO NAME="Title" VALUE=2>女士。<BR>
名字：<INPUT TYPE=TEXT NAME="GivenName" SIZE=25><BR>
姓氏：<INPUT TYPE=TEXT NAME="FamilyName" SIZE=25><BR>
电子邮件地址：<INPUT TYPE=TEXT NAME="Email" SIZE=25><BR>
<INPUT TYPE=SUBMIT>
</FORM>
</BODY>
</HTML>
```

## 第二部分 + PHP 与数据库

```php
<?php
{
  /* 打开数据库连接 */
  mysql_connect("localhost", "phpuser") or
  die("无法与数据库通信");
  mysql_select_db("phpbook");
  /* 插入值 */
  $query = "INSERT INTO addressbook (ID, Title, GivenName, Email) VALUES(NULL, '$Title', '$GivenName', '$Email');";
  $result = mysql_query($query);
  if($result == 0) {
    print("出现了问题。");
  } else {
    print("您的信息已记录。");
  }
}
?>
```

# 依赖变量的表单

PHP 非常擅长将变量存入数据库，但它在显示数据库变量的表单方面更为出色。它嵌入 HTML、易于传递变量以及流畅的数据库连接使其成为处理这类工作的最佳选择。这些技术极其有用，因为你会发现有数百万机会从 SQL 提取数据，以可编辑的形式显示，并将新变量替换回数据库。

让我们来看看各种类型的 HTML 表单数据元素以及如何处理它们。

# TEXT 和 TEXTAREA

`TEXT`和`TEXTAREA`是最直接的类型，因为它们的标识符和内容之间存在明确的一一对应关系。换句话说，每个`NAME`仅有一个可能的`VALUE`。记住，在 HTML 表单中，整数和双精度浮必须是`TEXT`或`TEXTAREA`类型。你只需要从数据库中提取数据，并通过引用适当的位置将其显示在表单中，如图 20-3 所示。

![](img/5b1cb1f01df587629b183371400fc04a_412_0.png)

图 20-3：用于编辑的文本显示

```html
<HTML>
<HEAD>
<TITLE>Weblog edit form</TITLE>
</HEAD>
<body
<?php
if(!isset($stage))
{
<FORM METHOD="POST" ACTION="<?php print(\$PHP_SELF); ?>">
想要编辑的条目日期 (YYYY-MM-DD): <INPUT TYPE=TEXT NAME="LogDate" SIZE=10><BR>
<INPUT TYPE=HIDDEN NAME="stage" VALUE=1>
<INPUT TYPE=SUBMIT>
</FORM>
```

```php
<?php
elseif($stage == 1) {
  /* 打开到数据库连接 */
  mysql_connect("localhost", "phpuser", "sesame") or
  die("Failure to communicate with database");
  mysql_select_db("phpbook");
  /* 获取值 */
  $query = "SELECT ID, LogText FROM weblog WHERE LogDate = \$LogDate";
  $result = mysql_query($query);
  $LogRow = mysql_fetch_array($result);
  $LogID = stripslashes($LogRow[1]);
?>
```
