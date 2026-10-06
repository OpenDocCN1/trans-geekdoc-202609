
你可以通过修改 `-format` 关来更改输出格式。默认情况下，输出以文本格式显示，但你可以将其输出为简单 XML（使用 `-format:XML` 切换）或格式化 XML（使用 `-format:pretty` 切换）。

- 6. 尝试以下命令：
WinRM e WinRM /config/listener -format:text
WinRM e WinRM /config/listener -format:xml
WinRM e WinRM /config/listener -format:pretty

虽然在服务器上可以对 WinRM 进行更多操作，但它用于远程管理的主要目的是通过 `quickconfig` 命令启用监听器。完成后，你可能会将注意力转到客户端，在客户端进行实际的管理。

## 使用 WinRS

Windows 远程外壳 (WinRS) 用于在已配置 WinRM 的远程服务器上执行命令。例如，你可以从 Windows 7 或 Windows 8 系统使用 WinRS 对远程服务器执行命令。
WinRS 命令的主要格式如下如下：

```
WinRS -r:servername command
```

- `-r` 关用于识别远程服务器的名称。虽然还有其他开关，但 `-r` 关是最常用的开关。

## 使用 WinRS 发出 WMIC 命令

WinRS 命令可以是你从命令行发出的任何命令。例如，你可以使用 Windows 管理实例命令行工具 (WMIC) 工具来记录计算机上运行的服务。
在使用 WinRS 之前，你可以使用此命令显示如何使用 WMIC 记录任何系统上运行的服务信息。启动命令行，并输入此命令：

```
WMIC /output:services.htm /node:localhost service list brief /format:htable
```

这会创建一个名为 `services.htm` 的 HTML 格式文件。你可以通过在命令提示符中输入 `services.htm` 来查看它，这将启动 Internet Explorer 显示该文档。它列出了系统上的所有服务，以及启动模式、状态、状况和一些额外细节。

现在，使用相同的命令记录已配置 WinRS 的远程计算机的服务。将 `Srv2012` 替换为你配置的服务器名称，并更改 HTML 文件的名称：

``````
WinRS -r:Srv2012 WMIC /output:Srv2012services.htm /node:Srv2012 service list brief /format:htable
```

你可以通过命令提示符输入文件名来查看此文件。在此示例中，它是 `Srv2012services.htm`。如果你想获取有关服务的详细信息，将 `list` 更改为 `full`。此工具可以轻松地提供有关多个服务器的重要文档，你可以轻松保存保存。

## 使用 WinRS 发出 PowerShell 命令

尽管 WMIC 功能丰富，但它并不是你唯一可以使用命令。你在服务器上输入的任何命令都可以通过 WinRS 远程输入。下面的链接显示了 PowerShell cmdlet：

http://msdn.microsoft.com/en-us/windows/desktop/powershell/v3.aspx

PowerShell 命令遵循“动词-名词”格式。动词指定操作，名词识别操作将采取的对象。最流行的动词是 `get`，如果你在 PowerShell 提示符处输入 `Get-Service`，它将列出所有与 `get` 动词关联的名词。其他动词还有 `set`、`copy`、`move` 等。你可以对这些动词执行相同的操作；使用连字符 (`-`) 并按 Tab 键遍历与该动词相关的所有名词。有关动词列表，请查看此 MSDN 页面：http://msdn.microsoft.com/en-us/library/powershell/verbs.aspx

例如，你可以从 PowerShell 提示符处输入以下 PowerShell 命令来检查系统中服务的状态：

```
Get-Service
```

你不需要输入整个命令。你只需要输入 `Get-S` 并按 Tab 键。此命令将列出系统上的所有服务（运行或停止）并显示名称。结合 WinRS 使用此命令，你可以远程执行相同的命令：

```
WinRS -r:Srv2012 PowerShell Get-Service > services.txt
```

如果你想将此重定向到文件：

## 远程服务器管理工具

远程桌面（Remote Desktops）允许你连接到服务器的桌面，你只需要执行单个任务，如重置用户账户的密码或验证 DNS 配置正确。RSAT 包含 Active Directory 用户和计算机 (ADUC) 以及 DNS 控制台等工具。在桌面上安装 RSAT 后，你可以启动 ADUC 来操作用户帐户，或者可以启动 DNS 控制台来验证 DNS 配置。

## 服务器管理工具

用户仍然需要适当权限来运行已安装的工具。例如，在桌面系统上安装工具的管理员不会被添加到域管理员 (Enterprise Admins) 角色，无法在域中执行任何操作。RSAT 中的可用工具用于管理 Windows Server 2012 R2 角色和功能。

## RSAT 性问题

RSAT 不兼容用于远程管理 Windows Server 2000 和 Windows Server 2003 服务器的管理工具包。如果你在系统中安装了这些工具，必须在安装 RSAT 之前卸载它们。

此外，RSAT 不允许你管理具有远程桌面角色的服务器。可以使用单独服务器管理工具管理托管远程桌面角色的 Windows Server 2012 R2 服务器。

有关远程桌面服务问题的更多信息，请查看 Microsoft KB 文章：http://support.microsoft.com/kb/934518。RSAT 信息位于文章末尾。

## RSAT 工具

在桌面上安装 RSAT 后，你可以启动 ADUC 来操作用户帐户，或者可以启动 DNS 控制台来验证 DNS 配置。

换句话说，如果服务器运行 DHCP 角色，可以使用 DHCP 控制台来管理它。

如果服务器不是 DHCP 服务器，则无法使用 RSAT DHCP 控制台。

以下列表显示了 RSAT 提供的常用工具。这并不是详尽列表，而是常用工具的摘要。有关完整列表，请查看 Microsoft KB 文章：http://support.microsoft.com/kb/94317。

### 活动目录服务工具
AD 工具包括 Active Directory 用户和计算机、Active Directory 域和信任、Active Directory 站点和服务以及用于远程管理活动目录的其他插件。

### 活动目录证书服务工具
这些工具包括用于枚举证书的独立证书机构工具。

### 动态主机配置协议服务器工具
包含 DHCP 控制台。

### 域名系统服务器工具
DNS 工具包括 DNS 管理器控制台和 `dnsc.exe` 命令行。

### 文件服务工具
这些工具包括共享和存储管理插件、分布式文件系统以及文件服务器资源。

### 网络策略和访问服务
包含路由和远程访问插件，用于网络策略和访问。

## 第17 章远程服务器管理

远程桌面服务包含远程桌面和远程桌面服务插件。

BitLocker 驱动加密工具包含用于 BitLocker 驱动加密的管理 bde 脚本。

故障转移集群工具这些工具包括故障转移集群管理器插件和 `cluster.exe` 命令行工具。

组策略管理工具包括组策略管理控制台、组策略编辑器和组策略启动编辑器。

网络负载平衡工具包含网络负载平衡程序以及 `nlb.exe` 和 `wbs.exe` 命令行工具。

SMTP 服务器工具包含 SMTP 插件。

SAN 管理工具包含 SAN 管理器插件和 `lovi-storage.exe` 命令行工具。

Windows 系统资源工具包含 Windows 系统资源管理器插件和 `wsm.exe` 命令行工具。

## 安装 RSAT

下载 RSAT 后，你可以按照以下步骤安装并启用 RSAT：

- 1. 使用 资源管理器浏览到保存下载的位置。
2. 双击安装包，并按照向导完成安装。
3. 安装完成后，点击关闭。
4. 选择开始 > 控制面板以启动控制面板。
5. 选择“程序”，然后点击“启用或关闭 Windows 功能”。
6. 勾选“远程服务器管理工具”复框。你的显示将类似于图 1740。
