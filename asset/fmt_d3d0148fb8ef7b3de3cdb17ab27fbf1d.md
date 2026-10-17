
```
cdkey /bfs1 /user:administrator /pass:P@ssw0
```

你可以选择将 `pass` 参数留空以便提示密码。在注册凭据后，你可以通过单元程序连接到服务器。

在之前的 Windows Server 版本中，你需要安装 `adminpak.msi` 包才能让单元程序管理所有 Windows 服务。在 Windows Server 2012 中，`adminpak.msi` 包被远程服务器管理工具（Remote Server Administration Tools）取代。这些功能使其安装更加简单且更精细。在图 3.10 中，你可以通过“角色和功能向导”启用“远程服务器管理工具”。

图 3.10

安装远程管理功能

![](img/41a83208e6906a3732620203b86cea7_155_0)

如果你愿意，可以在新的 MMC 添加单元程序时连接到另一台计算机。某些单元程序允许将多个服务器添加到一个中进行集中管理。以下步骤为 Windows Server 2012 Server Core 安装创建管理 DHCP 服务的 MMC。请注意，这些步骤只有在 DHCP 服务启动并授权后才能执行。这将在“配置 DHCP 服务”部分进行讨论。

1. 在完整安装上安装远程服务器管理工具后，在运行提示处输入 `MMC`。
2. 从文件下拉菜单选择“添加/删除单元程序”。
3. 弹出“添加/删除单元程序”窗口，列出了可以添加到此 MMC 实例的可用单元程序。
4. 选择 DHCP 单元程序并点击“添加”。然后点击“确定”。
5. 在 MMC 控制台中，右键点击 DHCP 图标并选择“添加服务器”。
6. 在添加服务器窗口中，授权的 DHCP 服务器列在底部区域，如图3.11所示。选择 Server Core 实例。
7. 点击确定，选定的服务器将显示并可以进行导航，如图3.12所示。

图 3.11

向 MMC 添加 DHCP 服务器

![](img/41a83208e6906a3732620203b86cea7_156_0.png)

### 图 3.12

聚焦于服务器核心（Server Core）的 DHCP 控制台

![](img/41a83208e6906a3732620203b836cea7_157_0.png)

## 远程发送命令：Windows 远程外（Remote Shell）

Windows Remote Shell 允许将命令发送到服务器。与 Telnet 类似，它允许你连接到服务器并从远程提示符运行命令。然而，它无法像 Telnet 那样提供持续连接。它在发送命令、接收结果后会关闭连接。

这是一个基于简单对象访问协议（SOAP）技术的轻量级客户端-服务器应用程序。对于此服务，你真正需要理解的 SOAP 就是客户端使用 XML 格式的文本向服务器发送命令，而返回给客户端的输出也是使用 HTTP 的相同格式。基于文本的通信可以被记事本等文本编辑器轻松读取，并能被协议分析器轻松嗅探。因此，请将其视为一种管理服务器的安全方法。你需要对其进行锁定。

微软提供了一个使用 `winrm quickconfig` 命令来测试 Windows Remote Shell 的选项。然而，它使用 HTTP 和 TCP 端口 `5985` 进行设置。正如他们建议的，这种设置并不适用于生产环境。为了将其锁定，你需要确保连接是加密的并且服务器经过了验证。Ifsec 提供这种安全性，但你可能无法使用该功能。你可以将 Windows Remote Shell 设置为 HTTPS (SSL) 通信，它使用服务器证书来验证服务器并加密连接。

我们将介绍基本步骤来启动它。

### 获取证书

获取证书有两种选择：从受信任的证书颁发机构购买，或者建立自己的证书颁发机构并从中请求证书。后者的成本低得多，特别是在使用 Windows Server 时。

你的证书颁发机构尚未建立；但是你应该对如何在生产 Active Directory 环境中实现这一点有一个完善的计划。你需要考虑会对整个组织产生深远影响的决策。这些影响将需要手动管理来消除。我们不会详细介绍这一部分，我们将在实验室环境中对此进行“快速且粗略”的处理。

在全量安装的 Windows Server 2012 域控制器上，安装了 Active Directory 证书角色。该角色的典型安装将包含网络注册组件。这需要 Internet 信息服务（IIS）。我们不会介绍如何安装它。我们只选择证书颁发机构服务。这将允许创建和管理证书。此外，它将允许组织中的域计算机使用 RPC 协议和 Kerberos 验证请求证书。我们将安装一个受信任的根企业证书颁发机构。选择根（Root）是因为它是组织中第一个也是唯一的域。选择企业（Enterprise）是因为它使用 Active Directory 来验证用户和计算机。因为我们是信任的。因为它使用 Active Directory，它会自动请求证书。快速且粗略。

我们想使用 Server Core 查看证书。（我们尝试过远程使用 MMC，但出于安全考虑，这不是一个选项。）在 Server Core 安装中查看证书有两种方法：使用 `certutil` 命令或 PowerShell 的 `dir` 命令：

```
rem using certutil
P:\Users\Administrator.BIGFIRM\Documents>certutil -viewstore my
```

`my` 指的是本地机存储的自身的证书。当你运行 `certutil` 时，会出现一个窗口列出已安装的证书，如图 3.13 所示。

### 图 3.13

certutil 显示的证书

![](img/41a83208e6906a373260203b836cea7_158_0.png)

注意唯一安装的证书下方的超链接，“点击此处查看证书属性”。这将打开证书信息。

PowerShell 通过其提供程序（providers）提供了获取证书的另一种路径。通常，提供程序是 PowerShell 遍历的对象组。文件系统是提供程序的一个示例，因此你可以对文件和文件夹对象进行操作。另一个提供程序是证书存储。你可以遍历证书存储来查看和管理证书。

`dir` 命令是 PowerShell 开发人员为 `get-items` 命令创建的别名。然后你可以使用标准的 MS-DOS 命令行提示符遍历文件系统。以下命令列出的位置与之前 `certutil` 列出的位置相同：

```
rem starting powershell
C:\Users\Administrator.BIGFIRM >powershell

P C: C:\Users\administrator.BIGFIRM dir:\localmachine\my | FL
```

```
Subject : CN=BFS1.bigfirm.com
Issuer : CN=bigfirm-BF1-CA, DC=bigfirm, DC=com
Thumbprint : 03AD6BC7063ED1DBB764CD7AA859C5D1854307C
FriendlyName =
NotBefore : 7/23/2009 06:55:41 AM
NotAfter : 7/23/2019 06:55:41 AM
Extensions : .oid,{System.Security.Cryptography.Oid,System.Security.Cryptography.Oid,System.Security.Cryptography.Oid,System.Security.Cryptography.phyd...}}
```

`FL` 参数是另一个值得出的命令。它将 `dir` 命令的输出格式化为行分隔的列表。我们喜欢使用这种格式，因为值不会像表格格式那样被截断。在这种特定情况下，表格格式（未显示）会截断。

### 创建监听器

监听器告诉 Windows Remote Shell 监听并响应哪些端口和地址。默认情况下，HTTP 端口是 `5985`，HTTPS 端口是 `5986`。你可以通过以下命令查看设置。HTTP 和 HTTPS 的输出会截断最重要的部分。这将手动管理来消除。可能会发送到服务器的请求。

```
P:\Users\Administrator.BIGFIRM>winrm get win/config -format=pretty
```

### 远程管理 Server Core

```
<cfg:MaxProviderRequests>429496295</cfg:MaxProviderRequests>
<cfg:Client>
  <cfg:NetworkDelays>5000</cfg:NetworkDelays>
  <cfg:URLPrefix>wsman</cfg:URLPrefix>
  <cfg:AllowUnencrypted>false</cfg:AllowUnencrypted>
  <cfg:Auth>
    <cfg:Basic>true</cfg:Basic>
    <cfg:Kerberos>true</cfg:Kerberos>
    <cfg:Negotiate>true</cfg:Negotiate>
    <cfg:Certificate>false</cfg:Certificate>
    <cfg:CredSSSP>false</cfg:CredSSSP>
  </cfg:Auth>
  <cfg:DefaultPorts>
    <cfg:HTTP>5985</cfg:HTTP>
    <cfg:HTTPS>5986</cfg:HTTPS>
  </cfg:DefaultPorts>
  <cfg:IPv4Filter>+</cfg:IPv4Filter>
  <cfg:IPv6Filter>+</cfg:IPv6Filter>
  <cfg:EnableCompatibilityHttpListener>false</cfg:EnableCompatibilityHttpListener
</cfg:
<cfg:Service>
  <cfg:RootSSL>=:NSG:BAD;P(A;GA;;;BA)S(PU;FA;GA;;;WD)(AU;SA;GW;;;WD)</cfg:RootSSL>
  <cfg:MaxConcurrentOperations>429496295</cfg:MaxConcurrentOperations>
  <cfg:MaxConcurrentOperationsPer>15</cfg:MaxConcurrentOperationsPer>
  <cfg:EnumerationTimeout>60000</cfg:EnumerationTimeout>
  <cfg:MaxConnections>25</cfg:MaxConnections>
  <cfg:MaxPacketRetrievalTime>120</cfg:MaxPacketRetrievalTime>
[/cfg>
```

## 第 3 章 服务器核心简介

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

`winrm winrm/config/Listener?Address=Transport=HTTPS @Hostname=bfsc1.big.com,CertificateThumbprint=03AD8670C63EBD1DBB764D7AA58YC51D8543077C`

以下是参数的说明：

- **Address=** 服务将在所有可用的 IP 地址上监听。
- **Transport=HTTPS** 只有两个选项：HTTP 和 HTTPS。它们分别使用默认端口 `5985` 和 `5986`。
- **Hostname=** 必须是证书上的主机名称。
- **CertificateThumbprint=** 这是通过 `certutil` 命令获得的证书指纹。

### 创建入站防火墙规则

下一个要求是启用一条入站防火墙规则以接收客户端请求。对于不安全的 HTTP，已经有一条可用的规则了，可以通过 `/quickconfig` 选项进行设置，但你需要为 HTTPS 端口手动构建一个。

如果你是一个“硬汉派”系统管理员，你可能倾向于通过折磨自己的学习体验来掌握 `netsh advfirewall-sipping` 防火墙命令。MMC 插入程序是给那些“喝着法式拿铁”的极客派系统管理员准备的。在本书中，我们兼顾了硬汉派和极客派。

我们将从构建规则的关键参数开始。像“新建入站规则”这样的向导非常有用，因为它们会引导你完成配置而不会遗漏重要项。它们将帮助你构建一个命令行来创建相同的规则。就像“服务器核心生存指南”章节中所建议，我们建议首先在标准安装上通过向导创建规则，然后尝试使用命令行完成。另一种选择是采取简单的方法，在标准安装上创建，然后简单地将其转换为服务器核心版，正如生存指南章节中解释的那样。

我们将针对服务器核心安装使用“带高级安全功能的 Windows 防火墙”，带你走一遍“新建入站规则”向导。

第一页（如图 3.14 所示）允许你选择端口规则。

### 图 3.14

选择入站规则的类型

![](img/41a83208e6906a3732620203b836cea7_162_0.png)

在“协议和端口”页上，选择 TCP 并在端口输入 `5986`，如图 3.15 所示。

“操作”页提供了三个选项，如图 3.16 所示：

- “允许连接”——这是本示例所需的设置。
- “如果连接是安全的则允许连接”——如窗口所示，这通过 IPSec 通信来继续连接。网络访问保护功能可以在网络内设置 IPSec 策略。
- “阻止连接”——这将阻止连接。

### 图 3.15

输入入站规则的协议和端口

![](img/41a83208e6906a3732620203b836cea7_163_0.png)

### 图 3.16

选择入站规则的操作

![](img/41a83208e6906a3732620203b836cea7_163_1.png)

“配置文件”页将规则应用于你选择的三个配置文件之一，如图 3.17 所示。公用和专用配置文件适用于移动计算机，以便你可以在家里或无线热点处工作。由于这台服务器是域控制器，专用和公用的概念并不适用。我们将仅使用域配置文件以确保安全。

### 图 3.17

将规则限制为域通信

![](img/41a83208e6906a3732620203b836cea7_164_0.png)

“名称”页允许你为新规则输入名称和可选描述，如图 3.18 所示。

### 图 3.18

为规则提供描述性名称

![](img/41a83208e6906a3732620203b836cea7_164_1.png)

## 第 3 章 服务器核心简介

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

## 第 3 章服务器 Core 简介

在本书中，你将找到有关为特定功能配置 Server Core 的更多细节。

## 创建域控制器和管理 DNS

在以前的 Windows Server 版本中，你会使用命令行中的 `DCPromo` 来创建并提升域控制器。在 Windows Server 2012 中，`DCPromo` 已被弃用，且只能配合响应文件使用。因此，我们将教你一种较新的方法——使用 PowerShell——来创建域控制器。由于你已经在本章中安装了 Active Directory 域服务 (AD DS)，大部分工作已经完成。
