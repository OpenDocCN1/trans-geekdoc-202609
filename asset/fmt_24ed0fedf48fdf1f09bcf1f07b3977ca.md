
| --- | --- | --- |

| laura luke | 7cbf2621e73c9b 1ef61090aeb2e59 | laura@tangledweb.com.au luke@tangledweb.com.au |

![](img/654520c37415debd4290b9b4aa2c03f2_596_0.png)

图 27.2 PHPbookmark 系统的数据库模式

`user` 表存储每个用户的用户名（作为主键）、密码和电子邮箱地址。`bookmark` 表存储用户名和书签（`bm_URL`）配对。该表中的用户名引用 `user` 表中的用户名。

用于创建这些内容以及从 Web 端连接数据库并创建用户的 SQL 语句如代码列表 27.1 所示。如果你计划在你的系统上使用它，应该编辑此文件。务必将用户的密码更改为更安全的内容！

### 代码列表 27.1 bookmarks.sql—设置数据库的 SQL

```sql
create database bookmarks;
use bookmarks;

create table user (
  username varchar(16) PRIMARY KEY,
  password char(40) NOT NULL,
  email varchar(100) NOT NULL
);

create table bookmark (
  username varchar(16),
  bm_URL varchar(255) NOT NULL,
  FOREIGN KEY (username) REFERENCES user(username)
);

grant SELECT, INSERT, UPDATE, DELETE ON bookmarks.* TO 'user'@'localhost';
```

你可以通过在命令行运行以下命令来创建数据库和表：

```bash
mysql -u root -p < bookmarks
```

```sql
CREATE USER 'user'@'localhost' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON bookmarks.* TO 'user'@'localhost';
FLUSH PRIVILEGES;
```

如你所见，`do_html_header()` 函数唯一的逻辑是启动 HTML 文档并向页面添加适当的标题和页眉。`login.php` 中使用的其他函数也类似。`display_site_info()` 函数添加了一些关于网站的通用文本，`display_login_form()` 显示如列表 27.3 所示的表单，而 `do_html_footer()` 则向页面添加标准的 HTML 页脚。

从你的主逻辑流中隔离或移除 HTML 的优势将在第 25 节“使用 PHP 和 MySQL 构建大型项目”中进行讨论。我们在这里使用了函数 API 的方法。

查看图 27.3，你有三个选择：用户可以注册、如果已经注册则登录，或者如果忘记了密码则重置密码。为了实现这些模块，我们进入下一节：用户身份验证。

## 实现用户身份验证

用户身份验证模块有四个主要元素：注册用户、登录和注销、更改密码和重置密码。在接下来的章节中，我们将逐一查看这些元素。

### 注册用户

要注册用户，你需要通过表单获取用户的详细信息并将用户存入数据库。

当用户点击 `login.php` 页面上的“不是成员？”链接时，用户将被引导到由 `register_form.php` 生成的注册表单。该脚本在列表 27.5 所示。

#### 列表 27.5 register_form.php——此表单提供了使用 PHP 注册的机会

```php
<?php
require_once('bookmark_fns.php');
do_html_header('User Registration');
display_registration_form();
do_html_footer();
```

再次，你可以看到此页面非常简单，只是调用了 `output_fns.php` 中输出库的函数。该脚本的输出位于列表 27.4。

此页面上的灰色表单由 `output_fns.php` 中的 `display_registration_form()` 函数输出。当用户点击“注册”按钮时，用户将被引导到列表 27.6 所示的 `register_new.php` 脚本。

# 第 27 节 构建用户身份验证与个性化

![](img/654520c37415debd4290b9b4aa2c03f2_601_0.png)

图 27.4 注册表单获取数据库所需的详细信息。此表单要求用户输入两次详细信息，以防出错。

#### 列表 27.6 register_new.php-此脚本验证新用户数据并存入数据库

```php
<?php
// 包含此应用程序函数文件
require_once('bookmark_fns.php');

// 创建短变量名
$email=$_POST['email'];
$username=$_POST['username'];
$password=$_POST['passwd'];
$passwd2=$_POST['passwd2'];
// 启动会，稍可能需要
// 现在启动它，因为它必须在标头之前之前
session_start();
try {
// 检查填充的表单
if (!filled_out($_POST)) {
    throw new Exception('你没有正确填写，
    请返回并重试。');
}
```

```php
// 电子邮件地址无效
if (!$valid_email($email)) {
    throw new Exception('这不是一个有效的电子邮件地址。
    请返回并重试。');
}

// 密码不一致
if ($passwd != $passwd2) {
    throw new Exception('你输入的密码不匹配，
    请返回并重试。');
}

// 检查密码长度是否正常
// 如果用户截断，但如果密码太长
// 它们将会乱码
if ((strlen($passwd) < 6) || (strlen($passwd) > 16)) {
    throw new Exception('你的密码必须在 6 到 16 位之间。');
}

// 注册成功
do_html_header('注册成功');
echo '注册成功！设置书签';
do_html_footer();
} catch (Exception $e) {
do_html_header('错误：');
echo $e->getMessage();
do_html_footer();
exit;
?>
```

## 第 27 章 构建用户身份验证与个性化

![](img/654520c37415debd4290b9b4aa2c03f2_605_0.png)

图 27.5 注册成功；用户现在可以进入会员页面

`register()` 函数位于名为 `user_auth_fns.php` 的包含库中。该函数显示在列表 27.9 中。

#### 列表 27.9 来自 user_auth_fns.php 的 `register()` 函数——该函数尝试将新用户信息存入数据库

```php
function register($username, $email, $password) {
  // 在数据库中注册新人员
  // 返回 true 或错误信息
  // 连接数据库
  $conn = db_connect();
  // 检查用户名是否唯一
  $result = $conn->query("select * from user where username='$username.'");
  if (!$result) {
    throw new Exception('Could not execute query');
  }
  if ($result->num_rows>0) {
    throw new Exception('That username is taken - go back and choose another one.');
  }
```

```php
// 如果成功，存入数据库
$result = $conn->query('insert into user values
    ('.$username.', sha1('.$password.'), '.$email.')');
```

```php
if (!$result) {
    throw new Exception('Could not register you in database - please try again later.');
}
```

```php
return true;
```

这个函数并没有特别新奇；它连接到你之前设置的数据库。如果会 或数据库无法更新，它将抛出一个异常。否则，它将更新数据库并返回 true。

请注意，你正在使用一个名为 `db_connect()` 的函数执行实际数据库连接。该函数提供了一个包含连接数据库所需的用户名和密码的单一位置。这样，如果你更改数据库密码，只需要更改应用程序中的一个文件。`db_connect()` 函数显示在列表 27.10 中。

#### 列表 27.10 来自 db_fns.php 的 `db_connect()` 函数——该函数连接到 MySQL 数据库

```php
function db_connect() {
    $result = new mysqli('localhost', 'bm_user', 'password', 'bookmarks');
    if (!$result) {
        throw new Exception('Could not connect to database server');
    } else {
        return $result;
    }
}
?>
```

当用户注册后，他们可以使用普通的登录和注销页面进行登录和注销。
你接下来将构建它们。

### 登录

如果用户在 `login.php`（见图 27.3）表单中输入详细信息并提交，他们将被引导至 `member.php` 脚本。如果他们有此表单，该脚本会将他们登录。它还会向登录的用户显示任何相关的书签。它是整个应用程序的核心。该脚本显示在列表 27.11 中。

#### 列表 27.11 member.php——该脚本是应用程序的主枢

```php
<?php
// 包含此应用程序的函数文件
require_once('bookmark_fns.php');
session_start();
// 创建短变量
if (isset($_POST['username'])) {
    // 如果未设置 -> 设置占位值
    $_POST['username'] = "";
}
$username = $_POST['username'];
if (!isset($_POST['password'])) {
    // 如果未设置 -> 设置占位值
    $_POST['password'] = "";
}
$password = $_POST['password'];
if ($username && $password) {
    // 他们刚刚尝试登录
    try {
        login($username, $password);
        // 如果他们在数据库中，注册用户 ID
        $_SESSION['valid_user'] = $username;
    } catch (Exception $e) {
        // 登录失败
        do_html_header('Problem:');
        echo 'You could not be logged in.<br>You must be logged in to view this page.';
        do_html_url('login.php', 'Login');
        do_html_footer();
        exit;
    }
}
do_html_header('Home');
check_valid_user();
// 获取此用户保存的书签
if ($url_array = get_user_urls($_SESSION['valid_user'])) {
    display_user_urls($url_array);
}
```

```php
// 提供选项菜单
display_user_menu();
```

```php
do_html_footer();
?>
```

你可能识别出 `member.php` 脚本中的逻辑：它复用了第 22 章中的一些思想。

首先，你检查用户是否来自首页——也就是说，用户是否刚刚填写了登录表单，并按照如下方式登录用户：

```php
if ($username && $password) {
  // 他们刚刚尝试登录
  try {
```
