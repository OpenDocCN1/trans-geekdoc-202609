
# 组策略

## 问答

### 访问组策略设置
A: 可以通过安全组权限来过滤对组策略设置的访问。默认情况下，已验证用户组对任何默认或新创建的 GPO 都启用了应用组策略权限。更改 GPO 的安全组权限将允许您控制谁可以处理 GPO 中的设置。

### Q: 如果我有想要应用到多个 OU 的组策略设置，我是否必须为每个 OU 创建具有相同设置的 GPO？
A: 不必。您可以创建一个单一的 GPO 并将其链接到多个 OU，以便在每个 OU 上应用相同的策略集。这种将策略设置应用于多个组的方法，如果出于任何原因需要更改策略设置，将有助于减轻管理开销。这样，您只需更改一个对象即可使设置生效。否则，在进行更改时您必须定位并编辑每个 GPO。

### Q: 委派组策略管理控制的优点和缺点是什么？
A: 如果您拥有一个非常大的 Active Directory 部署，其中包含多个域和具有不同需求的 OU，将组策略管理委派给他人可以减轻您的系统管理负担。对于一个非常大的组织来说，单个人或小型组织很难跟上其各种需求。委派控制将允许更接近各个下属组织的人更有效地管理策略需求。这里的主要缺点是组织问题。一旦您将缰绳交给另一人或另一组，您可能会失去对他们所做更改的了解。如果您最终负责整个组织的故障排除，不知道 GPO 中所做的更改可能会阻碍您的故障排除速度。委派控制可以在前期为您节省管理时间，但也可能在后期增加您的故障排除时间。

### Q: 重定向文件夹总是好主意吗？
A: 有些人认为只要能做某事就应该去做。在组织内部设置用户环境时，这并不总是如此。在某些组织中，重定向文件夹将带来显著的好处：通过将文件夹重定向到定期备份的网络共享来提高数据安全性，通过从公共的、写保护的位置提取桌面和“开始”菜单文件夹来强制执行标准等等。然而，不重定向文件夹的理由也一样多。在地理上庞大的组织中到处旅行的用户可能会发现，当他们从与重定向文件夹所在位置通过非常慢的 WAN 链路相连的位置登录时，访问数据需要等待很长时间。此外，如果存储其重定向文件夹的服务器发生灾难性硬件故障，用户在问题修复期间数小时或数天无法访问数据，他们会如何反应？与任何网络技术一样，在实施之前应进行研究和规划，以评估在您特定环境中重定向文件夹的影响。

### Q: 我可以使用软件限制策略来防止计算机病毒在我组织中的传播吗？
A: 可以，但不能作为完整解决方案。使用软件限制策略，您可以限制某些类型软件的执行，并且可以查找要阻止的特定程序代码。与任何好的病毒防护软件一样，这些“规则”必须定期更新，以跟上您想要阻止运行的软件类型的变化。系统管理员可能犯的最坏错误是为软件限制创建一组规则然后再也不去查看它们。设置软件限制策略的任务的一部分是定期维护它们。

## 自测

快速答案键在自测问题之后。有关本章以及本书其他章节中自测问题的完整问题、答案和解释，请参阅自测附录。

### 理解组策略
1. 您刚刚设置了一个 Windows Server 2003 Active Directory 网络，并希望使用组策略来控制用户配置。您已在域中的某些计算机上配置了本地策略，并且还希望配置一些站点和 OU 策略以实现更精细的控制，但您担心不同级别的策略会“相互抵消”。以下哪种类型的 GPO 会覆盖在域级别应用的设置？（选择所有适用项。）
A. Local
B. OU
C. Site
D. Domain
2. 您被要求在新的 Windows Server 2003 Active Directory 网络中设置组策略环境。您的主管询问本地计算机设置是否会覆盖在域 GPO 中应用的设置。您向他解释，一般来说，后处理的策略通常优先于先前设置的策略，组策略按什么顺序应用？
A. OU policies, domain policies, site policies, local policies
B. Site policies, domain policies, OU policies, local policies
C. Local policies, site policies, domain policies, OU policies
D. Local policies, OU policies, domain policies, site policies
3. 您的部门刚刚聘请了一名新的初级系统管理员，并要求您对其进行培训。该学员曾使用过 Active Directory，但从未使用过组策略。他一直在规划模式下运行 RSoP，以了解不同组策略设置存储的位置，但他一直感到困惑，因为他在报告中没有看到计算机设置和用户设置之间相同的分组。报告中他应该看到的用户和计算机配置的主要策略类型是什么，以控制台树中的节点表示？
A. Assign scripts, Manage applications, Redirect folders, and Change Registry settings
B. Software settings, Windows settings, and Administrative templates
C. Security settings, Account settings, and Software settings
D. Local settings, Site settings, Domain settings, and OU settings
4. 您在一家大型公司工作，该公司刚刚通过合并收购了另一家公司。被收购公司已将其 Active Directory 结构合并到您的林中。新团队希望对其目录部分保持控制，但您希望确保域策略设置不会被在 OU 级别应用的 GPO 所更改。您将如何实现这一点？
A. Set the No Override option on the domain GPO.
B. Set the Block Policy Inheritance option on the domain GPO,
C. Set the Disable Domain Inheritance option on the domain GPO,
D. Unlink the domain GPO from the domain container.

### 规划组策略策略
5. 您被要求为一家大型、地理分布广泛的公司实施组策略。该公司用户习惯于能够快速登录，并且您不希望在添加组策略设置时显著减慢登录过程。以下哪些方法可以在用户登录时减少组策略的处理时间？（选择所有适用项。）
A. Apply the Block Policy Inheritance setting on the OU closest to the logon object to keep all other policies from processing.
B. Set the Disable Computer Configuration Settings or Disable User Configuration Settings options in the GPO options.
C. Filter access to the GPO with WMI settings.
D. Filter access to the GPO with security group permissions.
6. 您的主管要求您为市场部复制销售部的组策略设置。一位同事建议，与其为市场部 OU 创建新的 GPO，不如直接将现有的销售 GPO 链接到市场部 OU。将 GPO 链接到容器的准则是什么？
A. Each GPO can be linked to only one container.
