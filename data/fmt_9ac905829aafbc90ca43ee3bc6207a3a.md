
# OSINT 工具与技术指南

## 浏览器选择与使用习惯

关于选择用于 OSINT 的网页浏览器，我推荐使用 TOR、Brave 或 Firefox。我也建议在案件推进过程中使用不同的浏览器，这有助于防止他人窥探你的活动，即使你是一名正在办案的特工。另一个良好习惯是不断清除浏览历史、Cookie 等。请注意，首先要查看的内容是 `robots.txt` 文件。同时，尽量在十个或更多不同的搜索引擎上进行搜索，因为国内网站通常提供更贴近案件的信息。例如，如果你在查找法国人的信息，可以 VPN 连接巴黎，然后在 Google、MetaGer.org 以及其他搜索引擎上从该地点进行搜索，这将提高生产力和结果的效率。

## 地图工具替代方案

如果你更喜欢替代 Google Maps 的地图方案，可以尝试 OpenStreetMap.org、WikiMapia.org，甚至 Bing.com 和 Yahoo.com（请注意这些平台可能有其他平台没有的功能，多多尝试）。你可以尝试将自己 VPN 到特定位置，然后打开默认地图（如 WikiMapia），观察该位置的默认地图。当然，你也可以使用俄罗斯搜索引擎（对人类非常友好）Yandex.ru。如果使用 Yandex.ru，我建议先 VPN 连接到某个欧洲国家，然后再从那里使用该搜索引擎。

## 核心 OSINT 工具网站

其他值得关注的网站包括：

*   WhatsMyName.app
*   TraffickCam.com
*   [`tools.kali.org/information-gathering/recon-ng`](https://tools.kali.org)
    *   用于开展侦察
    *   使用 Python 编写
*   [`www.exploit-db.com/google-hacking-database`](https://www.exploit-db.com/google-hacking-database)

## Web 抓取法律提示

> [Web 抓取](https://www.example.org)是一种从网站上收集信息的方法，但请记住，**这在所有国家都是合法的**，所以如果你要在法庭上使用收集的数据，请不要进行非法操作，然后在法庭上展示证据。

## 社交媒体情报 (SOCMINT)

社交媒体情报收集被称为 SOCMINT。如果你是政府人员，你可以轻松为你的行动设置假社交媒体账户。你也可以在非政府情况下进行，但有时这会对你（法律上或其他方面）造成风险。请始终关注你的工作中的模式，无论你收集的是哪种情报。在调查中需要关注的关键社交媒体账户有：

*   Facebook（你会看到 50 岁以上的人群在这里聚集，当然还有其他年龄层）
*   Twitter
*   Snap Chat
*   TikTok
*   Instagram（年轻人喜欢在这里活跃）
*   LinkedIn（商务专业人士聚集在这里）
*   Pinterest（这里的用户主要是女性）

## 笔记与管理工具

一些用于管理、编辑和做笔记的优秀工具：

*   CherryTree
    *   [`www.giuspen.com/cherrytree/`](https://www.giuspen.com)
    *   [`cherrytree-for-windows.en.lo4d.com/windows`](https://cherrytree-for-windows.en.lo4d.com)
*   Notepad++
    *   [`notepad-plus-plus.org/`](https://notepad-plus-plus.org)
    *   可以在 Microsoft Windows 上运行

## 数据分析平台

一个对数据分析工作非常有用的工具是 Kaggle：

*   [`www.kaggle.com/`](https://www.kaggle.com)
*   包含超过 50,000 个公共数据集和 400,000 个公共笔记本

## 平台特定工具

### Snapchat
如果你想使用 Snapchat 的信息，可以使用以下网站查看全球 Snapchatters 的快照：
*   [`map.snapchat.com/`](https://map.snapchat.com)

### Twitter
对于 Twitter，可以尝试：
*   [`www.trendsMap.com/map`](https://www.trendsMap.com)
    *   还有专业版
*   [`oneMillionTweetMap.com`](https://oneMillionTweetMap.com)

## DNS 与网络侦察工具

如果你想研究以下内容，可以使用 [`viewDNS.com`](https://viewDNS.com) 和 [`ns.tools/`](https://ns.tools)：

*   DNS 查找（各种记录类型，如：A、NS、MX、TXT、CNAME 等）
*   反向 IP 查找
*   IP 地理定位
*   Traceroute
    *   注意，这本质上是沿着网络路径的一系列 ping
*   Ping IP
*   检查网站是否上线或下线
*   WhoIs 查找
*   还可以尝试 [`dnsdumpster.com/`](https://dnsdumpster.com)、[`mxtoolbox.com/`](https://mxtoolbox.com) 以及 [`securitytrails.com/`](https://securitytrails.com)
    *   SecurityTrails 自称：“为第三方风险、攻击面管理和总体情报提供强大的工具”
*   `inurl:ftp -inurl:(http|https) intext:"advocavySolutionsllc.com"`

### DNS 提供商排名
在 DNS 流行度方面，Cloudflare 排名第一。他们自称：“Cloudflare DNS 是一个面向企业级权威 DNS 服务的服务，提供最快的响应时间、无与伦比的冗余性以及先进的安全性，内置 DDoS 缓解和 DNSSEC。”

*   [`www.cloudflare.com/dns/`](https://www.cloudflare.com/dns/)
*   BlueHost.com
*   SiteGround.com
*   OpenDNS.com

## Discord 社区资源

*   [`discordservers.com/browse/OSINT`](https://discordservers.com)
    *   公开的 OSINT Discord 服务器
    *   如果你不知道这是什么，可以参考“Discord for Dummies”这本书，下面是 Discord 服务器的简要说明：
        *   “也许最初最难做的是定义 Discord。表面上它看起来和听起来像 Skype 的增强版，但实际上它是一个强大、稳定的通信平台，可作为浏览器应用、独立桌面应用和手机应用（适用于智能手机和平板电脑）使用。Discord 提供以下功能：
            *   文本聊天
            *   音频和视频聊天（群组和私人）
            *   私人文本消息
            *   新闻动态
            *   链接和媒体共享
            *   流媒体和屏幕共享
        *   Discord 为游戏玩家、直播者和许多其他创意个人和组织提供了一个涵盖所有主题的聊天流、私人音频频道和公开公开聊天、播客和直播采访等功能。
        *   Discord 的费用与推出时一样：免费。
        *   Discord 在稳定性、音质、视频质量和易用性方面与其他游戏通信解决方案不同，对于依赖互联网进行通信的专业人士来说，它更具优势。它可能在首次启动时看起来有点令人望而生畏，但设置和使用非常容易。”

## 企业情报来源

发现创新公司及其背后的人物：

*   CrunchBase.com
*   DNB.com
*   Bloomberg.com

Quad9 宣布在瑞士重新注册，以保证全球 DNS 用户的隐私。
*   Quad9.com

还需要记住的是，你可以通过像 glassdoor.com、USAjobs.com、IntelligenceCareers.gov、Indeed.com、LinkedIn.com、Monster.com、CareerBuilder.com、Dice.com 等网站了解公司的文化、使用的技术等。此外，搜索“公开文件”可以获取各种公开信息。

## 恶意文件分析

如果你发现看起来像是异常文件，并且想对其进行恶意内容分析，可以使用：
*   [`www.virusTotal.com`](https://www.virusTotal.com)

## 外部风险评估

如何对感兴趣的组织进行外部风险评估？

*   使用上述 DNS 工具查看其 DNS 状态
    *   同样，也要对其供应链中的供应商进行同样的检查
    *   需要警惕的一个应用是 TeamViewer。这是桌面共享和通信软件，可以在 [`www.teamviewer.com/en-us/download/windows/`](https://www.teamviewer.com) 下载。恶意行为者可以在使用该软件时，直接向你的计算机系统推送不想要的文件。如果你使用它，就像使用其他类似程序一样，在使用前请确保你的网络和系统已得到适当的安全保护。

## 执法联络

CyWatch 是 FBI 的 24/7 操作中心和警戒室，提供 24/7 支持以跟踪事件并与美国各地分局沟通：

*   [`www.fbi.gov/investigate/cyber`](https://www.fbi.gov/investigate/cyber)
*   855-292-3937 或 CyWatch@FBI.gov
*   SAR = Suspicious Activity Report

## Windows 7 支持状态

对于 Microsoft Windows 7，请记住，尽管它已达到 Microsoft 所称的“生命周期结束”，但如果你愿意支付费用，仍可获得 ESU（Extended Security Updates）和技术支持。这适用于 Windows 7 Professional 和 Enterprise 版本，费用按设备标准收取。即使这种支持也将在 2023 年 1 月有效期结束。

## 情报联盟组织

从情报界的角度来看，关键政府组织有：

### Five Eyes（5-Eyes）
Five Eyes（FVEY）是一个由（按字母顺序排列）澳大利亚、加拿大、新西兰、英国和美国组成的情报联盟。FVEY 是共同 UKUSA 协议的签约方，该协议是一项关于信号情报领域多边协作的条约。

### Nine Eyes（9-Eyes）
在全球情报界中，这个组织包括 FVEY 的成员国加上另外四个国家——丹麦、法国、荷兰和挪威。

### Fourteen Eyes（14-Eyes）
这是一个由 Nine Eyes 的成员国加上另外五个国家——比利时、德国、意大利、西班牙和瑞典——组成的联盟。

### 其他合作国家
## 其他与“十四眼”联合合作的情报机构国家包括英国海外领地、以色列、日本、新加坡（不像以前那样多）以及韩国（由于朝北对话加剧，现在不像以前那样多）

## 其他未公开组别
## 还有其他“类似”的组别，但相关信息并未公开披露

## VPN 选择建议

让我们用 PIA 代表 Private Internet Access。从 OSINT 角度看，NordVPN（总部位于巴拿马）不推荐，而 ProtonVPN（总部位于瑞士且拥有严格的数据隐私法）是一个推荐选项。正如前文所述，使用 VPN 能让你获得地区化的搜索结果，这对 OSINT 调查非常有利。为了安全起见，最好随时拥有多个 VPN，以防主 VPN 因各种原因失效。备用总是好的。使用多个 VPN 的另一个原因是，有些 VPN 能访问其他 VPN 无法访问的地区和网站。对于所有安全工具，如果你能负担得起，几乎总是更倾向于使用付费产品，因为“免费”产品往往有其原因，而这“免费”可能会让你在不知情的情况下付出代价，所以请保持警惕。优秀的搜索引擎包括 MetaGer.org、DuckDuckGo.com、Bing.com 和 Google.com（以及前文提到的其他引擎）。如果想了解如何渗透网络，可以参考 [`www.offensive-security.com/`](https://www.offensive-security.com) 以获取备受雇主青睐的认证。

## Google Dorks 示例

### 一些使用 Google Dorks 的示例：

*   在 Google 或 DuckDuckGo 的搜索框中输入：
    *   相关：`Alstom.com`
        *   – 通过此搜索可看到其他可能感兴趣的站点/页面
    *   `Site: lifewire.com filetype: html`
        *   – 查看 lifewire.com 上的 HTML 文件
    *   `Inurl:php -Boeing.com`
        *   – 查看 Boeing.com 上的 PHP 文件
    *   `Intext: "<wallet address>"`
    *   只需尝试这些以及其他 Google Dorks，以便熟悉它们

## 网络广告拦截

通过 pi-hole（[`pi-hole.net/`](https://pi-hole.net)）可以消除不想要的广告干扰工作。pi-hole 本质上是网络范围的广告阻断器。与其在每个设备/浏览器上安装广告拦截插件不同，你可以在网络上仅安装一次 pi-hole，随后它会自动保护所有浏览器/设备。pi-hole 相当于在网络内部充当私有 DNS 服务器。它会拦截所有针对已知广告服务器域名的查询并阻止其加载，从而阻止广告下载。

## 数字足迹管理

如果想了解搜索引擎对你的了解情况并将其删除，可以尝试 [`onerep.com/`](https://onerep.com)。他们似乎已经建立了成功的方法来处理此类问题。不过，防止他人收集关于你的信息的最佳方式是遵循军事和情报社区教导的做法——制造并散布关于自己的错误信息，这样不明真相的人就很难判断哪些是事实、哪些是虚构。全球许多情报机构的成员已经根据所学指导，进行了二十多年的此类操作。现在你需要么彻底消除，要么显著减少你的数字足迹。所谓数字足迹，就像汽车尾气一样，是你在使用互联网时留下的数据/数字残留。FBI 已发布名为 “Digital Exhaust Opt Out Guide” 的文档，供你阅读并遵循。

## 历史档案可靠性警示

沿着同样的思路，不要认为 1985 年之前（甚至更久）的记录是准确的，尤其是军事和政府记录。1974 年，军事及情报机构普遍使用 “burn bags”（烧毁袋）来处理机密信息。这些烧毁袋放置在负责机密信息的每位人员的书桌上，定时的卡车会收集这些袋子并将其带到地下室的烤炉中，用火焰永久性地销毁机密信息。1974 年同时也是一个转型时期，纸质信息开始向计算机转移。当时不存在扫描仪，所有信息必须逐个文档手动输入电脑。当初并未意识到电子化信息的重要性。随着时间推移，越来越多的文档被输入电脑，由政府/军事当局设定的进度计划推动。这些计划越来越难以达成，且负责数千文档录入的工作人员日益感到无聊。上级和高级军官对这类录入工作毫无兴趣，也不认为它重要。录入任务通常分配给低级别人员，但有人发现这可以成为赚钱的途径。起初是以香烟作为报酬，随后报酬逐步升级为金钱。士兵们会找到进行录入的同事，要求他们更改入伍日期、服役期、战功徽章、战场晋升（导致晋升）以及其他众多记录。总之，一些在越南战争期间服役的军人因获得微不足道的小 favor，而接受了被一些人认为无意义的记录更改。虽然我没有个人了解其他案例，但这很可能在全球范围内同期同时发生在军政府和商业领域。人性如此。

## 正则表达式与数据提取

正则表达式是另一种数据提取的途径。此类操作可以使用 Linux、Python 等工具完成。这本身就是一门课程，如果想进一步了解，可自行在谷歌搜索该术语并从各类网站学习。

## DNS 深度解析与邮件安全

-   [早前我们讨论了 DNS 以及与之相关的各种工具。需要记住的关键点是，当你使用名为“Dig”的工具来获取 MX 记录时，设备旁边的较小数字表示该设备优先接收电子邮件。这种情况下可以利用的漏洞是 SPF 记录，因为许多系统管理员误解了电子邮件安全，导致 SPF 记录配置不当。即使现在，你也可以直接访问全球电子邮件服务器，并通过 Linux 命令行在不使用任何电子邮件工具（如 Outlook、Yahoo Mail 等）的情况下，匿名发送电子邮件。 “Dig” 是另一个流行的工具，既可以在命令行中使用，也可以通过前面提到的工具进行使用。如前所述，[`mxtoolbox.com`](https://mxtoolbox.com) 是获取各种 DNS 与电子邮件相关信息的优秀网站。Cisco 提供名为 IronPort 的服务，专注于缓解电子邮件及其他网络威胁（[`www.ironportstore.com/Technology.asp`](https://www.ironportstore.com)）。熟悉 “A” 记录可以让你代替其他域名发送电子邮件。

## 证书颁发机构与云存储安全

GlobalSign (globalsign.com) 发行 HTTPS 证书并提供全球范围内的许多身份相关服务。Let’s Encrypt (letsencrypt.org) 是由 Internet Security Research Group 运营的非营利证书机构，免费提供用于 Transport Layer Security 加密的 X.509 证书。它是全球最大的证书机构，已被超过 26500 万个网站使用，目标是让所有网站都安全并使用 HTTPS。Amazon AWS S3 桶在其云服务中用于存储，但曾多次被入侵。Mailgun (mailgun.com) 用于增强电子邮件营销。
