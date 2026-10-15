
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

13. C, D.  Elastic Block Store 为 Lightsail、Beanstalk（以及 EC2）提供存储卷。EC2 提供应用部署功能，但并未被认为是简单的。

14. A. Beanstalk、EC2（非预留实例）和 RDS 都根据实际使用量计费。

15. B, D. Ubuntu 是操作系统，不是堆栈；WordPress 是应用，不是操作系统。

16. B, C. 实际情况下，Elastic Block Store 视为 EC2 资源；RDS 基本上基于其自身基础设施。

17. A, C. 理论上可以手动在 Lightsail 或 EC2 实例上安装 Docker Engine，但这并非它们的主要功能。

18. A, B. Lambda 和 Lightsail 都是计算服务，虽然它们可能在内部使用容器，但本身并不是容器技术。

19. D. Python 是有效的 Lambda 函数运行环境之一，没有一种“主导”语言用于 Lambda API 调用。

20. A. 最大执行时间此前为 5 分钟，现已改为 15 分钟。

Chapter 8: The Core Storage Services

1. B. 桶（bucket）名称必须在 AWS 全局范围内唯一，与 Region 无关。桶名称长度不受限制（3 到 63 个字符之间）。存储类是按对象配置的，不影响桶命名。

2. A, C. STANDARD_IA 和 GLACIER 存储类提供最高级别的冗余，并至少跨三个可用区复制。由于可用性较低（分别为 99.9% 和 99.5%），它们是 infrequent access 数据的最具性价比的选择。ONEZONE_IA 仅在单个可用区存储对象，该可用区失效可能导致所有对象丢失。STANDARD 和 INTELLIGENT_TIERING 提供最高耐久性和跨区域复制，但在这类场景下成本效益较低。

3. A, D. S3 是对象存储服务，而 EBS 是块存储服务，用于存储卷。EBS 快照存储在 S3 中。S3 不存储卷，EBS 不存储对象。

4. A, B, D. 对象生命周期配置可以基于对象年龄执行转换或过期操作。转换操作可在存储类之间移动对象（例如从 STANDARD 到 GLACIER）。过期操作可删除对象及其版本。对象生命周期配置不能删除桶或移动对象到 EBS 卷。

5. A, B. 可以使用桶策略（bucket policies）或访问控制列表（ACLs）授予匿名用户对对象的访问权限。不能使用用户策略实现此目的，但可以用于授予 IAM 主体对对象的访问权限。安全组控制 VPC 中资源的访问，不用于控制 S3 中的对象访问。

6. C, D. S3 和 Glacier 都设计用于耐久、长期存储，并提供相同的耐久性级别。Glacier 中的数据可通过 Expedited 或 Standard 检索选项在 8 小时内可靠恢复。S3 的数据可比 Glacier 更快检索。S3 可存储最高 5 TB 的对象，Glacier 可存储最高 40 TB 的归档。两者均满足需求，但 Glacier 更具成本效益。

7. B. 可以在 Glacier 控制台创建或删除存储库（vault）。不能上传、下载或删除归档；要执行归档操作，必须使用 AWS CLI、AWS SDK 或第三方程序。Glacier 不使用桶。

8. D. Standard 检索通常需要 3 到 5 小时完成。Expedited 只需 1 到 5 分钟，Bulk 需要 5 到 12 小时。没有 Provisioned 检索选项，但可以购买预留容量以确保 Expedited 检索及时完成。

9. A. Glacier 归档最小可为 1 字节，最大可达 40 TB。零字节归档不可建立。

10. B, D. 传输网关（tape gateway）和卷网关（volume gateway）类型支持 iSCSI 存储连接。文件网关（file gateway）支持 NFS。不存在缓存网关。

11. B. 所有 AWS Storage Gateway 类型（文件、卷、传输）主要将数据存储在 S3 桶中。随后数据可存储在 Glacier 或 EBS 快照中，后者可作为 EBS 卷实例化。

12. A, B, D, E. AWS Storage Gateway 使用行业标准存储协议将本地服务器文件传输到 S3。作为文件网关，它支持 SMB 和 NFS 协议；作为卷网关，它支持 iSCSI 协议。AWS Snowball 和 AWS CLI 也可传输数据到 S3，但需要安装第三方软件。

13. A, C, E. 卷网关有两种配置：存储卷和缓存卷。存储卷本地存储所有数据，并异步备份到 S3 为 EBS 快照。存储卷最大可达 16 TB。缓存卷仅本地保存 frequently used 的子集，不异步备份到 S3 为 EBS 快照。缓存卷最大可达 32 TB。

14. C. 80 TB Snowball 设备提供 72 TB 可用存储，是最大的可选规格。50 TB Snowball 提供 42 TB 可用空间。

15. A, B. AWS Snowball 在静止和传输过程中强制加密，并使用 TPM 芯片检测硬件或软件未经授权的变更。它不使用 NFS 加密，也不具备防窃网络端口。

