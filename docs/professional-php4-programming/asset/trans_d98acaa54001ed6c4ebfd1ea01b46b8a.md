

## 查看所有图书标题

脚本 ViewBookShop.php 显示所有图书标题：

```php
<?php
header("Content-Type: text/vnd.wap.wml");
include_once("Common.php");
include_once("BookShop.php");

setSessionHandlers();
```

如果用户会话未经过身份验证，则发送错误页面：

```php
checkSessionAuthenticated();
```

如果会话变量 $bookShopContent 的值为 null，则表示这是首次访问该页面。请记住，变量 $bookShopContent 已在 Login.php 脚本中添加到会话：

```php
if (!$bookShopContent) {
```

变量 $currentIndex 是 $bookShopContent 数组中的一个索引。该 PHP 脚本在 WML 页面中仅显示从 $currentIndex 开始的三个图书标题。它创建一个链接，该链接再次指向同一个 PHP 脚本，用于显示其余标题：

```php
$currentIndex=0;
```

通过调用 Book_Shop 对象的 getItems() 方法获取图书商店项目：

```php
$bookShop = new Book_Shop();
$funcResult = $bookShop->getItems();
if ($funcResult->returnValue == null) {
  sendErrorPage($funcResult->errorMessage);
  exit;
}
$bookShopContent = $funcResult->returnValue;
}
?>
```

### WML 文档类型声明：

```xml
<!DOCTYPE wml PUBLIC "-//WAPFORUM//DTD WML 1.1//EN"
      "http://www.wapforum.org/DTD/wml_1.1.xml">
<wml>
<card id="name">
```

定义一个 label 为 Home 的 <do> 元素，类型为 options。该 <do> 元素向 AppMain.php 发送 HTTP GET 请求。这允许用户随时转到应用程序的主页：

```xml
<do type="options" label="HOME">
<go href="AppMain.php?<?php echo(getSessionIdString()) ?>"/>
</do>
```

<p>
<b> 图书商店项目</b>

用于显示图书标题的 select 元素：

```xml
<select>
<?php
$i = 0;
$contentSize = sizeof($bookShopContent);
```

将图书标题（最多三个）显示为链接。链接的动作指向同一 WML 页面中的一个 WML 卡片，包含图书的详细信息：

```php
while (($i<3) && ($currentIndex < $contentSize)) {
 generateOptionElement("#". $bookShopContent[
 $currentIndex]->getItemNo(),
 $bookShopContent[
 $currentIndex]->getTitle());
}
```

$generateDescCard 数组包含需要生成显示卡片的索引列表：

```php
$generateDescCard[] = $currentIndex;
$currentIndex++;
$i++;
}
```

如果还有更多图书标题要显示，则生成一个 View Next Items 链接，动作为 ViewBookShop.php。$currentIndex 变量和会话 ID 字符串作为 URL 参数传递：

```php
if ($currentIndex < $contentSize) {
 $nextHref = "ViewBookShop.php?currentIndex=" .
 $currentIndex . "&amp;" . getSessionIdString();
 generateOptionElement($nextHref, "View Next Items");
}
?>
</select>
</p>
</card>
```

为主卡中显示的每个图书标题生成一个包含图书描述的卡片：

```php
<?php
// Display the details of each card
for($i=0; $i<sizeof($generateDescCard); $i++) {
 $itemNo = $bookShopContent[$generateDescCard[$i]]->getItemNo();
 ?>
```

```xml
<card id="<?php echo($itemNo) ?>">
```

定义一个类型为 accept 的 <do> 元素。该 <do> 元素的动作是向 AddToCart.php 发送 HTTP GET 请求。图书的 itemNo 和会话 ID 字符串作为 URL 参数传递。AddToCart.php 脚本将图书添加到用户的购物车中：

```xml
<do type="accept" label="ADD">
<go href="AddToCart.php?selectedItem=<?php echo($itemNo) . "&amp;" . getSessionIdString() ?>"/>
</do>
```

定义一个类型为 options 的 <do> 元素，它将我们带回同一页面的主卡：

```xml
<do type="options" label="BACK">
<go href="#main" />
</do>
<p>
<?php
```

打印图书标题：

```php
printf("%s<br/>\n",
$bookShopContent[$generateDescCard[$i]]->getTitle());
```

打印图书作者：

```php
printf("%s<br/>\n",
$bookShopContent[$generateDescCard[$i]]->getAuthor());
printf("Book<br/>\n");
```

打印图书价格：

```php
printf("$$%2.2f\n",
$bookShopContent[$generateDescCard[$i]]->getPrice());
?>
</p>
</card>
<?php
} //end for
?>
</wml>
```

## 查看所有音乐专辑

脚本 ViewMusicShop.php 显示所有音乐专辑。ViewMusicShop.php 的代码与 ViewBookShop.php 类似，区别在于 ViewMusicShop.php 中显示了 MusicShop 表的所有行：

```php
<?php
header("Content-Type: text/vnd.wap.wml");
include_once "Common.php";
include_once "MusicShop.php";
setSessionHandlers();

checkSessionAuthenticated();

if (!$musicShopContent) {
    $currentIndex=0;
    $musicShop = new Music_Shop();
    $funcResult = $musicShop->getItems();
    if ($funcResult->returnValue == null) {
        sendErrorPage($funcResult->errorMessage);
        exit;
    }
    $musicShopContent = $funcResult->returnValue;
}
?>
```

```xml
<!DOCTYPE wml PUBLIC "-//WAPFORUM//DTD WML 1.1//EN"
    "http://www.wapforum.org/DTD/wml_1.1.xml">

<wml>
<card id="main">
    <do type="options" label="HOME">
        <go href="AppMain.php?<?php echo(getSessionIdString() ) ?>"/>
    </do>
    <p>
        <b> Music Shop Items</b>
        <select>
<?php
$i = 0;
$contentSize = sizeof($musicShopContent);
while (($i<3) && ($currentIndex < $contentSize)) {
    generateOptionElement("#".
        $musicShopContent[$currentIndex]->getItemNo(),
        $musicShopContent[$currentIndex]->getTitle());
    $generateDescCard[] = $currentIndex;
    $currentIndex++;
    $i++;
}

if ($currentIndex < $contentSize) {
    $nextHref = "ViewMusicShop.php?currentIndex=" .
        $currentIndex . "&amp;" . getSessionIdString();
    generateOptionElement($nextHref, "View Next Items");
}
?>
        </select>
    </p>
</card>
```

```php
<?php
// Display the details of each card
for($i=0; $i<sizeof($generateDescCard); $i++) {
    $itemNo = $musicShopContent[$generateDescCard[$i]]->getItemNo();
?>
```

```xml
<card id="<?php echo($itemNo) ?>" >
<do type="accept" label="ADD">
<go href="AddToCart.php?selectedItem=<?php echo($itemNo . "&amp;" . getSessionIdString()) ?>"/>
</do>
<do type="options" label="BACK">
<go href="#main" />
</do>
</card>
</p>
<?php
printf("%s<br/>\n",
$musicShopContent[$generateDescCard[$i]]->getTitle());
printf("%s<br/>\n",
$musicShopContent[$generateDescCard[$i]]->getArtist());
printf("%s<br/>\n",
$musicShopContent[$generateDescCard[$i]]->getItemType());
printf("$$%2.2f\n",
$musicShopContent[$generateDescCard[$i]]->getPrice());
?>
</p>
</card>
<?php
} //end for
?>
</wml>
```

## 搜索

PHP 脚本 DoSearch.php 对图书标题和音乐专辑进行搜索。它显示搜索结果：

```php
<?php
include_once("Common.php");
include_once("BookShop.php");
include_once("MusicShop.php");

header("Content-Type: text/vnd.wap.wml");
setSessionHandlers();
```

如果用户会话未经过身份验证，则发送错误页面：

```php
checkSessionAuthenticated();
```

如果会话变量 $searchContent 的值为 null，则表示这是首次调用该页面：

```php
if (!$searchContent) {
    $currentIndex=0;
    $bookShop = new Book_Shop();
    $musicShop = new Music_Shop();
```

通过调用 Book_Shop 和 Music_Shop 的相应函数获取搜索结果：

```php
if ($searchType == "Book by Title") {
    $searchContent = $bookShop->searchByTitle($searchText);
} else if ($searchType == "Book by Author") {
    $searchContent = $bookShop->searchByAuthor($searchText);
} else if ($searchType == "Music Album by Title") {
    $searchContent = $musicShop->searchByTitle($searchText);
} else if ($searchType == "Music Album by Artist") {
    $searchContent = $musicShop->searchByArtist($searchText);
} else {
```

如果搜索条件是整个数据库，则合并图书商店和音乐商店的搜索结果：

```php
$searchContent1 = $musicShop->search($searchText);
$searchContent2 = $bookShop->search($searchText);
$searchContent = array_merge($searchContent1, $searchContent2);
}
?>
```

### WML 文档类型声明：

```xml
<!DOCTYPE wml PUBLIC "-//WAPFORUM//DTD WML 1.1//EN"
    "http://www.wapforum.org/DTD/wml_1.1.xml">
<wml>
<card id="main">
```

定义一个 label 为 HOME 的 <do> 元素，类型为 options。该 <do> 元素的动作指向应用程序的主页（AppMain.php）：

```xml
<do type="options" label="HOME">
    <go href="AppMain.php?<?php echo(getSessionIdString()) ?>"/>
</do>
<p>
<b> Search Results</b> <br/>
<?php
$contentSize = sizeof($searchContent);
```

如果 $searchContents 数组的大小为零，则显示“No Items found”消息：

```php
if ($contentSize == 0) {
    printf("No Items Found!<br/>\n");
} else {
```

显示搜索结果的标题（最多三个）。链接的动作指向同一 WML 页面中的一个 WML 卡片，包含实体（图书/CD）的详细信息：

