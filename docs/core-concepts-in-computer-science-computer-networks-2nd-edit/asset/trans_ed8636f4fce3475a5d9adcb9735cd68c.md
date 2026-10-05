

# 媒体访问控制 (MAC) 协议概念

媒体访问控制（MAC）协议是计算机网络中数据链路层的一个基本方面，负责调节共享通信信道的访问和使用。在多个设备共享公共传输介质的场景中（例如以太网局域网或无线网络），MAC 协议确保数据传输的公平与高效，以防止冲突并最大化网络性能。

![](img/f7819d05465fc14719b3ebbba980271a_190_0.png)

MAC 协议的核心概念围绕着数据传输的协调和管理。配备网络接口卡（NIC）的设备在启动数据传输之前会监听介质，并使用载波感听多道接入（CSMA）等技术来检测正在进行的传输。如果介质是空闲，设备即可传输数据。然而，当多个设备尝试同时传输时，可能会发生冲突，导致数据丢失和网络效率低下。

为了解决冲突问题，MAC 协议利用冲突规避或检测机制，例如以太网中的带有冲突检测的载波感听多道接入（CSMA/CD）。当冲突发生时，设备会在重试数据传输之前引入随机退避计时器，以减少重复冲突的概率。

# 总结

- 数据链路协议是一组规定通信网络内设备间数据交换的关键性规则和规约。
- 寻址为设备分配唯一标识符，确保数据准确递送给目标接收者。错误检测和纠正机制能够识别并纠正传输错误，增强数据完整性。
- 流量控制调节设备之间的数据流，以防止接收方过载并避免拥塞。
- 计算机网络使用协议进行通信，协议定义了参与通信的系统将使用的程序。
- 链路执律（Line discipline）协调跳到跳的数据交付，其中“跳”是指计算机、网络控制器或某种网络连接设备（如路由器）。
- 链路执律是指协调数据通信网络上的半双工传输。数据通信网络中实现链路执律的两种基本方式是询问/确认（ENQ/ACK）和轮询/选择（poll/select）。
- 流量控制定义了一套程序，告诉发送站在在必须停止传输并等待目的站确认之前可以发送多少数据。

# 多选择题

1. OSI 模型中哪一层负责数据传输中的成帧和错误检测？
- a. 网络层
- b. 数据链路层
- c. 物理层
- d. 传输层

2. 数据链路层中媒体访问控制（MAC）子层的主要目的是？
- a. 数据包成帧
- b. 错误检测和纠正
- c. 控制对物理介质的访问
- d. 在网络之间路由数据包

3. 以下不是逻辑链路控制（LLC）子层的常见功能的是？
- a. 数据包成帧
- b. 网络设备寻址
- c. 错误检测和纠正
- d. 流量控制

4. 在以太网中，MAC 地址（媒体访问控制地址）的标准长度是多少？
- a. 24 位
- b. 32 位
- c. 48 位
- d. 64 位

5. 哪种协议常用于点对点通信并提供错误检测但不提供错误纠正？
- a. HDLC（高级数据链路协议）
- b. PPP（点对点协议）
- c. ARP（地址解析协议）
- d. SLIP（串行链路网协议）

# 答案

1. (b) 2. (c) 3. (a) 4. (c) 5. (b)

# 复习题

1. 你如何理解数据链路协议？
2. 描述字符型协议和位型协议。
3. 解释数据传输模式。
4. 区分异步和同步数据链路协议。
5. 针对以下主题写简要要记：
   a. 链路执律（Line Discipline）
   b. 轮询/选择（Poll/Select）
   c. 错误控制（Error Control）

计算机科学核心概念：计算机网络

182

# 参考文献

1. ABRAMSON N., “The ALOHA system – another alternative for computer communications”, Proceedings of 1970 Fall Joint Computer Conference, pp. 281–285, 1970.
2. ALI M.S., BHAGAVATHULA R., PENDSE R., “Airplane data networks and security issues”, The 23rd Digital Avionics Systems Conference DASC, Salt Lake City, United States, vol. 4, pp. 24–28, October 2004.
3. BARBEAU M., “WiMax/802.16 threat analysis”, Proceedings of the 1st ACM International Workshop on Quality of Service & Security in Wireless and Mobile Networks, Q2Swin ’05, ACM, New York, pp. 8–15, 2005.
4. BESSE F., PIROVANO A., GARCIA F., et al., “Aeronautical ad networks: a new datalink for ATM”, INO 2010, 9th Innovative Research Workshop & Exhibition, EUROCONTROL Experimental Center, Brétigny-sur-Or, France, 7–9 December 2010.
5. BESSE F., PIROVANO A., GARCIA F., et al., “Interference estimation in an aeronautical ad hoc network”, IEEE/AIAA 30th Digital Avionics Systems Conference (DASC) 2011, Seattle, WA, 16–20 October 2011.
6. BESSE F., PIROVANO A., GARCIA F., et al., “Wireless ad hoc networks access for aeronautical communications”, ISS 28th September 2010.
7. Security for securing wireless communication.
8. RFC 6929, April.
9. Transport Layer Security (TLS) Version 5746, August 2008.
10. Digital Video Broadcasting (DVB): Generic Encapsulation (GSE) Protocol, ETSI 102 07, Available at: www.etsi.org.
11. Digital Video Broadcasting (DVB): Generic Encapsulation (GSE) Protocol, ETSI 102 1.1, March 2013.
12. Digital Video Broadcasting (DVB): Generic Encapsulation (GSE) Protocol, ETSI 102 1.1, October 2004.

[195]

# 第6 章

# 无线网络安全

![](img/f7819d05465fc14719b3ebbba980271a_190_0.png)

无线网络安全是指对无线网络进行设计、实施并确保安全。它是网络安全的一个子集，为无线网络提供保护。无线网络安全也被称为无线安全。

学习本章后，你将理解以下核心概念：

- 无线技术概览
- 无线局域网

# 引言

无线网络安全是指用于保护无线传输数据的机密性、完整性和可用性的措施和协议。随着 Wi-Fi、蓝牙和蜂窝网络等无线技术的广泛应用，保护无线通信对于防止未经授权、数据泄露和其他恶意活动变得至关重要。

无线安全的主要在于无线传输与有线网络相比更容易被拦截。由于信号在空中传播，可能会被附近的设备捕捉，因此，建立强大的安全机制来保护无线通信至关重要。

无线网络的基础安全措施之一是实施加密。最常用的加密协议是无线保护访问 2 (WPA2) 或其继者 WPA3。这些加密协议对网络上的数据进行扰乱，使得未经授权的用户无法读取。采用强加密可以确保即使攻击者截获了无线数据，如果没有解密密钥也无法破解信息。

身份验证是网络安全的另一个关键方面。适当的身份验证确保只有授权用户才能访问网络资源。对于 Wi-Fi 网络，可以使用预共享密钥 (PSK) 或更安全的企业级身份验证（例如带有后端身份验证服务器 RADIUS 的扩展认证协议 EAP），在授予网络访问之前验证用户身份。

为了防止未经授权的访问，无线网络可以实施 MAC 地址过滤等措施，仅允许预注册 MAC 地址的特定设备加入网络。然而，仅凭 MAC 地址过滤不足以实现强大的安全，因为 MAC 地址可以被轻易伪造。

定期更新无线设备（如路由器和接入点）的固件和软件对于修复安全漏洞至关重要。应将设备的默认密码改为强且唯一的密码，以防止未经授权访问网络基础设施。

对于组织而言，实施虚拟专用网络 (VPN) 远程访问公司网络可以增加额外的安全层，对加密