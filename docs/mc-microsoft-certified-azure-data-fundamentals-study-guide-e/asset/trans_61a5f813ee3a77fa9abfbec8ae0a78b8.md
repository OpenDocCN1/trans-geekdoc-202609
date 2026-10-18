

## 4. 文档可以轻松分布到多个存储设备上。

## 33. 你正在设计一个数据存储解决方案，用于存储电子商务网站上进行的交易。这些交易的架构非常流动，通常每个交易都不同。还有一个要求是数据库能够全球扩展，其中一些复制区域可以进行写入。以下哪项是最合适的？

1. Azure SQL 数据库
2. Azure Cosmos DB API for MongoDB
3. Azure Cosmos DB Cassandra API
4. Azure Cosmos DB Core (SQL) API

## 34. 以下哪项是 Azure 表存储与 Azure Cosmos DB 表 API 之间的区别？

1. Azure 表存储中的实体维护定义的架构，而 Azure Cosmos DB 表 API 中的实体具有灵活的架构。
2. Azure 表存储提供单区域复制，而 Azure Cosmos DB 表 API 提供多区域复制。
3. 与 Azure 表存储交互时，查询只能对键进行搜索，而 Azure Cosmos DB 表 API 允许查询对键和值进行搜索。
4. Azure 表存储中实体的最大大小为 2 MB，而 Azure Cosmos DB 表 API 中实体的最大大小为 4 MB。

## 35. 用于表示读取和写入存储在 Azure Cosmos DB 中的数据所需吞吐量的计量单位是什么？

1. 数据库事务单位 (DTUs)
2. 请求单位 (RUs)
3. 吞吐量单位 (TUs)
4. Cosmos DB 事务单位 (CDTUs)

## 36. Azure Cosmos DB 帐户生成哪种类型的密钥以提供对其资源的访问？创建了多少个？

1. 一个读写密钥和一个只读密钥
2. 两个读写密钥和一个只读密钥
3. 一个读写密钥和两个只读密钥
4. 两个读写密钥和两个只读密钥

## 37. 哪种一致性级别保证所有读取都将返回文档的最新版本，但可能会导致写入性能变慢，因为在提交事务时应用程序连接会暂停？

1. 会话
2. 有限延迟
3. 强一致性
4. 最终一致性

## 38. 用于将 Azure Cosmos DB 数据分布到存储中的字段名称是什么？

1. 分区键
2. 分布键
3. 主键
4. 外键

## 39. 你被要求通过将 Azure Cosmos DB 帐户与虚拟网络中的子网关联来对其进行隔离。以下哪项服务可用于将子网中的专用 IP 地址附加到帐户？

1. 专用终结点
2. 服务终结点
3. IP 终结点
4. 访问终结点

## 40. 作为公司的数据架构师，你被指派设计一个存储解决方案，该方案针对存储视频、图像、音频文件以及每个文件的关联元数据进行了优化。应该使用哪种类型的数据存储？

1. 图形
2. 文档
3. 对象
4. 列式

## 41. 以下哪种存储服务用于替换现有的本地文件共享，并可通过 SMB 或 NFS 协议访问？

1. Azure Blob 存储
2. Azure 文件
3. Azure Data Lake Storage Gen2
4. Azure Cosmos DB 文件 API

## 42. 以下哪种访问层可用于托管在标准 Azure 存储帐户上的文件共享？

1. 事务优化
2. 热
3. 冷
4. 以上全部

## 43. 什么对象用于在 Azure Blob 存储中组织数据？

1. 容器
2. 目录
3. Blob
4. 表

## 44. 哪种存储服务由于其数据结构方式及其与 Hadoop 分布式文件系统的集成，而经过优化可用于向大数据分析环境（如 Azure HDInsight、Azure Databricks 和 Azure Synapse Analytics）提供数据？

1. Azure Blob 存储
2. Azure 文件
3. Azure Data Lake Storage Gen2
4. Azure 表存储

## 45. 以下陈述中斜体部分是正确的，还是需要替换为下面出现的其他片段之一？`Azure Data Lake Storage Gen2` 为用户提供使用类似 POSIX 的访问控制列表来授予对存储对象和数据的细粒度访问的功能。

1. Azure Blob 存储
2. Azure 文件
3. Azure 表存储
4. 无需更改

## 46. 你正在设计一个用于存储日志文件的 Azure 存储解决方案。解决方案的要求之一是，数据必须复制到不同 Azure 区域中的辅助存储帐户，以防发生区域中断。应该在存储帐户上启用以下哪个选项？

1. 地理冗余存储 (GRS)
2. 地理区域冗余存储 (GZRS)
3. 区域冗余存储 (ZRS)
4. A 和 B 都是

## 47. 要托管两个 Blob 容器、一个文件共享和一个表，最少需要创建多少个存储帐户？

1. 一个
2. 两个
3. 三个
4. 四个

## 48. 以下哪个 Azure RBAC 角色将授予用户对 Azure Blob 存储容器的读取、写入和删除访问权限，但不会授予他们对容器的完全管理权限？

1. 存储 Blob 数据所有者
2. 存储 Blob 数据参与者
3. 存储 Blob 数据读取者
4. 存储 Blob 数据写入者

## 49. 以下陈述中斜体部分是正确的，还是需要替换为下面出现的其他片段之一？`AzCopy` 是一个独立的桌面应用程序，可用于创建和删除 Azure 存储资源，例如 Blob 容器和文件共享。用户还可以使用 `AzCopy` 上传、下载和删除 Azure 存储数据。

1. Azure 数据工厂
2. Azure 数据盒
3. Azure 存储资源管理器
4. 无需更改

## 50. 以下哪个开源框架可以与 Azure HDInsight 一起部署？

1. Apache Hadoop
2. Apache Storm
3. Apache Kafka
4. 以上全部

## 51. 以下陈述中斜体部分是正确的，还是需要替换为下面出现的其他片段之一？`Spark 驱动程序` 安装在 Spark 群集的每个工作节点上，用于执行作业任务。

1. Spark 会话
2. Spark 执行器
3. 群集管理器
4. 无需更改

## 52. 关于 Azure Databricks 的以下哪项陈述是正确的？

1. Azure Databricks 可用于批处理和流处理工作流。
2. Databricks 文件系统 (DBFS) 是 Azure Databricks 用于在 Databricks 群集终止后持久保存数据的内置分布式文件系统，以防数据丢失。
3. Azure Databricks 提供用于数据探索的交互式开发环境。
4. 以上全部。

## 53. Azure Databricks 群集的成本由哪两个组件组成？

1. Azure VM 和 Databricks 单位 (DBUs)
2. Azure Kubernetes 服务 (AKS) 和 Databricks 单位 (DBUs)
3. Azure 容器实例 (ACI) 和 Databricks 单位 (DBUs)
4. Azure Kubernetes 服务 (AKS) 和 Databricks 成本单位 (DCUs)

## 54. 你正在配置一个新的 Azure Databricks 群集，该群集将用于每晚的批处理作业。该群集将负责处理非常大的数据集，并且需要能够水平扩展以便在几小时内完成数据处理。以下哪种群集模式最适合此工作负载？

1. 高并发
2. 标准
3. 单节点
4. 计算

## 55. 以下哪项不是 Azure Synapse Analytics 提供的分析池类型？

1. 无服务器 SQL 池
2. 专用 SQL 池
3. Databricks 池

