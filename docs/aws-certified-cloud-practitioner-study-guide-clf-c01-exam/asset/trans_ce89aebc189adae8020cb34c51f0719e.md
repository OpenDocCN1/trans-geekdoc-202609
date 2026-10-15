
18. C. SSE-KMS 是 KMS 管理的服务器端密钥。FedRAMP 是美国政府的联邦风险与授权管理计划（在其中，事务数据保护仅起到相对次要的作用）。ARPA 是澳大利亚审慎监管局。

19. B. SOC 并非主要提供指导或风险评估，并且绝不是对您自身部署状态的保证。SOC 报告是对 AWS 基础设施的审计报告，您可以将其作为自身报告需求的一部分。

20. A, B. AWS Artifact 文档是关于 AWS 基础设施符合外部标准的合规性文档。它们可以间接提供最佳实践的洞察。它们并不代表 AWS 的内部设计或策略。

## Chapter 6: Working with Your AWS Resources

1.  D. 您可以以 root 用户或 IAM 用户身份登录。虽然需要指定账户别名或账户 ID 来以 IAM 用户身份登录，但这些不是凭证。您无法使用访问密钥 ID 登录控制台。

2.  B. 一旦登录，您的会话将保持活动 12 小时。之后会过期并退出，以保护您的账户。

3.  A. 如果本应可见的资源看起来缺失，可能是选择了错误的区域。由于您以 root 身份登录，您拥有账户中所有资源的访问权限。您无需访问密钥即可使用控制台。您无法在导航栏中选择可用性区。

4.  C. 您创建的每个资源标签必须拥有一个键，但值是可选的。标签在账户内不需要唯一，并且区分大小写。

5.  A. AWS CLI 需要访问密钥 ID 和密钥密钥。您可以使用 IAM 用户或 root 用户的凭证。出站网络访问 TCP 443 端口是必需的，而不是 80 端口。Linux 不是必需的，但您可以在 Linux、macOS 或 Windows 上使用 AWS CLI。您还可以使用 Android 或 iOS 设备的 AWS 控制台移动应用。

6.  A, D. 您可以使用 Python 和 pip 包管理器，或（除 Windows Server 2008 外）使用 MSI 安装程序在 Windows 上安装 AWS CLI。AWS SDKs 不包含 AWS CLI。Yum 和 Aptitude 仅为 Linux 服务。

7.  B. `aws configure` 命令会引导您设置 AWS CLI 的默认区域以及访问密钥 ID 和密钥密钥。`aws --version` 命令显示已安装的 AWS CLI 版本，但运行该命令不是使用 AWS CLI 管理资源的必要步骤。重启也不是必要的。使用 root 用户管理 AWS 资源是不安全的，因此无需为 root 用户生成新的访问密钥 ID。

8.  C. AWS CLI 可以以 JSON、文本或表格格式显示输出。它不支持 CSV 或 TSV。

9.  B, D, E. AWS 为 JavaScript、Java 和 PHP 提供 SDK。Fortran 没有 SDK。JSON 是表示数据的格式，而非编程语言。

10.  A, B. AWS Mobile SDK for Unity 以及 AWS Mobile SDK for .NET 和 Xamarin 可让您为 Android 和 Apple iOS 设备创建移动应用。AWS SDK for Go 不支持移动应用开发。AWS Mobile SDK for iOS 支持 Apple iOS 设备开发，但不支持 Android。

11.  A, B. AWS IoT 设备 SDK 可用于 C++、Python、Java、JavaScript 和 Embedded C。Ruby 或 Swift 没有对应的 SDK。

12.  A, D. AWS CLI 是一个运行在 Linux、macOS 或 Windows 上的程序，允许您通过终端与 AWS 服务交互。AWS SDKs 让您使用喜欢的编程语言编写与 AWS 服务交互的应用。

13.  B. CloudWatch 指标存储 AWS 服务的性能数据。日志存储来自应用程序和 AWS 服务的文本日志。事件是针对 AWS 资源发生的操作。警报监控指标。指标过滤器从日志中提取指标信息。

14.  D. CloudWatch 警报监控指标并在该指标超过指定阈值时触发。如果指标没有变化，警报不会触发。终止 EC2 实例是一个事件，您无法创建基于事件的 CloudWatch 警报。您也无法创建基于 Web 服务器日志中 IP 地址存在的警报。但您可以创建指标过滤器，在日志中查找特定 IP 地址并为其出现时递增自定义指标。

15.  A, C. SNS 支持 SMS 和 SQS 协议用于发送通知。您无法向 CloudWatch 事件发送通知。不存在移动拉取通知。

16.  C, D. CloudWatch Events 监控导致 AWS 资源状态变化的事件以及 AWS 控制台登录事件。在响应事件时，CloudWatch Events 可以执行操作，包括向 SNS 发送通知或重启 EC2 实例。它还可以按计划执行操作。它不监控日志或指标。

17.  B, D. 查看 AWS 资源会触发 API 操作，无论是通过控制台还是 CLI 进行。配置 AWS CLI 不会触发任何 API 操作。登录 AWS 控制台也不会触发 API 操作。

18.  A. CloudTrail 事件历史记录日志保存每个区域的管理事件的最近 90 天。创建跟踪是过度设计且不具成本效益，因为它会将日志存储在 S3 桶中。将 CloudTrail 日志流式传输到 CloudWatch 需要创建跟踪。CloudWatch Events 不记录管理事件。

19.  A, D. 在包含桶的区域创建跟踪将生成 CloudTrail 日志，您可以将其流式传输到 CloudWatch 进行查看和搜索。CloudTrail 事件历史记录不记录数据事件。CloudTrail 默认记录全球服务事件，但 S3 数据事件未包含。

20.  B. 日志完整性验证使用加密哈希帮助您断言 CloudTrail 日志文件未被从 S3 删除。它不防止篡改或删除，也无法告知文件如何被篡改。日志完整性验证与 CloudWatch 无关。

21.  D. 成本和使用情况报告显示您按服务的月度支出。保留实例报告和保留实例建议不显示实际月度成本。

22.  A. RDS 允许您购买保留实例以节省费用。Lambda、S3 和 Fargate 不使用实例。

23.  B. 保留实例使用率报告显示您通过保留实例节省了多少成本。保留实例覆盖率报告显示如果您购买保留实例，本可以节省多少成本。每日成本和每月 EC2 运行时长成本与使用情况报告不知道您通过保留实例节省了多少成本。

24.  D. Cost Explorer 会为 EC2、RDS、ElastiCache、Redshift 和 Elasticsearch 实例提供保留实例建议。您需要选择要分析的服务。但 Cost Explorer 不会为已被保留实例覆盖的实例提供建议。由于您的 Elasticsearch 实例已连续运行至少七天，该使用情况将被分析。

## Chapter 7: The Core Compute Services

1.  C. 实例的硬件配置由实例类型定义。高吞吐（或低吞吐）数据处理操作和数据流可以使用任何存储卷或任何实例（尽管某些可能更适合特定场景）。

2.  A. 快速启动（Quick Start）仅包含数十个最流行的 AMI。Community 标签包含数千个公开可用的 AMI（无论是否经过验证）。My AMIs 标签仅包含您账户中创建的 AMI。
