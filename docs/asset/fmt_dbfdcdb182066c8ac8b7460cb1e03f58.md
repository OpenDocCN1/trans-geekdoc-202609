
```php
session_set_save_handler(
    array($this,"open"), array($this,"close"),
    array($this,"read"), array($this,"write"),
    array($this,"destroy"), array($this,"gc") );
}

public function __destruct() {
    session_write_close();
}

public function open( $path, $id ) {
    $this->conn = mysql_connect( CustomSession::$db_host,
                                CustomSession::$db_user,
                                CustomSession::$db_password );
    mysql_select_db( CustomSession::$database, $this->conn );
}

public function close() {
    mysql_close($this->conn);
}

public function read( $id ) {
    $escaped_id = mysql_escape_string( $id );
    $res = $this->query("SELECT * FROM `session` WHERE `sessionid`='$escaped_id'");
    if ( $row = mysql_fetch_assoc( $res ) ) {
        $this->query("UPDATE `session` "."SET `timestamp` = UTC_TIMESTAMP() "."WHERE `sessionid`='$escaped_id'");
        return $row['data'];
    }
    return "";
}

public function write( $id, $data ) {
    $query = "REPLACE INTO `session` "."(`sessionid`, `data`, `ip`, `timestamp`) "."VALUES ('%s', '%s', '%s', UNIX_TIMESTAMP(UTC_TIMESTAMP()))";
    $this->query(
        sprintf( $query, mysql_escape_string($id),
                mysql_escape_string($data),
                $_SERVER["REMOTE_ADDR"] ) );
}

public function destroy( $id ) {
    $escaped_id = mysql_escape_string( $id );
    $res = $this->query( "DELETE FROM `session` WHERE `id`='$escaped_id'" );
    return ( mysql_affected_rows($res) == 1 );
}

public function gc( $lifetime ) {
    $this->query( "DELETE FROM `session` WHERE ".
        "UNIX_TIMESTAMP(UTC_TIMESTAMP())-'timestamp' > $lifetime"
    );
}

public function query( $query ) {
    $res = mysql_query($query, $this->conn);
    return $res;
}
}
?>
```

在之前的代码中有几件重要的事情需要注意。最不明显的是，会话以序列化字符串的形式存储。回顾第 1 章，序列化字符串可能包含二进制字符，即使数据本身不是二进制的。此外，会话数据本身也可能是二进制的。因此，绝对不要在会话数据字符串上使用非二进制安全函数非常重要。这也是会话数据的数据类型为 `blob` 的原因。使用 `blob` 意味着你无法有效地查询会话数据，但它获得了对二进制数据的高效存储。

自 PHP 5.0.5 起，会话会在对象已被垃圾回收后自动写入并关闭。当使用对象作为会话处理器时，这会导致问题。为了解决这个问题，类析构函数调用 `session_write_close()`，这会导致写入和关闭立即发生。虽然这在此类中不是一个因素，但同样的问题也会影响异常抛出，因为一旦所有对象都被清理，就不可能再创建新对象。

之前的数据库设计留出了与会话一起存储用户 ID 的空间。通过将用户 ID 与会话一起存储，应用程序可以确定当前处于活跃状态的用户。由于会话会过期，可以安全地假设会话表中任何有行的用户最近已查看了网站上的页面。然而，这需要会话类了解会话的内容。这种行为在大多数应用程序中是可以接受的，但如果会话类可以在通用情况下使用，则并不理想。

会话确实会过期。因此不应使用它们来存储无法稍后重建的数据。仅凭会话不足以确定用户的登录状态。它可以包含诸如计算和缓存数据之类的信息。例如，如果电子商务网站的用户将电脑无人看管 1440 秒就丢失购物车，那是不希望的。一个或多个额外的 cookie 可以传递用户登录凭据和其他信息。

## 构建安全 Cookie

用户登录凭据绝不应以明文形式存储在应用程序中，攻击者可以轻松读取或复制。登录 cookie 就像一把钥匙，可以打开网页的所有功能并访问可能敏感的用户数据。本节概述了一个系统，你可以用它来创建防黑客和防劫持的 cookie。为此，cookie 必须存储一些基本信息：

- 用户 ID
- 用户上次已知的 IP 地址
- 一个时间戳

第一个字段不言自明。它是用来识别哪个用户已登录的。第二两个字段是为了增加一点额外安全性。

上次已知的 IP 地址用于与当前向服务器发出请求的 IP 地址进行比较。它也可以与会话表中的 IP 地址字段进行比较。如果 cookie 中的 IP 地址与远程客户端的 IP 地址不匹配，则 cookie 可能已被劫持。也有可能是用户只是使用笔记本电脑在不同 WiFi 接入点之间房间间行走。

时间戳是 cookie 创建的日期和时间。这具有双重用途。第一个是确定用户已登录多长时间。极长的登录时间可能意味着用户已将电脑无人看管。在这方面，时间戳就像基于时间的 nonce。时间戳的第二个用途是确保在登录时生成的 cookie 从不完全相同。例如，如果用户在中午登录一次，又在 3:00 登录一次，则 cookie 两次都会不同。这种简单技术使得攻击者更难在 cookie 中看到模式，并且结合过期时间，可以关闭重放攻击的机会窗口。

可以使用这种 cookie 设计表示三种信任级别：

- **最受信任的：** IP 地址匹配且时间戳为最新。
- **第二受信任的：** IP 地址匹配但时间戳已旧。用户可能已离开电脑无人看管。
- **最不受信任的：** IP 地址不匹配。

应用程序设计者需要确定特定数据所需的信任级别。例如，如果页面只是向当前登录用户问候，则不需要高信任级别。如果应用程序显示敏感数据或允许用户进行购买，则有必要将访问限制为仅最受信任的会话。

在上述任何情况下都不应自动注销用户。相反，正确的做法是再次提示用户输入密码。如果用户输入正确的密码，则时间戳和 IP 将被重置。例如，当用户在线访问商店并在购物一段时间后决定查看她的订单历史时即为这种情况。由于时间戳已旧，用户可能会再次被提示输入密码；将商品添加到购物车可能不需要高信任度，但查看订单历史需要。

如果信息可以被轻易读取或写入，则对安全毫无用处。为了解决这个问题，有必要对 cookie 进行加密。幸运的是，PHP 提供了多种加密方法。设置加密 cookie 的代码可能如下所示：

```
$cookieData = serialize( $user );
$iv_size = mcrypt_get_iv_size(MCRYPT_RIJNDAEL_256, MCRYPT_MODE_CBC);
srand();
$iv = mcrypt_create_iv($iv_size, MCRYPT_RAND);
$encryptedData = mcrypt_encrypt(MCRYPT_RIJNDAEL_256, $secret,
    $cookieData, MCRYPT_MODE_CBC, $iv);
setcookie( 'user', base64_encode($encryptedData).':.:'. $iv );
```

解密 cookie 的代码非常相似：

```
list($encryptedData,$iv) = explode(':.:', $_COOKIE['user']);
$rawData = mcrypt_decrypt( MCRYPT_RIJNDAEL_256, $secret,
    base64_decode($encryptedData),
    MCRYPT_MODE_CBC, $iv );
$user = unserialize( $rawData );
```

密钥是只有应用程序知道的东西。在极其安全的环境中，根据当前登录的用户拥有动态密钥可能很有用。为此，应用程序可以使用一种系统，其中 cookie 数据实际上分为三部分：密钥、初始化向量 `$iv` 和数据。该密钥附加到密钥以生成新的混合密钥，可以是用户 ID 到随机字符串之间的任何内容。

作为最终的安全级别，用会话数据验证用户 ID 是很有用的。这种方法要求用户 ID 实际上设置在会话内部。如果两者不匹配，则存在严重问题，会话和登录 cookie 都应被销毁。如果没有会话，可以认为会话已过期，在这种情况下，在重新计算所有会话数据之前提示再次输入密码可能是明智的。

> *从可用性角度来看：好的软件不仅仅是功能齐全和安全的。它还易于使用。*
> *因为 cookie 包含用户 ID 号 `uid`，因此可以确定用户登录名。在会话变得陈旧后重新提示密码时，登录名应使用该值自动填充。*

最终结果是一个 cookie，无法被不在同一网络中的人伪造，也无法轻易解密以获取有关用户的信息。它还为访问用户数据提供了多个信任级别。

将用户名存储在此 cookie 中也可能很有用，以便使显示登录框更加容易，并且无需数据库查询。最后一步是创建一个访问已认证用户的用户类。

## 访问控制列表

访问控制列表 `ACL` 在应用程序达到任何复杂程度时都是至关重要的。它们允许对系统中谁可以执行什么操作进行精细控制。任何使用过内容管理系统的人可能都使用过 ACL。

大多数 ACL 系统中有两个权限级别：

- **组级别：** 用户可以属于一个或多个组，每个组都有自己的权限集。组可以是任何内容，但一些常见组是匿名用户、成员、高级订阅者、版主和管理员。
- **用户级别：** 用户级别权限始终覆盖组级别权限。例如，在正常情况下只有版主和管理员可以编辑博客文章，但您可以直接授予“Bob”编辑博客文章的权限。

大多数 ACL 充当白名单。如果用户在任何地方存在权限，则用户可以执行该操作。否则，他不能。知道这一点，请考虑以下四个表：

```
CREATE TABLE `groups` (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(128)
);
CREATE TABLE `group_users` (
  `user_id` INT,
  `group_id` INT,
  KEY ( `user_id`, `group_id` ),
  KEY ( `group_id` )
);
CREATE TABLE `group_permissions` (
  `group_id` INT,
  `permission` VARCHAR(50),
  KEY ( `group_id`, `permission` ),
  KEY ( `permission` )
);
CREATE TABLE `user_permissions` (
  `user_id` INT,
  `permission` VARCHAR(50),
  KEY ( `user_id`, `permission` ),
  KEY ( `permission` )
);
```

您可以通过使用两个权限表的联合来选择特定用户的所有权限。查询如下所示：

```
( SELECT `permission` FROM `group_permissions`
  WHERE `group_id` IN (
    SELECT group_id FROM group_users WHERE user_id=USER_ID
  ))
UNION
( SELECT permission FROM user_permissions WHERE user_id=USER_ID )
```

最终结果是一个字符串列表。传统上，权限以字符串形式存储；然而，完全可以增加另一个规范化级别，并拥有一个具有数字索引的可能权限表。因此，在 SQL 中授予用户发布博客条目的权限如下所示：

```
INSERT INTO `user_permissions` (`user_id`, `permission`)
VALUES (USER_ID, "blog/add");
```

> 该节中的设计是最小的 ACL。在完整的基于 Web 的系统中，您还应缓存 ACL，以便不必在每次请求时都访问数据库。只需不要忘记在用户权限更改时使缓存失效。有关缓存的更多信息，请参阅第 4 章。

可以根据需要自定义列表。此 ACL 是白名单，但您可能希望在应用程序中使用黑名单来禁止用户执行某些操作。

## 摘要

本章涵盖了实现 PHP 身份验证所需的所有组件，允许进行基本的基于 HTTP 的身份验证、摘要身份验证和纯 PHP 基于身份验证。给定应用程序中使用的方法在很大程度上取决于项目要求，并且可以在 PHP 和两种 HTTP 方法之间混合搭配。

摘要身份验证是本章介绍的三种方法中唯一不以明文发送密码的方法。然而，它确实要求密码存储在数据库中，如果应用程序设计不正确，这可能会导致安全问题。设计良好的基于摘要的系统要么在数据库中存储 A1 哈希的整个结果而不是密码，要么使用双向算法加密密码。

另外两种方法几乎总应通过 SSL 使用。少数例外情况是用户账户不包含任何敏感信息、应用程序是尚未公开发布的快速原型、它是书籍的示例应用程序，或它位于企业内部网中。最后一点仅部分正确，因为攻击者也可能来自内部。实际上，今天使用的数千个应用程序没有采取适当的措施来保护用户的密码。

第 14 章更深入地介绍了安全问题，并详细说明了如何保护 MySQL 服务器免受攻击。

# 13
## 理解 INFORMATION_SCHEMA
### 本章内容
- INFORMATION_SCHEMA 中存在哪些表
- 如何检索有关架构和表的的信息
- 如何列出用于数据库对象的核心 MySQL 元数据
- 如何检索正在运行的 MySQL 实例的检测信息
- INFORMATION_SCHEMA 存在哪些扩展

ANSI 标准 SQL 使用 INFORMATION_SCHEMA 概念定义了数据库元数据支持的级别。从版本 5.0 开始，MySQL 实现了 INFORMATION_SCHEMA，通常称为 I_S，以提供对以前在流行但非 SQL 标准 SHOW 命令中找到的信息的 SQL 访问级别。元数据是一种数据字典形式的数据，提供用户访问各种信息，包括数据库对象，如 TABLES、COLUMNS 和 VIEWS；架构元数据，如 CHARACTER_SETS；以及内部 MySQL 操作，包括 GLOBAL_STATUS、GLOBAL_VARIABLES 和 PROCESSLIST。

本章逐步介绍版本 5.0、5.1 和 5.4 alpha 版本中的 INFORMATION_SCHEMA 表。它还给出了使用 InnoDB Plugin 1.0.4 及更高版本可能的 INFORMATION_SCHEMA 扩展的示例，该插件可单独获得，并从 MySQL 5.1.38 版本开始包含在 MySQL 中。

## 使用 INFORMATION_SCHEMA

`SHOW` 命令可用于从 INFORMATION_SCHEMA 表中检索信息。如您所见，此 5.1 架构包含许多表，本章将详细介绍：

```
SHOW TABLES FROM INFORMATION_SCHEMA;
```
