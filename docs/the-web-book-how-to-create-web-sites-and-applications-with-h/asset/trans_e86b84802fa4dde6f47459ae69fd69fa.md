

```
select firstname, surname from customers where surname='Smith' or
surname != 'Smith'
```

`!=` 符号表示“不等于”。因此，我们现在有一个查询，它会返回表中姓氏**是** Smith 或姓氏**不是** Smith 的所有记录。换句话说，它将返回表的全部内容！想象一下，如果来宾能够除了自己的记录外还能显示所有客户的记录会怎样。或者是一个安全的登录设施，访客只有在*“密码正确或密码不正确”*的情况下才被允许访问。

再看另一个例子。考虑一下，如果输入以下姓氏会发生什么：

```
Smith' or surname != 'Smith; delete from customers
```

分号是 MySQL 中用于在单行内分隔多个命令的标准字符。因此，在你的程序搜索输入的姓氏之后，它将**删除**你客户数据库的*全部内容*！

通过防止不需要的字符传递给 MySQL 查询，我们可以预防 SQL 注入攻击。因此，在编写数据库应用程序时，这必须成为你的黄金法则：如果你打算使用不可信的数据作为查询的一部分，请先清洗该数据。至少，不要允许像 `<` `>` `!` `;` 等符号。理想情况下，只允许字母和数字，以及特别需要的其他字符。例如，如果你要求某人提供他们的电子邮件地址，你需要允许点号、连字符、下划线和“@”符号。

不要低估保护系统免受注入攻击的重要性。黑客拥有复杂的工具，可以自动查找网站上的此类错误并尝试利用它们。因此，始终先清洗你的文本，并在查询中始终使用 _san 版本。

记住，你也应该只允许你实际需要的字符。否则，你会有意无意地允许导致问题的字符。例如，%3B 是分号的十六进制代码，所以，如果你阻止用户输入分号，他们仍然可以使用 %3B 来删除你的客户数据库。解决办法？也要阻止 % 符号。

## 向表中添加数据

既然我们可以读取和搜索 MySQL 表，是时候添加存储新数据记录的功能了。这将允许我们停止使用 phpMyAdmin 来插入数据，因为我们将能够使用自己的程序。

让我们编写一个小应用程序，允许我们在现有的 customers 表中创建新客户。我们首先显示一个表单，其中包含 6 个字段（firstname, surname, title, address, phone 和 email）的空间。然后，当用户按下提交按钮时，我们将这些字段的内容添加到一个新的数据库记录中（或者，使用正确的术语，是一个新的表行）。当然，我们还需要创建一个新的 id。不过，MySQL 会自动处理这一点，因为 id 字段被设置为 auto_increment。

以下是应用程序在运行中的样子。首先是数据输入表单：

![](img/50e1558b8202f19b96c1cc386ea5ec66_270_0.png)

填写完表单后，我点击按钮，看到以下内容：

![](img/50e1558b8202f19b96c1cc386ea5ec66_271_0.png)

不错。不仅表单中的数据被插入，我们还知道了为 auto_increment id 字段生成的 id。为了确认它确实起作用了，让我们进入 phpMyAdmin 检查是否确实创建了一个新的客户记录：

![](img/50e1558b8202f19b96c1cc386ea5ec66_271_1.png)

很好，尽管立即发现了一个小 bug。地址中的空格和回车字符被去除了，地址被存储为 `65TheStreetLondon`。你能找出原因以及需要做什么来修复这个问题吗？

另一个值得在此提及的要点。为什么 id 是 1, 2, 3, 14 而不是 1, 2, 3, 4？

在我编写和调试你即将看到的 addcust.php 程序时，创建了 id 从 4 到 13 的记录。我随后使用 phpMyAdmin 删除了这些记录。然而，下次 MySQL 自动生成 id 时，它使用的是 14，而不是回到 4。

关于如何生成自增字段并没有规则。你所保证的唯一事情是它们是唯一的，即不会有两名客户拥有相同的 id。你绝对不应该假设它们是连续的。因此，例如，通过查找 id 编号最高的那个来统计表中客户数量的尝试将不可靠。

以下是 addcust.php 应用程序的完整 PHP 代码：

```php
<?php

# ADDCUST.PHP - 向 customers 表添加新客户

# 检查是否指定了姓氏。
# 如果没有，则只显示表单。

if (!isset($_POST['tb_surname'])) # 如果没有指定姓氏
{
echo "<HTML>";
echo "<body>";
echo "<form method=\"POST\">";
echo "<table>";
echo "<tr>";
echo "<td>First Name</td>";
echo "<td><input type=\"text\" name=\"tb_firstname\" size=\"25\"></td>";
echo "</tr>";
echo "<tr>";
echo "<td>Surname</td>";
echo "<td><input type=\"text\" name=\"tb_surname\" size=\"25\"></td>";
echo "</tr>";
echo "<tr>";
echo "<td>Title</td>";
echo "<td><input type=\"text\" name=\"tb_title\" size=\"25\"></td>";
echo "</tr>";
echo "<tr>";
echo "<td>Address</td>";
echo "<td><textarea rows=\"2\" name=\"ta_address\" cols=\"20\"></textarea></td>";
echo "</tr>";
echo "<tr>";
echo "<td>Phone</td>";
echo "<td><input type=\"text\" name=\"tb_phone\" size=\"25\"></td>";
echo "</tr>";
echo "<tr>";
echo "<td>Email</td>";
echo "<td><input type=\"text\" name=\"tb_email\" size=\"25\"></td>";
echo "</tr>";
echo "</table>";
echo "<br><br>";
echo "<input type=\"submit\" value=\"Create Customer\" name=\"button\">";
echo "</p>";

echo "</form>";
echo "</body>";
echo "</HTML>";
} # 如果没有指定姓氏

else
{ # 指定了姓氏，因此创建新记录

# 从表单获取数据
$title = $_POST["tb_title"];
$firstname = $_POST["tb_firstname"];
$surname = $_POST["tb_surname"];
$address = $_POST["ta_address"];
$phone = $_POST["tb_phone"];
$email = $_POST["tb_email"];

# 现在清洗所有数据
$title = sanitize_form_text($title);
$firstname = sanitize_form_text($firstname);
$surname = sanitize_form_text($surname);
$address = sanitize_form_text($address);
$phone = sanitize_form_text($phone);
$email = sanitize_form_text($email);

# 现在连接到数据库
$db_host = "localhost";
$db_database = "thewebbo_hms";
$db_username = "thewebbo";
$db_password = "xyz";

$dbcnx = mysql_connect($db_host,$db_username,$db_password);
mysql_select_db($db_database);

# 现在构造 MySQL 查询以创建新记录
$query = "insert into customers ";
$query .= "(firstname,surname,title,address,phone,email) ";
$query .= "values (";
$query .= "'$firstname','$surname','$title','$address','$phone','$email')";
$q = mysql_query($query);
$new_row = mysql_insert_id();

echo "<HTML>";
echo "<body>";
echo "Done.  Inserted a new row with an id of " . $new_row;
echo "</body>";
echo "</HTML>";

} # else

exit(); # 我们完成了。下面除了函数外没有其他内容。

function sanitize_form_text($t)
{
  $t = strip_tags($t);
  $t = ereg_replace("[^A-Za-z0-9&.-]", "", $t);
  return $t;
}

?>
```

这里几乎一切都是熟悉的，因为结构与之前的搜索示例非常相似。最重要的新特性是我们如何将新行插入表中的方法。一旦连接到数据库，MySQL 查询的语法是：

```
insert into table (field1,field2) values ( 'value1', 'value2')
```

然后我们将其嵌入到一个 PHP **mysql_query** 函数调用中。在上面的示例中，我在 4 行中构建了查询字符串。这纯粹是为了清晰度，包括打印时的列表外观。如果你不想这样做，可以不必这样做。

括号中的两组项目对应于你要插入的字段名称及其值。你不需要指定每个字段 – 如果你不指定，省略的字段将
