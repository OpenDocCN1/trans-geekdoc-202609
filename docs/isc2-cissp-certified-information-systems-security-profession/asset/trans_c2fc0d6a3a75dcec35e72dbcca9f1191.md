
-   [基于角色的访问控制 (RBAC)](https://en.wikipedia.org/wiki/Role-based_access_control) 之所以容易与基于属性的访问控制 (DAC) 混淆，是因为两者都可以使用组来将用户组织为可管理的单元，但它们在部署和使用上存在区别。在 DAC 模型中，对象拥有者决定谁有权访问；在 RBAC 模型中，管理员确定主体权限并将相应权限分配给角色或组。在严格的 RBAC 模型中，管理员不直接向用户分配权限，而是通过将用户账户添加到角色或组来授予权限。

-   另一个与 RBAC 相关的方法是基于任务的访问控制 (TBAC)。TBAC 与 RBAC 类似，但不再是分配到一个或多个角色，而是为每个用户分配一个任务数组。这些项都与与用户账户关联的已分配工作任务有关。在 TBAC 下，关注点是通过已分配的任务来控制访问，而不是通过用户身份。

#### Rule-Based Access Controls

-   *基于规则的访问控制* 模型使用一组规则、限制或过滤条件来决定系统上可以发生什么以及不可以发生。它包括向主体授予对象的访问权限，或向主体授予执行操作的能力。基于规则的访问控制模型的一个显著特征是它们拥有适用于所有主体的全局规则。

-   一个常见的基于规则的访问控制模型示例是防火墙。防火墙在 ACL（访问控制列表）中包含一组规则或过滤条件，由管理员定义。防火墙检查所有经过它的流量，仅允许符合其中一条规则的流量通过。

-   防火墙包含一个最终规则（称为隐式拒绝规则），该规则拒绝所有其他流量。例如，最后一条规则可能是 `deny all all`，表示防火墙应阻止网络内或外所有未被之前规则明确允许的流量。换句话说，如果流量未满足任何先前明确定义的规则条件，则该最终规则确保流量被阻止。该最终规则有时会在 ACL 中可见，以便查看；有时则作为隐含的最终规则存在，但并未在 ACL 中明确列出。

#### Attribute Based Access Controls

-   传统的基于规则的访问控制模型包含对所有主体（如用户）均等适用的全局规则。然而，基于规则的访问控制的高级实现是 *Attribute Based Access Control (ABAC)* 模型。ABAC 使用包含多个属性的策略来定义规则。许多软件定义网络（SDN）应用程序使用 ABAC 模型。

-   属性几乎可以是用户、网络和网络设备的几乎任何特征。例如，用户属性可以包括组成员身份、工作部门以及使用的设备（如台式机或移动设备）。网络可以是本地内部网、无线网络、内部网或广域网（WAN）。设备可以包括防火墙、代理服务器、Web 服务器、数据库服务器等。

-   以 CloudGenix 开发的软件定义广域网（SD‑WAN）解决方案为例，它实现了策略以允许或阻止流量。管理员使用简洁的语言声明创建 ABAC 策略，例如“允许经理通过平板电脑或智能手机访问 WAN”。这使得经理角色的用户能够使用平板电脑或智能手机访问 WAN。由此可见，这提升了基于规则的访问控制模型的灵活性。基于规则的访问控制适用于所有用户，而 ABAC 可以更精准地控制。

#### Mandatory Access Controls

-   *强制访问控制 (MAC)* 模型依赖于分类标签。每个分类标签代表一个安全 *域*，即安全策略的领域。安全域是一组共享相同安全策略的主体和对象的集合。例如，安全域可以标记为 **Secret**，MAC 模型会以相同的方式保护所有标记为 Secret 的对象。只有拥有匹配的 Secret 标签的主体才能访问标记为 Secret 的对象。此外，获得 Secret 标签的要求对所有主体都是相同的。

-   用户的标签是根据其清除级别（一种特权形式）分配的。对象同样拥有标签，指示其分类或敏感程度。例如，美国军队使用 **Top Secret**、**Secret** 和 **Confidential** 标签对数据进行分类。管理员可以将 Top Secret 数据的访问权限授予拥有 Top Secret 清除级别的用户，但不能将其授予拥有较低清除级别（如 Secret 或 Confidential）的用户。

-   私有企业组织通常使用 **confidential（专有）**、**private**、**sensitive** 和 **public** 等标签。虽然政府使用法律规定的标签，私有企业则可自由选择自己喜欢的标签。

-   MAC 模型常被称为 *lattice-based* 模型。[Figure 14.3](#c14.xhtml#figure14-3) 提供了一个基于网格的 MAC 模型示例。它类似于花园中的栅栏，例如用于训练攀爬玫瑰的玫瑰栅栏。水平线标记为 **Confidential**、**Private**、**Sensitive** 和 **Public**，表示分类级别的上限。例如，Public 与 Sensitive 之间的区域包含标记为 Sensitive 的对象（上界）。拥有 Sensitive 标签的用户可以访问 Sensitive 数据。

-   ![FIGURE 14.3 A representation of the boundaries provided by lattice-based access controls](images/c14f003.jpg)

[**FIGURE 14.3**](#c14.xhtml#figureanchor14-3) A representation of the boundaries provided by lattice-based access controls

-   MAC 模型还允许标签标识更细致的安全域。在 **Confidential** 区域（位于 Private 与 Confidential 之间）内，有四个独立的安全域，分别标记为 **Lentil**、**Foil**、**Crimson** 和 **Matterhorn**。这些域均包含 Confidential 数据，但通过将其放在独立的隔离区中提供了额外的保护层。拥有 Confidential 标签的用户还必须拥有相应的域标签才能访问这些数据。例如，要访问 Lentil 数据，用户需要同时拥有 **Confidential** 标签和 **Lentil** 标签。

-   同样，标记为 **Domino**、**Primrose**、**Sleuth** 和 **Potluck** 的隔离区包含 **Private** 数据。访问该区域的用户需要 **Private** 标签以及该隔离区中的任一标签。

-   [Figure 14.3](#c14.xhtml#figure14-3) 中的标签是二战军事行动的名称，但组织可以使用任何名称。关键在于这些区域为数据等对象提供了额外的隔离层。注意，Sensitive 数据（位于 Public 与 Sensitive 之间）没有额外标签。拥有 Sensitive 标签的用户可以被授予访问任何标记为 Sensitive 的数据的权限。

-   组织内部人员会识别标签、定义其含义以及获得标签的要求。管理员随后将标签分配给主体和对象。标签到位后，系统依据已分配标签来决定访问权限。

-   使用 MAC 模型的隔离层强制执行 *需要知道* 原则。拥有 **Confidential** 标签的用户并不会自动获得 Confidential 区域内的隔离域访问权限。如果其工作需要访问特定数据（例如标记为 **Crimson** 的数据），管理员可以为其分配 **Crimson** 标签，从而授予访问该隔离域的权限。

-   MAC 模型采用 *隐式拒绝* 策略，即未明确授予访问权限的情况下，系统会拒绝访问相关数据。MAC 模型比 DAC 模型更安全，但相对更不灵活且难以扩展。

