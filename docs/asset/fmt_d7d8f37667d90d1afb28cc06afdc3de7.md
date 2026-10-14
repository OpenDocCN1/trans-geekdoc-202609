
## Summary

This chapter cannot make you a networking expert. However, you should now have a basic understanding of how networks and the Internet work. Before you move on to subsequent chapters, you should make certain you completely understand basic hardware such as switches, NICs, routers, and hubs. You should also be familiar with the basic protocols presented in this chapter. It is important that you be comfortable with the utilities presented. It is strongly suggested that you experiment with these utilities extensively. It is also important that you be comfortable with the basics of the OSI model. Many students struggle with it at first, but at least make sure you have a general understanding of it before you move on to Chapter 3, “Cyber Stalking, Fraud, and Abuse.”

The material in this chapter will be critical in later chapters. If you are new to this material, you should thoroughly study this chapter before continuing. In the exercises at the end of this chapter, you will be able to practice using `IPConfig`, `tracert`, and `ping`.

## Test Your Skills

### Multiple Choice Questions

**1.** Malek is purchasing cable to use in setting up small office networks. He wants to stock up on commonly used cable. What type of cable do most networks use?

**A.** Net cable

**B.** STP

**C.** Phone cable

**D.** UTP

**2.** You are assigned with attaching connectors to segments of cable. What type of connector is used with network cables?

**A.** RJ-11

**B.** RJ-85

**C.** RJ-12

**D.** RJ-45

**3.** What type of cable is used in most networks?

**A.** Unshielded twisted-pair

**B.** Shielded twisted-pair

**C.** Unshielded untwisted-pair

**D.** Shielded untwisted-pair

**4.** John is trying to simply connect three computers in a small network. He does not need any sort of routing capability and is not concerned about network traffic. What is the simplest device for connecting computers?

**A.** NIC

**B.** Interface

**C.** Hub

**D.** Router

**5.** Sharice is trying to teach a new technician basic networking terms. What should she tell this new technician NIC stands for?

**A.** Network interface card

**B.** Network interaction card

**C.** Network interface connector

**D.** Network interaction connector

**6.** Which of the following is a device used to connect two or more networks?

**A.** Switch

**B.** Router

**C.** Hub

**D.** NIC

**7.** Juan has just installed a new T1 line in a medical office. The front desk receptionist has asked what speed they can expect. A T1 line sends data at what speed?

**A.** 100Mbps

**B.** 1.54Mbps

**C.** 155Mbps

**D.** 56.6Kbps

**8.** How big is a TCP packet header?

**A.** The size depends on the data being sent.

**B.** The size is always 20 bytes.

**C.** The size depends on the protocol being used.

**D.** The size is always 40 bytes.

**9.** What protocol translates web addresses into IP addresses?

**A.** DNS

**B.** TFTP

**C.** DHCP

**D.** SMTP

**10.** What protocol is used to send email, and on what port does it work?

**A.** SMTP, port 110

**B.** POP3, port 25

**C.** SMTP, port 25

**D.** POP3, port 110

**11.** Gunther is setting up encrypted remote communications so that the server administrators can remotely access servers. What protocol is used for remotely logging on to a computer in a secure manner?

**A.** SSH

**B.** HTTP

**C.** Telnet

**D.** SMTP

**12.** Mohammed needs to open a firewall port so that web traffic can be passed through the firewall. What protocol is used for web pages, and on which port does it work?

**A.** HTTP, port 21

**B.** HTTP, port 80

**C.** DHCP, port 80

**D.** DHCP, port 21

**13.** What is the name for the point where the backbones of the Internet connect?

**A.** Connectors

**B.** Routers

**C.** Network access points

**D.** Switches

**14.** You are examining a list of IP addresses. Some are internal, some are external, and some are not valid. Which of the following is not a valid IP address?

A. `127.0.0.1`

B. `295.253.254.01`

C. `131.156.5.2`

D. `245.200.11.1`

15. 193.44.34.12 这个 IP 地址属于什么类型的地址？

A. `A`

B. `B`

C. `C`

D. `D`

16. 127.0.0.1 始终指向你的什么？

A. 最近的路由器

B. ISP

C. 自己

D. 最近的 NAP

17. 形式为 [www.chuckeasttom.com](http://www.chuckeasttom.com) 的 Internet 地址称为什么？

A. 用户友好的网页地址

B. 统一资源定位符

C. 用户可访问的网页地址

D. 统一地址标识符

18. 哪个美国政府机构创建了构成互联网基础的分布式网络？

A. 高级研究项目署

B. 中央情报局

C. NASA

D. 能源部

19. 原始分布式网络的三所参与大学中，哪一所在下列选项中被提及？

A. 加州大学伯克利分校

B. 哈佛大学

C. 麻省理工学院

D. 普林斯顿大学

20. 向一群一年级学生解释网络历史时，Vince Cerf 发明了什么？

A. 万维网

B. 电子邮件

C. TCP

D. 第一个计算机病毒

21. 向一群一年级学生解释网络历史时，Tim Berners-Lee 发明了什么？

A. 万维网

B. 电子邮件

C. TCP

D. 第一个计算机病毒

22. John 使用命令行工具收集诊断信息，针对无法连接网络的计算机，哪个工具提供机器的网络配置信息？

A. `Ping`

B. `IPConfig`

C. `Tracert`

D. `MyConfig`

23. Sheryl 向新技术人员解释 OSI 模型，问 TCP 在 OSI 模型的哪一层运行？

A. 传输层

B. 应用层

C. 网络层

D. 数据链路层

24. OSI 模型的哪一层被分为两个子层？

A. 数据链路层

B. 网络层

C. 表示层

D. 会话层

25. 下列哪个是唯一的十六进制数，用于标识你的网卡？

A. NIC 地址

B. MAC 地址

C. NIC ID

D. MAC ID

### Exercises

**Exercise 2.1:** 使用 `IPConfig`

1. 打开命令提示符或在 Windows 10 的搜索栏中输入 `cmd`。

2. 输入 `ipconfig`。

3. 使用 `IPConfig` 命令的输出查找计算机的信息。

4. 记录你的计算机的 IP 地址、默认网关和子网掩码。

**Exercise 2.2:** 使用 `Tracert`

1. 打开命令提示符或 DOS 提示符。

2. 输入 `tracert www.chuckeasttom.com`。

3. 记录你的计算机到 [www.chuckeasttom.com](http://www.chuckeasttom.com) 的路由跳数。

4. 重复步骤 2 和 3，分别对 [www.whitehouse.gov](http://www.whitehouse.gov) 和 [`home.pearsonhighered.com/`](http://home.pearsonhighered.com/) 进行操作。

5. 观察前几个跳数相同的情况，记录每个目标的跳数以及相同的跳数，然后简要说明为何部分中间步骤在不同目标之间相同。

**Exercise 2.3:** `NSLOOKUP`

1. 打开命令提示符。

2. 输入 `nslookup www.chuckeasttom.com`。

3. 记录该命令返回的实际服务器名称（依据托管公司的命名规范）、IP 地址以及该服务器的别名。

**Exercise 2.4:** 更多关于 `IPConfig`

1. 打开命令提示符或 DOS 提示符。

2. 使用 `ipconfig -?` 命令查看 `IPConfig` 的其他选项，例如 `/all`、`/renew` 等。

3. 执行 `ipconfig /all`，记录此时比仅使用 `ipconfig`（Exercise 2.1）时多出的信息。

**Exercise 2.5:** 更多关于 `Ping`

1. 打开命令提示符或 DOS 提示符。

2. 使用 `ping -?` 查看 `ping` 的其他选项，如 `-w`、`-t`、`-n`、`-i` 等。

3. 执行 `ping www.chuckeasttom.com`。

4. 尝试 `ping -n 2 www.chuckeasttom.com`，然后执行 `ping -n 7 www.chuckeasttom.com`，观察差异。

### Projects

**Project 2.1:** 学习 DNS 协议

1. 使用网络资源查找 DNS 协议，可参考：[www.freesoft.org/CIE/Topics/75.htm](http://www.freesoft.org/CIE/Topics/75.htm)。

2. 查找以下信息：谁发明了 DNS 协议？它的用途是什么？它是如何工作的？

3. 写一篇简短的论文，描述该协议的功能，并简要说明其发明者、发明时间以及工作原理。

**Project 2.2:** 学习你的系统

1. 查找你的组织（例如学校或企业）是否使用交换机、集线器或两者。原因是什么？可以向网络管理员或帮助台询问，并说明这是为课程项目而进行的。

2. 写一篇简短的论文，阐述你的发现，并说明如果可以进行改动，你会如何改进。例如，如果组织仅使用集线器，你会否改为使用交换机，理由是什么？

**Project 2.3:** 学习 `NetStat`

1. 在命令提示符中输入 `netstat`，观察它提供的信息，包括当前连接到你电脑的服务器的 IP 地址或名称。若使用的是家用电脑，需要登录互联网服务提供商（ISP）后才能看到相关内容。

Caution

停止 `NetStat`

注意：在许多 Windows 版本中，需要使用 `Ctrl+Break` 组合键停止 `netstat`，然后再次使用新选项启动。

2. 输入 `netstat -?` 查看可用的选项，如 `-a`、`-e` 等。

3. 执行 `netstat -a`，记录你看到的信息。

4. 最后，尝试 `netstat -e`，观察其输出内容。

在每个新前沿，犯罪分子必然会出现。在过去的时代，高 seas 孕育了海盗，美国的 Wild West 产生了出法者的帮派。Internet 与其他前沿不同寻常：它也有它的出法者。除了 Chapter 1 “Introduction to Computer Security”，提到的 Chapter 1 “Introduction to Computer Security”，还有其他危险。欺诈是互联网最常见的危险之一。随着越来越多的人将 Internet 作为商业的通道，欺诈机会随之增大。欺诈自文明存续以来就一直是生活的一部分；在过去的世纪里，“蛇油”推销员四处游荡，兜售面部治疗和药剂。Internet 让这种欺诈变得更加容易。事实上，许多专家会认为欺诈是互联网上最普遍的危险。诈骗者喜欢 Internet 欺诈的多种原因。首先，进行 Internet 欺诈不需要像黑客和病毒创建那样的技术专长。其次，在线各种形式的商业活动人数众多，这种大量的商业活动为欺诈提供了大量机会。

互联网上有许多欺诈途径。本章我们将探讨欺诈的主要类型、法律的规定以及你可以采取的自我保护措施。好消息是，对于某些读者而言，这一章并不特别技术性，因为大多数 Internet 欺诈并不依赖于深入的技术专长。Internet 欺诈仅仅把电脑作为实施多种历史上已有的欺诈手段的场所。

### How Internet Fraud Works

欺诈可以通过 Internet 以多种方式进行。美国证券交易委员会（SEC）在其网站上列出了若干 Internet 欺诈类型；^(1) 我们将简要讨论其中的每一种以及其他类型，但不可能全面覆盖每一种欺诈方案的所有变体。这将填满一整本书，甚至可能需要多卷。我们可以做的是介绍最常见的诈骗，并尝试总结出一些通用原则，供你应对任何潜在的欺诈。如果你用这些具体案例来总结通用原则，你就应该能够避免大多数欺诈方案。

1. [`www.sec.gov/reportspubs/investor-publications/investorpubscyberfraudhtm.html`](https://www.sec.gov/reportspubs/investor-publications/investorpubscyberfraudhtm.html)

#### Investment Offers
