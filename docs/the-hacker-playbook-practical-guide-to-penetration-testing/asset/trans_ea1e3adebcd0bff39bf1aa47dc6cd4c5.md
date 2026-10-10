

### c. git clone `https://github.com/mattifestation/PowerSploit.git`

### d. cd PowerSploit

### e. wget `https://raw.github.com/obscuresec/random/master/StartListener.py`

### f. wget `https://raw.github.com/darkoperator/powershell_scripts/master/ps_encoder.py`

## 18. 安装 Responder

### a. Responder 将用于获取 NTLM 质询/响应哈希

### b. cd /opt/

### c. git clone `https://github.com/SpiderLabs/Responder.git`

## 19. 安装社会工程学工具包（Kali 上无需重新安装）(SET)

### a. SET 将用于社会工程学攻击活动

### b. cd /opt/

### c. git clone `https://github.com/trustedsec/social-engineer-toolkit/set/`

### d. cd set

### e. ./setup.py install

## 20. 安装 bypassuac

### a. 将用于在后渗透阶段绕过 UAC

### b. cd /opt/

### c. wget `http://www.secmaniac.com/files/bypassuac.zip`

### d. unzip bypassuac.zip

### e. cp bypassuac/bypassuac.rb /opt/metasploit/apps/pro/msf3/scripts/meterpreter/

### f. mv bypassuac/uac/ /opt/metasploit/apps/pro/msf3/data/exploits/

## 21. 安装 BeEF

### a. BeEF 将用作跨站脚本攻击框架

### b. apt-get install beef-xss

## 22. 安装模糊测试列表 (SecLists)

### a. 这些是配合 Burp 用于模糊测试参数的脚本

### b. cd /opt/

### c. git clone `https://github.com/danielmiessler/SecLists.git`

## 23. 安装 Firefox 附加组件

### a. Web Developer Add-on: `https://addons.mozilla.org/en-US/firefox/addon/web-developer/`

### b. Tamper Data: `https://addons.mozilla.org/en-US/firefox/addon/tamper-data/`

### c. Foxy Proxy: `https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-standard/`

### d. User Agent Switcher: `https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/`

![](images/00012.jpeg)

我强烈建议你也配置一个 Windows 7 虚拟机。这是因为我在许多测试中都遇到过应用程序需要 Internet Explorer，或者像 `Cain and Abel` 这样的工具只能在一种操作系统上运行的情况。请记住，所有的 PowerShell 攻击都将要求你在 Windows 主机上运行命令。我想强调的观点是：时刻保持准备，拥有多个可用的操作系统将为你节省大量时间和麻烦。

## Windows 高级工具列表补充：

*   HxD (十六进制编辑器)
*   Evade (用于杀毒软件绕过)
*   Hyperion (用于杀毒软件绕过)
*   Metasploit
*   Nexpose/Nessus
*   Nmap
*   oclHashcat
*   Evil Foca
*   `Cain and Abel`
*   Burp Suite Pro
*   Nishang
*   PowerSploit
*   Firefox (附加组件)
    *   Web Developer Add-on
    *   Tamper Data
    *   Foxy Proxy
    *   User Agent Switcher

## 设置 Windows

建立 Windows 通用测试平台应当是为了补充你的 Kali Linux 主机。请记住修改主机名，如果不需要 NetBios 则将其禁用，并尽可能加固这些主机。你最不想要的就是在测试过程中被攻陷。

在 Windows 上我没有什么特别的设置，但通常我会安装以下内容。

1.  HxD `http://mh-nexus.de/en/hxd/`
2.  Evade `https://www.securepla.net/antivirus-now-you-see-me-now-you-dont/`
3.  Hyperion `http://www.nullsecurity.net/tools/binary.html`
    ### a. 下载/安装 Windows 编译器 `http://sourceforge.net/projects/mingw/`
    ### b. 在解压后的 Hyperion 文件夹中运行 `make`，你应该就能得到二进制文件。
4.  下载并安装 Metasploit `http://www.Metasploit.com/`
5.  下载并安装 Nessus 或 Nexpose
    ### a. 如果你是自掏腰包购买软件，可能应该考虑 Nessus，因为它便宜得多，但两者都很好用
6.  下载并安装 nmap `http://nmap.org/download.html`
7.  下载并安装 oclHashcat `http://hashcat.net/oclhashcat/#downloadlatest`
8.  下载并安装 evil foca `http://www.informatica64.com/evilfoca/`
9.  下载并安装 `Cain and Abel` `http://www.oxid.it/cain.html`
10. BURP `http://portswigger.net/burp/download.html`
11. 下载并解压 Nishang: `https://code.google.com/p/nishang/downloads/list`
12. 下载并解压 PowerSploit: `https://github.com/mat-tifestation/PowerSploit/archive/master.zip`
13. 安装 Firefox 附加组件
    ### a. Web Developer Add-on: `https://addons.mozilla.org/en-US/firefox/addon/web-developer/`
    ### b. Tamper Data: `https://addons.mozilla.org/en-US/firefox/addon/tamper-data/`
    ### c. Foxy Proxy: `https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-standard/`
    ### d. User Agent Switcher: `https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/`

![](images/00013.jpeg)

本章旨在帮助你构建一个标准的测试平台。工具总是在变化，因此保持测试平台更新和打补丁非常重要。希望这些信息足以让你入门，我已包含本书中使用的所有工具。如果你觉得我遗漏了任何关键工具，请随时在 `http://www.thehackerplaybook.com` 留言。对你的工作虚拟机进行一次完整的干净快照，让我们开始发现和攻击网络吧。

![](images/00014.jpeg)

在运行任何战术之前，你必须了解并分析你的对手。研究目标的弱点并理解环境将带来巨大的回报。本章将从一个与普通渗透测试书籍略有不同的角度来探讨扫描，应被视为对你当前扫描流程的补充，而非替代。

无论你是经验丰富的渗透测试员还是刚入行的新手，扫描可能已经被讨论过无数次了。我不会详细比较所有不同的网络扫描器、漏洞扫描器、SNMP 扫描器等，但我会尝试给你提供最高效的扫描流程。本节将分为外部扫描、内部扫描和 Web 应用程序扫描。

![](images/00015.jpeg)

