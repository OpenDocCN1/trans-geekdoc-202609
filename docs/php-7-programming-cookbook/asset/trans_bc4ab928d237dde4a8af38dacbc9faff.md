

## 13
### 最佳实践、测试与调试

在本章中，我们将涵盖以下主题：

- 使用特质（Traits）和接口（Interfaces）
- 通用异常处理器
- 通用错误处理器
- 编写简单的测试
- 编写测试套件
- 生成伪造的测试数据
- 使用 `session_start` 参数自定义会话

### 引言

在本章中，我们将展示特质和接口是如何协同工作的。然后，我们将关注一种回退机制的设计，该机制将在你无法（或忘记）定义特定的 `try/catch` 块的情况下捕获错误和异常。接着，我们将进入单元测试的世界，首先向你展示如何编写简单的测试，然后如何将这些测试组合成测试套件。接下来，我们将定义一个类，让你可以创建任意数量的通用测试数据。最后，我们将讨论如何利用新的 PHP 7 功能轻松管理会话。

| 模式 | 全称 | 备注 |
|---|---|---|
| OFB | 输出反馈（Output Feedback） | 非常对称：加密和解密是相同的；完全不支持并行化 |
| CTR | 计数器（Counter） | 操作类似于 OFB；支持加密和解密的并行化 |
| CCM | 带有 CBC-MAC 的计数器（Counter with CBC-MAC） | CTR 的衍生模式；仅设计用于 128 位的块长度；提供认证和保密性；**CBC-MAC** 代表 **分组密码链接 - 消息认证码（Cipher Block Chaining - Message Authentication Code）** |
| GCM | 伽罗瓦/计数器模式（Galois/Counter Mode） | 基于 CTR 模式；每个待加密的数据流应使用不同的 IV（初始化向量）；吞吐量极高（与其他模式相比）；支持加密和解密的并行化 |
| XTS | 基于 XEX 的调整码本分组密码模式（带有密文窃取）（XEX-based Tweaked-codebook mode with ciphertext Stealing） | 相对较新（2010 年）且快速；使用两个密钥；增加了可以作为单个块安全加密的数据量 |

5. 在选择加密方法和模式之前，你还需要确定加密内容是否需要在你的 PHP 应用外部进行解密。例如，如果你将数据库凭据加密并存储到独立的文本文件中，你是否需要能够从命令行解密它们？如果需要，请确保你选择的加密方法和操作模式在目标操作系统上得到支持。

6. 为 **IV** 提供的字节数根据所选的加密方法而异。为了获得最佳结果，请使用 `random_bytes()`（PHP 7 中新引入），它会返回一个真正的 **CSPRNG**（密码学安全伪随机数生成器）字节序列。IV 的长度变化很大。建议从 16 字节大小开始尝试。如果生成了 `警告`，将会显示该算法应提供的正确字节数，因此请相应地调整大小：

```php
$iv = random_bytes(16);
```

7. 要执行加密，请使用 `openssl_encrypt()`。以下是应传递的参数：

| 参数 | 备注 |
| :--- | :--- |
| Data | 需要加密的明文。 |
| Method | 使用 `openssl_get_cipher_methods()` 识别的方法之一。标识格式如下：`method_key_size-cipher_mode`。因此，例如，如果你想要 AES 方法，256 的密钥大小，以及 GCM 模式，你会输入 `aes-256-gcm`。 |
| Password | 虽然文档中注明为 *密码*，但可以将此参数视为 *密钥*。使用 `random_bytes()` 生成一个密钥，其字节数应与所需的密钥大小匹配。 |
| Options | 在你对 openssl 加密有更多经验之前，建议坚持使用默认值 0。 |
| IV | 使用 `random_bytes()` 生成一个 IV，其字节数应与加密方法匹配。 |

8. 作为示例，假设你希望选择 AES 加密方法，256 的密钥大小，以及 XTS 模式。以下是用于加密的代码：

```php
$plainText = 'Super Secret Credentials';
$key = random_bytes(16);
$method = 'aes-256-xts';
$cipherText = openssl_encrypt($plainText, $method, $key, 0, $iv);
```

9. 要解密，请使用相同的 `$key` 和 `$iv` 值，并结合 `openssl_decrypt()` 函数：

```php
$plainText = openssl_decrypt($cipherText, $method, $key, 0, $iv);
```

## 工作原理...

为了查看哪些加密方法可用，请创建一个名为 `chap_12_openssl_encryption.php` 的 PHP 脚本并运行此命令：

```php
<?php
  echo implode(',', openssl_get_cipher_methods());
```

输出应该看起来像这样：

![](img/39390f6d56c5a83b28db083a8bd5185c_501_0.png)

接下来，你可以添加待加密的明文、方法、密钥和 IV 的值。作为示例，尝试使用 AES，密钥大小为 256，使用 XTS 操作模式：

```php
$plainText = 'Super Secret Credentials';
$method = 'aes-256-xts';
$key = random_bytes(16);
$iv = random_bytes(16);
```

要加密，你可以使用 `openssl_encrypt()`，指定之前配置的参数：

```php
$cipherText = openssl_encrypt($plainText, $method, $key, 0, $iv);
```

你可能还希望对结果进行 base64 编码，使其更具可用性：

```php
$cipherText = base64_encode($cipherText);
```

要解密，请使用相同的 `$key` 和 `$iv` 值。别忘了先解码 base64 值：

```php
$plainText = openssl_decrypt(base64_decode($cipherText), $method, $key, 0, $iv);
```

以下是显示 base64 编码的密文，随后是解密后的明文的输出：

```text
Terminal
ENCODED:
BEER2t/v0MvKaO0VlLJBV3pZNFE2OvyI53FTiMGrek==

DECODED:
Super Secret Credentials

---------------------
<program exited with code: 0>
Press return to continue
```

如果你为所选加密方法提供了错误数量的 IV 字节，将会显示一条警告消息：

```text
Terminal
Warning: openssl_encrypt(): IV passed is only 12 bytes long, cipher expects an IV of precisely 16 bytes, padding with \0 in /home/d/Desktop/repos/php7_recipes/source/chapter12/chap_12_openssl_encryption.php on line 10
ENCODED:
aTGdZG1kSG9SQNrUmx1d2k1zOQwjhGUHziH09cVXK=

Warning: openssl_decrypt(): IV passed is only 12 bytes long, cipher expects an IV of precisely 16 bytes, padding with \0 in /home/d/Desktop/repos/php7_recipes/source/chapter12/chap_12_openssl_encryption.php on line 16
DECODED:
Super Secret Credentials

---------------------
<program exited with code: 0>
Press return to continue
```

## 更多参考...

在 PHP 7 中，使用 `openssl_encrypt()` 和 `openssl_decrypt()` 时存在问题，所支持的 **认证加密（Authenticated Encrypt with Associated Data，AEAD）** 模式为：GCM 和 CCM。相应地，在 PHP 7.1 中，这些函数增加了三个额外参数，如下所示：

| 参数 | 描述 |
|---|---|
| `$tag` | 通过引用传递的认证标签；如果认证失败，变量值保持不变 |
| `$aad` | 附加认证数据 |
| `$tag_length` | 对于 GCM 模式为 4 到 16；对于 CCM 模式没有限制；仅用于 `openssl_encrypt()` |

有关更多信息，你可以参考 `https://wiki.php.net/rfc/openssl_aead`。

## 另请参阅

关于为什么 mcrypt 扩展在 PHP 7.1 中被弃用的出色讨论，请参阅 https://wiki.php.net/rfc/mcrypt-viking-funeral 上的文章。关于块加密的良好描述，它构成了各种加密方法的基础，请参阅 https://en.wikipedia.org/wiki/Block_cipher 上的文章。关于 AES 的出色描述，请参阅 https://en.wikipedia.org/wiki/Advanced_Encryption_Standard。描述加密操作模式的好文章可以在 https://en.wikipedia.org/wiki/Block_cipher_mode_of_operation 上看到。

![](img/39390f6d56c5a83b28db083a8bd5185c_503_0.png)

对于一些较新的模式，如果要加密的数据小于块大小，`openssl_decrypt()` 将不返回任何值。如果你将数据填充到至少等于块大小，问题就会消失。大多数模式都实现了内部填充，因此这不是一个问题。在一些较新的模式（即 xts）中，你可能会看到这个问题。在将代码投入生产之前，务必对短于八个字符的数据短字符串进行测试。

