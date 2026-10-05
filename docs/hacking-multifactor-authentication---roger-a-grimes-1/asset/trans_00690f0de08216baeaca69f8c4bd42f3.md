

## 保护 API 密钥

如果你有一个 API 密钥，请意识到它可能会被黑客窃取以访问你的账户和信息。API 密钥就是“钥匙”。请像对待钥匙一样对待它们。不要将其留在电子邮件或散落在你的硬盘上。相反，请对其进行加密，或者将其放置在密码管理器中（如果你在使用的话）。

## 总结

本章介绍了 API 滥用问题。我们首先探索了常见的 API 技术和标准，以帮助你更好地理解 MFA API。我们还讨论了一些 MFA API 破解的示例。本章通过列出开发者和用户针对 API 滥用的防御措施作为结束。

下一章将涵盖无法归入之前章节的杂类 MFA 攻击。

# 20 杂类 MFA 破解方法

本章将涵盖一些不属于之前类别、且在前面的章节中未讨论过的 MFA 解决方案破解方法。

### 亚马逊神秘设备绕过

这种奇怪的 MFA 绕过方法由一位美国的 Amazon 用户（www.reddit.com/r/sysadmin/comments/dpbt3t/the_perils_of_security_and-how_i_finally_resolved）于 2019 年 11 月报告。该 Amazon 用户醒来后发现他的 Amazon 账户被欺诈支付了几张 Amazon 礼品卡。这让他很惊讶，因为他不仅没有购买这些礼品卡，而且作为 IT 安全专业人士，使用 OTP 令牌保护了他的 Amazon 账户。Amazon 提供了不同的 OTP 选项（见图 20.1）：短信、语音电话和手机应用。

启用后，在登录 Amazon 用户账户期间（包括用户连接的任何设备）都需要输入 OTP 代码。此案例中的受害者本认为他的账户受到了充分保护，直到他发现了那些欺诈扣费。他尝试联系 Amazon 欺诈支持，遗憾地发现除了承诺 48 小时内回复的外外没有其他选项。于是，他启用了另一个 OTP，从他的 Amazon 账户中删除了信用卡信息，删除了所有活动会话，移除了所有允许设备，并更改了银行和信用卡密码。

在经过大量研究并与一位海外技术支持人员交谈后，他得知对方（可能位于亚洲）是从一台华为智能电视完成购买的。但他并没有华为电视。直到今天，他仍然不知道自己的 Amazon 凭据是如何被窃取的。他对两件事感到困惑：1) 当他开启 OTP 时，那个外国电视是如何连接到他的 Amazon 账户的；2) 为什么他在账户选项中允许设备时，没有在允许和已连接的设备列表中看到那台电视。他得知，不仅非 Amazon 设备（如智能电视、游戏机和 Roku 盒）不会出现在 Amazon 的账户设备列表中，大多数 Amazon 技术支持人员也无法看到它们。只有特定的 Amazon 高级技术支持人员才拥有查看外国设备的工具。

![](img/c78b0f79db62998ee317a35df5629d85_440_0.png)

Pro 20.1：亚马逊 OTP 选项

他还发现，即使你在你的 Amazon 账户上指定需要 OTP，任何现有的连接在断开或删除重新连接之前都不会被强制使用 OTP。最后，他的整个经历记录在这里：www.theregister.co.uk/2019/10/31/amazon_account_hacking。这提醒我们，即使你认为自己要求了 OTP 保护，事实也可能并非如此——你仍然可能被某些不需要使用 MFA 的攻击者利用账户入侵。

### 获取旧手机号

在第 8 章“短信攻击”中，你学习了 SIM 卡劫持攻击（SIM swapping attacks），攻击者获取合法订阅者的 SIM 信息并将其转移到他们持有的手机中。在类似的场景下，攻击者合法地获得了受害者的旧手机号，只需能够使用该旧号码就足以控制受害者的当前 MFA 解决方案。

在一个示例中，MFA 供应商 Authy（authy.com）允许 Authy 用户在其 MFA 解决方案中注册并使用多个设备（以及手机号码）。这允许任何知道 Authy 旧手机号（此前在 Authy 解决方案中使用过）的攻击者获取该号码，并使用短信访问用户账户（如果用户没有禁用 Authy 的多设备功能，该功能是默认开启的）。这一疏忽在 Coinbase 处达到了顶点，全球最大、最流行的加密货币交易网站 Coinbase 将 Authy 视为有效的 MFA 解决方案（www.reddit.com/r/Bitcoin/comments/6f0nhb/coinbase_recommendation_migrate_from_authy_to），并告诉所有使用 Authy 的客户改为使用 Google Authenticator。此外，一家外部安全研究公司发现了一个漏洞（bitcoin.com/authy-vulnerability-exposed-users-affected），攻击者可以获取 Authy 用于向 Authy 证明身份的个人信息。如果启用了多设备功能，攻击者可以使用这些信息注册新的欺诈或电话号码。

### 自动登录 MFA 绕过

Duo Security 发现（duo.com/blog/bypassing-googles-two-factor-authentication），安卓手机和 Chrome OS 可以通过在 Google 浏览器中启用自动登录标记来绕过 Google 2FA 限制。攻击者必须拥有与 Google 账户关联的手机或设备的本地或远程控制（这本身就是一个很大的障碍）。[注：原文此处存在大量重复句子，已根据翻译要求去重]

### 密码重置

攻击者必须拥有与 Google 账户关联的手机或设备的本地或远程控制（这本身就是一个很大的障碍）。

### 隐藏摄像头

许多 MFA 解决方案可以被攻击者通过隐藏摄像头获取。例如，密码设备可以被隐藏摄像头获取。

### 键盘监听

几十年来，我读过在实验室进行的研究，其中“攻击者”可以记录击键声。关于这一点有两项早期研究：www.davidsalon.name/CompSec/auxiliary/Kybdation.pdf 和 www.csnell.com/sshat/courses6431/zhuang.pdf。在其中论文中，作者描述了能够在10 分钟内恢复 96% 的击键。在另一项研究中，如果有人使用 spritz.math.upid.it/projects/dst，则会被监听。无线键盘和鼠标即使通信经过加密也可以被监听。你可以在这里阅读相关内容：

- thehackernews.com/2016/02/mouse-hack-computer.html
- www.computerworld.com/article/3101006/keysniffer-hackers-can-snag-wireless-key-board-keystrokes-from-250-foot-away
- blog.emisoft.com/en/12317/keysweeper-proof-that-is-relatively-simple-to-hack-a

### 密码提示

许多软件和手机 MFA 解决方案最终都由用户名和密码保护。一旦用户登录，用户就可以永久或在一段时间内继续使用该 MFA 解决方案。但逻辑上这意味着该解决方案的强度与用户名和密码绑定。这本身就是一个问题。但更糟糕的是，某些允许使用用户名和密码的 MFA 解决方案还允许用户存储并让其他人查看密码提示（见图 20.2 中的示例）。

