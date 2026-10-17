
**提示**

The Art of Hacking GitHub 仓库包含了许多可用于逆向工程的工具列表：[`github.com/The-Art-of-Hacking/art-of-hacking/tree/master/reverse_engineering`](https://github.com/The-Art-of-Hacking/art-of-hacking/tree/master/reverse_engineering)。

#### 取证的常用工具

![](img/key_topic_icon2.jpg)

以下是几个可以用于取证的工具和 Linux 发行版示例：

* **ADIA (数字调查与分析设备):** ADIA 是一种基于 VMware 的设备，用于数字调查和取证，完全由公领域软件构建。ADIA 包含的工具有 Autopsy、The Sleuth Kit、数字取证框架、`log2timeline`、`Xplico` 和 `Wireshark`。大部分系统维护使用 `Webmin`。ADIA 专为小型数字调查和取证设计。该设备运行在 Linux、Windows 和 macOS 上。提供 `i386`（32 位）和 `x86_64`（64 位）版本。你可以从 [`github.com/The-Art-of-Hacking/art-of-hacking/tree/master/reverse_engineering`](https://github.com/The-Art-of-Hacking/art-of-hacking/tree/master/reverse_engineering) 下载 ADIA。

第 5 章，“利用有线和无线网络](#ch05.xhtml#ch05)”讨论了如何破解无线网络。它介绍了诸如 `Aircrack-ng`、`Kismet`、`KisMAC` 以及其他可用于无线网络评估的工具。有关这些工具的更多信息，请参阅第 5 章。

以下是几个可以帮助测试无线网络的无线破解工具：

* `Wifite2`：这是一个用于测试无线网络的 Python 程序，可以从 [`github.com/derv82/wifite2`](https://github.com/derv82/wifite2) 下载。
* `伪造的接入点 (Rogue access points)`：你可以使用 `hostapd` 等开源工具轻松创建伪造的接入点。关于如何构建自己的无线攻击实验室并使用 `hostapd` 的描述，我可以在 [`github.com/The-Art-of-Hacking/h4cker/blob/master/wireless\_resources/virtual\_adapters.md`](https://github.com/The-Art-of-Hacking/h4cker/blob/master/wireless_resources/virtual_adapters.md) 查看。
* `EAPHammer`：该工具用于进行双孪生攻击 (evil twin attacks)，可以在 [`github.com/s0lst1c3/eaphammer`](https://github.com/s0lst1c3/eaphammer) 下载。
* `mdk4`：该工具用于执行模糊测试、IDS 规避和其他无线攻击。`mdk4`可以从 [`github.com/aircrack-ng/mdk4`](https://github.com/aircrack-ng/mdk4) 下载。
* `Spooftooph`：该工具用于伪造和克隆蓝牙设备。可以在 [`gitlab.com/kalilinux/packages/spooftooph`](https://gitlab.com/kalilinux/packages/spooftooph) 下载。
* `Reaver`：该工具用于对 Wi-Fi 安全设置 (WPS) 实现进行暴力破解攻击。`Reaver`可以从 [`gitlab.com/kalilinux/packages/reaver`](https://gitlab.com/kalilinux/packages/reaver) 下载。
* `无线地理日志引擎 (WiGLE)`：你可以在 [`wigle.net`](https://wigle.net) 学习这个战争驱动 (war driving) 工具。
* `Fern Wi-Fi Cracker`：该工具用于对无线网络进行不同的攻击，包括破解 WEP、WPA 和 WPS 密钥。你可以从 [`gitlab.com/kalilinux/packages/fern-wifi-cracker`](https://gitlab.com/kalilinux/packages/fern-wifi-cracker) 下载 Fern Wi-Fi Cracker。

### 隐写工具

在第 8 章中，你学习了隐写术是将信息隐藏在图像、视频和其他文件行为。你还学习了诸如 `steghide` 等工具。以下是几个可以用于执行隐写的的额外工具：

* `OpenStego`：你可以从 [`www.openstego.com`](https://www.openstego.com) 下载此隐写工具。
* `snow`：这是一个基于文本的隐写工具，可以从 [`github.com/mattkwan-zz/snow`](https://github.com/mattkwan-zz/snow) 下载。
* `Coagula`：一个可以从图像制作声音的程序，可以在 [`www.abc.se/~re/Coagula/Coagula.html`](https://www.abc.se/~re/Coagula/Coagula.html) 下载。
* `Sonic Visualiser`：该工具可以分析音乐或音频录制中嵌入的信息。可以在 [`www.sonicvisualiser.org`](https://www.sonicvisualiser.org) 下载。
* `TinEye`：这是一个位于 [`tineye.com`](https://tineye.com) 的反向图像搜索网站。
* `metagoofil`：该工具可以从文档和图像中提取元数据信息。你可以从 [`github.com/laramies/metagoofil`](https://github.com/laramies/metagoofil) 下载 metagoofil。

### 云端工具

在第 7 章，“云端、移动和物联网安全](#ch07.xhtml#ch07)”中，你学习了多种用于测试云端解决方案的工具。以下是几个可以执行云评估的额外工具：

* `ScoutSuite`：这套工具可以用于发现 AWS、Azure、Google Cloud Platform 和其他云平台的漏洞。你可以从 [`github.com/nccgroup/ScoutSuite`](https://github.com/nccgroup/ScoutSuite) 下载 ScoutSuite。
* `CloudBrute`：你可以从 [`github.com/0xsha/CloudBrute`](https://github.com/0xsha/CloudBrute) 下载此云枚举工具。
* `Pacu`：这是一个用于 AWS 利用的框架，可以在 [`github.com/RhinoSecurityLabs/pacu`](https://github.com/RhinoSecurityLabs/pacu) 下载。

### 考试准备

如第 11 章中提到的，你有一些为了考试准备的选择：

### 复习所有主题

表 10-2 列出了这些关键主题以及所在的页码。

Images/key_topic.jpg

| 关键主题 | 描述 | 页码 |
| :--- | :--- | :--- |
| 语言逻辑 | 403 |
| 常见数据结构 | 404 |
| Python 资源 | 407 |
| 用于侦察和枚举的工具 | 413 |
| `Nslookup`, `Host` 和 `Dig` 用于被动侦察 | 413 |
| `Whois` 用于被动侦察 | 415 |
| `FOCA` 用于被动侦察 | 416 |
| `Shodan` 作为情报源 | 421 |
| `Maltego` 用于被动侦察 | 423 |
| `Recon-ng` 用于被动侦察 | 425 |
| 用于漏洞扫描的工具 | 443 |
| 用于凭据攻击的工具 | 463 |
| `John the Ripper` 用于破解密码 | 464 |
| `Cain and Abel` 用于凭据攻击 | 468 |
| `Hashcat` 用于破解密码 | 469 |
| `Hydra` 用于凭据攻击 | 471 |
| 彩虹表和 `RainbowCrack` 工具用于凭据攻击 | 473 |
| `Medusa` 和 `Ncrack` 用于凭据攻击 | 474 |
| `CeWL` 用于创建自己的字典文件 | 474 |
| `Mimikatz` 用于凭据攻击 | 475 |
| `Patator` 用于暴力破解、枚举 SNMPv3 用户名或 VPN 密码以及其他凭据攻击 | 476 |
| 用于持久化的工具 | 477 |
| `Veil` 用于规避安全控制 | 478 |
| `Tor` 用于规避和绕过监控 | 482 |
| `Proxychains` 用于规避 | 483 |
| 加密用于规避和绕过监控 | 483 |
| 使用 `DNS` 和其他协议（如 `NTP`）进行封装和隧道传输 | 484 |
| `Metasploit` 利用框架 | 486 |
| `Meterpreter` 用于后渗透 | 490 |
| `BeEF` 用于利用 应用程序 | 493 |
| `GDB` 用于调试应用程序和安全研究 | 494 |
| Windows 调试器 (`WinDbg`) 用于调试内核和用户态代码 | 496 |
| `OllyDbg` 用于调试、反汇编和分析应用程序以及安全研究 | 496 |
| `Immunity` 用于调试、反汇编和分析应用程序以及安全研究 | 498 |
| `IDA` 用于调试、反汇编和分析应用程序以及安全研究 | 498 |
| 用于取证的常用工具 | 501 |

| 段落 | 软件保障的常用工具 | 502 |
| :--- | :--- | :--- |
| 段落 | Peach，用于应用程序、协议和计算设备进行模糊测试 | 503 |
| 段落 | American Fuzzy Lop，用于对应用程序、协议和计算设备进行模糊测试 | 503 |

## 定义关键术语

请定义本章中的以下关键术语，并在词汇表中检查你的答案：

- 循环
- 条件判断
- 布尔运算符
- 字符串运算符
- 算术运算符
- JavaScript 对象表示法 (JSON)
- 数组
- 字典
- 键/值对
- 逗号分隔值 (CSV)
- 列表
- 树
- 库
- 过程
- 函数
- 类
- bash shell 壳
- Python
- Ruby
- PowerShell
- Perl
- SearchSploit
- JavaScript
- Nslookup
- Whois
- 带有收集档案的指纹识别组织 (FOCA)
- EXIF
- theHarvester
- Shodan
- Maltego
- Recon-ng
- Censys
- Burp Suite
- Nessus
- SQLmap
- Nikto
- OWASP 攻击代理 (ZAP)
- w3af
- DirBuster
- gobuster
- John the Ripper
- cain
- Hashcat
- Hydra
- 彩虹表
- Medusa
- CeWL
- Mimikatz
- Patator
- PowerSploit
- Empire
- Metasploit
- GDB
- WinDbg
- OllyDbg
- Immunity Debugger
- IDA

## 问答

这些问题的答案出现在附录 A。练习请使用 Pearson Test Prep。

1 `SQLmap` 是一个用于发现漏洞的工具。

2 `Nikto` 是一个开源 Web 漏洞。

3 你可以使用 `John the Ripper` 来查找哈希值。

4 下列命令是做什么的？

```
hashcat --force -m 0 -o words
```

5 下列命令在做什么？

```
ncrack -p 2 --user -P my_list 172.104.166

Discovered credentials for ssh on 172.104.166 2/tcp:

172.104.166 2/tcp ssh: password

Ncrack done: scanned in 00 seconds.

Ncrack finished.
```

6 什么工具可以从网站生成字典列表？

7 许多渗透测试人员、攻击者甚至恶意软件使用的工具用于从内存中检索密码，也是一个非常实用的后渗透工具？

8 `Metasploit` 是一个使用 `Ruby` 语言创建的利用框架。

9 参考下面的示例脚本。这里使用了什么语言？

```
@client = client

exec_opts = Rex::Parser::Arguments.new(

   "-h" => [false, "帮助菜单。"],

   "-i" => [false, "枚举接口"],

   "-r" => [true, "目标地址范围或 CIDR 标识符"],

   "-s" => [false, "将发现的 IP 地址保存到日志中."]

)

def enum_int

   print_status("Enumerating Interfaces")

   client.net.config.interfaces.each do |i|

    if not i.mac_name =~ /Loopback/

      print_status(" #{i.mac_name}")

      print_status(" #{i.ip}")

      print_status(" #{i.netmask}")

      print_status()

   end

end

def arp_scan(cidr)

   print_status("ARP Scanning #{cidr}")

   ws = client.railgun.ws232

   iphlp = client.railgun.iphlpapi

   i, a = 0, []

   iplst,found = [],""

   ipadd = Rex::Socket::RangeWalker.new(cidr)

   numip = ipadd.num_ips

   while (iplst.length < numip)

     ipa = ipadd.next_ip

      if (not ipa)

          break

   end

end
```

10 参考下面的示例脚本。这些语句称为什么？这里使用了什么编程语言？

```
# 向框架实例添加路由

def add_route(opts={})

   subnet = opts[:subnet]

   netmask = opts[:netmask] || "255.255.255.0" # 默认 C 类

   Rex::Socket::SwitchBoard.add_route(subnet, netmask, session)

end

# 从框架实例删除路由

def delete_route(opts={})

   subnet = opts[:subnet]

   netmask = opts[:netmask] || "255.255.255.0" # 默认 C 类

   Rex::Socket::SwitchBoard.remove_route(subnet, netmask, session)

end
```
