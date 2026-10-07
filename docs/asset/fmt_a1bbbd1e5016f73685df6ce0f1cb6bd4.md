
此命令将删除了 `Management` 组。

## 周一任务
（注：由于提供的原文文本存在大量重复，此处根据您的要求进行翻译并去重，确保不重复输出原文）

## 第 8 章 创建和管理用户账户

图 8.63
Active Directory 用户被锁定

![](img/41a83208e6906a3732620203b836cea7_471_0.png)

第二种场景是用户对他们的问题唯一了解就是他们无法登录。这可能涉及两个问题（首先）。用户可能忘记了密码，或者他们的账户可能被锁定了。你应该一石二鸟，同时处理这两种可能性。你可以打开重置用户密码的对话框，如图 8.64 所示。

图 8.64
解锁账户并重置密码

![](img/41a83208e6906a3732620203b836cea7_471_1.png)

遗憾的是，似乎没有用于解锁用户账户的命令行选项——当然，PowerShell 除外。
到此为止，我们已经涵盖了 Windows Server 2012 常用的基本用户和组管理的所有选项。现在我们将开始介绍 Windows Server 2012 的新功能。

## 使用新功能进行用户和组管理

我们在本章讨论的所有内容都适用于 Windows Server 2008 R2、Windows Server 2012 以及 Windows Server 2012 R2。Windows Server 2012 有两个与基本用户和组管理相关的重大变化：

- 微软更新了 Active Directory 管理中心 (`ADAC`)，并在 PowerShell 之上构建它。此外，控制台中集成了新功能，例如 Active Directory 回收区和细粒密码策略的 GUI。
- 微软在 `ADAC` 中加入了 PowerShell 历史记录，以便更容易管理和创建用户、组以及其他对象。
- Windows Server 2008 R2 已经原生集成 PowerShell 2.0，在管理用户方面，Windows Server 2012 并没有新的 cmdlet。尽管 Windows Server 2012 集成了全新的 PowerShell 3.0，Windows Server 2012 R2 集成了 PowerShell 4.0，但 Active Directory 领域大部分新 cmdlet 是用于管理 Active Directory 组件而不是用户。
- 然而，你可以从 `http://tinyurl.com/5otff8` 下载 Quest 的 Active Directory PowerShell 命令。这些 cmdlet 的语法与内置的 Windows Server 2012 cmdlet 类似，但在某些方面提供了更好的支持和灵活性，例如访问用户属性。在本节中，我们将介绍新的 Windows Server 2012 PowerShell cmdlet。

## Active Directory 管理中心

微软扩展并最终调整了 Active Directory 管理中心，以提供一个更以任务为导向的命令界面。据传，Active Directory 用户和计算机 (`ADUC`) 将停用，微软的重点将放在 Active Directory 管理中心。然而，在 Windows Server 2012 中，这两个工具都是可用的，且缺一不可。由于 `ADAC` 只是 PowerShell 功能的 GUI，这一点显而易见：PowerShell 值得研究此工具的力量。微软希望让重复性任务变得快速且方便，例如处理 Windows Server 2012 域控制器上的用户锁定问题。如果你安装了适用于 Windows 8 的远程 Active Directory 管理工具，也可以在 Windows 8 上使用它；参见 `http://www.microsoft.com/en-us/download/details.aspx?id=28972`。如果你已经在运行 Windows 8.1 并想要管理 Windows Server 2012 R2，请前往 `http://www.microsoft.com/en-us/download/details.aspx?id=39296`。它的加载速度比 Active Directory 用户和计算机慢一点，所以你可能会在早上和晚上觉得它很有用。

## ADAC 基础

当 `ADAC` 打开时，你就能看到我们所说的以任务为导向，如图 8.65 所示。中间面板是一个专门用于重置密码和解锁用户账户的界面。这些是 IT 人最常见的 Active Directory 任务，因此工具放在那里是合理的。

当用户拨打帮助热请求重置密码或解锁账户时，如果没有 `ADAC` 会发生什么？帮助台技术人员需要在 Active Directory 的组织单元中搜索该用户。然后他们必须右键点击该用户并执行任务。这假设帮助台工程师知道如何搜索 Active Directory。这也很耗时。如你在图 8.65 所示，使用 `ADAC`，帮助台工程师只需输入用户名和密码。“解锁账户”选项显示为灰色，因为账户尚未被锁定。`ADAC` 也让帮助台人员更容易找到对象。你可以从图 8.66 中看到，他们可以输入对象的名称进行搜索。

## 图 8.65
在 ADAC 中重置用户密码

![](img/41a83208e6906a3732620203b836cea7_473_0.png)

## 图 8.66
搜索 Active Directory 对象

![](img/41a83208e6906a3732620203b836cea7_473_1.png)

图 8.66 显示了该搜索的结果。你可以看到搜索 `SRed` 是多简单。工程师可以轻松地右键点击此用户对象以对其执行管理任务。你是否注意到你可以可以使用窗口右侧的“连接到域”控件来导航到其他域中的 OU 或容器？你可以使用 `ADAC` 一次性管理多个森林中的多个域。你可以可以使用右侧的磁盘图标保存你的查询。你可以为查询命名，然后通过点击左侧的图标再次访问。它也是一个下拉框，显示所有保存的查询。如果你选择一个，它将加载并为你执行结果。

现在我们已经涵盖了基础知识，让我们开始导航 `ADAC`。导航格有视图（默认值）和树形视图。列表视图包含一组预选的位置。这包括：

- `ADAC` 概览：你开始的地方，你可以在这里处理基本用户请求和简单搜索。
- 域：你可以从中跳转到任何 OU 或容器。
- 用户和计算机容器：你可以在这里添加任何内容。
- 全局搜索工具：你已经涵盖过了。

你可以通过右键点击导航格并添加导航节点来添加其他位置。这将打开一个窗口，你可以在其中导航 Active Directory 结构，如图 8.69 所示。

图 8.69
添加导航节点

![](img/41a83208e6906a3732620203b836cea7_476_0.png)

我们浏览了 `\BigFirm\Users` 并将该 OU 添加到了窗口右侧的控件中。

在图 8.70 中，你可以看到我们点击了确定将 `\BigFirm\Users` OU 添加到 `ADAC` 的列表视图中。现在你可以快速进入你管理用户账户的 OU，这是日常管理的另一个省力工具。任务窗格现在包含了新的操作，允许你在 OU 内执行管理操作。

## 8.68
找到未登录 15 天的所有用户

![](img/41a83208e6906a3732620203b836cea7_475_0.png)

## 图 8.70
使用导航节点

![](img/41a83208e6906a3732620203b836cea7_477_0.png)

注意，任何导航节点都会同时出现在树形视图和列表视图中。图 8.71 导航窗格中的树形视图提供了您在 `ADUC` 中习惯的更传统的方法。

## 图 8.71
ADAC 中的树形视图

![](img/41a83208e6906a3732620203b836cea7_477_1.png)

## 使用新功能进行用户和组管理 443

让我们来做一些操作。在这个示例中，你将创建一个用户。使用你刚刚在列表视图中创建的新导航节点导航到 `|BigFirm|`，并在任务面板中点击“新建 ➤ 用户”。这将打开图 8.72 所示的对话框。

## 图 8.72
在 ADAC 中创建新用户

![](img/41a83208e6906a3732620203b836cea7_478_0.png)

哇！这是一个巨大的对话框，起初看起来可能有点令人无畏。在执行任何操作之前，让我们先观察一下。首先，让我们简化一下。你只需要填写带有 ** 标记的字段即可创建用户。左侧的导航窗格提示你此窗口被分成了几个部分。你可以使用右上角的“部分 (Sections)”按钮来隐藏或显示这些部分。这允许你隐藏任何永不使用的部分。`ADAC` 会记住哪些部分是隐藏或显示的。

当你看到我们在图 8.73 中所示，我们重新组织了对话框中间的“组织 (Organization)”部分以及对话框右上角的“加密 (Encryption)”选项部分。我们已经填写了对话框创建一个名为 Greene Green 的用户。你不需要通过向导程序并打开用户属性来完成操作，而可以在这里完成所有工作。设置用户的每个常用选项在此对话框中都可用。这个初看令人无畏的窗口将缩短创建和配置用户账户的时间。

## 图 8-73
ADAC 中移除的对话框部分

![](img/41a83208e6906a3732620203b836cea7_479_0.png)

我们刚刚输入了全名和 SAM 账户名来创建此用户。如果你不输入强制性密码会发生什么？账户将被创建，但会被禁用。你将无法启用它，因为缺少密码违反了默认的域密码策略。你可以重置密码并启用账户。你应该这样做：

- 1. 输入用户详细信息。
- 2. 指定密码。
- 3. 将用户添加到组。
- 4. 点击确定。

用户被创建并被到到你所在的 OU（组织单元）中。你可能注意到并不是用户对象的每个属性或特性都是可用的。常用的属性可用，但许多其他属性并不可用。在 Active Directory 中，你可能会通过策略来配置这些属性。不过，你仍然可以访问它们。图 8.74 显示了 `ADAC` 中用户账户的属性。窗口中出现名为“扩展 (Extensions)”的新部分。这允许你查看和配置对象的高级功能。

## 图 8.74
在 ADAC 中查看用户属性

![](img/41a83208e6906a3732620203b836cea7_480_0.png)

如图 8.75 所示，我们已导航到列表并为 `BigFirmSecurity Groups` OU 创建了一个额外的导航节点。它允许在 `ADAC` 中管理组。在任务面板中点击“新建”，然后点击“组”。

## 图 8.75
用于安全组的额外导航节点

![](img/41a83208e6906a3732620203b836cea7_480_1.png)

正如图 8.76 所示，就像创建用户的对话框一样，你可以遮盖或隐藏这些部分。你现在将这样做。

## 8.76
在 ADAC 中创建新组

![](img/41a83208e6906a3732620203b836cea7_481_0.png)

你可以通过点击“部分”按钮来移除“成员所属 (Member Of)”部分，从而简化视图。让我们创建一个名为 `Helpdesk` 的组。图 8.77 显示了创建新 `Helpdesk` 组的完整对话框。同样，你不需要通过向导并在之后编辑组对象属性，可以在单个对话框中输入大量信息。执行以下操作：

- 1. 输入组名，并填写 `SamAccountName`。
- 2. 指定组类型和范围。
- 3. 勾选“防止意外删除”框，这样你就不会意外删除该组。
- 4. 指定电子邮件地址。
- 5. 编辑描述。
- 6. 将用户添加到组。
- 7. 点击确定。

## 图 8.77
在 ADAC 中创建新组

![](img/41a83208e6906a3732620203b836cea7_482_0.png)

## 图 8.78
在 ADAC 中查看用户属性

![](img/41a83208e6906a3732620203b836cea7_483_1.png)

- 结束任务 (`End Task`)
- 全部清除 (`Clear All`)
- 显示所有 (`Show All`)

`copy` 命令允许你从 PowerShell 历史窗口复制整个命令字符串，如果你需要，可以将其粘贴到你选择的编辑器中，例如记事本。你甚至可以通过按住 `Ctrl` 键并选择你想要的所有命令，然后复制它们：

你可能已经发现这个小窗口很快就会填满，如果你想跟踪某个操作，可能很难确定哪些 cmdlet（命令程序）属于哪个操作。因此，你可以使用开始任务 (`Start Task`)”、“结束任务 (`End Task)`”和全部清除 (`Clear All)`”任务。在开始之前，请确保之前图 8.79 中所示“显示所有 (`Show All)`”复选框未勾选。我们稍后会解释此选项的作用，但现在请保持不勾选并按照以下步骤操作：

1. 清除全部任务。
这将清空你 PowerShell 历史中的所有命令，你会得到一个干净的面板。
2. 启动任务 (`Start Task)`，这将为你提供一个矩形描述框，你可以在其中输入你将执行的任务的有效描述，例如，“新建用户 (`New User)`”。
3. 使用 `ADAC` 在活动目录中创建一个新用户，点击用户创建对话框上的 OK 按钮，然后结束任务 (`End Task)`。
4. 再次启动任务 (`Start Task)`，并在矩形描述框中输入“删除用户 (`Delete User)`”。
5. 转到 `ADAC` 中之前创建的用户并删除它。
6. 再次点击结束任务 (`End Task)`。你应该能看到命令的分组视图，如图 8.81 所示。

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

## 用于 WINDOWS POWERSHELL 的活动目录模块

你不仅可以在窗口中获得结构化的概览，如果你将命令复制到编辑器中，你会发现描述“新建用户 (`New User)`”和“删除用户 (`Delete User)`”被作为注释添加到你的脚本中，这非常有帮助。

你可以勾选的最后一个选项是“显示所有 (`Show All)`”。活动目录管理中心（Active Directory Administrative Center）将在 PowerShell 历史记录中显示更多命令。

7. 选择我们创建的 `BigFirmUsers` OU，并按 `F5` 刷新 OU 内容。
注意，你获得了以前没看到的新命令。这是为什么？想一下：`ADAC` 是构建在 PowerShell 之上的，如果你刷新了 OU，你实际上是强制 `ADAC` 查询该 OU。在 PowerShell 中，这是通过 `Get-ADObject` cmdlet 实现的。你可能不喜欢被 PowerShell 命令淹没，所以最好取消勾选此对象。

现在你已经对在 PowerShell 中创建对象有了初步介绍。在下一节中，你将更详细地了解基础 PowerShell。

## 用于 Windows PowerShell 的活动目录模块

用于 Windows PowerShell 的活动目录模块允许你使用微软新的外壳语言执行命令行和脚本操作。与 `ADAC` 类似，它仅适用于 Windows Server 2012 和 8（使用远程管理工具）。同样与 `ADAC` 一样，它要求在你希望管理的域中的至少一个域控制器上安装目录服务 (`Directory Services`)。你也可以在 Windows Server 2003 或 Windows Server 2008 上安装目录服务网关 (`http://technet.microsoft.com`) 以获得最佳性能。现在我们将介绍如何使用此模块管理用户和组。我们强烈建议你查看 `http://technet.microsoft.com/en-us/library/ss5274.aspx` 站点阅读更多关于该主题的内容。我们将涵盖常见的场景。当你第一次需要 PowerShell 时，从 Windows Server 2012 R2 启动用于 Windows PowerShell 的活动目录模块，你需要输入加载该模块：

```powershell
```
