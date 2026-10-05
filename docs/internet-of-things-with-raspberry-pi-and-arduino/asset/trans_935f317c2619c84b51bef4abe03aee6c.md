

# 基于树莓派和 Arduino 的物联网

- 3. 云端网关：用于在网关与物联网中央服务器之间传输数据。
- 4. 流媒体数据处理器：它将来自传感器的数据分发到网络中连接的相关设备上。
- 5. 数据湖：用于存储所有定义和未定义的数据。
- 6. 大数据仓库：用于收集有价值的数据。
- 7. 控制应用：用于向执行器发送命令。
- 8. 机器学习：通过在数据上应用算法生成模型，这些模型可用于控制应用。
- 9. 用户应用：使用户能够监控数据并对连接连接设备做出决策。
- 10. 数据分析：用于手动数据处理。

## 1.3.2 物联网协议

### 1.3.2.1 OSI 模型

用于物联网协议的 OSI（开放式系统互连）模型如图 1.1 所示，包含五层：物理层、链路层、网络层、传输层和应用层。

物理层由设备、对象和物体组成。链路层运行在如 IEEE 802.15.4、IEEE 802.11、ISO/IEC 18092:2004、Bluetooth、ANT、NB-IoT、EC-GSM-IoT、uIP、EnOcean 和 LTE-MTC 等协议上。网络层协议为 6LoWPAN、IPv6 和 NanoIP。传输层协议为 CoAP、TCP、UDP、MQTT、XMPP、AMQP、LLAP、DDS、SOAP 和 DTLS。应用协议为 JSON-ISO、REST API 对象和二进制对象。

| 应用层 | 协议 |
| :--- | :--- |
| 应用层 | REST API, JSON-ISO 对象, 二进制对象 |
| 传输层 | CoAP, MQTT, XMPP, AMQP, LLAP, DDS, SOAP, UDP, DTLS |
| 网络层 | 6LoWPAN, IPv6, uIP, NanoIP |
| 链路层 | IEEE 802.15.4, IEEE 802.11, ISO/IEC 8092:2004, NB-IoT, EC-GSM-IoT, Bluetooth, ANT, ISA100.11a, EnOcean, LTE-MTC |
| 物理层 | 设备, 对象, 物 |

图 1.1
物联网协议的 OSI 模型。

## 物联网简介

### 1.3.2.2 组织层

物联网协议也可以根据组织层分类，如下：

- 基础设施 (IPv4/IPv6, 6LoWPAN, RPL)
- 识别 (EPC, IPv6, uCode, URIs)
- 通信 (Bluetooth, Wi-Fi, LPWAN)
- 发现 (DNS-SD, mDNS, Physical Web)
- 数据协议 (AMQP, MQTT, Websocket, CoAP, Node)
- 设备管理 (TR-069, OMA-DM)
- 语义 (Web Thing Model, JSON-LD)
- 多层框架 (Weave, IoTivity, Alloyin, Homekit)

**IPv6:** IPv6 作为一种网络层协议，用于传输跨多个网络协议 (IP) 网络进行端到端传输的数据包。

**6LoWPAN:** 6LoWPAN 代表基于低功耗无线局域网的 IPv6。它是通过 IEEE 802.15.4 链路扩展 IPv6 的层。它工作在 2.4 GHz 频率，数据传输率为 250 kbps。

**RPL:** 它是一种用于低功耗和丢包性网络的基于 IPv6 的路由协议。

**UDP (用户数据报协议):** 该协议用于客户端/服务器之间基于 IP 的协议网络。UDP 用于具有实时性能要求的应用程序。它设计用于安全协议，以降低网络上连接和信息传输的延迟。

**μIP:** 缩写为微型互联网协议。它被广泛用于开源 TCP/IP 栈，可用于 8 位和 16 位微控制器。

**DTLS (数据报传输层安全):** DTLS 协议为数据报协议提供通信隐私。它用于防止网络中的篡改、消息伪造或窃听。

**NanoIP:** Nano 互联网协议旨在在嵌入式传感器和设备之间建立通信，而无需 TCP/IP 的开销。

**时间同步网格协议 (TSMP):** 这是一种通信协议，用于在称为 motes（微节点）的自定制无线传感器节点之间建立通信。

**物理网络 (Physical Web):** 物理网络是一种连接设备并无缝访问它们的方法。

**HyperCat:** 这是一个基于 JSON 的开源轻量级超媒体目录，用于公开 URIs 集合。

**MQTT (消息队列遥测传输):** MQTT 是一种发布订阅模型，常用于低带宽环境。

**CoAP (受限应用协议):** CoAP 是一种用于物联网的轻量级传输协议。

**Wi-Fi:** Wi-Fi 是一种本地局域网技术。

**Bluetooth:** 蓝牙是一种短距离无线通信技术。

**ZigBee:** ZigBee 是一种低功耗无线网网协议。

**ZWave:** ZWave 是一种用于家居自动化的无线协议。

**REST:** 表现状态转移是一种架构风格。

