

if (!($link = mysql_pconnect($dbHostName, $dbUserName, $dbPassword))) {
    return false;
}

// select mysql database
if (!mysql_select_db($dbName)) {
    return false;
}
```

Prepare the statement for deleting all the rows for which the value of lastAccessed column of the Session table plus $maxlifetime is greater than the current time. Whenever a row is accessed through a SELECT, UPDATE, or REPLACE SQL statement, the value of lastAccessed column is set to the current time:

```php
// DELETE Statement
$deleteStmt = "DELETE FROM Session WHERE CURRENT_TIMESTAMP < 
    (lastAccessed + ". $maxlifetime . ")";

// Execute the query
if (!($result = mysql_query($deleteStmt, $link))) {
    return false;
}

return mysql_affected_rows($link);
}
```

The function setSessionHandlers(), sets the session handlers:

```php
function setSessionHandlers()
{
    session_set_save_handler("open", "close", "read", "write",
        "destroy", "gc");
}
?>
```

## 数据与应用逻辑层

本应用程序的隐含设计目标之一是将应用逻辑与表示层分离（有关详细信息请参阅第 15 章）。在本应用程序中，我们将通过在表示层使用的独立类中实现数据访问和应用逻辑来实现这一目标。

以下是实现数据访问和应用逻辑的类列表：

- Item：封装不同类型项目通用属性的抽象类。
- Book_Item：此类用于建模图书项目。
- Music_Item：此类用于建模音乐项目。
- Book_Shop：此类包含从 BookShop 表获取/搜索图书项目的逻辑。
- Music_Shop：此类包含从 MusicShop 表获取/搜索音乐项目的逻辑。
- Shopping_Cart：此类用于建模用户的购物车。它实现了从购物车添加/移除项目的逻辑。
- Transaction：该类存储用户事务的详细信息。
- Credit_Card：该类存储信用卡详细信息。
- Shipping_Address：该类存储送货地址。
- User：此类用于建模用户。它存储所有用户属性并实现结账逻辑。它将所有保存操作委托给 User_Storage。
- User_Storage：此类实现 User 对象的保存操作。
- UserFactory：实现创建新用户和从数据库加载用户的函数。

## Item 类

脚本 Item.php 包含 Item 类的类定义：

```php
<?php
class Item
{
	var $itemNo;
	var $itemType;
	var $price;
}
```

构造函数设置成员变量 $itemNo、$itemType 和 $price 的值：

```php
function Item($itemNo, $itemType, $price)
{
	$this->itemNo = $itemNo;
	$this->itemType = $itemType;
	$this->price = $price;
}
```

函数 getItemNo() 返回成员变量 itemNo 的值：

```php
function getItemNo()
{
	return $this->itemNo;
}
```

函数 getItemType() 返回成员变量 itemType 的值：

```php
function getItemType()
{
	return $this->itemType;
}
```

函数 getPrice() 返回成员变量 price 的值：

```php
function getPrice()
{
    return $this->price;
}
?>
```

## Book_Item 类

脚本 BookItem.php 包含 Book_Item 类的类定义：

```php
<?php
include_once("Item.php");
```

类 Book_Item 继承自 Item 类：

```php
class Book_Item extends Item
{
    var $title;
    var $author;
```

调用 Item 类的构造函数以设置成员变量 $itemNo、$itemType 和 $price 的值：

```php
function Book_Item($itemNo, $itemType, $price, $title, $author)
{
    $this->Item($itemNo, $itemType, $price);
```

设置成员变量 $title 和 $author 的值：

```php
$this->title = $title;
$this->author = $author;
}
```

函数 getTitle() 返回成员变量 title 的值：

```php
function getTitle()
{
    return $this->title;
}
```

函数 getAuthor() 返回成员变量 author 的值：

```php
function getAuthor()
{
    return $this->author;
}
?>
```

## Music_Item 类

脚本 MusicItem.php 包含 Music_Item 类的类定义：

```php
<?php
include_once("Item.php");
```

类 Music_Item 继承自 Item 类：

```php
class Music_Item extends Item
{
	var $title;
	var $artist;
```

调用 Item 类的构造函数以设置成员变量 $itemNo、$itemType 和 $price 的值：

```php
function Music_Item($itemNo, $itemType, $price, $title, $artist)
{
	$this->Item($itemNo, $itemType, $price);
```

设置成员变量 $title 和 $artist 的值：

```php
$this->title = $title;
	$this->artist = $artist;
}
```

函数 getTitle() 返回成员变量 title 的值：

```php
function getTitle()
{
	return $this->title;
}
```

函数 getArtist() 返回成员变量 artist 的值：

```php
function getArtist()
{
	return $this->artist;
}
?>
```

## Book_Shop 类

脚本 BookShop.php 包含 Book_Shop 类的定义：

```php
<?php
include_once("Common.php");
include_once("BookItem.php");

class Book_Shop
{
```

函数 getItems() 在成功时以 Book_Item 对象数组的形式返回 BookShop 表的内容：

```php
function getItems()
{
```

获取数据库连接：

```php
$functionResult = getDBConnection();
if ($functionResult->returnValue == null) {
    return $functionResult;
}
$link = $functionResult->returnValue;
```

用于从数据库检索所有图书的 SELECT 查询：

```php
$bookShopSelectQuery = "SELECT itemNo, itemType, price,
title, author FROM BookShop";
```

执行 SQL 查询：

```php
if (!($result = mysql_query($bookShopSelectQuery, $link))) {
    return new Function_Result("Internal Error: Could not
execute sql query ", null);
}
$bookShopContent = null;
while (($row = mysql_fetch_array($result, MYSQL_NUM))) {
```

对于检索到的每一行，将一个 Book_Item 对象添加到 $bookShopContent 数组中：

```php
$bookShopContent[] = new
    Book_Item($row[0], $row[1], $row[2], $row[3], $row[4]);
}
mysql_free_result($result);
```

返回 $bookShopContent：

```php
return new Function_Result(null, $bookShopContent);
}
```

函数 getItem() 返回与项目编号 $itemNo 对应的 Book_Item 对象：

```php
function getItem($itemNo)
{
// Get DB Connection
$functionResult = getDBConnection();
if ($functionResult->returnValue == null) {
    return $functionResult;
}
$link = $functionResult->returnValue;
```

用于检索项目编号 $itemNo 的图书信息的 SELECT 查询：

```php
$bookShopSelectQuery = "SELECT itemNo, itemType, price,
title, author FROM BookShop
WHERE itemNo='". $itemNo . "'";
```

执行查询：

```php
if (!($result = mysql_query($bookShopSelectQuery, $link))) {
 return new Function_Result("Internal Error: Could not
execute sql query ", null);
}
```

从查询结果中提取行：

```php
$row = mysql_fetch_array($result, MYSQL_NUM);
if ($row == null) {
 return new Function_Result(null, null);
} else {
```

为检索到的行创建一个 Book_Item 对象：

```php
$item =
 new Book_Item($row[0], $row[1], $row[2], $row[3], $row[4]);
```

返回 Book_Item 对象：

```php
return new Function_Result(null, $item);
}
```

函数 search() 返回作者或标题列中包含 $searchText 的 Book_Item 对象：

```php
function search($searchText)
{
```

SELECT 语句检索作者或标题列中包含 $searchText 的图书项目：

```php
$searchStmt = "SELECT itemNo, itemType, price, title, author FROM
 BookShop WHERE author LIKE '%" . $searchText . "%' OR
 title LIKE '%" . $searchText . "%'";
```

调用 getSearchResults() 函数执行 $searchStmt SQL 查询：

```php
$funcResult = $this->getSearchResults($searchStmt);
```

返回搜索结果：

```php
return $funcResult->returnValue;
}
```

函数 searchByTitle() 返回标题列中包含 $searchText 的 Book_Item 对象：

```php
function searchByTitle($searchText)
{
    $searchStmt = "SELECT itemNo, itemType, price, title, author FROM
                   BookShop WHERE title LIKE '%" . $searchText . "%'" ;
    $funcResult = $this->getSearchResults($searchStmt);
    return $funcResult->returnValue;
}
```

函数 searchByAuthor() 返回作者列中包含 $searchText 的图书项目：

```php
function searchByAuthor($searchText)
{
    $searchStmt = "SELECT itemNo, itemType, price, title, author FROM
                   BookShop WHERE author LIKE '%" . $searchText . "%'" ;
    $funcResult = $this->getSearchResults($searchStmt);
    return $funcResult->returnValue;
}
```

函数 getSearchResults() 执行 $searchStmt 查询，并将结果作为 Book_Item 对象数组返回：

```php
function getSearchResults($searchStmt)
{
```

获取数据库连接：

```php
$functionResult = getDBConnection();
if ($functionResult->returnValue == null) {
    return $functionResult;
}
$link = $functionResult->returnValue;
```

执行 $searchStmt SQL 查询：

```php
if (!($result = mysql_query($searchStmt, $link))) {
    return new Function_Result("Internal Error: Could not
                             execute sql query", null);
}
$searchResults = null;
while (($row = mysql_fetch_array($result, MYSQL_NUM))) {
```

