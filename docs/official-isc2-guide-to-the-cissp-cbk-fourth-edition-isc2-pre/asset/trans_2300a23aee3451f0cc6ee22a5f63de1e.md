
客户端 SSL 证书或 S/MIME 证书可用于此目的。

当用户在支持表单签名的基于 Web 的表单上单击“Submit”按钮时，会出现一个对话框，显示要签名的确切文本。表单设计者可以指定应使用的证书，也可以允许用户从安装在 Communicator 中的客户端 SSL 和 S/MIME 证书中选择证书。当用户单击 OK 时，文本将被签名，并且文本和数字签名都提交到服务器。然后服务器可以使用名为 Signature Verification Tool 的 Red Hat 实用程序来验证数字签名。

## 单点登录

网络用户经常需要记住用于各种服务的多个密码。例如，用户可能需要输入不同的密码来登录网络、收取电子邮件、使用目录服务以及访问各种服务器。多个密码对用户、系统管理员和安全专业人员来说都是持续的困扰。用户难以跟踪不同的密码，倾向于选择较差的密码，并且倾向于将密码写在明显的地方。管理员和安全专业人员必须在每台服务器上跟踪单独的密码数据库，并处理与密码经常在网络上传输相关的潜在安全问题。

解决此问题需要一种方式让用户一次登录，使用单个密码，并获得对用户有权使用的所有网络资源的经过身份验证的访问，而无需在网络上传输任何密码。这种功能称为单点登录。

客户端 SSL 证书和 S/MIME 证书在全面的单点登录解决方案中可以发挥重要作用。用户只需使用单个密码登录本地客户端的私钥数据库，即可获得对用户有权使用的所有 SSL 启用服务器的经过身份验证的访问，而无需在网络上传输任何密码。这种方法简化了用户的访问，因为他们无需为每个新服务器输入密码。它还简化了网络管理，因为管理员可以通过控制证书颁发机构（CAs）列表而不是更长的用户和密码列表来控制访问。

除了使用证书之外，完整的单点登录解决方案还必须解决与依赖密码或其他形式身份验证的企业系统，例如底层操作系统互操作的需要。

## 对象签名

对象签名使用公钥加密的标准技术，让用户能够以与获取 shrink-wrapped 软件的可靠信息相同的方式，获取有关下载代码的可靠信息。

最重要的是，对象签名帮助用户和网络管理员实施有关通过内联网或互联网分发的软件的决策，例如是否允许特定实体签名的 Java 小程序在特定用户机器上使用特定的计算机功能。

使用对象签名技术签名的“对象”可以是小程序或其他 Java 代码、JavaScript 脚本、插件或任何类型的文件。“签名”是指数字签名。签名对象及其签名通常存储在称为 JAR 文件的特殊文件中。

希望使用对象签名技术签名文件的软件开发人员和其他人员必须首先获得对象签名证书。

## 证书内容

证书的内容是根据 X.509 v3 证书规范组织的，该规范自 1988 年以来一直被国际电信联盟（ITU），一个国际标准机构推荐。

用户通常不需要关心证书的确切内容。然而，处理证书的系统管理员和安全专业人员可能需要熟悉此处提供的信息。

## 区别名称

X.509 v3 证书将区别名称（DN）绑定到公钥。区别名称是一系列名称-值对，例如 uid=Sdog，它唯一标识一个实体，即证书主体。

例如，这可能是 (ISC)² 员工的一个典型 DN：

```
uid=Sdog, e=Sdog@isc2.org,cn=Snoopy Dog,o=ISC2,c=US
```

示例中每个等号之前的缩写含义如下：

- **用户 ID** — 用户 ID
- **电子邮件** — 电子邮件地址
- **通用名称** — 用户的通用名称
- **组织** — 组织
- **国家** — 国家

DNs 可能包含各种其他名称-值对。它们用于标识证书主体以及支持轻量级目录访问协议（LDAP）的目录中的条目。

构建 DN 的规则可能相当复杂，超出了本讨论的范围。有关 DN 的全面信息，请参阅以下 URL 上的“区别名称的字符串表示”：

http://www.ietf.org/rfc/rfc1485.txt

## 一个典型证书

每个 X.509 证书都由两个部分组成：

数据部分包括以下信息：

- 证书支持的 X.509 标准版本号。
- 证书的序列号。CA 发行的每张证书都有一个序列号，该序列号在其发行的证书中是唯一的。
- 有关用户公钥的信息，包括所使用的算法和密钥本身的表示。
- 发行证书的 CA 的 DN。
- 证书有效的期间（例如，从 2014 年 9 月 3 日晚上 10:00 点到 2016 年 9 月 3 日晚上 10:00 点）
- 证书主体的 DN（例如，在客户端 SSL 证书中，这将是用户的 DN），也称为主体名称。
- 可选的证书扩展，可能提供客户端或服务器使用的额外数据。例如，证书类型扩展指示证书的类型（它是客户端 SSL 证书、服务器 SSL 证书、用于签名电子邮件的证书等）。证书扩展也可用于各种其他目的。

**签名** 部分包括以下信息：

- 发行 CA 用于创建其自身数字签名的加密算法或密码。
- CA 的数字签名，通过对证书中的所有数据进行哈希处理并使用 CA 的私钥加密获得。

以下是证书的人类可读格式的数据和签名部分：

Certificate:
Data:
Version: v3 (0x2)
Serial Number: 3 (0x3)
Signature Algorithm: PKCS #1 MD5 With RSA Encryption
Issuer: OU=ABC123 Certificate Authority, O=ABC123, C=US
Validity:
Not Before: Friday Aug 18 18:36:25 2000
Not After: Sun Aug 18 18:36:25 2002
Subject: CN=Snoopy Dog, OU=Dog House, O=ABC123, C=US
Subject Public Key Info:
Algorithm: PKCS #1 RSA Encryption
Public Key:
Modulus:
00:ca:fa:79:98:8f:19:f8:d7:de:e4:49:80:48:e6:2a:2a:86:
ed:27:40:4d:86:b3:05:c0:01:bb:50:15:c9:de:dc:85:19:22:
43:7d:45:6d:71:4e:17:3d:f0:36:4b:5b:7f:a8:51:a3:a1:00:
98:ce:7f:47:50:2c:93:36:7c:01:6e:cb:89:06:41:72:b5:e9:
73:49:38:76:ef:b6:8f:ac:49:bb:63:0f:9b:ff:16:2a:e3:0e:
9d:3b:af:ce:9a:3e:48:65:de:96:61:d5:0a:11:2a:a2:80:b0:
7d:d8:99:cb:0c:99:34:c9:ab:25:06:a8:31:ad:8c:4b:aa:54:91:f4:15
Public Exponent: 65537 (0x10001)
Extensions:
Identifier: Certificate Type
Critical: no
Certified Usage:
SSL Client
Identifier: Authority Key Identifier
Critical: no
Key Identifier:
f2:f2:06:59:90:18:47:51:f5:89:33:5a:31:7a:e6:5c:fb:36:26:c9
Signature:
Algorithm: PKCS #1 MD5 With RSA Encryption
Signature:
6d:23:af:f3:d3:b6:7a:df:90:df:cd:7e:18:6c:01:69:8e:54:65:fc:06:
30:43:34:d1:63:1f:06:7d:c3:40:a8:2a:82:c1:a4:83:2a:fb:2e:8f:fb:
f0:6d:ff:75:a3:78:f7:52:47:46:62:97:1d:d9:c6:11:0a:02:a2:e0:cc:
2a:75:6c:8b:b6:9b:87:00:7d:7c:84:76:79:ba:f8:b4:d2:62:58:c3:c5:
b6:c1:43:ac:63:44:42:fd:af:c8:0f:2f:38:85:6d:d6:59:e8:41:42:a5:
4a:e5:26:38:ff:32:78:a1:38:f1:ed:dc:0d:31:d1:b0:6d:67:e9:46:a8:d:c4
Here is the same certificate displayed in the 64-byte-encoded form interpreted by software:
-----BEGIN CERTIFICATE-----
MIICKzCCAZSGaWIBAgIBAzANBgkqhkiG9w0BAQQFADA3MQswCQYDVQQGEwJVUzER
MA8GA1UEChMITmV0c2NhcGUxFTATBgNVBAsTDFN1cHJpeWEncyBDQTAeFw05NzEw
MTgwMTM2MjVaFw05OTE...
-----END CERTIFICATE-----
