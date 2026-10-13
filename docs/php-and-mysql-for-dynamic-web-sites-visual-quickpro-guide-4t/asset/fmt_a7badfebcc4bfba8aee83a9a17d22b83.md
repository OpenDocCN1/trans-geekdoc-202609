
# 创建登录函数

本章中多个脚本将使用的另一段代码用于验证登录表单。这是一个三步过程：

1. 确认提供了电子邮件地址。
2. 确认提供了密码。
3. 确认提供的电子邮件地址和密码与数据库中存储的匹配（注册过程中存储）。

接下来的脚本将定义两个不同的函数。每个函数的工作细节将在后续步骤中解释。

## 创建登录函数

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
1  <?php # Script 12.2 - login_functions.inc.php
2  // This page defines two functions used
3  // by the login/logout process.
4
5  /* This function determines an absolute
6   * URL and redirects the user there.
7   * The function takes one argument: the
8   * page to be redirected to.
9   * The argument defaults to index.php.
10   */
11  function redirect_user ($page = 'index.php') {
12
13      // Start defining the URL...
14      // URL is http:// plus the host name
15      // plus the current directory:
16      $url = 'http://' . $_SERVER['HTTP_HOST'] . dirname($_SERVER['PHP_SELF']);
17
18      // Remove any trailing slashes:
19      $url = rtrim($url, '/\\');
20
21      // Add the page:
22      $url .= '/' . $page;
23
24      // Redirect the user:
25      header("Location: $url");
26      exit(); // Quit the script.
27
28  } // End of redirect_user() function.
29
30
31  /* This function validates the form data
32   * (the email address and password).
33   * If both are present, the database is
34   * queried.
35   * The function requires a database
36   * connection.
37   * The function returns an array of
38   * information, including:
39   * - a TRUE/FALSE variable indicating
40   *   success
41   * - an array of either errors or the
42   *   database result
43   */
44  function check_login($dbc, $email = '', $pass = '') {
45
46      $errors = array(); // Initialize error array.
47
48      // Validate the email address:
49      if (empty($email)) {
50          $errors[] = 'You forgot to enter your email address.';
51      } else {
52          $e = mysqli_real_escape_string($dbc, trim($email));
53      }
54
55      // Validate the password:
56      if (empty($pass)) {
57          $errors[] = 'You forgot to enter your password.';
58      } else {
59          $p = mysqli_real_escape_string($dbc, trim($pass));
60      }
61
62      if (empty($errors)) { // If everything's OK.
63
64          // Retrieve the user_id and first_name for that email/password combination:
65          $q = "SELECT user_id, first_name FROM users WHERE email='$e' AND pass=SHA1('$p')";
66          $r = @mysqli_query($dbc, $q); // Run the query.
67
68          // Check the result:
69          if (mysqli_num_rows($r) == 1) {
70
71              // Fetch the record:
72              $row = mysqli_fetch_array($r, MYSQLI_ASSOC);
73
74              // Return true and the record:
75              return array(true, $row);
76
77          } else { // Not a match!
78              $errors[] = 'The email address and password entered do not match those on file.';
79          }
80
81      } // End of empty($errors) IF.
82
83      // Return false and the errors:
84      return array(false, $errors);
85
86  } // End of check_login() function.
```

首先，给 `$url` 赋值为 `http://` 加上主机名（可能是 `localhost` 或 `www.example.com`）。使用 `dirname()` 函数加上当前目录名，以防重定向发生在子文件夹内。`$_SERVER['PHP_SELF']` 指向调用此函数的当前脚本（包含目录名）。该完整值可能是 `/somedir/page.php`。`dirname()` 函数将仅返回该值的目录部分（即 `/somedir/`）。

**4.** 从 URL 中移除任何尾部斜杠：

```php
$url = rtrim($url, '/\\');
```

因为子文件夹的存在可能会添加额外的斜杠（`/`）或反斜杠（`\`，用于 Windows），函数需要移除它们。为此，应用 `rtrim()` 函数。默认情况下，此函数从字符串右侧移除空格。如果提供第二个参数作为要移除的字符列表，它将移除那些字符。要移除的字符是 `/` 和 `\`。但由于反斜杠是 PHP 中的转义字符，你需要使用 `\\` 来表示单个反斜杠。通过这行代码，如果 `$url` 以这些字符中的任何一个结尾，`rtrim()` 函数将移除它们。

**5.** 将特定页面追加到 URL：

```php
$url .= '/' . $page;
```

接下来，将特定页面名连接到 `$url`。它前面加上斜杠，因为第 4 步中移除了尾部斜杠，不能有 `www.example.compage.php` 这样的 URL。

这看起来可能相当复杂，但这是一种非常有效的方法，可确保无论在什么服务器上、从什么目录运行脚本，重定向都能正常工作（只要重定向发生在该目录内）。

**6.** 重定向用户并完成函数：

```php
header("Location: $url");
exit(); // Quit the script.
} // End of redirect_user() function.
```

最后步骤是发送 `Location` 头并终止脚本执行。

**7.** 开始一个新函数：

```php
function check_login($dbc, $email = '', $pass = '') {
```

此函数将验证登录信息。它接受三个参数：数据库连接（必需）、电子邮件地址（可选）和密码（可选）。

虽然此函数可以直接访问 `$_POST['email']` 和 `$_POST['pass']`，但最好将这些值传递给函数，使函数更加独立。

**8.** 验证电子邮件地址和密码：

```php
$errors = array();
if (empty($email)) {
    $errors[] = 'You forgot to enter your email address.';
} else {
    $e = mysqli_real_escape_string($dbc, trim($email));
}
if (empty($pass)) {
    $errors[] = 'You forgot to enter your password.';
} else {
    $p = mysqli_real_escape_string($dbc, trim($pass));
}
```
