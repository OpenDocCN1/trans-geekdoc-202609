

## 第 3 章服务器 Core 简介

在本书中，你将找到有关为特定功能配置 Server Core 的更多细节。

## 创建域控制器和管理 DNS

在以前的 Windows Server 版本中，你会使用命令行中的 DCPromo 来创建并提升域控制器。在 Windows Server 2012 中，DCPromo 已被弃用，且只能配合响应文件使用。因此，我们将教你一种较新的方法——使用 PowerShell——来创建域控制器。由于你已经在本章中安装了 Active Directory 域服务 (AD DS)，大部分工作已经完成。

你需要使用 Windows Server 2012 中的先决条件检查。这将帮助你显示服务器正确安装域控制器所需的配置。如果你正在执行实际安装，`Test-ADDDomainInstallation` 会检查域控制器安装的先决条件。系统将提示你输入域和登录凭据，如图 3.19 所示。

![](img/41a83208e6906a3732620203b836cea7_167_0.png)

```
C:\Users\Administrator> Test-ADDDSDomainControllerInstallation
cmdlet Test-ADDDSDomainControllerInstallation at command pipeline position 1
Using Parameters:
    DomainName: contoso-bigfire.com
    DomainAdministratorPassword: ******
    Confirm: $True

Message         Context         Required  Status
TestVerifyADTrustedFor...      False       Success
TestVerifyADPrereq...         False       Success
TestVerifyADReplication...     False       Prior
TestVerifyOutboundReplica...  False       Success
```

你已经准备好安装域控制器了。`Install-ADDDSDomainController` 命令将同时安装 DNS。如果你不添加任何参数，将将采用以下默认设置：

- 只读域控制器：否
- 全局目录：是
- DNS 服务器：是
- 数据库文件夹：C:\Windows\NTDS
- 日志文件文件夹：C:\Windows\NTDS
- SYSVOL.folder：C:\Windows\SYSVOL

有很多脚本可以下载并使用以更改所有不同的参数。以下是你可能需要更改配置的完整格式：

```
Install-ADDDSDomainController -DomainName <String> [-ADPrepCredential <PSCredential>] [-ApplicationPartitionsToReplicate <String>] [-CreateDnsDelegation] [-Credential <PSCredential>] [-CriticalReplicationOnly] [-DatabasePath <String>] [-DnsDelegationCredential <PSCredential>] [-Force]
```

## 配置规则和功能 133

- [-InstallationMediaPath<String>] [-InstallDns] [-LogPath<String>]
- [-MoveInfrastructureMasterRoleIfNecessary] [-DnsOnNetwork]
- [-GlobalCatalog] [-RebootOnCompletion] [-ReplicationSource<String>]
- [-SafeModeAdministratorPassword<SecureString>] [-SiteName]
- [-SkipAutoConfigns] [-SkipPreChecks] [-SystemKey<SecureString>]
- [-SysvolPath] [-Confirm] [-CommonParameters]]

继续运行该命令：

```
PS:\Users\administrator> Install-ADDSDomainController
```

你将收到以下提示：

目标服务器将配置配置为域控制器，并在操作完成后重启。

你是否要继续此操作？

+ [Y] 是 [A] 全是 [N] 否 [L] 全否 [S] 挂起 [?] 帮助（默认为 "Y"）

当你选择“是”时，安装将开始（图 3.20）。

![](img/41a83208e6906a3732620203b836cea7_168_0.png)

## 配置 DHCP 服务器

当 Windows Server 2003 发布时，微软开始向极极客风格的 Linux 系统发起挑战。它增加了可用命令套件，为想要尽可能进行配置的极客追随者提供了工具。这使得 `netsh` 命令随之流行。

一个分支机构需要一个基本的 DHCP 实现，包含一个带有默认网关、DNS 服务器和 DNS 域名称标准选项的单一范围。在设置之前，你需要通过 `add` 选项在 Active Directory 中标识它。在以下代码中，利用了交互模式来执行命令：

```
netsh dhcp
netsh dhcp>add server bfsc1.bigfirm.com 192.168.1.11
```

正在添加服务器 bfsc1.bigfirm.com, 192.168.1.11

命令成功完成。

```
netsh dhcp>show server
```

在目录服务中找到服务器：

```
Server [bfsc1.bigfirm.com] Address [192.168.1.11] Ds location: c
bfscl=bigfirm.com
```

命令成功完成。
要添加范围，你需要切换到 `netsh dhcp` 服务器提示符并使用 `scope` 命令。所需的参数是范围所代表的子网和子网掩码、范围名称以及任何注释：

```
netsh dhcp>server
netsh dhcp server>add scope 192.168.1.0 255.255.255.0 "Branch Office 1"
"Sample Dhcp scope"
```

命令成功完成。
netsh dhcp server>show scope

===============================================================================
| Scope Address | Subnet Mask | State | Scope Name | Comment |
| :--- | :--- | :--- | :--- | :--- |
| 192.168.1.0 | 255.255.255.0 | -Active | -Branch Office 1 | -Sample DHCP scope |
===============================================================================

范围总数 = 1
命令成功完成。
范围需要一组 IP 地址来为 DHCP 客户端提供服务，以及标准的范围选项。选项通过选项代码（三位标识符）进行标识。你可以在 DHCP 管理控制台中查看这些标识符。选项具有字节、字、字符串或 IP 地址格式的值。对于我们的示例，我们有以下选项、标识符和值：

* IP 范围：192.168.1.50-100
* 默认网关：003, 192.168.1.254
* DNS 服务器：006, 192.168.1.11
* DNS 域名称：015, bigfirm.com

```
netsh dhcp server>scope 192.168.1.1
```

已更改当前范围到 192.168.1.0。
netsh dhcp server>add range 192.168.1.50-100

命令成功完成。
netsh dhcp server>set option 003 192.168.1.254

命令成功完成。
netsh dhcp server>set option 006 192.168.1.11

命令成功完成。
netsh dhcp server>set option 015 bigfirm.com

命令成功完成。
netsh dhcp server>show option

范围 192.168.1.0 的选项：
DHCP 标准选项：

| Option Code | Value |
| :--- | :--- |
| 003 | 192.168.1.254 |
| 006 | 192.168.1.11 |
| 015 | bigfirm.com |

在 Server Core 上运行这些命令后，你也可以连接到该服务。

## 设置文件服务器

文件服务器提供基本的文件共享功能。在许多其他角色中，共享文件夹的过程通常由

## 创建主分区

第一个任务是提供一个数据分区。在以下示例中，我们决定将大小设为 10 GB。
DiskPart 命令非常适合此操作。它以命令行格式或交互式命令行格式管理磁盘控制台的所有功能。第一组命令显示磁盘和卷。我们的数据分区尚未分配，因此未列在卷列表中。

