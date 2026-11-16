
$country = trim($country);
$zipCode = trim($zipCode);
$gender = trim($gender);
$age = trim($age);
$emailId = trim($emailId);
$phoneNo = trim($phoneNo);
$cardType = trim($cardType);
$cardNumber = trim($cardNumber);
$cardExpiryDate = trim($cardExpiryDate);

如果任何 URL 参数为 null，则发送错误页面：

```php
if (($fname == "") || ($lname== "") || ($password == "") ||
($userId == "") || ($address== "") || ($city == "") ||
($country == "") || ($zipCode == "") || ($gender == "") ||
($age == "") || ($emailId == "") || ($phoneNo == "") ||
($cardType== "") || ($cardNumber == "") ||
($cardExpiryDate == "")) {
sendErrorPage("Error: Not all the form fields are filled");
exit;
}
```

调用 createUser() 函数创建用户：

```php
createUser($fname, $lname, $password, $userId,
$address, $city, $country,
$zipCode, $gender, $age,
$emailId, $phoneNo, $cardType,
$cardNumber, $cardExpiryDate );
?>
```

只有在用户成功创建时才会到达此处。生成一个显示用户已创建消息的 WML 页面：

```wml
<!DOCTYPE wml PUBLIC "-//WAPFORUM//DTD WML 1.1//EN"
"http://www.wapforum.org/DTD/wml_1.1.xml">
<wml>
<card>
<p>
User <?php echo($userId) ?> created. Go to the
<a href="main.php#login">Login page</a>
</p>
</card>
</wml>
```

## 登录

脚本 Login.php 执行用户身份验证。此脚本从主页面的登录卡片调用：

```php
<?php
include_once("Common.php");
include_once("UserFactory.php");
include_once("ShoppingCart.php");
include_once("User.php");
```

设置会话处理程序：

```php
header("Content-Type: text/vnd.wap.wml");
setSessionHandlers();
```

从 $userId 和 $password 表单变量中删除多余空格：

```php
// Check if the form variables are null
$userId = trim($userId);
$password = trim($password);
```

如果 $userId 或 $password 为 null，则发送错误页面：

```php
if (($userId == "") || ($password == "")) {
    sendErrorPage("The username and password you have entered are invalid.
    Please try again");
    exit;
}
```

加载用户：

```php
$funcResult = loadUser($userId);
if ($funcResult->returnValue == null) {
    sendErrorPage($funcResult->errorMessage);
    exit;
}
$user = $funcResult->returnValue;
```

检查用户的密码：

```php
if (!$user->checkPassword($password)) {
    sendErrorPage("Invalid Password");
    exit;
}
```

创建 PHP 会话：

```php
// Create user session
if (!session_start()) {
    sendErrorPage("Internal Error: Could not create user session");
    exit;
}
```

### 将 isAuthenticated 存储在会话中：

```php
// Register isAuthenticated flag
if (!session_register("isAuthenticated")) {
    sendErrorPage("Internal Error: Could not add isAuthenticated variable
        to the session");
    exit;
}
$isAuthenticated = true;
```

### 将 User 对象存储在会话中：

```php
if (!session_register("user")) {
    sendErrorPage("Internal Error: Could not add user variable to the
        session");
    exit;
}
```

### 创建 Shopping_Cart 对象并将对象存储在会话中：

```php
$shoppingCart = new Shopping_Cart();
if (!session_register("shoppingCart")) {
    sendErrorPage("Internal Error: Could not add shoppingCart variable to
        the session");
    exit;
}
```

### 将 userOrders 存储在会话中：

```php
if (!session_register("userOrders")) {
    sendErrorPage("Internal Error: Could not add userOrders variable to the
        session");
    exit;
}
```

### 将 $bookShopContent 存储在会话中：

```php
if (!session_register("bookShopContent")) {
    sendErrorPage("Internal Error: Could not add bookShopContent variable
        to the session");
    exit;
}
```

### 将 $musicShopContent 存储在会话中：

```php
if (!session_register("musicShopContent")) {
    sendErrorPage("Internal Error: Could not add musicShopContent variable to the session");
    exit;
}
```

### 将 $searchContent 存储在会话中：

```php
if (!session_register("searchContent")) {
    sendErrorPage("Internal Error: Could not add searchShopContent variable
    to the session");
    exit;
}
```

包含 AppMain.php。此脚本显示应用程序的主页面：

```php
<?php
include_once("Common.php");
include_once("User.php");

setSessionHandlers();
header("Content-Type: text/vnd.wap.wml" );
```

如果用户会话未经过身份验证，则发送错误页面：

```php
checkSessionAuthenticated();
```

将以下会话变量的值设置为 null：

```php
$musicShopContent = null;
$bookShopContent = null;
$searchContent = null;
$userOrders = null;
?>
```

### WML 文档类型声明：

```wml
<!DOCTYPE wml PUBLIC "-//WAPFORUM//DTD WML 1.1//EN"
"http://www.wapforum.org/DTD/wml_1.1.xml">
<wml>
```

### 应用程序的主卡片：

```wml
<card id="main">
<p>
```

### 打印问候消息：

```wml
Welcome <?php echo($user->getUserId() ) ?>
<select ivalue="1">
```

生成搜索链接。链接的操作指向同一 WML 页面的搜索卡片：

```wml
<option title="SRCH">
<onevent type="onpick">
<go href="#search"/>
</onevent>
Search
</option>
```

生成查看所有图书标题的链接。链接的操作指向 ViewBookShop.php。请注意，会话 ID 字符串已添加到 URL：

```wml
<option title="BOOK">
<onevent type="onpick">
<go
href="ViewBookShop.php?<?php echo(getSessionIdString()) ?>"/>
</onevent>
Book Shop
</option>
```

生成查看所有音乐专辑的链接。链接的操作指向 ViewMusicShop.php：

```wml
<option title="MUSC">
<onevent type="onpick">
<go
href="ViewMusicShop.php?<?php echo(getSessionIdString()) ?>"/>
</onevent>
Music Shop
</option>
```

生成显示用户购物车内容的链接。链接的操作指向 DisplayCart.php：

```wml
<option title="DISP">
<onevent type="onpick">
<go
href="DisplayCart.php?<?php echo(getSessionIdString()) ?>"/>
</onevent>
Display
</option>
```

生成结账链接。链接的操作指向 CheckOut.php：

```wml
<option title="COUT">
<onevent type="onpick">
<go href="CheckOut.php?<?php echo(getSessionIdString()) ?>"/>
</onevent>
Check Out
</option>
```

生成查看帐户详细信息的链接。链接的操作指向 ViewAccountStatus.php：

```wml
<option title="ASTAT">
<onevent type="onpick">
<go href="ViewAccountStatus.php?
<?php echo(getSessionIdString()) ?>"/>
</onevent>
Account Status
</option>
```

生成登出链接。链接的操作指向 Logout.php：

```wml
<option title="LOFF">
<onevent type="onpick">
<go href="Logout.php?<?php echo(getSessionIdString()) ?>"/>
</onevent>
Logout
</option>
</select>
</p>
</card>
```

搜索卡片。此卡片显示有关搜索功能的消息：

```wml
<card id="search">
<do type="options" label="HOME">
<go href="#main" />
</do>
<p>
Items can be searched for by title and Author/Performer of
Book/CD/Cassette
</p>
```

定义类型为 accept 的 <do> 元素，它将用户带到同一 WML 页面的 searchform 卡片。请注意，在同一页面的卡片之间导航时，不会向服务器发送请求：

```wml
<do type="accept">
<go href="#searchForm" />
</do>
</card>
```

搜索表单卡片：

```wml
<card id="searchForm">
```

定义类型为 options 的 <do> 元素，它将我们带回主卡片：

```wml
<do type="options" label="HOME">
<go href="#main" />
</do>
<p>
```

生成用于输入搜索文本的 input 元素。变量 $searchText 将包含用户输入的搜索文本：

```wml
Enter Search Text:
<input name="searchText" type="text" />
```

生成用于选择搜索条件的 select 元素。变量 $searchType 将包含用户选择的搜索条件：

```wml
Select Search Criteria:
<select name="searchType" ivalue="1">
<option value="Book by Title">Book by Title</option>
<option value="Book by Author">Book by Author</option>
<option value="Music Album by Title">Music Album by Title</option>
<option value="Music Album by Artist">Music Album by Artist</option>
<option value="Entire Database">Entire Database</option>
</select>
</p>
```

定义类型为 accept 的 <do> 元素。<do> 元素的操作是向 DoSearch.php 发送 HTTP GET 请求，将 searchText 和 searchType 的值作为 URL 参数传递：

```wml
<do type="accept">
<go
href="DoSearch.php?searchText=$( searchText :escape)&amp;
searchType=$( searchType :escape)&amp;
<?php echo(getSessionIdString()) ?>" />
</do>
</card>
</wml>
