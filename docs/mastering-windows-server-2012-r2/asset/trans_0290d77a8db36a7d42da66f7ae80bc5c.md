
假设你正在创建 10 个用户对象，并想为它们设置设置相同的密码并启用这些用户。你还想强制用户在第一次登录时更改密码。你可以执行以下操作：

```
PS C:\Users\Administrator> $pw = Read-Host "Please Enter The Password" -AsSecureString
```

请输入密码：*************

```
PS C:\Users\Administrator> New-ADUser "Philipp Witschi" -SamAccountName "Pwitschi" -GivenName "Philipp" -Surname "Witschi" -DisplayName "Philipp\nWitschi" -Path 'OU=Users,OU=BigFirm,DC=bigfirm,DC=com' -UserPrincipalName -AccountPassword $pw -Enabled 1 -ChangePasswordAtLogon 1
```

第一行提示管理员输入密码。当输入文本时，$pw 变量将成为你想要存储该值的变量或容器。`Read-Host` 词汇会提示你输入一个值。`-AsSecureString` 会将你响应提示输入的值转换为安全字符串。$pw 将存储在当前 PowerShell 会话的内存中，直到你覆盖该值或关闭 PowerShell 窗口。

当你运行命令时，系统会提示你输入密码。请响应符合密码复杂性和长度要求的易于通信的字符串。
第二个命令将创建你的用户。你可以添加几个标记来满足你的需求：

- **AccountPassword**: 使用上一个命令中的 $pw。这将以安全格式传递新用户对象所需的密码。
- **Enable**: 接受 1（启用用户对象）或 0（禁用用户对象）。
- **ChangePasswordAtLogon**: 接受 1（强制更改密码）或 0（不强制更改密码）。

其结果是创建了具有你所需密码的用户对象并已启用，用户在第一次登录时将被强制更改密码。
运行两个命令看起来很棒，不是吗？但其实只需要一个。然而，通过这种方法，你可以对想要创建的其他用户重复此操作。每个用户都拥有相同的密码。

如果你只想创建一个，那么可以在一个命令中完成所有操作。这种方法将利用 PowerShell 的速度。你需要使用 `Read-Host` 词汇：

```
PS C:\Users\Administrator> New-ADUser "Philipp Witschi" -SamAccountName "Pwitschi" -GivenName "Philipp" -Surname "Witschi" -DisplayName "Philipp\nWitschi" -Path 'OU=Users,OU=BigFirm,DC=bigfirm,DC=com' -UserPrincipalName -AccountPassword (read-host "Please Enter The Password") -AsSecureString -Enabled 1 -ChangePasswordAtLogon 1
```

请输入密码：*************

你在这里所做是用 `Read-Host` 词汇替换了之前方法中的 $pw 变量。这将导致 `Read-Host` 词汇在 `New-ADUser` 词汇完成之前运行，然后输入安全字符串作为 `-AccountPassword` 标记的值。当你运行命令时，系统会提示输入密码，然后创建用户对象。

# 一次创建多个用户

假设你在一家大学担任 Active Directory 管理员。你可能有一个用于学生账户的森林。每个夏天你都会删除所有旧的学生账户。然后你为参加当年第一学期的每位学生创建新用户。你面对的是可能需要创建数千个用户对象的任务。你真的打算使用 ADUC、ADAC 或之前的某个 PowerShell 示例来完成它吗？我们希望你没有计划使用这些方法之一。

你可以使用一条强大的单行 PowerShell 命令以极少的努力完成这项工作。你要做的是在 Excel 或其他表格工具中创建一个逗号分隔值 (CSV) 文件。更高级的网络可能会有一个人事管理系统，可以通过某些导出功能创建此文件。CSV 文件是一个文本文件，包含一个描述值的表头行，随后是每个用户的一行。每行都将包含描述用户的值。以下是名为 `users.csv` 的文件内容，你可以用它创建用户：

| Name | SamAccountName | GivenName | Surname | Path | UserPrincipalName | AccountPassword |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Kelly Kelly | RKelly | Rachel | Kelly | OU=Users,OU=BigFirm,DC=bigfirm,DC=com | RKelly@bigfirm.com | NewPassword |
| Ulrika Gerhardt | UGerhardt | Ulrika | Gerhardt | OU=Users,OU=BigFirm,DC=bigfirm,DC=com | UGerhardt@bigfirm.com | NewPassword |
| Tomasz Kozlowski | TKozlowski | Tomasz | Kozlowski | OU=Users,OU=BigFirm,DC=bigfirm,DC=com | TKozlowski@bigfirm.com | NewPassword |

如果你在记事本中打开该 .csv 文件，它看起来像这样：
Name,SamAccountName,GivenName,Surname,Path,UserPrincipalName,AccountPassword
Kelly Kelly,RKelly,Rachel,Rachel Kelly,"OU=Users,OU=BigFirm,DC=bigfirm,DC=com",RKelly@bigfirm.com,NewPassword
Ulrika Gerhardt,UGerhardt,Ulrika,Gerhardt,"OU=Users,OU=BigFirm,DC=bigfirm,DC=com",UGerhardt@bigfirm.com,NewPassword
Tomasz Kozlowski,TKozlowski,Tomasz,Kozlowski,"OU=Users,OU=BigFirm,DC=bigfirm,DC=com",TKozlowski@bigfirm.com,NewPassword

# 第 8 章 创建和管理用户账户

## 注意表头行

表头行与早之前配合 `New-ADUser` 词汇使用的变量相同。CSV 文件中表头下的行包含创建每个用户的值。现在你想运行一个命令，从你保存的 CSV 文件中读取每一行。该命令将使用这些值执行 `New-ADUser` 词汇：

```
PS C:\Users\Administrator> Import-csv c:\users.csv | foreach {New-ADUser -Name $_ -SamAccountName $_ -GivenName $_ -Surname $_ -DisplayName $_ -Path $_ -UserPrincipalName $_ -AccountPassword (Convert-SecureString $_.Password -PlainText -Force) -Enabled 1 -ChangePasswordAtLogon 1}
```

不要让此命令的大小困扰你。一旦你理解了如何拆解它，它就很简单：
- **Import-csv**: 这个词汇读取你创建的 c:\users.csv 文件。
- **Foreach**: 这个词汇处理 CSV 文件中的每一项。
- **New-ADUser**: 这个词汇使用这些值执行 `New-ADUser` 词汇。
- **AccountPassword**: 你再次将密码转换为安全字符串。

通过这种方法，你可以手动或自动（通过某些导出工具）创建此文件并创建许多账户。这就是 PowerShell 的意义所在：通过自动化让工作变得简单。

# Windows Active Directory 模块

## 解锁用户账户

你也可以使用 PowerShell 来这些琐碎的工作。如果你想解锁用户账户，可以运行：

```
PS C:\Users\Administrator> Unlock-ADAccount -identity SRed
```

`-identity` 标记接受要解锁用户的名称。在此示例中我们使用了友好名称。你可能想使用 DN 来标识用户对象：

```
PS C:\Users\Administrator> Unlock-ADAccount -identity "CN=Steve Red,OU=Users,OU=Bigfirm,DC=com"
```

你可以使用此命令重置用户的密码：

```
PS C:\Users\Administrator> Set-ADAccountPassword -identity SRed -resetpassword (read-host "Please Enter The Password" -AsSecureString)
```

Set-ADAccountPassword 词汇使用 `-identity` 指定用户对象。`-reset` 标记告诉 PowerShell 你不是在进行正常的密码更改。相反，由于用户忘记了密码，你想为用户对象更改密码。你再次使用 `Read-Host` 词汇读取密码并将其转换为安全字符串传递给 `-newpassword` 标记。
Get-ADUser 词汇将检索用户的属性：

```
PS C:\Users\Administrator> Get-ADUser SRed
```

DistinguishedName: CN=Steve Red,OU=Users,OU=Bigfirm,DC=com
Enabled: True
Name: Steve Red
ObjectClass: user
ObjectGUID: 5cf6f3ac-93ec-4cf8-bf80-2136fb8b3a8d
SamAccountName: SRed
SID: S-1-5-21-362581918-275756322-308910462-1108
Surname: Red
UserPrincipalName: SRed@bigfirm.com

默认情况下，它只检索可用属性的一部分。如果你想查看用户对象中的所有内容，运行 `Get-ADUser` 命令并使用 `*` 通配符请求所有属性：

```
PS:\Users\Administrator> Get-ADUser SRed -properties * | more
```

在这里你将结果管道到 `More` 词汇，这样结果显示的速度就会比你阅读的速度快，你可以按键继续。结果可能包含太多内容，因此你可以以下方式修改结果：

