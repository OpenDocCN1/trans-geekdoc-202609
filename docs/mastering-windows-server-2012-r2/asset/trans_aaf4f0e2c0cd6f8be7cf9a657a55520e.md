

# 配置角色和功能

在触发通信之前，计算机将在宽限期内运行，最终将超时。这将启用“功能受限模式”。

在拥有超过 25 个许可证但未与总部建立安全 TCP/IP 连接的分机构办公室中，设置 KMS 服务器是一个切实行的选项。如果您的数量未达到“25”的阈值，微软提供了批量许可多激活密钥 (MAK)，其工作原理与产品密钥的在线激活类似。

后续章节详细介绍了在分机构办公室的 Server Core 安装上设置 KMS 服务器的步骤。

SRV 记录位于 DNS 中，用于发布网络内服务的存在性。这将在第 5 章“IP 地址管理和 DHCP 故障转移”中讨论。默认情况下，KMS 服务器会在主 DNS 域中使用 SRV 记录发布服务。对于您的 Windows Server 2012 Server Core 示例，它是 BigFirm.com。

在 BigFirm.com DNS 域中，你会看到一个 _VLMS._TCP.Bigfirm.com 的 SRV 记录。它具有以下属性：

- * 名称：_vlms._TCP
- 类型：SRV
- 优先级：0
- 权重：0
- 端口：1688
- 主机名：Bfsc.bigfirm.com

要实现这种情况，你需要向 DNS 区域添加权限，以允许更新 KMS 服务器。我们建议使用域控制器作为 KMS 服务器。该服务非常轻量，且域控制器已经具有在 DNS 中注册 SRV 记录的权限。

然而，使用 SRV 记录，如果客户端位于分机构办公室，无法控制它们将调用哪个 KMS 服务器。它们将查询 DNS 并收到位于其他处的服务器响应。此外，应禁用分机构办公室服务器的 DNS 发布。这是通过在 HKEY_LOCAL_MACHINE\SOFTWARE\Windows\NT\CurrentVersion\key 中创建一个数值为 1 的 DisabledPublishing dword 值来实现。

# 启用防火墙

Windows 防火墙配置中已有一个入站规则，它是“密钥管理服务”规则组的一部分。你需要启用它。该操作命令如下：

```
netsh advfirewall firewall set group="Key Management Service" new enable=yes
```

# 激活安装

就像你激活 Server Core 实例一样，分机构办公室的 KMS 服务器需要使用 `slmgr.vbs /ipk` 和 `ato` 进行激活。

# 将客户端指向 KMS

默认情况下，批量激活 3.0 客户端（Windows 8 和 Windows Server 2012）尝试使用 SRV 记录连接到 KMS。由于该过程是不可感知的，它将访问任何提供的 KMS 服务器。你可以手动将任何客户端上的 KMS 主机与以下内容关联：

```
cscript c:\windows\system32\slmgr.vbs /sk bfsc.bigfirm.com:1688
```

你可以使用组策略对象在整个站点分发此设置。

# 使用 Windows 备份保护数据

这是添加到 Server Core 安装的功能之一。备份数据是一个好主意。你的环境可能倾向于使用原生备份工具或第三方企业级备份解决方案。然而，Windows 备份尚未安装或配置。

微软重新设计了其原生实用程序并将其命名为 Windows 备份。它利用卷影复制服务来冻结数据状态以便备份。最初，它仅设计为在磁带驱动器上提供离备份。磁带备份已被取消。幸运的是，微软将应用范围扩展到了本地连接的硬盘。

在讨论中，我们将探索管理 Windows 备份的 PowerShell cmdlet。首先，你需要安装 Windows 备份功能。然后你可以运行 `Get-WindowsFeature` 查看与 Windows 备份关联的名称列表。

```
PS C:\Users\Administrator>Install-WindowsFeature Server-Backup
```

如果安装正确，你将在 PowerShell 中看到以下内容：

| 成功 | 退出代码 | 结果 |
|---|---|---|
| True | No | Windows Server Backup |

你需要创建一个备份策略。备份策略是自动化备份的指令集。当你创建一个新的时，它默认是空的。因此，你将创建它并填充指令。这些指令包括调度备份、设置备份目标位置以及其他几个参数，你将在安装策略时看到这些参数。使用 `New-WBPolicy` cmdlet 进行安装：

```
PS C:\Users\Administrator>New-WBPolicy
```

| Schedule : |
| BackupTargets : |
| VolumesToBackup : |
| FilesSpecsToBackup : |
| FilesSpecsToExclude : |
| ComponentsToBackup : |
| BMR : False |
| SystemState : False |
| OverwriteOldVhd : False |
| BackupOptions : False |

```

现在你看到了 New-WBPolicy 的属性，你可以使用以下脚本来设置它们。该脚本将设置策略为每天早上 9 点备份 Sales 文件夹中的所有内容：

```
PS C:\Users\Administrator> $policy = New-WBPolicy

$fileSpec = New-WBFileSpec -FileSpec C:\Sales
Add-WBFileSpec -Policy $policy -FileSpec $fileSpec

Add-WBBackupMetadata $policy

$disks = Get-WBDisk
$backupLocation = New-WBBackupTarget -Disk $disks[0]
Add-WBBackupTarget -Policy $policy -Target $backupLocation

Set-WBSchedule -Policy $policy 09:00

Set-WBPolicy -Policy $policy
```

这将帮助你开始使用 PowerShell 处理 Windows 备份。你可以在 http://microsoft.com/en-us/library/ee70683.aspx 参考 Windows Server Backup 的完整 cmdlet 列表。

# 总结

使用 Server Core 中的新功能。Windows Server 2012 操作系统是其完整安装版的精简版本。移除的代码减少了安全威胁的配置面，并提高了了性能。主要的管理界面是命令提示符。它可以运行良好，但无法像完整安装版那样执行所有角色。

**精通它** Windows Server 2012 Server Core 版本与 Windows Server 2008 的原始版本有所不同。那些关键区别是什么？它们如何影响服务器可以执行的角色？

安装并配置 Server Core。Server Core 的安装与安装 Windows Server 2012 完整版相同。完整版提供了一系列初始任务，例如加入域、启动自动更新和安装功能。这些操作中的每一个都有一个对应的命令。

**精通它** Server Core 有一个特定的脚本用于执行几项编辑注册表的常用任务。该脚本的名称是什么？哪个参数可以提供额外的命令列表以执行许多常用配置任务？

为分机构办公室部署设置 Server Core。分机构办公室部署是 Server Core 实现的一种可能场景。基础架构角色活动目录服务、DNS、DHCP、文件服务以及打印文档服务将安装并配置在服务器上，为小型办公室环境内的用户提供这些基本服务。这些服务的配置可以远程进行。

**精通它** 为了配置活动目录服务和 DNS，需要从命令行运行活动目录服务安装向导 (DCPromo)。需要什么来为命令输入参数？

远程管理操作系统。Server Core 可以通过三种选项进行远程管理。远程桌面管理是用的，但可以使用命令提示符和 Server Core 提供的 GUI。MMC 单元可以连接到服务器的服务，使用标准的 Windows 工具进行管理。最后，一项新服务 Windows Remote Shell 提供了到服务器的单命令连接。

**精通它** Windows Remote Shell 提供 quickconfig 选项。系统管理员在使用该选项时应该注意哪些安全担忧？可以做什么来解决这些担忧？

