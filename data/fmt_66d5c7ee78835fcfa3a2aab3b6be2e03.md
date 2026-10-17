
## sudo 权限

Linux 机器上的`sudo`权限允许特定用户以`root`用户或本地机器上的其他用户身份直接运行命令。这在大多数环境中是必需的，尤其是对于系统管理员和其他必要的系统任务。如果范围和测试得当，`sudo`的使用可以高效且安全。

可以为`sudo`程序启用和利用多种插件策略，最常见的是`sudoers`文件。该文件位于`/etc/sudoers`，利用存储在那里的策略来决定在`sudo`命令中允许谁以及允许发生什么。该策略可以定义使用某些命令是否需要密码。

要列出当前账户可以使用`sudo`执行的操作，请运行下面的命令（这里使用小写的 “L” 作为开关）。这将列出当前主机上允许和禁止该用户执行的命令。这还将进一步揭示哪些命令被允许以及以何种格式。

```text
$ sudo -l
Matching Defaults entries for chris on MSI:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:
    /bin\:/snap/bin

User chris may run the following commands on MSI:
    (ALL : ALL) NOPASSWD: ALL
```

要分析`sudo -l`命令的结果，我们可以看到用户账户`chris`可以使用`sudo`运行所有命令，而无需输入密码。为了进一步细化`sudo`配置列表所显示的信息，我们可以指定`-ll`选项（即小写字母“L”，共两个）。这有助于进一步列出`sudo`输出信息的含义。

```
$ sudo -ll
Matching Defaults entries for chris on MSI:
    env_reset, mail_badpass,
secure_path=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:
/bin:/snap/bin

User chris may run the following commands on MSI:

Sudoers entry:
    RunAsUsers: ALL
    RunAsGroups: ALL
    Options: !authenticate
    Commands:
        ALL
```

请注意，这里并没有显示出额外的权限，只是这些信息以更易于人类阅读的格式呈现。我们可以看到，我们可以以任何用户和任何组的身份运行所有命令（`ALL`），并且无需验证身份。这是一种自定义配置，旨在允许用户运行`sudo`命令时，无需在每次执行特定命令时输入密码。

显然，这是一个极其不安全的`sudo`策略文件。因为任何能够访问该用户的人，即使不知道用户密码，也能以`root`用户身份运行命令。一旦获得`root`权限，他们就可以获取密码哈希、SSH 密钥以及其他可能存储于其他用户账户中的敏感信息。但请记住，`sudo -l`命令只会列出当前用户的`sudo`权限，而不是系统上其他所有用户的权限。

要知道主机上还有哪些其他用户可以运行`sudo`命令，我们需要查询`/etc/group`文件，看看谁在`sudo`组中。这表示该指定用户将有权使用机器上的`sudo`命令。为了识别这一点，我们可以使用`grep`搜索`/etc/group`文件中的`sudo`组，并查看其中包含哪些成员。通过搜索`sudo`组并将其打印到屏幕上来完成：

```
$ grep '^sudo:.*$' /etc/group
sudo:x:27:chris
```

要对`sudoers`文件进行修改，我们应该确保使用`visudo`命令，而不是直接编辑该文件。我们需要先获得合法的`sudo`访问权限才能进行这些修改！使用`visudo`命令时，`sudoers`文件会被编辑，并检查其中可能导致`sudo`配置损坏的差异。直接编辑`sudoers`文件无法保护系统免受策略中错误配置的影响，并可能导致用户被锁定在系统之外。此外，配置错误的`sudoers`策略会阻止我们再次通过`sudo`进入文件进行修改，很可能需要启动到“单用户”模式才能恢复。简而言之，请使用`visudo`命令，而不是直接编辑`/etc/sudoers`。

## 在这里，谁可以更改我们的 Windows？

Windows 利用组来帮助跟踪和管理哪些人应该被允许对机器拥有管理控制权。与枚举本地用户类似，我们可以使用`net localgroup`命令来确定哪些用户位于`Administrators`组中。这用于找出哪些用户账户在机器上拥有管理访问权限，从而帮助我们取得完全控制。

下面的命令可用于任何 Windows 机器，以枚举哪些用户属于此组：

```
> net localgroup Administrators
Alias name          Administrators
Comment             Administrators have complete and unrestricted access to the computer/domain

Members

---------------------------------------------------
Administrator
chris
The command completed successfully.
```

上述命令的输出显示，用户`Administrator`和`chris`被设置为`Administrators`组的成员。

上述活动来自较早的 Windows 命令提示符时代。在过去十年左右，微软一直在大力推动 PowerShell 尽可能取代 CMD。PowerShell 是一种非常高效的语言，但如果编程不是你的强项，它也可能很难学习。到目前为止，我们已经在 PowerShell 中介绍了一些有用的内容，接下来将继续探索更多。

PowerShell 内置了用于枚举本地组和本地用户的 cmdlet，而无需导入新模块，这与本章前面介绍的`ActiveDirectory`模块类似。要探索本地组和用户，我们可以使用`Get-LocalGroup`、`Get-LocalGroupMember`和`Get-LocalUser`这些 cmdlet。枚举组就像执行`Get-LocalGroup`一样简单。

```powershell
PS C:\Users\mboone2f> Get-LocalGroup

Name                           Description
----                           -----------
Access Control Assistance Operators Members of this group can remotely...
Administrators                  Administrators have complete and u...
Backup Operators                Backup Operators can override secu...
Cryptographic Operators         Members are authorized to perform ...
Device Owners                   Members of this group can change s...
Distributed COM Users           Members are allowed to launch, act...
Event Log Readers               Members of this group can read eve...
Guests                          have the same access as mem...
Hyper-V Administrators          Members of this group have complet...
IIS_IUSRS                       Built-in group used by Internet In...
Network Configuration Operators Members in this group can have som...
Performance Log Users           Members of this group may schedule...
Performance Monitor Users       Members of this group can access p...
Power Users                     Power Users are included for backw...
Remote Desktop Users            Members in this group are granted ...
Remote Management Users         Members of this group can access W...
Replicator                      Supports file replication in a domain
System Managed Accounts Group   Members of this group are managed ...
Users                           Users are prevented from making ac...
```

我们看到该 cmdlet 返回了大量组，但其中有一些非常有趣的名字。我们当然对`Administrators`组感兴趣，可以使用`Get-LocalGroupMember`cmdlet 来请求该组的成员。

要查询这一点，我们可以使用下面的命令来显示此组的所有成员。

```powershell
PS C:\Users\mboone2f> Get-LocalGroupMember -Group Administrators

ObjectClass Name                         PrincipalSource
----------- ----                         ---------------
User        DESKTOP-CHRIS\Administrator Local
User        DESKTOP-CHRIS\chris         Local
```

在上面的例子中，我们可以看到有两个本地账户是这台特定机器上`Administrators`组的成员。这些账户被特别授予了本地计算机的管理级访问权限，而不是对整个域的管理权限。然而，很多时候，本地计算机上可用的某些信息可以用于进一步利用权限深入到域中。

## Active Directory 管理员

要搜索并识别 Active Directory 上的管理级账户，我们可以利用`ActiveDirectory`模块中的几个不同 PowerShell cmdlet。第一个`Get-ADGroupMember`利用`ActiveDirectory`模块查找指定组中的条目。通过将其传给`Administrators`组，我们可以识别谁和哪些组是成员，并确保我们要求它递归运行！这很好地表明了域中谁会成为有价值的攻击目标。

```powershell
PS C:\Users\mboone> Get-ADGroupMember -Identity Administrators -Recursive

SamAccountName     : Domain Admins
SID                : S-1-5-21-711274202-1094311838-204602813-512
DistinguishedName  : CN=Domain Admins,CN=Users,DC=goblins,DC=local
Name               : Domain Admins
ObjectClass        : group
ObjectGuid         : 86a6d36c-a866-4226-add7-d723682f4598
PropertyNames      : {distinguishedName, name, objectClass,
                     objectGUID...}
AddedProperties    : {}
RemovedProperties  : {}
ModifiedProperties : {}
PropertyCount      : 6

SamAccountName     : Enterprise Admins
SID                : S-1-5-21-711274202-1094311838-204602813-519
DistinguishedName  : CN=Enterprise Admins,CN=Users,DC=goblins,DC=local
Name               : Enterprise Admins
ObjectClass        : group
ObjectGuid         : ca5a8211-1e97-4f4e-a938-2c6577c6a03e
PropertyNames      : {distinguishedName, name, objectClass,
                     objectGUID...}
AddedProperties    : {}
RemovedProperties  : {}
ModifiedProperties : {}
PropertyCount      : 6

SamAccountName     : Administrator
SID                : S-1-5-21-711274202-1094311838-204602813-500
```

## 为所有人提供备份

对于系统管理员来说，通常会在`/tmp`或`/var`等世界可读目录中创建 tarball 或其他类型的归档文件，下载备份后将归档文件留在本地系统上。这是因为系统管理员关注运营的正常运行时间和弹性，而很少关注系统上的本地攻击者可能访问到什么。我们能责怪他们吗？也不能太多，考虑到系统管理员专注于运营能力——这正是我们专业知识发挥作用的地方。

沿着同样的思路，系统管理员通常非常擅长检查并禁用那些已知不应面向公众的高风险服务。例如，许多人都很擅长确保 3306（MySQL）或 1433（MSSQL）等数据库端口无法通过互联网访问。然而，根据作者的亲身经验，系统管理员对本地系统上文件的可读权限并未给予足够的重视。许多系统管理员不理解或不充分重视本地被攻破的可能性，从而导致非预期文件可被获取。

记住这一点，我们很可能会找到主机上运行的敏感应用程序的某种备份，甚至是`git`目录。一定要将这些文件下载到本地副本，以便在我们的主机上分析，因为它们很可能包含某种程度的硬编码凭据。其他程序，例如`LinPEAS`，会自动搜索本地机器中的潜在密码和认证活动。`LinPEAS`和`WinPEAS`将在本章后面详细讨论。

## 访问数据库

一旦我们在 Linux 机器上站稳脚跟，就需要检查任何仅在`localhost`上运行、且最初网络中不可用的服务。Web 应用程序的数据库通常只绑定到`localhost`，从而阻止非本地机器上的任何人访问数据库登录面板。

当我们确实可以访问系统时，如果使用了 Web 应用程序，我们可以确定它如何连接到其数据库。通常，这会以配置文件的形式列在 Web 应用程序的根目录中，浏览网站的用户无法访问该文件。但是，借助对本地系统的访问权限，我们可以读取该文件，并确定用于数据库认证的凭据。

连接到该数据库时，我们可以搜索认证材料，以确定是否存储了任何额外的密码哈希。如果幸运的话，我们会看到机器上的管理员或其他本地用户帐户有额外的哈希可用。一旦发现这些哈希，就立即抓取并开始破解它们。

这一点在第三章“Web 应用程序攻击与防御”中有深入介绍，但在本领域也始终值得注意。

## 认证材料

用户可以通过几种不同的方式向 Linux 机器进行认证，即用户密码和 SSH 密钥。SSH 密钥是一对公钥/私钥，可以使用`ssh-keygen`命令在命令行生成。使用 SSH 密钥对进行认证比密码更安全，它依赖于使用文件向服务器认证。生成新密钥很简单，运行命令并按屏幕上的说明操作即可。

默认情况下，将生成 RSA 密钥对，但可以使用`-t`选项指定其他类型的密钥。还可以为密钥设置口令，以增加一层安全性，但这不是必需的。
