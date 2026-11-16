

## 购物车中更改数量

脚本 GenChangeQuantityForm.php 用于生成更改购物车商品数量的表单。URL 参数 $selectedItem 包含 $shoppingCartArray 中所选商品的索引：

```php
<?php
include_once("Common.php");
include_once("MusicItem.php");
include_once("BookItem.php");
include_once("ShoppingCart.php");

setSessionHandlers();
header("Content-Type: text/vnd.wap.wml");
```

如果会话未经过身份验证，则发送错误消息：

```php
checkSessionAuthenticated();
```

WML 文档类型声明：

```html
<!DOCTYPE wml PUBLIC "-//WAPFORUM//DTD WML 1.1//EN"
 "http://www.wapforum.org/DTD/wml_1.1.xml">
<wml>
<card>
```

定义一个类型为 options 的 <do> 元素。<do> 元素的操作指向应用程序的主页面 (AppMain.php)：

```html
<do type="options" label="HOME">
 <go href="AppMain.php<?php echo(getSessionIdString()) ?>"/>
</do>
<p>
```

定义一个用于输入新数量的 <input> 元素。用户输入的值存储在 $quantity 变量中：

```php
<?php
$shopCartItem = $shoppingCart->getShoppingCartItem($selectedItem);
$item = $shoppingCart->getItem($selectedItem);
?>
Enter Quantity for <?php echo($item->title()) ?>
<input name="quantity" type="text" format="N"
 value="<?php echo($item->getQuantity()) ?>" />
```

定义一个类型为 accept、标签为 Submit 的 <do> 元素。<do> 元素的操作指向 ChangeQuantity.php。变量 $selectedItem、$quantity 和会话 ID 字符串作为 URL 参数发送：

```xml
<do type="accept" label="Submit">
  <go href="ChangeQuantity.php?selectedItem=<?php echo($selectedItem)?&amp;quantity=$quantity&amp;<?php echo(getSessionIdString()) ?>" />
  </do>
  </p>
  </card>
</wml>
```

脚本 ChangeQuantity.php 更新购物车商品的数量：

```php
<?php
include_once("Common.php");
include_once("ShoppingCart.php");
include_once("BookItem.php");
setSessionHandlers();
header("Content-Type: text/vnd.wap.wml");
// Check if the user is authenticated
checkSessionAuthenticated();
```

更新所选商品的数量：

```php
$shoppingCartItem = $shoppingCart->getShoppingCartItem($selectedItem);
$shoppingCart->changeQuantity($shoppingCartItem->getItem(), $quantity);
```

包含 DisplayCart.php，以显示购物车的内容：

```php
include_once("DisplayCart.php");
```

## 结账

CheckOut.php 实现结账功能：

```php
<?php
include_once("Common.php");
include_once("User.php");
setSessionHandlers();
if (!headers_sent()) {
    header("Content-Type: text/vnd.wap.wml" );
}
checkSessionAuthenticated();
```

调用 User 的 checkout() 函数：

```php
$checkOutDone = $user->checkOut($shoppingCart);
```

清空购物车：

```php
$shoppingCart->clear();
```

### WML 文档类型声明

```html
<!DOCTYPE wml PUBLIC "-//WAPFORUM//DTD WML 1.1//EN"
"http://www.wapforum.org/DTD/wml_1.1.xml">
<wml>
<card id="main">
<do type="options" label="HOME">
<go href="AppMain.php?<?php echo(getSessionIdString()) ?>"/>
</do>
<?php
if ($checkOutDone == FALSE) {
```

如果购物车为空，则显示“购物车中没有商品”消息：

```php
printf("No Items in the Cart\n");
} else {
```

显示一条消息，指示购物车中的商品已发送进行配送：

```php
printf("Cart Items are sent for delivery<br/>");
```

生成一个链接，其操作指向同一 WML 页面的地址卡片：

```php
printf("<a href=\"#address\"> Address Details </a><br/>" );
```

生成一个链接，其操作指向同一 WML 页面的 cardDetails 卡片：

```php
printf("<a href=\"#cardDetails\">
Credit Card Details </a><br/>" );
}
if ($checkOutDone == TRUE) {
```

地址卡片：

```html
<card id="address">
```

定义一个类型为 accept 的 <do> 元素，它将带我们返回本页的主卡片：

```html
<do type="accept" label="BACK">
<go href="#main"/>
</do>
<p>
```

### 显示送货地址

```html
<b> Shipping Address </b>
<?php
$shippingAddress = $user->getShippingAddress();

printf("%s %s<br/>\n", $user->getFirstName(), $user->getLastName());
printf("%s <br/>\n", $shippingAddress->getStreetAddress());
printf("%s <br/>\n", $shippingAddress->getCity());
printf("%s, %s<br/>\n",
     $shippingAddress->getCountry(),
     $shippingAddress->getZipCode());
?>
</p>
</card>
<?php
}
?>
<?php
if ($checkOutDone == TRUE) {
```

### 信用卡详细信息卡片

```html
<card id="cardDetails">
```

### 定义一个类型为 accept、用于返回本页主卡片的 <do> 元素

```html
<do type="accept" label="BACK">
    <go href="#main"/>
</do>
</p>
```

### 显示信用卡详细信息

```html
<b> Card Details </b>
<?php
$creditCard = $user->getCreditCard();

printf("Card No: %s <br/>\n", $creditCard->getCardNumber());
printf("Card Type: %s <br/>\n", $creditCard->getCardType());
printf("Expiry Date:  %s<br/>\n",
     convertDateFromMysqlFormat($creditCard->getExpiryDate()));
?>
</p>
</card>
<?php
}
?>
</wml>
```

## 查看账户详情

ViewAccountStatus.php 显示用户账户的详细信息：

```php
<?php
include_once("Common.php");
include_once("User.php");
include_once("Transaction.php");
include_once("BookItem.php");
include_once("MusicItem.php");

setSessionHandlers();

if (!headers_sent()) {
    header("Content-Type: text/vnd.wap.wml" );
}

checkSessionAuthenticated();
```

如果会话未经过身份验证，则发送错误页面：

```php
checkSessionAuthenticated();
$generateDescCard = null;
```

如果 $userOrders 为 null，则表示页面是第一次被调用：

```php
if (!$userOrders) {
}
```

将 $currentIndex 设置为零：

```php
$currentIndex = 0;
```

获取用户的事务：

```php
$userOrders = $user->getTransactions();
}
```

WML 文档类型声明：

```html
<!DOCTYPE wml PUBLIC "-//WAPFORUM//DTD WML 1.1//EN"
    "http://www.wapforum.org/DTD/wml_1.1.xml">
<wml>
```

主卡片：

```html
<card id="main">
    <do type="options" label="HOME">
        <go href="AppMain.php?<?php echo(getSessionIdString()) ?>"/>
    </do>
    <p>
    <b> Account Status </b> <br/>
```

显示用户的账户余额：

```html
<b> Balance: </b>
<?php printf("$%.2f\n", $user->getAccountBalance() ) ?> <br/>
<?php
```

显示用户事务（最多三个）。链接的操作指向同一 WML 页面内包含事务详细信息的 WML 卡片：

```php
if ($currentIndex < sizeof($userOrders)) {
printf("<select>\n");
for($i=0; (($i < 3) && ($currentIndex < sizeof($userOrders))); $i++ ) {
$item = $userOrders[$currentIndex]->getItem();
generateOptionElement("#card".
$userOrders[$currentIndex]->getOrderNo(),
$item->getTitle());
}
```

$generateDescCard 数组包含需要生成描述卡片的索引列表：

```php
$generateDescCard[] = $currentIndex;
$currentIndex++;
}
```

如果还有更多用户事务需要显示，则生成一个以 ViewAccountStatus.php 为操作的链接。$currentIndex 变量和会话 ID 字符串作为 URL 参数传递：

```php
if ($currentIndex < sizeof($userOrders)) {
$nextHref = "ViewAccountStatus.php?currentIndex=" .
$currentIndex . "&amp;" . getSessionIdString();
generateOptionElement($nextHref, "View Next Items");
}
printf("</select>\n");
}
?>
</p>
</card>
```

为主卡片中显示的每个事务生成一个包含实体描述的卡片：

```php
<?php
// Display the details of each card
for($i=0; $i<sizeof($generateDescCard); $i++) {
$orderNo = $userOrders[$generateDescCard[$i]]->getOrderNo(); ?>
```

<card> 元素的 id 属性设置为事务的订单编号：

```html
<card id="card<?php echo($orderNo) ?>" >
```

定义一个类型为 accept 的 <do> 元素，它将带我们返回同一页面的主卡片：

```html
<do type="accept" label="BACK">
<go href="#main" />
</do>
<do type="options" label="HOME">
<go href="AppMain.php?<?php echo(getSessionIdString()) ?>"/>
</do>
<p>
```

打印事务详细信息：

```php
<?php
$item = $userOrders[$generateDescCard[$i]]->getItem();
```

打印商品标题：

```php
printf("%s<br/>\n", $item->getTitle());
```

打印商品的作者/艺术家：

```php
if (strncasecmp($item->getItemType(), 'BOOK', 4) == 0) {
printf("%s<br/>\n", $item->getAuthor());
} else {
printf("%s<br/>\n", $item->getArtist());
}
```

打印商品数量：

```php
printf("Quantity: %s<br/>\n",
$userOrders[$generateDescCard[$i]]->getQuantity());
```

打印事务日期：

```php
printf("Date:%s<br/>\n",
convertDateFromMysqlFormat($
userOrders[$generateDescCard[$i]]->getDate()));
```

打印商品状态（待处理/已发货）：

```php
printf("Status:%s<br/>\n",
$userOrders[$generateDescCard[$i]]->getStatus());
?>
</p>
</card>
<?php
} //end for
?>
</wml>

