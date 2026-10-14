
***

### 复习与实践

如果您对复习问题或实践提示有任何疑问，请访问本书的支持论坛（[www.LarryUllman.com/forums/](http://www.LarryUllman.com/forums/)）。

#### 复习

*   发送电子邮件使用什么函数？该函数的参数有哪些？服务器发送电子邮件需要什么条件？
*   `\n` 在单引号和双引号中使用有区别吗？
*   能否确切知道收件人是否以及何时收到了 PHP 发送的电子邮件？
*   如果没有收到 PHP 脚本本应发送的任何电子邮件，可以采取哪些调试步骤？
*   文件夹权限在处理上传文件时起什么作用？
*   处理文件上传时使用哪两个目录？
*   为了处理文件上传，必须在开始 `form` 标记中添加什么额外属性？
*   什么是 MIME 类型？
*   PHP 和 JavaScript 有哪些相似之处？有哪些不同之处？
*   向 HTML 页面添加 JavaScript 使用什么标记？
*   JavaScript 中 `var` 关键字是什么意思？
*   JavaScript 中的连接运算符是什么？
*   PHP `header()` 函数有什么作用？
*   *headers already sent*（标头已发送）错误消息是什么意思？
*   什么是*代理脚本*？何时可能需要代理脚本？
*   `readfile()` 函数有什么作用？

#### 实践

*   创建一个更定制的联系表单。让 PHP 脚本也发送一封更定制的电子邮件，包含表单请求的任何其他数据。
*   使用关键词 *php email spam filters* 在线搜索，了解提高 PHP 发送邮件成功投递率的技巧（即最大限度地减少垃圾邮件过滤器拦截合法邮件的可能性）。
*   制作 `upload_image.php` 的一个变体，支持上传不同的文件类型。创建相应版本的 `show_image.php`。注意：您需要研究 MIME 类型才能完成这些挑战。
*   查看 PHP 手册中关于 `glob()` 函数的页面。
*   本章介绍了大量信息和新函数。查阅 PHP 手册中的相关内容以了解更多。

## 12. Cookie 和 Session

本章内容

*   制作登录页面 368
*   制作登录函数 371
*   使用 Cookie 376
*   使用 Session 388
*   提高 Session 安全性 396
*   复习与实践 400

### 超文本传输协议 (HTTP) 是一种 `stateless` 技术

超文本传输协议 (HTTP) 是一种 `stateless` 技术，这意味着每个单独的 HTML 页面都是一个无关的实体。HTTP 没有跟踪用户或在用户浏览网站时保留变量的方法。如果没有服务器跟踪用户的能力，就不可能有购物车或定制的网站个性化功能。使用像 PHP 这样的服务器端技术，你可以克服 Web 的无状态性。为此目的最好的两个 PHP 工具是 `cookies` 和 `sessions`。

Cookie 和 Session 的关键区别在于：Cookie 将数据存储在用户的 Web 浏览器中，而 Session 将数据存储在服务器本身上。Session 通常比 Cookie 更安全，并且可以存储更多的信息。由于这两种技术在 PHP 中都很容易使用且值得掌握，本章将同时介绍 Cookie 和 Session。用于演示这些信息的示例将是一个登录系统，基于现有的 `sitename` 数据库。

#### 制作登录页面

登录过程仅涉及几个组件：

*   一个用于提交登录信息的表单
*   一个确认已提交必要信息的验证例程
*   一个将提交的信息与存储的信息进行比较的数据库查询
*   用于存储反映登录成功数据的 Cookie 或 Session

后续页面随后可以进行检查，以确认用户已登录（以限制对该页面的访问或添加功能）。当然，还有一个注销过程，它涉及清除代表已登录状态的 Cookie 或 Session 数据。

为了开始这一切，让我们获取一些这些通用元素并将它们放入单独的文件中。然后，需要此功能的页面可以包含必要的文件。以这种方式分解逻辑将使一些后续脚本更易于阅读和编写，并减少冗余。你将定义两个可包含的文件。第一个脚本将包含登录页面的主要部分，包括页眉、错误报告、表单和页脚。

#### 脚本 12.1：`login_page.inc.php` 脚本

`login_page.inc.php` 脚本创建完整的登录页面，包括表单，并报告任何错误。它将被其他需要显示登录页面的页面包含。

```php
<?php # Script 12.1 - login_page.inc.php

// This page prints any errors
// associated with logging in
// and it creates the entire login page,
// including the form.

// Include the header:
$page_title = 'Login';
include ('includes/header.html');

// Print any error messages, if they exist:
if (isset($errors) && !empty($errors)) {
    echo '<h1>Error!</h1>
<p class="error">The following
    error(s) occurred:<br />';
    foreach ($errors as $msg) {
        echo " - $msg<br />\n";
    }
    echo '</p><p>Please try again.</p>';
}

// Display the form:
?><h1>Login</h1>
<form action="login.php" method="post">
    <p>Email Address: <input type="text"
        name="email" size="20" maxlength="60" />
    </p>
    <p>Password: <input type="password"
        name="pass" size="20" maxlength="20" />
    </p>
    <p><input type="submit" name="submit"
        value="Login" /></p>
</form>
<?php include ('includes/footer.html'); ?>
```

#### 制作登录页面

**1.** 在文本编辑器或 IDE 中开始一个新的 PHP 页面，命名为 `login_page.inc.php`（脚本 12.1）：

```php
<?php # Script 12.1 - login_page.inc.php
```

**2.** 包含页眉：

```php
$page_title = 'Login';
include ('includes/header.html');
```

本章将使用第 3 章“创建动态网站”中首创、第 9 章“将 PHP 与 MySQL 结合使用”中修改的相同模板系统。

**3.** 如果存在错误消息则打印它们：

```php
if (isset($errors) && !empty($errors)) {
    echo '<h1>Error!</h1>
    <p class="error">The following error(s) occurred:<br />';
    foreach ($errors as $msg) {
        echo " - $msg<br />\n";
    }
    echo '</p><p>Please try again.</p>';
}
```

这段代码也是在第 9 章中开发的，尽管增加了一个额外的 `isset()` 子句作为预防措施。如果存在任何错误（在 `$errors` 数组变量中），它们将作为无序列表打印出来。

**4.** 显示表单：

```php
?><h1>Login</h1>
<form action="login.php" method="post">
    <p>Email Address: <input type="text" name="email" size="20" maxlength="60" /> </p>
    <p>Password: <input type="password" name="pass" size="20" maxlength="20" /></p>
    <p><input type="submit" name="submit" value="Login" /></p>
</form>
```

HTML 表单只需要两个文本输入框：一个用于电子邮件地址，另一个用于密码。输入框的名称与 `sitename` 数据库 `users` 表中的名称相匹配（该登录系统即基于此数据库）。

为了更容易创建 HTML 表单，首先关闭 PHP 部分。该表单不是粘性的，但你可以轻松添加代码来实现该功能。

**5.** 完成页面：

```php
<?php include ('includes/footer.html'); ?>
```

**6.** 将文件保存为 `login_page.inc.php` 并将其放在你的 Web 目录中（在 `includes` 文件夹中，与第 3 章和第 9 章的文件 `header.html`、`footer.html` 和 `style.css` 放在一起）。

该页面将使用 `.inc.php` 扩展名，以表明它既是一个可包含的文件，又包含 PHP 代码。

> **提示**
>
> 该脚本从 `includes` 目录中包含页眉和页脚文件，而该脚本本身也将位于同一目录中，这看起来可能不合逻辑。这段代码之所以有效，是因为该脚本将被主目录中的页面包含；因此包含引用是相对于父文件的，而不是相对于该文件的。

### 制作登录函数

除了存储在 `login_page.inc.php` 中的登录页面外，还有一小部分功能将是本章中多个脚本的通用部分。在接下来的这个脚本中（也将被登录/注销系统中的其他页面包含），将定义两个函数。

首先，许多页面最终会将用户从一个页面重定向到另一个页面。例如，成功登录后，用户将被带到 `loggedin.php`。如果用户访问 `loggedin.php` 但未登录，他们应该被带到 `index.php`。重定向使用第 11 章“Web 应用程序开发”中介绍的 `header()` 函数。重定向的语法是：

```php
header ('Location: http://www.example.com/page.php');
```

由于此函数会将浏览器发送到 `page.php`，因此应在之后立即使用 `exit()` 终止当前脚本：

```php
header ('Location: http://www.example.com/page.php');
exit();
```

如果不调用 `exit()`，当前脚本将继续运行（只是不在 Web 浏览器中）。

`header()` 调用中的 location 值应该是一个绝对 URL（`http://www.example.com/page.php` 而不是仅仅 `page.php`）。你可以将此值硬编码到每个 `header()` 调用中，或者更好的是，让 PHP 动态确定它。这个脚本中的第一个函数将做到这一点，然后将用户重定向到该绝对 URL。

#### 创建登录函数

本章中多个脚本将使用的另一段代码用于验证登录表单。这是一个三步过程：

1. 确认提供了电子邮件地址。
2. 确认提供了密码。
3. 确认提供的电子邮件地址和密码与数据库中存储的匹配（注册过程中存储）。

接下来的脚本将定义两个不同的函数。每个函数的工作细节将在后续步骤中解释。

#### 创建登录函数

**1.** 在文本编辑器或 IDE 中开始一个新的 PHP 文档，命名为 `login_functions.inc.php`（**脚本 12.2**）：

```php
<?php # Script 12.2 - login_functions.inc.php
```

由于此文件将被其他文件包含，因此不需要包含任何 HTML。

**2.** 开始定义一个新函数：

```php
function redirect_user ($page = 'index.php') {
```

`redirect_user()` 函数将创建一个适合运行这些脚本的站点的绝对 URL，然后将用户重定向到该页面。动态执行此操作的好处（相对于硬编码 `http://www.example.com/page.php`）在于：你可以在一台服务器（如你自己的电脑）上开发代码，然后将其移至另一台服务器，而无需更改此代码。

该函数接受一个可选参数：最终目标页面名称。默认值为 `index.php`。

**3.** 开始定义 URL：

```php
$url = 'http://' . $_SERVER['HTTP_HOST'] . dirname($_SERVER['PHP_SELF']);
```

**脚本 12.2.** `login_functions.inc.php` 脚本定义了两个函数，将在登录/注销过程中由不同脚本使用。

```php
<?php # Script 12.2 - login_functions.inc.php
// This page defines two functions used
// by the login/logout process.

/* This function determines an absolute
 * URL and redirects the user there.
 * The function takes one argument: the
 * page to be redirected to.
 * The argument defaults to index.php.
 */
function redirect_user ($page = 'index.php') {

    // Start defining the URL...
    // URL is http:// plus the host name
    // plus the current directory:
    $url = 'http://' . $_SERVER['HTTP_HOST'] . dirname($_SERVER['PHP_SELF']);

    // Remove any trailing slashes:
    $url = rtrim($url, '/\\');

    // Add the page:
    $url .= '/' . $page;

    // Redirect the user:
    header("Location: $url");
    exit(); // Quit the script.

} // End of redirect_user() function.


/* This function validates the form data
 * (the email address and password).
 * If both are present, the database is
 * queried.
 * The function requires a database
 * connection.
 * The function returns an array of
 * information, including:
 * - a TRUE/FALSE variable indicating
 *   success
 * - an array of either errors or the
 *   database result
 */
function check_login($dbc, $email = '', $pass = '') {

    $errors = array(); // Initialize error array.

    // Validate the email address:
    if (empty($email)) {
        $errors[] = 'You forgot to enter your email address.';
    } else {
        $e = mysqli_real_escape_string($dbc, trim($email));
    }

    // Validate the password:
    if (empty($pass)) {
        $errors[] = 'You forgot to enter your password.';
    } else {
        $p = mysqli_real_escape_string($dbc, trim($pass));
    }

    if (empty($errors)) { // If everything's OK.
```
