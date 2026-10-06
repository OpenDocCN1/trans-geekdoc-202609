

# 第 16 章在 Windows Server 2012 R2 网络上共享打印机

如果你在服务器上运行 Server Core 并希望将此服务器作为打印服务器（包括打印和文档服务），你需要激活 PowerShell。在 Server Core 命令行中，输入 `PowerShell`。注意，命令行以 `PS` 开头，这提示你正处于 PowerShell 应用程序中。

然后，在 Server Core 命令行中输入以下命令：

```
PS:\Users\Administrator>import-module ServerManager
PS:\Users\Administrator>add-WindowsFeature Print-Server
```

稍等片，你将看到安装结果，如图 16.15 所示。

# 图 16.15
使用 PowerShell 在 Server Core 上安装打印服务器

![](img/41a83208e6906a3732620203b836cea7_881_0.png)

## 使用 GET-WINDOWSFEATURE 获取已安装的角色

你可以使用 `Get-WindowsFeature` get来为你的 Server Core 安装提供配置信息。这还能让你获取想要添加的所有角色的正确拼写和语法。例如，打印机角色被标识为 `Print-Services`。

此时，你需要做一个决定。你是想从命令行还是图形界面 GUI 管理 `Print-Services` 角色？如果你想通过 GUI 管理（这要直观得多），可以配置 Server Core 以进行远程管理。第 17 章“远程服务器管理”将介绍如何操作。

为了进行打印服务器管理，必须在 Server Core 上启用网络发现。你可以通过以下 PowerShell 命令启用它：

```
PS:\Users\Administrator>netsh advfirewall service set printfile enabled
```

你还需要使用以下命令允许服务器通过远程服务器上的 MMC 进行管理。尽管它在书中显示为两行，但请将其作为单条 PowerShell 命令输入。

```
PS:\Users\Administrator>netsh advfirewall firewall rule group="Remote Administration" new enable=yes
```

一旦为 Server Core 配置了远程管理，你就可以从安装了完整操作系统的服务器对其进行远程管理。例如，你可能有 10 台运行 Server Core 的文件和打印服务器，但只有一台安装了完整操作系统的中央服务器，你可以用它来远程管理所有服务器。

要向 MMC 添加打印服务器，右键点击“打印服务器”，并选择“添加/删除服务器”。在“添加/删除服务器”页面上，输入远程服务器的名称。你也可以点击“浏览”。如果网络发现已关闭，系统会提示你开启它以便找到其他计算机。选择你的服务器，并点击“选择”按钮。

如果你需要在 Server Core 命令行中执行任何任务，有几个工具可以提供帮助。

## PowerShell Cmdlet 参考

如果你计划在 Windows Server 2012 R2 上使用 PowerShell，拥有一份用于管理打印机任务的 cmdlet 快速参考查表将对你非常有益。使用这些 cmdlet 还能让你免于使用脚本管理打印机和驱动程序的麻烦。

- Add-Printer: 向指定的计算机添加打印机。
- Add-PrinterDriver: 在指定的计算机上安装打印机驱动程序。
- Add-PrinterPort: 在指定的计算机上安装打印机端口。
- Get-PrinterConfiguration: 获取打印机的配置信息。
- Get-Printer: 获取指定计算机上的打印机列表。
- Get-PrinterDriver: 获取指定计算机上的打印机驱动程序。
- Get-PrinterPort: 获取指定计算机上的打印机端口。
- Get-PrinterProperty: 获取打印机的属性。
- Get-PrintJob: 获取打印机上的打印任务。
- Remove-Printer: 从指定的计算机上删除打印机。
- Remove-PrinterDriver: 从指定的计算机上删除打印机驱动程序。
- Remove-PrinterPort: 从指定的计算机上删除打印机端口。
- Remove-PrintJob: 删除打印机上的打印任务。
- Rename-Printer: 重命名打印机。
- Restart-PrintJob: 重启打印机上的打印任务。
- Resume-PrintJob: 恢复已挂起的打印任务。
- Set-PrinterConfiguration: 设置打印机的配置。
- Set-Printer: 更新现有打印机的设置。
- Set-PrinterProperty: 修改打印机的属性。
- Suspend-PrintJob: 挂起打印机上的打印任务。

## 将打印机部署到所有计算机

一旦你将打印机添加到服务器，你就希望它们对客户端可用。你可以通过三种方式实现：

- 手动
- 通过 Active Directory 搜索
- 通过组策略

如果你的计算机在 Active Directory 域中，你可能会使用第二或第三种方法来实现自动化。在接下来的章节中，你将学习如何使用这三种方法部署打印机。

## 手动向客户端添加打印机

当你将打印机添加到打印服务器后，向客户端添加打印机（并自动安装正确的驱动程序）相对简单。以下步骤显示了如何在 Windows 7 客户端上添加打印机：

1.  Windows 7，选择开始 > 打印机。
2. 点击“添加打印机”。
3. 选择“添加网络、无线或蓝牙打印机”。系统将搜索网络上的可用打印机。
4. 选择“我需要的打印机不在列表中”。
5. 点击“按名称选择共享打印机”，并输入路径。
6. 选择所需的打印机。
7. 点击“下一步”。

## 将打印机部署到所有计算机

Active Directory 是一个可以搜索的海量数据库。但是，默认不会列出打印机。要启用此功能，右键点击打印机，访问共享选项卡，勾选“在目录中列出此打印机”复选框如图 16.16 所示。

# 图 16.16
连接共享打印机

![](img/41a83208e6906a3732620203b836cea7_883_0.png)

## 字符串搜索

注意不需要输入模型的完整名称。这非常有用，因为打印机型号的长度往往很像小王室成员的名字。相反，Active Directory 查找的是字符串匹配，因此任何以 HP 开头的模型都会被找到。

