
新的 Active Directory 配额（不要与磁盘配额混淆）定义为在给定目录分区中给定用户可以拥有的对象数量。幸运的是，Domain Admins 和 Enterprise Administrators 被免除配额，并且它们对架构分区完全不适用。复制操作不计入配额；只有原始操作才计入。配额管理通过一组命令行工具执行，包括 `dsadd`、`dsmod`、`dsget` 和 `dsquery`。配额管理不存在图形界面。

## 链接值复制
链接值复制解决了 Windows 2000 对 5000 个直接组成员的限制。不是将大型组视为单个复制单元，链接值复制允许在复制期间向组中添加或删除单个成员，从而减少网络流量。例如，没有它，任何对 10,000 成员分发组的更改都会触发完整复制。对于如此庞大的组，在典型的一天中这种情况很可能会发生多次。

## 改进的知识一致性检查器
由于站点间复制拓扑生成器算法的复杂性，Windows 2000 知识一致性检查器 (`KCC`) 在包含超过 200 个站点的林中无法正常运行。在这种情况下，该服务必须关闭，并且复制拓扑必须手动管理。由于采用了新的、更高效的算法，Windows Server 2003 `KCC` 可以自动管理多达 5000 个站点之间的复制。此外，它使用大幅改进的拓扑生成事件日志记录来协助故障排除。

## 减小 `NTDS.DIT` 大小
Windows Server 2003 目录利用了名为单实例存储 (`SIS`) 的新功能。这限制了冗余信息的重复。新目录存储比 Windows 2000 中的小约 60%。

## 森林信任
在 Windows NT 4.0 中，业务单元互操作性的选项很少；例如，要么 [Calico.cats.com](http://www.Calico.cats.com) 信任 [Labs.dogs.com](http://www.Labs.dogs.com)，要么不信任。没有其他真正的选项。此外，如果存在信任，通常是完全的。当 Windows 2000 引入 Active Directory 时，出现了更多选项，以便合作伙伴关系和集成项目团队可以在网络上形成，就像在现实生活中一样。该方法的问题在于根部始终必须有一个主导合作伙伴——竞争环境永远不可能完全公平。

单一森林的田园诗式乌托邦无法处理某些情况。根所有者雇用 Administrators、Domain Admins 和 Enterprise Admins，其中任何一个只需稍加坚持即可访问林中任何资源。域是良好的管理边界，域和站点是良好的复制边界，但只有森林才能提供可行的安全边界。

理解业务的政治，微软在 Windows Server 2003 中推出了名为多森林信任的解决方案，使用时会导致一种称为联合森林的配置。如果没有森林信任，林之间的 Kerberos 身份验证将无法工作。请记住，拥有两个森林意味着两个 Active Directory 数据库和两个完全不同的目录对象集，例如用户帐户。跨联合森林边界访问资源所需的信任路径比单个森林内域之间的信任路径更复杂。有关多森林信任路径的示例，请参阅 [图 4.2](#B9781931836944500106_1.xhtml#f0015)。

![图 4.2 森林信任路径](images/B9781931836944500106/f04-02-9781931836944.jpg)
图 4.2 森林信任路径

![u04-05-9781931836944](images/B9781931836944500106/u04-05-9781931836944.jpg)注意
请注意，“federated forest” 并不是您会在 Windows Server 2003 帮助文件中找到的术语。然而，这一术语已在 Windows Server 2003 的 TechNet 文章中使用。有关概念和实现的更多信息，请参阅 Planning and Implementing Federated Forests in Windows Server 2003：[www.microsoft.com/technet/treeview/default.asp?uri=/technet/prodtechnol/windowsserver2003/maintain/security/fedffin2.asp](http://www.microsoft.com/technet/treeview/default.asp?uri=/technet/prodtechnol/windowsserver2003/maintain/security/fedffin2.asp)。

### 班级之首…
### 如何在两个 Active Directory 之间共享资源？
这就是两个 Active Directory 之间共享资源的工作方式。假设 Tabby 是 Windows 2000 [Calico.cats.com](http://www.Calico.cats.com) 域中的用户，她尝试访问 Windows Server 2003 [Black.labs.dogs.com](http://www.Black.labs.dogs.com) 域中名为 Onyx 的文件服务器上的公共文件夹，如 [图 4.2](#B9781931836944500106_1.xhtml#f0015) 所示。

首先，Tabby 使用 Kerberos 身份验证登录到她的 workstation 并尝试访问 Onyx 上的公共文件夹。她的 workstation 天真地联系 [Calico.cats.com](http://www.Calico.cats.com) 的一个 `DC`，该 `DC` 主机 Kerberos `KDC`，请求 [Onyx.black.labs.dogs.com](http://www.Onyx.black.labs.dogs.com) 的服务器主体名称 (`SPN`) 的服务票据。自然地，`DC` 的数据库不包含该信息，因此它查询 [Cats.com](http://www.Cats.com) `GC`，以查看其林中的其他域是否包含此类机器。事实证明，`GC` 并非如此全局，Tabby 收到错误。

这是因为 Windows 2000 `GC` 仅限于其自己的林。Tabby 明智地咕噜并说服她的经理将他们的林升级到 Windows Server 2003。非常“猫性”地，[Cats.com](http://www.Cats.com) 中的 Enterprise Administrators 在升级完成后迅速处理了与 [Dogs.com](http://www.Dogs.com) 建立森林信任的先决条件。

这次，而不是生成错误，Tabby 的新升级的 `GC` 检查其数据库中的森林信任。当它找到一个时，它会查看森林信任受信任域对象，以查看其列出的名称后缀是否与目标 `SPN` 对应。果然找到了匹配项，并生成路由提示返回到 [Calico.cat.com](http://www.Calico.cat.com) `DC`，后者反过来提示 Tabby 的 workstation 需要去爬另一棵树。

毫不气馁，workstation 根据刚刚收到的路由提示，向 [Cats.com](http://www.Cats.com) 的森林根 `DC` 请求推荐到 [Dogs.com](http://www.Dogs.com) 森林根的其中一个 `DC`。这产生了更多的电子文书工作。现在 Calico workstation 必须向 [Dogs.com](http://www.Dogs.com) `KDC` 发出请求以获取访问 Onyx 的服务票据。不是一群中最聪明的灯泡，`KDC` 必须询问其在 [Dogs.com](http://www.Dogs.com) 域中的自己的 `GC` 服务器，以查看它是否知道此文件服务器。这次足够全局，找到了匹配项，`SPN` 返回到 [Dogs.com](http://www.Dogs.com) 森林根 `KDC`，后者将其发送回 Calico 子域中的 Tabby 的 workstation。

成功！好吧，几乎。重新开始，这次使用已解析的 `SPN`，workstation 与 [Calico.cats.com](http://www.Calico.cats.com) 中的 `KDC` 协商以让 Tabby 访问 Onyx，并收到适当的服务器服务票据。最后，通过一条由一个森林信任、两个树根域信任和一个父子域信任组成的信任路径，将服务票据直接发送到 Onyx，文件服务器检查 Tabby 的凭据并向她发送访问令牌。

`Windows Explorer` 打开并显示 `\\Onyx\\public` 文件夹中的文件名。Tabby 不知晓她的请求引发的复杂事件链，访问了文件。

## 森林信任的路由提示
