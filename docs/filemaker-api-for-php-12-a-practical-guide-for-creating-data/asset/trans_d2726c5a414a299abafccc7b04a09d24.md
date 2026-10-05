
如果出现问题，提供 OEM 技术支持。如果任何部分损坏，你可能需要等待很长时间才能修复。

- 4. 使用 JDBC 驱动只是又增加了一层需要处理的技术。
- 5. JDBC 驱动的速度没有 PHP 的 FileMaker API 快。
- 6. 如果你不使用 OS X Server，必须安装并配置 Tomcat。

# IWP

即时网络发布（Instant Web Publishing）是一项很的技术，作为 FileMaker Server Advanced 的一部分提供。你只需要创建数据库和布局，剩下的工作由 FileMaker Server Advanced 处理。然而，请记住，它并不是真正的自定义网页发布，非常适用于非常特定的场景。它并不打算作为高流量网站的日常解决方案。它的目的是复制 FileMaker Pro 客户端，如果没有经过训练，这对于访问你网站的外部用户来说可能会令人困惑。

- 服务器操作系统：Windows 或 OS X
- Web 服务器：IIS 或 Apache
- 应用服务器：无（从技术上，FileMaker Server Advanced 会安装 Tomcat）
- 驱动程序：无

优点：

- 1. 无需创建网页。FileMaker Server Advanced 会动态生成网页。
- 2. 脚本按预期运行，除了少数不兼容的脚本步骤外。
- 3. 用户交互与 FileMaker Pro 客户端非常相似。
- 4. 安全性按预期运行。
- 5. 可以在 Windows 或 OS X 上运行。
- 6. 不需要特殊的驱动程序。在安装 FileMaker Server 时只需选择你将使用的 Web 服务器，即可“开箱即用”。

缺点：

- 1. 限制 100 个并发用户，包括自定义网页发布连接。
- 2. 对于大型复杂系统，速度较慢。
- 3. 通常需要对 FileMaker Pro 和 IWP 客户端进行仔细的脚本编写。
- 4. FileMaker Server Advanced 非常昂贵——3000 美元。
- 5. 没有 SSL 能力。

# 成本

互联网在我们的生活中已经无处不在，以至于每个人认为它是免费的。我有一个坏消息要告诉你：互联网一点也不免费，创建和托管网站的费用比第一次要贵得多。请记住，10 年前的成本是现在的 10 倍，因为硬件和带宽非常昂贵。然而，从今天，自己完成一切并托管自己的服务器的初始成本，与支付顾问和托管商的长期成本相比，很快就能回本。以下是你可以预期支付的合理价格列表。

| 项目 | 成本 |
|---|---|
| FileMaker Server | $1000 |
| FileMaker Advanced | $499 |
| Adobe Dreamweaver | $399 |
| Adobe Fireworks | $299 |
| OSX Server (Mac, Xserve) | $999 - $3000 |
| Dell (Windows) Server (2008 SP 2 标准版) | $2000 - $5000 + CALS |
| Apache/IIS | 免费 |
| PHP | 免费 |
| 网络连接 (上传 Mbps: 0.768, 1, 2) | $120/月, $200/月, $300/月 |
| 静态 IP 地址 | $15/月 |
| FileMaker Host (4GB 数据传输, 1GB 存储, 8 个文件) | $250/月+ |

构建你的网站需要 FileMaker Server 和 FileMaker Pro。FileMaker Server 将托管你的数据库。只有在使用 ODBC/JDBC 或 IWP 时才需要 FileMaker Advanced。构建数据库时 FileMaker Advanced 是必要的。虽然你可以通过 FileMaker Pro 获得它，但调试和查看工具会使开发工作变得高效得多，这笔额外费用是值得的。

Adobe：虽然你可以使用书中前面描述的免费文本编辑器之一，但 Dreamweaver 的效率远高于其成本。如果你是从零开始创建网站，你还需要图像创建和编辑软件。Fireworks 专为网站设计。在处理网站时，我实际上更倾向于使用它而不是 Photoshop 和 Illustrator。

OSX Server：如果你要托管自己的网站，你需要购买一台服务器。如今的 OSX Server 相对便宜。你实际的限制因素是带宽，而不是硬件容量或性能。几乎任何廉价的服务器都会有足够的动力来支持你的网站。如果你想结账，实际上可以使用 Mac Mini。为了与 iOS Server 完美匹配，Mac Mini 起始价为 599 美元。第一年的费用将是 199 美元。如果你想设置得复杂一点，可以花 999 美元安装带有 OSX Server。由于服务器仅用于托管网站，OSX Server 的表现会比基于 Linux 的服务器更好。应用程序：Mac Mini 的唯一缺点是它不是服务器级硬件。除非你有 RAID 5 或 6，否则它并非设计为 24/7 运行。然而，你可以获得双处理器和 8GB RAM，这对于大多数网站来说动力绰有余。在我看来，服务器的寿命是 3 年。那么为什么不花 1/3 的费用，并在坏掉时将其扔掉呢？实际上，Mac Mini 只能运行几年。如果你真的需要超越 Mac Pro 的动力，你完全可以选择 Mac Pro。双网卡、12 核心、64GB RAM、8TB 存储。这样你不需要为 OSX 或 Windows 的 CALS 支付高价。

Windows 服务器：如果你只需要一个网站，你可能可以使用 Windows 服务器。无论你使用什么操作系统，FileMaker Server 都不在，但你可能需要 CALS。对于每个访问网站的用户，购买 Windows 2008 R2 标准版 ($2000 - $5000 + CALS) 可能会更贵一些。相比之下，OSX Server 大约只需要花费 1000 美元。

Apache/IIS：如果你只需要一个网站，你可能可以使用 Apache 或 IIS。无论你使用什么操作系统，FileMaker Server 都不在，但你可能需要 CALS。对于每个访问网站的用户，购买 Windows 2008 R2 标准版 ($2000 - $5000 + CALS) 可能会更贵一些。
