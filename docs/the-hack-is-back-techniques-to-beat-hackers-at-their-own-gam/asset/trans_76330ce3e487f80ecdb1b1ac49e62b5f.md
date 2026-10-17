

要分析 sudo -l 命令的结果，我们可以看到用户账户 chris 可以使用 sudo 运行所有命令，而无需输入密码。为了进一步细化 sudo 配置列表所显示的信息，我们可以指定 -ll 选项（即小写字母“L”，共两个）。这有助于进一步列出 sudo 输出信息的含义。

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

请注意，这里并没有显示出额外的权限，只是这些信息以更易于人类阅读的格式呈现。我们可以看到，我们可以以任何用户和任何组的身份运行所有命令（ALL），并且无需验证身份。这是一种自定义配置，旨在允许用户运行 sudo 命令时，无需在每次执行特定命令时输入密码。

显然，这是一个极其不安全的 sudo 策略文件。因为任何能够访问该用户的人，即使不知道用户密码，也能以 root 用户身份运行命令。一旦获得 root 权限，他们就可以获取密码哈希、SSH 密钥以及其他可能存储于其他用户账户中的敏感信息。但请记住，sudo -l 命令只会列出当前用户的 sudo 权限，而不是系统上其他所有用户的权限。

要知道主机上还有哪些其他用户可以运行 sudo 命令，我们需要查询 /etc/group 文件，看看谁在 sudo 组中。这表示该指定用户将有权使用机器上的 sudo 命令。为了识别这一点，我们可以使用 grep 搜索 /etc/group 文件中的 sudo 组，并查看其中包含哪些成员。通过搜索 sudo 组并将其打印到屏幕上来完成：

```
$ grep '^sudo:.*$' /etc/group
sudo:x:27:chris
```

要对 sudoers 文件进行修改，我们应该确保使用 visudo 命令，而不是直接编辑该文件。我们需要先获得合法的 sudo 访问权限才能进行这些修改！使用 visudo 命令时，sudoers 文件会被编辑，并检查其中可能导致 sudo 配置损坏的差异。直接编辑 sudoers 文件无法保护系统免受策略中错误配置的影响，并可能导致用户被锁定在系统之外。此外，配置错误的 sudoers 策略会阻止我们再次通过 sudo 进入文件进行修改，很可能需要启动到“单用户”模式才能恢复。简而言之，请使用 visudo 命令，而不是直接编辑 /etc/sudoers。

## 在这里，谁可以更改我们的 Windows？

Windows 利用组来帮助跟踪和管理哪些人应该被允许对机器拥有管理控制权。与枚举本地用户类似，我们可以使用 net localgroup 命令来确定哪些用户位于 Administrators 组中。这用于找出哪些用户账户在机器上拥有管理访问权限，从而帮助我们取得完全控制。

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

上述命令的输出显示，用户 Administrator 和 chris 被设置为 Administrators 组的成员。

上述活动来自较早的 Windows 命令提示符时代。在过去十年左右，微软一直在大力推动 PowerShell 尽可能取代 CMD。PowerShell 是一种非常高效的语言，但如果编程不是你的强项，它也可能很难学习。到目前为止，我们已经在 PowerShell 中介绍了一些有用的内容，接下来将继续探索更多。

PowerShell 内置了用于枚举本地组和本地用户的 cmdlet，而无需导入新模块，这与本章前面介绍的 ActiveDirectory 模块类似。要探索本地组和用户，我们可以使用 Get-LocalGroup、Get-LocalGroupMember 和 Get-LocalUser 这些 cmdlet。枚举组就像执行 Get-LocalGroup 一样简单。

```
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

我们看到该 cmdlet 返回了大量组，但其中有一些非常有趣的名字。我们当然对 Administrators 组感兴趣，可以使用 Get-LocalGroupMember cmdlet 来请求该组的成员。

要查询这一点，我们可以使用下面的命令来显示此组的所有成员。

```powershell
PS C:\Users\mboone2f> Get-LocalGroupMember -Group Administrators

ObjectClass Name                         PrincipalSource
----------- ----                         ---------------
User        DESKTOP-CHRIS\Administrator Local
User        DESKTOP-CHRIS\chris         Local
```

在上面的例子中，我们可以看到有两个本地账户是这台特定机器上 Administrators 组的成员。这些账户被特别授予了本地计算机的管理级访问权限，而不是对整个域的管理权限。然而，很多时候，本地计算机上可用的某些信息可以用于进一步利用权限深入到域中。

## Active Directory 管理员

要搜索并识别 Active Directory 上的管理级账户，我们可以利用 ActiveDirectory 模块中的几个不同 PowerShell cmdlet。第一个 **Get-ADGroupMember** 利用 ActiveDirectory 模块查找指定组中的条目。通过将其传给 Administrators 组，我们可以识别谁和哪些组是成员，并确保我们要求它递归运行！这很好地表明了域中谁会成为有价值的攻击目标。

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

