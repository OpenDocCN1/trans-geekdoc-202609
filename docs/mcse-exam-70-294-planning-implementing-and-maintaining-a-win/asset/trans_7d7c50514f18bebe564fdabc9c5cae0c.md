
如果您想使用与登录账户不同的授权，请使用 `rendom.exe` 的 `/user` 和 `/pwd` 命令行开关提供备用凭据。执行 [练习 4.22](#B9781931836944500106_1.xhtml#b0125) 以生成基线森林描述。

## 练习 4.22

### 生成当前森林描述文件

1. 使用企业管理员权限登录控制站。
2. 打开命令提示符，切换到 `RenameTools` 目录，并键入 `rendom /list`。
3. 键入以下命令以保存森林描述文件的副本以供将来参考：`copy domainlist.xml domainlist-save.xml`

`rendom.exe` 的 `/list` 选项在当前目录中创建一个名为 `domainlist.xml` 的 XML 编码文件。它包含您当前森林结构的文本描述，包括森林中所有应用程序目录分区和域目录分区的列表。您将找到每个域和应用程序目录分区的条目，由 `<Domain></Domain>` XML 标签界定，如 [图 4.53](#B9781931836944500106_1.xhtml#f0265) 所示。每个条目包含命名数据，其中包括分区根对象的对象 GUID、域或应用程序目录分区的 DNS 名称以及域的 NetBIOS 名称。应用程序目录分区没有 NetBIOS 名称。

![图 4.53 森林描述文件，domainlist.xml，由 Rendom.exe 生成](images/B9781931836944500106/f04-53-9781931836944.jpg)

图 4.53 森林描述文件，`domainlist.xml`，由 `Rendom.exe` 生成

在示例中，`domainlist.xml` 文件显示了一个包含两个域 Zoo.net 和 Fish.zoo.net 的森林结构，其 NetBIOS 名称分别为 ZOO 和 FISH。还有三个其他条目，与 Active Directory 集成 DNS 服务使用的应用程序目录分区相对应。这些应用程序目录分区也必须重命名：

■ DomainDnsZones.fish.zoo.net
■ DomainDnsZones.zoo.net
■ ForestDnsZones.zoo.net

应用程序目录分区的条目以 XML 注释的形式进行注释：

`<!— PartitionType: Application —>`

森林根域的条目也以 XML 注释的形式进行注释：

`<! — ForestRoot —>`

对于此过程，关键字段是由 `<DNSname></DNSname>` 和 `<NetBiosName></NetBiosName>` 标签界定的字段。

## 第 4 步：设计新的森林

根据初步步骤，您的新森林结构应得到充分记录。在此步骤中，您将把新结构叠加到旧结构之上，如步骤 3 中生成的 `domain-list.xml` 文件所述。您将使用文本编辑器编辑 `domainlist.xml` 文件并用新名称替换旧的域名。您还必须以相同的方式编辑应用程序目录分区的名称。当您重命名 Active Directory 域时，如果您使用的是 Active Directory 集成 DNS，则相应的 DNS 特定应用程序目录分区也必须重命名。如果不这样做，添加到网络中的新 DNS 服务器将不会自动加载存储在 DNS 特定应用程序目录分区中的 DNS 区域，并且将无法正常运行。

使用 `Notepad` 等简单的文本编辑器进行更改。请记住，此时您可以更改任何域的 NetBIOS 名称、DNS 名称或两者。此外，请注意更改受重命名父域影响的任何子域的名称。查看本章“Windows 2003 森林中的域重命名限制”部分中所述的域重命名限制，以检查所有名称更改是否符合良好的格式。

![b04-18-9781931836944](images/B9781931836944500106/b04-18-9781931836944.jpg)警告

请仔细检查此步骤，最好由不止一个人来确保更改完整且正确。这些是实际要实现的名称，任何拼写或层次结构错误都可能导致森林或域无法正常运行。如果您的目标结构不是您所期望的，您必须重新执行整个域重命名过程。

以下是名称更改的一些准则：

■ 将 DNS 名称从旧名称更改为新名称，即由标签 `<DNSname></DNSname>` 界定的字段。
■ 将 NetBIOS 名称从旧名称更改为新名称，即由标签 `<NetBiosName></NetBiosName>` 界定的字段。
■ 将域级 DNS 应用程序分区名称从旧名称更改为新名称，即 DomainDnsZones. `<domain DNS name>` 字段，由标签 `<DNSname></DNSname>` 界定。
■ 将森林级 DNS 应用程序分区名称从旧名称更改为新名称，即 ForestDnsZones. `</forest DNS name>` 字段，由标签 `<DNSname></DNSname>` 界定。
■ 不要更改由 `<Guid></Guid>` 标签界定的字段中表示的 GUID。

查看 [图 4.54](#B9781931836944500106_1.xhtml#f0270) 以了解在以下重构设计叠加后 `domainlist.xml` 文件的示例。在这种情况下，DNS 和 NetBIOS 名称都已更改：

![图 4.54 森林描述文件，domainlist.xml，定制为新的森林设计](images/B9781931836944500106/f04-54-9781931836944.jpg)

图 4.54 森林描述文件，`domainlist.xml`，定制为新的森林设计

■ Zoo.net 的顶级 DNS 名称已更改为在政治上更正确的名称 Naturepreserve.net，而其子域 fish.zoo.net 已更改为 Aquatics.naturepreserve.net。
■ ZOO 的 NetBIOS 名称已更改为 PRESERVE，而其子域的 NetBIOS 名称已从 FISH 更改为 AQUATICS。
■ 域级 DNS 应用程序分区名称已从 DomainDnsZones.fish.zoo.net 更改为 DomainDnsZones.aquatics.naturepreserve.net。
■ 域级 DNS 应用程序分区名称已从 DomainDnsZones.zoo.net 更改为 DomainDnsZones.naturepreserve.net。
■ 森林级 DNS 应用程序分区名称已从 ForestDnsZones.zoo.net 更改为 ForestDnsZones.naturepreserve.net。
■ GUID 字段未被修改。
■ 未为任何 Partition Type: Application 分配 NetBIOS 名称。

![b04-19-9781931836944](images/B9781931836944500106/b04-19-9781931836944.jpg)注意

如果您为 Active Directory 域拥有 Microsoft TAPI 动态目录，则可能拥有用于 TAPI 应用程序数据的应用程序分区。通常每个域有一个 TAPI 特定应用程序目录分区。当您重命名 Active Directory 域时，对应的 TAPI 特定应用程序目录分区不会自动重命名。如果存在，您也应更改它们。

`Rendom.exe` 将使用 `/showforest` 选项以用户友好的格式，使用文本缩进来反映域层次结构，在 `domainlist.xml` 文件中显示新的森林结构。在对 `domainlist.xml` 文件进行每次更改后，从 `Renametools` 目录中的命令提示符键入命令 `rendom /showforest` 以验证森林结构。在确定其正确之前，请在每次编辑后重新检查此文件的内容。

## 第 5 步：起草域重命名说明

现在您已经构建了新森林结构的定义，是时候生成将实现更改的域重命名说明了。这些说明将在森林中的每个 DC 上单独且远程执行。毫不奇怪，域命名主机在重命名过程中发挥着核心作用。`rendom.exe` 实用程序创建特殊格式的脚本，其中包含一系列目录更新，并将其写入森林的域命名主机上配置目录分区中的 `Partitions` 容器对象上的 `msDS-UpdateScript` 属性。

新的森林描述必须作为 XML 编码文件 `domainlist.xml` 可用，您已通过编辑上一步中的原始森林描述文件创建了该文件。按照以下步骤创建域重命名说明。
