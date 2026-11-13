
每次加载页面时，都会显示旧值并设置新值。请注意，如果你浏览其他网站然后再回来，这些值会被记住，但如果你关闭网络浏览器再回来，这些值会被重置。

### 使用会话变量

会话变量相对于 Cookie 的一个优势在于其能够使用 PHP 的数据类型。Cookie 值始终是简单的文本值，但会话变量可以采用普通 PHP 变量可以采用的任何值。

例如，要在 Cookie 中存储一个项目列表，你需要创建一个数组并将其传递给 `serialize` 进行存储。通过使用会话变量，你可以直接创建一个数组，并将该数据结构存储在会话中。

**清单 14.2** 中的示例使用存储在会话中的数组来保留通过表单输入的一组值。这是一个相当简单的示例，但它展示了使用会话变量时所拥有的灵活性。

### 清单 14.2. 使用数组作为会话变量

```php
<?php

session_start();

if (isset($_POST["word"]))
    $_SESSION["words"][] = $_POST["word"];

if (is_array($_SESSION["words"])) {
    foreach($_SESSION["words"] as $word) {
        echo $word . "<br>";
    }
}

?>
<FORM ACTION="list.php" METHOD=POST>
Enter a word: <INPUT SIZE="10" NAME="word">
<INPUT TYPE=SUBMIT VALUE="Add word to list">
</FORM>
```

## 总结

在本课中，你学习了如何从 PHP 设置 Cookie，以及如何使用 PHP 的会话管理在浏览器会话中存储值。在下一课中，你将使用这些技术使用 PHP 创建用户身份验证系统。

## 第 15 课。用户身份验证

在本课中，你将构建一个用户身份验证流程，该流程可通过密码保护网站的某些页面。

### 身份验证类型

很可能你过去需要登录过网站，因此你应该了解从用户角度看身份验证流程的工作原理。一般来说，系统会要求你输入用户名——有时是你的电子邮件地址——和密码。

不过，网站对用户进行身份验证实际上有两种方法：使用基本 HTTP 身份验证和使用基于会话的身份验证。以下部分阐明了这两种方法之间的区别。

#### 基本 HTTP 身份验证

基本 HTTP 身份验证可以由 Web 服务器执行，与 PHP 脚本无关。本节中的示例假设你使用的是 Apache Web 服务器；对于其他 Web 服务器，请参阅相关文档。

身份验证通常按目录进行，但如果需要，可以设置为适用于单个文件。通过在网站上使用 .htaccess 文件，你可以为该目录指定自定义配置，指示 Web 服务器在继续之前要求登录。典型的配置指令集如下：

```
AuthType Basic
AuthName "Protected Website"
AuthUserFile /home/yourname/htpasswd
require valid-user
```

AuthUserFile 指向使用 htpasswd 程序创建的密码文件的位置。要创建新密码文件，你可以运行类似以下的命令：

```
$ htpasswd c /home/yourname/htpasswd chris
New password:
Re-type new password:
```

> **密码文件** 仅在要创建新文件时才应使用 c 开关。htpasswd 程序不会询问你是否要覆盖现有文件。在现有密码文件上运行不带 c 选项的 htpasswd 会添加用户。

你需要输入两次新密码，之后会向给定的密码文件添加一条条目。该条目由用户名和密码的加密版本组成，两者用冒号分隔。但是，你永远不需要直接处理此文件。典型的密码文件条目可能如下所示：

```
chris:XNiv7qSUTFPU6
damon:ZxxE2PTExEVNU
shelley:SVzAEtXmMLEAls
vanessa:cX/t1Pv2oQfrY
```

当你尝试访问受保护目录中的文件时，Web 浏览器会弹出一个要求输入用户名和密码的窗口，仅在输入正确信息后才会加载请求的页面。

`require valid-user` 指令指示 Web 服务器向任何经过身份验证的用户显示页面。你可能希望仅向特定用户授予访问权限，这可以通过 `require user` 指令实现：

```
require user chris damon shelley
```

基本 HTTP 身份验证还允许你设置用户组，以便仅向特定用户授予对站点特定部分的访问权限。然后可以使用 `require group` 指令指定对一个或多个用户组的访问权限。

以下名为 `htgroups` 的组文件将密码文件中的用户划分为两组：

```
boys: chris damon
girls: shelley vanessa
```

要仅向 boys 组授予访问权限，你可以使用以下 `.htaccess` 文件：

```
AuthType Basic
AuthName "Boys Only"
AuthUserFile /home/yourname/htpasswd
AuthGroupFile /home/yourname/htgroup
require group boys
```

虽然设置起来相当容易且相当灵活，但基本 HTTP 身份验证有一些缺点。首先，你无法更改弹出式登录框的外观和感觉。如果你想以任何方式自定义该过程，则无法使用此方法。此外，密码文件存储在服务器的文件系统上，从脚本更新它可能会出现问题；你将在处理文件读写（第 17 课“文件系统访问”）时了解更多有关这些问题的信息。

**Apache 插件** Apache Web 服务器的多个第三方模块（例如 `mod_auth_mysql` 和 `mod_auth_sqlite`）允许你将基本 HTTP 身份验证与存储在数据库中的密码信息配合使用。请与你的 Web 主机联系，查看是否安装了这些模块。

#### 基于会话的身份验证

要为你的网站提供完全可自定义的登录流程，你必须自行实现，而在 PHP 中这样做需要使用会话变量。

简而言之，一旦用户登录，浏览器的会话中就会包含足够信息，以说服网站上的脚本允许你查看页面。用户通过你网站上的表单登录，在其中输入用户名和密码。你可以随意设置登录流程的布局和流程。

与基本 HTTP 身份验证的一个相当显著的区别在于，检查用户会话有效性的指令出现在脚本本身中，而不是在按目录的配置文件中。

**保护 HTML** 如果你的网站包含不含任何 PHP 的纯 HTML 文件，则需要向其中添加 PHP 代码，以防止匿名用户查看它们。你还需要将其文件扩展名更改为 `.php`。

### 构建身份验证系统

本课的其余部分将指导你使用 PHP 会话构建身份验证机制。

#### 系统工作原理

你现在要构建的身份验证系统有两个主要组件。首先，你需要一个登录处理器来检查表单中输入的用户名和密码的有效性。你还需要一段代码，可以将其放在每个脚本的顶部，以检查会话并确保在继续之前用户已通过身份验证。

> **登录表单** 你需要确保始终对登录表单使用 POST 方法。使用 GET 方法提交用户名和密码会导致这些值出现在下一页面的 URL 中，任何人都可以看到！

你应该将会话检查代码拆分为一个包含文件 auth.inc，以便通过仅在脚本顶部放置以下语句即可轻松保护页面：

```
include "auth.inc";
```

你可以使用一个会话变量来存储已登录用户的用户名。如果变量中包含用户名，则该用户已登录；注销用户只需删除此会话变量即可。只要没有其他人共享你的网站所在的域并可能创建冲突会话，这就足够安全。基于此，auth.inc 可以简单如下：

```
session_start();
if (!isset($_SESSION["auth_username"])) {
    echo "You must be logged in to view this page";
    exit;
}
```

这里只是在用户未登录时显示一条消息并退出脚本。稍后你将了解如何为可用性改进这一点，但你需要先创建登录流程本身。
