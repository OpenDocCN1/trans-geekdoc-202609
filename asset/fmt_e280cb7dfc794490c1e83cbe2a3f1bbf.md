
15. C. 传输中加密要求数据在远程客户端加密后再上传。服务器端加密（SSE-S3 或 SSE-KMS）仅在 S3 桶内加密数据。DynamoDB 是一种 NoSQL 数据库服务。

16. A. 只能在创建 EBS 卷时加密，不能在创建后进行加密。

17. D. 客户端主密钥用于在到达 AWS（特别是 S3）之前加密对象。不存在常见的称为 SSH 或 KMS 主密钥的名称。

18. C. SSE-KMS 是 KMS 管理的服务器端密钥。FedRAMP 是美国政府的联邦风险与授权管理计划（在其中，事务数据保护仅起到相对次要的作用）。ARPA 是澳大利亚审慎监管局。

19. B. SOC 并非主要提供指导或风险评估，并且绝不是对您自身部署状态的保证。SOC 报告是对 AWS 基础设施的审计报告，您可以将其作为自身报告需求的一部分。

20. A, B. AWS Artifact 文档是关于 AWS 基础设施符合外部标准的合规性文档。它们可以间接提供最佳实践的洞察。它们并不代表 AWS 的内部设计或策略。

## Chapter 6: Working with Your AWS Resources

1. D. 您可以以 root 用户或 IAM 用户身份登录。虽然需要指定账户别名或账户 ID 来以 IAM 用户身份登录，但这些不是凭证。您无法使用访问密钥 ID 登录控制台。

2. B. 一旦登录，您的会话将保持活动 12 小时。之后会过期并退出，以保护您的账户。

3. A. 如果本应可见的资源看起来缺失，可能是选择了错误的区域。由于您以 root 身份登录，您拥有账户中所有资源的访问权限。您无需访问密钥即可使用控制台。您无法在导航栏中选择可用性区。

4. C. 您创建的每个资源标签必须拥有一个键，但值是可选的。标签在账户内不需要唯一，并且区分大小写。

5. A. AWS CLI 需要访问密钥 ID 和密钥密钥。您可以使用 IAM 用户或 root 用户的凭证。出站网络访问 TCP 443 端口是必需的，而不是 80 端口。Linux 不是必需的，但您可以在 Linux、macOS 或 Windows 上使用 AWS CLI。您还可以使用 Android 或 iOS 设备的 AWS 控制台移动应用。

6. A, D. 您可以使用 Python 和 pip 包管理器，或（除 Windows Server 2008 外）使用 MSI 安装程序在 Windows 上安装 AWS CLI。AWS SDKs 不包含 AWS CLI。Yum 和 Aptitude 仅为 Linux 服务。

7. B. `aws configure` 命令会引导您设置 AWS CLI 的默认区域以及访问密钥 ID 和密钥密钥。`aws --version` 命令显示已安装的 AWS CLI 版本，但运行该命令不是使用 AWS CLI 管理资源的必要步骤。重启也不是必要的。使用 root 用户管理 AWS 资源是不安全的，因此无需为 root 用户生成新的访问密钥 ID。

8. C. AWS CLI 可以以 JSON、文本或表格格式显示输出。它不支持 CSV 或 TSV。

9. B, D, E. AWS 为 JavaScript、Java 和 PHP 提供 SDK。Fortran 没有 SDK。JSON 是表示数据的格式，而非编程语言。

10. A, B. AWS Mobile SDK for Unity 以及 AWS Mobile SDK for .NET 和 Xamarin 可让您为 Android 和 Apple iOS 设备创建移动应用。AWS SDK for Go 不支持移动应用开发。AWS Mobile SDK for iOS 支持 Apple iOS 设备开发，但不支持 Android。

11. A, B. AWS IoT 设备 SDK 可用于 C++、Python、Java、JavaScript 和 Embedded C。Ruby 或 Swift 没有对应的 SDK。

12. A, D. AWS CLI 是一个运行在 Linux、macOS 或 Windows 上的程序，允许您通过终端与 AWS 服务交互。AWS SDKs 让您使用喜欢的编程语言编写与 AWS 服务交互的应用。

13. B. CloudWatch 指标存储 AWS 服务的性能数据。日志存储来自应用程序和 AWS 服务的文本日志。事件是针对 AWS 资源发生的操作。警报监控指标。指标过滤器从日志中提取指标信息。

14. D. CloudWatch 警报监控指标并在该指标超过指定阈值时触发。如果指标没有变化，警报不会触发。终止 EC2 实例是一个事件，您无法创建基于事件的 CloudWatch 警报。您也无法创建基于 Web 服务器日志中 IP 地址存在的警报。但您可以创建指标过滤器，在日志中查找特定 IP 地址并为其出现时递增自定义指标。

15. A, C. SNS 支持 SMS 和 SQS 协议用于发送通知。您无法向 CloudWatch 事件发送通知。不存在移动拉取通知。

16. C, D. CloudWatch Events 监控导致 AWS 资源状态变化的事件以及 AWS 控制台登录事件。在响应事件时，CloudWatch Events 可以执行操作，包括向 SNS 发送通知或重启 EC2 实例。它还可以按计划执行操作。它不监控日志或指标。

17. B, D. 查看 AWS 资源会触发 API 操作，无论是通过控制台还是 CLI 进行。配置 AWS CLI 不会触发任何 API 操作。登录 AWS 控制台也不会触发 API 操作。

18. A. CloudTrail 事件历史记录日志保存每个区域的管理事件的最近 90 天。创建跟踪是过度设计且不具成本效益，因为它会将日志存储在 S3 桶中。将 CloudTrail 日志流式传输到 CloudWatch 需要创建跟踪。CloudWatch Events 不记录管理事件。

19. A, D. 在包含桶的区域创建跟踪将生成 CloudTrail 日志，您可以将其流式传输到 CloudWatch 进行查看和搜索。CloudTrail 事件历史记录不记录数据事件。CloudTrail 默认记录全球服务事件，但 S3 数据事件未包含。

20. B. 日志完整性验证使用加密哈希帮助您断言 CloudTrail 日志文件未被从 S3 删除。它不防止篡改或删除，也无法告知文件如何被篡改。日志完整性验证与 CloudWatch 无关。

21. D. 成本和使用情况报告显示您按服务的月度支出。保留实例报告和保留实例建议不显示实际月度成本。

22. A. RDS 允许您购买保留实例以节省费用。Lambda、S3 和 Fargate 不使用实例。

23. B. 保留实例使用率报告显示您通过保留实例节省了多少成本。保留实例覆盖率报告显示如果您购买保留实例，本可以节省多少成本。每日成本和每月 EC2 运行时长成本与使用情况报告不知道您通过保留实例节省了多少成本。

24. D. Cost Explorer 会为 EC2、RDS、ElastiCache、Redshift 和 Elasticsearch 实例提供保留实例建议。您需要选择要分析的服务。但 Cost Explorer 不会为已被保留实例覆盖的实例提供建议。由于您的 Elasticsearch 实例已连续运行至少七天，该使用情况将被分析。

## Chapter 7: The Core Compute Services

1. C. 实例的硬件配置由实例类型定义。高吞吐（或低吞吐）数据处理操作和数据流可以使用任何存储卷或任何实例（尽管某些可能更适合特定场景）。

2. A. 快速启动（Quick Start）仅包含数十个最流行的 AMI。Community 标签包含数千个公开可用的 AMI（无论是否经过验证）。My AMIs 标签仅包含您账户中创建的 AMI。

3. B, C. 可以创建包含基础操作系统和预装应用的 AMI，但不会包含任何网络或硬件配置信息——这些信息主要取决于实例类型。

4. B, D. `c5d.18xlarge` 和 `t2.micro` 是 EC2 实例类型的名称，而不是实例类型族。

5. D. 虚拟中央处理单元（vCPU）是衡量实例类型计算能力的指标，大致对应物理服务器上的处理器数量。它与高流量容错性、系统内存或底层 AMI 无关。

6. A. 由单个 AWS 账户专用并受其控制的物理主机上运行的 EC2 实例称为专用主机（dedicated host）。专用主机既不是 AMI，也不是实例类型。

7. C. 与物理存储驱动器直接关联且虚拟化的存储分区称为实例存储卷（instance store volume）。用于轻松复制和部署到 EC2 实例的软件堆栈包描述的是 EC2 AMI。可以加密 EBS 卷，但加密并不定义它们。

8. C, D. 实例存储卷无法加密，且其数据在实例关闭后不会保留。这些是 EBS 卷的特性。

9. B. 对于此类用途，Spot 实例不可靠，因为它们可能会意外关闭。预留实例在长时间、24/7 使用时更具经济性。“专用”并不是一种计价模型。

10. D. 由于您的“基础”实例需要长期、24/7 运行，预留实例适用。Spot 实例和 Spot 集群实例不可靠，因为可能会被意外关闭。按需实例在如此长的周期内成本过高。

11. A. 由于 AWS 极少会出现容量不足的情况，无需保证可用容量。您可自行选择预留实例的付费方式。所有 All Upfront、Partial Upfront 和 No Upfront 选项均可用，且没有自动计费。在此情境下，实例不会自动启动。

12. A, C. 由于 Spot 实例可能被关闭，因此不建议用于提供任何 always‑on 服务的应用。

13. C, D. Elastic Block Store 为 Lightsail、Beanstalk（以及 EC2）提供存储卷。EC2 提供应用部署功能，但并未被认为是简单的。

14. A. Beanstalk、EC2（非预留实例）和 RDS 都根据实际使用量计费。

15. B, D. Ubuntu 是操作系统，不是堆栈；WordPress 是应用，不是操作系统。

16. B, C. 实际情况下，Elastic Block Store 视为 EC2 资源；RDS 基本上基于其自身基础设施。

17. A, C. 理论上可以手动在 Lightsail 或 EC2 实例上安装 Docker Engine，但这并非它们的主要功能。

18. A, B. Lambda 和 Lightsail 都是计算服务，虽然它们可能在内部使用容器，但本身并不是容器技术。

19. D. Python 是有效的 Lambda 函数运行环境之一，没有一种“主导”语言用于 Lambda API 调用。

20. A. 最大执行时间此前为 5 分钟，现已改为 15 分钟。

## Chapter 8: The Core Storage Services

1. B. 桶（bucket）名称必须在 AWS 全局范围内唯一，与 Region 无关。桶名称长度不受限制（3 到 63 个字符之间）。存储类是按对象配置的，不影响桶命名。

2. A, C. STANDARD_IA 和 GLACIER 存储类提供最高级别的冗余，并至少跨三个可用区复制。由于可用性较低（分别为 99.9% 和 99.5%），它们是 infrequent access 数据的最具性价比的选择。ONEZONE_IA 仅在单个可用区存储对象，该可用区失效可能导致所有对象丢失。STANDARD 和 INTELLIGENT_TIERING 提供最高耐久性和跨区域复制，但在这类场景下成本效益较低。

3. A, D. S3 是对象存储服务，而 EBS 是块存储服务，用于存储卷。EBS 快照存储在 S3 中。S3 不存储卷，EBS 不存储对象。

4. A, B, D. 对象生命周期配置可以基于对象年龄执行转换或过期操作。转换操作可在存储类之间移动对象（例如从 STANDARD 到 GLACIER）。过期操作可删除对象及其版本。对象生命周期配置不能删除桶或移动对象到 EBS 卷。

5. A, B. 可以使用桶策略（bucket policies）或访问控制列表（ACLs）授予匿名用户对对象的访问权限。不能使用用户策略实现此目的，但可以用于授予 IAM 主体对对象的访问权限。安全组控制 VPC 中资源的访问，不用于控制 S3 中的对象访问。

6. C, D. S3 和 Glacier 都设计用于耐久、长期存储，并提供相同的耐久性级别。Glacier 中的数据可通过 Expedited 或 Standard 检索选项在 8 小时内可靠恢复。S3 的数据可比 Glacier 更快检索。S3 可存储最高 5 TB 的对象，Glacier 可存储最高 40 TB 的归档。两者均满足需求，但 Glacier 更具成本效益。

7. B. 可以在 Glacier 控制台创建或删除存储库（vault）。不能上传、下载或删除归档；要执行归档操作，必须使用 AWS CLI、AWS SDK 或第三方程序。Glacier 不使用桶。

8. D. Standard 检索通常需要 3 到 5 小时完成。Expedited 只需 1 到 5 分钟，Bulk 需要 5 到 12 小时。没有 Provisioned 检索选项，但可以购买预留容量以确保 Expedited 检索及时完成。

9. A. Glacier 归档最小可为 1 字节，最大可达 40 TB。零字节归档不可建立。

10. B, D. 传输网关（tape gateway）和卷网关（volume gateway）类型支持 iSCSI 存储连接。文件网关（file gateway）支持 NFS。不存在缓存网关。

11. B. 所有 AWS Storage Gateway 类型（文件、卷、传输）主要将数据存储在 S3 桶中。随后数据可存储在 Glacier 或 EBS 快照中，后者可作为 EBS 卷实例化。

12. A, B, D, E. AWS Storage Gateway 使用行业标准存储协议将本地服务器文件传输到 S3。作为文件网关，它支持 SMB 和 NFS 协议；作为卷网关，它支持 iSCSI 协议。AWS Snowball 和 AWS CLI 也可传输数据到 S3，但需要安装第三方软件。

13. A, C, E. 卷网关有两种配置：存储卷和缓存卷。存储卷本地存储所有数据，并异步备份到 S3 为 EBS 快照。存储卷最大可达 16 TB。缓存卷仅本地保存 frequently used 的子集，不异步备份到 S3 为 EBS 快照。缓存卷最大可达 32 TB。

14. C. 80 TB Snowball 设备提供 72 TB 可用存储，是最大的可选规格。50 TB Snowball 提供 42 TB 可用空间。

15. A, B. AWS Snowball 在静止和传输过程中强制加密，并使用 TPM 芯片检测硬件或软件未经授权的变更。它不使用 NFS 加密，也不具备防窃网络端口。

16. C. 如果 AWS 检测到任何篡改或损坏的迹象，它将不会更换 TPM 芯片或从设备中转移客户数据。相反，AWS 会安全地擦除它。

17. B. Snowball Client 让你可以使用运行 Windows、Linux 或 macOS 的机器将文件传输到或从 Snowball 中传输。它不需要编程知识，但 Snowball 的 S3 SDK Adapter 需要。Snowball 不支持 NFS、iSCSI 或 SMB 存储协议。

18. A, D. Snowball Edge 提供计算能力来运行 EC2 实例，并支持使用 NFSv3 和 NFSv4 协议复制文件。Snowball 设备不能集群，也没有 QFSP+ 端口。

19. B. Snowball Edge—Compute Optimized with GPU 选项针对机器学习和高性能计算应用进行优化。尽管 Compute Optimized 和 Storage Optimized 选项也可以工作，但它们不是最佳选择。不存在 Network Optimized 选项。

20. B. Snowball Edge 与 Compute Optimized 配置包括 QSFP+ 网络接口，支持最高 100 Gbps。Storage Optimized 配置的 QSFP+ 端口仅支持最高 40 Gbps。80 TB Snowball 仅支持最高 10 Gbps。存储网关是虚拟机，不是硬件设备。

## Chapter 9: The Core Database Services

1. B. 关系型数据库以称为属性的列存储数据，以称为记录的行存储数据。非关系型数据库（包括键值存储和文档存储）以集合或项存储数据，但不使用列或行。

2. B. SQL INSERT 语句用于向关系型数据库添加数据。QUERY 命令用于读取数据。CREATE 可用于创建表，但不能向其添加数据。WRITE 不是有效的 SQL 命令。

3. D. 非关系型数据库是无架构的，意味着无需预先定义要在表中存储的所有数据类型。这并不妨碍你存储具有固定结构的数据，因为非关系型数据库可以存储几乎任何类型的数据。主键是唯一标识表中每个项的必要条件。可以创建多个表，但大多数使用非关系型数据库的应用程序只使用一张表。

4. C. No‑SQL 数据库是非关系型数据库的另一种说法。按定义，非关系型数据库是无架构的，必须使用主键。不存在“无架构的关系型数据库”。No‑SQL 永远不会用来描述任何种类的关系型数据库。

5. B. RDS 实例使用 EBS 卷进行存储。它们不再可以使用磁盘存储。实例卷用于临时存储，而非数据库存储。你可以对数据库实例取快照并将其还原到新实例并使用新的 EBS 卷，但 RDS 实例不能直接使用快照作为数据库存储。

6. B, D. PostgreSQL 和 Amazon Aurora 是 RDS 数据库引擎的选项。IBM dBase 和非关系型数据库 DynamoDB 和 Redis 不可用作 RDS 数据库引擎。

7. A, B. Aurora 是 Amazon 的专有数据库引擎，与现有 PostgreSQL 和 MySQL 数据库兼容。Aurora 不支持 MariaDB、Oracle 或 Microsoft SQL Server。
