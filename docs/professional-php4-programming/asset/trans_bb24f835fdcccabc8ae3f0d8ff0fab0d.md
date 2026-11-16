

对于每个检索到的行，将 Book_Item 对象添加到 $searchResults 数组中：

```
$searchResults[] =
	new Book_Item($row[0], $row[1], $row[2], $row[3], $row[4]);
}
mysql_free_result($result);
```

返回 $searchResults 数组：

```
return new Function_Result(null, $searchResults);
}
}
?>
```

## Music_Shop 类

脚本 MusicShop.php 包含 Music_Shop 类的类定义：

```
<?php
include_once("Common.php");
include_once("MusicItem.php");

class Music_Shop
{
```

函数 getItems() 在成功时以 Music_Item 对象数组的形式返回 MusicShop 表的内容：

```
function getItems()
{

```

获取数据库连接：

```
$functionResult = getDBConnection();
if ($functionResult->returnValue == null) {
	return $functionResult;
}
$link = $functionResult->returnValue;
```

用于从数据库中检索所有音乐项目的 SELECT 查询：

```
$musicShopSelectQuery = "SELECT itemNo, itemType, price, title,
	artist FROM MusicShop";
```

执行查询：

```
if (!($result = mysql_query($musicShopSelectQuery, $link))) {
	return new Function_Result("Internal Error: Could not
	execute sql query ", null);
}
```

```
$musicShopContent = null;
while (($row = mysql_fetch_array($result, MYSQL_NUM))) {
```

对于每个检索到的行，将 Music_Item 对象添加到 $musicShopContent 数组中：

```
$musicShopContent[] = new Music_Item($row[0], $row[1], $row[2],
$row[3], $row[4]);
}
mysql_free_result($result);
```

返回 $musicShopContent：

```
return new Function_Result(null, $musicShopContent);
}
```

函数 getItem() 返回与项目编号 $itemNo 对应的 Music_Item 对象：

```
function getItem($itemNo)
{
$functionResult = getDBConnection();
if ($functionResult->returnValue == null) {
	return $functionResult;
}
$link = $functionResult->returnValue;
```

用于检索项目编号 $itemNo 的音乐项目信息的 SELECT 查询：

```
$musicShopSelectQuery = "SELECT itemNo, itemType, price, title,
artist FROM MusicShop WHERE itemNo='" .
$itemNo . "'";
```

执行查询：

```
if (!($result = mysql_query($musicShopSelectQuery, $link))) {
	return new Function_Result("Internal Error: Could not
	execute sql query ", null);
}
```

从查询结果中获取行：

```
$row = mysql_fetch_array($result, MYSQL_NUM);
if ($row == null) {
	return new Function_Result(null, null);
} else {
```

为检索到的行创建 Music_Item 对象：

```
$item =
new Music_Item($row[0], $row[1], $row[2], $row[3], $row[4]);
```

返回 Music_Item 对象：

```
return new Function_Result(null, $item);
}
```

函数 search() 返回 artist 或 title 列中包含 $searchText 的音乐项目：

```
function search($searchText)
{
```

用于检索 artist 或 title 列中包含 $searchText 的音乐项目的 SELECT 语句：

```
$searchStmt = "SELECT itemNo, itemType, price, title, artist FROM
MusicShop WHERE artist LIKE '%' . $searchText . '%'
OR title LIKE '%' . $searchText . '%' ";
```

调用 getSearchResults() 来执行 $searchStmt SQL 查询：

```
$funcResult = $this->getSearchResults($searchStmt);
```

返回搜索结果：

```
return $funcResult->returnValue;
}
```

函数 searchByTitle() 返回 title 列中包含 $searchText 的 Music_Item 对象：

```
function searchByTitle($searchText)
{
    $searchStmt = "SELECT itemNo, itemType, price, title, artist
    FROM MusicShop
    WHERE title LIKE '%' . $searchText . '%' ";
    $funcResult = $this->getSearchResults($searchStmt);
    return $funcResult->returnValue;
}
```

函数 searchByArtist() 返回 artist 列中包含 $searchText 的音乐项目：

```
function searchByArtist($searchText)
{
    $searchStmt = "SELECT itemNo, itemType, price, title, artist
    FROM MusicShop
    WHERE artist LIKE '%' . $searchText . '%' ";
    $funcResult = $this->getSearchResults($searchStmt);
    return $funcResult->returnValue;
}
```

函数 getSearchResults() 执行 $searchStmt SQL 查询，并将结果作为 Music_Item 对象数组返回：

```
function getSearchResults($searchStmt)
{

```

获取数据库连接：

```
$functionResult = getDBConnection();
if ($functionResult->returnValue == null) {
	return $functionResult;
}
$link = $functionResult->returnValue;
```

执行 $searchStmt SQL 查询：

```
if (!($result = mysql_query($searchStmt, $link)) {
	return new Function_Result("Internal Error: Could not
	execute sql query ", null);
}
$searchResults = null;
while (($row = mysql_fetch_array($result, MYSQL_NUM))) {
```

对于每个检索到的行，将 Music_Item 对象添加到 $searchResults 数组中：

```
$searchResults[] = new Music_Item($row[0], $row[1], $row[2],
$row[3], $row[4]);
}
```

返回 $searchResults 数组：

```
mysql_free_result($result);
return new Function_Result(null, $searchResults);
}
}
?>
```

## Shopping_Cart 和 Shopping_Cart_Item 类

脚本 ShoppingCart.php 包含 Shopping_Cart 和 Shopping_Cart_Item 类的类定义：

```
<?php
include("MusicItem.php");
include("BookItem.php");

class Shopping_Cart
{

```

$shoppingCartItem 存储 Shopping_Cart_Item 对象的数组：

```
var $shoppingCartItems;
```

构造函数初始化成员变量 $shoppingCartItems：

```
function Shopping_Cart()
{
    $this->shoppingCartItems = array();
}
```

函数 addItem() 将 $quantity 个项目 ($item) 添加到购物车中：

```
function addItem($item, $quantity)
{
    $itemNo = $item->getItemNo();
```

获取与 $item 对应的购物车项目：

```
$shoppingCartItem = $this->getShoppingCartItem($itemNo);
if (!$shoppingCartItem) {
```

如果没有与 $item 对应的购物车项目，则添加与 $item 对应的购物车项目：

```
$this->shoppingCartItems[] =
    new Shopping_Cart_Item($item, $quantity);
} else {
```

将 $quantity 添加到购物车项目中：

```
$shoppingCartItem->addQuantity($quantity);
}
}
```

函数 getShoppingCartItem() 返回与 $itemNo 对应的购物车项目：

```
function &getShoppingCartItem($itemNo)
{
    for($i=0; $i<sizeof($this->shoppingCartItems); $i++) {
        $shoppingCartItem = & $this->shoppingCartItems[$i];
        $item = $shoppingCartItem->getItem();

        if ($item->getItemNo() == $itemNo) {
            return $this->shoppingCartItems[$i];
        }
    }
    return null;
}
```

函数 removeItem() 从购物车中移除 $item：

从购物车中移除项目相当于将其数量设置为零：

```
function removeItem($item){
    $shoppingCartItem = $this->getShoppingCartItem($item->getItemNo());

    if ($shoppingCartItem != null) {
        $shoppingCartItem->setQuantity(0);
    }
}
```

函数 changeQuantity() 将 $item 的数量更改为 $newQuantity：

```
function changeQuantity($item, $newQuantity)
{
    $shoppingCartItem = &$this->getShoppingCartItem(
            $item->getItemNo());

    if ($shoppingCartItem != null) {
        $shoppingCartItem->setQuantity($newQuantity);
    }

    $shoppingCartItem = &$this->getShoppingCartItem(
            $item->getItemNo());
}
```

函数 getItems() 返回购物车项目数组：

```
function getItems()
{
    $retItems = array();
    for($i=0; $i<sizeof($this->shoppingCartItems); $i++) {
        $shoppingCartItem = $this->shoppingCartItems[$i];

        if ($shoppingCartItem->getQuantity() != 0) {
            $retItems[] = $shoppingCartItem;
        }
    }
    return $retItems;
}
```

重置购物车：

```
function clear()
{
    $this->shoppingCartItems = array();
}
}
```

Shopping_Cart_Item 类存储购物车中项目的数量：

```
class Shopping_Cart_Item
{
    var $item;
    var $quantity;
}
```

构造函数设置成员变量 $item 和 $quantity 的值：

```
function Shopping_Cart_Item($item, $quantity)
{
    $this->item = $item;
    $this->quantity = $quantity;
}
```

函数 setQuantity() 设置成员变量 $quantity 的值：

```
function setQuantity($quantity)
{
    $this->quantity = $quantity;
}
```

函数 addQuantity() 将成员变量 $quantity 的值增加 $quantity：

```
function addQuantity($quantity)
{
    $this->quantity += $quantity;
}
```

函数 getItem() 返回成员变量 $item 的值：

```
function getItem()
{
    return $this->item;
}
```

函数 getQuantity() 返回成员变量 $quantity 的值：

```
function getQuantity()
{
    return $this->quantity;
}
?>
```

