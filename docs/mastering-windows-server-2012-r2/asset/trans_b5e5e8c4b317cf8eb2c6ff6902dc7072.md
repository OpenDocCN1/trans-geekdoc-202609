

-   可以使用 Ldifde .exe 实用程序在本地域中恢复组成员关系。

-   7. 输入 `quit` 退出权威还原模式，然后输入 `quit` 退出 Ntdutil。
    正常重启服务器。

    在更改已经同步的情况下执行权威性还原，需要先从备份进行非权威性还原，然后执行相同的步骤对已删除的对象执行权威性还原。

# 核心要点

    使用 Windows Server Backup 备份和恢复运行 Windows Server 2012 R2 的计算机。Windows Server Backup 作为功能安装在 Windows Server 2012 R2 中，并可用于创建各种类型的备份来保护您的服务器计算机。全备包含操作系统、关键卷以及服务器上的所有数据；而关键备份则保护操作系统所依赖的所有卷，但并不一定包含存储在服务器上的额外数据。

    **精通它** 您的服务器包含两块硬盘；第一块包含操作系统，第二块包含用户数据。您将如何使用 Windows Server Backup 保护操作系统和用户数据？

    离线对 AD 进行整理。Windows Server 2012 R2 让您能够对 AD 数据库进行离线碎片整理和完整性检查，而无需重启计算机并使用 DSRM。相反，您可以停止 AD，然后从具有提权权限的命令提示符中使用 `Ndsutil.exe` 来执行离线碎片整理和完整性检查。

    **精通它** 您想对 AD DS 数据库进行碎片整理，但不想关闭服务器并在 DSRM 模式下重启。您应该如何做？

    安装活动回收池（Active Recycle Bin）。对于某些使用 Windows Server 2008 R2 版本回收池的人来说，缺点是必须完全通过 PowerShell 进行管理。在 Windows Server 2012 R2 中，您现在拥有对回收池的 GUI 管理。

    **精通它** 您想在不使用 PowerShell 的情况下安装活动回收池。您如何实现这一目标？

    为 Active Directory 创建并恢复系统状态备份。由于域控制器包含 Active Directory 的所有数据库信息，因此恢复故障的域控制器至关重要。使用 Windows Server Backup 或命令行实用程序 `wbadmin.exe` 时，至少要执行包含系统状态的备份以保护 Active Directory。

    **精通它** 您想保护您的 Active Directory 数据免受服务器计算机完全硬件故障的影响。哪种类型的备份将提供这种保护？

# 附录

# 核心要点

章节中的每个“核心要点”部分都建议通过练习来加深技能和理解。有时只有一种解决方案，但通常鼓励您利用自己的技能和创造力来创建基于已有知识的内容，并让您探索许多可能性中的一种。

# 第 2 章：安装和升级到 Windows Server 2012 R2

    升级您的旧服务器。微软为 Windows Server 2012 R2 提供了多种升级选项。

    **精通它** 您有一台 Windows Windows 2008 x86 文件服务器。升级到 Windows Server 2012 R2 的路径是什么？

    **解决方案** Windows Server 2012 R2 仅作为 x64 版本提供。您将需要准备一台安装 Windows Server 2012 R2 的新机器。然后您将服务和数据从 Windows 2008 机器迁移到 Windows Server 2012 R2 机器。

    配置您的服务器。Windows Server 2012 R2 允许您使用服务器管理器和 PowerShell 添加或删除角色、角色服务和功能。

    **精通它** 您已开始部署 Windows Server 2012 R2。您正计划尽可能地自动化某些构建过程。您将使用什么工具来添加或删除角色、服务和功能？

    **解决方案** `Import-Module` 将添加以下 PowerShell 命令行。`Get-WindowsFeature` 将列出每个角色、角色服务和功能的状态。`Add-WindowsFeature` 将允许您安装组件，而 `Remove-WindowsFeature` 将允许您卸载组件。您可以编写 PowerShell 脚本来自动化您的配置更改。

    构建一个小型服务器群。正常安装 Windows Server 通常需要您坐在机器前并回答许多问题。这非常耗时，并且会分散管理员处理其他可能正在从事的工程或项目任务的注意力。可以采用许多替代技术。

    **精通它** 您被指示构建四台运行 Windows Server 2012 R2 的新服务器。这将是您的组织首次部署 Windows Server 2012 R2。由于几位同事正在休假，您的部门人手短缺。您希望快速且高效地完成此任务。您将如何做？

    **解决方案** 如果您有更多时间，可以研究使用 Windows 部署服务 (WDS) 准备服务器。然而，您需要快速工作。您可以从微软网站下载并安装最新的 Windows 部署工具包 (ADK)。您使用 Windows 映像管理器 (WSIM) 准备一个名为 `autounattend.xml` 的无人值服务器文件，将该文件复制到 USB 盘上，向每台服务器插入 Windows Server 2012 R2 DVD，从 DVD 启动服务器。将 USB 盘插入服务器，Windows 安装程序将从 USB 盘加载答案文件并自动完成 Windows 的安装。您在服务器上的下一步操作是更改管理员密码并登录。

# 第 3 章：Server Core 简介

    使用 Server Core 的新功能。Windows Server 2012 Server Core 是完整安装版的精简版本。主要界面是命令提示符。它减少了安全威胁和需求。

    **精通它** Windows Server 2012 Server Core 与原始的 2008 版本不同。那些关键区别是什么？它们如何影响服务器？

    **解决方案** Windows Server 2012 Server Core 允许切换到 GUI 模式。完整安装提供了许多 Core 中不具备的功能。

    安装并配置 Server Core。Server Core 的安装与完整安装相同，但许多图形功能已被移除。命令提示符是主要的界面。

    **精通它** Server Core 拥有一个执行注册表的特定脚本。该脚本的名称是什么？

    **解决方案** 脚本位于 c:\windows\system32\scedit.wsf。

    为分支机构部署设置 Server Core。分支机构部署是 Core 的一种可能场景。

# 第 4 章：Windows Server 2012 R2 网络增强

    在小型环境中安装并配置目录域服务、DNS、DHCP、文件服务和打印服务。

    **精通它** 活动目录安装向导 (DCPromo) 从命令行运行。需要什么来输入参数？

    **解决方案** DCPromo 在 Core 上需要一个答案文件。由于图形功能已被移除，该工具无法以交互方式运行。

    远程管理操作系统。Server Core 可以通过三种方式管理。远程桌面是可选，但只能使用命令提示符和提供的 GUI。MMC 节点连接到服务器的服务以使用 Windows 工具进行管理。最后，一项新服务 Windows Remote Shell 提供了命令行连接。

    **精通它** Windows Remote Shell 提供了一个 `quickconfig` 选项。系统管理员在使用它时应该注意哪些安全问题？如何解决这些问题？

    **解决方案** `quickconfig` 选项设置服务通过 TCP 端口 5985 使用 HTTP 监听请求。这意味着传输未加密。此外，服务器未经过验证，可能会导致配置错误的服务器。解决此问题的方法是在服务器客户端之间设置 IPSec。另一种方法是配置服务使用 HTTPS TCP 端口 5986，这将加密传输并验证服务器。

    理解 IPv6。从 IPv4 到 IPv6 的转变可能不会在短期内发生，IPv6 的设计者显然已经意识到两种协议必须在相同的基础设施上共存并协同工作。遗憾的是 IPv4 和 IPv6 无法原生通信，因此在过渡期间，需要一种解决方案来解决这些协议之间的通信障碍。

    **精通它** 下列哪项不是 IPv6 过渡技术？

+   a. ISATAP

+   b. DirectAccess

+   c. 6to4

+   d. Teredo

