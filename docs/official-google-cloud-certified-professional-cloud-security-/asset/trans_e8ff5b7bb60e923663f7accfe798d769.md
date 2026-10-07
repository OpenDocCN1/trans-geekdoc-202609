

# Google 专业级云安全工程师考试 – 模拟题 II

- 13. 安全策略在 Google Cloud Armor 中起什么作用？
- A. 安全策略定义了对 Google Cloud 资源访问控制的规则
- B. 安全策略强制执行静态和传输中数据加密
- C. 安全策略允许对防火墙规则和网络访问控制列表（ACL）进行配置
- D. 安全策略规定了 Google Cloud Armor 对传入请求的行为

- 14. Google Cloud Logging 中日志汇集器（log sinks）的作用是什么？
- A. 从各种 Google Cloud 服务收集日志并将其存储在 Cloud Storage 中
- B. 使用机器学习算法分析日志数据并生成洞察
- C. 将日志导出到第三方日志和监控系统
- D. 管理日志数据的访问控制和权限

- 15. 在 Google Cloud Logging 中启用基于日志的指标（log-based metrics）的好处是什么？
- A. 它允许你使用自定义仪表板和图表将特定事件可视化
- B. 它允许你监控特定事件并根据日志条目触发告警
- C. 它能够对日志数据进行实时分析以检测安全威胁
- D. 它帮助你自动管理日志存储和保留策略

- 16. Google Cloud Compute Engine 中实例模板（instance templates）的作用是什么？
- A. 实例模板用于创建 Compute Engine 实例的快照
- B. 实例模板允许管理机器类型和大小
- C. 实例模板允许从头创建自定义镜像
- D. 实例模板定义了创建虚拟机（VM）实例的配置设置

- 17. 哪个陈准确描述了 Google Cloud 上 Compute Engine 的镜像生命周期管理？
- A. Compute Engine 提供自动镜像生命周期管理，包括对所有自定义镜像进行定期备份和版本控制
- B. 用户对镜像生命周期具有完全控制，包括创建和管理自定义镜像快照及元数据的能力
- C. Compute Engine 在活动一段时间后自动删除所有未使用的镜像以优化存储使用
- D. 镜像生命周期管理仅适用于 Google 管理镜像，不能应用于自定义镜像

- 18. 哪种 Google Cloud 功能通过启用安全启动（Secure Boot）、虚拟可信平台模块（vTPM）和完整性监控为虚拟机（VMs）提供增强安全性？
- A. 保护型虚拟机（Shielded VM）
- B. 虚拟私有云（VPC）
- C. Google Cloud Armor
- D. Cloud 安全扫描器（Cloud Security Scanner）

- 19. 应实施何种安全措施来保护 Google Cloud CI/CD 流水线产生的制品？
- A. 将制品存储在公共访问的存储桶中
- B. 对静态和传输中的制品进行加密
- C. 为所有流水线服务账户授予广泛的读取权限
- D. 禁用制品访问的日志记录和审计

- 20. 哪种 Google Cloud 功能通过允许组织根据元数据和属性定义并强制容器镜像部署的自定义策略，来执行安全的软件供应链？
- A. 二进制授权（Binary Authorization）
- B. 容器注册表（Container Registry）
- C. Cloud Build
- D. Google Kubernetes Engine (GKE)

- 21. Google Kubernetes Engine (GKE) 中的哪种安全功能通过自动管理和轮换静态加密密钥来保护容器工作负载？
- A. Google Cloud Armor
- B. Cloud 身份感知代理（IAP）
- C. 二进制授权（Binary Authorization）
- D. 使用 Cloud Key Management Service（KMS）的 GKE 数据加密

- 22. 哪个陈准确描述了 Google Kubernetes Engine (GKE) 中命名空间（namespaces）的作用？
- A. 命名空间用于控制不同 GKE 集群之间的网络流量
- B. 命名空间通过划分资源在单个 GKE 集群内提供逻辑隔离
- C. 命名空间负责自动伸缩 GKE 集群中的节点数量
- D. 命名空间通过基于令牌的身份验证确保对 GKE API 服务器的安全访问

- 23. Google Kubernetes Engine (GKE) 中基于角色的访问控制（RBAC）的主要目的是什么？
- A. RBAC 允许对 Kubernetes 资源的权限和访问进行细粒度控制
- B. RBAC 根据工作负载需求自动伸缩 GKE 节点数量
- C. RBAC 管理 GKE 集群内容器化应用程序的网络流量
- D. RBAC 使用服务网格确保 GKE 集群之间的安全通信

- 24. 哪个陈准确描述了 Google Kubernetes Engine (GKE) 中服务网格（service mesh）的作用？
- A. 服务网格为 GKE 集群内的静态数据安全提供额外的加密层
- B. 服务网格负责管理 GKE 服务的网络策略和入站控制（ingress）
- C. 服务网格增强 GKE 集群中微服务的的可观测性、流量管理和安全性
- D. 服务网格在 GKE 中自动扫描容器镜像的漏洞和安全风险

- 25. 哪种安全措施有助于确保 Google Cloud 中容器镜像的完整性和安全性？
- A. 容器注册表（Container Registry）漏洞扫描
- B. 为了加快镜像部署而禁用镜像扫描
- C. 为了系统兼容性，以特权权限运行容器
- D. 在不进行任何访问控制的情况下公开共享容器镜像

- 26. 正确或错误：Google Cloud 中的容器漏洞扫描会自动识别并告警容器镜像中的安全风险和漏洞。
- A. 正确
- B. 错误

- 27. 你的 Google Cloud 组织策略为所有组织的安全控制提供了护栏（guardrails）。在设置组织策略时，以下哪些不是最佳实践（选择所有适用项）？
- A. 组织策略应随着需求的明确随时间推实施
- B. 将组织策略的控制权委托给 SRE 团队
- C. 在执行策略之前，充分测试并验证其对你的资源和应用程序的影响
- D. 通常不需要监控和审计策略，因为它们从一开始就提供了一个实施安全控制的稳健框架
- E. 由于组织策略是在组织层级设置的，通常不需要在文件夹或项目层级实施它们
- F. 你不应该通过基础设施即代码（IaC）对策略进行版本控制

- 28. 在 Google 中创建项目时，以下哪项**不是**最佳实践（选择所有适用项）？
- A. 为你的项目实施一致的命名规范，以确保清晰且易于识别
- B. 使用默认项目控制，因为这可以让你快速上手
- C. 为你的项目启用审核日志和监控，以跟踪并分析环境中的活动
- D. Google 不对 Google Cloud 组织中的项目数量设置限制，因此放弃项目并创建新项目是安全的
- E. 使用宽泛的 IAM 角色授予超出所需的访问，以免阻碍开发
- F. 利用 Google Cloud 的资源层次结构（包括文件夹和项目）来有效地组织和管理资源

- 29. 客户有一个团队专门管理用户身份和访问。另一个云工程团队管理 Google Cloud 并对组织策略有深入了解。该公司管理 Google Cloud 的正确权限模型应该是什么？
- A. 为云工程团队授予超级管理员角色，以便他们可以管理整个组织的用户和组。
- B. 限制超级管理员角色。将用户和组管理权限授予身份访问团队。为云工程团队授予组织管理员角色。
- C. 为身份访问团队授予超级管理员角色，为云工程团队授予组织管理员角色。
- D. 为身份访问团队授予超级管理员和组织管理员角色，以便他们可以有效地管理整个组织的访问。

