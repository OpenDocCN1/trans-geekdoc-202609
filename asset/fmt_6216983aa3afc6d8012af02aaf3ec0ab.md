
Figure 25-11 中显示的那种图表 notoriously 难以绘制，仅仅因为构建软件的方式有如此多不同之处。这里显示的是一个可能的表示，仅用于说明构建路由器（或其他网络设备）所需的各种组件。

在 `Figure 25-11` 中：

• 转发专用集成电路（`ASIC`）、风扇/LED 等以及 `PHY`（物理网络接口芯片组）是唯一显示的硬件设备；其余均为软件组件。

• 假设软件组件在某些本地处理器、内存和存储资源上运行；这些在考虑网络设备架构时通常不会显示。

• 路由栈由两个组件组成：实际的路由协议（或其他控制平面）应用程序和路由信息库（`RIB`）。

• 内核主要管理进程，包括内存和处理器使用；内核还可能为某些组件对提供通信通道。

• 系统中可能没有、有一个或有两个数据总线。如果存在此组件，则负责提供在系统其他组件之间传输信息以及可能充当系统状态数据存储的标准方式。数据总线可以实现为数据库或发布/订阅系统。

• 可能有也可能没有配置数据库。如果存在，配置数据库负责保存设备上所有其他系统的配置状态。

• 配置系统提供读取和写入设备配置的某种方式。通常，这将包括机器可读（`API`）和人类可读接口（命令行界面 `CLI`）。机器可读接口将在 `Chapter 26`，“The Case for Network Automation”中更全面地考虑。

有一个单一术语，*Network Operating System*（`NOS`），通常用于描述

• 所有软件组件

• 内核、数据总线和（有时）其他组件，例如 `HAL` 和 `PAL`

由于 `NOS` 的含义是可变的，你需要确保你精确理解使用该术语时包含哪些组件，以及不包含哪些组件。

鉴于这组组件，有趣的去耦合问题变为：哪些组件可以或应该被拆分并由不同的人开发、拥有等？有几个不同的逻辑位置可以放置这种划分：

• 路由协议与 `RIB` 之间

• `HAL` 与其余组件之间

• `PAL` 与其余组件之间

• 硬件与软件之间

• `RIB` 与数据总线之间

• 配置系统与配置数据库之间

• 配置数据库与数据总线之间

传统上，所有这些组件都作为单个项目购买——即设备。要去耦合网络，你希望能够将此设备拆分为多个部分。在去耦合模型中，运营商可以

• 从一家供应商处购买硬件、`HAL` 和 `PAL`，在开源或供应商提供的 `RIB` 之上运行自己的控制平面，并从另一家供应商处购买系统的其余部分，这可能被称为 `NOS`

• 从一家供应商处购买硬件，从另一家供应商处购买软件（其中整个软件部分可能被称为 `NOS`）

• 从单一供应商处购买除系统配置系统之外的所有内容并自行构建其配置系统

关键点是运营商必须选择他想要拥有的网络的哪些部分，他想要购买的哪些部分，以及哪种去耦合模型对他的业务最有意义。所选的具体模型将取决于特定环境中的业务驱动因素和要求。通过将网络中的硬件与软件去耦合可以实现的某些具体成本优势包括

• 通过将硬件与软件分离来商品化硬件。如果一套软件可以在多个硬件平台上使用，则硬件功能和成本成为驱动因素，而非外部的品牌以及随硬件捆绑的软件。这是网络运营商中白盒运动的主要目标。

• 通过多代硬件提供运营稳定性。如果软件和硬件可以分别替换或修改，则可以在不修改运营流程和节奏的情况下用更新、更强大的设备替换硬件。与此同时，软件可以在不更换硬件的情况下随时间修改，允许网络在成长和成熟过程中无需使用叉车式替换来一次性更换所有设备。

与计算和应用领域中的去耦合一样，网络空间中的去耦合远不止成本节约。将软件与硬件解耦允许软件专门围绕应用架构构建——记住，去耦合的应用将整个网络视为单一的“事物”。就像构建高性能计算机需要根据具体的计算任务调整和优化硬件一样，构建高性能分布式应用通常需要将网络作为平台构建，针对应用进行调优以提高性能，并将运营商花费时间的地方集中在投资回报率更高的领域。

**Note**

网络工程师倾向于不把移除功能作为调优以获得最佳性能的方法，而更倾向于添加功能。当你打造一辆赛车时，你不会先从加装更大的发动机开始；你会先移除不必要的东西的重量。这简化了问题集合，减少了所需组件的数量，并且通常使替换或重新配置剩余部件变得简单得多，同时也使汽车本身更易于维护。网络工程师必须养成思考可以移除什么的习惯，而不仅仅是思考可以添加什么。

结果是双重收益。一方面，硬件被商品化，推动成本下降。另一方面，软件被定制化，提供更大的价值，并允许软件以业务的速度发展。即使在完全支持的解耦环境中（在撰写本文时已可用），也可能将软件生命周期与硬件生命周期分离。这允许以更快的计划更换硬件以获得新的速度和功能，以及新的交换功能，同时让软件保持更长的周期，使业务流程能够调整并围绕软件工作。

### 关于解耦的最终思考

网络世界正在迅速变化，而解耦在推动这些变化中发挥了主要作用。网络本身是否最终会以同样的方式和出于同样的原因被解耦呢？最后一章，第 30 章，“展望未来”，将审视网络的未来并尝试回答这些问题。

计算和应用空间中的解耦已在 IT 世界和网络管理中推动了更多变化。例如，网络中另一种形式的解耦是将网络本身提供的服务与网络设备分开。

### 延伸阅读

Churchill, Elizabeth F. “Patchwork Living, Rubber Duck Debugging, and the Chaos Monkey.” *Interactions* 22, no. 3 (April 2015): 22–23. doi:10.1145/2752126.

“Engineered Elephant Flows for Boosting Application Performance in Large-Scale CLOS Networks.” Irvine, CA: Broadcom, 2014. [`docs.broadcom.com/docs/1211168569445?eula=true`](https://docs.broadcom.com/docs/1211168569445?eula=true).

Gill, Phillipa, Navendu Jain, and Nachi Nagappan. *Understanding Network Failures in Data Centers: Measurement, Analysis, and Implications*. ACM, 2011. [`www.microsoft.com/en-us/research/publication/understanding-network-failures-data-centers-measurement-analysis-implications/`](https://www.microsoft.com/en-us/research/publication/understanding-network-failures-data-centers-measurement-analysis-implications/).

Lapukhov, Petr. “Routing Design for Large Scale Data Centers.” British Columbia, Canada, June 3, 2012. [`www.nanog.org/meetings/nanog55/presentations/Monday/Lapukhov.pdf`](https://www.nanog.org/meetings/nanog55/presentations/Monday/Lapukhov.pdf).

Lapukhov, Petr, Ariff Premji, and Jon Mitchell. *Use of BGP for Routing in Large-Scale Data Centers*. Request for Comments 7938. RFC Editor, 2016. doi:10.17487/RFC7938.

Martin Casado, and Justin Pettit. “Of Mice and Elephants.” *Network Heresy*, November 1, 2013. [`networkheresy.com/2013/11/01/of-mice-and-elephants/`](https://networkheresy.com/2013/11/01/of-mice-and-elephants/).

Pepelnjak, Ivan. *Data Center Design Case Studies*. ipspace.net, 2014. [`www.ipspace.net/Data_Center_Design_Case_Studies`](http://www.ipspace.net/Data_Center_Design_Case_Studies).

Roy, Arjun, Hongyi Zeng, Jasmeet Bagga, and Alex C. Snoeren. “Passive Realtime Datacenter Fault Detection and Localization.” In *14th USENIX Symposium on Networked Systems Design and Implementation (NSDI 17)*, 595–612. Boston, MA: USENIX Association, 2017. [`www.usenix.org/conference/nsdi17/technical-sessions/presentation/roy`](https://www.usenix.org/conference/nsdi17/technical-sessions/presentation/roy).

Singh, Arjun, Joon Ong, Amit Agarwal, Glen Anderson, Ashby Armistead, Roy Bannon, Seb Boving, et al. “Jupiter Rising: A Decade of Clos Topologies and Centralized Control in Google’s Datacenter Network.” In *Proceedings of the 2015 ACM Conference on Special Interest Group on Data Communication*, 183–197. SIGCOMM ’15. New York, NY: ACM, 2015. doi:10.1145/2785956.2787508.

White, Russ. “The State of Open Source Routers.” Presented at the North American Network Operators Group, Bellevue, WA, June 7, 2017. [`www.youtube.com/watch?v=JTQqmnVRToI`](https://www.youtube.com/watch?v=JTQqmnVRToI).

White, Russ, and Denise Donohue. *The Art of Network Architecture: Business-Driven Design*. 1st edition. Indianapolis, IN: Cisco Press, 2014.

### 复习问题

1. 研究虚拟机和容器之间的区别。提供两者之间三到四个差异的简短列表。

2. 研究环形结构布线设计。它与更广泛使用的脊柱和叶状设计有何不同？环形设计对过订阅会产生什么影响？

3. 解释“普通”网络和结构之间的差异。

4. 阻塞问题在无阻塞设计中并未真正消除，而是被转移了。它被转移到哪里？

5. 解释大象流和老鼠流之间的区别。

6. 查找网络操作系统可用的两个硬件抽象层。注意这两个抽象层之间的四个差异。

7. 查找两个开源路由协议栈。支持哪些协议？每个项目似乎获得了多少支持？

## 第 26 章

### 网络自动化的案例

**学习目标**

阅读本章后，你应该理解：

![Image](img/bull.jpg)网络自动化的主要目标

![Image](img/bull.jpg)基本网络管理需求

![Image](img/bull.jpg)`NETCONF` 的基本目的和操作

![Image](img/bull.jpg)`RESTCONF` 的基本目的和操作

![Image](img/bull.jpg)网络自动化中使用的一些语言及其属性

![Image](img/bull.jpg)设备上自动化和网络控制器

典型的网络由一组分布式节点组成，每个节点运行操作系统，每个节点都配置了协议和功能集。网络范围的功能——例如路由协议——需要同步配置以使节点能够协同工作。节点数量加上分布式配置导致了复杂性。新的节点或新功能增加了系统的复杂性，而复杂性增加会增加故障机会，增加运营成本，并阻碍网络改变的能力。这些货币和非货币成本通常限制网络工程师采用新功能、使用网络解决业务问题或理解网络故障。

网络自动化可以带来网络部署、操作和故障排除的改善。它可以降低网络部署、配置和操作的复杂性；提高敏捷性，即运营商更快地根据新需求重塑网络的能力；并通过消除人为因素并使用自动化工具与单个网络设备交互来降低成本和风险。

#### 网络自动化与复杂性

网络工程领域普遍存在一个假设，即自动化降低了复杂性。虽然自动化可以提供执行重复性任务的简单工具集，并减少人类与单个网络设备的交互，但它并不能从根本上降低复杂性。在 `State/Optimization/Surface (SOS)` 模型中，自动化减少了人类与单个网络设备之间的交互表面，但它增加了更多状态，以配置的额外数据库和新的协议交互的形式存在，并增加了一个额外的交互表面，即管理平面的新协议——`Application Programming Interface (API)`。最终，有人必须维护自动化过程中创建和使用的新工具和 `API`。

这并不意味着自动化是坏事；在网络运营中，几乎任何超出平凡规模的场景都需要它。然而，工程师应始终考虑权衡，并为增加的复杂性可能如何影响网络运营做好准备。与其假设复杂性会被降低，不如假设复杂性会被转移到其他地方，并考虑如何管理这种转移。

自动化也可以作为一种抽象形式，将大型配置替换为几个简单的命令。这既是好事也是坏事：好的一面是，它确保配置以一致的方式完成；坏的一面是，抽象通常在某处移除了状态，同时在其他地方降低了优化程度。同样，这并不意味着不应部署自动化；在许多情况下，自动化是唯一的前进路径。另一方面，工程师应始终寻找抽象可能影响优化的地方，并了解其对网络的潜在影响。所有非平凡的抽象都会以某种方式泄漏；尽可能地寻找并理解这些泄漏非常重要。

如果你还没有找到权衡，你就还没有足够仔细地寻找。

考虑权衡的一个特定地方是 `API` 的复杂性和能力以及用于访问 `API` 的工具，与状态的数量以及交互表面的广度和深度之间的关系。例如，与为人类交互而专门设计的接口交互通常意味着从人类到工具、从工具到以人为中心的接口、然后从以人为中心的接口到设备配置的交互链。经过以人为中心的接口的移动增加了大量复杂性，并使交互表面变得非常难以维护。从自动化工具通过某种专门为机器对机器交互设计的 `API`，然后到设备配置的移动要简单得多，因此在自动化系统中增加的复杂性也少得多。事实上，后一种情况，即工具到 `API` 到配置，在系统层面可以 *降低* 整体复杂性。

网络自动化可以简单到在数据中心自动部署新交换机，到通过动态软件开发更改配置，再到自动化对 `Syslog` 事件的响应。更强大的实现使网络团队能够停止将网络视为单个网络设备的集合，而开始将网络视为一个系统。

网络自动化催生了网络团队中的一个新职位：自动化工程师。自动化工程师通常是运营团队的一部分，需要具备高级网络、协议和故障排除技能；精通 `Python` 或 `Bash` 等脚本语言；以及能够操作文本，例如使用正则表达式。网络自动化团队通常规模很小。

###### Note

正则表达式是一种在更大的文本文件（如网络设备配置，甚至一本书）中匹配文本字符串的方法，要么是为了查找这些字符串，要么是使用文本处理器将一个字符串替换为另一个字符串。有关正则表达式的格式和用法的更多信息，可在本章末尾的“Further Reading”部分找到。

##### Automation Concepts

要自动化网络设备，网络自动化工具需要某种方法来连接、验证并与网络节点的控制平面交互。传统上，几乎所有网络设备都具有命令行界面 (`CLI`)。`CLI` 通过 `Telnet` 或安全外壳 (`SSH`) 提供对管理平面的访问，形成众所周知的从人到机器的系统。虽然 `CLI` 接口针对人类进行了优化，但它们可以使用诸如 `Expect`、`Puppet`、`Ansible`、`Chef`、`Salt` 和 `CFEngine` 等工具进行自动化（有关这些工具的信息链接，请参阅本章末尾的“Further Reading”部分）。

以其中一种工具为例：`Expect` 是一种脚本语言，用于通过交互式接口自动化配置——例如，通过 `SSH` 运行的 `CLI` 交互。`Expect` 创建了一个从机器到人类再到机器的系统，通常使用 `CLI` 作为 `API`（因此 `Expect` 可用于任何具有 `CLI` 的系统）。`Expect` 脚本在 `SSH` 会话返回某些文本后运行一组命令。例如，一个用于登录的 `Expect` 脚本可能包含以下内容：

```
expect "Username: "
send "Groot"
expect "Password: "
send "cisco123"
```

`Expect` 处理器实时检查文本流，寻找“User-name:”提示（通常通过在传入文本流上使用某种形式的正则表达式匹配引擎）。当遇到此提示时，处理器会根据先前编写的脚本发送包含“Groot”的文本字符串作为回复。密码的处理遵循相同的模式。在 Cisco `CLI` 的情况下，`Expect` 可能只是响应特定级别的命令提示，例如 `enable` 提示。`Expect` 具有很强的可扩展性，可以自动化单个设备或整个网络上的任何基于 `CLI` 的功能。在大多数情况下，网络自动化管理员会使用 `Expect` 与文本解析和操作工具（例如正则表达式）结合使用，以自动化大量设备的配置，从而使用少量脚本管理整个网络。
