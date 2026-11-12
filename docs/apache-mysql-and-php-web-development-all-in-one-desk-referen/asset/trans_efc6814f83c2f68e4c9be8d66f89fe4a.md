

```
Category Number:
<select name="categorynum">
<?php
foreach ($catByNum as $num=>$name) {
print "<option value=\"$num\">$name</option>\n";
}
?>
</select>
<br>
<input type="submit" name="Submit"
value="Show All">
</form>
</body></html>
```

如果在客户端计算机的浏览器中打开清单 5-3（categoryname.php），您会看到类似图 5-1 的内容。

![](img/3f967ab8a8fddc723173059f56621648_585_0.png)

图 5-1：客户端浏览器显示类别列表。

在清单 5-3 中，PHP 代码仅对整个类别表执行查询。以下是 select 语句：

```
select * from phpbase.category
```

然后 PHP 代码遍历每一行，将类别名称保存在以 categoryID（一个数字）为键的关联数组中。当代码到达 mysql_close 函数时，catByNum 数组包含所有类别作为值，类别编号作为键。

稍后，在 HTML 表单中，PHP 处理器再次启动，进行第二轮 PHP 乐趣。这次，PHP 代码为组合框控件（在 HTML 世界中称为“select”对象）构建了一组 HTML option 值语句。option 值语句的好处是，您可以设置要在组合框中显示的单词列表，并为每个单词提供一个值，该值将通过 URL 发送到服务器。没错！您就可以在这里放置类别编号。因此，此代码产生的一个 option 值如下：

```
<option value="1">appliances</option>
```

这意味着组合框将显示单词 appliances，但如果我选择 appliances，浏览器将发送值 1，而不是单词 appliances。值 1 反过来是与 appliances 关联的 categoryID。它有效！

此时，您可能意识到，您完全可以在 HTML 文件中硬编码类别值，而不是从表中查找它们。但是，其理念是，如果您通过更改类别名称、删除类别或添加新类别来修改表，使用 option 值方法意味着您不必更改 categoryname.php 文件。如果您硬编码值，在更改数据库中的表后，您还必须更改 HTML，这是额外的工作。

即便如此，我至少能想到两种情况，您可能希望跳过 PHP 并在 HTML 中硬编码类别。第一，如果您不打算经常更改类别；第二，如果您运行的是非常大的服务器，需要将数据库查询降到最低。这两种情况都可以证明在 HTML 中硬编码类别是合理的。

## 使用网页修改数据

尽管允许用户查找数据很棒，但允许他们更改数据（在某些情况下）更好。例如，您可能希望用户能够通过修正拼写错误或更改广告状态来修改广告。

通常，您允许用户通过先查找行并确定行的所有信息来修改表中的行。然后，您在 HTML 表单中显示该行，允许用户更改数据。HTML 表单将数据发送回服务器，在那里，一个 .php 文件使用任何新值更新该行。这听起来并不难——确实不难。

在本节中，我将向您展示如何允许用户修改广告。问题是任何人都可以修改任何广告。如果这是一个真正的分类广告系统，您会想要添加一些安全措施，例如登录部分。通过使用我在图书 VI，第 7 章中向您展示的技术，您可以添加登录部分。要使其工作，您必须修改客户表以包含加密密码。当用户登录时，您加密用户的密码并将其与客户表中的密码进行比较。然后，该客户只能修改该客户“拥有”的广告，这意味着包含与登录客户的 customerID 匹配的 customerID 值的广告。

## 应对添加、搜索和更新

在线数据库系统的设计者往往希望为添加、搜索和更新界面使用同一个表单。这是一个坏主意，因为它可能会让人困惑。例如，在 20 世纪 80 年代中期，我曾帮助开发一个机油更换中心的数据库系统。那个单一表单包含所有字段，您可以在任何字段中输入内容，并可以使用此表单进行添加、搜索和更新。输入数据后，您可以单击搜索按钮以获取行的其余列，然后从那里，您可以更改它们并制造一团混乱。困惑吗？绝对！相反，应有一个用于添加新数据的表单。然后，应有一个用于搜索数据的另一个表单。最后，如果用户搜索数据并获得一行，您可能希望在页面上包含一个链接，让用户跳转到另一个页面来修改数据。使用不同的表单，所有相关人员的生活将会轻松得多。用户最终会感谢您。

遵循“应对添加、搜索和更新”侧边栏的精神，我在此示例中使用三个表单。此示例包括一个用于添加广告的表单、一个用于查找广告的表单（基于本章前面的示例）和一个用于更新数据的表单。

### 创建新广告

我在此向您展示的技术并不新鲜。我在此向您展示的一切，我在图书 VI，第 4 章中都有描述。此外，此表单包含一个类别搜索，使用我之前在“按类别名称查找”部分中解释的技术。清单 5-4 中的 createAd1.html 文件是用作创建广告起点的表单。这是一个不含任何 PHP 代码的 .html 文件，它仅包含一个询问用户电子邮件地址的表单。当用户单击提交（Submit）时，Web 服务器将转到清单 5-5 中的 createAd2.php 文件。

### 清单 5-4：询问用户电子邮件地址的表单

```
<html><head><title>Locate Customer</title></head>
<body bgcolor="#FFFFFF" text="#000000">
<h2>Please enter your email address
so I can find you in the system.</h2>
<form name="form1" method="get"
action="createAd2.php">
<input type="text" name="email">
<input type="submit" value="Submit">
</form></body></html>
```

获取用户的电子邮件地址后，广告系统即准备好让用户输入广告。清单 5-5 中的 createAd2.php 文件使您能够做到这一点。此 PHP 程序首先要做的是确保电子邮件地址属于系统的合法用户。如果不是，代码将打印消息“Sorry, you are not a known user。”

为了演示通过 Web 将数据输入 MySQL 服务器的技术，我故意省略了任何在线分类广告系统可能都很重要的一部分：密码系统。就目前而言，任何人都可以访问此系统并为任何其他人发布广告。然而，此处的重点是向您展示如何通过 HTML 表单输入数据。在图书 VI，第 7 章中，我将引导您创建一个示例网站，允许用户在该网站上注册并登录。要创建一个成功的分类广告系统，请将该章中的信息与本章中的信息相结合。

### 清单 5-5：允许用户输入广告的表单

```
<html><head><title>Create New Ad</title></head>
<body bgcolor="#FFFFFF" text="#000000">
<?php
$CustomerOkay = false;
mysql_connect("localhost", "phpuser", "phppass");
$email = $_GET['email'];
$result = mysql_query(
 "select ID, name from phpbase.customer ". // space!
 "where email = '$email'");
if ($result) {
 if (mysql_num_rows($result) > 0) {
 $row = mysql_fetch_assoc($result);
 $CustomerOkay = true;
 $CustName = $row['name'];
 $CustID = $row['ID'];
 }
}
if ($CustomerOkay == false) {
 print "<h1>Sorry, you are not ".
 "a known customer.</h1>";
}
else {
 print "<h1>Welcome, $CustName!</h2>";
 // Categories
 $result = mysql_query(
 "select * from phpbase.category");
 if ($result) {
 if (mysql_num_rows($result) > 0) {
 while ($row =
 mysql_fetch_assoc($result)){
 $name = $row["category_name"];
 $num = $row["categoryID"];
```

