
In this chapter, we are narrowing our look at information and cybersecurity specifically to computer systems, ignoring network security for the most part, for now. Recall that a primary role for technology managers, as far as security is concerned, is to provide well-defined means of identifying, monitoring, mitigating, and managing security risks. This includes oversight of members in the organization who are responsible for taking the appropriate actions. Viewed traditionally, it may seem as though security is only a technological problem by the concentration on techniques and technologies for creating better defenses and using criteria in performing risk analyses and the application of security countermeasures, but it is important to note that security is mainly a behavioral issue. Later, we will cover security behaviors in greater detail, but for now, let’s examine where security policies and security models come into play. Security policies are the rules used to maintain organizational security as well as for monitoring and reporting in the case of security breaches. Security models are criteria and techniques designed to “carry out” certain aspects of the security policy, such as what privileges are allocated for which resource and to whom. Said differently, models are patterns that are applied to certain general countermeasures such as ways to manage access to resources.

Security policies and models are part of a technology manager’s arsenal to combat cybercrime and other incidents, along with the other measures we have discussed so far that strive for the reduction of risk exposure by using the processes of threat identification, asset measurement, and control and minimization of losses associated with threats. We have seen how the security life cycle calls for surveys and classification of assets, conducting security reviews, performing risk analyses, evaluating and selecting information security technologies, performing cost/benefit analyses, and testing security effectiveness. Next, we will also explore the roles of practices, models, and policies in the information security management life cycle.

### 8.1.1 Computer Architecture and Systems Security

In addition to the technical and administrative measures we have discussed so far, maintaining information and systems security involves the development of policies and conducting comparisons against standards, procedures, and guidelines. All these activities help us to ensure information in the confidentiality, integrity, and availability (C-I-A) triad. Also, thus far, we have covered the importance of assets and information classification, identification of threats and vulnerabilities, and to ensure that effective countermeasures are implemented. As we noted, there are a variety of tools available to technology managers, including information classification systems, configuration management and change controls, and employee security training.

Now it’s time to consider all the organizational security aspects of a company’s information systems infrastructure, which comprise all the resources and assets and efforts related to information and the computing facilities used by people in organizations for decision-making and action taking. An organization’s information and systems security infrastructure support the organizational mission and objectives by helping to ensure C-I-A. Under the umbrella of information infrastructure resides information architecture, which consists of computer architecture, along with how information and systems are organized within a company and between trading partners; therefore, the information architecture outlines all the facilities that must be secured.

建筑学在经典意义上是通过蓝图可视化结构的组织方式以及其设施或特性。信息架构同样包含规格、图表、设计、需求文档、拓扑结构以及所有描述组织所使用的信息和计算资源的草图。其功能是创建并通信“信息环境”，包括在组织和促进信息易用性、完整性、访问性和有用性方面涉及的美学、结构和机制（Figure 8.1）¹

![FIGURE 8.1 Layered Relationships](img/9781284236378_CH08_FIGF01.jpg)

FIGURE 8.1 Layered Relationships

信息架构分为宏观层面和微观层面。例如，宏观层面的 Web 应用程序架构会展示信息存储和流经消费者-生产者（价值）链的所有交叉点和分布，包括在贸易合作伙伴、公司地点、共址处以及组织对应的机构（如航空公司与联邦航空管理局（FAA）或银行与联邦储备系统）之间的交互。另一方面，微观层面的 Web 应用程序架构则展示系统或系统集合内的单个组件。它可能显示软件和系统的分区方式、网络接入点的位置、哪些组件是集中化的、哪些是分布式的，甚至指定一些关键技术，以限制架构适用于某种平台或软件系统。信息安全管理生命周期（ISML）的一部分要求信息架构被记录，并指定安全对策。

### 8.1.2 Security Models and Systems Architecture

此前，我们在微观层面上讨论了操作系统（OSs）及其他应用程序和资源（如数据库和网络）所执行的功能。现在，让我们探讨系统架构、安全模型和网络安全如何相互关联。为此，我们需要先回顾一些基本的计算机架构概念，并重述在本文早期已提及的几点。

操作系统、硬件、网络设备、协议和应用程序的安全需求层级多样，常常导致人们忽视可能影响整个信息系统生态系统的安全漏洞。我们将架构视为系统组装的规格或蓝图。安全模型则是实施技术、模式和对策的方式，遍及信息和系统架构的宏观与微观层面；因此，理解计算机架构至关重要。请记住，对策有不同的分类。稍后，我们将查看与安全模型相关的一些对策。

请记住，对策是为抵御威胁而实施的行动或技术。有些对策基于已知威胁，另一些则在攻击过程中学习到的经验中生成。

| Countermeasures | Description |
| --- | --- |
| Availability Countermeasures | 防范性措施，用于防止对资源和数据访问的丧失。 |
| Integrity Countermeasures | 防止未经授权修改数据或处理的技术和方法。 |
| Confidentiality Countermeasures | 防止未经授权披露消息内容或数据的预防性措施。 |

虽然某些对策可能是“ bolted on”（即事后附加），如加密或系统与基础设施监控，其他对策则属于操作系统的管辖范围；正是在这里安全模型发挥主要作用。总体而言，安全模型规定系统应如何上线。其目标是保持系统、软件、信息和数据的问责性、真实性、不可否认性和可依赖性。通过加密电子邮件和传输（在传输中）及存储（持久化）的数据，以及在信息架构的各个层面（如数据仓库、Web 服务器和应用程序）确保数据保护。例如，通过输入验证保护进程执行，并确保数据在数据仓库、Web 服务器和应用程序中的安全。一个例子是确保输入验证并保护进程的执行。为使措施有效，它们必须在信息安全管理生命周期（ISML）的设计和架构规划阶段即时制定，并通过 DevSecOps 工程、配置、实施、测试、审计、评估、认证和授权的过程逐步细化。

### 8.1.3 Security Models and Computer Architecture

要理解安全模型，我们必须具备计算机架构的基础知识，因此让我们快速回顾。计算机架构指的是硬件和操作系统（如中央处理器（CPU）、内存（静态和动态）、所有电路、磁盘驱动器或其他存储设备以及网络组件）。CPU 与算术逻辑单元（ALU，以及寄存器）负责进程的执行。CPU 的控制单元管理并同步系统，并在执行不同应用程序代码和操作系统指令时，决定哪些应用指令被处理以及以何优先级顺序处理，以及在进程完成前能分配多少时间片。它控制何时执行指令，而这一执行使得应用程序能够处理数据。操作系统中与控制单元协同工作的主要组件是调度器。调度器扫描运行队列中的可运行进程，选择优先级最高的进程在其分配的时间片内执行，随后如果未完成，将其返回队列。通过这种方式，CPU 执行操作系统和用户应用程序的指令流。需要处理的数据会传递到指令寄存器，而控制单元则通过 CPU 协调进程和处理上下文的切换（Figure 8.2）。

![FIGURE 8.2 Computer Architecture](img/9781284236378_CH08_FIGF02.jpg)

FIGURE 8.2 Computer Architecture

CPU 以块或组的方式处理数据。如果软件指令未正确设置在等待执行时可以存储的数据边界，可能导致缓冲区溢出（故意造成的，这是缓冲区溢出攻击）。由于 CPU 是多处理器的，这意味着系统会并发服务许多任务、程序和用户，尽管在大多数系统中，只有单个程序或线程实际在执行。协调通过硬件和软件中断实现。中断发生在高优先级事件需要 CPU 转到另一个进程时，称为上下文切换。硬件中断是如磁盘驱动器需要写入且正在等待 CPU（而 CPU 正在处理其他任务，如接受用户界面的输入）的情况。软件中断相似，但优先级低于硬件中断，它们向 CPU 发出信号，表示某个进程需要在另一个进程之上执行。例如，调度器会在运行队列中选择内核进程而非用户进程，或选择在运行队列中等待较长时间的进程，而不是因等待资源（如等待数据缓冲区被清空）而被阻塞的进程。

操作系统指令、应用程序和数据存储在不同的内存段中，如栈、文本、堆、缓冲区和寄存器，同时也包括基本输入/输出系统（BIOS）、设备控制指令和固件。内存还分为多种类型，例如随机存取存储器（RAM），它是一种由操作系统和应用程序用于读写活动的临时存储介质。RAM 是易失性的，即电源断开后，存储的数据会消失。RAM 有两种类型：动态 RAM（DRAM）需要不断进行充电或刷新才能保持数据在芯片中的完整性，而静态 RAM（SRAM）则无需刷新即可保持数据。只读存储器（ROM）是一种非易失性存储介质，电源断开后数据仍然保留。写入 ROM 的指令被称为固件。ROM 大部分是可擦除可编程只读存储器（EPROM），其中的指令“埋入”芯片，但有限度地可以修改数据。缓存是一种用于频繁访问数据的高速读写存储类型，它用于存储从主存储器中获取的程序指令和数据，并在 CPU 准备执行应用程序时进行访问。

#### 8.1.3.1 内存映射

鉴于各种内存类型，你会发现每一种内存都有特定的用途。本质上，它是为了隔离软件和数据的重要部分，以便最快速地执行。由于内存分段，操作系统必须有办法映射进程及其数据的所有片段；这称为内存映射。内存映射使用数据结构，例如页表，专门用于保存指向其他应用程序地址位置的指针。页表是虚拟内存系统用来存储逻辑地址与物理地址映射的数据结构。软件不直接使用物理地址，而是使用虚拟或逻辑内存。间接访问内存提供了一个保护与效率的访问控制层，用于软件与内存之间。该设计的重点在于性能，但这也导致了某些难以根除的漏洞，只能通过缓解措施进行监控。例如，用于 SMTP 邮件的 `SENDMAIL` 应用程序是一个庞大的程序，包含众多潜在的利用入口。对此无法根治，我们只能实施缓解措施来隐藏、过滤或限制对它的访问。我们将稍后探讨一些方法，如使用代理。

| Storage Type | Description |
| --- | --- |
| Primary Storage | 这是直接由 CPU 访问、间接由应用程序访问的主存储部分，存储在易失性 RAM 中。 |
| Secondary Storage | 这是用于磁盘驱动器、闪存盘和二次固态存储的非易失性存储，用于间接访问。 |
| Virtual Storage | 通过虚拟地址映射到内存中其他位置的物理地址，由 RAM 和二次存储分配并使用的存储空间。 |

#### 8.1.3.2 CPU 模式和保护环

进程竞争系统资源，如内存和 CPU。软件应用程序可能需要访问相同的内存段、向 CPU 发送指令进行处理，或访问二次存储设备。用户应用程序（如浏览器、电子邮件客户端、文字处理程序等）可能会尝试执行冲突操作，例如一个进程在写入数据块的同时另一个进程在读取同一块数据。操作系统必须管理这些进程和事件，以确保系统顺畅运行并防止违反安全策略。为实现高效运作，操作被分离为用户应用程序和操作系统或内核进程。内核进程优先于用户进程，设备操作优先于应用程序。保护环是该整体方案的一部分，用于控制主体和对象（如图 8.3 所示）。

![FIGURE 8.3 Rings and Resources](img/9781284236378_CH08_FIGF03.jpg)

图 8.3 环和资源

保护环的作用是创建基于操作系统权限的行为边界。在内层环的进程拥有比外层环的进程更多的特权。内层环仅允许最受信任的组件和进程在其边界内运行。保护环的数量取决于操作系统，但通常将内层划分为特权模式（如管理员、内核、超级用户或监视者），而外层进程则运行在用户模式。当进程需要访问它无权直接访问的组件时，它会通过系统调用向操作系统请求执行该任务。如果外层应用程序尝试发送超出其权限的 CPU 指令，CPU 会将其视为异常并产生错误，从而阻止该操作。攻击者可能试图提升权限（例如通过 rootkit），或利用此保护特性导致系统崩溃。
