
## 离线碎片整理活动目录

在 Windows Server 的早期版本中，你必须在 DRMM 中重启域控制器以对 AD 进行离线碎片整理和完整性检查。能够停止和重启 AD 的用处包括离线碎片整理以及在不需要重启计算机的情况下应用服务器更新。然而，在不通过 ADRM 重启计算机的情况下，不支持执行系统状态恢复。

## 停止和重启 AD DS

AD DS 的停止方式与你在 Windows 中停止任何服务完全相同，即使用服务器管理器 ➢ 工具中的“服务”加载插程序或从命令行。
你必须是域管理员组的成员才能执行这些步骤：

- 打开服务器管理器 ➢ 工具菜单，选择“服务”。
- 在详细信息窗格中右键点击“活动目录域服务”，并在上下文菜单中点击“停止”。

系统将提示你批准 AD DS 依赖的其它服务列表。

- 接受该列表，这些服务也将被停止。

当你再次停止 AD DS 时，它们将重新启动。

- 要启动 AD DS，右键点击“活动目录域服务”，然后点击“启动”。

## 停止和重启活动目录

在 Windows Server 2008 中引入的可重启的活动目录域服务（AD DS）允许你停止 AD 以对服务器进行维护，而无需在活动目录恢复模式（ADRM）下重启服务器。能够停止和重启 AD 的用处包括离线碎片整理以及在不需要重启计算机的情况下应用服务器更新。然而，在不通过 ADRM 重启计算机的情况下，不支持执行系统状态恢复。

一旦你在服务器上停止了 AD，如果你的域控制器是可控的，用户就可以继续登录域。此外，如果有另一个可用的域管理员控制器来处理你的登录，你就可以在服务器上执行任务。如果你在域控制器上停止了 AD，你必须修改 `FDSAdminLoginBehavior` 值为 1（目录服务恢复模式管理员帐户可以登录）或 2（目录服务恢复模式管理员帐户可以始终登录到服务器）。允许目录服务恢复模式（ADSR）管理员帐户无论 AD DS 是否停止都能登录到服务器并不是一个好主意，因为凭据不会根据任何密码策略进行检查。注册表值位于：

```
HKLM\System\CurrentSet\Control\Lsa\FDSAdminLoginBehavior
```

## 执行 NTDS 的离线碎片整理

这些步骤假设你已经停止了活动目录，并且正在向共享文件夹压缩数据库。如果计划向共享文件夹映射驱动器：

- 1. 打开具有权限的命令行。
- 2. 输入 `ntdsutil` 并按回车。
- 3. 激活实例 `NTDS`，按回车。
- 4. 在生成的 `ndsutil` 提示符处输入 `Files`（区分大小写），然后按回车。
- 5. 在文件维护提示符处输入 `compact` 加上路径，例如 `c:\Windows\NTDS`
- 6. 输入 `quit` 并按回车。
- 7. 输入 `quit` 退出文件维护模式，然后输入 `quit` 退出 `dsutil`。
- 8. 完成这些步骤后，重启 AD DS。

## 检查活动目录的完整性

活动目录使用与 Exchange 服务器相同的索引访问管理器（ISAM）数据库引擎，Windows Server 2012 中使用的版本称为可扩展存储引擎（ESE）。

## 第32 章 Windows Server 2012 R2 与活动目录备份及维护

有时你需要检查 AD 数据库的完整性——排除损坏问题并生成删除或虚构记录数量的报告。你可以通过两种方式检查 `Nt.dit` 文件的完整性：首先使用 `dsutil.exe` 的 `Files` 子命令，其次使用 `dsutil.exe` 的语义数据库分析子命令。尽管微软警告不要使用语义分析，但每次你使用 `Files` 下的 `integrity` 和 `recover` 命令时，它都会提示你运行语义分析。

## 执行 NTDS.dit 的完整性检查

使用 `dsutil` 的 `Files` 子命令可以让你验证数据库文件的完整性并修复发现的任何损坏。在执行完整性检查之前，应该始终使用 `recover` 命令。`recover` 命令会将所有事务刷新到数据库，确保文件是最新的。使用 `Esent exe` 对 `Ntds.dit` 数据库进行软恢复。

## 使用语义分析

`dsutil` 的 `Files` 子命令检查 `Ntds.dit` 文件是否存在普通文件损坏，使用语义分析子命令检查 `Ntds. dit` 的内部结构以确保其符合活动目录的正常语义，并输出数据库中创建的记录报告，包括删除和虚构记录。报告名为 `dsdit.bmp.x`，其中 x 是每次运行报告时都会增加的数字。

- 1. 打开具有管理员权限的命令提示符。点击“开始”，右键点击“命令提示符”，选择“以管理员身份运行”。
- 2. 输入 `ntdsutil` 并按回车。
- 3. 输入 `Activate instance NTDS` 并按回车。
- 4. 输入 `Semantic database analysis`（区分大小写），然后按回车。
- 5. 在语义检查提示符处，输入 `Go` 开始分析。使用 `Go Fixup` 运行分析并修复文件中的语义错误。
- 6. 输入 `quit` 退出语义检查模式，然后输入 `quit` 并按回车退出 `Ntdsutil.exe`。
- 7. 完成这些步骤后，重启 AD DS。

`Semantic database analysis` 子命令生成的报告文件位于运行 `Ntdsutil.exe` 的当前文件夹，通常为 `c:\username%`。系统变量 `%username%` 将替换为当前登录用户的名称。

# 捕获 Active Directory 快照

在 Windows Server 2012 R2 中，你可以使用卷量复制服务 (VSS) 创建 AD 数据库的快照。你可以将其作为离线副本查看数据，或将其作为轻量级目录访问协议 (LDAP) 目录数据库使用。快照可查看 AD DS 中的当前对象，而不会危及数据库当前状态。在 Windows Server 2012 R2 中，恢复 AD DS 中删除对象的更简单方法是 Active Directory 回收站，它将在本章稍后的“使用回收站恢复删除的对象”中进行描述。

# 创建 Active Directory 快照

你可以从具有管理员权限的命令提示符使用 `Ntdsutil exe` 工具创建 AD 快照。由于在创建快照之前不需要停止 AD DS，因此快照非常适合在不让域控制器离线状态的情况下查看其对象。

- 1. 打开具有管理员权限的命令提示符。点击“开始”，右键点击“命令提示符”，选择“以管理员身份运行”。
- 2. 输入 `ntdsutil` 并按回车。
- 3. 输入 `Snapshot` 然后按回车。
- 4. 在快照提示符处，输入 `Activate instance NTDS` 然后按回车。
- 5. 输入 `Create` 然后按回车。

快照将被创建，并显示快照的 GUID，如图 3.2 所示。

### 图 32.8 创建 Active Directory 快照

```
Administrator: C:\Windows\system32\cmd.exe - ntdsutil

Microsoft Windows (Version 6.2.7601)

(C) 2012 Microsoft Corporation. All rights reserved.

C:\Administrators\Administrator> ntdsutil

tdssnapshot: activate instance ntds

Building instance is "ntds"

Creating snapshot...

snapshot: {c66b1272-68b6-44c1-adf9-d798bc685efe} generated successfully.
```
