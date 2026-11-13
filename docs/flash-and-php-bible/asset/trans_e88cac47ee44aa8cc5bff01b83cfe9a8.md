

{
    login.close();
}

> 注意：此应用程序不存储登录信息，这意味着有效的登录仅限于当前会话。用户每次访问应用程序时都必须登录。

loginHandler 函数用于处理成功的登录，但不会在登录尝试不正确时通知用户。可以通过添加一个 else 语句来修复此问题，该语句会更新登录框中的响应框。

```
function loginHandler(e:Event):void
{
    if(login.data.username == "guest" && login.data.password == "pass")
    {
        login.close();
    }
    else
    {
        login.responseString = "username and password incorrect";
    }
}
```

最后一步是对 resize 事件进行初始调用，以首次绘制登录组件。您也可以直接调用 redraw 方法，而无需经过 resize 事件。

```
stage.dispatchEvent(new Event(Event.RESIZE));
```

以下是此测试的完整代码。登录组件的大部分内容在内部处理，但它仍然提供了卓越的可用性。

```
var login:LoginWindow = new LoginWindow();
login.addEventListener(LoginWindow.LOGIN_ATTEMPT, loginHandler);

addChild(login);

stage.align = StageAlign.TOP_LEFT;
stage.scaleMode = StageScaleMode.NO_SCALE;
stage.addEventListener(Event.RESIZE, stageResizeHandler);

function stageResizeHandler(e:Event):void
{
    login.redraw();
}

function loginHandler(e:Event):void
{
    trace("Do Login");
    trace("Username: " + login.data.username);
    trace("Password: " + login.data.password);

    if(login.data.username == "guest" && login.data.password == "pass")
    {
        trace("user logged in");
        login.close();
    }
    else
    {
        login.responseString = "username and password incorrect";
    }
}

stage.dispatchEvent(new Event(Event.RESIZE));
```

现在您已为示例完成所需的 ActionScript，可以测试登录组件。您应该会立即看到登录屏幕，并且在输入正确的登录信息之前，无法与电影中的任何部分交互（登录屏幕除外），如图 17.6 所示。

### 图 17.6
显示登录组件的示例应用程序

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_496_0.png)

## 构建 PHP 登录管理器类

构建登录系统的下一步是将其连接到用户数据库，因为硬编码的登录名和密码不太实用，当然也不安全。

## 创建用户的 MySQL 表

第一步是在现有数据库中创建用户表：

```
CREATE TABLE `users` (
 `id` int(11) NOT NULL auto_increment,
 `username` varchar(25) default NULL,
 `password` varchar(40) default NULL,
 `active` varchar(1) default '1',
 PRIMARY KEY (`id`)
) ENGINE=MyISAM;
```

然后，您可以使用一些示例登录名预填充表，以供测试之用：

```
INSERT INTO users (username, password) VALUES ('guest',
MD5('pass'));
INSERT INTO users (username, password) VALUES ('timmy',
MD5('bird'));

```

与 Flash 中预定义的登录名不同，这些登录名的密码是加密的，作为额外的安全级别。

在添加连接到服务的逻辑之前，您需要创建 PHP 类。此类将检查有效用户，如果找到一个，它将返回 true，这意味着用户有效，登录框可以被移除。

## 构建用户类

User.php 类与其他服务类类似，它扩展了 DatabaseConnector 类以进行所有数据库通信。以下是用户类的框架：

```
<?php

require_once 'DatabaseConnector.php';

class User extends DatabaseConnector
{
 function User()
 {
 ...
 }
}

?>
```

### login 方法

此类中第一个也是唯一的方法是 login。该方法接受两个参数：要验证的用户名和密码。该方法的第一部分是创建到数据库的新连接：

```
/**
 * Check user auth
 * @access remote
 * @returns status of user login attempt
 */
function login($user, $pass)
{
	$link = $this->getConnection();
}
```

建立数据库连接后，您可以将用户标记为未登录。这可以防止任何可能意外使用户登录的黑客攻击尝试。

```
$loggedIn = false;
```

接下来是尝试验证用户名和密码组合的 SQL 查询。密码被传递到 md5 函数中，因为 Flash 以明文发送密码，但数据库存储的是 md5 结果。

```
$query = sprintf("SELECT * FROM users WHERE username='%s' AND password=MD5('%s')", $user, ($pass));
```

下一步是进行数据库调用并将响应存储在 $result 变量中，如下面的代码所示：

```
$result = mysql_query($query, $link);
```

存储响应后，会使用条件语句来确定是否返回了任何行。如果返回了一行，则表示数据有效，并且用户已根据其提供的凭据进行身份验证。

当找到有效响应时，将 $loggedIn 变量设置为 true，以告知 Flash 用户确实有效，并且现已成功登录。

```
if(mysql_num_rows($result) > 0)
{
	$loggedIn = true;
}
```

最后一步是返回结果，以便 Flash 可以相应地采取行动。

```
return array('response' => $loggedIn);
```

现在您已完成 PHP 类，下一步是对其进行测试。为此项测试，您可以使用随 AMFPHP 一起提供的服务浏览器。您将在类似于以下网址的位置找到该浏览器，具体取决于您安装源的位置：

```
http://localhost/flashphp/amfphp/browser/
```

最后，以下是完整的 User 类，如果您尚未保存，应将其保存为 AMFPHP 安装目录 services 目录下的 User.php：

```
<?php
require_once 'DatabaseConnector.php';
class User extends DatabaseConnector
{
/**
* Check user auth
* @access remote
* @returns status of user login attempt
*/
function login($user, $pass)
{
$link = $this->getConnection();
$loggedIn = false;
$query = sprintf("SELECT * FROM users WHERE username='%s' AND password=MD5('%s')", $user, ($pass));
$result = mysql_query($query, $link);
if(mysql_num_rows($result) > 0)
{
$loggedIn = true;
}
return array('response' => $loggedIn);
}
}
?>
```

## 为登录组件添加远程处理

现在您已完成 PHP User 类，下一步是修改现有登录组件以使用此新服务类。

第一步是添加 gateway 变量以及开发服务器上可找到 gateway.php 文件的 URL。

```
var gateway:NetConnection;
var gatewayURL:String = "http://localhost/amfphp/gateway.php";
```

原示例直接在 Flash 文件中执行用户名验证。虽然这很实用，但不太实际，因为只能使用一个登录名或密码。

### loginHandler 方法

此新系统通过添加远程服务调用来修改现有 loginHandler 函数，发送登录窗口组件捕获的用户名和密码。

```
function loginHandler(e:Event):void
{
    trace("Do Login");
    trace("Username: " + login.data.username);
    trace("Password: " + login.data.password);

    var responder:Responder = new Responder(loginRespHandler,
    onFault);
    gateway = new NetConnection();
    gateway.connect(gatewayURL);
    gateway.call("User.login", responder,
    login.data.username,
    login.data.password
    );
}
```

Responder 类需要定义响应处理程序，因此下一个函数处理此服务响应。在此示例中，该服务将返回一个布尔值，指示用户是否已登录，或者在出错时返回一个错误。

```
function loginRespHandler(o:Object):void
{
    ...
}
```

使用一个简单的条件语句来根据远程服务的响应确定用户是否已登录。

### 处理登录响应

如果用户已登录，则会调用登录组件的 close 方法来隐藏登录窗口并启用应用程序界面。

```
function loginRespHandler(o:Object):void
{
    if(o.response == true)
    {
    login.close();
    }
}
```

