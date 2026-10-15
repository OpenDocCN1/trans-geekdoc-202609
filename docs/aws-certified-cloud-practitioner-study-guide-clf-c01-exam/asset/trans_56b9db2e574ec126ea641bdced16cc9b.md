
## 2. PostgreSQL

## 3. MariaDB

## 4. Oracle

## 5. Microsoft SQL Server

## 8. 哪两项 Amazon RDS（托管关系型数据库服务）功能可在可用性区（Availability Zone）故障时防止数据丢失？（选择两项）

1. 只读副本  
2. 多可用区（Multi‑AZ）  
3. 快照  
4. IOPS  
5. 垂直扩展  

## 9. 哪项 RDS 数据库引擎会自动扩展存储空间，最大可达 64 TB？

1. Microsoft SQL Server  
2. Amazon Aurora  
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

1. 99.99 %  
2. 99.95 %  
3. 99.9 %  
4. 99.0 %  

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

1. 2 PB  
2. 326 TB  
3. 2 TB  
4. 326 PB  
5. 236 TB  

## Chapter 10  

## The Core Networking Services  

## THE AWS CERTIFIED CLOUD PRACTITIONER EXAM OBJECTIVES COVERED IN THIS CHAPTER MAY INCLUDE, BUT ARE NOT LIMITED TO, THE FOLLOWING:  

## Domain 3: Technology  

## ![images](images/correction.png) 3.1 Define methods of deploying and operating in the AWS Cloud  

## ![images](images/correction.png) 3.2 Define the AWS global infrastructure  

## ![images](images/correction.png) 3.3 Identify the core AWS services  

![images](images/clogo.jpg)  

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

Each VPC requires a Classless Inter-Domain Routing (*CIDR*) block to define the range of IP version 4 (IPv4) addresses that resources within the VPC can use. Default VPCs have a CIDR of 172.31.0.0/16, which includes all addresses from 172.31.0.0 to 172.31.255.255. The /16 refers to the size of the CIDR. You must choose a CIDR size between /16 and /28, but otherwise, any CIDR you could assign to a traditional network can also be assigned to a VPC. The smaller the CIDR size, the greater the number of IP addresses available to the VPC. The following are a few examples of CIDR blocks that you could assign to a VPC:  

* 10.0.0.0/16 (10.0.0.0–10.0.255.255)  
* 192.168.0.0/24 (192.168.0.0–192.168.0.255)  
* 172.16.0.0/28 (172.16.0.0–172.16.0.15)  

At your request, AWS can also assign an IPv6 CIDR block to your VPC. The IPv6 CIDR will be a global unicast IPv6 address with a size of /56.  

![](images/note.jpg) The acronym CIDR is usually pronounced “cider” for brevity.  

### Subnets  

Each VPC requires further division into one or more subnets. A subnet provides logical separation and isolation of resources within the same VPC. For example, you may want to have web servers and application servers in the same VPC, but you want only the web servers to be accessible from the internet.  

As with a VPC, you must define a CIDR for each subnet. The subnet CIDR must be a subset of the VPC CIDR, with a size between /16 and /28. For example, if the default VPC CIDR is 172.31.0.0/16, then a subnet CIDR could be 172.31.16.0/20. Each subnet exists only within a single Availability Zone. Refer to [Figure 10.1](#c10.xhtml#figure10-1) for a sample VPC topology with two subnets.  

![FIGURE 10.1 A VPC with two subnets in different Availability Zones.](images/c10f001.jpg)  

[**FIGURE 10.1**](#c10.xhtml#figureanchor10-1) A VPC with two subnets in different Availability Zones.  

Each EC2 instance exists within a subnet. This is why within each default VPC, Amazon creates a default subnet in each Availability Zone. This way, you can launch EC2 instances without ever having to configure a VPC.  

### Internet Access  

An *internet gateway* is a VPC resource that allows EC2 instances to obtain a public IP address and access the internet.  

For instances in a subnet to have internet access, that subnet must contain a default route to the internet gateway that’s attached to the VPC. A subnet with a default route to an internet gateway is called a *public subnet*.  

Each instance must also have a public IP address. When you launch an instance, you can choose to have AWS automatically assign it one. You can’t reassign an automatically assigned public IP address, and when the instance stops or terminates, you lose it. Alternatively, you can allocate an elastic IP address and then assign it to an instance. Elastic IP addresses can be reassigned to different instances and don’t change until you deallocate them.  

### Security Groups  

