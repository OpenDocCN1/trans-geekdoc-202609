

# AWS 认证考试题库

## 44. 以下哪项在 AWS 中取代了传统防火墙设备？

1.  NACLs、IAM、WAF
2.  **安全组**、IAM、WAF
3.  NACLs、**安全组**
4.  **安全组**、VPCs、VPGs

## 45. 以下哪些资源会作为 AWS 为所有 AWS 账户设置的默认 VPC 的一部分而自动创建？（选择两项。）

1.  **Internet gateway**
2.  Virtual private gateway
3.  **Public subnet**
4.  NAT gateway

## 46. 将终止作为 Auto Scaling Group 一部分的实例时所考虑的因素按优先级从高到低排序。

1.  启动配置的使用时长、拥有最多实例的可用区、距下一个计费小时的临近程度
2.  **拥有最多实例的可用区、启动配置的使用时长、距下一个计费小时的临近程度**
3.  启动配置的使用时长、距下一个计费小时的临近程度、拥有最多实例的可用区
4.  拥有最多实例的可用区、距下一个计费小时的临近程度、启动配置的使用时长

## 47. AWS 支持两种虚拟化类型：半虚拟化和硬件虚拟机。为何要选择其中一种虚拟化类型而非另一种？

1.  半虚拟化允许使用硬件扩展（如增强联网和 GPU 处理），但硬件虚拟化不允许。
2.  **硬件虚拟化允许使用硬件扩展（如增强联网和 GPU 处理），但半虚拟化不允许。**
3.  硬件虚拟化仅适用于特定实例类型，而半虚拟化适用于所有实例类型。
4.  半虚拟化和硬件虚拟化的运作方式完全相同；两者在性能方面没有优劣之分。

## 48. 哪种 EBS 卷类型最适合执行 OLTP 且需要极高且一致性能的工作负载？

1.  **Provisioned IOPS volumes**
2.  General SSH volumes
3.  Magnetic storage
4.  Throughput Optimized HDD

## 49. 发现 HTTPS 未被允许通过安全组到达实例后，你添加了一条规则以允许 HTTPS 入站。更改需要多久才能在受影响的实例上生效？

1.  **Immediately**
2.  Approximately 30 seconds
3.  Approximately 1 minute
4.  实例立即生效，但如果实例前面有 ELB 则需要更长时间

## 50. 你发现生产数据库实例在夜间脚本运行时 CPU 使用率峰值达到 90%。脚本执行复杂查询并收集报表数据，次日通过邮件分发。由于负载过高，数据库性能下降，查询延续到下一个工作日才能完成。你会推荐哪种方案来降低晚间的峰值使用率？

1.  增加附加到数据库实例的内存。
2.  设置第二个数据库实例作为 Multi-AZ 数据库，并针对 Multi-AZ 数据库运行查询。
3.  **设置数据库实例的只读副本，并针对只读副本运行查询。**
4.  在数据库实例前设置 ElastiCache 实例。

## 51. 谁可以删除启用了版本控制的 S3 存储桶中的对象？

1.  任何拥有修改存储桶 IAM 权限的人
2.  **任何拥有删除存储桶中对象 IAM 权限的人**
3.  仅存储桶所有者
4.  一旦启用版本控制，对象永远无法被完全移除。

## 52. 客户要求对应用程序中所有静态对象进行加密。客户经常接受审计，必须证明符合一组特定的政府政策。你会推荐哪种加密方法？

1.  SSE-C
2.  **SSE-KMS**
3.  SSE-S3
4.  客户提供的加密密钥

## 53. 你为主数据库实例设置了三个只读副本。你发现副本的读取并不总是返回一致的结果，尤其是在对主数据库实例进行大量写入后。可能的原因是什么？

1.  这是正常的；从主实例复制到只读副本总是需要 30 到 60 秒。
2.  **这是正常的；从主实例复制到只读副本是异步的，虽然有时几乎是即时的，但有时也可能需要更长时间才能完成。**
3.  你需要将只读副本上的复制模型从异步切换为同步，以确保读取一致性。
4.  你需要调查主实例和只读副本之间的网络延迟，并考虑将副本移至与主实例相同的可用区。

## 54. 默认情况下，单个 AWS 账户可以创建多少个 S3 存储桶？

1.  20
2.  50
3.  100
4.  **There is no default limit.**

## 55. 你想在自定义 VPC 中创建公有子网。以下哪项**不是**实现此目的所必需的？

1.  An internet gateway
2.  **An elastic IP address**
3.  A routing table with a route to an internet gateway
4.  公有子网需要以上所有项目。

## 56. Provisioned IOPS EBS 卷允许的最大卷大小是多少？

1.  4TiB
2.  12TiB
3.  **16TiB**
4.  32TiB

## 57. 关于 EBS 卷和 EC2 实例，以下哪项陈述**不正确**？

1.  **You can attach multiple EC2 instances to a single EBS volume at one time.**
2.  You can attach multiple EBS volumes to a single EC2 instance at one time.
3.  You can attach multiple EC2 instances to a single EBS volume, but not all at the same time.
4.  Non-root EBS volumes are not deleted when an attached instance is terminated by default.

## 58. 以下哪项 AWS 服务**不**以键值对形式存储数据？

1.  S3
2.  DynamoDB
3.  IAM programmatic credentials
4.  **RDS**

## 59. 你正在审计运行三个面向 Web 的数据密集型应用程序的多个 EC2 实例的 EBS 卷。你注意到许多卷被配置为吞吐量优化 HDD，而非 General Purpose SSD 或 Provisioned IOPS SSD。为何此决策可能是合适的？（选择两项。）

1.  **降低成本是主要考量因素。**
2.  **数据吞吐量是主要考量因素。**
3.  应用程序主要使用大型性能关键型工作负载。
4.  吞吐量优化 HDD 仅服务于测试环境而非生产环境。

## 60. 以下哪种数据库**不**受 RDS 支持？

1.  MariaDB
2.  SQL Server
3.  Aurora
4.  **InnoDB**

## 61. 关于标准 AWS 账户创建的默认子网，以下哪些陈述是正确的？（选择两项。）

1.  **在其中创建的实例默认将是公有的。**
2.  在其中创建的实例默认将拥有公有弹性 IP。
3.  **在其中创建的实例默认将通过 Internet gateway 拥有通往 Internet 的路由。**
4.  创建该子网的 VPC 将同时附加 Virtual private gateway 和 Internet gateway。

## 62. 经典负载均衡器支持以下哪些类型的流量？（选择两项。）

1.  **HTTPS**
2.  SSH
3.  FTP
4.  **HTTP**

## 63. 哪种 S3 存储类的持久性与可用性相同？

1.  S3 standard
2.  S3-IA
3.  **S3-RRS**
4.  S3 One Zone-IA

## 64. 你想确保 S3 中的对象永远不会被意外删除，并保留已删除文件的审计追踪。你会考虑哪些选项？（选择两项。）

1.  SSE-KMS
2.  **MFA Delete**
3.  **Versioning**
4.  使用 CloudWatch 进行详细监控

