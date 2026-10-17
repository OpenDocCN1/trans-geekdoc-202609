
将这些看作最终在线年鉴数据库的草稿。我们采用了通常的惯例，即每个表始终有一个名为`ID`的字段，它是主键，并使用连续整数自动为每个新行分配它。虽然你无法从前面的描述中判断出来，但这些表在它们的结构中体现了“关系”——City 表的`country`字段与 Country 表的`ID`字段匹配，代表该城市所属的国家。（如果你在设计一个真实的年鉴数据库，你可能希望更进一步，将 Country 表拆分为 Country 和 Continent 表的关系对。）

要查看我们是如何创建这些表并填充示例数据的，请参阅本章末尾的“创建示例表”部分。

# 第 16 章 ♦ 在表格中显示查询

![](img/70f9bfaf3d714f908e4cb0592b8eb9a6_339_0.png)

图 16-1：简单的数据库表显示

## 改进显示器

我们这个函数的第一个版本有一些局限性：它只处理单个表，不进行错误检查，且呈现形式非常简陋。我们将通过一次全面的修订来解决这些问题并一次性修复。如果你想前瞻一下，该函数的改进新版本在列表 16-2 中。

## 显示列头

我们第一个版本的数据库表显示简单地显示了所有表格单元格，而没有任何关于不同元素的指示。在 HTML 中，使用`<th>`元素作为列头或行头是惯例——在大多数浏览器和样式中，它显示为粗体表格单元格。我们可以做的一个改进是可选地显示基于表字段本身名称的列头。为了实际检索这些名称，我们可以使用`mysql_field_name()`函数。

## 错误检查

我们代码的原版本假设我们写得正确，并且假设数据库运行正常。

> 交叉引用
> 对于 PHP5 中的异常处理，请参见第 31 页。

## 观感问题

对我们简单显示器的一个不满意点是它总是具有相同的样式。通过在函数中调用`die()`来部分解决这个问题，在简单的示例中这种做法是可以接受的。

## 显示任意查询

最后，我们将表格显示器拆分，意味着我们可以使用连接不同表数据的任意查询字符串来实现类似的显示。这些带有观感改进和更好的错误检查的两个函数在列表 16-2 中。

### 列表 16-2：查询显示器

```php
<?php
include("/home/phpbook/phpbook-vars.inc");
$global_db = mysql_connect($hostname, $username, $password)
or die("无法连接数据库");

mysql_select_db($db, $global_db)
or die("无法选择数据库");

function display_db_query($query_string, $connection,
  $header_bool, $table_params) {
    // 执行数据库查询
    $result_id = mysql_query($query_string, $connection)
    or die("查询失败: " . mysql_error());

    // 获取结果中的列数
    $column_count = mysql_num_fields($result_id)
    or die("查询失败: " . mysql_error());

    // TABLE 包含了传递的参数
    进入函数
    print("<TABLE" . $table_params . ">\n");

    // 可选地在表格顶部打印粗体头
    if ($header_bool) {
        print("<TR>");
        while ($row = mysql_fetch_row($result_id)) {
            for ($column_num = 0; $column_num < $column_count; $column_num++) {
                $field_name = mysql_field_name($result_id, $column_num);
                print("<TH>$field_name</TH>");
            }
            print("</TR>\n");
        }
    }
    print("</TABLE>\n");
}

function display_db_table($tablename,$connection,
  $header_bool, $table_params)
{
  $query_string = "SELECT * FROM $tablename";
  display_db_query($query_string, $connection,
  $header_bool, $table_params);
}
?>

<HTML>
<HEAD>
<TITLE>Countries and cities</TITLE>
</HEAD>
<BODY>
<TABLE><TR>
<?php display_db_table("country", $global_db,
  TRUE,"BORDER=2"); ?>
</TR><TD>
<?php display_db_table("city", $global_db,
  TRUE,"BORDER=2"); ?>
</TR></TABLE></BODY></html>
```

此代码在相同数据库连接上的结果如图 16-2 所示。唯一的区别是列头。

## 复杂映射

在这一章中，我们享受了查询结果集与 HTML 表格之间一种非常棒且简单的对应关系——结果集中的每一行对应表格中的某行，代码结构简单来说就是两个嵌套循环。遗憾的是，生活并不总是如此简单，有时我们想要显示的 HTML 表格结构与数据库表的关系型结构之间存在复杂的联系。

## 多次查询与复杂打印

假设我们不想单独显示简单的“城市”和“国家”表，而是希望在表格显示中将它们匹配。

我们可以轻松地编写一个`SELECT`语句来适当地连接这些表：

```
SELECT city.country, country.countryname,
city.cityname
FROM country, city
WHERE city.countryID = country.ID
ORDER BY continent, countryname, cityname
```

现在这里是使用我们的查询显示函数的好地方——我们要做的只是将处理语句作为字符串发送，它就会打印出一个匹配了所属大洲和国家的城市表格。然而，如果我们这样做，我们将为每个城市看到一个独立的 HTML 表格，而且大洲和国家会在每个示例中打印——因为我们会看到“北美”被打印了多次。相反，如果我们想要一个名称对应许多标题呢？这种情况就是我们打印内容的结构与最方便的查询结构不同的情况。

## 视图与存储过程

我们的查询显示器假设了 PHP 代码与数据库系统之间存在特定的分工——PHP 代码发送一个任意查询字符串，数据库通过建立结果集来做出响应。具体来说，这意味着数据库系统必须解析查询，然后找出检索结果的最佳方式。这是导致查询数据库变得略微昂贵的原因之一。

在可能动态构建新颖查询的情况下，这就是你能期待的最好结果。然而，某些数据库允许预设查询，这让数据库系统有机会预判处理查询的方式。其中一种构造在 MS Server 和一些其他 RDBMS 中被称为“视图”——在你将一个查询设置为命名视图后，它可以像存储过程一样被对待处理，允许将运行时参数插入查询中。通常，如果你发现自己正受查询性能缓慢的困扰，你可能需要调查你的 RDBMS 提供了哪些优化方案。

如果我们想进行更复杂的映射，我们有两个选择：我们可以向问题抛出查询，也可以编写更复杂的显示代码。让我们逐一查看每个选项。（对于这些示例中的每一个，我们将放弃之前编写的函数的重用性，转向解决特定显示问题的函数。）

## 多次查询示例

如果我们只想为每个国家打印一行 HTML，我们可以先对国家进行查询，然后在遍历每个国家行时，对相关的城市进行另一次查询。列表 16-3 显示了使用这种策略的函数。

### 16-3：多次查询显示

```php
<?php
include("/home/phpbook/phpbook-vars.inc");
/* 打开数据库连接 */
$global_db = mysql_connect($hostname, $username, $password)
or die("Could not connect to database");
mysql_select_db($db, $global_db)
or die("Could not select database");

function display_cities($db_connection)
{
/* 显示城市和国家列表 */
$country_query = "SELECT id, continent, countryname
FROM country
ORDER BY continent, countryname";

$country_result = mysql_query($country_query, $db_connection);

/* 开始表格，打印硬编码的表头 */
print("<TABLE ORDER=1>\n");
print("<TR><TH>Continent</TH><TH>Country</TH>
<TH>Cities</TH></TR>");

/* 遍历国家 */
while ($country_row = mysql_fetch_row($country_result))
{
    /* 设置国家信息 */
    $country_id = $country_row[0];
    $continent = $country_row[1];
    $country_name = $country_row[2];

    print("<TR ALIGN=LEFT VALIGN=TOP>\n");
    print("<TD>$continent</TD>\n");
    print("<TD>$country_name</TD>\n");

    /* 开始城市列表列表 */
    $city_query = "SELECT name FROM city
                  WHERE country = $country_id";
    $city_result = mysql_query($city_query, $db_connection);

    while ($city_row = mysql_fetch_row($city_result)) {
        print("<TD>$city_row[0]<BR>\n");
    }
    print("</TD><TR>\n");
}
print("</TD><TR></TABLE>\n");
```

## 复杂打印示例

该策略显然很简单：有一个外部循环遍历国家。对于每个国家，内部查询查找属于该国家的城市。这种方法执行了多次查询（参见列表 16-4）。效率取决于数据库的优化程度。

现在让我们用另一种策略来解决相同的问题。我们不再进行多次查询，而是使用单个查询并打印 HTML 行。

### 16-4：单次查询显示

```php
<?php
/* 这是一个更复杂的查询，但它高效得多。
   我们使用 MySQL 的 GROUP_CONCAT 函数在一行中获取所有城市。 */

$query = "SELECT country.countryname, 
          GROUP_CONCAT(city.name SEPARATOR '<BR>') as cities
FROM country
JOIN city ON country.ID = city.countryID
GROUP BY country.countryname
ORDER BY country.countryname";

$result = mysql_query($query, $db_connection);

print("<TABLE ORDER=1>\n");
print("<TR><TH>Country</TH><TH>Cities</TH></TR>\n");

while ($row = mysql_fetch_assoc($result)) {
    print("<TR>\n");
    print("<TD>$row['countryname']</TD>\n");
    print("<TD>$row['cities']</TD>\n");
    print("</TR>\n");
}
print("</TABLE>\n");
?>
```

这段代码有些棘手——尽管它是按顺序遍历结果行的，并且它打印的所有内容都是从当前行获取的，但只有在值发生变化时才打印计数（大洲仍然会被冗余地打印）。

国家的变化通过监控国家行的`ID`字段来检测。计数的变化也是一个信号，用于打印关闭前一个表格行并开始新一行的所需的 HTML。最后，代码必须处理用于开始第一行和结束最后一行的所需的 HTML。

## 创建示例表格

现在我们将向你展示我们实际上用于创建示例表格的 PHP/MySQL 代码。（通常此类数据可能会通过仅与 MySQL 交互来创建，但我们决定通过 PHP 来完成，以尊重我们书名的标题）。代码（位于列表 16-5）是一个特殊用途的一次性补救方案，并不是风格范例，但它包含了使用 SQL `INSERT`的有用示例。

### 列表 16-5：创建示例表格

```php
<?php
include("/home/phpbook/phpbook-vars.inc");
$global_dbh = mysqli_connect($hostname, $username, $password)
or die("Could not connect to database");
mysql_select_db($db, $global_dbh)
or die("Could not select database");

function new_country($dbh, $continent, $countryname)
{
    $country_query = "INSERT INTO country (continent, countryname)
    VALUES ('$continent', '$countryname');
    $result_id = mysql_query($country_query)
    OR die($country_query . mysql_error());
    if ($result_id)
    {
        $countryID = mysql_insert_id($dbh);
        for ($city = current($city_array); $city = next($city_array);
        {
            $city_query = "INSERT INTO city (countryID, city)
            VALUES ('$countryID', '$city');
            mysql_query($city_query, $dbh)
            OR die($city_query . mysql_error());
        }
    }
}
?>
```
