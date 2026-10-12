

# AWS 认证考题

## 存储服务

### EFS

### DynamoDB

## 缓存服务

### 181. 以下哪项是缓存引擎？

1.  ElastiCache
2.  DynamoDB
3.  memcached
4.  IAM

### 182. 以下哪些是 ElastiCache 使用的缓存引擎？（选择两项。）

1.  Redis
2.  DynamoDB
3.  memcached
4.  CloudFront

## 预留实例

### 183. 以下哪项可以与预留实例一起使用？

1.  RDS
2.  EC2
3.  A 和 B 皆可
4.  以上皆非

### 184. 以下哪项可以使用预留实例？

1.  RDS 多可用区部署
2.  RDS 标准部署
3.  ElastiCache 节点
4.  以上皆是

## RDS 多可用区部署

### 185. 在以下哪种情况下，配置了多可用区的 RDS 实例会发生故障转移？（选择两项。）

1.  当你手动强制故障转移时
2.  当主可用区不可达时
3.  当备用可用区不可达时
4.  当连续两次数据库读取失败时

### 186. 创建 RDS 实例时，你可以选择以下哪些内容？（选择两项。）

1.  要使用的数据库类型
2.  故障转移前允许的网络连接数
3.  允许的数据库进程数
4.  部署实例的可用区

### 187. 当你拥有一个单可用区 RDS 数据库且备份开始时，可能会发生以下哪种情况？（选择两项。）

1.  延迟增加
2.  数据库响应可能暂时变慢
3.  数据库暂时离线
4.  网络请求将失败长达一分钟

## RDS 数据库引擎

### 188. 以下哪些数据库引擎可用于 RDS？（选择两项。）

1.  Hyperion
2.  Cassandra
3.  Oracle
4.  SQL Server

### 189. 关于 RDS，以下哪项描述是正确的？（选择两项。）

1.  预留实例可用于多可用区部署
2.  自动备份默认关闭
3.  RDS 支持的每种数据库也都可以直接安装在 EC2 实例上
4.  所有 RDS 数据库都支持 SQL 作为接口

### 190. 通过 RDS 使用 MySQL 的默认端口是多少？

1.  80
2.  443
3.  22
4.  3306

## OLAP 与 OLTP

### 191. 当 AWS 使用术语 *OLAP* 时，该首字母缩略词代表什么？

1.  Online analytics processing（在线分析处理）
2.  Offline analytic processing（离线分析处理）
3.  Online aggregation processing（在线聚合处理）
4.  Offline activity and payment（离线活动与支付）

### 192. 当 AWS 使用术语 OLTP 时，该首字母缩略词代表什么？

1.  Offline training and practice（离线培训与实践）
2.  Offline transaction processing（离线事务处理）
3.  Online traffic provisioning（在线流量配置）
4.  Online transaction processing（在线事务处理）

### 193. 以下哪项最适合 OLAP？

1.  Redshift
2.  ElastiCache
3.  DynamoDB
4.  Aurora

### 194. 以下哪项最适合 OLTP？

1.  Redshift
2.  ElastiCache
3.  DynamoDB
4.  Aurora

### 195. 以下哪些最适合 OLTP？（选择两项。）

1.  memcached
2.  Oracle
3.  DynamoDB
4.  SQL Server

### 196. 以下哪项最适合数据仓库？

1.  redis
2.  Oracle
3.  DynamoDB
4.  Redshift

### 197. 以下哪项最适合大数据处理？

1.  EMR
2.  QuickSight
3.  ElastiCache
4.  Athena

### 198. 以下哪项最适合实时分析？

1.  EMR
2.  QuickSight
3.  Kinesis
4.  Athena

### 199. 以下哪项最适合仪表板和可视化？

1.  EMR
2.  QuickSight
3.  Kinesis
4.  Athena

### 200. 以下哪项最适合交互式分析？

1.  EMR
2.  QuickSight
3.  Kinesis
4.  Athena

## Amazon EMR

### 201. 与 Amazon EMR 搭配使用最常见的框架有哪些？（选择两项。）

1.  Scala
2.  Hadoop
3.  Java
4.  Spark

## Amazon Aurora

### 202. Aurora 默认存储多少份数据副本？

1.  一份
2.  三份
3.  四份
4.  六份

### 203. Aurora 默认跨多少个可用区存储你的数据？

1.  一个
2.  三个
3.  四个
4.  两个

### 204. 在 RDS 托管服务容量下，以下哪种数据库通常速度最快？

1.  PostgreSQL
2.  MySQL
3.  Aurora
4.  它们都相当

### 205. 在 RDS 托管服务容量下，以下哪种数据库默认情况下最能抵御灾难？

1.  Aurora
2.  Oracle
3.  MySQL
4.  它们都相当

### 206. 以下哪些数据库可以与 Aurora 无缝交互？（选择两项。）

1.  DynamoDB
2.  PostgreSQL
3.  MySQL
4.  HyperionDB

## RDS 访问与备份

### 207. 以下哪项操作在你的 RDS 实例上是被允许的？（选择两项。）

1.  SSH
2.  SQL 查询
3.  RDP
4.  可通过 HTTP 访问的 API

### 208. RDS 允许的最大备份保留期是多少天？

1.  15 天
2.  30 天
3.  35 天
4.  45 天

### 209. 如果你在 EC2 实例上安装 Oracle，应该为该数据库使用什么存储？

1.  EBS
2.  S3
3.  EFS
4.  RDS

## OLTP 适用性

### 210. 以下哪些适合 OLTP？（选择两项。）

1.  EBS
2.  Aurora
3.  DynamoDB
4.  MariaDB

### 211. 以下哪些不适合 OLTP？（选择两项。）

1.  Kinesis
2.  PostgreSQL
3.  Redshift
4.  SQL Server

## Multi-AZ 与读取副本对比

### 212. 多可用区 RDS 设置解决了以下哪些问题？（选择两项。）

1.  灾难恢复
2.  读取性能
3.  数据冗余
4.  网络延迟

### 213. 读取副本 RDS 设置解决了以下哪些问题？（选择两项。）

1.  灾难恢复
2.  读取性能
3.  离线备份
4.  网络延迟

### 214. 读取副本支持以下哪些功能？（选择两项。）

1.  来自应用程序的读取
2.  面向应用程序的写入
3.  来自主实例的写入
4.  使用 RDS API 的来自应用程序的写入

### 215. 多可用区设置**不**提供以下哪项？

1.  灾难恢复
2.  数据冗余
3.  性能提升
4.  访问所有 RDS 数据库

### 216. 多可用区设置提供以下哪项？

1.  降低网络延迟
2.  同步复制
3.  异步复制
4.  面向应用程序的多个读取源

### 217. 读取副本提供以下哪项？

1.  增加网络延迟
2.  同步复制
3.  灾难恢复
4.  异步复制

### 218. 以下哪项与读取副本相关？

1.  高可扩展性
2.  主实例和备用实例
3.  高持久性
4.  自动故障转移

### 219. 以下哪项与多可用区 RDS 相关？

1.  手动备份配置
2.  独立的数据库升级
3.  高持久性
4.  两个以上的数据库实例

### 220. 读取副本设置支持多少个读取副本？

1.  三个
2.  五个
3.  七个
4.  无限制（尽管每个副本都会产生费用）

### 221. 以下哪些数据库不支持读取副本设置？（选择两项。）

1.  DynamoDB
2.  Redshift
3.  MySQL
4.  MariaDB

## DynamoDB 特性

### 222. 关于 DynamoDB，以下哪些陈述是正确的？（选择两项。）

1.  DynamoDB 提供一键式扩展
2.  DynamoDB 支持读取副本
3.  DynamoDB 数据库可以在不需要更大底层实例的情况下扩展
4.  DynamoDB 实例大小在运行时选择

### 223. 关于 DynamoDB，以下哪些陈述是正确的？（选择两项。）

