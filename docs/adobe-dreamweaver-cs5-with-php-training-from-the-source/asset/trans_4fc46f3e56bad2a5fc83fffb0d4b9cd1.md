
相对链接在 include 文件中被视为相对于被 include 的页面，而不是相对于 include 文件本身的位置。虽然本脚本位于 scripts 文件夹，但它将被包含在 login.php 中，而 login.php 与 members_only.php 位于同一文件夹。因此，成功后重定向用户的相对链接需要相对于 login.php，而不是 user_authentication.php。

# 测试登录脚本

要使用登录脚本，需要在登录页面的 `DOCTYPE` 声明上方 include 它，并在登录失败时添加一个条件语句来显示错误信息。

1. 将 lesson07/start 中的 login.php 和 members_only.php 复制到 lesson07/workfiles。

2. 在 login.php 的 `DOCTYPE` 声明上方添加以下代码以 include user_authentication.php：

```php
<?php
require_once('scripts/user_authentication.php');
?>
```

3. 在设计视图中，在 Members Only 标题后插入一个新段落，输入 “Login failed. Check username and password.”，然后在属性检查器的 Class 菜单中选择 warning。这样会使文本变为粗体红色。

4. 切换到代码视图，将刚才创建的段落用如下条件语句包裹：

```php
<?php if ($failed) { ?>
<p class="warning">Login failed. Please check username and password.</p>
<?php } ?>
```

脚本在 user_authentication.php 中将 `$failed` 设为 FALSE，仅在登录尝试失败时将其设为 TRUE，因此除非用户的凭据被拒绝，否则不会显示错误信息。

### ![Image](graphics/tip.jpg)NOTE:

一些开发者会本能地把条件语句中的 HTML 转换为字符串并使用 echo 来显示，这并不必要，而且会让代码更难书写。

5 保存 login.php，并在 Live View 或浏览器中测试。页面首次加载时错误信息不显示。使用无效的用户名或密码尝试登录，错误信息会出现。

6 在未填写任何字段的情况下点击 “Sign in”，会得到如下消息：“A value for the identity was not provided prior to authentication with Zend_Auth_Adapter_DbTable.” 这来自 catch 块。未在用户名字段输入任何内容导致 Zend_Auth 抛出异常。相较于没有 try 和 catch 时冗长的错误信息，这种方式更优雅，但不适合向访客显示。

7 返回 user_authentication.php，在脚本顶部已有的条件语句内部再添加一个条件：

```php
if ($_POST) {
    if (empty($_POST['username']) || empty($_POST['password'])) {
        $failed = TRUE;
    } else {
        require_once('library.php');
```

这里使用 empty() 检查 `$_POST['username']` 或 `$_POST['password']` 是否为空。如果任一为空，则把 `$failed` 设为 TRUE。验证脚本现在位于 else 块中，仅在两个字段都有值时执行。

8 脚本最后一行会出现红色标记，提示需要为 else 块的开头添加缺失的闭合大括号。技术上讲，缺失的大括号应位于脚本底部的最后两个大括号之间，但你可以把它放在最后一行，这样红色标记就会消失。

9 保存 user_authentication.php，再次在未填写字段的情况下测试登录表单。这次会出现你自定义的红色错误信息。

10 使用已注册的用户名和密码测试登录表单。点击 “Sign in” 后，你会被导向 members_only.php。

你可以将你的代码与 lesson07/completed/login.php 以及 lesson07/completed/scripts/user_authentication01.php 进行对比。

## 密码保护页面

构建登录脚本是复杂的部分。要限制对页面的访问，你可以使用 hasIdentity() 方法，它返回 TRUE 或 FALSE。如果用户已登录，使用 getIdentity() 获取其信息；否则，用 header('Location: login.php') 将用户重定向到登录页。

1. 创建一个 PHP 页面，保存为 lesson07/workfiles/scripts 中的 **restrict_access.php**，并删除 Dreamweaver 自动插入的 HTML。

```php
<?php
require_once('library.php');
try {
    $auth = Zend_Auth::getInstance();
    if ($auth->hasIdentity()) {
        $identity = $auth->getIdentity();
    } else {
        header('Location: login.php');
        exit;
    }
} catch (Exception $e) {
    echo $e->getMessage();
}
```

2. 要对 members_only.php 进行密码保护，只需在其 `DOCTYPE` 声明上方 include 该脚本：

```php
<?php
require_once('scripts/restrict_access.php');
?>
```

如果你已经登录，需要先注销才能测试。为此，你需要一个注销按钮和脚本，这将在下一部分介绍。

## 显示已登录用户的信息

restrict_access.php 中的代码调用 getIdentity() 并将用户名、名和姓作为 `$identity` 的属性保存，从而可以在登录后用名字问候用户。

1. 在代码视图中，修改 members_only.php 第一个段落的开头：

```html
<p>Hi, <?php echo "$identity->first_name $identity->family_name"; ?>. You're in!</p>
```

列标题被视为 `$identity` 的属性，使用 `->` 运算符即可访问包含用户信息的属性。

2. 保存 members_only.php，重新登录后即可看到名字问候。
