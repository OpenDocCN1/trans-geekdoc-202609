
组策略选项卡将在下一节中讨论。

## 练习 5.02 创建组织单位

1. 通过点击 `Start | Control Panel | Performance and Maintenance | Administrative Tools` 打开 `Active Directory Users and Groups`，然后双击 `Active Directory Users and Groups`。
2. 在控制台树中，右键单击域节点。在上下文菜单中选择 `New`，然后选择 `Organizational Unit`。
3. 在 `New Organizational Unit` 窗口中，输入 `OU` 的名称。
4. 单击 `OK` 创建 `OU`。
5. 右键单击新的 `OU` 并从菜单中选择 `Properties`。
6. 在 `General` 选项卡上，输入描述以说明 `OU` 的用途（参见 [图 5.10](#B9781931836944500118.xhtml#f0055)）。
![图 5.10 OU 属性](images/B9781931836944500118/f05-10-9781931836944.jpg)
图 5.10 OU 属性
7. 单击 `Managed By` 选项卡（参见 [图 5.11](#B9781931836944500118.xhtml#f0060)）。单击 `Change` 按钮。从 `Users and Groups` 窗口中选择一个用户帐户来管理 `OU`。
![图 5.11 由...管理的属性](images/B9781931836944500118/f05-11-9781931836944.jpg)
图 5.11 由...管理的属性
8. 单击 `Group Policy` 选项卡（参见 [图 5.12](#B9781931836944500118.xhtml#f0065)）。单击 `New` 按钮创建新的 `GPO`。
![图 5.12 组策略属性](images/B9781931836944500118/f05-12-9781931836944.jpg)
图 5.12 组策略属性
9. 通过输入新名称重命名 `GPO`。
10. 右键单击 `GPO`，并从菜单中选择 `No Override`。注意 `No Override` 列中 `GPO` 旁边的复选标记（参见 [图 5.13](#B9781931836944500118.xhtml#f0070)）。
![图 5.13 不覆盖选项](images/B9781931836944500118/f05-13-9781931836944.jpg)
图 5.13 不覆盖选项
11. 单击 `Edit` 按钮。从 `GPO` 窗口中，双击 `User Configuration | Administrative Templates | Start Menu & Taskbar`。双击 `Remove Favorites menu from Start Menu`。在打开的窗口中，单击 `Enable` 以从开始菜单中删除收藏夹。
12. 单击 `Explain` 选项卡。这定义了您的操作的影响。
13. 单击 `OK` 关闭 `Remove Favorites menu from Start Menu` 窗口。
14. 关闭 `GPO` 窗口。
15. 选中 `Block Inheritance` 选项。
16. 右键单击 `GPO` 并从菜单中选择 `Disable`。
17. 关闭所有窗口。

### 将组策略应用于 OU

创建 `OU` 的基本原因之一是向其应用 `GPO`。创建 `OU` 后，您可以创建新的 `GPO` 或应用现有的 `GPO`。在 `OU Properties` 窗口中找到的 `Group Policy` 选项卡是 `OU` 属性中最重要的选项卡。在此创建、关联和编辑将影响 `OU` 的 `GPO`。此选项卡具有以下按钮：
■ `New`
■ `Add`
■ `Edit`
■ `Options`
■ `Delete`
■ `Properties`
`New` 按钮将创建新的 `GPO`。单击时，需要提供新 `GPO` 的名称。
`GPO` 创建后，使用 `Edit` 按钮编辑其配置设置。`GPO` 分为两组配置设置，`Computer` 和 `User`。每种设置进一步由三个设置类别定义：`Software`、`Windows` 和 `Administrative Templates`。这些是您用来控制 `OU`（或应用 `GPO` 的其他单元）的设置。
`Add` 按钮可让您创建 `Group Policy Object Link`。链接可让您将现有 `GPO` 应用于 `OU`。您将能够在域中导航以找到现有 `GPO` 并将其链接到新的 `OU`。
`Options` 按钮提供两个选项：`No Override` 和 `Disable`。`Disable` 非常直观；它将禁用 `GPO`。`No Override` 选项由父 `OU` 的 `GPO` 使用，以确保 `GPO` 中的设置不会被子 `OU` 的 `GPO` 覆盖。可以通过右键单击 `GPO` 并从上下文菜单中选择选项来访问这些选项。
`Properties` 按钮打开 `GPO` 的 `Properties` 窗口。`Properties` 窗口有三个选项卡：`General`、`Links` 和 `Security`。`General` 选项卡显示摘要部分和禁用部分。摘要部分显示 `GPO` 信息，例如创建日期、上次修改日期、修订版本、域名和 `GPO` 的唯一名称。禁用部分允许您禁用一或两组配置设置。您可以禁用 `Computer Configurations Settings` 和/或 `User Configuration Settings`。禁用 `GPO` 中未使用的部分可提高性能。`Links` 选项卡显示使用该 `GPO` 的所有站点、域或 `OU`。它有一个查找按钮，可帮助您定位 `GPO` 的应用位置。`Security` 选项卡设置 `GPO` 的权限。
通过 `Security` 选项卡设置的权限控制用户或用户组对 `GPO` 的访问级别。权限级别如下：
■ `Full Control`
■ `Read`
■ `Write`
■ `Create Child Objects`
■ `Delete Child Objects`
■ `Apply Group Policy`
最后一个按钮是 `Delete`，用于删除 `GPO`。
`Group Policy` 选项卡底部是 `Block Inheritance` 选项。`Block Inheritance` 将阻止原本从父 `OU` 继承的 `GPO` 设置。这使子 `OU` 能够控制接受哪些来自父 `OU` 的设置。但是，如果父级设置了 `No Override` 且子级设置了 `Block Inheritance`，则 `No Override` 设置优先。
![b05-06-9781931836944](images/B9781931836944500118/b05-06-9781931836944.jpg)考试日提示
`GPO` 与 `OU` 之间的关系很容易成为考试题目。请特别注意 `No Override` 设置和 `Block Inheritance` 设置的效果。

#### 委派 OU 的控制权

对 `OU` 的控制委派是为了减轻网络管理员执行 `OU` 的例行功能的任务。通常，`OU` 中拥有帐户的管理人员或主管将更好地了解属于该 `OU` 的用户和计算机相关的日常任务，因此能够很好地照顾 `OU`。委派是一个简单的过程。向导将引导您完成该过程。`Delegation of Control Wizard` 将在章节后面讨论。
在决定要将控制权委派给谁之后，决定要委派哪些任务。您可以委派对用户和组以及 `Group Policy Links` 的管理控制。您可以将不同活动的控制权传递给组织中的不同人员。
具体来说，委派级别如下：
■ `Create, delete, and manage user accounts`
■ `Reset passwords on user accounts`
■ `Read all user information`
■ `Create, delete, and manage groups`
■ `Modify the membership of a group`
■ `Manage Group Policy Links`
如您所见，委派可以减少网络管理员所需的日常管理任务量。
![b05-07-9781931836944](images/B9781931836944500118/b05-07-9781931836944.jpg)考试日提示
将控制权委派给他人的管理任务很可能在考试中涉及。它很可能是一个直接的场景，要求您将控制权委派给另一用户或用户组。请注意可以委派的控制级别。

## 为您的组织规划 OU 结构和策略

`OU` 结构可以让您的生活更轻松——也可以相反。如果您花时间规划结构和实施，您的生活变得更轻松的机会就会增加，并且您可以专注于网络管理的许多方面，而无需执行 `OU` 的日常维护和用户问题，例如重置密码。您的策略应包括以下内容：
■ 要创建哪些 `OU`
■ 需要应用哪些策略来满足 `OU` 的安全要求

