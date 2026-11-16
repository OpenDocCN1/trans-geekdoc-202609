
```
printf("<select>\n");
$i = 0;
while (($i < 3) && ($currentIndex < $contentSize)) {
    generateOptionElement("#".
    $searchContent[$currentIndex]->getItemNo(),
    $searchContent[$currentIndex]->getTitle());
}
```

$generateDescCard 数组包含需要生成描述卡片的索引列表：

```
$generateDescCard[] = $currentIndex;
$currentIndex++;
$i++;
}
```

如果还有更多搜索结果需要显示，则生成一个链接 View Next Items，其 action 为 DoSearch.php。$currentIndex 变量和会话 ID 字符串作为 URL 参数传递：

```
if ($currentIndex < $contentSize) {
    $nextHref = "DoSearch.php?currentIndex=" .
    $currentIndex . "&amp;" . getSessionIdString();
    generateOptionElement($nextHref, "View Next Items");
}
printf("</select>\n");
?>
</p>
</card>
```

对于主卡中显示的每个实体（书/CD），生成一个包含实体描述的卡片：

```
<?php
if ($contentSize > 0) {
    // Display the details of each card
    for($i=0; $i<sizeof($generateDescCard); $i++) {
    $itemNo = $searchContent[$generateDescCard[$i]]->getItemNo();
?>
```

card 元素的 id 属性设置为实体的 itemNo：

```
<card id="<?php echo($itemNo) ?>">
```

定义一个类型为 accept 的 <do> 元素。<do> 元素的操作是向 AddToCart.php 脚本发送 HTTP GET 请求。书/CD 的 itemNo 和会话 ID 字符串作为 URL 参数传递。AddToCart.php 脚本将该项目添加到用户的购物车中：

```
<do type="accept" label="ADD">
    <go href="AddToCart.php?selectedItem=<?php echo($itemNo . "&amp;" . getSessionIdString()) ?>"/>
</do>
```

定义一个类型为 options 的 <do> 元素，它将带回同一页面的主卡片：

```
<do type="options" label="BACK">
<go href="#main"/>
</do>
<p>
```

打印实体的详细信息：

```
<?php
$item = $searchContent[$generateDescCard[$i]];
```

打印标题：

```
printf("%s<br/>\n", $item->getTitle());
```

打印书籍的作者/专辑的艺术家：

```
if (strncasecmp($item->getItemType(), 'BOOK', 4) == 0) {
    printf("%s<br/>\n", $item->getAuthor());
} else {
    printf("%s<br/>\n", $item->getArtist());
}
```

打印实体的类型（书/CD/磁带）：

```
printf("%s<br/>\n", $item->getItemType());
```

打印价格：

```
printf("$%.2f\n", $item->getPrice()); ?>
</p>
</card>
<?php
} //end for
} //end if
?>
</wml>
```

## 将商品添加到用户购物车中

PHP 脚本 AddToCart.php 将商品（URL 参数 $selectedItem）添加到用户的购物车中：

```
<?php
include_once("Common.php");
include_once("BookShop.php");
include_once("MusicShop.php");
include_once("User.php");

setSessionHandlers();
```

如果会话未经过身份验证，则发送错误页面：

```
checkSessionAuthenticated();
```

从数据库获取所选商品的详细信息：

```
$bookShop = new Book_Shop();
$musicShop = new Music_Shop();
$funcResult = $bookShop->getItem($selectedItem);
if ($funcResult->returnValue == null) {
  if ($funcResult->errorMessage == null) {
```

如果在图书商店中找不到商品，则搜索音乐商店：

```
    $funcResult = $musicShop->getItem($selectedItem);
    if ($funcResult->returnValue == null) {
      sendErrorPage($funcResult->errorMessage);
      exit;
    } else {
      $item = $funcResult->returnValue;
    }
  } else {
    sendErrorPage($funcResult->errorMessage);
    exit;
  }
} else {
  $item = $funcResult->returnValue;
}
```

将商品添加到用户的购物车中：

```
// Add the selected item to the shopping cart
$shoppingCart->addItem($item, 1);
?>
```

WML 文档类型声明：

```
<!DOCTYPE wml PUBLIC "-//WAPFORUM//DTD WML 1.1//EN"
  "http://www.wapforum.org/DTD/wml_1.1.xml">
<wml>
  <card id="main">
```

定义一个类型为 options 的 <do> 元素。<do> 元素的操作指向应用程序的主页面（AppMain.php）：

```
<do type="options" label="HOME">
  <go href="AppMain.php?<?php echo(getSessionIdString()) ?>"/>
</do>
<p>
```

显示一条消息（带有查看已添加商品详细信息的链接），指示商品已添加到用户的购物车中：

```
The item <a href="#details"> <?php echo($row[1]) ?></a> has been added
to your cart. <br />
```

生成一个锚元素以查看购物车中的商品：

```
<a href="DisplayCart.php?<?php echo(getSessionIdString()) ?>">
Display Cart
</a>
</p>
</card>
```

商品详情卡片：

```
<card id="details">
```

定义一个类型为 options 的 <do> 元素，用于转到应用程序的主页面（AppMain.php）：

```
<do type="options" label="HOME">
<go href="AppMain.php?<?php echo(getSessionIdString()) ?>"/>
</do>
```

定义一个类型为 accept 的 <do> 元素，将用户带回同一页面的主卡片：

```
<do type="accept" label="BACK">
<go href="#main"/>
</do>
<p>
```

打印商品的详细信息：

```
<?php
```

打印商品的标题：

```
printf("%s <br/>\n", $item->getTitle());
```

打印商品的艺术家/作者：

```
if (strncasecmp($item->getItemType(), 'BOOK', 4) == 0) {
    printf("%s<br/>\n", $item->getAuthor());
} else {
    printf("%s<br/>\n", $item->getArtist());
}
```

打印商品的类型 – 书/CD/磁带：

```
printf("%s <br/>\n", $item->getItemType());
```

打印商品的价格：

```
printf("$%s <br/>\n", $item->getPrice());
?>
</p>
</card>
</wml>
```

## 显示用户购物车

PHP 脚本 DisplayCart.php 显示用户的购物车：

```
<?php
include_once("Common.php");
include_once("User.php");
include_once("BookItem.php");
include_once("MusicItem.php");

setSessionHandlers();

if (!headers_sent()) {
   header("Content-Type: text/vnd.wap.wml" );
}
```

如果会话未经过身份验证，则发送错误页面：

```
checkSessionAuthenticated();
?>
```

WML 文档类型声明：

```
<!DOCTYPE wml PUBLIC "-//WAPFORUM//DTD WML 1.1//EN"
  "http://www.wapforum.org/DTD/wml_1.1.xml">
<wml>
<card id="main">
```

定义一个类型为 options 的 <do> 元素。<do> 元素的操作指向应用程序的主页面（AppMain.php）：

```
<do type="options" label="HOME">
   <go href="AppMain.php?<?php echo(getSessionIdString()) ?>"/>
</do>
<p>
<b> Shopping Cart Items </b>
<?php
```

获取购物车商品：

```
$shoppingCartItems = $shoppingCart->getItems();
$first = true;
$insertedSelect = false;
for($i=0; $i < sizeof($shoppingCartItems) ; $i++) {
  if ($first) {
    printf("<select>");
    $insertedSelect = true;
  }
  $item = $shoppingCartItems[$i]->getItem();
```

将商品标题显示为链接。链接的操作指向同一页面中包含商品详细信息的卡片：

```
generateOptionElement("#". $item->getItemNo(),
                      $item->getTitle());
              $first=false;
}
if ($insertedSelect) {
  printf("</select>");
}
?>
</p>
</card>
```

对于主卡中显示的每个实体（书/音乐专辑），生成一个包含实体描述的卡片：

```
<?php
// Display the details of each card
for($i=0; $i<sizeof($shoppingCart); $i++) {
  $item = $shoppingCartItems[$i]->getItem();
  $itemNo = $item->getItemNo();
?>
```

card 元素的 id 属性设置为实体的 itemNo：

```
<card id="<?php echo($itemNo) ?>">
```

生成一个带有标签 CHG 的类型为 accept 的 <do> 元素。<do> 元素的操作指向 GenChangeQuantityForm.php。该脚本生成一个用于更改商品数量的表单。商品的 itemNo 和会话 ID 字符串作为 URL 参数传递给 GenChangeQuantityForm.php：

```
<do type="accept" label="CHG">
  <go href="GenChangeQuantityForm.php?selectedItem=<?php echo($itemNo)
       ?>&amp;
<?php echo(getSessionIdString()) ?>
"/>
</do>
```

生成一个类型为 options 的 `<do>` 元素，它将带回同一页面的主卡片：

```
<do type="options" label="BACK">
    <go href="#main" />
</do>
<p>
```

### 打印商品的详细信息：

```
<?php
$item = $shoppingCartItems[$i]->getItem();
```

### 打印商品的标题：

```
printf("%s<br/>\n", $item->getTitle());
```

### 打印商品的作者/艺术家：

```
if (strncasecmp($item->getItemType(), 'BOOK', 4) == 0) {
    printf("%s<br/>\n", $item->getAuthor());
} else {
    printf("%s<br/>\n", $item->getArtist());
}
```

### 打印商品的类型：

```
printf("%s<br/>\n", $item->getItemType());
```

### 打印商品的数量：

```
printf("Quantity: %s<br/>\n", $shoppingCartItems[$i]->getQuantity());
```

### 打印商品的价格：

```
printf("$%.2f\n",
    $item->getPrice() * $shoppingCartItems[$i]->getQuantity()); ?>
    </p>
    </card>
    <?php
    } //end for
    ?>
</wml>
