

## 破解多因素身份认证

### Google Authenticator 漏洞

Google Authenticator 基于时间的一次性密码（TOTP）应用在第 9 章“一次性密码攻击”中得到了详细介绍。在该章中，任何 OTP 的密钥种子（secret seed values）都需要经过严格保护。如果攻击者能够获取这些值，他们就可以生成额外的未经授权实例，并使用它们伪装成合法用户进行响应。

为了在你的设备上实现并使用 Google Authenticator，管理员必须在配置为目标网站身份提供者的服务器上安装并配置 Google Authenticator 软件。Google Authenticator 是通过在 Linux 主机上安装可插件认证模块（PAM） `pam_google_authenticator.so` 来实现的。安装过程会创建一个包含生成代码设置的密钥文件，该文件必须防止未经授权的用户访问。

2012 年，人们发现该密钥文件的权限过大，在这种情况下，所有用户均可读取。Google Authenticator PAM 的操作被更改，以以更严格的权限运行并提升用户访问权限（即 sudo）。欲了解更多信息，请访问 www.openwall.com/lists/oss-security/2013/04/18/10 和 .cvedetails.com/cve/CVE-2012-6140。

2013 年发现了第二个 Google MFA 绕过漏洞（www.cvedetails.com/cve/CVE-2013-0258）。如果用户的账户启用了 Google Authenticator，但其令牌（token）未与账户关联，任何人都可以仅使用用户名登录该账户（无需密码）。详情见此处：www.drupal.org/node/1903282。

### YubiKey 漏洞

YubiKey 制造了互联网上最受喜的一些 MFA 设备和令牌。数百万用户在使用它们，它们可能是历史上第二受欢迎的 MFA 解决方案（仅次于 RSA）。2018 年，一名研究人员在在 Yubico 软件的多个版本中发现了多个漏洞，这些漏洞允许任何了解如何制作自定义 MFA 设备的人，能够成功绕过安装了该软件设备上的 YubiKey 身份验证检查。攻击者可以插入他们的自定义设备，他们会立即登录，就像他们成功提交了合法的 YubiKey 设备一样。这是由于缓冲区溢出漏洞导致的。详情见此处：www.yubico.com/support/security-advisories/ysa-2018-3/。2017 年发现了一种针对 Yubico 设备的更广泛的利用漏洞，被称为 ROCA，并在稍后对其了讨论。

### 多个 RSA 漏洞

RSA Security, Inc. 成立于 1982 年，其历史比大多数其他安全厂商都要长。他们是公钥加密和 MFA 身份认证的最早实施者。几十年来 RSA 非常流行，如果你看到一个 MFA 解决方案，通常是 RSA 令牌（RSA SecurIDs）或 RSA 软件。

## 第 15 章 有缺陷软件（第 319 页）

因此，RSA 的漏洞数量高于它的大多数竞争对手这并不意外。CVE 显示自 1999 年以来有 79 个不同的 RSA 漏洞（www.cvedetails.com/vendor/334/RSA.html）。至少有九个安全绕过漏洞（www.cvedetails.com/vulnerability-list/vendor_id-334/obyp-1/RSA.html）。许多 MFA 解决方案也存在其中，包括这一个：www.cvedetails.com/CVE-2010-3321。通过这一特定漏洞，拥有授权访问不安全的 SecID 令牌的人可以将设备的私钥导出。智能卡和 SecID 令牌上的私钥本应受到保护以防止从设备中导出。如果有人可以导出它，他们本质上就可以复制设备及其身份验证方式。RSA Security 据称还参与了最大的种子值盗窃案之一，正如第 9 章讨论的那样。

### SafeNet 漏洞

几十年来，我一直是 PKI 领域的专家。在那个领域，安全存储用于证书证书机构（CA）和其他关键 PKI 设备的 PKI 密钥的最受信任的三家公司是：SafeNet 和 Gemalto（后者在 2010 年曾是一次大规模 SIM 卡攻击的目标，已在第 8 章“SMS 攻击”中介绍）。现在，所有品牌都由同一公司 Thales（www.thalesgroup.com）拥有。

Thales 的发音为 "Talice"，类似于 malice 或 Alice，但首字母是 t。

2016 年，SafeNet 宣布了 10 个处理权限过大的独立 CVE（labs.nettitude.com/wp-content/uploads/2016/03/160125-1-Gemalto-IDSS-Security-SAS-Privilege-Escalation.pdf）。特别是，微软 Windows 的身份验证用户（Authenticated Users）对 SafeNet 关键文件具有完全控制（Full Control）权限。这将允许受影响系统的任何身份验证用户查看机密身份验证信息，并能够恶意修改 SafeNet 文件。

### Login.gov

Login.gov (login.gov) 是一个允许“安全且隐私地在线访问参与的政府计划”的网站。数千万美国人通过它访问公共政府资源。2017 年，一名黑客报告了使用 MFA 绕过漏洞（hackrone.com/reports/264090）。他能够启动注册过程，然后他们向他发送了一封确认邮件。该网站要求用户点击链接确认注册，并告诉他只有 24 小时时间完成。然后他注意到这并不需要这样做。

## 破解多因素身份认证

### ROCA 漏洞

一家名为 Infineon 的公司创建名为 RSAlib 的加密库。它被实现在数百台设备的软件和硬件中。2017 年，RSA 生成的密钥（512 位到 2048 位）存在一个严重漏洞——如果你可以访问公钥（理论上世界上任何人都可以访问），你就可以立即确定私钥。这是一件如此大的事情，以至于尽管被研究人员在 2017 年 2 月发现，但直到 2017 年 10 月才公开。其间时间被用于调用漏洞并制作补丁。在公开宣布几周前，我曾听过一些相关的迹象，但我个人认识的人没有人知道其严重性。这是关于厂商员工的一个被保守得很好、但某种程度上选择性为人知的秘密。在某个实例中，漏洞一旦公开，数百万设备（例如带有 TPM 芯片的 Windows 电脑）被宣布为可被利用。我们在当时工作的微软公司召开了紧急会议，讨论我们需要做什么。结果确定，受影响的微软智能卡需要更换。随后，微软公司内部进行了数十万个设备和软件的更新。

数百万台设备必须进行升级。受影响的智能卡需要更换。今天我之所以还在做这些，是因为我经常遇到那些销售智能卡的人以及那些 MFA 管理员，他们最近经常有受影响的设备，却从未听说过 ROCA。早期我们估计，如果数百万个受影响设备和非对称密钥从未被修复，后果严重。两年后，大多数漏洞密钥现在可能已经过期（非对称密钥平均寿命只有 1 到 2 年）。但毫无疑问，某些寿命较长的密钥仍在世界范围内使用。欲了解更多信息，请查看以下网站：

- en.wikipedia.org/wiki/ROCA_vulnerability
- crocs.fi.muni.cz/media/public/nemec_roca_ccs17_preprint.pdf
- theernews.com/2017/10/rsa-encryption-keys
- arastechnica.com/information-technology/2017/10/crippling-crypto-weakness-opens-millions-of-smartcards-to-cloning/

