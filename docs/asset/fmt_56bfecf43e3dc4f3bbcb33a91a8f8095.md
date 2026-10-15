
3. Oracle
4. Amazon Athena

## 10. 哪项 RDS 功能可帮助您实现 99.95% 的月度可用性？

1. 多可用区（Multi‑AZ）
2. 只读副本
3. 点时间恢复（Point‑in‑time recovery）
4. 水平扩展（Horizontal scaling）

## 11. 关于 DynamoDB 分区（partition）的两项正确描述是？

1. 它存储在表内部。
2. 它基于固态硬盘（solid‑state drives）。
3. 它是唯一标识表中项目的方式。
4. 它跨越多个可用性区（Availability Zones）进行复制。

## 12. DynamoDB 在单个 Region 中的最小月度可用性是多少？

1. 99.99 %
2. 99.95 %
3. 99.9 %
4. 99.0 %

## 13. 关于 DynamoDB 表的正确描述是？

1. 它只能存储一种数据类型。
2. 创建表时必须定义它可以存储的最大项数。
3. 表中的项可以对主键具有重复值。
4. 表中的项不必拥有所有相同的属性。

## 14. 哪两项配置参数可用于提高 DynamoDB 表的写入性能？（选择两项）

1. 减少读容量单位（RCU）
2. 增加读容量单位
3. 增加写容量单位（WCU）
4. 减少写容量单位
5. 启用 DynamoDB 自动扩缩（Auto Scaling）

## 15. 哪项 DynamoDB 操作最具读取密集性？

1. 写入
2. 查询（Query）
3. 扫描（Scan）
4. 更新（Update）

## 16. 对于存储客户列表的 DynamoDB 表，以下哪项最适合作为主键？

1. 客户的全名
2. 客户的电话号码
3. 客户的城市
4. 一个随机生成的客户 ID

## 17. 哪种 Redshift 节点使用磁盘存储？

1. 成本优化
2. 密集计算
3. 密集存储
4. 密集内存

## 18. 哪项 Redshift 功能可分析存储在 S3 中的结构化数据？

1. Redshift Spectrum
2. Redshift S3
3. Amazon Athena
4. Amazon RDS

## 19. 用于存储大量来自多种来源的结构化数据以用于报告和分析的关系型数据库的术语是什么？

1. 数据存储库
2. 数据仓库
3. 报告集群
4. 密集存储节点

## 20. 使用密集存储节点时，Redshift 集群的最大可存储数据量是多少？

1. 2 PB
2. 326 TB
3. 2 TB
4. 326 PB
5. 236 TB

# Chapter 10: The Core Networking Services

## THE AWS CERTIFIED CLOUD PRACTITIONER EXAM OBJECTIVES COVERED IN THIS CHAPTER MAY INCLUDE, BUT ARE NOT LIMITED TO, THE FOLLOWING:

### Domain 3: Technology

- ![images](img/correction.png) 3.1 Define methods of deploying and operating in the AWS Cloud
- ![images](img/correction.png) 3.2 Define the AWS global infrastructure
- ![images](img/correction.png) 3.3 Identify the core AWS services

![images](img/clogo.jpg)

## Introduction

Networking is ultimately about transporting data to and from your AWS resources. How you achieve this depends on many factors, including the type of data, the speed of data transport, your security requirements, who or what will be accessing that data, and how they’ll be accessing it. In this chapter, you’ll learn about the following three core networking services AWS offers:

* Virtual Private Cloud
* Route 53
* CloudFront

## Virtual Private Cloud

The Amazon Virtual Private Cloud (VPC) service provides the network backbone for many AWS services. A virtual private cloud is a virtual network in the AWS cloud that’s logically isolated from other networks. The most well-known use of VPCs is connecting EC2 instances together and to other AWS services and networks, including the internet.

When you create an AWS account, Amazon automatically creates a default VPC in each region. The default VPC is configured to allow instances within the VPC to access the internet. This way you don’t have to create and configure your own VPC just to use EC2.

You can create your own nondefault VPCs. Nondefault VPCs are fully isolated from every other network and AWS resource, including other VPCs. This means you’ll have to configure them explicitly if you want them to have access to other networks and AWS resources outside of the VPC.

### VPC CIDR Blocks

Each VPC requires a Classless Inter-Domain Routing (*CIDR*) block to define the range of IP version 4 (IPv4) addresses that resources within the VPC can use. Default VPCs have a CIDR of 172.31.0.0/16, which includes all addresses from 172.31.0.0 to 172.31.255.255. The /16 refers to the size of the CIDR. You must choose a CIDR size between /16 and /28, but otherwise, any CIDR you could assign to a traditional network can also be assigned to a VPC. The smaller the CIDR size, the greater the number of IP addresses available to the VPC. The following are a few examples of CIDR blocks that you could assign to a VPC:

* 10.0.0.0/16 (10.0.0.0–10.0.255.255)
* 192.168.0.0/24 (192.168.0.0–192.168.0.255)
* 172.16.0.0/28 (172.16.0.0–172.16.0.15)

At your request, AWS can also assign an IPv6 CIDR block to your VPC. The IPv6 CIDR will be a global unicast IPv6 address with a size of /56.

![](img/note.jpg) The acronym CIDR is usually pronounced “cider” for brevity.

### Subnets

Each VPC requires further division into one or more subnets. A subnet provides logical separation and isolation of resources within the same VPC. For example, you may want to have web servers and application servers in the same VPC, but you want only the web servers to be accessible from the internet.

As with a VPC, you must define a CIDR for each subnet. The subnet CIDR must be a subset of the VPC CIDR, with a size between /16 and /28. For example, if the default VPC CIDR is 172.31.0.0/16, then a subnet CIDR could be 172.31.16.0/20. Each subnet exists only within a single Availability Zone. Refer to Figure 10.1 for a sample VPC topology with two subnets.

![FIGURE 10.1 A VPC with two subnets in different Availability Zones.](img/c10f001.jpg)

**FIGURE 10.1** A VPC with two subnets in different Availability Zones.

Each EC2 instance exists within a subnet. This is why within each default VPC, Amazon creates a default subnet in each Availability Zone. This way, you can launch EC2 instances without ever having to configure a VPC.

### Internet Access

An *internet gateway* is a VPC resource that allows EC2 instances to obtain a public IP address and access the internet.

For instances in a subnet to have internet access, that subnet must contain a default route to the internet gateway that’s attached to the VPC. A subnet with a default route to an internet gateway is called a *public subnet*.

Each instance must also have a public IP address. When you launch an instance, you can choose to have AWS automatically assign it one. You can’t reassign an automatically assigned public IP address, and when the instance stops or terminates, you lose it. Alternatively, you can allocate an elastic IP address and then assign it to an instance. Elastic IP addresses can be reassigned to different instances and don’t change until you deallocate them.

### Security Groups

一个 `security group` 是一个防火墙，用于决定哪些网络流量可以进入和离开实例。每个实例必须至少关联一个 security group。

Security groups 包含入站和出站规则，根据 IP 地址和协议允许网络流量通过。入站规则控制哪些 IP 地址可以向实例发送流量，而出站规则控制实例可以向哪些 IP 地址发送流量。默认情况下，security groups 不包含入站规则，这确保不会有未经请求的流量到达实例。例如，如果你想让任何人都能访问公共子网中的 Web 服务器，你需要创建一个入站规则，允许来自任何 IP 地址的 HTTP 流量。

默认情况下，每个 security group 包含一个出站规则，允许访问任何 IP 地址。需要注意的是，当实例发送流量时，security group 会允许回复流量到达实例，无论入站规则如何配置。

每个 VPC（不仅仅是默认 VPC）都包含一个默认 security group，你可以对其进行修改以满足需求。

### Network Access Control Lists

一个 `network access control list` (`NACL`) 是一个在子网层面运行的防火墙。NACL 包含入站和出站规则，默认情况下允许所有流量。NACL 不能限制同一子网内实例之间的流量，但它可以阻止流量进入或离开子网。每个 VPC 都有一个默认 NACL，可以将其关联到一个或多个子网。

### VPC Peering

一个 `VPC peering connection` 是仅限两个 VPC 之间的私有、点对点连接。VPC peering 允许不同 VPC 中的资源通过私有 AWS 网络进行通信，而不是通过公共互联网。VPC peering 连接允许一个 VPC 中的实例访问另一个 VPC 中的特定资源，例如另一个实例或网络负载均衡器。

VPC peering 连接是快速、可靠且安全的。此外，使用 VPC peering 无需 VPC 资源拥有 internet 访问权限即可使用。 peered VPCs 可以在同一区域或不同区域。

### Virtual Private Networks

一个 virtual private network (`VPN`) 允许你通过安全的、跨越公共互联网的连接将 VPC 连接到外部网络，例如数据中心或办公室。要设置 VPN 连接，你需要创建一个 virtual private gateway 并将其附加到 VPC。然后，你需要配置你的 customer gateway（一个物理或虚拟路由器或防火墙）以连接到 virtual private gateway。AWS 已测试了多种厂商的 customer gateway，包括 Cisco、Juniper、Palo Alto Networks 和 Check Point。

VPN 连接使用 AES 128 位或 256 位加密。IP 路由可以配置为静态，也可以使用 Border Gateway Protocol (BGP) 在 VPC 和外部网络之间共享路由。一个 VPC 最多可以有 10 个 VPN 连接。

## Direct Connect

Direct Connect 提供私有网络连接到你的 VPC 和公共服务，如 Amazon S3 和 Glacier。无需单独建立 internet 电路即可访问这些服务。这意味着在访问 AWS 资源时可以完全绕过公共互联网。请注意，Direct Connect 不提供 internet 访问，因此如果你需要它，仍需单独建立 internet 连接。

Direct Connect 链路通过 AWS Partner Network (APN) 合作伙伴提供。Direct Connect 使用专用链路，运行在 1 或 10 Gbps。由于此原因，它不受宽带 internet 连接的高延迟和不可预测性的影响。如果你需要快速、稳定的连接到 AWS，Direct Connect 是一个比通过公共 internet 连接更好的选择。然而，它更昂贵。

如果你需要少于 1 Gbps 的带宽，可以从 APN 合作伙伴处获得 hosted Direct Connect 连接。hosted 连接的速率包括 50 Mbps、100 Mbps、200 Mbps、300 Mbps、400 Mbps 和 500 Mbps。

## Route 53
