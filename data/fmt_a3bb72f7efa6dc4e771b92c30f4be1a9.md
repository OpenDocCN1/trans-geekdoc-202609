
`repadmin <command> <arguments>`

当使用 `replsingleobj` 命令或开关时，语法如下：

```
repadmin /replsingleobj sourceDC destinationDC ObjectDN
```

源域控制器和目标控制器都通过其名称（例如 `BFI`）或其完全限定域名名（例如 `BF1.Bigfirm.com`）来标识。
区分名称（DN）遵循 LDAP DN 规则。例如，在 `Bigfirm.com` 域的 `Sales` OU 中名为 `TestCPU` 的计算机将具有以下 DN：`DN=TestCPU,OU=Sales,DC=bigfirm,DC=com`。
如果 DN 包含从 `BF1` 到 `BF2` 的任何对象，你可以使用以下命令：
该命令在书中跨越了多行，但在输入时应在单行内：

```
repadmin /replsingleobj BF1.bigfirm.com BF2.bigfirm.com CN=TestCPU,OU=Sales,DC=bigfirm,DC=com
```

## 配置客户端访问最近的站点

Windows Server 2012 R2 提供的一项强大功能是能够教导客户端，如果其站点内的域控制器宕机，应该访问哪个站点。考虑图 22.20 所示的 `Bigfirm.com` 企业。

图 22.20
最近的站点

![](img/41a83208e6906a3732620203b836cea7_1181_0.png)

每个站点至少有一个域控制器，通常用户会登录到其所在站点的域控制器。但如果跨区站点的域控制器故障了怎么办？
你可能不希望用户使用较慢的连接登录到远程办公室站点的 DC。然而，如果未启用“最近的站点”，这正是可能会发生。DC Locator 服务首先尝试在与客户端相同的站点中查找 DC。如果失败，除非启用了“最近的站点”设置，否则它将查找任何位置的任何 DC。

“最近站点（closest site）”一词有点是误导。Active Directory 并没有距离的概念，但它确实理解在站点链接属性中配置的成本（cost）。虽然最近站点可能拥有最快的 WAN 链路并配置了最低成本，但组织的配置可能会有所不同。

例如，远程办公室可能距离跨区办公室一英里，但距离总部五英里。远程办公室与总部之间的链路成本为 25，而跨区办公室与远程办公室之间的链路成本为 100。如果使用距离，跨区办公室将被视为最近的；但如果考虑成本，总部将被识别为最近的站点，因为它的成本最低。

### PRE-WINDOWS V 客户端不支持“最近的站点”功能

“最近的站点”功能适用于 Windows 7、Windows 8 以及 Windows Server 2008 或更高版本的客户端和服务器。此功能不会影响 Windows XP、Windows Server 2003 或更早版本客户端的行为。

你可以配置 Windows 7、Windows 8 和 Windows Server 2012 R2 服务器使用成本来定位最近的站点。以下是配置此功能的两种方法：

- 组策略
- 修改注册表

### 使用组策略配置最近的站点

如果你想配置多个客户端使用成本来确定哪些站点是最近的，你可以通过修改组策略来实现。你可以使用以下步骤配置域中的所有客户端。

| 站点、域或 OU |
| :--- |
| 以下步骤将引导你通过修改默认域策略来配置域中的所有客户端。然而，你可以稍微修改这些步骤，以创建或更改任何 GPO 并将其链接到站点、域或组织单元 (OU)，取决于你想影响哪些计算机。 |

1. 通过选择服务器管理器 > 组策略管理 启动组策略管理控制台。
2. 在“森林 > 域 > 域名称”文件夹中找到“默认域策略”对象。
3. 右键点击“默认域策略”，点击“编辑”。

## 第 22 章 添加更多位置：Active Directory 中的站点

4. 浏览到“计算机配置 > 策略 > 管理模板 > 系统 > Net Logon > DC Locator DNS 记录策略”文件夹。
5. 双击“最近的站点”设置，并点击“启用”。你的显示将与图 22.21 类似。点击“确定”。

![](img/41a83208e6906a3732620203b836cea7_1183_0.png)

6. 关闭组策略管理编辑器和组策略管理控制台。

你可以等待组策略通过正常的刷新周期生效，或者使用命令行中的 `gpupdate /force` 命令来更新任何单个客户端。

### 通过注册表配置最近的站点

组策略允许你配置一次设置并影响许多客户端。但是，如果你只想让单个客户端使用最近的站点，可以修改注册表。

> 修改注册表时要小心

在任何修改注册表时你都应该保持谨慎。错误地编辑注册表可能会严重损坏你的系统。建议在修改注册表之前备份计算机上的所有数据。

#### 配置客户端访问最近的站点

你可以使用以下步骤为 Windows 7 或 8 启用“尝试最近站点（Try Closest Site）”设置。

1. 点击开始，在启动框中输入 `regedit` 并回车启动注册表编辑器。
2. 选择 `HKEY_LOCAL_MACHINE`。
3. 浏览到 `System\CurrentSet\Services\Netlogon\Parameters`。
4. 寻找名为 `Closest Site` 的键。如果不存在，按照以下步骤创建：
   a. 右键点击 `Parameters`，选择新建 > DWORD (32 位 值)。
   b. 将键重命名为 `Closest Site`。
5. 双击 `Closest Site`。将值更改为 `1`。你的显示将与图 22.22 类似。

图 22.22
修改注册表
![](img/41a83208e6906a3732620203b836cea7_1184_0.png)

6. 点击“确定”。关闭注册表编辑器。

提醒一下，此设置仅在连接与客户端相同的站点时被引用。如果此键值为 1，DC Locator 进程将使用成本值。

### 使用 PowerShell

PowerShell 命令在本书的多个章节中介绍，因此你已经见过很多。本节重点介绍你可以使用并组合从 Active Directory 获取信息的少量命令。它包含了 PowerShell 内置的 AD 搜索工具的基础，如果你的组织足够大并支持多个站点，这将非常有用。

#### 使用区分名称

这些步骤涉及区分名称（DN），它们在第 7 章中有更深入的讨论，在本章早期也提到过。在动态创建 DN 之前需要一些练习，你会发现创建和识别 DN 非常有用，特别是在编写脚本或深入研究 Active Directory 时。

1. 启动 Windows PowerShell 实例。
2. 使用以下命令通过创建一个代表域的变量来获取有关环境的一些信息。它会将域的 DN 填充到变量 `$dom`。注意 `LDAP` 必须大写：
   `$dom=[adsi]LDAP://RootDSE`
3. 使用以下命令使用 `$dom` 变量查询域的任何信息：
   a. 查看根域的命名上下文：
   `Write-Host $dom.RootDomainNamingContext`
   结果：`DC=bigfirm,DC=com`
   b. 查看森林中所有域的命名上下文：
   `Write-Host $dom.NamingContexts`
   结果：`DC=bigfirm,DC=com`
   c. 查看默认命名上下文（或你的域的部分 DN）：
   `Write-Host $dom.DefaultNamingContext`
   结果：`DC=bigfirm,DC=com`

有时你可能不知道用户的区分名称（distinguished name，简称 DN），因为你不知道他们所在的组织单元（OU）。如果你知道账户的某些信息（例如显示名称），可以使用内置的活动目录目录搜索器（Active Directory searcher）来检索区分名称。此示例假设显示名称为“名字.点.姓氏”（例如 John Smith）。你只需要知道用户的名和姓即可进行搜索。

1. 首先，使用此行代码为过滤器（你的搜索项目）创建一个变量：
   `$filter = "(&(objectCategory=User)(DisplayName=John.Smith))"`
   使用通配符 `*` 来查找所有实例（例如 John.Smith2 和 John.Smith3）。
2. 接下来，使用此行代码通过过滤器创建搜索器实例：
   `$Searcher = New-Object System.Services.DirectorySearcher($Filter)`
3. 最后，使用此命令查找所有实例：
   `Searcher.FindAll()`

将显示所有匹配此显示名称的账户的 DN。你甚至可以将之前的代码制作成脚本以接受参数（例如用户名）。

4. 将以下行输入到任何文本编辑器（如记事本）中，并将其保存到 `C:\Scripts` 文件夹中命名为 `FindUser.ps1`
第一行标识将接受的参数，第二行在过滤器中使用该参数。其余部分如下：

```
Param($filterName)

$filter = "(&(objectCategory=User)(DisplayName=$filterName))"

$Searcher = New-Object System.Services.DirectorySearcher($filter)

$Searcher.FindAll()
```
