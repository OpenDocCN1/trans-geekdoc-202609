
要加入 SRT，黑客可以通过在线申请请求加入。这需要个人填写一份表格，包含其安全背景、认证、经验年限以及任何其他漏洞赏金经验。收到申请后，Synack 团队将联系该个人，让他们完成一项动手黑客测试。这项实践评估用于确定申请人是否具备被邀请加入该计划所需的技术技能。

![](img/181571ad74cba0e6a2f38fcd2658651e_175_0.png)

**图 5.33** Synack Red Team 在线申请页面。

Synack 在付款处理方式上也不同。对于 HackerOne 和 BugCrowd，付款直到漏洞报告被认为关闭后才支付。这个过程可能从几天到几个月不等——Synack 在其团队完成漏洞分诊后立即支付。

对于黑客来说，Synack 的平台可以是一个在较少竞争的情况下寻找漏洞的好方法。然而，这需要一定的知识基础才能被邀请加入该平台——完成像 HackTheBox 这样的 CTF 将*显著*帮助新黑客通过考试。

### OpenBugBounty

OpenBugBounty 是一个网站，为没有设置漏洞赏金项目的公司进行负责任披露。这为负责任地披露漏洞提供了机会，同时给黑客提供了一个报告漏洞的地方。许多小型公司的网站或没有建立漏洞赏金计划，甚至没有专职安全分析员的组织，依赖 OpenBugBounty 上发布的通知和信息。

要向 OpenBugBounty 报告漏洞，请点击网站首页的**报告漏洞**按钮。这样就可以为 OpenBugBounty 网站中存在的漏洞提交报告。

![](img/181571ad74cba0e6a2f38fcd2658651e_176_0.png)

**图 5.34** [OpenBugBounty.org](https://OpenBugBounty.org)网页截图。

关于 OpenBugBounty 的另一个有趣视角是，它可以用来收集关于某个网站的情报。所有报告，无论是否已解决，都会在原始提交后的 90 天内公开展示。这意味着，一个曾经被报告存在 XSS 且从未修复的网站，可以通过 OpenBugBounty 的历史报告快速定位。该漏洞可能仍然存在，或者也可能出现在网站的其他区域。

## 防御者视角

防御者可以应用这些技术来帮助识别组织内部的其他漏洞。清晰理解漏洞的表现形式及其可能出现的区域，对于降低组织风险至关重要。

故障排除步骤在判断计算机或服务器上的问题是否需要升级处理方面起着关键作用。详细的故障排除工作有助于判断资产是否受到某种利用或攻击的影响，而不仅仅是配置错误。务必确保有证据支持你的理论和处理方式。漏洞赏金计划对组织方也同样有效，建立赏金计划可以激励黑客查找漏洞并报告以获取现金。这反而能提升被测试产品的安全性，防止其被用来攻击环境。然而，一些组织对允许黑客攻击其网站的计划持犹豫态度——请记住，黑帽黑客无论如何都会这么做。

## 总结

发现漏洞归根结底取决于对计算机基础知识、直觉和练习的深入理解。如果没有计算机基本功能和网络的基础知识，发现和评估漏洞将极其困难。通常，这些概念仅靠阅读书籍很难掌握，需要动手实践的学习经验。

开始漏洞 hunting 有多种方式，每种方式都有其优缺点。CTF 是一种在引导下学习的好方法，配合 write-up 可以在迷路时提供方向。当对 CTF 足够熟悉后，转向带有漏洞赏金计划的真实目标，将进一步巩固已有技能。

除此之外，我们必须了解如何将这些漏洞在攻击链中组合利用以产生实际影响。在大多数情况下，单个漏洞本身只能访问有限的信息，但当多个漏洞组合在一起时，一个小问题就可能演变成完全沦陷。

## 注释

- 1. https://www.mynavyhr.navy.mil/Portals/55/Messages/NAVADMIN/NAV2018/NAV18095.txt?ver=OC-H-ZNx2mGNpfNjuJg6jg%3D%3D

- 2. https://explodingtopics.com/blog/iot-stats

- 3. https://www.tutorialspoint.com/what-are-logical-link-control-llc-and-medium-access-control-mac

- 4. https://attack.mitre.org/techniques/T1110/003/

- 5. https://github.com/m4lwhere/pySpray

# 6 漏洞利用与反弹Shell

## 引言

理解漏洞利用和反弹 Shell 对于对目标产生有效影响至关重要。识别漏洞只是游戏的一半，我们需要能够证明这些漏洞可以被利用并对组织造成影响。证明影响的最佳方式是构建一个漏洞利用程序，它要么让我们在系统内获得额外访问权限，要么允许我们收集可用于进一步攻击的敏感信息。

Shell 是交互式终端，也是我们在被攻破主机上执行命令的方式。在黑客社区中，获得 Shell 通常也被称为“立足点”，因为初始访问会被进一步利用，以获得用户或 root 级别的访问权限。本章涵盖识别获取 Shell 的方法以及如何检测它们。我们将探索查找漏洞利用、使用 Metasploit、利用 Meterpreter，以及使用 `msfvenom` 生成漏洞利用代码。

## 为什么漏洞利用很重要

漏洞利用不仅仅是简单地针对目标使用漏洞，我们需要确保发起的漏洞利用会产生影响。在识别了漏洞及其在目标系统上的工作原理之后，我们应该非常清楚系统会容易受到哪些类型的攻击以及如何被利用。通过漏洞利用，我们的任务是在其中放置 payload，以在系统或网络中获得进一步的访问权限。

从防御角度来看，我们必须清楚地了解攻击者可以对我们使用的各种能力。红队和紫队是测试现有防御是否按预期运行的有效方式。当高知名度和高影响力的漏洞被披露时，例如 Log4J 漏洞，组织需要确保其拥有现成的专业知识，不仅要修复漏洞，还要测试修复措施实施中是否存在漏洞。了解攻击者如何通过详细的漏洞利用来收集针对环境的信息，这一点至关重要。

## Exploit-DB

Exploit-DB 是由 Offensive Security 运营的漏洞利用数据库，可通过 [https://www.exploit-db.com/](https://www.exploit-db.com/) 访问。该网站是一个符合 CVE 规范的漏洞利用存档，收录了已知漏洞的漏洞利用代码以及可用于攻击这些漏洞的公开漏洞利用代码。¹ 为易受攻击的系统托管已知的漏洞利用代码，为黑客和防御者提供了资源，以确定易受攻击的系统是否可被公开的漏洞利用代码利用。另请注意，Exploit-DB 同时也托管了在 Web 应用攻击章节中介绍的 GHDB（Google 黑客数据库）。

浏览 Exploit-DB 就像从你的 Web 浏览器访问该页面一样简单。有些工作场所和大学网络可能会阻止对该网站的访问，这也不无道理。如果用户能识别系统中的漏洞，那么 Exploit-DB 上可能就有可用的公开漏洞利用代码来进一步攻击系统。打开网页时，每个漏洞利用都有几个不同的属性。日期表示漏洞利用上传到 Exploit-DB 的时间，下载（D）用于下载漏洞利用代码，应用程序（A）用于获取易受攻击应用程序本身的副本（用于测试漏洞利用），已验证（V）表示 Exploit-DB 团队已验证该漏洞利用是有效且一致的。

![](img/181571ad74cba0e6a2f38fcd2658651e_179_0.png)

**图 6.1** Exploit-DB 截图，显示了针对各种系统的可用漏洞利用代码，注意每个漏洞利用的不同属性。

提供的漏洞利用代码可能使用多种不同的编程语言编写，并涵盖广泛的受影响软件和硬件资产。大多数漏洞利用代码是用 Python 编写的，然而也有许多漏洞利用代码是使用其他脚本语言编写的，或是用于编译可执行文件的源代码。其他漏洞利用则只是如何利用系统中漏洞的说明，并不提供一套可直接运行的代码。这些说明可能简单到只是用于利用系统的 HTTP 请求，但大多数都不是可以立即运行漏洞利用的“一键自动攻击”。

大多数这类漏洞利用代码需要某种形式的手动修改或命令行输入，才能用于我们想要攻击的目标系统；这就是为什么创建漏洞利用代码的本地副本进行修改至关重要。这也是为什么能够审查代码并理解正在发生的活动同样至关重要，这样我们才能有效地使用漏洞利用代码，并在必要时进行调试。

Exploit-DB 还提供了其他工具，例如 `searchsploit` 命令，这是一个命令行工具，可以从命令行查询 Exploit-DB。除此之外，我们可以自己检查漏洞利用代码，甚至可以直接从终端请求漏洞利用的镜像副本以供使用。例如，要搜索已识别的 wpDiscuz WordPress 插件中的潜在漏洞，我们可以使用下面的**图 6.2** 中的命令。

![](img/181571ad74cba0e6a2f38fcd2658651e_179_1.png)

**图 6.2** 使用 searchsploit 查找已知的 wpDiscuz 漏洞利用。

这表明针对影响 wpDiscuz 7.0.4 版本的未认证漏洞，存在三个已知的漏洞利用。远程代码执行对系统的整体机密性、完整性和可用性具有毁灭性影响，当与未认证攻击相结合时，可能会造成重大麻烦。让我们尝试通过使用另一个 `searchsploit` 命令来窥探该漏洞利用，这次引用结果中给出的“路径”。我们将重点放在这个漏洞利用的 Python 版本上，其标签为 `php/webapps/49967.py`。运行下面的命令将检查该漏洞利用（将 `-x` 视为 examine），以便我们查看。

```bash
searchsploit -x php/webapps/49967.py
```

此命令会打开一个交互式文本窗口，我们可以在其中自行评估漏洞利用代码，以决定是否使用它。在粗略浏览代码并确定需要进一步调查后，我们可以按“q”键退出文本窗口。如需查看代码并在需要时添加修改，我们可以使用镜像（`-m` 开关）创建漏洞利用的本地副本。与之前的命令类似，下面的命令依赖于特定漏洞利用给出的路径。

```bash
searchsploit -m php/webapps/49967.py
```

```text
Exploit: WordPress Plugin wpDiscuz 7.0.4 - Remote Code Execution
(Unauthenticated)
    URL: https://www.exploit-db.com/exploits/49967
    Path: /usr/share/exploitdb/exploits/php/webapps/49967.py
File Type: Python script, Unicode text, UTF-8 text executable, with very
long lines (864)

Copied to: /home/chris/49967.py
```

请注意，该漏洞利用已被复制到当前工作目录，在本示例中即主目录。复制到我们的目录后，我们可以用 `vim` 或 `nano` 等工具打开它，继续审查代码。审查该漏洞利用代码可以发现，它分别通过 `-u` 和 `-p` 开关请求 URL 和路径。之后，它似乎在提交带有 PHP 载荷的漏洞利用之前收集环境信息。

```python
# Exploit Title: WordPress Plugin wpDiscuz 7.0.4 - Remote Code Execution (Unauthenticated)
# Date: 2021/06/08
# Exploit Author: Fellipe oliveira
# Vendor Homepage: https://gvectors.com/
# Software Link: https://downloads.wordpress.org/plugin/wpdiscuz.7.0.4.zip
# Version: wpDiscuz 7.0.4
# Tested on: Debian9, Windows 7, Windows 10 (Wordpress 5.7.2)
# CVE : CVE-2020-24186
# Thanks for the great contribution to the code: Z3r0c00l (https://twitter.com/zeroc00l)

#!/bin/python3

import requests
import optparse
import re
import random
import time
import string
import json

parser = optparse.OptionParser()
parser.add_option('-u', '--url', action="store", dest="url", help="Base target host: http://192.168.1.81/blog/")
parser.add_option('-p', '--path', action="store", dest="path", help="Path to exploitation: /2021/06/blogpost")

options, args = parser.parse_args()

if not options.url or not options.path:
    print('[+] Specify an url target')
```

**图 6.3** 审查漏洞利用代码，以识别可能发生的活动以及预期结果。

![](img/181571ad74cba0e6a2f38fcd2658651e_182_0.png)

**图 6.4** 使用 banner 启动 Metasploit。

## 选择漏洞利用模块

当 `msfconsole` 窗口出现后，我们可以使用 `search` 命令搜索特定漏洞利用。在此示例中，我们将搜索名为 ChurchInfo 的程序，以确定是否有可用模块。此实例中要运行的命令是 `search churchinfo`，它会返回一个模块。

![](img/181571ad74cba0e6a2f38fcd2658651e_182_1.png)

**图 6.5** 搜索 ChurchInfo 显示有一个模块可用。

要使用通过搜索功能识别出的漏洞利用，我们可以复制并粘贴模块名称，并使用“`use`”命令将其选中，例如 `use exploit/multi/http/churchinfo_upload_exec`。正如 Metasploit 返回的信息中所指出的，我们也可以从搜索窗口中选择一个模块，并使用其编号来使用它——这比输入模块完整名称要快得多、简单得多。相反，我们可以只需在“`use`”命令中提供模块编号，例如 `use 0`，这会从搜索结果中选择编号为 0 的模块。

在查看此信息时，我们可以看到该模块需要对系统进行经过身份验证的访问。通过身份验证后，模块会在应用程序中创建一封草稿邮件，为电子邮件上传附件，而漏洞就在于服务器如何存储该附件。如需更详细的文档，运行 `info -d` 命令会以 markdown 格式打开该模块的适用文档。该文档包含如何安装应用程序、如何配置应用程序，以及如何证明该漏洞能够被该模块有效利用。

![](img/181571ad74cba0e6a2f38fcd2658651e_184_0.png)

**图 6.8** 可通过 info -d 命令获取的详细 markdown 模块文档。

`msf6 exploit(multi/http/churchinfo_upload_exec) > show payloads`

兼容的载荷

| # | 名称 | 披露日期 | 排名 | 检查 | 描述 |
|---|------|-----------------|------|-------|-------------|
| 0 | `payload/generic/custom` | | 普通 | 否 | 自定义载荷 |
| 1 | `payload/generic/shell_bind_tcp` | | 普通 | 否 | 通用命令 Shell，内联 TCP 绑定 |
| 2 | `payload/generic/shell_reverse_tcp` | | 普通 | 否 | 通用命令 Shell，内联反向 TCP |
| 3 | `payload/generic/shell_internet` | | 普通 | 否 | 通用命令 Shell，反向 TCP 连接 |
| 4 | `payload/multi/meterpreter/reverse_http` | | 普通 | 否 | 与体系结构无关的 Meterpreter 阶段，反向 HTTP |
| 5 | `payload/multi/meterpreter/reverse_https` | | 普通 | 否 | 与体系结构无关的 Meterpreter 阶段，反向 HTTPS |
| 6 | `payload/php/bind_perl` | | 普通 | 否 | PHP 命令 Shell，通过 Perl 绑定 TCP |
| 7 | `payload/php/bind_php_ipv6` | | 普通 | 否 | PHP 命令 Shell，通过 PHP 绑定 TCP IPv6 |
| 8 | `payload/php/bind_php` | | 普通 | 否 | PHP 命令 Shell，通过 PHP 绑定 TCP |
| 9 | `payload/php/bind_php_ipv6` | | 普通 | 否 | PHP 命令 Shell，通过 php 绑定 TCP IPv6 |
| 10 | `payload/php/download_exec` | | 普通 | 否 | PHP 可执行文件下载并执行 |
| 11 | `payload/php/exec` | | 普通 | 否 | PHP 执行命令 |
| 12 | `payload/php/meterpreter/bind_tcp` | | 普通 | 否 | PHP Meterpreter，绑定 TCP 存根 |
| 13 | `payload/php/meterpreter/bind_tcp_ipv6` | | 普通 | 否 | PHP Meterpreter，绑定 TCP 存根 IPv6 |
