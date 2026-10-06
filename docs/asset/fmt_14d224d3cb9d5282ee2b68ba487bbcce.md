
> 你可能以前使用过会话。它们是与特定客户端关联的服务器端数据存储机制。它们通常基于 cookie 进行键控，但有时也会使用通过查询字符串传递的值。在此情况下，会话用于存储已登录的用户和密码的哈希值。

会话的存储方式是可定制的，如本章后面将看到的那样。

前面的示例没有任何错误检查。这样做是为了让你能够轻松阅读以了解其工作原理。生产应用程序应更加健壮并具备错误检查机制。

前述方法中的会话存储已认证用户的信息。它不用于直接确定用户是否已登录，因为客户端会在每次请求时发送认证头。相反，使用会话比为每个页面视图触发数据库查询更高效。如果用户名和密码与会话匹配，则无需检查数据库。会话还可用于存储其他经常引用的计算信息，这些信息以后可能很昂贵。

在使用 Microsoft IIS Web 服务器时，在旧版本的 PHP 中 `PHP_AUTH` 变量未被设置。此示例认证代码未考虑这一点，因为假设应用程序使用 PHP 5 或更高版本。在旧版本的情况下，`HTTP_AUTHORIZATION` 服务器变量包含头的完整内容（包括认证类型）。PHP 参考手册包含一种轻松解析此数据的方法：

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

- **域:** 此指令是一个在哈希创建过程中不使用但允许你在多个域之间使用相同身份验证的值。它是一个以空格分隔的域名列表，作为客户端的提示。它不是必需的值。
- **随机数:** 也称为“number used once”。你使用此指令来防止重放攻击。重放攻击是指用户计算机上的软件或网络上的恶意机器记录用户身份验证信息。然后该信息稍后会被“replayed”以冒充用户访问应用程序。确保同一个 nonce 不被用于多个请求可以解决该问题。Nonce 值被用于多种形式的身份验证，包括 OpenID（一种使用来自不同站点的凭据验证对网站访问的方法）。在最严格的形式下，nonce 在单次使用后应变为无效（或 stale）。在一定时间后使 nonce 无效也很常见。
- **不透明:** 一个应原样传回服务器的字符串。它可以验证所访问的 realm 是否与生成哈希时相同的 realm；然而，由于它未用于生成哈希，因此很容易被伪造。
- **过期:** 应用程序还可以向客户端传递 stale 指令（设为 TRUE），表示 nonce 在某一时刻有效但现在不再有效。服务器应在发送此请求前检查哈希对设置的 nonce 是否有效。如果哈希无效，应用程序不应将其标记为 stale，因为当遇到 stale 响应消息时，客户端可以选择仅使用新的 nonce 重新生成哈希。当用户名或密码错误时将 nonce 标记为 stale 会导致混淆。
- **算法:** 无需指定，因为它默认为“MD5”（下一个示例使用的就是它）。
- **qop:** 一个指定“保护质量”的引号字符串。它是可选的，但应为与先前摘要规范的向后兼容而指定。两个常见值是 auth 和 auth-int（本书使用前者）。

> *摘要身份验证规范并不要求 nonce 实际上是一个数字。例如，它可以是一个编码字符串，指定诸如 nonce 创建时间等值，后续可以解码以确定 nonce 是否已过期。也可以拥有永不过期的 nonce。然而，这种方法不推荐，因为它完全不能防止重放攻击。本节中的示例使用在 120 秒后过期的 nonce。存在更复杂的生成 nonce 的方法，这里不予涵盖。*

> *你可以在 RFC2617（HTTP Authentication）和 RFC2069（Digest Access Authentication）中找到有关指令和哈希计算的更多详细信息。*

摘要身份验证的头部与基本身份验证非常相似。然而，在摘要身份验证中，有必要指定本节前面列出的指令。响应头中唯一发生变化的部分是 `WWW-Authenticate`：

```
header('WWW-Authenticate: Digest realm="'.$this->realm.
'",qop="auth",nonce="'.uniqid().'",opaque="'.md5($this->realm).
'"'.($stale ? ',stale="TRUE"'));
```

现在可以向 `requireAuthentication()` 调用传递一个名为 `$stale` 的参数。记住，`stale` 用于告诉客户端身份验证是正确的但已太旧而无法再使用。客户端很可能会通过使用相同的密码重新生成哈希来响应，而不会再次提示用户输入密码。

为了验证发送的密码，有必要使用共享密钥生成客户端创建的相同字符串。如果字符串不匹配，则共享密钥（密码）错误。本节介绍 MD5 算法，这是最简单的实现方式。RFC 规定了如何计算三个部分：A1、A2 和最终结果。A1 和 A2 部分是各种指令连接后的哈希值。最终字符串是将 A1 和 A2 与 nonce 连接后进行哈希。

PHP 文档提供了一个非常有用的辅助函数来解析客户端返回的字符串：

```
private function parseDigest($txt)
{
    // protect against missing data
    $needed_parts = array('nonce'=>1, 'nc'=>1, 'cnonce'=>1, 'qop'=>1,
                          'username'=>1, 'uri'=>1, 'response'=>1);
    $data = array();
    $keys = implode('|', array_keys($needed_parts));
    preg_match_all('@(' . $keys . ')=(?:(["\'])([^\']+?)\2|([^\s,]+))@',
                   $txt, $matches, PREG_SET_ORDER);
    foreach ($matches as $m) {
        $data[$m[1]] = $m[3] ? $m[3] : $m[4];
        unset($needed_parts[$m[1]]);
    }
    return $needed_parts ? false : $data;
}
```

本书通常使用 `/` 来包裹正则表达式。然而，也可以使用 `@`，如前例所示，或任何其他字符。

该代码获取字符串的所有部分。如果数组 `$needed_parts` 不为空，则 RFC 要求的一些信息缺失。使用该实用函数（源自 http://us2.php.net/manual/en/features.http-auth.php 中的示例），然后可以生成各个部分：

```
public function requireAuthentication() {
    if ( !($directives = $this->parseDigest($_SERVER['PHP_AUTH_DIGEST'])) )
```

```
$this->forceAuthentication();
if ( $this->getValidDigest($directives) != $directives['response'] )
    $this->forceAuthentication();
}
```

```
private function getValidDigest( $directives ) {
$conn = mysql_connect( self::$db_host,
                        self::$db_user,
                        self::$db_password );
mysql_select_db( self::$database, $conn );
$query = "SELECT * FROM `users` WHERE `username`='%s';"
$query = sprintf($query, mysql_escape_string($directives['username']));
$user = mysql_fetch_assoc( mysql_query($query) );
mysql_close($conn);
if ( !$user ) return false;
$A1 = md5($directives['username'] . ':' .
          $this->realm . ':' . $user['password']);
$A2 = md5($_SERVER['REQUEST_METHOD'] . ':' . $directives['uri']);
$validDigest = md5($A1 . ':' . $directives['nonce'] . ':' .
                   $directives['nc'] . ':' . $directives['cnonce'] . ':' .
                   $directives['qop'] . ':' . $A2);
return $validDigest;
}
```

> 前面的示例要求用于计算 `$A1` 的密码为明文。这只是为了便于理解，不应在生产应用中这样做。如前所述，以这种方式将密码存储在数据库中不是一种良好实践。存储密码明文的替代方案包括将 `$A1` 的整个值存储在数据库中（只要 realm 不变，它就不会改变），或使用双向算法加密密码数据。

PHP 应用中最常见的方法是实际上从头创建身份验证系统。虽然内置的 HTTP 身份验证方法很有用，但它们的可定制性和灵活性都不高，并且存在相关安全问题。例如，登录对话框无法设置样式以符合应用程序其余部分的视觉效果，并且两种身份验证方法都容易受到中间人攻击。

## 纯 PHP 身份验证

纯 PHP 身份验证采用的方法与本章迄今为止看到的标准 HTTP 方法不同。纯 PHP 系统通常不使用标准 HTTP 头，而是显示嵌入在其他内容中的用户名和密码表单。然后，一旦用户

进行身份验证，就会放置一个 cookie 来维护用户会话。你也可以在 PHP 中实现其他方法，例如 OAuth 和 OpenID；然而，它们不会提示输入用户名和密码，而是启动应用程序与身份验证服务器之间的握手。

如果不采取适当的预防措施，很容易创建出恶意人员可以劫持用户会话的应用程序。这种情况发生的两种最常见方式如下：

- 恶意用户通过嗅探网络流量或通过 XSS 攻击（在第 14 章中介绍）窃取用户的 cookie。然后恶意用户在其机器上镜像这些 cookie 以冒充合法用户。
- 恶意用户嗅探网络上的流量并看到用户名和密码以明文形式在 cookie 中传输，并使用该信息以用户身份登录。

第一个场景实际上是一种重放攻击的形式，需要客户端指纹识别或 nonce 来防止。第二个场景更容易防止，本节的大部分重点将放在它上面。防止用户名和密码被窃取有两种方法。第一种是使用服务器端会话来存储用户信息。第二种是在加密的 cookie 中存储有关用户的全部凭据信息。

### 使用 PHP 会话

PHP 会话是一种在服务器上存储有关用户的信息的方式，这样就不需要在每次请求时通过 cookie 传递所有信息。相反，只有一个 session ID 存储在 cookie 中，然后检索完整的会话。PHP 中的会话通过 session API 创建和维护，该 API 由许多函数组成，最常见的是 `session_start()`。会话初始化后，会话数据存储在 `$_SESSION` 全局数组中。对数组所做的更改会反映在会话中。

> 会话不需要使用 cookie。会话 ID 也可以通过 GET 和 POST 变量传递。会话 ID 传递的行为可以在 PHP 配置中控制。

默认会话处理将会话数据存储在磁盘上。可以覆盖会话处理以使用不同的存储机制。本节中的示例编写了一个类，将会话数据存储在 MySQL 数据库中。此新数据库的表如下所示：

```
CREATE TABLE `session` (
  `sessionid` VARCHAR(128),
  `uid` INT,
  `data` MEDIUMBLOB,
  `timestamp` INT,
  `ip` VARCHAR(15),
  PRIMARY KEY ( `sessionid` ),
  KEY ( `timestamp`, `sessionid` )
)
```

键之前的最后一个字段是为了增加一点额外安全性以防止会话被窃取而添加的。当会话打开时，脚本会检查 IP 是否与客户端的 IP 匹配，如果不匹配则抛出异常。这样，如果有人试图劫持会话，会话 cookie 就会变得毫无价值。不幸的是，这仅在攻击者不在同一网络上并且因此没有与用户相同的外部 IP 地址时才成立。然而，它确实提供了更精细的安全性。

时间戳字段稍后用于使旧会话过期。本节后面会详细介绍。

要使用自定义会话处理器，必须在会话开始之前先注册它们。一种良好的做法是拥有一个 `session.php` 文件，该文件始终包含在脚本的第一行。

注册新的会话 I/O 处理器的方法是 `session_set_save_handler()`。该方法接受六个参数，全部都是回调函数。注册事件处理器的简单代码如下所示：

```
session_set_save_handler( 'custom_session_open', 'custom_session_close',
    'custom_session_read', 'custom_session_write',
    'custom_session_destroy', 'custom_session_gc' );
```

第一个回调函数是 `open`，在此示例中它会创建到 MySQL 的连接。`open` 函数有两个参数。第一个参数是会话应保存的路径。在这个简单的基于 MySQL 的示例中它只是被忽略。路径是脚本被允许写入会话信息的目录。文件名通常由会话名称加上前缀和扩展名组成。会话名称是第二个参数，并用作表的主键。

第二个函数 `close` 函数，在脚本完成对会话的读写并且不再计划使用它时被调用。需要注意的是，会话是加锁的。同一会话不能同时被多个脚本读取或写入。有时使用 `session_write_close()` 提前关闭会话是有用的。此方法将在后面审查 `CustomSession` 类时更详细地讨论。

`read` 和 `write` 函数是互补的。会话数据以字符串形式存储。在正常使用下，字符串的内容无关紧要，因此 `read` 函数只是从存储中原样返回一个字符串，而 `write` 函数则在不更改或处理的情况下将其写入存储。在此示例中，`open` 函数相当于 MySQL `SELECT`，而 `write` 函数是 `INSERT / UPDATE` 查询。

`destroy` 函数仅在手动使用 `session_destroy()` 销毁会话时使用。销毁会话仅会删除与其关联的所有数据。它不会使会话 ID 或 cookie 失效。在本章后面的身份验证系统中，还需要取消设置会话 cookie。

旧会话需要定期从系统中清除。这就是垃圾回收的工作。请注意，它与你在第 8 章看到的不是同一个。它定期执行只是为了清理旧会话。收集器被执行的概率是 `php.ini` 变量 `session.gc_maxlifetime`、`session.gc_probability` 和 `session.gc_divisor` 的函数。当垃圾收集器执行时，它会采用会话的最大生命周期，并预期删除所有超过该生命周期的会话。默认值为 24 分钟（或 1440 秒）。

> 如果超时不是一个键，则删除旧会话可能是一项昂贵的操作，尤其是在你有数百万个会话时。然而，将该值设为键也有其自身的问题，主要是所有键必须是唯一的。本章中的表设计使用时间戳和会话 ID 的复合键，以避免在多个用户在同一秒登录时发生冲突的情况。

第 3 章详细介绍了回调函数。此会话类使用回调函数引用单例会话类中的会话处理方法。基本会话类如下所示，如清单 12-2 所示：

### 清单 12-2：CustomSession.class.php

```php
<?php
class CustomSession {
    private static $db_host = "localhost";
    private static $db_user = "sessions";
    private static $db_password = "password";
    private static $database = "sessions";
    private $conn;
    public static function getInstance() {
        static $instance = null;
        if ( $instance == null ) {
            $instance = new CustomSession();
        }
        return $instance;
    }
    public function __construct() {
```
