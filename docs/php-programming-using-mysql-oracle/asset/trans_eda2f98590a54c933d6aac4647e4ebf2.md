

# Cookie 示例

```html
<html><head><title>Cookie Example</title></head><body><form action="cookie.php" method="post"> Yellow<input type="radio" name="color" value="Yellow"/>Red<input type="radio" name="color" value="Red"/>Blue<input type="radio" name="color" value="Blue"/><br>Please complete the feedback form and send your preference of color. </p><p><input type ="submit" name="submit" value="color"></form></body></html>
```

输出如下。

![](images/00036.jpeg)

![](images/00037.jpeg)

![](images/00038.jpeg)

因此该 cookie 的持续时间从当前时间算起为 60 秒。如果需要 1 小时，则为 `time() + 3600`，以此类推。安全标志的数字 `0` 表示 cookie 不会通过安全连接发送。替代方案是用于 HTTPS 连接的 `1`。

在 60 秒或 1 分钟后，如果使用 `$_COOKIE['color']` 选项读取 cookie，则找不到任何值。将会显示错误消息。

要删除 cookie，可以按以下方式使用 `setcookie()`。

```php
setcookie('cookiename',' ');
```

```php
setcookie('cookiename', ' ', time()-60);
```

这相当于将过期日期设为过去。

让我们来看这段代码。

```php
<?php$cookies=false;if(isset($_POST['submit'])){setcookie('color',$_POST['color'], time()+60,' ',' ',0);$cookies=true;}?><html><head><title>Cookie Example</title></head><body><form action="cookie.php" method="post"> Yellow<input type="radio" name="color" value="Yellow"/>Red<input type="radio" name="color" value="Red"/>Blue<input type="radio" name="color" value="Blue"/><br>Please complete the feedback form and send your preference of color.</p><p><input type ="submit" name="submit" value="color"></form><?phpif($cookies) {print"Your preference has been saved.";}?></body></html>
```

基本上上面的代码是 cookie PHP 文件及其 HTML 页面的组合。唯一的补充是行 `if(isset($_POST['submit'])){ }`，此条件和 PHP 中的函数允许我们将 cookie 的 PHP 文件写成单个文件，而不是两个不同的文件。

`isset()` 函数检查 HTML 表单中的提交按钮是否已被点击。如果是，它将继续执行括号内的行，即创建 cookie。大多数网站托管服务将允许这种 PHP 和 HTML 在单个 PHP 文件中的混合。也可能在 HTML 文件中包含 PHP。在注册前或之后请向托管服务核实他们可能要求的任何配置。此建议适用于使用共享托管的用户。

## Session

会话提供了一种在多个页面上跟踪用户数据的方法。Cookie 将数据存储在客户端，而会话将其存储在服务器上。除此之外，会话具有以下特征。

1. 它们更安全，因为数据仅在服务器上。
2. 它们允许存储比 cookie 更多信息。
3. 即使用户不接受 cookie，它们也可以正常工作。

会话就像英文单词的含义一样（一段时期，如课堂会话）。会话开始时，会创建一个随机会话 ID。这是引用该特定会话及其存储数据的标识。

会话 ID 会作为 cookie 发送到 Web 浏览器，后续的 PHP 页面将使用此 cookie 获取会话 ID 以访问其数据。

要在 PHP 中启动或创建会话，我们从 `session_start()` 函数开始。此函数必须是使用会话的每个 PHP 页面上的第一行之一。

发送到浏览器的 cookie 将具有 `PHPSESSID` 之类的名称和 `3bcc37dc87cb4b54d63f99da23fb41f1` 之类的值。

一旦会话开始，可以通过为 `$_SESSION` 数组分配值来记录数据到其中。

```php
$_SESSION['color'] ='Yellow';
$_SESSION['age'] =35;
```

数据会写入服务器上存储的临时文件。让我们来看下面的代码。

此代码用于登录框。

```php
<?phpif(isset($_POST['submit'])){if ($_POST['username']=='admin' && $_POST['password']=='admin'){session_start();$_SESSION['username'] ='admin';$_SESSION['login'] =time();print"You are logged in";exit();}}?><html><head><title>Session Example</title></head><body><form action="session.php" method="post"> <p>Username:<input type="text" name="username" size="20"><p>Password:<input type="text" name="password" size ="20"><p><input type ="submit" name="submit" value="Submit"></form></body></html>
```

登录框如下所示。

![](images/00039.jpeg)

此代码从上一个 cookie 示例中看到的 `isset` 函数开始。这检查提交按钮是否被点击。

下一个 `if` 语句检查密码和用户名是否符合要求。如果是，它将打印一条消息并且 `exit()` 函数将停止执行任何进一步的代码。或者如果要重定向到欢迎页面，可以使用 `header()` 函数，如下所示- `header('Location:welcome.php');` 后跟 `exit();` 在上面的代码中进行更改。

如果输入的用户名和密码不正确，程序将显示一个空表单以供再次登录尝试。

因此现在我们已为登录页面启动了会话。要访问会话变量，让我们首先创建 `welcome.php` 文件，以便用户登录后将获得此页面。

从此页面我们将访问用户的登录时间段。

欢迎页面的代码如下所示。

```php
<?phpsession_start();print"Welcome to my webpage!!<p>";print ($_SESSION['username']);print"<p>You have logged in since:<p>";print date('g:i a',$_SESSION['login']);print "<p><a href=logout.php>Logout</a>";?>
```

此代码将打印欢迎消息、用户名、登录时间并提供注销选项。此代码的输出如下。

![](images/00040.jpeg)

注销页面脚本如下所示。

```php
<?phpprint"You have logged out!!<p>";?>
```

注销脚本将很快更改。会话中的最后一点是如何删除会话。

为此，从 `session_start()` 开始，然后使用 `unset()` 函数删除会话变量，在我们的示例中为用户名和登录时间。

```php
unset($_SESSION);
```

最后，使用 `session_destroy()` 函数从服务器删除数据。因此，上面的注销脚本将如下所示。

```php
<?phpsession_start();unset($_SESSION);session_destroy();print"You have logged out!!<p>";print"Thank you for visiting my page.";?>
```

在看到注销页面后，尝试点击返回按钮，看看会发生什么。

输出如下：

![](images/00041.jpeg)

需要注意的是，会话可能在共享类型的 Web 托管上以略有不同的方式实现。因此，重要的是要检查 Web 主机的常见问题解答表或技术支持，了解它是如何为这种类型的托管配置的。

## PHP 中的用户自定义函数

PHP 中的函数可以由用户创建。到目前为止看到的函数已经在 PHP 中定义。

用户自定义函数在没有已知函数执行特定任务时很有用。函数就像所有编程语言中的一样，减少了代码的重复，实际上减少了整体代码行的大小。

创建函数的格式如下：

```php
function function_name() {
statements;
}
```

函数名遵循变量名的相同规则，只是函数没有 `$` 符号。`{}` 内的语句可以是任何有效的 PHP 语句。

现在让我们看一个用户制作的函数。这个函数叫做 `make_car_menu`，从名字上可以明显看出这个函数与汽车有关。

```php
<?phpfunction make_car_menu (){$car =array(1=>'Nissan',2=>'GM',3=>'Ford',4=>'Toyota',5=>'Mazda',6=>'Tesla',7=>'Mitsubishi',8=>'Hyundai',9=>'VW',10=>'BYD');print"<select name='car'>";foreach ($car as $key=>$value){print"<option value=$key>$value</option>";}print"<select>";}//end of functionprint"<form action='' method='post'>";make_car_menu();print"</form>";?>
```

