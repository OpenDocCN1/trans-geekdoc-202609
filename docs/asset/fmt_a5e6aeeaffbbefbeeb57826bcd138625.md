
Some organizations choose to utilize `off-site storage` for their backup media, either at a site they own and operate or through a third-party service like Iron Mountain, which specializes in storage of secure backups in environmentally controlled facilities. Off-site storage, a form of geographic diversity, helps ensure that a single disaster cannot destroy an organization's data entirely. As in our earlier discussion of geographic diversity, distance considerations are also important to ensure that a single regional disaster is unlikely to harm the off-site storage.

Although traditional backup methods have used on-site storage options like tape drives, `storage area networks (SANs)`, and `network attached storage (NAS)` devices, cloud and third-party off-site backup options have continued to become increasingly common. A few important considerations come into play with cloud and off-site third-party backup options:

*   **Bandwidth requirements for both the backups themselves and restoration time if the backup needs to be restored partially or fully**. Organizations with limited bandwidth or locations with low bandwidth are unlikely to be able to perform a timely restoration. This fact makes off-site options less attractive if quick restoration is required, but they remain attractive from a disaster recovery perspective to ensure that data is not lost completely.
*   **Time to retrieve files and cost to retrieve files**. Solutions like Amazon's Glacier storage focus on low-cost storage but have higher costs for retrieval, as well as slower retrieval times. Administrators need to understand storage tiering for speed, cost, and other factors, but they must also take these costs and technical capabilities into account when planning for the use of third-party and cloud backup capabilities.
*   **Reliability**. Many cloud providers have extremely high advertised reliability rates for their backup and storage services, and these rates may actually beat the expected durability of local tape or disk options.
*   **New security models required for backups**. Separation of accounts, additional controls, and encryption of data in the remote storage location are all common considerations for use of third-party services.

### Response and Recovery Controls

When failures do occur, organizations need to respond and then recover. Response controls are controls used to allow organizations to respond to an issue, whether it is an outage, a compromise, or a disaster. Recovery controls and techniques focus on returning to normal operations. Because of this, controls that allow a response to compromise or other issues that put systems into a nontrusted or improperly configured state are important to ensure that organizations maintain service availability. The Security+ exam focuses on a handful of common response and recovery controls, which you should make sure you are familiar with.

An important response control in that list is the concept of `nonpersistence`. This means the ability to have systems or services that are spun up and shut down as needed. Some systems are configured to revert to a known state when they are restarted; this is common in cloud environments where a code-defined system will be exactly the same as any other created and run with that code. Reversion to a known state is also possible by using snapshots in a virtualization environment or by using other tools that track changes or that use a system image or build process to create a known state at startup.

One response control is the ability to return to a last-known good configuration. Windows systems build this in for the patching process, allowing a return to a checkpoint before a patch was installed. Change management processes often rely on a last-known good configuration checkpoint, via backups, snapshots, or another technology, to handle misconfigurations, bad patches, or other issues.

When loads on systems and services become high or when components in an infrastructure fail, organizations need a way to respond. High-availability solutions like those we discussed earlier in the chapter, including load balancing, content distribution networks, and clustered systems, provide the ability to respond to high-demand scenarios as well as to failures in individual systems. `Scalability` is a common design element and a useful response control for many systems in modern environments where services are designed to scale across many servers instead of requiring a larger server to handle more workload. You should consider two major categories of scalability:

*   **Vertical scalability** requires a larger or more powerful system or device. Vertical scalability can help when all tasks or functions need to be handled on the same system or infrastructure. Vertical scalability can be very expensive to increase, particularly if the event that drives the need to scale is not ongoing or frequent. There are, however, times when vertical scalability is required, such as for every large memory footprint application that cannot be run on smaller, less capable systems.
*   **Horizontal scaling** uses smaller systems or devices but adds more of them. When designed and managed correctly, a horizontally scaled system can take advantage of the ability to transparently add and remove more resources, allowing it to adjust as needs grow or shrink. This approach also provides opportunities for transparent upgrades, patching, and even incident response.

Moves to the cloud and virtualization have allowed scaling to be done more easily. Many environments support horizontal scaling with software-defined services and systems that can scale at need to meet demand, while also allowing safer patching capabilities and the ability to handle failed systems by simply replacing them with another identical replacement as needed.

Not every environment can be built using horizontally scalable systems, and not every software or hardware solution is well suited to those scenarios. At the same time, natural and human-created disasters, equipment failures, and a host of other issues can impact the ability of an organization to operate its facilities and datacenters.

### 站点弹性与物理安全控制

#### 站点弹性

当组织需要规划在其数据中心或其他托管基础设施的位置离线时如何运作时，会将站点弹性选项作为一种响应控制进行考量。*站点弹性* 历来是组织的主要设计要素，对某些组织而言，它仍然是关键设计要素。用于站点弹性的灾难恢复站点主要有三种类型：

*   **热站点** 拥有运行组织所需的所有基础设施和数据。因此，一些组织全天候运行它们，在多个站点之间分流流量和负载，以确保站点正常运行。这种方法还能确保在紧急情况下有员工到位。
*   **温站点** 拥有组织所需工作的部分或全部系统，但实时数据未就位。由于硬件成本，温站点维护费用高昂，但由于系统已就绪且大部分配置完成，它们可以缩短总恢复时间。它们在热站点和冷站点之间平衡了成本与能力。
*   **冷站点** 拥有空间、电力，通常还有网络连接，但未预置系统或数据。这意味着发生灾难时，组织虽有去处，但必须自行携带或采购系统。冷站点具有挑战性，因为某些灾难会阻碍硬件采购，且数据必须从灾难发生时存储数据的另一设施传输过来。然而，冷站点也是三种类型中维护成本最低的选项。

在上述每种场景中，都需要考虑 *恢复顺序*。恢复顺序决策在系统和服务对组织运营的关键性与其他基础设施就绪并运行以允许各组件上线、安全且正常运行的需求之间取得平衡。站点恢复顺序可能包含如下列表：

1.  恢复网络连接和堡垒主机或 Shell 主机。
2.  恢复网络安全设备（防火墙、IPS）。
3.  恢复存储和数据库服务。
4.  恢复关键业务服务器。
5.  恢复日志记录和监控服务。
6.  尽可能恢复其他服务。

每个组织和基础设施设计都会根据对组织功能需求的关键性以及数据中心或服务运行环境中的依赖关系，做出略有不同的恢复顺序决策。

越来越多的设计利用云来替代现有恢复站点或与其协同工作。主要云基础设施供应商跨多个地理区域进行设计，且通常在一个区域内链接多个数据中心。这意味着组织无需投资热站点，而是可以在云托管环境中构建和部署基础设施，然后使用工具将环境复制到另一个区域，或者从一开始就设计（或重新设计）架构以利用多区域优势。由于云服务通常按使用量定价，设计和构建可按需在另一位置启动的基础设施，有助于应对容量规划和灾难恢复场景。

#### 物理安全控制

安全从业者通常关注技术控制，但组织最重要的防线之一是其部署的物理控制集合。对系统、设施和网络的物理访问是绕过技术控制最简单的方式之一，无论是直接访问机器、窃取驱动器或设备，还是插入受信网络以绕过保护其免受外部世界侵害的多层网络安全控制。

### 站点安全

防止物理访问的第一步是实施站点安全计划。站点安全会审视组织使用的整个设施，并根据与每个特定位置相关的威胁和风险实施安全计划。这意味着组织在不同位置使用的设施，或作为不同业务活动一部分的设施，通常会有不同的站点安全计划和控制措施。

一些组织使用 *工业伪装* 来帮助保护自身。常见示例是公司为呼叫中心选择的不起眼位置。与其让呼叫中心成为愤怒客户寻找的显眼地点，许多中心基本无标识且外观普通。虽然“通过隐匿实现安全”不是合法的技术控制，但在物理世界中，不易被注意到有助于防止许多原本可能发生的入侵。

许多设施将围栏作为第一道防线。*围栏* 既通过让设施看起来难以进入起到威慑作用，又作为实际的物理防御。高安全设施将使用多重围栏、顶部的刺铁丝或刀片刺绳及其他技术来增强围栏提供的安全性。围栏材料、高度、入口位置及设计等多种因素均纳入安全围栏的考量范围。

第二种常见的物理控制是设置挡车柱。挡车柱是如图 9.1 所示的柱子或其他障碍物，用于防止车辆穿越某区域。挡车柱外观可能像柱子、石柱甚至花盆，但其目的始终如一：防止车辆进入。一些挡车柱设计为可拆卸甚至机械驱动，可根据需要升降。许多挡车柱设在入口前，以防止意外和利用车辆的蓄意袭击。

*照明* 在外部和内部安全中发挥作用。不留阴影或黑暗区域的明亮照明用于阻止入侵者，并让员工感到更安全。自动照明还能指示员工活动区域，让保安和其他员工知晓人员所在位置。

![图 9.1 挡车柱](img/c09f001.png)

**图 9.1** 挡车柱
