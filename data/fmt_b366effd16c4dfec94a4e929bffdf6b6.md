
`DELETE FROM userslist`

`WHERE pass = 'password' AND`

`name = '' OR 1 = '1'`

## II.4.6. 页面导航

MySQL 中的页面导航可以使用 `LIMIT` 语句来限制记录数量（列表 II.4.22）。

### 列表 II.4.22. 页面导航

```php
<?php
// 设置每页记录数
$number = 3;
// 连接到数据库
require_once("config.php");
// 构造查询以提取
// 目录列表
$query = "SELECT * FROM catalogs";
$cat = mysql_query($query);
if (!$cat) exit(mysql_error());
while ($catalog = mysql_fetch_array($cat)) {
  // 显示目录的链接
  echo "<a href=\$SERVER['PHP_SELF']?id_catalog=$catalog['id_catalog']\">$catalog['name']</a><br>";
}
echo "<a href=\$SERVER['PHP_SELF']?id_catalog=0>All items</a><br>";
```

## 204 第二部分：解决方案

```php
if(isset($_GET['page'])) $page = $_GET['page'];
else $page = 1;
// 初始位置
$start = (($page - 1)*$number + 1);
if ($_GET[id_catalog] != 0) 
$where = "WHERE id_catalog = $_GET[id_catalog]";
else $where = "";
// 构造查询以提取
// 当前目录中的项目
$query = "SELECT * FROM products
$where
ORDER BY price
LIMIT $start, $pnumber";
$prd = mysql_query($query);
if (!$prd) exit(mysql_error());
// 如果当前目录包含
//至少一个项目，则显示项目
if(mysql_num_rows($prd) > 0) {
    echo "<table border = 1>
        <tr>
            <td>Product Name</td>
            <td>Price</td>
        </tr>
        while($product = mysql_fetch_array($prd)) {
            echo "<tr>
                <td>$product[name]</td>
                <td>$product[price]</td>
            </tr>";
        }
    echo "</table>";
}
// 页页数
$query = "SELECT COUNT(*) FROM products $where";
$stot = mysql_query($query);
if(!$stot) exit(mysql_error());
```

## 第二 II.4 章：MySQL 与 SQL 注入 207

```php
$total = mysql_result($tot,0);
$number = (int) ($total/$pnumber);
if((float) ($total/$pnumber) - $number != 0) $number++;
// 输出页码
for($i = 1; $i <= $number; $i++)
{
    if($i != $number)
    {
        if($page == $i)
        {
            echo "[.($i - 1)*$pnumber + 1).".$i*$pnumber].&nbsp";
        }
    else
    {
        echo "<a href=$SERVER['PHP_SELF']?id_catalog=\.page=\.i.">
            $GET['id_catalog']&page=\.i.".
            (($i - 1)*$pnumber + 1)."-"
            $i*$pnumber."></a>&nbsp";
        }
    }
    if($page == $i)
    {
        echo "[.($i - 1)*$pnumber + 1).-($total - 1).".&nbsp";
    }
    else
    {
        echo "<a href=$SERVER['PHP_SELF']?id_catalog=\.page=\.i.">
            $GET['id_catalog']&page=\.i.".
            (($i - 1)*$pnumber + 1)."-"
            ($total - 1)."></a>&nbsp";
    }
}
}
?>
```

### II.4.7. 字母导航

字母排序问题可以通过从 `products` 表中提取备件名称的首字母，并使用 `GROUP` 构造对其进行分组来解决。列表 II.4.23 显示了执行此操作的查询。

#### 列表 II.4.23.提取备件名称首字母的查询

```sql
SELECT SUBSTRING(name, 1, 1) AS letter
FROM products
GROUP BY letter
ORDER BY letter
```

接下来，得到的字母用于形成链接，并通过 GET 参数传递所选字母。选择所有以所选字母开头的项目名称的查询如列表 II.4.24 所示。

#### 列表 II.4.24.选择以指定字母开头的项目的查询

```sql
SELECT * FROM products
WHERE SUBSTRING(name, 1, 1) = 'D'
ORDER BY price
```

列表 II.4.25 显示了结合这两个查询的脚本。

#### 列表 II.4.25. 字母排序输出

```php
<?php
// 连接数据库
require_once("config.php");
// 构造查询以提取备件名称的
// 首字母
$query = "SELECT SUBSTRING(name, 1, 1) AS letter
FROM products
GROUP BY letter
ORDER BY letter";
$prd = mysql_query($query);
if(!$prd) exit(mysql_error());
```

## 第二 II.4 章：MySQL 与 SQL 注入 209

```php
// 如果存在给定字母的项目，
// 显示它们
if (mysql_num_rows($prd) > 0)
{
    while ($product = mysql_fetch_array($prd))
    {
        echo "<a href=\$SERVER['PHP_SELF']?letter=$product['letter']\">$product['letter']</a>";
    }
}
```

```php
// 如果传递了单字母参数，
// 显示表格内容
if (preg_match("^[a-z]$/i", $_GET['letter']))
{
    // 显示备件列表
    $query = "SELECT * FROM products
    WHERE SUBSTRING(name,1,1) = '$GET['letter']'
    ORDER BY price";
    $prd = mysql_query($query);
    if(!$prd) exit (mysql_error());
    // 如果当前目录包含至少
// 一个项目，显示该项目
    if (mysql_num_rows($prd) > 0)
    {
        echo "<br><table border=1>
        <tr>
        <td>Product Name</td>
        <td>Price</td>
        </tr>";
        while($product = mysql_fetch_array($prd))
        {
            echo "<tr>
            <td>\$product['name']</td>
            <td>\$product['price']</td>
        </tr>";
        }
        echo "</table>";
    }
}
```

### II.4.8. 排序

SQL 查询请求的结果使用 `ORDER BY` 语句后跟列名按升序排序。指定可选的 `DESC` 关键字将导致结果按降序排序。因此，解决问题的关键在于构造一个 SQL 查询，并在 `ORDER BY` 语句之后动态添加用于对结果排序的列名。该查询可能是：

```sql
SELECT * FROM products
ORDER BY $order $desc
```

在这里，`order` 变量持有用于结果排序的列名。根据排序顺序，`desc` 变量的值为空或设置为 `DESC`。

### II.4.26. 排序

```php
<?php
// 检查传递给脚本的参数
$order = "name";
if($_GET['order'] == 'name') $order = "name";
if($_GET['order'] == 'price') $order = "price";
if($_GET['order'] == 'grade') $order = "grade";
if($_GET['order'] == 'count') $order = "count";
if($_GET['add'] == 'desc')
{
    $desc = "DESC";
    $add = "";
}
else
{
    $desc = "";
    $add = "desc";
}
// 连接数据库
require_once("config.php");
// 显示备件列表
$query = "SELECT * FROM products
ORDER BY $order desc";
$prd = mysql_query($query);
if(!$prd) exit(mysql_error());
// 如果当前目录包含至少
// 一个项目，显示该项目
if(mysql_num_rows($prd) > 0) {
    echo "<table border=1>
<tr>
<td><a href=\"\$SERVER['PHP_SELF']?order=name&add=$add\">Name</a></td><td><a href=\"\$SERVER['PHP_SELF']?order=price&add=$add\">Price</a></td><td><a href=\"\$SERVER['PHP_SELF']?order=grade&add=$add\">Grade</a></td><td><a href=\"\$SERVER['PHP_SELF']?order=count&add=$add\">Qty</a></td>";
}
```

### II.4.9. 双重下拉列表

在脚本开始时，检查传递的参数。

```php
<?php
// 连接数据库
require_once("config.php");
// HTML 表单的开始
echo "<form method=post>";
// 形成第一个下拉列表
$query = "SELECT * FROM catalogs
ORDER BY name";
$cat = mysql_query($query);
if(!$cat) exit(mysql_error());
// 如果至少有一个记录，
// 形成下拉列表
if(mysql_num_rows($cat) > 0) {
    echo "<select name=id_catalog onChange='this.form.submit()'>";
    echo "<option value=0>No item selected.</option>";
    while($catalog = mysql_fetch_array($cat)) {
	if($_POST['id_catalog'] == $catalog['id_catalog']) {
		$selected = "selected";
	}
```

```php
else $selected = "";
echo "<option value \$catalog['id_catalog'] \$selected
\$catalog['name']</option>";
}
echo "</select>";
}
```

```php
// 检查 id_catalog 是否为整数
if (preg_match('/^\d+$/', $_POST['id_catalog']))
{
    // 形成第二个下拉列表
    $query = "SELECT * FROM products
    WHERE id_catalog = $_POST[id_catalog]
    ORDER BY name";
}
$prd = mysql_query($query);
if (!$prd) exit(mysql_error());
// 如果当前目录包含至少
// 一个项目，形成下拉列表
if (mysql_num_rows($prd) > 0)
{
    echo "<select name=id_product onchange='this.form.submit()'>";
    while ($product = mysql_fetch_array($prd))
    {
        echo "<option value = \$id_product>
\$product['name']</option>";
    }
    echo "</select>";
}
```

```php
// HTML 表单的结束
echo "</form>";
?>
```

列表 II.4.27 中方法的缺点之一是必须刷新页面。解决此问题的另一种方法是预先加载第二个下拉列表的所有版本，并在选择第一个下拉列表的项目时使用 JavaScript 显示它们。

# 214 第二部分：解决方案

为此，在构建第一个列表时，会创建一个名为 `$array_catalog` 的主键数组，用于 `catalogs` 表。该数组用于形成一个 JavaScript 数组（列表 II.4.28）。

## 列表 II.4.28. 构建 JavaScript 数组

```javascript
<script language='JavaScript1.1' type='text/javascript'>
<!--
var messageIdList = new Array<?= implode(",", $array_catalog) ?>);
-->
</script>
```

在最终的 HTML 页面中，该数组将如下：

```
var messageIdList = new Array(3, 4, 2, 5, 1);
```

该列表用于隐藏和显示第二个下拉列表的不同版本。列表的每个版本被称为 `product$i`，其中 `$i` 从 `messageIdList` 数组中顺序取值。此外，每个下拉列表都设置了 `$id` 属性，该值与当前数字 `$i` 相同。这使得 JavaScript 更容易访问该列表。要隐藏下拉列表，必须将 `<select>` 标签的 `style` 属性值设置为 `display:none;`；要显示列表，则将 `style` 值设置为 `display:block;`。在显示选定的列表之前，必须隐藏所有列表，以便在任何时刻只显示第二个下拉列表的版本。这一操作通过第一个下拉列表的 `onchange` 事件处理器来完成。

## 列表 II.4.29. 第一个下拉列表的 change 事件处理器

```javascript
<script language='JavaScript1.1' type='text/javascript'>
<!--
var messageIdList = new Array<?= implode(",", $array_catalog) ?>);
function show(sel)
{
  for (i = 0; i < messageIdList.length; i++)
  {
    document.getElementById(messageIdList[i]).style.display = "none";
  }
  var selectedVal = sel.options[sel.selectedIndex].value;
document.getElementById(selectedVal).style.display = "block";
}
<!---->
<script>
```
