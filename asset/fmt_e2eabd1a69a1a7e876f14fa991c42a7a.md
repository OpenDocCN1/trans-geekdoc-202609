
**提示**

The Art of Hacking GitHub 仓库包含了一系列可用于逆向工程的工具：[`github.com/The-Art-of-Hacking/art-of-hacking/tree/master/reverse_engineering`](https://github.com/The-Art-of-Hacking/art-of-hacking/tree/master/reverse_engineering)。

## 常用的取证工具

![](img/key_topic_icon2.jpg)

以下是几个可以用于取证的工具和 Linux 发行版示例：

* **ADIA (数字调查与分析设备)：** ADIA 是一种基于 VMware 的设备，用于数字调查和取证，完全由公共领域软件构建。ADIA 包含的工具有 Autopsy、Sleuth Kit、Digital Forensics Framework、log2timeline、Xplico 和 Wireshark。大部分系统维护使用 Webmin。ADIA 针对中规模的数字调查和取证设计。该设备运行在 Linux、Windows 和 macOS 上。提供 i386（32 位）和 x86_64（64 位）版本。你可以从 [`github.com/The-Art-of-Hacking/art-of-hacking/tree/master/reverse_engineering`](https://github.com/The-Art-of-Hacking/art-of-hacking/tree/master/reverse_engineering) 下载 ADIA。

# 第 5 章：利用线路和无线网络

第 5 章讨论了如何破解无线网络。它讨论了如 `Aircrack-ng`、`Kismet`、`KisMAC` 以及其他可用于无线网络评估工具。有关这些工具的更多信息，请参阅第 5 章。

以下是几个有助于测试无线网络的无线破解工具：

* `Wifite2`：这是一个用于测试无线网络的 Python 程序，可以从 [`github.com/derv82/wifite2`](https://github.com/derv82/wifite2) 下载。
* `Rogue access points`（伪造接入点）：你可以通过使用 `hostapd` 等开源工具轻松地创建伪造接入点。关于如何构建你自己的无线攻击实验室以及使用 `hostapd` 的描述，请访问 [`github.com/The-Art-of-Hacking/h4cker/blob/master/wireless_resources/virtual_adapters.md`](https://github.com/The-Art-of-Hacking/h4cker/blob/master/wireless_resources/virtual_adapters.md)。
* `EAPHammer`：该工具可用于执行恶意孪生攻击，可以 [`github.com/s0lst1c3/eaphammer`](https://github.com/s0lst1c3/eaphammer) 下载。
* `mdk4`：该工具用于执行模糊测试、IDS 规避以及其他无线攻击。`mdk4` 可以 [`github.com/aircrack-ng/mdk4`](https://github.com/aircrack-ng/mdk4) 下载。
* `Spooftooph`：该工具用于欺骗和克隆蓝牙设备。可以 [`gitlab.com/kalilinux/packages/spooftooph`](https://gitlab.com/kalilinux/packages/spooftooph) 下载。
* `Reaver`：该工具用于对 Wi-Fi 安全设置 (WPS) 实现进行暴力破解攻击。`Reaver` 可以 [`gitlab.com/kalilinux/packages/reaver`](https://gitlab.com/kalilinux/packages/reaver) 下载。
* `Wireless Geographic Logging Engine (WiGLE)`：你可以在 [`wigle.net`](https://wigle.net) 学习这种无线路驱动工具。
* `Fern Wi-Fi Cracker`：该工具用于对无线网络执行不同的攻击，包括破解 WEP、WPA 和 WPS 密钥。你可以从 [`gitlab.com/kalilinux/packages/fern-wifi-cracker`](https://gitlab.com/kalilinux/packages/fern-wifi-cracker) 下载 Fern Wi-Fi Cracker。

## 隐术工具

在第 8 章中，你学习了隐术是将信息隐藏在图像、视频和其他文件中。你还学习了 `steghide` 等工具。以下是几个可以用于执行隐术的额外工具：

* `OpenStego`：你可以从 [`www.openstego.com`](https://www.openstego.com) 下载此隐术工具。
* `snow`：这是一个基于文本的隐术工具，可以从 [`github.com/mattkwan-zz/snow`](https://github.com/mattkwan-zz/snow) 下载。
* `Coagula`：这个可以从图像制作声音的程序可以从 [`www.abc.se/~re/Coagula/Coagula.html`](https://www.abc.se/~re/Coagula/Coagula.html) 下载。
* `Sonic Visualiser`：该工具可以分析音乐或音频录制中的嵌入信息。可以 [`www.sonicvisualiser.org`](https://www.sonicvisualiser.org) 下载。
* `TinEye`：这是一个 [`tineye.com`](https://tineye.com) 反向搜索网站。
* `metagoofil`：该工具可以从文档和图像中提取元数据。可以 [`github.com/laramies/metagoofil`](https://github.com/laramies/metagoofil) 下载。

## 云工具

在第 7 章“云、移动和物联网安全”中，你学习了多种用于云解决方案的工具。以下是几个可用于云评估的额外工具：

* `ScoutSuite`：这系列工具可以揭示 AWS、Azure、Google Cloud 以及其他云平台的漏洞。可以 [`github.com/nccgroup/ScoutSuite`](https://github.com/nccgroup/ScoutSuite) 下载。
* `CloudBrute`：此云枚举工具可以 [`github.com/0xsha/CloudBrute`](https://github.com/0xsha/CloudBrute) 下载。
* `Pacu`：用于 AWS 攻击的框架，可以 [`github.com/RhinoSecurityLabs/pacu`](https://github.com/RhinoSecurityLabs/pacu) 下载。
* `Cloud Custodian`：此云安全、治理和管理工具可以 [`cloudcustodian.io`](https://cloudcustodian.io) 下载。

## 考试准备任务

正如引言中“如何使用本书”部分提到的，你有几个考试准备选择：第 11 章中的后期准备](#ch11.xhtml#ch11)”以及 Pearson Test Prep 在线上的考试模拟题。

### 复习所有主题

回顾本章中最重要的主题，这些主题在页边上标记有关键主题图标。表 10-2 列出了这些主题及其所在的页码。

![](img/key_topic_icon.jpg)

**表 10-2** 第 10 章关键主题

| 主题元素 | 描述 | 页码 |
| --- | --- | --- |
| 段落 | 编程语言逻辑 | 403 |
| 段落 | 编程语言数据结构 | 404 |
| 段落 | Python 编程资源 | 407 |
| 段落 | 侦察和枚举常用工具 | 413 |
| 段落 | `Nslookup`、`Host` 和 `Dig` 用于被动侦察 | 413 |
| 段落 | `Whois` 用于被动侦察 | 415 |
| 段落 | `FOCA` 用于被动侦察 | 416 |
| 段落 | `Shodan` 作为情报源 | 421 |
| 段落 | `Maltego` 用于被动侦察 | 423 |
| 段落 | `Recon-ng` 用于被动侦察 | 425 |
| 段落 | 常用于漏洞扫描的工具 | 443 |
| 段落 | 凭据攻击常用工具 | 463 |
| 段落 | `John the Ripper` 用于破解密码 | 464 |
| 段落 | `Cain and Abel` 用于凭据攻击 | 468 |
| 段落 | `Hashcat` 用于破解密码 | 469 |
| 段落 | `Hydra` 用于凭据攻击 | 471 |
| 段落 | 彩虹表和 `RainbowCrack` 等工具用于凭据攻击 | 473 |
| 段落 | `Medusa` 和 `Ncrack` 用于凭据攻击 | 474 |
| 段落 | `CeWL` 用于创建自己的字典 | 474 |
| 段落 | `Mimikatz` 用于凭据攻击 | 475 |
| 段落 | `Patator` 用于暴力破解攻击、枚举 SNMPv3 用户名或 VPN 密码以及其他类型的凭据攻击 | 476 |
| 段落 | 常用于持久化的工具 | 477 |
| 段落 | `Veil` 用于规避安全控制 | 478 |
| 段落 | `Tor` 用于规避监控和控制 | 482 |
| 段落 | `Proxychains` 用于规避 | 483 |
| 段落 | `Encryption` 用于规避监控和控制 | 483 |
| 段落 | 结合 `DNS` 和其他协议（如 `NTP`）进行封装和隧道传输 | 484 |
| 段落 | `Metasploit` 攻击框架 | 486 |
| 段落 | `Meterpreter` 用于后期渗透 | 490 |
| 段落 | `BeEF` 用于利用 Web 应用 | 493 |
| 段落 | `GDB` 用于调试应用程序和安全研究 | 494 |
| 段落 | `Windows Debugger (WinDbg)` 用于调试内核和用户态代码 | 496 |
| 段落 | `OllyDbg` 用于应用程序的调试、反汇编和分析以及安全研究 | 496 |
| 段落 | `Immunity` 用于应用程序的调试、反汇编和分析以及安全研究 | 498 |
| 段落 | `IDA` 用于应用程序的调试、反汇编和分析以及安全研究 | 498 |
| 段落 | 用于取证的工具 | 501 |
| 段落 | 软件保障的常用工具 | 502 |
| 段落 | 用于应用程序、协议和计算设备的 Peach 测试工具 | 503 |
| 段落 | 用于应用程序、协议和计算设备的美国模糊测试工具 (American Fuzzy Lop) | 503 |

## 定义关键术语

定义本章中的以下关键术语，并在术表中检查你的答案：

- 循环
- 条件
- 布尔运算符
- 字符串运算符
- 算术运算符
- JavaScript 对象表示 (JSON)
- 数组
- 字典
- 键值对
- 逗号分隔值 (CSV)
- 列表
- 树
- 库
- 过程
- 函数
- 类
- bash shell
- Python
- Ruby
- PowerShell
- Perl
- SearchSploit
- JavaScript
- Nslookup
- Whois
- 收集档案的指纹识别 (FOCA)
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
- OWASP 破坏攻击代理 (ZAP)
- w3af
- DirBuster
- gobuster
- John the Ripper
- Cain
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

这些问题的答案出现在 附录 A。如需更多考试格式的练习，请使用在线 Pearson Test Prep 软件。

**1.** `SQLmap` 是一种用于寻找 \_\_\_\_\_\_\_\_ 漏洞的工具。

**2.** `Nikto` 是一种开源 Web 漏洞 \_\_\_\_\_\_\_。

**3.** 你可以使用 `John the Ripper` 来 \_\_\_\_\_\_\_\_\_\_\_。

**4.** 下述命令是做什么用的？

点击查看图像

```
hashcat --force -m 0 -a 0 -o words file1 file2
```

**5.** 下述命令正在做什么？

点击查看图像

```
# ncrack -p 22 --user dave -P my_list 172.18.104.166

在 172.18.104.166 22/tcp 上发现了 凭据：

172.18.104.166 22/tcp ssh: dave 'password12'
```
