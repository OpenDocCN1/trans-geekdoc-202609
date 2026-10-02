
键之前的最后一个字段是为了增加一点额外安全性以防止会话被窃取而添加的。当会话打开时，脚本会检查 IP 是否与客户端的 IP 匹配，如果不匹配则抛出异常。这样，如果有人试图劫持会话，会话 cookie 就会变得毫无价值。不幸的是，这仅在攻击者不在同一网络上并且因此没有与用户相同的外部 IP 地址时才成立。然而，它确实提供了更精细的安全性。

时间戳字段稍后用于使旧会话过期。本节后面会详细介绍。

要使用自定义会话处理器，必须在会话开始之前先注册它们。一种良好的做法是拥有一个 session.php 文件，该文件始终包含在脚本的第一行。

注册新的会话 I/O 处理器的方法是 session_set_save_handler()。该方法接受六个参数，全部都是回调函数。注册事件处理器的简单代码如下所示：

```
session_set_save_handler( 'custom_session_open', 'custom_session_close',
    'custom_session_read', 'custom_session_write',
    'custom_session_destroy', 'custom_session_gc' );
```

第一个回调函数是 open，在此示例中它会创建到 MySQL 的连接。open 函数有两个参数。第一个参数是会话应保存的路径。在这个简单的基于 MySQL 的示例中它只是被忽略。路径是脚本被允许写入会话信息的目录。文件名通常由会话名称加上前缀和扩展名组成。会话名称是第二个参数，并用作表的主键。

第二个函数 close 函数，在脚本完成对会话的读写并且不再计划使用它时被调用。需要注意的是，会话是加锁的。同一会话不能同时被多个脚本读取或写入。有时使用 session_write_close() 提前关闭会话是有用的。此方法将在后面审查 CustomSession 类时更详细地讨论。

read 和 write 函数是互补的。会话数据以字符串形式存储。在正常使用下，字符串的内容无关紧要，因此 read 函数只是从存储中原样返回一个字符串，而 write 函数则在不更改或处理的情况下将其写入存储。在此示例中，open 函数相当于 MySQL SELECT，而 write 函数是 INSERT / UPDATE 查询。

destroy 函数仅在手动使用 session_destroy() 销毁会话时使用。销毁会话仅会删除与其关联的所有数据。它不会使会话 ID 或 cookie 失效。在本章后面的身份验证系统中，还需要取消设置会话 cookie。

旧会话需要定期从系统中清除。这就是垃圾回收的工作。请注意，它与你在第 8 章看到的不是同一个。它定期执行只是为了清理旧会话。收集器被执行的概率是 php.ini 变量 session.gc_maxlifetime、session.gc_probability 和 session.gc_divisor 的函数。当垃圾收集器执行时，它会采用会话的最大生命周期，并预期删除所有超过该生命周期的会话。默认值为 24 分钟（或 1440 秒）。

> 如果超时不是一个键，则删除旧会话可能是一项昂贵的操作，尤其是在你有数百万个会话时。然而，将该值设为键也有其自身的问题，主要是所有键必须是唯一的。本章中的表设计使用时间戳和会话 ID 的复合键，以避免在多个用户在同一秒登录时发生冲突的情况。

第 3 章详细介绍了回调函数。此会话类使用回调函数引用单例会话类中的会话处理方法。基本会话类如下所示，如清单 12-2 所示：

### 清单 12-2：CustomSession.class.php

```
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

在之前的代码中有几件重要的事情需要注意。最不明显的是，会话以序列化字符串的形式存储。回顾第 1 章，序列化字符串可能包含二进制字符，即使数据本身不是二进制的。此外，会话数据本身也可能是二进制的。因此，绝对不要在会话数据字符串上使用非二进制安全函数非常重要。这也是会话数据的数据类型为 blob 的原因。使用 blob 意味着你无法有效地查询会话数据（反正此类也不这样做），但它获得了对二进制数据的高效存储。

自 PHP 5.0.5 起，会话会在对象已被垃圾回收后自动写入并关闭。当使用对象作为会话处理器（如前述类所做的）时，这会导致问题。为了解决这个问题，类析构函数调用 `session_write_close()`，这会导致写入和关闭立即发生。虽然这在此类中不是一个因素，但同样的问题也会影响异常抛出，因为一旦所有对象都被清理，就不可能再创建新对象（而这对于异常处理是必要的）。

之前的数据库设计留出了与会话一起存储用户 ID 的空间。通过将用户 ID 与会话一起存储，应用程序可以确定当前处于活跃状态的用户。由于会话会过期，可以安全地假设会话表中任何有行的用户最近已查看了网站上的页面。然而，这需要会话类了解会话的内容。这种行为在大多数应用程序中是可以接受的，但如果会话类可以在通用情况下使用，则并不理想。

会话确实会过期。因此不应使用它们来存储无法稍后重建的数据。仅凭会话不足以确定用户的登录状态。它可以包含诸如计算和缓存数据之类的信息。例如，如果电子商务网站的用户将电脑无人看管 1440 秒就丢失购物车，那是不希望的。一个或多个额外的 cookie 可以传递用户登录凭据和其他信息（如购物车）。

## 构建安全 Cookie

用户登录凭据绝不应以明文形式存储在应用程序中，攻击者可以轻松读取或复制。登录 cookie 就像一把钥匙，可以打开网页的所有功能并访问可能敏感的用户数据。本节概述了一个系统，你可以用它来创建防黑客和防劫持的 cookie。为此，cookie 必须存储一些基本信息：

- 用户 ID
- 用户上次已知的 IP 地址
- 一个时间戳

第一个字段不言自明。它是用来识别哪个用户已登录的。第二两个字段是为了增加一点额外安全性。

上次已知的 IP 地址用于与当前向服务器发出请求的 IP 地址进行比较。它也可以与会话表中的 IP 地址字段进行比较。如果 cookie 中的 IP 地址与远程客户端的 IP 地址不匹配，则 cookie 可能已被劫持。也有可能是用户只是使用笔记本电脑在不同 WiFi 接入点之间房间间行走。

时间戳是 cookie 创建的日期和时间。这具有双重用途。第一个是确定用户已登录多长时间。极长的登录时间可能意味着用户已将电脑无人看管。在这方面，时间戳就像基于时间的 nonce。时间戳的第二个用途是确保在登录时生成的 cookie 从不完全相同。例如，如果用户在中午登录一次，又在 3:00 登录一次，则 cookie
