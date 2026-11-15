

当你读完本章时，如果愿意，你将掌握向成员专区添加一些现实世界功能的技能。

成员需要登录才能访问成员专区，因此你将创建一个脚本让他们实现这一功能。该过程包括显示登录表单，请求他们的用户名和密码。当他们提交表单时，你将其详细信息与成员表中的记录进行核对。如果匹配，你显示欢迎页面，欢迎他们进入成员专区；否则提示他们检查登录详细信息并重试。

同样，你将创建一个脚本，允许成员从成员专区登出。

对于成员专区内的每个页面，你将加入代码以检查他们是否已登录，如果未登录，则将其重定向到登录页面。同时，你将增强 LogEntry 类，以便应用程序可以将成员专区内的页面浏览记录到 accessLog 数据库表中。

## 为 Member 类添加身份验证方法

首先要做的事。为了使成员能够登录到成员专区，你需要向 Member 类添加一个方法，该方法检查成员提供的用户名和密码以确保其正确。登录脚本将在稍后使用此方法来在成员登录时对其进行身份验证。

打开 Member.class.php 文件，将以下 authenticate() 方法添加到类的末尾，紧跟在现有 insert() 方法之后：

```
public function authenticate() {
    $conn = parent::connect();
    $sql = "SELECT * FROM " . TBL_MEMBERS . " WHERE username = :username
    AND password = password(:password)";

    try {
        $st = $conn->prepare( $sql );
        $st->bindValue( ":username", $this->data["username"], PDO::PARAM_STR );
        $st->bindValue( ":password", $this->data["password"], PDO::PARAM_STR );
        $st->execute();
        $row = $st->fetch();
        parent::disconnect( $conn );

        if ( $row ) return new Member( $row );
    } catch ( PDOException $e ) {
        parent::disconnect( $conn );
        die( "Query failed: " . $e->getMessage() );
    }
}
```

此方法获取对象 username 和 password 字段中存储的用户名和密码，并在成员表中查找具有该用户名和密码的记录。请注意，查询使用 MySQL 的 password() 函数对密码进行加密；表中存储的密码已加密，因此对象中存储的纯文本密码需要加密，以便与表中的密码进行比较。

如果找到与用户名和密码匹配的记录，则该记录作为新 Member 对象返回。否则，不返回任何内容。

## 增强 LogEntry 类以记录页面浏览

每次成员在成员专区中查看页面时，你都将在 accessLog 表中记录该事件。为此，你需要向 LogEntry 类添加一个方法。打开 LogEntry.class.php 文件，将以下 record() 方法添加到类的末尾，位于 getLogEntries() 方法之后：

```
public function record() {
    $conn = parent::connect();
    $sql = "SELECT * FROM " . TBL_ACCESS_LOG . " WHERE memberId = :memberId
    AND pageUrl = :pageUrl";
    try {
        $st = $conn->prepare( $sql );
        $st->bindValue( ":memberId", $this->data["memberId"], PDO::PARAM_INT );
        $st->bindValue( ":pageUrl", $this->data["pageUrl"], PDO::PARAM_STR );
        $st->execute();
        if ( $st->fetch() ) {
            $sql = "UPDATE " . TBL_ACCESS_LOG . " SET numVisits = numVisits + 1
            WHERE memberId = :memberId AND pageUrl = :pageUrl";
            $st = $conn->prepare( $sql );
            $st->bindValue( ":memberId", $this->data["memberId"], PDO::PARAM_INT );
            $st->bindValue( ":pageUrl", $this->data["pageUrl"], PDO::PARAM_STR );
            $st->execute();
        } else {
            $sql = "INSERT INTO " . TBL_ACCESS_LOG . " ( memberId, pageUrl,
            numVisits ) VALUES ( :memberId, :pageUrl, 1 ) ";
            $st = $conn->prepare( $sql );
            $st->bindValue( ":memberId", $this->data["memberId"], PDO::PARAM_INT );
            $st->bindValue( ":pageUrl", $this->data["pageUrl"], PDO::PARAM_STR );
            $st->execute();
        }
        parent::disconnect( $conn );
    } catch ( PDOException $e ) {
        parent::disconnect( $conn );
        die( "Query failed: " . $e->getMessage() );
    }
}
```

record() 方法获取对象 memberId 和 pageUrl 数据字段中存储的成员 ID 和页面 URL，并使用它们在 accessLog 表中记录页面浏览。如果表中已为该特定成员和页面存在一行，则其 numVisits 字段会通过 UPDATE 语句递增。如果该行不存在，则通过 INSERT 语句将其创建，并将 numVisits 设置为 1。

## 添加更多公共代码

由于成员专区页面将位于读书俱乐部文件夹内的子文件夹中，你需要修改 `common.inc.php` 中的 `displayPageHeader()` 函数，以便在从成员专区内的页面调用时更改 `common.css` 样式表的 URL。将函数定义的第一行改为：

```
function displayPageHeader( $pageTitle, $membersArea = false ) {
```

现在，在函数中，将包含样式表的行改为：

```
<link rel="stylesheet" type="text/css" href="<?php if ( $membersArea )
echo "../" ?>../common.css" />
```

如果向函数传递第二个参数 `true`，这会在 `common.css` URL 中添加额外的 "../"。

接下来，添加一个函数来检查成员是否已登录。这将从成员专区中的每个页面调用。如果未登录的用户尝试访问成员专区中的页面，你希望将其重定向到登录页面。将以下 `checkLogin()` 函数添加到 `common.inc.php` 文件中现有 `setSelected()` 函数之后：

```
function checkLogin() {
    session_start();
    if ( !$_SESSION["member"] or !($_SESSION["member"] = Member::getMember( $_SESSION["member"]->getValue( "id" ) )) {
        $_SESSION["member"] = "";
        header( "Location: login.php" );
        exit;
    } else {
        $logEntry = new LogEntry( array (
            "memberId" => $_SESSION["member"]->getValue( "id" ),
            "pageUrl" => basename( $_SERVER["PHP_SELF"] )
        ) );
        $logEntry->record();
    }
}
```

此函数使用 `session_start()` 确保 PHP 会话处于活动状态，然后检查 `$_SESSION` 超全局数组中的 "member" 元素是否存储了一个 `Member` 对象；这表明成员已登录，如下一节所示。如果找到了 `Member` 对象，则通过调用 `Member::getMember()` 从数据库重新加载它。这不仅确保会话中的数据是最新的，还确保当前登录的成员确实存在于 `members` 表中（例如，如果成员在登录期间被删除了，则不应允许其继续使用系统）。

如果未找到 `$_SESSION` 元素，或其包含的 `Member` 对象不再存在于数据库中，则会清除 `$_SESSION` 元素（以避免再次查找成员），使用 PHP `header()` 函数将用户重定向到登录页面，并使用 PHP `exit` 命令退出应用程序（这防止任何受保护页面内容发送到浏览器）。如果找到了 `Member` 对象，则通过创建新的 `LogEntry` 对象，用登录成员的 ID 和当前页面 URL 填充它，并调用对象的 `record()` 方法来记录页面浏览。

页面 URL 从 $_SERVER 超全局数组的 "PHP_SELF" 元素中检索：

```
"pageUrl" => basename( $_SERVER["PHP_SELF"] )
```

$_SERVER 是另一个有用的超全局变量，类似于你在第 7 章和第 9 章中遇到的那些。它存储与 Web 服务器和脚本环境相关的各种值。"PHP_SELF" 元素存储当前页面相对于网站顶层的 URL。例如，如果查看 http://www.example.com/myscripts/script.php 处的 PHP 脚本，则 $_SERVER[ "PHP_SELF" ] 设置为 /myscripts/script.php。为此应用程序，你只想存储页面的文件名——例如 diary.php——因此使用 PHP 的 basename() 函数删除 URL 的路径部分。

你在第 10 章中研究了会话，将在第 16 章中更详细地了解 $_SERVER 超全局变量。

## 编写登录页面脚本

现在你已经更新了类和公共代码，可以创建显示和处理成员登录页面的脚本了。首先，在 book_club 文件夹中创建一个 members 文件夹；该文件夹不仅保存登录脚本，还保存成员专区的受保护页面。在此 members 文件夹中，创建以下脚本并将其命名为 login.php：

```
<?php
require_once( "../common.inc.php" );
session_start();

if ( isset( $_POST["action"] ) and $_POST["action"] == "login" ) {
    processForm();
} else {
    displayForm( array(), array(), new Member( array() ) );
}

function displayForm( $errorMessages, $missingFields, $member ) {
    displayPageHeader( "Login to the book club members' area", true );

    if ( $errorMessages ) {
        foreach ( $errorMessages as $errorMessage ) {
            echo $errorMessage;
        }
    } else {
?>
<p>To access the members' area, please enter your username and password
below then click Login.</p>
<?php } ?>

<form action="login.php" method="post" style="margin-bottom: 50px;">
    <div style="width: 30em;">
        <input type="hidden" name="action" value="login" />

        <label for="username"><?php validateField( "username", $missingFields )
        ?>>Username</label>
```

