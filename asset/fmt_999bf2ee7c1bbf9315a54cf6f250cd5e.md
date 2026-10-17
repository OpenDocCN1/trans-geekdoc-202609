
The IoT Gateway manages the two‑way exchange of data between various networks and protocols, making sure the connected devices and sensors are compatible. With the use of advanced encryption methods, it provides a level of security for the network and data transmission. The gateway acts as a barrier between the devices and the cloud to prevent unauthorized access and malicious intrusion. In certain cases, it can also locally process the data from thousands of sensors before forwarding it, thereby reducing the amount of data being transmitted. The gateway serves as an extra layer of security for the data in transit with the latest encryption techniques. However, not all IoT gateways are capable of analyzing, aggregating, and only sending the relevant data to the cloud.

### 9.2.5 Resource of IoT

The IoT connects physical objects in the world to the global Internet. At the core of IoT is a diverse array of smart devices with sensors, actuators, and the ability to process and communicate information. These devices collect data about their surroundings through various types of sensors that measure things like pressure, temperature, and humidity. This information is then either directly uploaded to a server or transmitted through a gateway. Based on server feedback, IoT devices may also send commands to actuators. Applications of IoT in the real world include smart cities, intelligent transportation systems, smart homes, retail operations, health monitoring, and environmental and energy management. Due to the numerous benefits of IoT technology, industries, research and development facilities, and governments are investing large sums of money into IoT, resulting in intense competition and market fragmentation, hindered by compatibility issues with standards.

#### 9.2.5.1 Resources in IoT Ecosystems

Resources of many kinds used in IoT contexts are displayed in Figure 9.6. The tools used for resource management can be applied to various tasks for the benefit of the system, network, or applications utilized by end users. There are two main types of resources: those focused on apps and those focused on infrastructure. Infrastructure‑based resource management encompasses computing, networking, storage, and other resources. Resource management for energy is also important and includes hardware such as sensors, CPUs, and memory, as well as firmware and software. From the system’s perspective, hardware and software resources are differentiated, while from the network’s perspective, resources could include radio antennas, channels, bandwidth, routing paths, or nodes. Storage resource management encompasses various components, such as memory and the file system. Energy resource management deals with energy sources and batteries. Resource management can impact any software components from an application or user perspective, including application management modules, resource databases, customer databases, resource identification, and resource modeling.

![Figure 9.6 IoT resource modeling.](img/fig9_6_B.jpg)

Figure 9.6 IoT resource modeling.

### 9.2.6 IoT Objects

This section will look into the devices and physical components we use to make an IoT ecosystem work. We will also profoundly analyze the type of these components.

#### 9.2.6.1 Introduction of IoT Devices

The number of IoT devices has surpassed the global population. Currently, the world has a population of approximately 7.62 billion people, but by 2022, it is estimated that the number of IoT devices in operation will rise to 20 billion. This increase in IoT devices is driving the demand for 5G networks [17]. It is estimated that, in a few years, the average person in America will own more than ten IoT devices. The growth of IoT is increasing rapidly, with a multitude of devices available, including computers, smartphones, smart gadgets, smartwatches, and smart vehicles (Figure 9.7). These findings are further discussed in this section.

![Figure 9.7 Number of IoT devices.](img/fig9_7_B.jpg)

Figure 9.7 Number of IoT devices.

-   各种物联网设备的功能可能不同，但它们的工作原理相似。物联网设备是能够感知现实世界中发生的事件的实体，配备有`CPU`、网络适配器、固件和`IP`地址。为了接入网络，它们会连接到`DHCP`服务器。

大多数物联网设备通过软件应用程序（如智能手机应用）进行操作和监控。例如，使用智能手机应用可以控制家中的灯光。但某些设备内置网页服务器，无需外部程序，例如当有人进入房间时灯会自动打开。以下是一些物联网设备的例子：

1.  **家庭安全**

    物联网是确保家庭安全和保障的关键组成部分。可以通过物联网连接并管理各种传感器、警报和摄像头，并从移动设备中进行管理，从而提供持续的保护。

2.  **活动跟踪器**

    使用基于传感器的活动跟踪器可以实现健康监测。这些设备可以持续跟踪血压、身体活动、食欲和氧气水平等重要健康指标，并提供更新。

3.  **工业安全与防护**

    物联网在通过嵌入传感器和摄像头的检测系统来维护受限区域的安全方面发挥着重要作用。这些设备可以检测入侵者以及潜在的泄漏和压力升高，从而及时纠正这些问题。在`AR`中，配备计算机的可穿戴眼镜允许用户通过在其看到的场景中添加虚拟信息（如 3D 动画和电影）来增强现实体验。眼镜通过在镜片中嵌入相关信息，为用户提供访问互联网应用的功能。

4.  **运动检测**

    运动传感器能够检测建筑物、桥梁、大坝等大型结构中的运动或振动。通过这样做，它们可以识别可能导致灾难性后果的结构异常或中断。这些传感器也可以部署在容易受到自然灾害（如地震、滑坡和洪水）影响的地区，以提供早期预警和预防措施。

让我们来看看一些最受欢迎的物联网设备：

1.  **Google Home 语音控制器**

    Google Home 语音控制器是一个流行的物联网设备，提供语音激活的各种功能控制，包括灯光、温度控制和音量调节。

2.  **Amazon Echo Plus 语音控制器**

    Amazon Echo Plus 是一个广为人知且可靠的物联网设备，为用户提供众多语音激活功能，如接听电话、创建提醒和闹钟、获取天气更新等。

3.  **August 门铃摄像头**

    August 门铃摄像头是一个智能设备，提供对前门的远程监控和交互。其持续记录功能帮助你了解门廊上任何可疑行为。

4.  **August 智能门锁**

    August 智能门锁是一个知名且可靠的物联网设备，允许用户从任何地方管理门锁。

5.  **Foobot**

    Foobot 是一个物联网设备，能够准确跟踪室内空气污染，帮助改善家庭、办公室、咖啡馆和其他室内公共空间的空气质量。

### 9.2.7 物联网数据

物联网一词涵盖了配备传感器、计算能力、软件和其他技术的实体，这些实体可以通过互联网或其他网络相互通信。尽管有人批评这个名称暗示与整个互联网的连接，但实际上它仅指可以访问并连接到网络的单个设备。

物联网指的是一个相互连接的物理对象网络，包括计算机、数字和机械设备、生物体或任何可以分配`IP`地址并通过网络交换数据的事物。例如，植入心脏监测器的人、带有生物芯片转发器的农场动物、配备内置胎压传感器的汽车等。

### 9.3 传感器

物联网系统建立在传感器之上，传感器作为系统的感官，收集有用信息。这些传感器可以被视为类似于人类的感官（如眼睛、耳朵、嘴巴和鼻子），但它们能够收集更大量的数据。物联网系统的“大脑”可以根据这些传感器收集到的信息进行移动和变化。

#### 9.3.1 介绍

任何物联网部署的基础是使用传感器，它们是数据收集的来源。这些传感器为软件提供最佳运行所需的感官信息。构成该系统的智能设备群被称为`WSN`或`MEMS`。该网络中的节点能够执行特定任务，这得益于处理和传感技术的小型化，使得低功耗且成本效益高的设备得以实现。传感器被放置在周围环境中，用于监测或跟踪感兴趣的对象。它们处于休眠状态，但可以自主创建网络拓扑，自行配置，并通过短距离与附近的节点进行通信。被检测到的节点集合能够通过多跳架构实现远程通信，其中被称为集群头的优秀节点会汇总结果后转发到下一跳。这有助于防止基础设施故障，节约资源，提高生产力，增强安全性，并为新应用的出现铺平道路。网络中的水龙头和节点数量可以有所不同，但它们负责收集、组织和分发必要的读数，实时监测温度、湿度、声音、亮度和振动等物理因素。这些设备能够提供实时环境测量的能力也使其能够全球运行，尽管仍存在一些需要改进的局限性，如能耗、电力需求、安全问题和存储空间。

#### 9.3.1.1 传感器在物联网行业中的作用

物联网是一个综合网络，将不同的信息采集设备与互联网相结合。互联网的进步是信息时代的基石，而物联网的发展需要智能感知、识别和通信等技术能力。传感器及相关技术在提供感知方面发挥着至关重要的作用，物联网的扩展离不开它们的进步。传感器的使用对于收集数据并对物联网的成功作出重大贡献是必不可少的。在传感器领域，预计将出现 tremendous growth（巨大增长）。

### 9.3.2 背景

`WSN`可以通过构建临时的远程系统在其网络内的设备之间实现短距离通信。但将它们连接到互联网或其他移动通信系统面临挑战，因为通信协议尚未标准化。`WSN`传输协议的限制使得在长距离传输数据和检测技术进步变得困难。这一问题通过物联网得到解决，物联网通过开发`IoT Gateways`提供解决方案。这些网关旨在降低传感器与移动通信系统之间的异质性，改善带有终端设备的`WSN`管理，并支持已建立的通信系统与传感器系统的集成。这使得管理传感器系统的设备变得更加容易。

-   物联网是一个高级且智能的全球网络基础设施，由自配置节点组成。借助各种智能传感器，该网络能够感知并修改当前现实，将收集的数据转换为用于传输到网关的数字流。物联网因其多功能性和微芯片单元所提供的有价值信息而受到欢迎。它还能够节约资源，并在参数超出可接受限制时提醒用户。尽管这些设备存储容量和处理能力有限，但它们仍能在面对隐私、性能、可扩展性和可靠性等挑战时，提供对真实世界的出色表示。

另一个传感器面临的问题就是存储容量有限。云基础设施通过传感器技术为该问题提供解决方案。云计算是一个广阔且不断扩展的领域，提供无限存储空间和强大的计算能力。它允许组织在任何地点按需从一系列可配置的计算资源中获取服务，包括数据存储、服务提供、服务器管理以及开发高效管理的程序。云计算专注于提升互联网传输，已被证明是一个高度创新的领域。移动云计算将分布式计算的概念推向更高水平，使其能够随时随地访问。

移动设备客户服务的管理得益于移动应用和云计算的发展。移动应用为用户提供了关于各种服务的大量信息。这些系统在移动设备和远程服务器之间通过隔离系统运行。移动设备中心的各类应用类型已大量涌现，如娱乐、游戏、商业、即时通信、旅游和新闻。雾计算扩展了云技术的使用，增强了边缘计算能力，并使在边缘网络附近的设备（如建筑或办公室）能够作为本地资源，而交换机则可充当现代服务器。

### 9.3.3 工作原理：传感器在不同应用中的作用

传感器在当代许多企业的运作中发挥着关键作用。预测性维护得以实现，使公司能够通过在问题升级前检测潜在故障来最大限度地减少昂贵的停机时间。通过分析传感器数据的趋势，业务所有者可以获得有价值的洞察，并基于坚实证据做出明智决策。这些传感器设计用于响应特定的物理条件，并生成指示情况严重程度的信号，如温度、声音、距离、压力，甚至气体或液体的存在与否。典型的物联网传感器包括：

1.  入侵检测
2.  温度监测
3.  光传感器
4.  湿度传感器
5.  水质监测
6.  化学传感器
7.  陀螺仪传感器
8.  气体传感器

#### 9.3.3.1 入侵检测

入侵检测系统用于监测其监控范围内的任何潜在入侵，并发出警报。它通常与其他物理安全系统集成，并利用具有`Internet`接入的`IT`系统。系统由三个关键组件组成：传感器、控制单元和警报装置。传感器采用多种技术检测入侵并向控制单元发送警报信号。控制单元在收到警报后会触发隐蔽警报，或警报装置（如灯光或警报器）发出警告。

不同作者提出了多种保护系统免受入侵的方法。攻击耐受技术被描述为攻击者与传感器之间的非零和博弈。博弈论框架为两个玩家——攻击者和`IDS`——提供纳什平衡。第二种方法是`IDS`，它依赖于马尔可夫决策过程。`IDS`在监控系统的同时观察对手行为，试图判断需要保护的节点。如果`IDS`确认对手正在发起攻击，它会使攻击失败；如果对手攻击了意外的节点，则`IDS`认为攻击成功。第三种方法是，`IDS`测量流量并决定保护流量负载最高的节点。在模拟中，环境中存在 20–200 个集群头节点，模拟在奔腾 III 处理器（1133 MHz）上运行 [20]。

#### 9.3.3.2 温度监测
