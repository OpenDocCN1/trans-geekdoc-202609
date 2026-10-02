
两种方法都使用 HTTP 401 响应来提示用户输入登录信息。代码 401 是“Unauthorized”（未授权）响应。可以仅发送该代码而不发送指示客户端使用何种认证方法的指令，在这种情况下客户端会显示响应的主体。或者，可以发送 WWW-Authenticate 头部，它会告诉客户端使用两种认证方案中的哪一种。

## Basic Authentication

基础认证自 HTTP 早期就已存在。标准定义了一种将登录凭据作为 URL 的一部分以及 HTTP 头部的一部分来指定的方法。

通常只有在用户点击链接或书签时，或在执行非常简单的 HTTP 获取脚本时，才会通过 URL 传递用户名和密码。通过 URL 传递信息看起来像这样：

```
http://username:password@example.com/
```

需要注意的是，这种做法非常不安全，以至于 Internet Explorer 以及可能的其他浏览器完全禁用了它，主要有两个原因，都与 URL 通常会被记录这一事实有关：

- **用户名和密码会以明文形式清晰地出现在 Web 服务器日志中。** 即使你完全信任服务器管理员或自己管理日志，也不是一个好主意让用户密码以明文形式散落各处。
- **URL 也会出现在客户端浏览器历史记录中。** 任何人都可以轻松返回到需要身份验证的站点。这在公共计算机上尤其是个问题。

基于 URL 的方法应避免使用，即使在使用 SSL 时也是如此，原因如上所述。然而，即使密码不通过 URL 传递，也并不安全。当密码通过 HTTP Authorization 请求头传递时，它会以 base64 编码的字符串发送。Base64 只是使用仅 ASCII 字符表示二进制数据的另一种方式；它类似于十六进制（base16）。在此情况下，它主要用作一种混淆数据的方式，并确保如果密码或用户名包含二进制字符时能得到正确处理。它只提供了额外的安全性的假象，因为它可以很容易地解码。但它仍然比将用户名和密码放在 URL 中要好。

要强制进行身份验证，必须发送 HTTP 401 响应以及认证类型。本节创建一个基础认证类，以便每个部分都作为成员方法呈现。以下方法强制客户端进行身份验证：

```
public function forceAuthentication() {
    header('WWW-Authenticate: Basic realm="'.$this->realm.'"');
    header('HTTP/1.0 401 Unauthorized');
    die( $this->unauthorizedNotice );
}
```

该方法会发送认证类型以及 realm。realm 主要向用户显示一个友好的名称，但如前所述，它还有其他用途。消息在前述代码中由变量 $unauthorizedNotice 引用，在用户在认证对话框中点击取消时显示。由于此时用户未通过身份验证，因此最好结束脚本的执行。规范并未限制用户名和密码请求的次数，因此完整的应用程序也可能跟踪无效密码尝试次数，并在达到限制时显示通知。要在不提示输入密码的情况下显示消息，只需发送状态头而不发送认证头即可。

> 最佳实践是永远不要在用户无权查看页面时发送 200（Found）头。相反，应发送 401（Unauthorized）头。同样的做法适用于找不到的数据（404）和应用程序错误（500 范围）。

类中的另一个方法可以读取服务器变量并验证它们。可用的两个变量是 PHP_AUTH_USER 和 PHP_AUTH_PW，两者都可以在 $_SERVER 全局数组中找到：

```
public function requireAuthentication() {
    if ( array_key_exists('PHP_AUTH_USER', $_SERVER) &&
        array_key_exists('PHP_AUTH_PW', $_SERVER) ) {

        session_start();

        $saltedPassword = md5($_SERVER['PHP_AUTH_PW'].'-'.$this->salt);

        if ( $_SERVER['PHP_AUTH_USER'] != $_SESSION['user'] ||
            $saltedPassword != $_SESSION['password'] ) {

            $conn = mysql_connect( self::$db_host,
                                   self::$db_user,
                                   self::$db_password );
            mysql_select_db( self::$database, $conn );

            $query = "SELECT * FROM `users` WHERE `username`='s' AND ".
                     "`password`='s'";
            $query = sprintf($query, mysql_escape_string($_SERVER['PHP_AUTH_USER']),
                             $saltedPassword );

            $user = mysql_fetch_assoc( mysql_query($query) );
            mysql_close($conn);

            if ( $user ) {
                $_SESSION['user'] = $_SERVER['PHP_AUTH_USER'];
                $_SESSION['password'] = $saltedPassword;
            } else {
                $this->forceAuthentication();
            }
        }
    } else {
        $this->forceAuthentication();
    }
}
```

> 你可能以前使用过会话。它们是与特定客户端关联的服务器端数据存储机制。它们通常基于 cookie 进行键控，但有时也会使用通过查询字符串传递的值。在此情况下，会话用于存储已登录的用户和密码的哈希值。

会话的存储方式是可定制的，如本章后面将看到的那样。

前面的示例没有任何错误检查。这样做是为了让你能够轻松阅读以了解其工作原理。生产应用程序应更加健壮并具备错误检查机制。

前述方法中的会话存储已认证用户的信息。它不用于直接确定用户是否已登录，因为客户端会在每次请求时发送认证头。相反，使用会话比为每个页面视图触发数据库查询更高效。如果用户名和密码与会话匹配，则无需检查数据库。会话还可用于存储其他经常引用的计算信息，这些信息以后可能很昂贵。

在使用 Microsoft IIS Web 服务器时，在旧版本的 PHP 中 PHP_AUTH 变量未被设置。此示例认证代码未考虑这一点，因为假设应用程序使用 PHP 5 或更高版本。在旧版本的情况下，HTTP_AUTHORIZATION 服务器变量包含头的完整内容（包括认证类型）。PHP 参考手册包含一种轻松解析此数据的方法：

```php
list($user, $pw) = explode(':',
    base64_decode(substr($_SERVER['HTTP_AUTHORIZATION'], 6)));
```

完成的类包含数据库的配置变量以及认证 realm。请记住，如果网站上有任何敏感信息，基础认证应在 SSL 上进行。任何未加密的页面都可能被用作攻击的潜在向量，因为认证数据会随每次请求发送。

一种替代的认证方法——一种不会以明文发送密码的方法——是摘要认证。

## Digest Authentication

摘要认证与基础认证不同，它依赖于使用共享密钥对各种数据创建单向哈希。共享密钥是用户的密码。此方法使得可以在不通过网络发送密码的情况下对用户进行身份验证。

哈希涉及基于客户端和服务器都已知的数据创建长字符串，然后使用该字符串连同密码创建 MD5 哈希。服务器不需要存储任何公共变量。它们是随每次请求一起传递的。创建哈希时使用多条数据：

- **realm：** 与基础认证相同。它只是一个显示给用户的字符串，以及客户端区分多个认证区域的一种方式。在摘要认证中，它也用作哈希的一部分。
