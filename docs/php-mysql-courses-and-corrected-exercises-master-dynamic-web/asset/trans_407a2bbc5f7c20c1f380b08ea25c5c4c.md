

域根目录。

要删除 Cookie，可以将其值设置为空，并指定过去的过期日期。这会告诉浏览器删除该 Cookie。同样，请确保指定与原始 Cookie 相同的选项，以确保 Cookie 被正确删除。

```php
<?php
// Set an expiration date in the past to delete the cookie
setcookie('user', '', time() - 3600, '/');
?>
```

在本示例中，我们通过将用户 Cookie 的值设置为空字符串并指定过去的过期日期来删除该 Cookie。这会导致 Cookie 在用户的浏览器中立即过期，从而将其永久删除。

# Cookie 安全性

需要注意的是，Cookie 存储在客户端，用户可以对其进行修改。因此，不要在 Cookie 中存储敏感信息，并在将数据用于应用程序之前，务必验证并清理所有数据。

Cookie 管理是现代 Web 开发的重要组成部分，它为在用户浏览器上存储临时信息提供了一种便捷的方式。然而，理解其局限性并安全地使用它们至关重要，以保证应用程序数据的完整性和机密性。

# Session 管理

PHP 中的 Session 是一种在不同 HTTP 请求之间维护 Web 应用程序状态的基本技术。Session 是一种在浏览网站时存储用户特定信息的方法，例如用户身份验证、购物车、用户偏好设置等。与 Cookie 不同，Session 数据存储在服务器上，因此更安全，因为它不会暴露给客户端。

## Session 管理流程

PHP Session 管理流程包含以下步骤：

- **Session 启动：** 在使用 Session 之前，需要通过调用 session_start() 函数来启动一个 Session。该函数会初始化一个新 Session，如果 Session 已存在，则恢复该 Session。

- **将数据存储在 Session 中：** 启动 Session 后，可以使用 $_SESSION 关联数组在 Session 中存储数据。$_SESSION 中存储的数据在 Session 期间可用于网站的所有页面。

- **访问 Session 数据：** 要访问存储的 Session 数据，只需使用带有相应键的 $_SESSION 数组来访问相应的值即可。

- **关闭 Session：** 使用完 Session 后，可以通过调用 session_destroy() 函数来关闭它。这将销毁所有现有的 Session 数据。

## Session 的优势

- **安全性：** Session 数据存储在服务器上，因此比客户端 Cookie 更安全。

- **持久性：** Session 数据在 Session 期间始终可用，即使用户在网站的不同页面之间导航。

- **灵活性：** Session 可以存储大量数据，因此非常适合管理敏感或复杂的信息。

## 实际示例

为了更好地理解 Session 的工作原理，让我们以带有会员区的网站为例。每个用户都必须登录才能访问该区域，并且必须保证用户在其在网站上的整个 Session 期间保持已识别状态。

为此，我们需要为用户提供一个登录表单：

首先，让我们创建一个新的 connection.php 文件，并在其中放入以下表单：

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Connect to member area</title>
</head>
<body>
<h2>Connect to member area</h2>
<form action="verification.php" method="post">
<div>
<label for="username">Username:</label>
<input type="text" id="username" name="username">
</div>
<br>
<div>
<label for="password">Password:</label>
<input type="password" id="password" name="password">
</div>
<div>
<input type="submit" value="Login">
</div>
</form>
</body>
</html>
```

该表单通过 POST 方法将用户输入的数据发送到名为 "verification.php" 的验证脚本。它包含两个字段：一个用于用户名（"text" 类型），另一个用于密码（"password" 类型）。

verification.php 文件将负责验证用户提供的信息，以授权或拒绝访问会员区。但为了本示例的目的，我们的目标是解释 Session 的工作原理，以便数据可以从一页传递到另一页。

为了将我们的示例付诸实践，我们创建了一个名为 "verification.php" 的文件，在其中为测试目的定义了基本用户名和密码。理想情况下，在实际场景中，我们将查询数据库以验证用户提供的信息的真实性。

## 启动和存储 Session 数据

```php
<?php
// Basic username and password for tests
$valid_username = "toto";
$valid_password = "azerty123";

// Check if form data has been sent
if (isset($_POST['username']) && isset($_POST['password'])) {
    // Check that username and password are correct
    if ($valid_username == $_POST['username'] && $valid_password == $_POST['password']) {
        // Start session
        session_start();

        // Save session parameters
        $_SESSION['username'] = $_POST['username'];
        $_SESSION['password'] = $_POST['password'];

        // Display a welcome message and a link to the members' area
        echo "Logged in as " . $_SESSION['username'] . "<br />";
        echo 'You can access the members\' area: <a href="members.php">Link to members\' page</a>';
    } else {
        // Error message if username or password is incorrect
        echo 'Sorry, the username or password is incorrect.';
    }
} else {
    // Message if form data not sent
    echo 'You need to go to the login page.';
}
?>
```

以下是代码的详细解释：

- **初始化变量：**

$valid_username 和 $valid_password 被定义为连接的有效用户名和密码。
在实际场景中，这些值通常会与数据库或其他身份验证系统进行核对。

- **检查表单数据：**

if 条件 (isset($_POST['username'])) && isset($_POST['password'])) 检查表单数据是否已通过 POST 方法提交。

- **检查登录名和密码：**

如果已提交表单数据，代码会检查用户名和密码是否与先前定义的有效值相符。这是通过条件 if ($valid_username == $_POST['username'] && $valid_password == $_POST['password']) 完成的。

- **启动 Session：**

如果登录名和密码正确，则通过 session_start() 启动一个 Session。随后，用户信息会通过 $_SESSION['username'] 和 $_SESSION['password'] 存储在 Session 变量中。

- **消息显示：**

如果登录名和密码正确，将显示一条欢迎消息，其中包含已登录用户的名称以及指向会员专用页面的链接。

![](img/caba2aa22f5409ba73dea47176330677_337_0.png)

如果用户 ID 或密码不正确，将显示一条错误消息来通知用户。

![](img/caba2aa22f5409ba73dea47176330677_338_0.png)

- **错误情况管理：**

如果未提交表单数据，将显示一条消息，告诉用户前往登录页面。
这段代码展示了 PHP 中登录和密码验证以及 Session 管理的简单示例。

# 访问 Session 数据

在 members.php 页面中（用户登录后将被重定向到该页面），应通过验证其 Session 信息的存在来检查用户是否已登录。如果用户已登录，则可以显示会员专用内容。

以下是你可以在 members.php 页面中包含的示例：

```php
<?php
session_start();

// Check if user is logged in
if (isset($_SESSION['username']) && isset($_SESSION['password'])) {
    // Display members-only content
    echo 'Welcome to the members\' area, ' . $_SESSION['username'];
    echo '<br>';
    echo 'Members-only content...<br />';
    echo '<a href="logout.php">Log out</a>'; // link for disconnect
} else {
    // Redirect user to login page if not logged in
    header('Location: login.php');
    exit();
}
?>
```

这段 PHP 代码检查用户是否已以会员身份登录。其工作原理如下：

第一步是通过调用 **session_start()** 函数来启动 Session，该函数必须在代码的最开头声明。这使得可以访问存储的 Session 信息。

接下来，代码会通过验证 $_SESSION 数组中是否存在 "username" 和 "password" 键来检查用户的 Session 信息是否存在。这些键包含在连接时存储的用户身份识别信息。

