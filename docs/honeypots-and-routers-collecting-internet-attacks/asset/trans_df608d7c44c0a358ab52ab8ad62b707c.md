

### 1.3.1 广域网

广域网是由分布在广阔区域（例如一个州、一个大陆，甚至更大）的设备组成的网络。因此，互联网通常被称为广域网；事实上，它是最大的广域网。同样，某些互联网服务提供商的全国性网络也是广域网的一个例子。

### 1.3.2 局域网

局域网通常局限于一栋建筑或同一管理下的一组相邻建筑。局域网的地理界限并不那么精确，当局域网覆盖区域显著较大时，也会使用诸如 `campus area network`（校园区域网）之类的术语。然而，从技术上讲，当所有参与设备都使用私铺的物理拓扑互连，并在同一管理之下时，该网络被视为局域网。这一定义也引出了这样一个结论：当一个组织的业务分布在一个大都市区或广域区时，在几乎所有情况下，该组织的城域网或广域网在逻辑上（`logically`）都是铺设在其他组织（通常是该地区公共电话和数据网络的所有者）的物理网络之上的。

局域网和广域网使用的协议和技术也不同，这主要还是由于所用物理介质的不同衰减特性所致。

## 1.4 网络协议与标准

尽管设备和介质是计算机网络的物理组件，但协议对于通信的成功同样重要，因为设备需要遵循一个既定的计划。协议描述了设备在通信期间要执行的动作和遵循的准则。如前所述，OSI 参考模型是计算机网络通信的基础文档。在大多数情况下，协议针对 OSI 模型的工作计划；然而，没有单一协议能覆盖 OSI 模型的所有七层。单个协议通常针对单个层的工作，且协议始终与相应的 OSI 层相关联。为了执行通信，设备遵循多个协议，这些协议以协作方式工作。这要求协议之间应当相互兼容。由于这一事实，协议以家族或群组的形式演进，其中一个家族包含属于不同 OSI 层且相互兼容的协议。

协议和标准的类别实际上非常丰富且无穷无尽；然而，在本节中，我们将讨论范围限制在该列表中的相关项目。在计算机网络中，术语 `standard`（标准）宽泛地指代由某些既定权威或组织（如 IEEE）设计或批准、供更广泛商业用途的协议、模型、架构或其组合。

### 1.4.1 IEEE 802 标准家族

IEEE 802 是一组用于局域网和城域网的标准。它针对 OSI 模型前两层的通信任务。IEEE 802 局域网和城域网参考模型进一步将数据链路层划分为两个子层：介质访问控制（MAC）和逻辑链路控制，如 [图 1.2](#06_Chapter01.xhtml#fig1_2) 所示。

IEEE 802 局域网和城域网是基于分组的网络，消息作为数据八位字节序列传输；大多数商业可用的设备和应用程序都受这些标准支持。在该层面上，分组在技术上被称为 `frames`（帧）。MAC 子层主要负责两个设备之间的无连接帧传输，而逻辑链路控制更关注管理、安全或确认等服务（[图 1.3](#06_Chapter01.xhtml#fig1_3)）。

IEEE 802 标准家族针对多种类型的物理介质制定了单独的标准，如 [图 1.4](#06_Chapter01.xhtml#fig1_4) 所示。每个标准都是针对特定物理介质和相关 MAC 层的协议和准则的集合，例如以太网、无线局域网和宽带无线城域网。所有类型的 MAC 都通过 MAC 服务访问点向逻辑链路控制提供具有核心功能的通用服务。

![Figure 1.2 IEEE 802 LAN and MAN reference model for end stations. LLC—logical link control, MAC—medium access control, LSAP—link service access point, MSAP—MAC service access point, And PhSAP—physical service access point. (Data from IEEE Standard for Local and Metropolitan Area Networks: Overview and Architecture, IEEE Std 802®-2001 [R2007].)](images/pg10_1.jpg)

**图 1.2** IEEE 802 终端站局域网和城域网参考模型。LLC—逻辑链路控制，MAC—介质访问控制，LSAP—链路服务访问点，MSAP—MAC 服务访问点，PhSAP—物理服务访问点。（数据来源：《IEEE Standard for Local and Metropolitan Area Networks: Overview and Architecture》，IEEE Std 802®-2001 [R2007]。）

![Figure 1.3 IEEE 802 reference model with end-station management and security. LMM— LAN/MAN management and SDE—secure data exchange. (Data from IEEE Standard for Local and Metropolitan Area Networks: Overview and Architecture, IEEE Std 802®-2001 [R2007].)](images/pg10_2.jpg)

**图 1.3** 带有终端站管理和安全的 IEEE 802 参考模型。LMM—局域网/城域网管理，SDE—安全数据交换。（数据来源：《IEEE Standard for Local and Metropolitan Area Networks: Overview and Architecture》，IEEE Std 802®-2001 [R2007]。）

![Figure 1.4 IEEE 802 standards family. (Data from IEEE Standard for Local and Metropolitan Area Networks: Overview and Architecture, IEEE Std 802®-2001 [R2007].)](images/pg11_1.jpg)

**图 1.4** IEEE 802 标准家族。（数据来源：《IEEE Standard for Local and Metropolitan Area Networks: Overview and Architecture》，IEEE Std 802®-2001 [R2007]。）

最初，该标准将局域网视为一种具有共享介质、信息广播给所有站点的对等通信网络。然而，后来也纳入了用于局域网互连的网桥及相关功能。事实上，在不需要任何中间交换节点的情况下直接通信的能力，是 IEEE 对局域网和城域网定义中的第二个区别点，第一个是它们地理区域的差异。在其范围内，该标准讨论了两类局域网互连设备：用于 MAC 层互连的网桥（见 [1.1 节](#06_Chapter01.xhtml#sch1_1)）以及用于物理层互连的中继器和集线器。为了理解这两类的区别，我们需要回顾术语 `access domain`（接入域）。

**接入域**。局域网或城域网中一组使用单一 MAC 协议且介质在所有设备间共享的设备和介质被称为 `access domain`。在这种情况下，最多只有一个设备发送，连接到介质上的所有其他设备接收。中继器以一种方式连接两个局域网，使它们成为单个接入域，这意味着当来自任一参与局域网的一个设备发送时，所有连接的局域网上的所有其他设备都将接收。当我们有兴趣扩大局域网的范围时，中继器很有用，这可能是由于介质的技术限制，如信号衰减。当局域网中的设备使用星型布线拓扑连接时，术语 `hub`（集线器）用来指代中继器。

