

## 第23章

### 添加用户登录

> “Haskell 比 C++ 更快，比 Perl 更简洁，比 Python 更规范，比 Ruby 更灵活，比 C# 更具类型感，比 Java 更健壮，而且与 PHP 毫无共同之处。”
>
> —唐凤

## 23. 添加用户登录

既然我们已经掌握了保护 Web 应用程序的正确技术，现在回到我们的 *电影列表* 应用程序。我们需要对应用程序进行三项重大更改。首先，我们添加个人登录功能，并允许注册新用户。其次，我们添加导航菜单以提高应用程序的易用性。第三，我们加入一个预订系统，允许用户借出电影并归还。我们还将修改应用程序，只允许管理员添加、编辑和删除电影。以下是将 *电影列表* 应用程序转变为 *电影预订* 应用程序所需进行的修改的详细列表：

- 1. **添加个人用户登录**
  - 1. 创建一个数据库表，用于存储用户信息及其访问权限
  - 2. 为个人用户创建注册、登录和注销脚本
  - 3. 修改 `authorizeaccess.php` 脚本，只允许具有 `admin` 访问权限的用户添加、编辑和删除电影
- 2. **添加导航菜单以提高易用性**
  - 1. 创建并集成一个可供多个页面使用的导航栏脚本
- 3. **添加预订功能**
  - 1. 创建一个数据库表，用于存储电影预订信息
  - 2. 在 `movielisting` 数据库表中添加字段，以跟踪每部电影的副本数量和已预订电影
  - 3. 修改添加和编辑电影脚本，使其包含电影的副本数量
  - 4. 修改电影列表页面，为已登录用户显示预订电影的链接
  - 5. 修改电影列表页面，为以管理员权限登录的用户显示删除电影的链接
  - 6. 添加一个供用户借出电影的预订脚本
  - 7. 添加一个购物车脚本，允许用户预订购物车中的电影并将其从购物车中移除
  - 8. 添加一个购物车图标，允许用户查看其购物车
  - 9. 添加一个已预订电影脚本，允许用户归还电影
  - 10. 添加一个预订图标，允许用户查看其预订记录

在本章中，我们修改应用程序以添加个人用户登录。我们将在接下来的两章中添加其他功能。

## 创建用户表

要添加用户登录，我们需要在 Movie 数据库中创建另一个表来存储用户信息。让我们创建一个包含以下字段的用户表：

| 列名 | 类型 | 默认值 |
|---|---|---|
| id | int(11) 自动递增 | |
| user_name | varchar(50) | |
| password_hash | varchar(255) | |
| access_privileges | varchar(25) | [user] |
| date_created | datetime | [CURRENT_TIMESTAMP] |

> PHP 手册中关于 password_hash()[1] 的条目建议将哈希长度允许在 60 到 255 个字符之间，以便随着算法更新，哈希值可以随时间扩展。
>
> 在专业应用程序中，您会希望获取更多人口统计信息（联系信息等）。

使用 Adminer，在 Movie 数据库中创建一个新表，包含上面列出的列（及相关数据类型）。我们将有两种类型的访问权限：user 和 admin。当我们注册新用户时，我们希望将默认访问权限设置为 user。任何您希望拥有管理员权限的用户帐户都必须在数据库表中手动修改。我们还希望为 date_created 字段设置默认值 CURRENT_TIMESTAMP，该值也会在我们注册新用户时自动设置。

[1] password_hash(): https://php.net/password_hash

## 23. 添加用户登录

## 创建 Signup.php 脚本

为了允许新用户访问我们的应用程序，我们需要创建一个 signup.php 脚本。图 23.1 显示了我们希望注册页面的样子。

为了使我们的应用程序更安全，我们可能会在我们的“注册”表单上实现一个 CAPTCHA[2] 功能，以降低自动化脚本注册帐户的风险。验证码对用户来说很烦人，因此更好的实现是像 Google 的 reCAPTCHA 那样，如图 23.2 所示。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_346_0.png)

图 23.1.

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_346_1.png)

图 23.2.

Google 有一个新版本 v3[3]，通过分析来最大限度地减少用户交互，以更好地判断是用户还是自动化脚本在与网站交互。

### 创建注册表单

让我们先创建一个基本的 Bootstrap 页面，并将其命名为 signup.php，如清单 23.1 所示。

清单 23.1.

```
<!DOCTYPE html>
<?php
require_once('pagetitles.php');
$page_title = MR_SIGNUP_PAGE;
?>
<html>
<head>
<title><?= $page_title ?></title>
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/css/bootstrap.min.css" integrity="sha384-9aIt2nRpC1Uk9sG9sG9sG9sG9sG9sG9sG9sG9sG9sG9sG9sG9sG9sG9sG9sG9sG9s" crossorigin="anonymous">
</head>
<body>
<script src="https://code.jquery.com/jquery-3.5.1.slim.min.js" integrity="sha384-DfXdz2htPH0mLsSsN5nCTpuj/zy4C+0GpamoFvY38MVBnE+IbbVYwew+OrCXaRkfj" crossorigin="anonymous"></script>
```

[2] CAPTCHA: https://en.wikipedia.org/wiki/CAPTCHA

[3] 版本 v3: https://www.google.com/recaptcha/intro/v3.html

```
18. <script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.0/dist/umd/popper.min.js"
19.     integrity="sha384-Q6EPRbIbV..."
20.     crossorigin="anonymous"></script>
21. <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/js/bootstrap.min.js"
22.     integrity="sha384-OgV..."
23.     crossorigin="anonymous"></script>
24. </body>
25. </html>
```

注意，我添加了一个页面标题的定义，该定义包含在一个名为 pagetitles.php 的脚本中：

```
<!DOCTYPE html>
<?php
require_once('pagetitles.php');
$page_title = MR_SIGNUP_PAGE;
?>
```

这段代码稍后会帮助我们，当我们添加导航栏以根据访问权限显示指向特定页面的链接，以及当我们希望提供应用程序功能时。我稍后会更详细地介绍。

现在，创建一个名为 pagetitles.php 的新脚本，并添加注册页面的定义：

```
<?php
// Page Titles
define('MR_SIGNUP_PAGE', 'Movie Reservations - Sign Up');
```

现在回到我们的 signup.php 脚本。在 `<body>` 标签的开头，我们将添加一些描述性文本和用于注册新用户的表单，如清单 23.2 所示。

### 清单 23.2.

```
1. <body>
2. <div class="card">
3.     <div class="card-body">
4.         <h1>Sign up for a Movie Reservations Account</h1>
5.         <hr/>
6.         <form class="needs-validation" novalidate method="POST"
7.             action="<?= $_SERVER['PHP_SELF'] ?>">
8.             <div class="form-group row">
9.                 <label for="user_name"
10.                     class="col-sm-2 col-form-label-lg">User Name</label>
11.                 <div class="col-sm-4">
12.                     <input type="text" class="form-control"
13.                         id="user_name" name="user_name"
14.                         placeholder="Enter a user name" required>
15.                 <div class="invalid-feedback">
16.                     Please provide a valid user name.
```

```
</div>
</div>
</div>
<div class="form-group row">
    <label for="password"
           class="col-sm-2 col-form-label-lg">Password</label>
    <div class="col-sm-4">
        <input type="password" class="form-control"
               id="password" name="password"
               placeholder="Enter a password" required>
        <div class="form-group form-check">
            <input type="checkbox"
                   class="form-check-input"
                   id="show_password_check"
                   onclick="togglePassword()">
            <label class="form-check-label"
                   for="show_password_check">Show Password</label>
        </div>
        <div class="invalid-feedback">
            Please provide a valid password.
        </div>
    </div>
</div>
<button class="btn btn-primary" type="submit"
        name="signup_submission">Sign Up
</button>
</form>
</div>
</div>
// ?>
</body>
```

与之前为此应用程序创建的表单类似，您会注意到我添加了 Bootstrap 对密码和 user_name 字段的验证。因此，当用户未在这些表单字段中输入任何数据时，我们会得到图 23.3 所示的结果。

要启用此行为，与之前我们创建的需要验证的表单一样，我们需要将清单 23.3 中的 JavaScript 函数包含在 HTML `<body>` 中的 `<script>` 元素标签内（位于其他 `<script>` 标签之前）。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_348_0.png)

