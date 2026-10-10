
![Image](boxx.jpg) **A、B** 和 **D** 不正确。这些操作不一定能帮助防御固件使设备暴露出的漏洞。

##### 基于性能的题目

[**21.**](#ch08.xhtml#rch8que21) Security+ 考试可能会向你呈现一个网络图，并要求你根据题目中给出的标准，识别出需要在防火墙上配置的规则。考试极有可能要求你从可用规则列表中选择规则。下图标识了此场景的规则：

![Image](f0388-01.jpg)

[**22.**](#ch08.xhtml#rch8que22) 以下是安全术语与其描述的正确匹配。

![Image](f0388-02.jpg)

## 第 9 章

## 无线网络与安全

### 认证目标

[9.01 理解无线网络](#ch09.xhtml#ch9obj01)

[9.02 保护无线网络](#ch09.xhtml#ch9obj02)

[9.03 配置无线网络](#ch09.xhtml#ch9obj03)

[9.04 其他无线技术](#ch09.xhtml#ch9obj04)

[✓ 两分钟演练](#ch09.xhtml#ch9lev1sec6)

[**问答** 自我测试](#ch09.xhtml#ch9lev1sec7)

如今的网络不再局限于使用有线设备。网络现在混合使用有线系统和无线系统，后者利用射频将数据发送到 `wireless access point`（无线接入点）。`wireless access point` 与有线网络相连，允许无线设备与有线网络上的主机通信。许多小型办公室网络和家庭办公室网络使用家用路由器（参见[图 9-1](#ch09.xhtml#ch9fig1)），这是一种多功能设备，可充当交换机、路由器和无线客户端的 `wireless access point`。请注意，在大型企业网络中，`wireless access point` 将只有一个端口用于连接有线网络。

![Image](f0390-01.jpg)

**图 9-1**  

`wireless access point`，也称为 `wireless router`（无线路由器）

本章将带你进入无线网络的世界。这是 Security+ 认证考试的重要主题，请务必认真学习本章。本章将介绍无线标准和协议，展示如何设置 `wireless network`（无线网络），然后讨论一些 `wireless security`（无线安全）问题。

### 认证目标 9.01

### 理解无线网络

如前所述，`wireless network` 使用射频通过空气传输数据。这意味着，如果你有希望在办公室内移动办公的笔记本用户，只要他们的笔记本电脑安装了 `wireless network card`（无线网卡），就可以允许他们通过 `wireless access point` 访问 `network`（网络）。

你可以创建两种类型的 `wireless networks`：`ad hoc mode wireless network`（自组网模式无线网络）和 `infrastructure mode wireless network`（基础设施模式无线网络）。使用 `ad hoc mode` 时，`wireless device`（无线设备）（如笔记本电脑）直接连接到其他 `wireless devices`，形成点对点环境，无需 `wireless access point`。使用 `infrastructure mode` 时，`wireless clients`（无线客户端）连接到中央 `wireless access point`。`wireless client` 将数据发送给 `access point`，后者再将数据转发至 `wired network`（有线网络）上的目标，如[图 9-2](#ch09.xhtml#ch9fig2)所示。

![Image](f0391-01.jpg)

**图 9-2**  

运行在 `infrastructure mode` 下的典型 `wireless network`

这两种 `wireless modes` 各有优势。`ad hoc mode` 的优势在于无需购买 `access point`，因为 `ad hoc mode` 旨在使用 `wireless communication`（无线通信）直接连接系统。使用 `ad hoc wireless`，你的目标是允许系统连接，以便用户共享数据，或者可能一起玩局域网游戏。`infrastructure mode` 的优势在于你可以使用 `wireless access point` 让所有 `wireless users` 访问互联网。使用 `infrastructure mode`，你通常可以控制谁可以连接到 `wireless network`，并可以过滤 `network traffic`（网络流量）类型。例如，如果你使用 `wireless access point` 允许 `wireless clients` 连接互联网，你可以控制用户可以连接到哪些网站。这种集中式控制使得 `infrastructure mode` 非常流行。

#### 标准

`Institute of Electrical and Electronics Engineers (IEEE)`（电气和电子工程师协会）委员会在 `802` 项目模型中为 `wireless networking` 开发了 `wireless standards`（无线标准）。`Wireless` 由 `802.11` 项目模型定义，并定义了多个标准。

##### 802.11a

`802.11a` `wireless standard` 是第一个在 `5-GHz`（吉赫兹）频率下运行的 `wireless standard`。`802.11a` 设备的数据传输速率为 `54 Mbps`。

##### 802.11b

`802.11b` `wireless standard` 的传输速率为 `11 Mbps`，使用 `2.4 GHz` 频率。`802.11b` 设备与 `802.11a` 网络不兼容，因为它们运行在不同频率上。还应注意，`802.11b` 开启了 `Wi-Fi`（wireless fidelity，无线保真）标准。

##### 802.11g

在 `802.11b` 之后，`802.11g` `wireless standard` 推出，旨在兼容 `802.11b`，同时也提高了传输速率。`802.11g` 设备的传输速率在 `2.4-GHz` 频率范围内为 `54 Mbps`。

所有 `802.11g` 设备都与 `802.11b` 设备兼容，因为它们都遵循 `Wi-Fi` 标准，且都在 `2.4 GHz` 频率下运行。

##### 802.11n

`802.11n` `wireless standard` 于 `2009` 年底最终确定。`802.11n` 的目标是将传输速率提高到当前标准（如 `802.11g`）所支持的水平之上。理论上 `802.11n` 标准传闻支持高达 `600 Mbps` 的传输速率，但目前大多数 `802.11n` 网络组件运行在 `150 Mbps`。为了实现更高的传输速率，`802.11n` 使用了两项新功能：`multiple input multiple output (MIMO)`（多输入多输出）和 `channel bonding`（信道绑定）。`MIMO` 使用多根天线来实现单根天线无法达到的吞吐量。`Channel bonding` 允许 `802.11n` 通过两个信道传输数据以实现更高的吞吐量。`802.11n` 标准设计为与 `802.11a`、`802.11b` 和 `802.11g` 向后兼容，并可在 `2.4-GHz` 或 `5-GHz` 频率下运行。

重要的是要注意，`802.11a` 是 `wireless networking` 的早期实现，与 `Wi-Fi` 网络不兼容。以兼容性为例，我以前家里的 `wireless network` 使用的是 `802.11g` 设备作为 `access point`，但我有一台旧笔记本电脑装的是 `802.11b` `wireless network card`。我仍然能让旧笔记本在 `network` 上通信，因为这两个标准 `100 percent` 兼容。在这个例子中，装有 `802.11b` 网卡的笔记本只能以 `11 Mbps` 连接，而装有 `802.11g` 网卡的较新笔记本可以以 `54 Mbps` 连接。

##### 802.11ac

`802.11ac` `wireless standard` 于 `2014` 年获批，被认为是一种高吞吐量 `wireless standard`，运行在 `5-GHz` 频率范围内。`802.11ac` 标准通过增加信道宽度，并提供类似于 `802.11n` 标准的功能（如 `MIMO` 和 `multi-user MIMO (MU-MIMO)`（多用户 MIMO）），提供潜在的 `1 Gbps` 吞吐量，后者涉及允许多个发射机发送独立信号，多个接收机同时接收独立信号。

大多数 `802.11ac` `wireless routers` 都有一个 `USB 3.0` 端口，允许你将外部硬盘连接到 `wireless router` 并向客户端流式传输高清视频。

![Image](exam.jpg)

**针对 Security+ 认证考试，请确保你熟悉 IEEE 无线网络标准的基础知识：`802.11a/b/g/n/ac`。**

[表 9-1](#ch09.xhtml#ch9tab1) 总结了关于不同 `wireless standards` 你需要为 Security+ 认证考试熟悉的关键点。

**表 9-1**  

不同 `Wireless Standards` 的比较

![Image](t0393-01.jpg)

#### 信道
