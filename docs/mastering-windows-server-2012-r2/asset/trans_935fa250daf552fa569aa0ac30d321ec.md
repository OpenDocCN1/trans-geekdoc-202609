

# 图 2-45

PowerShell
Get-WindowsFeature

![](img/41a83208e6906a3732620203b836cea7_100_0.png)

让我们验证安装情况。再次运行 PowerShell 并使用 `Get-WindowsFeature` 命令行来检查结果，如图 2.46 所示：

```
PS C:\Windows\Administrator> Get-WindowsFeature
```

# 图 2.46

检查我们
已安装的角色

![](img/41a83208e6906a3732620203b836cea7_100_1.png)

# 第 2 章安装和升级 WINDOWS SERVER 2012 R2

你请求的角色和角色服务被标记为 X，这意味着它们已经安装。。你还可以看到 FTP 服务所需的各种功能也已安装。你可以通过启动服务器管理器（Server Manager）来确保结果与使用 GUI 获得的结果一致。

任何对命令行管理感到一丝畏惧的人可能会产生一丝兴趣。

如果你想获取服务器配置的文本报告，只需运行一个命令即可。它会将报告导出到名为 `C:\InstalledFeatures.txt` 的文件中。

```
PS C:\Administrator> get-windowsfeature C:\InstalledFeatures.txt
```

一个很棒的功能是，你可以在不实际运行命令的情况下查看运行后会发生什么。你可以通过添加 `-whatif` 标志来实现这一点：

```
Add-WindowsFeature -name
```

如果你打算添加“File-Services”角色和“FS-Resource-Manager”角色服务，以下是运行该命令后会发生的情况：

```
PS C:\Users\Administrator> add-windowsfeature File-Services,FS-Resource-Manager -whatif
```

如果: 正在检查是否以 'WhatIf' 模式运行。
如果: 正在对目标 "[File Services Resource Manager" 上执行操作 'Add-WindowsFeature'。
如果: 正在对目标 "[File Services File Server" 上执行操作 'Add-WindowsFeature'。
如果: 安装完成后，此服务器可能需要重启。

得益于 `-whatif` 标志，服务器上没有发生任何变化。注意，你可能需要重启？知道在执行此命令后你需要进行重启是很有用的。这将让你能够为重启以及重启此机器托管的任何服务制定计划。

# 使用 PowerShell 在多个服务器上安装角色

想象你正在设置许多更多的角色、角色和服务功能。你可以将所有内容封装到这一个脚本中并运行它。通过 PowerShell 中的该命令行选项，你可以像 Microsoft System Center Configuration Manager 那样自动配置数百或数千台服务器。你现在应该理解 PowerShell 的威力。你可以轻松地为服务器部署和配置项目节省数小时的工作时间。

在深入设置脚本安装之前，你首先需要检查是否被允许运行脚本。打开 PowerShell 并运行以下命令行工具：

```
PS C:\Users\Administrator> get-executionpolicy
Restricted
```

# 使用服务器管理器配置您的服务器

此命令显示我们的服务器上禁用了脚本。这是 PowerShell 的默认设置。如果你的服务器上禁用了脚本，若要运行脚本，你必须运行此命令：

```
PS C:\Users\Administrator> set-executionpolicy unrestricted
```

# 更改执行策略

执行策略可以保护你免受你不信任的脚本的影响。更改执行策略可能会让你暴露在 `about_Execution_Policies` 帮助主题中所述的风险中。你想要更改执行策略吗？

[Y] 是 [N] 否 [S] 挂起 [?] 帮助（默认值为 "Y"): Y

你可以通过运行 Get-ExecutionPolicy 命令来验证更改：

```
PS C:\Users\Administrator> get-executionpolicy
```

你的服务器现在已设置为允许所有脚本。出于安全考虑，我建议在完成脚本安装后将其更改为 `Restricted`（受限制）。

让我们看看如何在 PowerShell 中使用脚本。当你想要向多个服务器添加角色、角色服务或功能时，就会发现它的作用。你需要一个配置文件来实现这一点。为了演示如何进行操作，我们将使用“添加角色和功能”向导，并将配置页导出到文件（见图 2.47）。

由于前面的页面已经解释了如何使用向导添加角色，请继续添加“远程桌面服务”角色，但在到达角色配置页面时停止。在确认页面上（向导的最后一页），页面底部下方有一个链接，可以将配置导出到文件（见图 2.47）。

# 图 2.47
将角色导出到配置 XML 文件

![](img/41a83208e6906a3732620203b836cea7_102_0.png)

# 第 2 章安装和升级 WINDOWS SERVER 2012 R2

将文件保存为 `RemoteDesktopConfig.xml` 到 C 盘上的任何方便位置。如果你想通过 Internet Explorer 查看它像什么样，图 2.47 是一个部分截图。你可以取消向导并安装！

