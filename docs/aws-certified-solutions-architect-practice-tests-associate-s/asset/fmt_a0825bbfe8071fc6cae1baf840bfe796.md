
# AWS 认证考题

## 存储服务

### EFS

### DynamoDB

## 缓存服务

### 181. Which of the following is a caching engine?

1.  ElastiCache
2.  DynamoDB
3.  memcached
4.  IAM

### 182. Which of the following are caching engines used by ElastiCache? (Choose two.)

1.  Redis
2.  DynamoDB
3.  memcached
4.  CloudFront

## 预留实例

### 183. Which of the following can you use reserved instances with?

1.  RDS
2.  EC2
3.  Both A and B
4.  None of the above

### 184. For which of the following can you use reserved instances?

1.  RDS Multi-AZ deployments
2.  RDS standard deployments
3.  ElastiCache nodes
4.  All of the above

## RDS 多可用区部署

### 185. In which situations will an RDS instance with Multi-AZ configured fail over? (Choose two.)

1.  When you manually force a failover
2.  When the primary zone is unreachable
3.  When the secondary zone is unreachable
4.  When two successive database reads fail

### 186. Which of the following can you select when you create an RDS instance? (Choose two.)

1.  The type of database to use
2.  The number of network connections to allow before failing over
3.  The number of database processes to allow
4.  The availability zone to deploy the instance to

### 187. Which of the following may happen when you have a single-AZ RDS database and a backup begins? (Choose two.)

1.  Latency increases
2.  Database responses may temporarily slow
3.  The database goes offline temporarily
4.  Network requests will fail for up to a minute

## RDS 数据库引擎

### 188. Which of the following database engines are available for RDS? (Choose two.)

1.  Hyperion
2.  Cassandra
3.  Oracle
4.  SQL Server

### 189. Which of the following is true about RDS? (Choose two.)

1.  Reserved instances can be used for Multi-AZ deployments
2.  Automated backups are turned off by default
3.  Every database supported by RDS can also be installed directly on EC2 instances
4.  All RDS databases support SQL as an interface

### 190. What is the default port for MySQL via RDS?

1.  80
2.  443
3.  22
4.  3306

## OLAP 与 OLTP

### 191. When AWS uses the term *OLAP*, what does that acronym stand for?

1.  Online analytics processing
2.  Offline analytic processing
3.  Online aggregation processing
4.  Offline activity and payment

### 192. When AWS uses the term OLTP, what does that acronym stand for?

1.  Offline training and practice
2.  Offline transaction processing
3.  Online traffic provisioning
4.  Online transaction processing

### 193. Which of the following is most suitable for OLAP?

1.  Redshift
2.  ElastiCache
3.  DynamoDB
4.  Aurora

### 194. Which of the following is most suitable for OLTP?

1.  Redshift
2.  ElastiCache
3.  DynamoDB
4.  Aurora

### 195. Which of the following are most suitable for OLTP? (Choose two.)

1.  memcached
2.  Oracle
3.  DynamoDB
4.  SQL Server

### 196. Which of the following is best suited for data warehousing?

1.  redis
2.  Oracle
3.  DynamoDB
4.  Redshift

### 197. Which of the following is best suited for big data processing?

1.  EMR
2.  QuickSight
3.  ElastiCache
4.  Athena

### 198. Which of the following is best suited for real-time analytics?

1.  EMR
2.  QuickSight
3.  Kinesis
4.  Athena

### 199. Which of the following is best suited for dashboards and visualizations?

1.  EMR
2.  QuickSight
3.  Kinesis
4.  Athena

### 200. Which of the following is best suited for interactive analytics?

1.  EMR
2.  QuickSight
3.  Kinesis
4.  Athena

## Amazon EMR

### 201. What are the most common frameworks used with Amazon EMR? (Choose two.)

1.  Scala
2.  Hadoop
3.  Java
4.  Spark

## Amazon Aurora

### 202. How many copies of data does Aurora store by default?

1.  One
2.  Three
3.  Four
4.  Six

### 203. Across how many availability zones does Aurora store your data by default?

1.  One
2.  Three
3.  Four
4.  Two

### 204. In an RDS, managed service capacity, which of the following databases is generally fastest?

1.  PostgreSQL
2.  MySQL
3.  Aurora
4.  They are all equivalent

### 205. In an RDS, managed service capacity, which of the following databases is most resistant to disaster by default?

1.  Aurora
2.  Oracle
3.  MySQL
4.  They are all equivalent

### 206. Which of the following databases can Aurora interact with seamlessly? (Choose two.)

1.  DynamoDB
2.  PostgreSQL
3.  MySQL
4.  HyperionDB

## RDS 访问与备份

### 207. Which of the following is allowed on your RDS instance? (Choose two.)

1.  SSH
2.  SQL queries
3.  RDP
4.  HTTP-accessible APIs

### 208. What is the maximum backup retention period allowed by RDS, in days?

1.  15 days
2.  30 days
3.  35 days
4.  45 days

### 209. If you install Oracle on an EC2 instance, what should you use for storage for that database?

1.  EBS
2.  S3
3.  EFS
4.  RDS

## OLTP 适用性

### 210. Which of the following are suitable for OLTP? (Choose two.)

1.  EBS
2.  Aurora
3.  DynamoDB
4.  MariaDB

### 211. Which of the following are not suitable for OLTP? (Choose two.)

1.  Kinesis
2.  PostgreSQL
3.  Redshift
4.  SQL Server

## Multi-AZ 与读取副本对比

### 212. Which of the following does a Multi-AZ RDS setup address? (Choose two.)

1.  Disaster recovery
2.  Read performance
3.  Data redundancy
4.  Network latency

### 213. Which of the following does a read replica RDS setup address? (Choose two.)

1.  Disaster recovery
2.  Read performance
3.  Offline backup
4.  Network latency

### 214. Which of the following does a read replica support? (Choose two.)

1.  Reads from applications
2.  Writes to applications
3.  Writes from the primary instance
4.  Writes from applications using the RDS API

### 215. Which of the following does a Multi-AZ setup not provide?

1.  Disaster recovery
2.  Data redundancy
3.  Improved performance
4.  Access to all RDS databases

### 216. Which of the following does a Multi-AZ setup provide?

1.  Decreased network latency
2.  Synchronous replication
3.  Asynchronous replication
4.  Multiple read sources for applications

### 217. Which of the following does a read replica provide?

1.  Increased network latency
2.  Synchronous replication
3.  Disaster recovery
4.  Asynchronous replication

### 218. Which of the following is associated with read replicas?

1.  High scalability
2.  Primary and secondary instances
3.  High durability
4.  Automatic failover

### 219. Which of the following is associated with Multi-AZ RDS?

1.  Manual backup configuration
2.  Independent database upgrades
3.  High durability
4.  More than two database instances

### 220. How many read replicas are supported in a read replica setup?

1.  Three
2.  Five
3.  Seven
4.  Unlimited (although cost applies for each replica)

### 221. Which of the following databases do not support a read replica setup? (Choose two.)

1.  DynamoDB
2.  Redshift
3.  MySQL
4.  MariaDB

## DynamoDB 特性

### 222. Which of the following statements about DynamoDB are true? (Choose two.)

1.  DynamoDB offers push-button scaling
2.  DynamoDB supports read replicas
3.  DynamoDB databases can scale up without needing a bigger underlying instance
4.  DynamoDB instance sizes are selected at runtime

### 223. Which of the following statements about DynamoDB are true? (Choose two.)
