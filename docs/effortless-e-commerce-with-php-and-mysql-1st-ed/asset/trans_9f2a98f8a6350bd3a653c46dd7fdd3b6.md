

### 6. 如果未返回任何行，则打印错误：

```php
if (mysqli_num_rows($r) != 1) {
    $page_title = 'Error!';
    include ('./includes/header.html');
    echo '<p class="error">This page has been accessed in error.</p>';
    include ('./includes/footer.html');
    exit();
}
```

再次，与 category.php 一样，如果提供的 ID 值是整数但与任何数据库记录都不相关，则会创建一个指示问题的完整页面（类似于图 5.9）。

### 7. 获取页面信息：

```php
$row = mysqli_fetch_array($r, MYSQLI_ASSOC);
$page_title = $row['title'];
include ('includes/header.html');
echo "<h3>$page_title</h3>";
```

页面的标题将用作浏览器标题和页面上的标题。

### 8. 如果用户的账户有效，则显示内容：

```php
if (isset($_SESSION['user_not_expired'])) {
    echo "<div>{$row['content']}</div>";
} elseif (isset($_SESSION['user_id'])) { // Logged in but not current.
    echo '<p class="error">Thank you for your interest in this content, but your account is no longer current. Please <a href="renew.php">renew your account</a> in order to view this page in its entirety</p>';
    echo "<div>{$row['description']}</div>";
} else { // Not logged in.
    echo '<p class="error">Thank you for your interest in this content. You must be logged in as a registered user to view this page in its entirety.</p>';
    echo "<div>{$row['description']}</div>";
}
```

此条件语句决定基于查看页面的用户显示的内容。只有账户有效的登录用户——即拥有 $_SESSION['user_not_expired'] 值的用户——才能查看内容本身。其他类型的用户只能看到描述以及适合其情况的消息。

### 9. 完成 ID 条件语句：

```php
} else { // No valid ID.
$page_title = 'Error!';
include ('includes/header.html');
echo '<p class="error">This page has been accessed in error.</p>';
} // End of primary IF.
```

如果此页面未接收到有效的 ID 值，用户将看到此错误消息。

- 10. 完成页面：
- include ('./includes/footer.html');
- ?>

- 11. 保存并测试 page.php 脚本。

要测试它，您需要在 category.php 上点击链接。您还应该以三种不同的用户类型（访客、过期会员和活跃会员）进行测试，以获得完整效果。

## 添加 PDF

本示例中的第二个管理页面将处理将 PDF 文件上传到网站。尽管管理员只需提供三项信息——标题、描述和 PDF 文件本身——但处理表单的过程很棘手，很大程度上是因为我希望表单具有粘性（sticky），就像网站中的其他表单一样。您可能知道，文件表单输入无法以与文本输入相同的方式设为粘性，因此我不得不使用一些逻辑来模拟这一概念（图 5.13）。

![](img/4f47e47c67bd619ac73250f11c9fc7ce_137_0.png)

图 5.13

另外，允许用户（甚至管理员）将文件上传到服务器是一个潜在的安全漏洞，因此需要应用多种技术来使此过程尽可能安全。但首先，服务器需要设置为允许文件上传。

### 设置服务器

文件和目录的服务器权限归结为谁可以做什么。至于“什么”，选项有：读取、写入和执行。“谁”要么是特定的服务器用户，要么是用户组。

在 PHP 脚本能够将文件放到服务器之前，服务器上必须有一个文件夹，PHP 脚本可以向其中写入，也就是说更改目录的内容。由于 PHP 是通过 Web 服务器运行的，“谁”就是 Web 服务器用户。因此，目标是创建一个 Web 服务器用户可以写入的文件夹。

具体如何操作将取决于您的服务器设置、所使用的操作系统以及 PHP 相对于 Web 服务器的运行方式。归根结底，这通常意味着您将创建一个目录，并给予“所有人”写入权限。在 Unix 术语中，这由数字 777 表示。通常您的 Web 主机提供一个控制面板，您可以通过它更改文件夹的权限，或者您可能可以通过 FTP 应用程序完成此操作（图 5.14）。

![](img/4f47e47c67bd619ac73250f11c9fc7ce_138_0.png)

图 5.14

虽然后允许每个人对目录做任何事听起来非常危险，但实际上并非如此。这里的“每个人”指的是服务器上的每个用户。所谓“用户”，我指的是在服务器上注册的用户帐户。例如，可能有一个运行数据库的 mysql 用户，而 Web 服务器可能以 nobody 用户身份运行。使用开放权限，这两个用户，以及任何具有 FTP 或 SSH 访问服务器权限的人，都可以读取、写入或执行目录中的文件。这并非无关紧要，但对每个人可用并不意味着互联网上任何人都可以将文件写入该目录：仍然需要一个被认可的服务器用户。

尽管如此，这并不意味着您应该对创建这样的开放目录漫不经心。如果您在共享服务器上，该服务器上拥有用户帐户的每个人都可以操纵这个目录——当然，前提是他们知道它的存在，而这是一个很大的如果。而且，如果网站存在安全漏洞，该漏洞可能被用来操纵目录——在这种情况下，是通过互联网上的用户，因为 Web 服务器用户将是活跃代理。

有许多情况需要开放目录才能使网站正常运行。问题在于如何使系统尽可能安全。答案在于像黑客一样思考。如果黑客无法闯入服务器，下一个目标将是让服务器为他或她执行一些危险代码。一种方法是尝试让 PHP（或其他）打开、require 或 include——从而执行——在另一台服务器上找到的一些危险代码。我在第 2 章“安全基础”中讨论过这一点。第二种途径是以某种方式将危险代码放到服务器上，然后直接执行它。这是一个两步过程。因此，防范此类尝试也是一个两步过程：

- 1. 尽你所能防止危险代码被放置在服务器上。
- 2. 使直接执行动态添加的内容变得困难，如果不可能的话。

对于第一步，很大程度上是验证上传的内容：确保它是可接受的类型。对于第二步，最好的解决方案是将上传的内容存储在 Web 根目录之外的目录中。在这种情况下，如果坏人 Bob（在互联网上，而不是在您的服务器上）能诱骗您的系统上传一些危险脚本，他仍然无法执行该脚本，因为如果它不在 Web 根目录中，就没有方法调用它。

提示
使用 Web 服务器保护目录的方法将在第 7 章“第二个网站：结构与设计”中讨论。

如果不可能（例如，某些共享主机不允许您将内容放在 Web 目录之上），则应该在 Web 目录中创建一个不明显的文件夹。这个文件夹仍然需要开放权限，但您应该对目录进行密码保护，以便只有授权用户才能（通过 HTTP）访问它。您可以使用 Web 主机的控制面板完成此操作。

提示
我在第 3 章“第一个网站：结构与设计”中讨论过服务器的组织以及 pdfs 目录理想情况下应该放在哪里。

一旦您用开放权限创建了 pdfs 目录，并在必要时将其放置在 Web 根目录中适当地进行了保护，您就可以创建将 PDF 文件上传到该文件夹的 PHP 脚本。但首先，我建议在配置文件中创建另一个常量，作为该文件夹的绝对路径：

提示
将 PDFS_DIR 的值更改为适合您服务器的值。

```php
// In config.inc.php:
define('PDFS_DIR', BASE_URI . 'pdfs/');
```

### 创建 PHP 脚本

此 PHP 脚本与所有其他表单具有相同的基本结构：首先显示表单；用户提交表单后验证数据；如果有任何错误，则再次显示表单并指示当前值。但是，这个特定过程将比其他表单更棘手，因为它还涉及上传的文件。文件输入无法设为粘性，更重要的是，当表单因其他错误而需要重新显示时，必须处理服务器上的实际文件。我将在以下步骤中解释所有相关逻辑。

- 1. 在文本编辑器或 IDE 中创建一个新的 PHP 脚本，命名为 add_pdf.php 并存储在 Web 根目录中。

