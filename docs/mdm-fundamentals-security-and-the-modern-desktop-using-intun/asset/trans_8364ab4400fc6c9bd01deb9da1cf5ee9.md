
但你似乎会获得额外的好处：标准用户会在其配置文件中看到自己的密钥，而不是设备所有者的密钥。以下是两篇表达此方法的博客文章：

`https://blogs.technet.microsoft.com/showmewindows/2018/01/18/how-to-enable-BitLocker-and-escrow-the-keys-to-azure-ad-when-using-Autopilot-for-standard-users/`

`https://blogs.technet.microsoft.com/home_is_where_i_lay_my_head/2017/06/07/hardware-independent-automatic-BitLocker-encryption-using-aadmdm/`

再次强调：我没有尝试过这些方法，因此请自担风险使用。

### BitLocker 密钥恢复与管理

BitLocker 非常敏感。事实上，仅仅在启动时插入媒体（如可启动的 USB 闪存盘）就经常会让 BitLocker 说：“哇哦……你想干什么？”并向用户显示令人生畏的 BitLocker 恢复密钥屏幕。（当然，只需移除可启动媒体（如 DVD 或 USB 闪存盘），然后重启计算机，通常就能解决问题。）但其他因素也可能让 BitLocker 认为有人在篡改它。

因此，你的用户（在这种情况下是设备所有者）可能需要检索他们的 BitLocker 密钥。他们可以通过访问 `https://myapps.microsoft.com` 并使用其 AAD 凭据登录，然后选择其配置文件来实现。当他们这样做时，可以看到所有计算机以及启用了 BitLocker 的计算机，并可以按[图 10.16](#c10.xhtml#figure10-16) 所示检索密钥。

但请注意，只有最初注册计算机的人（也称为设备所有者）才能读取密钥。因此，如果 Frank 注册了一台计算机但 Jack 每天都在使用，那么，这对 Jack 来说并不是一个理想的情况。但另一方面，如果 Jack 的计算机是通过 Autopilot 部署的，且 Jack 既是该计算机上的标准用户又是设备所有者，那么……太棒了！

使用其他计算机（任何带有 Web 浏览器的计算机），Jack 可以通过 `myapps.microsoft.com` 页面查看自己的 BitLocker 密钥，点击“配置文件”并找到带有 BitLocker 屏幕的计算机。这样他就没事了！

![图 10.16 用户如何恢复其 BitLocker 密钥](images/c10f016.jpg)

[**图 10.16**](#c10.xhtml#figureanchor10-16) 用户如何恢复其 BitLocker 密钥

正如我所说，如果日常用户不是设备所有者，这就会成问题。稍后我有一些想法可以帮你摆脱这个困境。让我们在接下来的几节中探讨用户如何在不是设备所有者的情况下恢复其密钥。

#### 管理员如何通过电话读取 BitLocker 密钥

Jack Tors 因为在开会前遇到了 BitLocker 蓝屏而惊慌失措。他手头没有恢复密钥，也离不了另一台计算机来恢复自己的密钥。

所以他给你打电话。你该怎么办？

你将在 Azure Active Directory ➢ 设备中查找他的计算机，在本例中为 `COMPUTER15`，然后点击它。在页面底部，如[图 10.17](#c10.xhtml#figure10-17) 所示，你将找到驱动器标识符（BitLocker 密钥 ID）和 BitLocker 恢复密钥。微软还宣布 BitLocker 恢复密钥将成为 Intune 门户的一部分，因此请留意即将推出的这些更改。

只需将那些（感觉像）823 位数字读给 Jack 听，他的计算机就应该能启动。

![图 10.17 使用 Azure AD 发现 BitLocker 恢复密钥](images/c10f017.jpg)

[**图 10.17**](#c10.xhtml#figureanchor10-17) 使用 Azure AD 发现 BitLocker 恢复密钥

当然，你公司里的 IT 管理员可能不止*你*一个，你可能希望将获取 BitLocker 密钥的权限委派给公司其他受信任的管理员。为此，你将使用 Azure 的管理员角色功能。我意识到这本身可能是一个话题，但我们在这里必须长话短说。你可以通过以下三个链接了解如何将 IT 管理员角色委派给其他管理员：

`https://docs.microsoft.com/en-us/azure/active-directory/users-groups-roles/directory-assign-admin-roles` 并使用 `portal.microsoft.com`

`https://docs.microsoft.com/en-us/azure/active-directory/users-groups-roles/directory-manage-roles-portal`

`https://docs.microsoft.com/en-us/azure/billing/billing-add-change-azure-subscription-administrator`

通过这种方式，全局管理人员、帮助台管理人员、安全管理人员、安全读取者、Intune 服务管理员和云设备管理员角色可以从 `portal.microsoft.com` 查看设备的 BitLocker 密钥。

#### 使用自动化和 PowerShell 获取 BitLocker 密钥

此外，还可以使用带有 Azure API 的 PowerShell 获取 BitLocker 密钥并将其导出到其他地方，如本地或 Azure SQL 数据库或 SharePoint。你可以批量执行此操作，因此不必逐个点击计算机来查找每个密钥。

也许你只是想在别处有一个备份，这样宇宙中就不只存在 Azure 这一条密钥记录。

以下是一个示例 PowerShell 脚本，可帮助你收集现有的 BitLocker 密钥并将其转换为你选择的格式：

`https://pwsh.nl/2018/10/26/retrieving-BitLocker-keys-from-azure-ad-with-powershell/`

#### 启用标准用户在本地管理其自己的 BitLocker 密钥和设置

我听到的关于 BitLocker 的问题之一是，其所有功能都仅限于本地管理员。因此，如果用户想要使用[图 10.14](#c10.xhtml#figure10-14) 中所示的“备份恢复密钥”设置，但他不是本地管理员，则会被 UAC 提示阻止。这对我来说似乎总有点不公平，因为我能理解某些用户应该能够维护自己的备份密钥副本。

然而，有一种方法可以克服这一挑战，例如，如果你想让标准最终用户能够将恢复密钥保存到 USB 闪存盘、打印出来等。为此，你需要一种方法来提升相关应用程序的权限。在本例中，它是 BitLocker 备份恢复密钥向导，其实际可执行文件名也称为 `BitLockerWizardElev.exe`。

你需要一个（付费）工具，如 PolicyPak MDM（更多内容见最后一章）。但大体思路是，使用像 PolicyPak Least Privilege Manager（PolicyPak MDM 的一部分）这样的工具，你可以指定需要以提升权限运行的应用程序，如[图 10.18](#c10.xhtml#figure10-18) 所示。然后导出你的设置并使用 MDM 进行部署。（同样，更多内容见下一章。）

结果就是你在[图 10.18](#c10.xhtml#figure10-18) 中看到的内容：一条克服 UAC 挑战的规则，成功的结果可见于[图 10.19](#c10.xhtml#figure10-19)，用户可以备份自己的恢复密钥，例如保存到 USB 闪存盘上的文件中（如果他们愿意）。

![图 10.18 使用 PolicyPak Least Privilege Manager 创建规则，使标准用户能够运行 BitLocker 备份恢复密钥向导](images/c10f018.jpg)

[**图 10.18**](#c10.xhtml#figureanchor10-18) 使用 PolicyPak Least Privilege Manager 创建规则，使标准用户能够运行 BitLocker 备份恢复密钥向导

![图 10.19 标准用户无法备份自己的 BitLocker 密钥。但使用带有 PolicyPak Least Privilege Manager 的 PolicyPak MDM，你可以克服标准用户的 UAC 提示，启用此类场景。](images/c10f019.jpg)

[**图 10.19**](#c10.xhtml#figureanchor10-19) 标准用户无法备份自己的 BitLocker 密钥。但使用带有 PolicyPak Least Privilege Manager 的 PolicyPak MDM，你可以克服标准用户的 UAC 提示，启用此类场景。

### BitLocker 最终思考与其他资源
