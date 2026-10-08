

```php
print(urldecode("mail leon@clearink.com"));
?>
```

# string urlencode(string url_text)

urlencode 函数将 `url_text` 转换为 URL 格式。该格式使用百分号 (%) 按照其 ASCII 代码来指定字符。此函数不安全用于二进制数据。

```php
<?php print(urldecode("mail leon@clearink.com"));
?>
```

# 加密

加密是将信息转换为不可读状态的过程。某些算法简单地打乱文本；而其他算法则允许反该过程。PHP 提供了 C 语言 `crypt` 函数的封装，该扩展是对 mcrypt 库的封装。

mcrypt 函数依赖于 Nikos Mavroyanopoulos 编写的同名库，该库提供了一个高级的数据加密系统。该项目的 URI 为 <ftp://argaes-cs-net.gr/pub/unix/mcrypt/>。Sascha Schumann 为 PHP 添加了 mcrypt 功能。

密码学是一个超出本文范围的话题。本节讨论的一些概念需要熟悉密码学理论。学习密码学的绝极地方是 crypt Usenet 新闻组的 FAQ 文件。其 URI 为 <http://www.faqs/orgs/cryptography-faq/>。另一个资源是 Prentice Hall 出版的 William Stallings 编写的《Cryptography and Network Security: Principles and Practice》。PHP 手册建议阅读 Bruce Schneider 的《Applied Cryptography》。

# string crypt(string text, string salt)

crypt 函数使用 C 语言的 crypt 函数对字符串进行加密，该函数通常使用 DES 加密，但取决于你的操作系统。返回加密后的参数。salt 是可选的。如果未提供，PHP 将创建一个随机盐值。你可能希望阅读关于 crypt 的页面以获得更好的理解。

请注意，使用 crypt 函数加密的数据无法解密。该函数通常用于加密密码，以便在需要授权时保存。此时，会要求密码，对其进行加密，并与之前加密的密码进行比较。

取决于你的操作系统，可能会有 DES 加密的替代方案。salt 参数用于确定使用哪种算法。两个字符的盐用于 DES 加密。九字符的盐指定扩展 DES。十二字符的盐指定 MD5 加密。十六个字符的盐指定 blowfish 算法。

在编译 PHP 时，会包含可用算法。以下常量将持有 TRUE 或 FALSE 值，你可以使用它们来确定四种算法的可用性：CRYPT_STD_DES, CRYPT_EXT_DES, CRYPT_MD5, CRYPT_BLOWFISH。

```php
$password = "secret";

if (CRYPT_MD5) {
    $salt = "leonatkinson";
    print("Using MD5: ");
}
```

# string mcrypt_create_iv(integer size, integer source)

使用 mcrypt_create_iv 创建初始化向量。size 应该匹配加密算法，并应使用 mcrypt_get_block_size 设置。source 参数可以是三个常量之一。CRYPT_DEV_RANDOM 使用来自 /dev/random 的随机数。CRYPT_DEV_URANDOM 使用来自 /dev/urandom 的随机数。CRYPT_RAND 使用 rand 函数的随机数，你可能需要用 srand 对其进行种子。

# string mcrypt_cbc(integer algorithm, string key, string data, integer mode, string initialization_vector)

mcrypt_cbc 函数使用密文块链接（CBC）对字符串进行加密。这种方法最适合加密整个文件。algorithm 参数是表 9.8 中列出的常量之一。mode 参数可以是 MCRYPT_DECRYPT 或 MCRYPT_ENCRYPT。初始化向量是可选的。记住，如果你使用它加密，必须使用相同的进行解密。

```php
<?php
// 设置测试数据
$message = "This message is sensitive";
$key = "secret";

// 加密消息
$code = mcrypt_cbc(MCRYPT_BLOWFISH_128, $key, $message, MCRYPT_ENCRYPT, $iv);

// 解密消息
print(mcrypt_cbc(MCRYPT_BLOWFISH_128, $key, $code, MCRYPT_DECRYPT, $iv));
?>
```

# mcrypt_cf(integer algorithm, string key, string data, integer mode, string initialization_vector)

mcrypt_cf 函数使用密文反馈（CF）对字符串进行加密。然而，在本文期间，PHP 的 mcrypt 接口不支持流加密器。algorithm 参数是表 9.8 中列出的常量之一。mode 参数可以是 MCRYPT_DECRYPT 或 MCRYPT_ENCRYPT。需要初始化向量。你必须使用相同的进行解密。

# mcrypt_ecb(integer algorithm, string key, string data, integer mode)

mcrypt_ecb 函数使用电子密码本（ECB）方法对字符串进行加密，它适用于短不规则数据的加密。algorithm 参数是表 9.8 中列出的常量之一。mode 参数可以是 MCRYPT_DECRYPT 或 MCRYPT_ENCRYPT。

```php
<?php
// 设置测试数据
$message = "This message is sensitive";
$key = "secret";

// 加密消息
$code = mcrypt_ecb(MCRYPT_BLOWFISH_128, $key, $message, MCRYPT_ENCRYPT);

// 打印解密消息
print(mcrypt_ecb(MCRYPT_BLOWFISH_128, $key, $code, MCRYPT_DECRYPT));
?>
```

# integer mcrypt_get_block_size(integer algorithm)

使用 mcrypt_get_block_size Find给定加密算法的块大小。使用表 9.8 中列出的常量之一。参见 mcrypt_get_cipher_name 的用法示例。

# string mcrypt_get_cipher_name(integer algorithm)

使用 mcrypt_get_cipher_name 获取加密算法名称。使用表 9.8 中列出的常量之一。

```php
<?php
// 创建加密算法数组
$algorithm = array(
    MCRYPT_3DES, MCRYPT_3WAY, MCRYPT_BLOWFISH_128, MCRYPT_BLOWFISH_192,
    MCRYPT_BLOWFISH_256, MCRYPT_BLOWFISH_448, MCRYPT_CAST_128, MCRYPT_CAST_256,
    MCRYPT_DES, MCRYPT_GOST, MCRYPT_IDEA, MCRYPT_LOKI97,
    MCRYPT_RC2_1024, MCRYPT_RC2_128, MCRYPT_RC2_256, MCRYPT_RC4, MCRYPT_RC6_128,
    MCRYPT_RC6_192, MCRYPT_RC6_256, MCRYPT_RIJNDAEL_128, MCRYPT_RIJNDAEL_192,
    MCRYPT_RIJNDAEL_256, MCRYPT_SAFERPLUS, MCRYPT_SAFER_128, MCRYPT_SERPENT_128,
    MCRYPT_SERPENT_192, MCRYPT_SERPENT_256, MCRYPT_TWOFISH_128,
    MCRYPT_TWOFISH_192, MCRYPT_TWOFISH_256, MCRYPT_XTEA
);

foreach ($algorithm as $value) {
    if ($value) {
        echo mcrypt_get_cipher_name($value) . ": " . mcrypt_get_block_size($value) . " bytes\n";
    }
}
?>
```

# PHP 核心编程

