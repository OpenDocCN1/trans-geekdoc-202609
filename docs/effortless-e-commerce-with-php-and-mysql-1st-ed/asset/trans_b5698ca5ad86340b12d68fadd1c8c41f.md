

- 11. 执行查询：

```php
mysqli_stmt_execute($stmt);
$affected += mysqli_stmt_affected_rows($stmt);
```

首先执行查询，然后将受影响的行数添加到现有计数中。

- 12. 完成控制结构并打印受影响的行数：

```php
} // End of IF.
} // End of FOREACH.
echo "<h4>$affected Product(s) Were Created!</h4>";
```

脚本只是忽略任何不完整的提交，而不是生成错误。采用这种方法，管理员不会仅仅因为只添加了六个新商品而不是完整的十个（或$count 的任何值）而被告知存在问题。

- 13. 完成表单提交条件语句：

```php
} else {
   echo '<p class="error">Please select a category.</p>';
}
} // End of the submission IF.
```

如果未选择任何类别，则适用 else 子句。

- 14. 开始定义表单：

```php
?><h3>Add Specific Coffees</h3>
<form action="add_specific_coffees.php" method="post"
   accept-charset="utf-8">
<fieldset><legend>Fill out the form to add specific coffee products
   to the site.</legend>
```

- 15. 创建类别选择菜单：

```php
<div class="field"><label for="category"><strong>General Coffee Type</strong></label><br />
<select name="category"><option>Select One</option>
<?php
$q = 'SELECT id, category FROM general_coffees ORDER BY category
   ASC';
$r = mysqli_query ($dbc, $q);
while ($row = mysqli_fetch_array ($r, MYSQLI_NUM)) {
   echo "<option value="$row[0]">$row[1]</option>\n";
}
?>
</select></div>
```

咖啡类别列表将从数据库查询中获取。由于这是一个静态查询——它永远不会改变，因此无需使用预处理语句。

### 16. 定义表格：

```
<table border="0" width="100%" cellspacing="5" cellpadding="5">
<thead>
<tr>
<th align="right">Size</th>
<th align="right">Ground/Whole</th>
<th align="right">Caf./Decaf.</th>
<th align="center">Price</th>
<th align="center">Quantity in Stock</th>
</tr>
</thead>
<tbody>
```

添加特定产品的表单使用表格行来呈现一系列表单元素：每个可能的产品属性对应一个。

### 17. 确定尺寸选项：

```
<?php
$q = 'SELECT id, size FROM sizes ORDER BY id ASC;';
$r = mysqli_query ($dbc, $q);
$sizes = "";
while ($row = mysqli_fetch_array ($r, MYSQLI_NUM)) {
$sizes .= "<option value=\"{$row[0]}\">{$row[1]}</option>\n";
}
```

$count 个表单元素中的每一个都将包含三个选择菜单。由于这些菜单的值对于每一行都是相同的，因此最好只定义一次菜单选项，而不是为每个生成的菜单查询数据库。首先，$sizes 变量将被分配一系列 <OPTION> 标签（作为 HTML 字符串），基于从 sizes 表中检索到的值。

### 18. 确定研磨度和咖啡因选项：

```
$grinds = '<option value="ground">Ground</option>
<option value="whole">Whole</option>';
$caf_decaf = '<option value="caf">Caffeinated</option>
<option value="decaf">Decaffeinated</option>';

```

这两个属性各有两个可能的选项。同样，只定义了 <OPTION> 标签。<SELECT> 标签将为每一行赋予唯一的名称。

- 19. 为 $count 中的每个数字创建一行表单元素的表格行：

```
for ($i = 1; $i <= $count; $i++) {
	echo '<tr>
	<td align="right"><select name="size[ . $i . ]"> . $sizes . '
	</select></td>
	<td align="right"><select name="ground_whole[' . $i . "]"> .
	$grinds . '</select></td>
	<td align="right"><select name="caf_decaf[' . $i . "]"> .
	$caf_decaf . '</select></td>
	<td align="center"><input type="text" name="price[' . $i . ']"
	id="price[]" class="small" /></td>
	<td align="center"><input type="text" name="stock[' . $i . ']"
	id="stock[]" class="small" /></td>
	</tr>';
}
```

> **提示**
> 
> 此表单中的两个文本输入具有 class="small" 属性。
> 由于 CSS，这使得它们不如标准输入那么宽。

每个表格行包含五个列，每个列包含一个表单元素。每个表单元素的名称是一个数组，使用当前计数作为其索引。结果将是一个名为 $_POST['size'] 的数组，索引从 1 到 $count，另一个名为 $_POST['ground_whole']，索引从 1 到 $count，依此类推。

- 20. 完成 PHP 块和表格：

```
?></tbody>
</table>
```

- 21. 完成表单：

```
<div class="field"><input type="submit" value="Add These
Products" class="button" /></div>
</fieldset>
</form>
```

- 22. 完成页面：

```php
<?php include ('./includes/footer.html'); ?>
```

- 23. 保存文件并在 Web 浏览器中测试它（图 11.6）。

![](img/4f47e47c67bd619ac73250f11c9fc7ce_346_0.png)

图 11.6

## 添加库存

在销售实物产品的电子商务网站中，库存管理是一项重要功能。如您将在本章后面看到，商品发货时商品库存会减少（您也可以选择在商品售出时减少现有数量）。还需要一种增加库存的方法。

就我所想，管理员可能每天或每周审查销售和当前库存，然后订购更多产品数量以补充企业的库存。当该批货物到达时，增加的库存需要在网站上体现。

为实现此目的，管理员将看到待售每种产品的列表。每个产品都将有一个文本输入，管理员在其中输入刚收到的数量（图 11.7）。

![](img/4f47e47c67bd619ac73250f11c9fc7ce_347_0.png)

图 11.7

- 1. 在文本编辑器或 IDE 中创建一个名为 add_inventory.php 的新 PHP 脚本，并将其存储在管理目录中。

- 2. 包含配置文件、页眉和数据库连接：

```php
<?php
require ('../includes/config.inc.php');
$page_title = 'Add Inventory';
include ('./includes/header.html');
require (MYSQL);
```

- 3. 检查表单提交：

```php
if ($_SERVER['REQUEST_METHOD'] == 'POST') {
if (isset($_POST['add']) && is_array($_POST['add'])) {
require ('../includes/product_functions.inc.php');
```

该脚本的表单将提交 $_POST['add'] 中的一组值数组。唯一的初始验证是 $_POST['add'] 已设置且为数组。如果是，则需要 product_functions.inc.php（来自 Web 根目录的 includes 目录），因为脚本将需要使用其中定义的 `parse_sku()` 函数。

- 4. 定义两个查询：

```php
$q1 = 'UPDATE specific_coffees SET stock=stock+? WHERE id=?';
$q2 = 'UPDATE non_coffee_products SET stock=stock+? WHERE id=?';
```

该脚本将执行两个不同的 UPDATE 查询：一个用于更新 `specific_coffees` 表中的库存值，另一个用于更新 `non_coffee_products` 表中的库存值。这里每个都分配给一个单独的变量。每个查询中的占位符代表要添加到库存的数量和 ID 值（即正在更新的哪个产品）。

- 5. 准备语句：

```php
$stmt1 = mysqli_prepare($dbc, $q1);
$stmt2 = mysqli_prepare($dbc, $q2);
```

每个查询都单独准备，将结果分配给不同的变量。

- 6. 绑定变量：

```php
mysqli_stmt_bind_param($stmt1, 'ii', $qty, $id);
mysqli_stmt_bind_param($stmt2, 'ii', $qty, $id);
```

对于每个语句，变量都绑定到参数。相同的变量绑定到每个查询，尽管对于每个提交的值，只有两个查询中的一个会被执行。

- 7. 循环处理每个提交的值：

```php
$affected = 0;
foreach ($_POST['add'] as $sku => $qty) {
```

首先，将一个变量初始化为零，以计算受影响的行数。然后 foreach 循环将遍历 $_POST['add'] 数组。对于该数组中的每个项，索引被分配给 $sku，值被分配给 $qty。这是与已绑定到预处理语句的相同 $qty 变量。

- 8. 验证要添加的数量：

```php
if (filter_var($qty, FILTER_VALIDATE_INT, array('min_range' => 1))) {
```

第一个要求是要添加的项目数是一个大于或等于 1 的整数。

- 9. 解析 SKU：

```php
list($type, $id) = parse_sku($sku);
```

