

# 第 8 章创建和管理用户账户

- 结束任务 (End Task)
- 全部清除 (Clear All)
- 显示所有 (Show All)

copy 命令允许你从 PowerShell 历史窗口复制整个命令字符串，如果你需要，可以将其粘贴到你选择的编辑器中，例如记事本。你甚至可以通过按住 Ctrl 键并选择你想要的所有命令，然后复制它们：

你可能已经发现这个小窗口很快就会填满，如果你想跟踪某个操作，可能很难确定哪些 cmdlet（命令程序）属于哪个操作。因此，你可以使用开始任务 (Start Task)”、“结束任务 (End Task)”和全部清除 (Clear All)”任务。在开始之前，请确保之前图 8.79 中所示“显示所有 (Show All)”复选框未勾选。我们稍后会解释此选项的作用，但现在请保持不勾选并按照以下步骤操作：

1. 清除全部任务。
这将清空你 PowerShell 历史中的所有命令，你会得到一个干净的面板。
2. 启动任务 (Start Task)，这将为你提供一个矩形描述框，你可以在其中输入你将执行的任务的有效描述，例如，“新建用户 (New User)”。
3. 使用 ADAC 在活动目录中创建一个新用户，点击用户创建对话框上的 OK 按钮，然后结束任务 (End Task)。
4. 再次启动任务 (Start Task)，并在矩形描述框中输入“删除用户 (Delete User)”。
5. 转到 ADAC 中之前创建的用户并删除它。
6. 再次点击结束任务 (End Task)。你应该能看到命令的分组视图，如图 8.81 所示。

图 8.81
分组 PowerShell 命令

| POWHELL 历史记录 | |
| :--- | :--- |
| 搜索 (Search) | 复制 (Copy) 启动任务 (Start Task) 结束任务 (End Task) 全部清除 (Clear All) |
| Cmdlet | |
| 新建用户 (New User) | |
| -New-ADUser | |
| -DisplayName:Name="Test"GivenName="Test"Name="Test"-Path... | |
| -New-ADUser | |
| -DisplayName:Name="Test01"GivenName="Test01"Name="Test01... | |
| -Set-AccountPassword | |
| -Identity="Test01,OU,OU=Bigfirm;DC=bigfirm,DC | |
| -Enable-ADAccount | |
| -Identity="Test01,OU,OU=Bigfirm;DC=bigfirm,DC... | |
| -AccountNotDeleted=False -AllowReversiblePasswordEncry... | |
| -Set-AccountControl | |
| -Set-ADUser | |
| -ChangePasswordAtLogon=True-CN=Test01,OU,OU=Bigfirm... | |
| 删除用户 (Delete User) | |
| -Remove-ADObject | |
| -Confirm=$False -Identity="Test01,OU,OU=Bigfirm... | |

# 用于 WINDOWS POWERSHELL 的活动目录模块

你不仅可以在窗口中获得结构化的概览，如果你将命令复制到编辑器中，你会发现描述“新建用户 (New User)”和“删除用户 (Delete User)”被作为注释添加到你的脚本中，这非常有帮助。

你可以勾选的最后一个选项是“显示所有 (Show All)”。活动目录管理中心（Active Directory Administrative Center）将在 PowerShell 历史记录中显示更多命令。

7. 选择我们创建的 BigFirmUsers OU，并按 F5 刷新 OU 内容。
注意，你获得了以前没看到的新命令。这是为什么？想一下：ADAC 是构建在 PowerShell 之上的，如果你刷新了 OU，你实际上是强制 ADAC 查询该 OU。在 PowerShell 中，这是通过 `Get-ADObject` cmdlet 实现的。你可能不喜欢被 PowerShell 命令淹没，所以最好取消勾选此对象。

现在你已经对在 PowerShell 中创建对象有了初步介绍。在下一节中，你将更详细地了解基础 PowerShell。

# 用于 Windows PowerShell 的活动目录模块

用于 Windows PowerShell 的活动目录模块允许你使用微软新的外壳语言执行命令行和脚本操作。与 ADAC 类似，它仅适用于 Windows Server 2012 和 8（使用远程管理工具）。同样与 ADAC 一样，它要求在你希望管理的域中的至少一个域控制器上安装目录服务 (Directory Services)。你也可以在 Windows Server 2003 或 Windows Server 2008 上安装目录服务网关 (http://technet.microsoft.com) 以获得最佳性能。现在我们将介绍如何使用此模块管理用户和组。我们强烈建议你查看 http://technet.microsoft.com/en-us/library/ss5274.aspx 站点阅读更多关于该主题的内容。我们将涵盖常见的场景。当你第一次需要 PowerShell 时，从 Windows Server 2012 R2 启动用于 Windows PowerShell 的活动目录模块，你需要输入加载该模块：

```powershell
PS:\Users\Administrator> Import-Module ActiveDirectory
```

在 Windows Server 2012 中，你处于一个很方便的情况下，模块会自动加载。因此，当你输入一个 shell 识别为活动目录 cmdlet 的命令时，该模块将自动加载。创建用户、组、计算机、OU 等活动目录对象的的基础 PowerShell 命令在 PowerShell 中也同样有效。

# 更新帮助文件

我强烈建议在深入研究 PowerShell 3.0 / 4.0 之前更新已存储的文件。你可以通过运行 `Update-Help` 命令来实现。该命令连接到互联网，并为当前 shell 中加载的模块以及安装在计算机上的模块下载最新的帮助文件。帮助文件是 XML 文件，将自动提取并复制到相应的路径。因此，如果你没有互联网连接，可以访问 https://technet.microsoft.com/en-us/library/ss5274.aspx 了解更多关于该主题的信息。

# 创建用户 (Creating Users)

让我们从创建用户开始。

1. 清除全部任务。
这将清空你 PowerShell 历史中的所有命令，你会得到一个干净的面板。
```powershell
PS:\Users\Administrator> New-ADUser
```
2. 启动任务 (Start Task)，这将为你提供一个矩形描述框，你可以在其中输入你将执行的任务的有效描述，例如，“新建用户 (New User)”。
```powershell
PS:\Users\Administrator> -New-ADUser -DisplayName="Test" -GivenName="Test" -Name="Test" -Path "OU=Users,OU=Bigfirm,DC=bigfirm"
```
3. 使用 ADAC 在活动目录中创建一个新用户，点击用户创建对话框上的 OK 按钮，然后结束任务 (End Task)。
```powershell
PS:\Users\Administrator> -New-ADUser -DisplayName="Test01" -GivenName="Test01" -Name="Test01" -Path "OU=Users,OU=Bigfirm,DC=bigfirm" -Set-AccountPassword -Identity="Test01,OU,OU=Bigfirm,DC=bigfirm,DC" -Enable-ADAccount -Identity="Test01,OU,OU=Bigfirm,DC=bigfirm,DC" -AccountNotDeleted=$False -AllowReversiblePasswordEncryption=$true -Set-AccountControl -Set-ADUser -ChangePasswordAtLogon=$True -CN=Test01,OU,OU=Bigfirm
```
4. 再次启动任务 (Start Task)，并在矩形描述框中输入“删除用户 (Delete User)”。
```powershell
PS:\Users\Administrator> -Remove-ADObject
```
5. 转到 ADAC 中之前创建的用户并删除它。
```powershell
PS:\Users\Administrator> -Remove-ADObject -Confirm=$False -Identity="Test01,OU,OU=Bigfirm,DC=bigfirm,DC"
```
6. 再次点击结束任务 (End Task)。你应该能看到命令的分组视图，如图 8.81 所示。

# 删除用户 (Deleting User)

让我们从删除用户。

1. 清除全部任务。
这将清空你 PowerShell 历史中的所有命令，你会得到一个干净的面板。
```powershell
PS:\Users\Administrator> -Remove-ADObject
```
2. 启动任务 (Start Task)，这将为你提供一个矩形描述框，你可以在其中输入你将执行的任务的有效描述，例如，“新建用户 (New User)”。
```powershell
PS:\Users\Administrator> -New-ADUser
```
3. 使用 ADAC 在活动目录中创建一个新用户，点击用户创建对话框上的 OK 按钮，然后结束任务 (End Task)。
```powershell
PS:\Users\Administrator> -New-ADUser
```
4. 再次启动任务 (Start Task)，并在矩形描述框中输入“删除用户 (Delete User)”。
```powershell
PS:\Users\Administrator> -Remove-ADObject
```
5. 转到 ADAC 中之前创建的用户并删除它。
```powershell
PS:\Users\Administrator> -Remove-ADObject
```
6. 再次点击结束任务 (End Task)。你应该能看到命令的分组视图，如图 8.81 所示。

# 设置密码 (Setting Passwords)

说到密码，你并没有设置密码，对吧？你被强制要求这样做。然而，如果你想，可以使用 `-AccountPassword` 参数来指定密码。这里有一个问题：`-AccountPassword` 需要输入一个安全字符串，所以你不能直接添加 `My Password`。你必须在创建用户之前创建一个安全字符串。

