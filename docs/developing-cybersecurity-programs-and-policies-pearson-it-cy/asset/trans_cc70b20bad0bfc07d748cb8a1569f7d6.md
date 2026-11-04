
Several of these solutions provide application programming interfaces (APIs) that provide a deep level of integration with monitored SaaS, IaaS, PaaS, and IDaaS solutions. They provide advanced cloud DLP functionality that includes out-of-the-box policies designed to help administrators maintain compliance.

An important benefit of cloud-based DLP solutions is that they allow you to monitor data at rest within platforms via APIs and provide a comprehensive picture of user activity through retroactive monitoring capabilities. Security administrators can mitigate risk efficiently using configurable, automated response actions, including encryption, quarantine, and end-user notification.

Data loss doesn’t always take place because of a complex attack carried out by an external attacker; many data loss incidents have been carried out by internal (insider) attacks. Data loss can also happen because of human negligence or ignorance—for example, an internal employee sending sensitive corporate email to a personal email account, or uploading sensitive information to an unapproved cloud provider. This is why maintaining visibility into what’s coming as well as leaving the organization is so important.

Data loss prevention (DLP) tools are designed to detect and prevent data exfiltration (unauthorized release or removal of data). DLP technologies locate and catalogue sensitive data (based on a predetermined set of rules or criteria), and DLP tools monitor target data while in use, in motion, and at rest. [表 5-3](#ch05.xhtml#ch05tab03) summarizes some DLP tools and where they are placed in the network.

**表 5-3** DLP 位置/部署

| **DLP 工具** | **描述/部署位置** |
|---|---|
| 网络型（本地部署） | 基于网络（硬件或虚拟设备）处理传输中的数据，通常位于网络边界。 |
| 存储型 | 存储型（软件）在长期存储（归档）上运行。 |
| 端点型 | 端点型（软件）在本地设备上运行，专注于使用中的数据。 |
| 云端型（异地） | 云端型在云中运行，涵盖使用中、传输中和静态的数据。 |

DLP 解决方案可用于识别和控制端点端口以及阻止对可移动介质的访问。

* 通过类型（例如 USB 闪存盘、CD 烧录机、智能手机）、制造商、型号和 MAC 地址识别连接到您网络的可移动设备/介质。
* 通过端点端口（包括 USB、FireWire、Wi-Fi、调制解调器/网络网卡和蓝牙）控制和管理可移动设备。
* 要求加密，限制文件类型，限制文件大小。
* 根据人员、时间、文件类型和数量提供设备使用和数据传输的详细取证信息。

## 摘要

您可能听说过“安全通过隐蔽”这一说法。该说法暗示资产隐藏程度与其安全性之间存在比例关系。该概念的问题在于，将我们的信息和系统锁起来既不切实际，也不可取。信息资产对组织具有价值，并且经常在日常运营中使用以完成其使命。“安全通过隐蔽”的反面是“安全通过分类和标记”。保护信息资产或系统的最佳方式是识别机密性、完整性和可用性（CIA）要求，然后应用适当的保护措施和处理标准。识别和区分的过程称为 *分类*。信息所有者负责正确识别和分类其负责的信息。信息保管人负责实施安全控制。

FISMA 要求联邦机构信息所有者根据 FIPS-199 中概述的标准，将其信息和信息系统分类为低、中或高安全级别。信息在机密性方面根据未经授权披露的影响以及信息的使用情况进行评估，在完整性方面根据未经授权修改或破坏的影响进行评估，在可用性方面根据访问或使用信息中断的影响进行评估。五个特殊分类保留用于国家安全相关信息，表示特殊访问和处理要求：绝密、机密、保密、非机密和敏感但未分类（SBU）。降低分类的过程称为 *解密*。提高分类的过程称为 *重新分类*。

私营部门没有可比的分类要求。然而，多项州和联邦法规要求所有组织保护特定类别的信息。最广泛的类别是非公开个人资料（NPPI）。NPPI 是被视为个人性质、受公开可用性约束的信息，若被披露即构成隐私侵犯。私营部门组织通常采用三级或四级分类系统，以考虑法律、隐私和商业保密要求。标记是向信息保管人和用户传达所分配分类的媒介。处理标准告知保管人和用户如何处理他们使用的信息和交互的系统。

信息系统提供了处理、存储和传输信息资产的方式和场所。维护最新的硬件和软件资产清单非常重要。硬件资产是可见且有形的设备和介质。软件资产是提供硬件、用户和数据之间接口的程序或代码。描述符可能包括资产的用途、其位置、称为 MAC 地址的唯一硬件识别号、称为 IP 地址的唯一网络标识符、主机名和域名。

组织资产管理政策包括信息所有权、信息分类、处理和标记要求以及信息系统清单。

在本章中，您了解到 DLP 是检测任何离开您组织的敏感电子邮件、文档或信息的技术和能力。这通常被称为 *数据外泄* 或 *数据挤出*。数据外泄是通过手动方式（由具有对该系统物理访问权限的人员执行）从系统或网络未经授权转移数据，也可能通过恶意软件或通过网络系统入侵而自动执行。

## 测试你的技能

### 多选题

**[1](#app02.xhtml#ch05qu-1).** 以下哪个术语最能描述一种可定义的信息，无论以何种方式存储，都被认为是具有组织价值的？

**A.** NPPI

**B.** 信息资产

**C.** 信息系统

**D.** 分类数据

**[2](#app02.xhtml#ch05qu-2).** 信息系统 \_\_\_\_\_\_\_\_\_\_, \_\_\_\_\_\_\_\_\_\_, 和 \_\_\_\_\_\_\_\_\_\_ 信息。

**A.** 创建、修改和删除

**B.** 分类、重新分类和解密

**C.** 存储、处理和传输

**D.** 使用、标记和处理

**[3](#app02.xhtml#ch05qu-3).** 信息所有者负责以下哪项任务？

**A.** 分类信息

**B.** 维护信息

**C.** 使用信息

**D.** 注册信息

**[4](#app02.xhtml#ch05qu-4).** 以下哪个角色负责实施和维护安全控制并报告疑似事件？

**A.** 信息所有者

**B.** 信息供应商

**C.** 信息用户

**D.** 信息保管人

**[5](#app02.xhtml#ch05qu-5).** FIPS-199 要求联邦政府信息和信息系统被分类为 \_\_\_\_\_\_\_\_\_\_\_\_。
