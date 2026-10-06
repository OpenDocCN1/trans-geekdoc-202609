

# 第 3 章 服务器核心简介

```
<listener>
<cfg:EnableCompatibilityHttpsListener>false</cfg:EnableCompatibilityHttpsListener>
<cfg:CertificateThumbprint></cfg:CertificateThumbprint>
<cfg:Service>
<cfg:Winrs>
<cfg:AllowRemoteShellAccess>true</cfg:AllowRemoteShellAccess>
<cfg:IdleTimeout>1880000</cfg:IdleTimeout>
<cfg:MaxConcurrentUsers>5</cfg:MaxConcurrentUsers>
<cfg:MaxShellRunTime>217483647</cfg:MaxShellRunTime>
<cfg:MaxProcessesPerShell>15</cfg:MaxProcessesPerShell>
<cfg:MaxMemoryPerShell>156</cfg:MaxMemoryPerShell>
<cfg:MaxShellsPerUser>5</cfg:MaxShellsPerUser>
</cfg:Winrs>
</cfg:Config>
```

该监听器还复制了证书到端口和 IP 地址的映射。因此，使用从 `winrm / command` 嵌入文档中复制示例的可靠技巧，我们创建了以下命令来创建一个监听器：
winrm winrm/config/Listener?Address=Transport=HTTPS @Hostname=bfsc1.big.com,CertificateThumbprint=03AD8670C63EBD1DBB764D7AA58YC51D8543077C

以下是参数的说明：

- **Address=** 服务将在所有可用的 IP 地址上监听。
- **Transport=HTTPS** 只有两个选项：HTTP 和 HTTPS。它们分别使用默认端口 5985 和 5986。
- **Hostname=** 必须是证书上的主机名称。
- **CertificateThumbprint=** 这是通过 `certutil` 命令获得的证书指纹。

# 创建入站防火墙规则

下一个要求是启用一条入站防火墙规则以接收客户端请求。对于不安全的 HTTP，已经有一条可用的规则了，可以通过 `/quickconfig` 选项进行设置，但你需要为 HTTPS 端口手动构建一个。

如果你是一个“硬汉派”系统管理员，你可能倾向于通过折磨自己的学习体验来掌握 `netsh advfirewall-sipping` 防火墙命令。MMC 插入程序是给那些“喝着法式拿铁”的极客派系统管理员准备的。在本书中，我们兼顾了硬汉派和极客派。

我们将从构建规则的关键参数开始。像“新建入站规则”这样的向导非常有用，因为它们会引导你完成配置而不会遗漏重要项。它们将帮助你构建一个命令行来创建相同的规则。就像“服务器核心生存指南”章节中所建议，我们建议首先在标准安装上通过向导创建规则，然后尝试使用命令行完成。另一种选择是采取简单的方法，在标准安装上创建，然后简单地将其转换为服务器核心版，正如生存指南章节中解释的那样。

我们将针对服务器核心安装使用“带高级安全功能的 Windows 防火墙”，带你走一遍“新建入站规则”向导。
第一页（如图 3.14 所示）允许你选择端口规则。

# 图 3.14
选择入站规则的类型

![](img/41a83208e6906a3732620203b836cea7_162_0.png)

在“协议和端口”页上，选择 TCP 并在端口输入 5986，如图 3.15 所示。

“操作”页提供了三个选项，如图 3.16 所示：

- “允许连接”——这是本示例所需的设置。
- “如果连接是安全的则允许连接”——如窗口所示，这通过 IPSec 通信来继续连接。网络访问保护功能可以在网络内设置 IPSec 策略。
- “阻止连接”——这将阻止连接。

# 图 3.15
输入入站规则的协议和端口

![](img/41a83208e6906a3732620203b836cea7_163_0.png)

# 图 3.16
选择入站规则的操作

![](img/41a83208e6906a3732620203b836cea7_163_1.png)

“配置文件”页将规则应用于你选择的三个配置文件之一，如图 3.17 所示。公用和专用配置文件适用于移动计算机，以便你可以在家里或无线热点处工作。由于这台服务器是域控制器，专用和公用的概念并不适用。我们将仅使用域配置文件以确保安全。

# 图 3.17
将规则限制为域通信

![](img/41a83208e6906a3732620203b836cea7_164_0.png)

“名称”页允许你为新规则输入名称和可选描述，如图 3.18 所示。

# 图 3.18
为规则提供描述性名称

![](img/41a83208e6906a3732620203b836cea7_164_1.png)

# 第 3 章 服务器核心简介

现在你知道了创建入站规则所需的参数，我们将看看硬汉派的方法。嵌入帮助信息提供了以下创建防火墙规则的语法。请注意这是在 netsh 交互式 shell 中执行的。它也可以通过一条命令行完成：

```
netsh advfirewall firewall=add rule ?
```

```
Usage: add name=<string>
dir=inout
action=allow|block|bypass
program=<program path>
service=<service name> any
description=<string>
enable=yes|no (default=yes)
profile=[public|private|domain](...
localip=<IPv4 address|<IPv6 address><subnet>|<range>|list>
rememoteip=<localsubnet|dhcp|wins|defaultgateway>
IPv4 address|<IPv6 address><subnet>|<range>|list>
localport=0-65535|<port range>[...]|RPC-EPC-PM|IPHTPS
```

