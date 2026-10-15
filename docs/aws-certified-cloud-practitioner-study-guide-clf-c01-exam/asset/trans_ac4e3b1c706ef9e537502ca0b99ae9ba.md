
16. C. 如果 AWS 检测到任何篡改或损坏的迹象，它将不会更换 TPM 芯片或从设备中转移客户数据。相反，AWS 会安全地擦除它。

17. B. Snowball Client 让你可以使用运行 Windows、Linux 或 macOS 的机器将文件传输到或从 Snowball 中传输。它不需要编程知识，但 Snowball 的 S3 SDK Adapter 需要。Snowball 不支持 NFS、iSCSI 或 SMB 存储协议。

18. A, D. Snowball Edge 提供计算能力来运行 EC2 实例，并支持使用 NFSv3 和 NFSv4 协议复制文件。Snowball 设备不能集群，也没有 QFSP+ 端口。

19. B. Snowball Edge—Compute Optimized with GPU 选项针对机器学习和高性能计算应用进行优化。尽管 Compute Optimized 和 Storage Optimized 选项也可以工作，但它们不是最佳选择。不存在 Network Optimized 选项。

20. B. Snowball Edge 与 Compute Optimized 配置包括 QSFP+ 网络接口，支持最高 100 Gbps。Storage Optimized 配置的 QSFP+ 端口仅支持最高 40 Gbps。80 TB Snowball 仅支持最高 10 Gbps。存储网关是虚拟机，不是硬件设备。

Chapter 9: The Core Database Services

1. B. 关系型数据库以称为属性的列存储数据，以称为记录的行存储数据。非关系型数据库（包括键值存储和文档存储）以集合或项存储数据，但不使用列或行。

2. B. SQL INSERT 语句用于向关系型数据库添加数据。QUERY 命令用于读取数据。CREATE 可用于创建表，但不能向其添加数据。WRITE 不是有效的 SQL 命令。

3. D. 非关系型数据库是无架构的，意味着无需预先定义要在表中存储的所有数据类型。这并不妨碍你存储具有固定结构的数据，因为非关系型数据库可以存储几乎任何类型的数据。主键是唯一标识表中每个项的必要条件。可以创建多个表，但大多数使用非关系型数据库的应用程序只使用一张表。

4. C. No‑SQL 数据库是非关系型数据库的另一种说法。按定义，非关系型数据库是无架构的，必须使用主键。不存在“无架构的关系型数据库”。No‑SQL 永远不会用来描述任何种类的关系型数据库。

5. B. RDS 实例使用 EBS 卷进行存储。它们不再可以使用磁盘存储。实例卷用于临时存储，而非数据库存储。你可以对数据库实例取快照并将其还原到新实例并使用新的 EBS 卷，但 RDS 实例不能直接使用快照作为数据库存储。

6. B, D. PostgreSQL 和 Amazon Aurora 是 RDS 数据库引擎的选项。IBM dBase 和非关系型数据库 DynamoDB 和 Redis 不可用作 RDS 数据库引擎。

7. A, B. Aurora 是 Amazon 的专有数据库引擎，与现有 PostgreSQL 和 MySQL 数据库兼容。Aurora 不支持 MariaDB、Oracle 或 Microsoft SQL Server。

8. B, C. 多可用区 (Multi‑AZ) 和快照可在可用区故障时保护数据。读取副本不使用同步复制，可能会丢失部分数据。IOPS 是存储吞吐量的度量。垂直扩展指更改实例类型，与防止数据丢失无关。

9. B. Amazon Aurora 使用共享存储卷，该卷会自动扩展至最高 64 TB。Microsoft SQL Server 和 Oracle 数据库引擎不提供此功能。Amazon Athena 不是数据库引擎。

10. A. 多可用区 (Multi‑AZ) 让你的数据库即使在整个可用区失败的情况下也能抵御 RDS 实例的故障。读取副本是实现水平扩展以提高读取性能的方法，但不增加可用性。时间点恢复允许你将数据库还原到特定时间点，但同样不提升可用性。

11. B, D. 分区是由固态驱动器支持并跨多个可用区复制的存储分配。表存储在分区中，但表本身不包含分区。主键而非分区用于唯一标识表中的项。

12. A. DynamoDB 在单个 Region 中的最小月度可用性为 99.99 百分比。它不是 99.95 百分比、99.9 百分比或 99.0 百分比。

13. D. DynamoDB 表中的项可以拥有不同的属性。例如，一个项可以有五个属性，而另一个只有 1 个。表可以存储包含多种数据类型的项。无需预先定义表中的项数量。表中的项不能有重复的主键。

14. C, E. 增加 WCU（写容量单位）或启用自动扩展将提高对表的写入性能。增大或减小 RCU（读容量单位）不会提升写入性能。减小 WCU 会使写入性能恶化。

15. C. 扫描（Scan）需要读取表存储的所有分区。查询（Query）基于主键进行，使 DynamoDB 只读取包含匹配项的那一个分区。写入和更新项不是读取密集操作。

16. D. 主键在表中必须唯一。全名、电话号码或城市可能不唯一，因为不同客户可能共享相同的姓名或电话号码。随机生成的客户 ID 号是唯一且适合作为主键使用。

17. B. 密集计算节点使用磁盘，密集存储节点使用 SSD。不存在密集内存或成本优化节点。

18. A. Redshift Spectrum 可分析存储在 S3 中的结构化数据。不存在 Redshift S3 服务。Amazon Athena 可以分析 S3 中的结构化数据，但它不是 Redshift 的功能。Amazon RDS 不会分析存储在 S3 中的数据。

19. B. 数据仓库存储来自其他关系型数据库的大量结构化数据。它不叫数据存储库或报告集群。密集存储节点是 Redshift 计算节点的一种类型。

20. A. 密集存储节点可以在集群中使用，最多可存储 2 PB 的数据。密集计算节点可用于存储最高 326 TB 的数据。

Chapter 10: The Core Networking Services

1. B, D. 对于每个账户，AWS 在每个 Region 创建默认 VPC。VPC 跨越该 Region 内的所有可用区，但不跨越 Regions。

2. A. VPC 或子网 CIDR 的大小范围是 /16 到 /28（含），因此 10.0.0.0/28 是唯一有效的 CIDR。

3. B, C. 子网仅存在于单个可用区内，并且其 CIDR 必须是所在 VPC CIDR 的子集。VPC 不一定需要两个子网，但至少需要一个。

4. C. 创建安全组时，它包含一个默认的出站规则，允许访问任何 IP 地址。默认不包含入站规则。安全组规则只能允许访问，不能拒绝，因此未明确允许的流量会被拒绝。

5. B, D. 网络访问控制列表（NACL）是工作在子网层面的防火墙。安全组是工作在实例层面的防火墙。

6. B. VPC 对等连接是仅限于两个 VPC 之间的私有连接。它使用私有 AWS 网络，而非公共 Internet。VPC 对等连接不同于 VPN 连接。

7. A, B. Direct Connect 使用专用链路而非 Internet，提供确定性延迟。Direct Connect 不使用加密，但通过私有链路提供一定安全性。VPN 连接使用 Internet 进行传输，使用 AES 128 或 256 位加密。VPN 连接不需要专有硬件。
