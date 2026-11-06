
## 密码永不过期

此设置使用户的密码免于受为域启用的最大密码使用期限组策略设置的限制。这在服务或程序正在使用该账户时很有帮助。如果设置了 `User must change password at next logon` 选项，则此选项将被覆盖。

## 账户已禁用

此复选框用于防止用户使用此账户登录。如果员工已被解雇、处于长期休假或休假中，或尚未开始工作，则可使用此功能。

输入此信息后，单击 `Next` 按钮以到达创建新用户账户的最终屏幕。

如 [图 2.8](#B9781931836944500088.xhtml#f0045) 所示，用于创建新用户对象的最终屏幕提供摘要信息。此屏幕上显示的信息提供了将用于创建账户的用户信息和密码选项的回顾。单击 `Finish` 按钮后，账户将在您最初选择用于存储对象的容器中创建。

![图 2.8 新对象对话框的摘要屏幕](images/B9781931836944500088/f02-08-9781931836944.jpg)

图 2.8 新对象对话框的摘要屏幕

现在我们已经了解了如何创建用户账户，让我们将这些知识付诸实践，并在 [练习 2.02](#B9781931836944500088.xhtml#b0075) 中创建一个。

### 练习 2.02

#### 在 Active Directory 用户和计算机中创建用户对象

1. 从 `Start | Administrative Tools | Active Directory Users and Computers` 打开 `Active Directory Users and Computers`。
2. 当实用程序打开时，展开控制台树，以便可以看到您的域及其内部的容器。
3. 从控制台树中选择您在 [第 1 章](#B9781931836944500076.xhtml) 中创建的 `TestOU` OU。从 `Action` 菜单中选择 `New | User`。
4. 当 `New Object - User` 对话框出现时，在相应的字段中输入以下信息：

| 字段 | 输入数据 |
|---|---|
| 名字 | John |
| 姓名缩写 | Q |
| 姓氏 | Public |
| 全名 | John Public |
| 用户登录名 | Jpublic |
| 用户登录名（Windows 2000 之前） | Jpublic |

5. 输入此信息后，单击 `Next` 按钮继续。
6. 在 `Password` 字段中输入您选择的密码，然后在 `Confirm password` 字段中重新输入。
7. 清除 `User must change password at next logon` 复选框。
8. 单击 `Next` 继续。当摘要屏幕出现时，查看您输入的设置并单击 `Finish` 创建账户。
9. 从 `Action` 菜单中选择 `New | User`。
10. 当 `New Object - User` 对话框出现时，在相应的字段中输入以下信息：

| 字段 | 输入数据 |
|---|---|
| 名字 | Jane |
| 姓氏 | Doe |
| 全名 | Jane Doe |
| 用户登录名 | Jdoe |
| 用户登录名（Windows 2000 之前） | Jdoe |

11. 输入此信息后，单击 `Next` 按钮继续。
12. 在 `Password` 字段中输入您选择的密码，然后在 `Confirm password` 字段中重新输入。
13. 单击 `Next` 继续。当摘要屏幕出现时，查看您输入的设置并单击 `Finish` 创建账户。
14. 注销然后以 `jdoe` 用户身份重新登录。注意，您需要更改密码。
15. 注销然后以 `jpublic` 用户身份重新登录。注意，您不需要更改密码。

### 使用 `DSADD` 命令创建账户

正如我们在 [第 1 章](#B9781931836944500076.xhtml) 中看到的，Windows Server 2003 包含许多命令行工具，可让您从命令提示符执行常见的管理任务。使用 `DSADD` 命令，您可以在 Active Directory 中创建新对象，包括用户对象。与使用 `Active Directory Users and Computers` 时的情况一样，只有 `Administrators` 组、`Account Operators` 组、`Domain Admins` 组、`Enterprise Admins` 组成员，或被授予权限的人员才能创建用户账户。这意味着 `DSADD` 命令不能用作未经授权创建账户的变通方法。

使用以下语法通过 `DSADD` 创建新用户：

```
DSADD USER UserDN [-samid SAMName] -pwd {Password | *}
```

输入此命令时，必须输入以下参数：

- `UserDN` 这是要添加的用户对象的 DN。这提供了账户将被创建位置的信息。
- `SAMName` 这是 NetBIOS 名称，用于从 Windows 2000 之前的计算机登录。如果未添加此参数，`DSADD` 将根据您为 `UserDN` 参数输入的常用名的前 20 个字符创建一个。
- `Password` 这是此账户将使用的密码。如果为此参数输入星号 (`*`)，系统将提示您输入密码。

除了这些参数之外，还可以使用以下语法在创建用户账户时应用其他设置。请注意，这是一行很长的命令。

```
dsadd user UserDN [-samid SAMName] [-upn UPN] [-fn FirstName] [-mi Initial] [-ln LastName] [-display DisplayName] [-empid EmployeelD]
[-pwd {Password | *}] [-desc Description] [-memberof Group;…]
[-office Office] [-tel PhoneNumber] [-email Email] [-hometel HomePhoneNumber] [-pager PagerNumber] [-mobile CellPhoneNumber]
[-fax FaxNumber] [-iptel IPPhoneNumber] [-webpg WebPage] [-title Title]
[-dept Department] [-company Company] [-mgr ManagerDN] [-hmdir HomeDirectory] [-hmdrv DriveLetters] [-profile ProfilePath] [-loser ScriptPath] [-mustchpwd {yes | no}] [-canchpwd {yes | no}]
[-reversiblepwd {yes | no}] [-pwdneverexpires {yes | no}] [-acctexpires NxmberOfDays] [-disabled {yes | no}] [{-s Server| -d Domain}]
[-u UserName] [-p {Password | *}] [-q] [{-uc [-uco | -uci}]
```

正如您所见，使用 `DSADD` 命令可以设置大量选项，这些选项在初始使用 `Active Directory Users and Computers` 创建账户时不可用。我们将在下一节解释如何使用 `Active Directory Users and Computers` 将此类信息添加到账户中。首先，让我们检查可与 `DSADD` 命令一起使用的各种参数。此语法中的参数在 [表 2.3](#B9781931836944500088.xhtml#t0020) 中进行了说明。

#### 表 2.3

创建用户的 DSADD 参数

| 参数 | 描述 |
|---|---|
| `-upn UPN` | 指定账户的 UPN。 |
| `-fn FirstName` | 指定用户的名字。 |
| `-mi Initial` | 指定用户的姓名缩写。 |
| `-ln LastName` | 指定用户的姓氏。 |
| `-display DisplayName` | 指定账户的显示名称。 |
| `-empid EmployeelD` | 指定用户的员工 ID。 |
| `-desc Description` | 描述账户的信息。 |
| `-memberof Group` | 指定此账户将成为其成员的组的 DN。 |
| `-office Office` | 指定用户的工作地点。 |
| `-tel PhoneNumber` | 指定用户的电话号码。 |
| `-email Email` | 指定用户的电子邮件地址。 |
| `-hometel HomePhoneNumber` | 指定用户家庭电话号码。 |
| `-pager PagerNumber` | 指定寻呼机号码。 |
| `-mobile CellPhoneNumber` | 指定蜂窝电话号码。 |
| `-fax FaxNumber` | 指定用户的传真号码。 |
| `-iptel IPPhoneNumber` | 指定用户的 IP 电话号码。 |
| `-webpg WebPage` | 指定用户网页的 URL。 |
| `-title Title` | 指定用户的职称。 |
| `-dept Department` | 指定用户的部门。 |
| `-company Company` | 指定公司信息。 |
| `-mgr ManagerDN` | 指定用户经理的 DN。 |
| `-hmdir HomeDirectory` | 指定用户的主目录。 |
