

# 在线销售：电子商务的快速方法

## 工作原理

我们必须在调用 `session_start()` 函数之前调用 `session_id()` 函数，以确保 `session_id` 的值不会被覆盖，并保持当前的会话 ID。`session_id()` 函数简单返回当前的会话 ID（由浏览器分配），并允许我们在脚本的后半部分使用它的值（方便的是，我们通过 `$_sess` 变量实现了这一点）。

为了查询的简单起见，我们再次在查询中重命名了 `POST` 变量，然后运行 `insert` 查询将我们收集到的信息放入临时表中。

倒数第二行是包含我们的购物车，这样客户就能看到产品是否已成功添加到购物车，并且他或她可以查看那里所有的产品。

## 尝试查看购物车

现在让我们创建实际的购物车 `cart.php`：

```php
<?php
session_id();
session_start();
//连接到数据库
$connect = mysql_connect("localhost", "root", "mysqlpass") or die ('Hey loser, check your server connection.');
?>
<HTML>
<HEAD>
<TITLE>这里是您的购物车！</TITLE>
</HEAD>
<body>
<div align="center">
您当前有

<?php
$sessid = session_id();

//显示购物车中的产品数量
$query = 'SELECT * FROM carttemp WHERE sess = '$sessid*';
$results = mysql_query($query)
or die (mysql_error($connect));
$rows = mysql_num_rows($results);
echo $rows;
?>

<table border="1" align="center" cellpadding="5">
<tr>
<td>数量</td>
<td>商品图片</td>
<td>商品名称</td>
<td>单价</td>
<td>总价</td>
</tr>
```

# 第 14 章

```php
<td></td>
<td></td><td></td><td></td>
<tr>
<?php
while ($row = mysql_fetch_array($results)) {
  extract($row);
  $prod = 'SELECT * FROM PRODUCTS WHERE prodnum = ';
  $prod2 = mysql_query($prod);
  $prod3 = mysql_fetch_array($prod2);
  extract($prod3);
  echo '<form method='POST' action='change.php'>
  <input type='hidden' name='prodnum'
  value='$prodnum'>
  <input type='hidden' name='sessid'
  value='$sessid'>
  <input type='hidden' name='hidden'
  <input type='hidden' name='qty' size='2'
  value='$quan'>
  </td>>';
  echo '<a href='getprod.php?prodid='
  $prodnum.'*'>
  THUMBNAIL<br>IMAGE</td</a>';
  echo '</td>';
  echo '<a href='getprod.php?prodid='
  $prodnum.'*'>
  $fname;
  echo '</td></a>';
  echo '<td align='right'>
  echo $price;
  echo '</td>';
  echo '<td align='right'>
//获取扩展价格价
$extprice = number_format($price * $quan, 2);
  echo $extprice;
  echo '</td>';
  echo '</td>';
  echo '<input type='submit' name='Submit'
  value='更改数量'>
  </form></td>';
  echo '<td>';
  echo '<form method='POST' action='delete.php'>
  <input type='hidden' name='prodnum'
  value='$prodnum'>
  <input type='hidden' name='qty' value='$quan'>
  <input type='hidden' name='hidden'
  value='$hidden'>
  <input type='hidden' name='sessid'
  value='$sessid'>
  echo '<input type='submit' name='Submit'
  value='删除项目'>
  </form></td>';
</tr>
</tr>
```

474

# 在线销售：电子商务的快速方法

```php
//将扩展价格加到总计
$total = $extprice + $total;

}?>
<tr>
<td colspan='4' align='right'>您的运费前总计为：</td>
<td align='right'> <?php echo number_format($total, 2) ?></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<table>
<form method="POST" action="checkout.php">
<input type='submit' name='Submit' value='去结算'>
</form>
<a href="cbashop.php">返回主页</a>
</</div>
<BODY>
</HTML>
```

我们决定只需要一套超级英雄紧身衣，因此向购物车中添加了一个。我们的屏幕看起来就像图 14-4 所示。

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_497_0.png)

图 14-4

# 第 14 章

## 工作原理

现在，观察我们的代码，你可以看到以下：
<div align="center">
您有
<?php
$sessid = session_id();
//显示购物车中的产品数量
$query = 'SELECT * FROM carttemp WHERE sess = '$sessid*';
$results = mysql_query($query)
（此处代码省略）

