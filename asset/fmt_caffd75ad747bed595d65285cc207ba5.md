
- 创建组织单元 (OU)、账户和组 285
- 域维护任务 297
- 使用 Swing 迁移 339
- 使用微软免费迁移工具：ADMT 347
- 转换本地配置文件 364
- 回滚考虑 68
- 创建和管理账户 78
- 创建本地账户 80
- 设置本地账户属性 86
- 管理组 92
- Active Directory 组 100
- 忘记的密码 104
- 使用新功能进行用户和组管理 107
- ADAC 基础知识 107
- PowerShell 历史记录 118
- 创建用户 122
- 批量创建用户 125
- 启用账户 129

核心结论。

# 第 9 章 · 组策略：AD 的挑战与活动目录委托

- 组策略概念
- 策略是“全有或全无”的
- 策略具有继承性和累积性。
- 组策略的力量！刷新间隔
- 组策略基础。
- 组策略的复制是内置的
- GPO 在删除时会自动撤销。
- 你尚未登录以应用 GPO 设置。
- 本地策略与组策略对象
- 管理员或非管理员的 LGPO
- 用户特定的 LGPO。
- 创建 GPO。
- 修改组策略的默认行为
- 组策略策略。
- 组策略的应用
- 组策略是如何被隐含的。
- 使用访问控制列表 (ACL) 过滤组策略
- 强制和阻止继承
- 组策略设置的可能性
- 解密用户和计算机配置设置。
- 使用组策略设置密码和账户锁定策略
- 组策略首选项。
- 新版改进的 GPMC。
- 启动 GPO。
- 备份和恢复 GPO。
- 组策略故障排除。
- 策略结果工具 (RSOP)。
- 使用 GPMC 查看组结果。
- 使用 GPMC 进行组策略建模。
- gresult 命令。
- 使用事件查看器
- 故障排除 101：保持简单
- 活动目录委托。
- 委托组策略管理。
- 使用组织单元 (OU) 委托控制
- 创建新的组织单元
- 将用户账户移动到 OU 中
- 创建 MktPswAdm 组
- 委托营销部门密码。
- 重置控制到 MktPswAdm。
- 高级委托：手动设置权限。

查找已设置的委托，或取消委托 530

核心结论 531

# 第 10 章 • 活动目录联合服务 (AD FS) 533

- 理解 AD FS 关键组件和术语 534
- AD FS 常用术语和组件 534
- 理解 AD FS 证书。安装并配置 AD FS 基础架构。 5 536
- 使用服务器管理器规划 AD FS 角色和功能。使用 IIS 创建受信 SSL 证书 5 543
- 使用 AD FS 服务器配置向导。在 AD FS 中使用 Windows PowerShell 544
- 为 AD FS 添加受信泛赖方的其他配置选项 5 549
- 使用组策略实现客户端配置 核心结论 559

# 第 11 章 • 共享存储与聚类简介 561

- 共享存储基础 561
- 存储区域网络 (SAN) 562
- iSCSI 562
- 光纤通道 (Fiber Channel) 5 563
- SAS 机箱 563
- RAID 563
- SMB 3.0 563
- Windows Server 2012 R2 文件和存储服务 564
- 聚类 (Clustering) 566
- 聚类要求 566
- 聚类功能 567
- 聚类共享卷 (CSV) 568
- 聚类与虚拟化 569
- 理解仲裁 (Quorums) 570
- 高可用存储 5 571
- 存储空间 (Storage Spaces) 5 571
- 虚拟机内部的聚类 5 573
- 设置聚类 5 573
- 聚类配置 5 574
- 存储 5 575
- 在聚类中添加第一个节点 5 575
- 向聚类中添加第二个节点 5 585
- 设置基于来的聚类 5 587
- 核心结论 588

# 第 12 章 • Windows 2012 R2 存储：存储空间、SAN 能力和更佳工具 589

Windows Server 2012 R2 存储有什么新变化？ 589

- 分层存储空间 (Tiered Storage Spaces) 590
- 写回缓存 (Write-back Cache) 590
- 并行修复 (Parallelized Repair) 591
- 低级别改进：原生支持 591
- UEFI 支持 GPT 磁盘 592
- CHDS 更智能 592
- 在线自愈 (Online Self-healing) 592
- 在线识别 (Online Identification) and 593
- 精确和快速修正 (Precise and Rapid Correction) 593
- 深入查看存储空间 (In-depth Look at Storage Spaces) 594
- 复用微软云技术 (Reusing Technology from Microsoft's Cloud) 595
- 提供类 SAN 功能管理 (Providing SAN-like Capabilities with Microsoft Management) 595
- 创建存储空间 (Creating a Storage Space) 598
- 创建存储池 (Creating a Pool) 599
- 存储池限制 (Pool Limitations) 602
- 在磁盘管理中查看驱动器 (Viewing Drives in Disk Management) 603
- 使用 PowerShell 进行池化 (Pooling with PowerShell) 604
- 为虚拟磁盘分配空间 (Allocating Space to a Virtual Disk) 606
- 存储级演示与设置 (Storage-tier Demo and Setup) 519
- 在存储空间上使用 iSCSI (iSCSI on Storage Spaces) 523
- 添加 iSCSI 目标服务 (Adding the iSCSI Target Service) 523
- 从客户端侧连接 iSCSI 虚拟磁盘 (Connecting to iSCSI Virtual Disk from the Client Side) 528
- NFS 共享 (NFS Shares) 631
- 何处使用 NFS 共享 (Where to Use an NFS Share) 631
- 快速 NFS 设置 (Quick NFS Setup) 632
- 从客户端侧连接 NFS (Connecting to NFS from the Client Side) 636
