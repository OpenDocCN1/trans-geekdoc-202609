
DNS 故障经常导致用户认为网络已宕机。如果用户在 Web 浏览器中输入域名，例如 www.cisco.com，而 DNS 服务器无法访问，则名称无法转换为 IP 地址，网站也不会出现。

![](img/e71dc48d3ae3db3394e5857ab2acae75_663_0.png)

## Lab—Design and Build a Small Business Network (17.8.1)

在本实验中，您将设计并构建一个网络。

![](img/e71dc48d3ae3db3394e5857ab2acae75_663_1.png)

## Packet Tracer—Skills Integration Challenge (17.8.2)

在此 Packet Tracer 活动中，您将使用本书中获得的所有技能。

![](img/e71dc48d3ae3db3394e5857ab2acae75_663_2.png)

## Packet Tracer—Troubleshooting Challenge (17.8.3)

在此 Packet Tracer 活动中，您将排查并解决现有网络中的多个问题。

## Practice

以下活动提供了对本章介绍主题的练习。实验可在配套的 Introduction to Networks Labs & Study Guide (CCNAv7)（ISBN 9780136634454）中找到。Packet Tracer 活动说明也提供在 Labs & Study Guide 中。PKA 文件可在在线课程中获取。

![](img/e71dc48d3ae3db3394e5857ab2acae75_663_3.png)

## Labs

- Lab 17.4.6: 使用 Ping 和 Traceroute 测试网络延迟
- Lab 17.7.6: 排查连接问题
- Lab 17.8.1: 设计并构建小型网络

![](img/e71dc48d3ae3db3394e5857ab2acae75_663_4.png)

## Packet Tracer Activities

- Packet Tracer 17.5.9: 解析 show 命令输出
- Packet Tracer 17.7.7: 排查连接问题
- Packet Tracer 17.8.2: 技能综合挑战
- Packet Tracer 17.8.3: 故障排除挑战

## Check Your Understanding Questions

完成此处列出的所有复习问题，以测试您对本章主题和概念的理解。附录“Answers to ‘Check Your Understanding’ Questions”列出了答案。

1. 与小型企业相比，下列哪项网络设计考虑对大型企业更重要？
   a. Internet 路由器
   b. firewall
   c. 低端口密度交换机
   d. redundancy
2. 一名新聘用的网络技术人员被要求为一家增长预测较大的小型企业订购新硬件。选择新设备时，技术人员应主要关注哪一因素？
   a. 接口数量和类型固定的设备
   b. 支持网络监控的设备
   c. 冗余设备
   d. 支持模块化的设备
3. 哪种类型的流量最有可能在网络中具有最高优先级？
   a. FTP
   b. 即时消息
   c. voice
   d. SNMP
4. 网络技术人员正在调查从 PC 到地址为 10.1.1.5 的远程主机的网络连接。在 Windows PC 上发出时，哪条命令会显示到远程主机的路径？
   a. trace 10.1.1.5
   b. traceroute 10.1.1.5
   c. tracert 10.1.1.5
   d. ping 10.1.1.5
5. 用户在 Web 浏览器中输入 http://www.cisco.com 时无法访问网站。然而，她可以通过输入 http://72.163.4.185 访问同一站点。问题是什么？
   a. default gateway
   b. DHCP
   c. DNS
   d. TCP/IP protocol stack
6. Cisco IOS 调试输出消息默认发送到哪里？
   a. memory buffers
   b. vty lines
   c. syslog server
   d. console line
7. 扩展网络的哪个要素涉及识别物理和逻辑拓扑？
   a. traffic analysis
   b. network documentation
   c. device inventory
   d. cost analysis
8. 在小型网络中可以实施什么机制来帮助最小化实时流媒体应用的网络延迟？
   a. QoS
   b. PoE
   c. AAA
   d. ICMP
9. 如果计算机无法访问互联网并且收到了 IPv4 地址 169.254.142.5，则哪个进程失败了？
   a. IP
   b. DNS
   c. DHCP
   d. HTTP
10. 一家小型公司只有一个路由器作为通往其 ISP 的出口点。如果路由器本身或其与 ISP 的连接出现故障，可以采用哪种解决方案来保持连接？
    a. 激活连接到 ISP 的另一个路由器接口，以便流量可以通过它传输。
    b. 拥有一个连接到另一家 ISP 的第二台路由器。
    c. 从另一家 ISP 购买第二条最低成本链路以连接到此路由器。
    d. 为连接到内部网络的路由器添加更多接口。
11. 管理员应在何时建立网络基线？
    a. 网络流量处于峰值时
    b. 流量突然下降时
    c. 网络流量最低点时
    d. 在一段时间内定期
12. 哪两种流量类型需要延迟敏感的传输？（选择两项。）
    a. 电子邮件
    b. web
    c. FTP
    d. voice
    e. video
13. 网络技术人员怀疑两台 Cisco 交换机之间的特定网络连接存在双工不匹配。技术人员应使用哪条命令查看交换机端口的第 1 层和第 2 层详细信息？
    a. show interfaces
    b. show running-config
    c. show ip interface brief
    d. show mac address-table
14. 关于 Cisco 设备上的 CDP，哪种说法是正确的？
    a. show cdp neighbor detail 命令仅在存在第 3 层连接时才会显示邻居的 IP 地址。
    b. 要全局禁用 CDP，必须在接口配置模式下使用 no cdp enable 命令。
    c. CDP 可以全局禁用或在特定接口上禁用。
    d. 由于它在数据链路层运行，因此 CDP 只能在交换机中实现。
15. 在设计小型网络时选择设备时应考虑什么因素？
    a. 设备成本
    b. redundancy
    c. traffic analysis
    d. ISP

## Answers to “Check Your Understanding” Questions

### Chapter 1

1. C. 间谍软件是一种安装在用户设备上以收集用户信息的软件类型。
2. C. 组织可能会使用 extranet 为在不同组织工作但需要访问组织数据的个人提供安全可靠的访问。
3. C. BYOD 为终端用户提供使用个人设备访问信息并在企业或校园网络中通信的自由。
4. C. 家用用户、远程工作者和小型办公室通常需要连接到 ISP（互联网服务提供商）来访问互联网。
5. B. 无线互联网服务提供商（WISP）是一种 ISP，它使用与家庭无线局域网（WLAN）中类似的无线技术将订阅用户连接到指定的接入点或热点。WISP 最常见于 DSL 或有线服务不可用的农村环境。
6. B. 可扩展网络可以快速扩展以支持新用户和应用程序。
7. D. 容错网络在故障期间限制受影响设备的数量。它旨在在发生此类故障时允许快速恢复。
8. B and D. 可扩展网络可以快速扩展以支持新用户和应用程序。它在不降低现有用户访问的服务性能的情况下实现这一点。可扩展性通常在具有无线和移动设备的网络中是必需的，其中设备数量可能随时增加。
9. A. 路由器是一种互连多个网络的设备，负责在它们之间转发消息。
10. B and C. 蜂窝和卫星通信是无需物理电缆的无线技术。
11. B. 互联网是用于访问电子商务网站的通信网络。
12. D. BYOD 为终端用户提供使用个人设备访问信息并在企业或校园网络中通信的自由。趋势是允许员工从个人设备访问内部网络服务和信息。
13. C. 虚拟专用网络（VPN）为远程工作者提供对组织网络的安全访问。
14. C. 互联网是互连网络（internetwork，或简称为 internet）的全球集合。
15. A and D. 用户使用终端设备与网络交互。终端设备是网络上传输的消息的源或目的地。

### Chapter 2

1. A. 运行配置文件反映当前配置。修改运行配置会立即影响 Cisco 设备的操作。
