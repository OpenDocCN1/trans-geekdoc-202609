

# 第 3 章 服务器核心简介

以下 PowerShell 命令行列出了可用的角色和功能：

```
rem list可用（已启用和禁用）的角色
PSC:\Users\administrator>Get-WindowsFeature
```

现在你已经将这些信息呈现在面前了，你可以看到要添加到下一个命令中的角色名称。下面的列表显示了 DHCP 服务器角色。你希望使用 Name（名称）列中的条目作为该命令的参数。

| 显示 (Display) | 名称 (Name) | 安装状态 (Install State) |
| --- | --- | --- |
| DHCP Server | DHCP | available |
| Active Directory Domain Services | AD-Domain-Services | available |
| DNS Server | DNS | available |
| Print and Document Services | Print-Services | available |

每个角色可能需要几分钟来安装。PowerShell 会告诉你安装过程中是否出现任何问题。它还会告诉你是否需要任何先决条件。添加角色后，你可以再次运行 Get-WindowsFeature 查看状态是否显示为已安装。以下是剩余的功能：

```
PSC:\Users\administrator>Add-WindowsFeature AD-Domain-Services
PSC:\Users\administrator>Add-WindowsFeature DNS
PSC:\Users\administrator>Add-WindowsFeature Print-Services
```

# 启用远程桌面

随后 CONFIGG 为我们提供了帮助。如果你参考图 3.9，你会看到这将是选项 7，远程桌面。在你输入命令 7 后，它会要求你启用或禁用远程桌面。输入字母 E 来启用。系统将提示你是否允许运行任何版本远程桌面的客户端进行连接，或仅允许运行具有网络级身份验证的远程桌面客户端。

输入你的选择；它会弹出一个窗口，你就完成了！

# 配置防火墙

你有几个防火墙配置需要执行。防火墙需要允许远程协议通过它。这包括配置端口以允许微软管理控制台（MMC）单元程序所需的通信。以下命令启用了与“远程管理”（Remote Administration）组相关的端口：

```
netsh advfirewall firewall set group="Remote Administration" new enable=yes
```

此组包含了可以在服务器上访问的所有 MMC 端口。它包含了所有协议，因此你可以拥有细度的防火墙策略来远程管理 MMC 操作，例如事件查看器、磁盘管理、文件和打印服务以及任务计划程序。

惊讶的是，此组并不包含远程桌面。它是属于同名独立组的一部分。它应该通过以下命令启用，顺便说一下，该命令是 netsh advfirewall firewall set rule 的嵌入字段。在生成此命令时并没有执行实际的向导。（new 参数表示向规则中添加新设置）

```
netsh advfirewall firewall set rule group="Remote Desktop" new enable=yes
```

如果你想从 MMC 管理防火墙，你还需要运行以下命令：

```
netsh advfirewall set currentprofile settings remotemanagement enable
```

尽管防火墙按理应是启用状态的，但在某些情况下（例如测试新应用程序时），你可能想要禁用它。以下是开启和关闭它的命令：

```
netsh advfirewall set allprofiles state on
netsh advfirewall set allprofiles state off
```

如果你犯了配置错误，还可以使用此命令重置防火墙：

```
netsh advfirewall reset
```

我们将展示的最后一个防火墙命令可能是最常用的，用于启用或禁用端口。以下是如何添加和删除 SQL Server 端口 1433 的示例：

```
netsh advfirewall add rule name="Open SQL Server Port 1433" dir=in action=allow protocol=TCP localport=1433
```

```
netsh advfirewall delete rule name="Open SQL Server Port 1433" protocol=tcp localport=1433
```

我们还需要使用用于配置防火墙的 PowerShell 命令行工具属性。你可以使用此命令设置规则、修改规则并通过更改属性来控制行为：

```
Set-NetFirewallProfile -Profile Domain,Public,Private -Enabled True
```

要删除防火墙规则只需使用此命令：

```
Remove-NetFirewallRule -Action Block
```

# 管理服务器远程控制台

在配置服务器上已安装的角色之前，你需要了解远程管理的选项。我们已经简要提到过它们，你将在接下来的章节的角色配置中看到它们的应用。

远程桌面是一种非常可靠且安全的管理远程标准安装的方法，它在 Server Core 上同样可用。只要网络支持，微软管理控制台及其单元程序对于 Server Core 管理来说是非常出。一个新选项是 Windows 远程外（Windows Remote Shell），它提供了到远程服务器的命令行连接。

# 使用远程桌面管理服务器

终端服务（管理模式）随 Windows Server 2000 发布。这是一个备受欢迎的补充，因为它提供了你所连接计算机的虚拟桌面环境。Windows Server 2003 通过将其设置为默认安装改进了它。它是在服务器上执行远程工作的基本方法。我们经常使用这种方法安装和配置位于北美大陆另一侧的 Windows 服务器应用程序。对于 Server Core 来说，这是一个可靠的选项。

对于 Windows Server 2012 Server Core，你必须意识到桌面仍然只是提示符和少量 GUI 工具。虽然有方法可以将 Server Core 的提示符发布到你的 RemoteApp，但我们不建议这样做。你仍然需要任务管理器、记事本和注册表编辑器等 GUI 工具，这些都是 Server Core 要素。

记住，远程桌面及其防火墙策略必须启用才能使用。我们将在“Server Core 的初始配置”部分提前说明。

# 使用 MMC 单元程序远程管理

管理员发现微软管理控制台是一种管理计算机的多功能方法。它的优势在于使用了 RPC 协议和集成的 Windows 身份验证，使其在管理局域网内的域计算机时变得快速高效。

你可以使用备用凭据运行身份验证。在工作站上，你可以运行远程命令注册这些凭据：

```
cdkey /bfs1 /user:administrator /pass:P@ssw0
```

你可以选择将 pass 参数留空以便提示密码。在注册凭据后，你可以通过单元程序连接到服务器。

在之前的 Windows Server 版本中，你需要安装 adminpak.msi 包才能让单元程序管理所有 Windows 服务。在 Windows Server 2012 中，adminpak.msi 包被远程服务器管理工具（Remote Server Administration Tools）取代。这些功能使其安装更加简单且更精细。在图 3.10 中，你可以通过“角色和功能向导”启用“远程服务器管理工具”。

图 3.10
安装远程管理功能

![](img/41a83208e6906a3732620203b86cea7_155_0)

如果你愿意，可以在新的 MMC 添加单元程序时连接到另一台计算机。某些单元程序允许将多个服务器添加到一个中进行集中管理。以下步骤为 Windows Server 2012 Server Core 安装创建管理 DHCP 服务的 MMC。请注意，这些步骤只有在 DHCP 服务启动并授权后才能执行。这将在“配置 DHCP 服务”部分进行讨论。

- 1. 在完整安装上安装远程服务器管理工具后，在运行提示处输入 MMC。
2. 从文件下拉菜单选择“添加/删除单元程序”。
3. 弹出“添加/删除单元程序”窗口，列出了可以添加到此 MMC 实例的可用单元程序。
4. 选择 DHCP 单元程序并点击“添加”。然后点击“确定”。
5. 在 MMC 控制台中，右键点击 DHCP 图标并选择“添加服务器”。
6. 在添加服务器窗口中，授权的 DHCP 服务器列在底部区域，如图3.11所示。选择 Server Core 实例。
7. 点击确定，选定的服务器将显示并可以进行导航，如图3.12所示。

图 3.11
向 MMC 添加 DHCP 服务器

![](img/41a83208e6906a3732620203b86cea7_156_0.png)

