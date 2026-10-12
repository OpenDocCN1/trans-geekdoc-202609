

# ACL 规则与防火墙技术

## 标准 ACL 与扩展 ACL

| 规则编号 | 动作 | 协议 | 源地址 | 目的地址 | 方向 | 状态 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Rule 255 | Deny | ALL | — | — | Bidirectional | None |

对于 CASP 考试，你需要对 ACL 及其格式有基本的了解。在 Cisco IOS 环境中，标准 ACL 的命令语法格式如下：

```
access-list access-list-number {permit|deny} ↵
{host|source source-wildcard|any}
```

此外还有扩展 ACL。这些规则能够更深入地检查流量，并可检测更多项目，例如：

*   协议
*   端口号
*   区分服务代码点（DSCP）值
*   优先级值
*   同步序列号（SYN）位的状态

扩展 IP、ICMP、TCP 和 UDP ACL 的命令语法格式如下所示：

### IP 流量

```
access-list access-list-number
     [dynamic dynamic-name [timeout minutes]]
     {deny|permit} protocol source source-wildcard
     destination destination-wildcard [precedence precedence]
     [tos tos] [log|log-input] [time-range time-range-name]
```

### ICMP 流量

```
access-list access-list-number
     [dynamic dynamic-name [timeout minutes]]
     { deny|permit } icmp source source-wildcard
     destination destination-wildcard
     [icmp-type [icmp-code] |icmp-message]
     [precedence precedence] [tos tos] [log|log-input]
     [time-range time-range-name]
```

### TCP 流量

```
access-list access-list-number
     [dynamic dynamic-name [timeout minutes]]
     { deny|permit } tcp source source-wildcard [operator [port]]
     destination destination-wildcard [operator [port]]
     [established] [precedence precedence] [tos tos]
     [log|log-input] [time-range time-range-name]
```

### UDP 流量

```
access-list access-list-number
     [dynamic dynamic-name [timeout minutes]]
     { deny|permit } udp source source-wildcard [operator [port]]
     destination destination-wildcard [operator [port]]
     [precedence precedence] [tos tos] [log|log-input]
     [time-range time-range-name]
```

## 基本规则工作原理回顾

[图 4.2](#c04.xhtml#c04-fig-0002) 展示了一个基本网络配置，其中两个网段由一台路由器和一个通用的互联网连接隔开。

![图 4.2 带防火墙的基本网络](images/c04f002.jpg)

[**图 4.2**](#c04.xhtml#c04-fig-anc-0002) 带防火墙的基本网络

在第一个示例中，假设已决定阻止所有 Telnet 流量。Telnet 通过明文发送信息，不被视为安全协议。

```
hostname R1
!
interface ethernet0
ip access-group 102 in
!
access-list 102 deny tcp any any eq 23
access-list 102 permit ip any any
```

在此配置中，所有目标端口为 23 的 TCP 流量均被防火墙阻止。所有其他流量均被允许。

在该示例中，目标端口非 TCP/23 的 Telnet 连接仍将被允许。若要阻止任意 TCP 端口上的 Telnet，则需要其他控制手段。此外需了解，标准 ACL 常用于限制对路由器等设备的 Telnet 或 SSH 访问，方法是将访问权限限制在特定 IP 地址。扩展 ACL 则用于更多任务。另请注意，前面的示例仅用于演示目的。通常认为最佳实践是仅允许所需内容并拒绝其他所有内容，即遵循最小权限原则。

[练习 4.1](#c04.xhtml#c04-ex-01) 演示了如何查看基本 ACL。

## 基于主机的防火墙

在回顾了防火墙之后，我们将关注点转移到基于主机的防火墙。防火墙通常部署在受信与非受信网络元素的分界线上，但也可部署在主机系统上。**基于主机的防火墙**是直接运行在网络主机或设备上的设备。部署基于主机的防火墙旨在保护其所安装的设备免受攻击。基于主机的防火墙通常具有预定义规则，以针对特定攻击模式保护主机。基于主机的防火墙可与隔离和修复配合使用。某些基于主机的防火墙还能防止恶意软件攻击网络上的其他设备。增加基于主机的防火墙体现了纵深防御的概念。[图 4.3](#c04.xhtml#c04-fig-0003) 展示了该概念的示例。

![图 4.3 纵深防御与多层防护](images/c04f003.jpg)

[**图 4.3**](#c04.xhtml#c04-fig-anc-0003) 纵深防御与多层防护

基于主机的防火墙通过检查和控制入站及出站流量来工作。尽管防火墙种类繁多，但只有基于主机的防火墙设计为驻留在终端主机上并保护其免受攻击。与所有防火墙一样，基于主机的防火墙通过检查穿过接口的流量来工作。其工作方式与边境警卫和海关人员非常相似。当人员和产品跨越一国边境前往另一国时，都会接受检查。所有防火墙均通过使用预定义规则集工作。

基于主机的防火墙的一大优势是，它可以通过增加另一层控制来强化纵深防御。如果网络防火墙失效，基于主机的防火墙将充当额外的防御层。基于主机的防火墙的一个缺点是，如果主机失效，则防火墙可能被突破。另一个缺点是在多基于主机的防火墙系统中更新策略会比较困难。基于主机的防火墙产品示例包括 `Windows Firewall`、`IPTables`、`Norton Personal Firewall`、`Zone Labs ZoneAlarm`、`Sunbelt Personal Firewall` 和 `Sygate Personal Firewall`。

即使有边缘防护（部署在网络边缘的设备）和基于主机的防火墙，攻击有时仍能突破。这就是为什么公司要增加应用感知和协议感知技术，包括入侵检测、入侵防御以及下一代防火墙，它们具备检查 Web 应用程序数据的能力。下一代防火墙可协助对可疑网络流量进行隔离/修复。下一代防火墙通常部署在网络边缘，位于非军事区/外部/内部网络之间，有助于关键资产的隔离。

Web 应用程序防火墙（WAF）是一种下一代技术，有助于解决 Web 应用程序安全问题。WAF 并非传统防火墙的替代品，而是增加了另一层防护。传统防火墙仅阻断或允许流量，而 WAF 可防范跨站脚本攻击、隐藏字段篡改、Cookie 投毒甚至 SQL 注入。WAF 通过检查 TCP/IP OSI 模型的高层来工作，并与特定 Web 应用紧密集成。可以这样理解：传统防火墙可能在边界拒绝入站流量。但对于 80 或 443 端口的流量呢？对于公司或组织而言，完全停止互联网通信可能并非可行选项。这就是 WAF 发挥作用的地方。WAF 在保护组织免受社交网络及其他 Web 2.0 应用固有的新兴威胁方面具有重大意义，而传统防火墙并未设计用于防御这些威胁。开源 WAF 示例包括 `ModSecurity`。商业选项由 `Barracuda Networks`、`Fortinet` 和 `Cisco Systems` 提供。顺便提一下，`Suricata` IDS 项目中使用的解析器（HTP Library）由 `ModSecurity` 的 `Ivan Ristic` 编写；这两个项目在不久的将来值得关注。

[练习 4.2](#c04.xhtml#c04-ex-02) 演示了如何配置 `IPTables`。

## 可信操作系统

