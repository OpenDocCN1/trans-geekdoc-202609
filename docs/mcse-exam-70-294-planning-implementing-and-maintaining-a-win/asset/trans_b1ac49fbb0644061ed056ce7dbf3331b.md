
## 14. 昨晚你完成了为新的 `Windows Server 2003` `Active Directory` 环境配置一组复杂的组。你今天早上花时间将用户添加到相应的组中。现在 `Active Directory` 环境已配置好，你正尝试将组添加到文件系统中的 `ACLs`。由于某种原因，它们在可供选择的组列表中没有显示出来。你可以看到操作系统和 `Active Directory` 安装的所有默认组。为什么看不到你创建的组？

A. 你没有权限。

B. 你没有在 `Active Directory` 中激活这些组。

C. 你创建了分发组。

D. 你创建了安全组。

☑ C. 分发组设计用于消息传递，而不是在 `Windows Server 2003` 中应用安全。因此，在操作系统中配置 `ACLs` 时它们不可用。

![错误](images/wrong.png) 答案 A 不正确。因为你可以查看和选择默认系统组，所以你知道自己具有适当的权限。答案 B 也不正确。组在你在 `Active Directory` 中创建它们的那一刻就被激活了。答案 D 不正确，因为如果你创建了安全组，它们会与默认组一起显示。

## 15. 你的公司有一个单域环境，将升级到 `Windows Server 2003`。由于自定义应用程序需要，公司现有的 `Windows NT 4.0` `BDCs` 之一必须保留在原位。该应用程序要到明年某个时候才会迁移。公司有许多部门，每个部门都有子部门和团队。公司希望利用 `Windows Server 2003` 的新组嵌套功能。以下哪种组模型适合该公司？

A. `AGDLP`

B. `AGGDLP`

C. `AGGUDLP`

D. `AGUDLP`

☑ A. 因为 `Windows NT` 域控制器必须保留在网络上，所以只有答案 A 是正确的。公司希望利用 `Windows Server 2003` 中的额外组嵌套功能，但要等到将所有域控制器升级到至少 `Windows 2000` 之后才能实现。额外的组嵌套仅由 `Windows 2000` 原生和 `Windows Server 2003` 域功能级别支持。这些功能级别不支持 `Windows NT` 域控制器。

![错误](images/wrong.png) 答案 B、C 和 D 均不正确。虽然它们允许使用组嵌套，但都需要更高的域功能级别，而由于 `Windows NT` 域控制器的存在，这是不可能的。

# 第四章 使用林和域

## 理解林和域功能

### 1. 你的 [Yellow.labs.dogs.com](http://www.Yellow.labs.dogs.com) 信息保证部门刚刚使用 `John the Ripper`，一个密码破解程序，对你的 `Active Directory` 用户账户进行了测试。他们报告说在八小时内有 40% 的密码被破解。经过一些研究，你确定删除针对下级客户端的 `LM` 身份验证将使密码猜测变得更加困难。此外，你决定在所有 `DCs` 上要求 `Kerberos` 身份验证。经过一些电话沟通，你向你的经理和 CIO 保证，所有林中所有域中的计算机都安装了 `Windows 2000`、`2003` 或 `XP`。没有需要向后 `LM` 或 `NTLM` 兼容性的旧工作站。在他们的许可下，你使用 `Group Policy` 应用了安全设置。几乎立即，[Fish.com](http://www.Fish.com) 和 [theYellow.labs.dogs.com](http://www.theYellow.labs.dogs.com) 域之间的身份验证失败，这两个域位于不同的 AD 林中，并通过外部单向信任相互连接。但是，两个域中的主机之间 `ping` 仍然有效。之前，两个域中的所有用户都可以完全访问两个域中的所有资源，但现在每次经过身份验证的访问都失败。请参考 [图 4.56](#B9781931836944500180_1.xhtml#f0010)。为什么会出现这个问题？

A. 网络问题。

B. 选择性身份验证问题。

C. `NT LAN Manager` 身份验证问题。

D. 信任传递性问题。

☑ C. 答案 C 正确，因为外部信任的限制与 `NT 4.0` 信任相同。`NT LAN Manager` 建立所有外部信任。当启用仅 `Kerberos` 身份验证时，你的两个外部信任会因依赖 `NTLM` 而失败。

![错误](images/wrong.png) 答案 A 不正确，因为基本网络连接没有受到影响，正如成功的 `ping` 命令所示。答案 B 不正确，因为选择性身份验证需要在两个域的所有用户和所有资源之间设置明确的权限。之前完全不受限制的访问表明未配置选择性身份验证。答案 D 不正确，因为作为外部非传递信任，只有 [Yellow.labs.dogs.com](http://www.Yellow.labs.dogs.com) 曾经可以访问 [Fish.com](http://www.Fish.com)，并且只有 [Yellow.labs.dogs.com](http://www.Yellow.labs.dogs.com) 受到了中断的影响。未发现任何传递性问题。

![图 4.56 问题 #1 图表](images/B9781931836944500180/a01-01-9781931836944.jpg)

图 4.56 问题 #1 图表

### 2. 在周末，你将 `Windows NT 4.0` 域通过 `Windows Server 2003` 过渡功能级别升级到 `Windows Server 2003` 功能级别。大多数客户端 PC 运行 `Windows NT 4.0`。你的测试 NT 工作站继续正常运行，但在周一早上，你开始收到几台无法登录到新域的工作站的故障票据。作为临时解决方法，这些用户能够从其他工作站登录。最可能的原因是什么？

A. 出现故障的工作站运行的是 `Windows NT 4.0` `SP2`。

B. 用户的旧密码不符合 `Windows Server 2003` 的新复杂性要求。

C. 某些工作站未获取新的信任关系，需要将其从域中删除并重新加入。

D. 某些用户账户尚未复制到所有 `DCs`。从 `Active Directory Domains and Trusts` `MMC` 快照中选择 `Synchronize all domain controllers` 选项。

☑ A. `Windows NT 4.0` 系统在 `SP3` 之前与 `NTLMV2` 身份验证不兼容，而 `NTLMV2` 身份验证是 `Windows Server 2003` 的最低身份验证要求。

![错误](images/wrong.png) 答案 B 不正确，因为虽然 `Windows Server 2003` 默认设置了密码复杂性要求，但定义的问题存在于工作站，而不是用户账户。答案 C 不正确，因为信任在域级别运行，而不是在工作站级别。答案 D 不正确，因为 `Active Directory` 中的复制比 NT 中更稳健、更及时。在健康的局域网环境中，这不太可能是问题。虽然在安装后 `Active Directory` 复制可能尚未完成，但所述问题与特定工作站有关，而不是用户账户。

### 3. 一家大型公司刚刚与贵公司合并。他们有一个运行在 `Windows Server 2003` 功能级别的林的 24 小时企业管理员组。贵公司在单个 NT 域上拥有 NT、`2000` 和 `XP` 客户端。你的 `PDC` 和五个 `BDCs` 中的四个仍在运行 `Windows NT`。你的两个权限组中有超过 5000 名成员。新集团已为升级本地基础设施以便通过跨林信任参与企业林结构提供了预算。在加入企业林之前，你必须满足的最低要求是什么？（选择所有适用项。）

A. 请企业管理员暂时使用手动 `LDAP` 管理工具将他们的林设置为过渡级别。

B. 安装新服务器并使用你的命名空间创建一个全新的本地林根。

C. 将你的 `PDC` 升级到 `Windows Server 2003`，并在升级期间加入企业林。
