

表示匹配规则末尾的美元符号指示字符串的结尾。这意味着，如果在此点之后匹配的内容后面还有任何字符，则匹配无效。换句话说，最终的美元符号仍然允许 shop/Mugs 或 shop/Mugs/，但不允许 shop/Mugs/a 或 shop/Mugs/123。

当发生匹配时，URL 将被重写为 shop.php?type=$1。$1 表示匹配第一个分组的任何字符串：([A-Za-z\-]+)。这称为反向引用，因为它指向已经找到的内容。最终结果是，shop/coffee 和 shop/coffee/ 变成 shop.php?type=coffee，而 shop/goodies 变成 shop.php?type=goodies。在这两种情况下，$_GET['type'] 都可供 shop.php 脚本使用，因为重写模块将创建它并为其赋值。

虽然所有产品都可以通过 shop.php 访问，但特价商品将在 sales.php 脚本上列出。但为了使 URL 保持一致，让我们为这种情况添加一条规则：

```
RewriteRule ^shop/sales/?$ sales.php
```

此规则专门匹配 shop/sales 或 shop/sales/，并将其重写为 sales.php。但是，此规则必须在前一条规则之前定义，因为前一条规则也会应用于 shop/sales，而我们不希望 URL 被重写为 shop.php?type=sales。

接下来，browse.php 页面将在一般类别中列出特定产品：所有可用的 Kona 咖啡或所有杯子。browse 脚本需要知道类别类型和特定类别 ID。出于搜索引擎优化（SEO）目的，也为了让客户更容易访问 URL，URL 将采用 browse/type/CategoryName/id 的格式，例如 browse/coffee/Kona/3。处理此问题的规则是：

```
RewriteRule ^browse/([A-Za-z+\-]+)/([A-Za-z+\-]+)/([0-9]+)$ -> browse.php?type=$1&category=$2&id=$3
```

此规则匹配任何以 browse 开头、后跟斜杠和一些字母与加号组合的 URL。第一个分组表示 type 值，例如 coffee 或 goodies。之后应跟一个斜杠，以及一些字母、加号和连字符的组合。第二个分组匹配类别，例如 Kona 或 Gift+Baskets。匹配应以一个或多个数字结尾，这些数字将是 ID 值。

此类匹配将被重写为 browse.php?type=$1&category=$2&id=$3，其中 $1、$2 和 $3 分别代表第一个、第二个和第三个匹配分组。因此，www.example.com/browse/coffee/Kona/3 变为（幕后）www.example.com/browse.php?type=coffee&category=Kona&id=3。

## 强制 SSL

在站点使用 mod_rewrite 的同时，让我们为几个页面强制实施 SSL：

- 整个管理目录
- checkout.php
- billing.php
- final.php

要做到这一点，您必须启用 SSL（请参阅“启用 SSL”侧边栏），并将此代码添加到 .htaccess 文件中，位于相同的 <IfModule mod_rewrite.c> 块内：

```
RewriteCond %{HTTPS} off
RewriteRule ^(checkout\.php|billing\.php|final\.php|admin/(.*))$ https://%{HTTP_HOST}/$1 [R=301,L]
```

第一行检查 HTTPS 已关闭的条件：%{something} 引用服务器环境变量。然后，规则尝试匹配 checkout.php、billing.php、final.php 或 admin/任何内容。如果发生匹配，URL 将被重写为 https://hostname/$1，其中 $1 是匹配的项目。

R=301,L 部分表示这应该是永久重定向类型，关联服务器代码 301，并且这是应评估的最后一条规则。

添加此规则后，服务器将不允许浏览器通过非安全连接加载这些页面中的任何页面。

## 启用 SSL

在服务器上启用 SSL 是任何电子商务项目的重要步骤，但遗憾的是，我无法为您提供具体说明：涉及的因素太多，从托管公司到服务器类型，再到您获取 SSL 证书的位置。在第 2 章“安全基础”中，我谈到了一些提供数字证书的网站以及您应考虑的功能。如果您通过托管公司购买，他们很可能会为您安装，这是一个好处。如果您通过第三方购买，您可能会节省资金，但需要自己安装（尽管第三方应提供一些说明）。在这种情况下，您可能可以通过 Web 托管控制面板安装证书。如果这不是一个选项，那么安装就是使用命令行将正确的文件放在正确的位置，然后编辑服务器的配置文件。网上有大量教程将详细说明这些步骤。

## 辅助文件

Coffee 网站将使用多个辅助文件，不包括 HTML 模板和视图。此处讨论的前两个文件在语法和用法上与第二部分中的相应脚本基本相同，但让我们逐个查看它们。

### 连接到数据库

第一个辅助脚本将连接到数据库。名为 mysql.inc.php 的此文件理想情况下应存储在 Web 目录之外（参见图 7-5）。它定义如下：

```
mysql.inc.php

1 <?php
2 // Set the database access information as constants:
3 DEFINE ('DB_USER', 'username');
4 DEFINE ('DB_PASSWORD', 'password');
5 DEFINE ('DB_HOST', 'localhost');
6 DEFINE ('DB_NAME', 'ecommerce2');
7
8 // Make the connection:
9 $dbc = mysqli_connect (DB_HOST, DB_USER, DB_PASSWORD,
   DB_NAME);
10 // Set the character set:
11 mysqli_set_charset($dbc, 'utf8');
12
13 // Omit the closing PHP tag to avoid 'headers already sent' errors!
```

如我所说，此代码与第 3 章“第一个网站：结构与设计”中的代码基本相同，只是连接常数的值会有所不同，并且不需要 get_password_hash() 或 escape_data() 函数。后者不是必需的，因为将使用存储过程和预处理语句（将在本章末尾介绍）。

如果要改善此示例的安全性，可以创建不同的 MySQL 用户，在特定表上拥有不同的权限。最常见的 MySQL 用户将在所有非客户相关表上拥有 SELECT 权限；另一个 MySQL 用户将在 carts 和 wish_lists 表上拥有 SELECT 以及 INSERT、UPDATE 和 DELETE 权限；第三个用户将仅在订单相关表上拥有 INSERT 权限。要在页面级别切换 MySQL 用户，您需要在包含 MySQL 连接脚本之前指示用户类型：

```
$user = 'general';
require (MYSQL);
```

然后，在连接脚本中，您将拥有：

```
DEFINE ('DB_HOST', 'localhost');
DEFINE ('DB_NAME', 'ecommerce2');
if (isset($user) && ($user == 'general')) {
DEFINE ('DB_USER', 'username');
DEFINE ('DB_PASSWORD', 'password');
} elseif (isset($user) && ($user == 'cart')) {...}
DEFINE ('DB_USER', 'otherUser');
DEFINE ('DB_PASSWORD', 'otherPassword');
```

### 配置文件

本站点的配置文件基本上与“知识就是力”网站的配置文件功能相同：定义站点设置、常量并声明错误处理程序。不过，Coffee 网站不会使用会话，因此会话从配置文件中省略，重定向函数也是如此。

### includes/config.php

```
<?php

// Are we live?
$live = false;

// Errors are emailed here:
$contact_email = 'you@example.com';

// Determine location of files and the URL of the site:
define ('BASE_URI', '/path/to/Web/parent/folder/');
define ('BASE_URL', 'www.example.com/');
define ('MYSQL', '/path/to/mysql.inc.php');

// Function for handling errors:
function my_error_handler ($e_number, $e_message, $e_file, $e_line,
$e_vars) {
global $live, $contact_email;

// Build the error message:
$message = "An error occurred in script '$e_file' on line
$e_line.$e_message\n";
// Add the backtrace:
$message .= " <pre>" . print_r(debug_backtrace(), 1) . "</pre>\n";
if ($live) { // Show the error in the browser.
echo '<div class="error">' . nl2br($message) . '</div>';
} else { // Development (print the error).
// Send the error in an email:
error_log($message, 1, $contact_email,
'From:admin@example.com');
// Only print an error message in the browser, if the error isn't
// a notice:
if ($e_number != E_NOTICE) {
echo '<div class="error">A system error occurred. We
apologize for the inconvenience.</div>';
}
} // End of $live IF-ELSE.
return true; // So that PHP doesn't try to handle the error, too.
} // End of my_error_handler() definition.
// Use my error handler:
set_error_handler('my_error_handler');
// Omit the closing PHP tag to avoid 'headers already sent' errors!
```

我应当指出，错误处理程序引入了一个不一致之处，这在接下来的一两章中可能会变得明显。本站点中的每个 PHP 脚本都使用视图文件——单独的 HTML 页面——来显示内容。从技术上讲，还应该创建一个单独的视图文件来显示错误。如果没有这样的文件，您可能会在奇怪的位置看到错误。此处省略了专门的错误视图文件，以免进一步使事情复杂化，但您可以在 www.DMCInsights.com/ecom/ 提供下载的代码中找到它。

> 如果您对三个辅助文件中的任何代码不确定，请参阅第二部分，其中详细解释了每个文件。

