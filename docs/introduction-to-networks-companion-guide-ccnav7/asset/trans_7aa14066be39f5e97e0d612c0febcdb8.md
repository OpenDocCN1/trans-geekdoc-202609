
## 练习

以下活动提供了本章介绍主题的练习。实验可在配套的 *Introduction to Networks Labs & Study Guide* (*CCNAv7*)（ISBN 9780136634454）中找到。Packet Tracer 活动说明也提供在 *Labs & Study Guide* 中。PKA 文件可在在线课程中获得。

![](img/e71dc48d3ae3db3394e5857ab2acae75_603_0.png)

## 实验

- Lab 16.2.6：研究网络安全威胁
- Lab 16.4.7：使用 SSH 配置网络设备
- Lab 16.5.2：保护网络设备

![](img/e71dc48d3ae3db3394e5857ab2acae75_603_1.png)

## Packet Tracer 活动

- Packet Tracer 16.4.6：配置安全密码和 SSH
- Packet Tracer 16.5.1：保护网络设备

## 检查你的理解问题

完成此处列出的所有复习问题，以测试你对本章主题和概念的理解。附录“‘检查你的理解’问题的答案”列出了答案。

+   1. 哪个组件旨在防止对计算机的未经授权的通信？
   a. security center
   b. port scanner
   c. antimalware
   d. antivirus
   e. firewall
2. 如果在 10 秒内有 2 次登录失败，哪个命令会阻止对 RouterA 的登录尝试 30 秒？
   a. RouterA(config)# login block-for 10 attempts 2 within 30
   b. RouterA(config)# login block-for 30 attempts 2 within 10
   c. RouterA(config)# login block-for 2 attempts 30 within 10
   d. RouterA(config)# login block-for 30 attempts 10 within 2

3. 网络安全记账功能的目的何在？
a. to require users to prove who they are
b. to determine which resources a user can access
c. to keep track of the actions of users
d. to provide challenge-and-response questions

4. 可能涉及使用 nslookup 和 fping 等工具的攻击类型是什么？
a. access attack
b. reconnaissance attack
c. denial-of-service attack
d. worm attack

5. SSH 相对于 Telnet 在远程管理路由器时提供什么好处？
a. encryption
b. TCP usage
c. authorization
d. connections via multiple vty lines

6. 保护用户免受外部威胁的最有效安全工具之一是什么？
a. firewall
b. router that run AAA services
c. path server
d. password encryption

7. 哪种类型的网络威胁旨在阻止授权用户访问资源？
a. DoS attack
b. access attack
c. reconnaissance attack
d. trust exploitation

8. AAA 框架提供了哪三项服务？（选择三项。）
+   a. accounting
b. automation
c. authorization
d. authentication
e. availability
f. autoconfiguration

9. 哪种恶意代码攻击是自包含的并试图利用系统中的特定漏洞？
+   a. virus
b. worm
c. Trojan horse
d. maintenance

10. 空调单元故障后，配线间中的一些路由器和交换机出现故障。这种情况描述了哪种类型的威胁？
+   a. configuration
b. environmental
c. electrical
d. maintenance

11. 术语“漏洞”是什么意思？
+   a. a weakness that makes a target susceptible to an attack
b. a computer that contains sensitive information
c. a method of attack to exploit a target
d. a known target or victim machine
e. a potential threat a hacker creates

12. 实现对路由器的 SSH 访问必须执行哪三个配置步骤？（选择三项。）
+   a. a password on the console line
b. an IP domain name
c. a user account
d. an enable mode password
e. a unique hostname
f. an encrypted password

13. 网络侦察攻击的目标是什么？
+   - a. discover and map systems
- b. manipulate data without authorization to do so
- c. disable network systems or services
- d. deny access to resources by legitimate users

14. 出于安全原因，网络管理员需要确保本地计算机不能相互 ping。哪些设置可以完成此任务？
+   - a. smartcard settings
- b. firewall settings
- c. MAC address settings
- d. file system settings

15. 网络管理员通过 SSH 建立到交换机的连接。什么特征唯一描述了 SSH 连接？
+   - a. out-of-band access to a switch through the use of a virtual terminal with password authentication
- b. remote access to the switch through the use of a telephone dialup connection
- c. on-site access to a switch through the use of a directly connected PC and a console cable
- d. remote access to a switch where data is encrypted during the session
- e. direct access to the switch through the use of a terminal emulation program

## 目标

完成本章后，你将能够回答以下问题：

- 在小型网络中使用哪些设备？
- 在小型网络中使用哪些协议和应用程序？
- 小型网络如何作为大型网络的基础？
- 如何使用 ping 和 tracert 命令的输出来验证连接并建立相对网络性能？
- 如何使用主机和 IOS 命令获取有关网络中设备的的信息？
- 常见的网络故障排除方法有哪些？
- 如何排除网络中设备的故障？

## 关键术语

本章使用了以下关键术语。你可以在本书末尾的词汇表中找到定义。

*冗余* 第 576 页
*协议分析器* 第 583 页
*服务质量 (QoS)* 第 577 页

## 引言 (17.0)

Hooray! 你已经来到本书的最后一章。你现在已经掌握了设置自己的网络所需的大部分基础知识。接下来去哪里？当然是构建网络。一旦你构建了网络，你需要验证它是否正常工作，并且可能还需要排除一些常见的网络问题。本章包含实验和 Packet Tracer 活动，帮助你练习作为网络管理员的新技能。让我们开始吧！

## 小型网络中的设备 (17.1)

小型网络中的网络设备数量和类型通常与大型网络不同，但各种规模的网络都必须能够提供许多相同的服务。

### 小型网络拓扑 (17.1.1)

大多数企业规模较小；因此，大多数企业网络也规模较小，这并不令人惊讶。

小型网络设计通常很简单。与大型网络相比，小型网络的设备数量和类型明显较少。例如，请参阅图 17-1 所示的示例小型企业网络。

![](img/e71dc48d3ae3db3394e5857ab2acae75_608_0.png)

图 17-1 小型企业网络拓扑

此小型网络需要路由器、交换机和无线接入点来连接有线和无线用户、IP 电话、打印机和服务器。小型网络通常具有单个 WAN 连接，由 DSL、电缆或以太网连接提供。

大型网络需要 IT 部门来维护、保护和排除网络设备的故障并保护组织数据。管理小型网络需要与管理大型网络所需的许多相同技能。小型网络由本地 IT 技术人员或合同专业人员管理。

### 小型网络的设备选择 (17.1.2)

与大型网络一样，小型网络也需要规划和设计以满足用户需求。规划确保所有需求、成本因素和部署选项都得到充分考虑。

第一个设计考虑因素之一是用于支持网络的中介设备类型。以下各节描述了在选择网络设备时必须考虑的因素。

### 成本

交换机或路由器的成本由其容量和功能决定，例如可用端口的数量和类型以及背板速度。影响成本的其他因素包括网络管理能力、嵌入式安全技术和可选的高级交换技术。连接网络上每个设备所需的布线费用也必须考虑。影响成本考虑的另一个关键因素是要纳入网络中的冗余量。

### 速度和端口/接口类型

选择路由器或交换机上的端口数量和类型是一个关键决策。较新的计算机具有内置 1 Gbps NIC。一些服务器甚至可能具有 10 Gbps 端口。虽然成本更高，但选择能够适应更高速度的第 2 层设备可以使网络演进，而无需更换核心设备。

### 可扩展性

网络设备有固定和模块化物理配置。固定配置设备具有特定数量和类型的端口或接口，不能扩展。模块化设备具有扩展槽，可在需求演变时添加新模块。交换机可提供额外的端口用于
