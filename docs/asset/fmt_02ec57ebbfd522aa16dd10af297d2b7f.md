
# 物联网 2.0 智能计算、大数据分析与区块链技术

![](img/coverpage.jpg)

*CRC Press is an imprint of Taylor & Francis Group, LLC*

Reasonable efforts have been made to publish reliable data and information, but the author and publisher cannot assume responsibility for the validity of all materials or the consequences of their use. The authors and publishers have attempted to trace the copyright holders of all material reproduced in this publication and apologize to copyright holders if permission to publish in this form has not been obtained. If any copyright material has not been acknowledged, please write and let us know so we may rectify in any future reprint.

Except as permitted under U.S. Copyright Law, no part of this book may be reprinted, reproduced, transmitted, or utilized in any form by any electronic, mechanical, or other means, now known or hereafter invented, including photocopying, microfilming, and recording, or in any information storage or retrieval system, without written permission from the publishers.

For permission to photocopy or use material electronically from this work, access [www.copyright.com](http://www.copyright.com) or contact the Copyright Clearance Center, Inc. (CCC), 222 Rosewood Drive, Danvers, MA 01923, 978-750-8400. For works that are not available on CCC please contact mpkbookspermissions@tandf.co.uk

*Trademark notice*: Product or corporate names may be trademarks or registered trademarks and are used only for identification and explanation without intent to infringe.

ISBN: 978-1-003-32623-6 (ebk)

DOI: [10.1201/9781003326236](https://dx.doi.org/10.1201/9781003326236)

Typeset in Times New Roman

by SPi Technologies India Pvt Ltd (Straive)

# 前言

作为本书的编辑，我们旨在帮助读者深入理解物联网（IoT）技术、大数据分析和区块链技术的广泛应用，以及这些技术如何整合以造福社会。鉴于这些技术在全球语境下高度多样、快速演变且经济新兴，所有作者均致力于分享关于增强版 IoT、IoT 中大数据集成、区块链在保障 IoT 网络中的作用以及机器学习在 IoT 网络系统整体应用方面的观点。

![](img/front1_B.jpg)

![](img/front2_B.jpg)

National Institute of Technology Jamshedpur, India

## 3.2.3.2.1 Cluster Computing

每台计算机通过高带宽网络相连。因此，集群计算通过降低主帧计算的成本，成为一个很好的替代方案。互联网的出现使全球的本地网络能够相互连接并在一定限制下共享资源，这被称为 Internet computing。

## 3.2.3.2.2 Grid Computing

它指位于不同物理区域的系统通过 Internet 相互连接的网络。这些系统由专用软件（如中间件）控制，使用户可以远程访问和使用资源。网格服务本质上是通过中间件管理对网格资源访问的过程。网格服务具备多种访问控制和安全服务，从读取库和数据库中的数据的权限到使用大容量存储设施的权限。距离问题得到解决，但远距节点提供高带宽成为限制因素。

## 3.2.3.2.3 Virtualization

虚拟化将软件环境与物理基础设施分离，使得同一台机器可以同时运行多个操作系统和应用程序。虚拟化是 Amazon、Google 以及众多云服务提供商使用的技术。

### 3.2.3.3 Phase 3 – Cloud Phase

在将网格计算与虚拟化技术相结合后，需要良好的硬件和 Internet 资源。因此，云的发展才刚刚开始。

#### 3.2.3.3.1 Web 2.0 and Web 3.0

Web 应用主要借助云计算提供的按需服务，尤其是 Web 2.0 和 Web 3.0，它们通过利用 Internet 作为主要公用事业和平台，提升创意、信息共享和用户协作。用户通过宽带连接 uninterrupted 地访问 Internet 服务的连续性由 Web 3.0 技术实现。Web 3.0 技术为云计算提供服务保障。

#### 3.2.3.3.2 Service Orientation

服务导向将云资源与各类业务服务相结合，这些服务包括降低依赖度的组件。因此，业务流程需要采用服务导向，以利用现有资源。

#### 3.2.3.3.3 Cloud Computing

许多公司开始提供云存储、基础设施和管理服务。最初称为公用计算，今天云计算已成为现实。存在多种云模型和服务类型，将在后续章节中详细描述。

### 3.2.4 Cloud Computing Architecture and Services

云的架构包含四个主要层次，如图 3.4 所示。

![Figure 3.4 Cloud computing architecture.](img/fig3_4_B.jpg)

Figure 3.4 Cloud computing architecture.

*   **Layer 1** 称为客户端基础设施，它使用户与云之间通过图形用户界面（GUI）进行交互。换句话说，它是前端，通常是简单的 Web 浏览器。该层代表拥有足够计算能力的设备，即用户或客户端，用于请求云访问。

*   **Layer 2** 称为网络层，负责维持用户与云之间的连接。该层被视为云骨架，所有网络服务在此向客户端提供，因此所有云服务都高度依赖于此层。例如，在公共云中，该层实际上是 Internet，通常位于云用户不知晓但可通过 Internet 全球访问的地点。私有云则可通过局域网（LAN）将用户与云相连。

*   **Layer 3** 称为云管理层，负责管理所有云实体，包括用户和访问控制、数据、应用以及服务。精确地说，该层负责在用户与云运营商之间达成服务级协议 [5]。根据 NIST，定义了三种基本服务模型：SaaS、PaaS 和 IaaS，如表 3.1 所示。用户服务模型的分类在 Layer 3 根据与云用户共享云组件的协议来定义，即 Software-as-a-Service（SaaS）、Platform-as-a-Service（PaaS）和 Infrastructure-as-a-Service（IaaS） [5]。该层集成了负责云资源共享和管理的软件，包括服务器级别的调度和配置、工作负载优化、服务器和工作负载的优化，以及组织内部的云控制。Figure 3.4 展示了该层的六个组件：

## 表 3.1 云服务模型

| 服务模型 | 用户类型 | 资源管理 | 示例 |
| --- | --- | --- | --- |
| 软件即服务 SaaS | 业务用户 | 业务应用、Web 服务、多媒体 | Google Apps、邮件、计费和工资、Facebook、YouTube |
| 平台即服务 PaaS | 开发人员、网络架构师、部署者 | 软件框架（Java、.Net）、存储、数据库、操作系统、运行时环境 | Microsoft Azure、Google App Engine |
| 基础设施即服务 IaaS | 系统管理员 | 虚拟机、CPU、内存、操作系统、负载均衡、Internet、带宽供应 | Amazon EC2、GoGrid、Flexiscale、数据中心 |

1.  **应用**：各种应用软件均可进行供应。

2.  **数据**：存在两种数据，要么结构化，要么非结构化，取决于客户的需求。可以从图 3.4 观察到 SaaS 与应用和数据组件相关联。SaaS 包含的应用示例有 Gmail、Facebook、YouTube 和 Dropbox。

3.  **运行时**：该组件为虚拟机提供运行时环境和执行环境。

4.  **中间件**：这是一种软件，为应用提供验证、消息、API 监督等必要服务和功能。

5.  **操作系统 (OS)**：它是处理存储、执行和外设等所有基本管理任务的核心软件。PaaS 与运行时、中间件和操作系统组件相关联。GAE 等软件框架以及 Microsoft Azure 属于此服务。

6.  **虚拟化**：它是指创建硬件或软件资源的虚拟抽象，而不是实际的 OS、服务器、存储设备或网络等资源的实例，如操作系统、服务器、存储设备或网络。IaaS 属于虚拟化组件和第 4 层。IaaS 相关的服务示例包括虚拟机、Amazon Web Services、Go Greed、Rack Space 等。这是面向管理员的服务层级。

*   **第 4 层** 也称为硬件层，由实际硬件资源组成。例如，数据中心可用于前端公有云和私有云的后端。数据中心包含各种网络系统和基础设施，供企业处理大容量数据。由于组织数据中心旨在保护资源，云服务提供商和不同组织始终保持和谐合作。

    下面提供对每种云服务模型的更详细视图：

    1.  **软件即服务 (SaaS)**：云服务提供商 (CSP) 将运行在云上的应用发布给云服务客户 (CSC)。应用可通过不同类型的客户端系统访问，如客户邮件、专用编程接口或集成开发环境 (IDE)。CSC 没有能力操纵或控制云基础结构（网络实体、电力、存储、系统以及应用）。响应迅速且及时的应用无法从 SaaS 中受益。相反，最可能适用 SaaS 的是竞争对手使用的应用，例如邮件；按需、周期性高峰出现的应用如计费和工资；移动销售管理软件；以及短期协作软件项目。

    2.  **平台即服务 (PaaS)**：在此服务模型中，CSP 拥有的平台实例被租给 CSC，以便在 CSP 的平台上部署其自有的编程应用。除了已部署的应用和 CSC 可自行设置的受限用户配置和设置外，核心云基础设施（网络、服务器、处理器和操作系统）完全由 CSP 管理 [12]。用户可以控制云应用，并可能将其与管理和配置相结合。这些设施包括通用描述发现和集成 (UDDI)、内容、会话和知识管理、设备集成与测试、以及沙箱。

    3.  **基础设施即服务 (IaaS)**：在此服务类别中，CSP 拥有的基础设施（通常是虚拟化的处理、存储和其他资源）被提供给 CSC。CSC 可以在租用的基础设施上部署和运行不同类型的软件，如操作系统和编程环境。核心云基础设施仍然完全由 CSP 控制，但 CSC 可以控制其在 CSP 基础设施上部署的所有应用，包括针对主机设备的特定安全和网络设置。动态分配可扩展资源、便捷的计费以及多用户共享硬件是 IaaS 模型的 essential 特征。在需求波动、公司快速增长或新业务仅需要计算资源的情况下，IaaS 模型非常有用。云服务模型也在演进，其他更具体的服务类别包括分析即服务 (AaaS)、网络即服务 (NaaS)、移动后端即服务 (MBaaS)、移动网络即服务 (MNaaS) 和通信即服务 (CaaS)。

    现有的服务和使能器是云计算技术成功的动因，或者说是云计算的益处所对应的因素。这些使能器可以列出如下：

    1.  **虚拟化**：虚拟化的主要功能是通过最小化实际物理硬件及其所需的软件资源，为云服务提供商提供灵活性。VM 技术（如 VMware 和 Xen）以及虚拟网络 (VN)（如 VPN）是虚拟化的核心工具。虚拟化可采取多种形式，包括应用虚拟化、桌面虚拟化、存储虚拟化、服务器虚拟化和网络虚拟化。

    2.  **大规模伸缩性**：云计算的大规模伸缩性通过多核处理器以及虚拟机提供最高可能的按需扩展能力。通过这种方式，客户无需额外购买硬件，也不必承担管理相关的麻烦。相反，云服务提供商提供虚拟服务器的快速供应、标准化硬件以及持久化云存储。

    3.  **通用访问**：这是云计算的主要特征，指客户可以通过 Internet 从世界任何地点访问同一云服务提供商提供的服务。尽管云资源由全球不同客户共享，但其数据和在云上执行的操作仍保持机密且相互独立。这是公共计算提供 IaaS、PaaS 和 SaaS 服务的共同特征。

    4.  **使用管理和费用**：经济效益与云计算的采用相关联。因此，使用管理和费用或收费是提供云计算供应商经济优势的主要特征。通过云计算，用户可以根据自身需求以 `按需付费` 的方式租用处理能力和存储设施。例如，在特定时期内，如果需要高处理能力，消费者只需为该高处理能力在该特定时期付费。

    5.  **标准化资源**：云计算提供标准化的硬件、虚拟化和应用平台。然而，硬件和软件设施不需要是同质或标准化的。相反，服务器配置具有灵活性；编程语言如 `Java`、`Python` 和 `C++`；操作系统如 `Linux` 或 `Windows`；以及应用堆栈如 `LAMB` 或 `Microsoft.Net`。云计算提供商旨在提供丰富的选项以满足客户需求，同时利用其服务。因此，其目标是平衡客户的需求与可用的服务选项。
