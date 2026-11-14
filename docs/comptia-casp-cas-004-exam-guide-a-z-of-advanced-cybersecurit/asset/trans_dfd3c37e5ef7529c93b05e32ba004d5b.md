

## 特权访问管理优势

*   无需共享某些 `软件定义存储` (`SDS`) 产品所需的特权管理凭据（如 Linux 上的 root 用户密码）。
*   提供有时限的特权存储管理员会话，并支持远程终止存储管理员会话。
*   支持访问存储管理员会话的用户进行多因素身份验证。
*   可捕获按键记录、进程活动和正在运行的程序（在某些 `SDS` 产品中非常有用）。
*   管理和审计特权存储账户及认证密钥，如密码和 `SSH` 密钥。

## 安全远程支持

安全远程支持由客户管理，具有以下优势：

*   为服务、维护或支持团队提供有时限的受审计访问权限。
*   支持为每个访问会话自定义审批工作流（多级审批）。
*   记录并审计在支持或服务会话中执行的所有活动。

## 用例示例

本章演示了 IBM Spectrum Scale 与 Verify Privilege Vault 的集成。该概念可扩展并应用于其他 IBM 存储系统。IBM® Security™ Verify Privilege Vault On-Premises (Verify Privilege Vault)，前身为 IBM Security™ Secret Server，是新一代特权账户管理方案，它与 IBM Storage 集成，确保对 IBM Storage 管理会话的访问安全且受实时监控，并具备满足审计和合规要求的录制功能。存储管理会话的特权访问实现集中管理，每个会话均可设定时限并进行远程监控。

## IBM Spectrum Scale

IBM Spectrum Scale 是一种可扩展的高性能文件系统，适用于各种用例（图 8.2）。它提供世界级的存储管理，具备可扩展性、闪存加速性能和自动存储分层功能。IBM Spectrum Scale 在降低存储成本的同时，提升了云、大数据和分析环境中的安全性与管理效率。简而言之，IBM Spectrum Scale 提供以下优势：

*   近乎无限的扩展性，支持高达九百京（nine quintillion）个文件和千万亿亿字节（yottabytes）级别的数据。
*   高性能并支持对一组共享数据的同时访问。
*   集成 `信息生命周期管理` (`ILM`) 功能，可在存储层级（包括闪存、磁盘、磁带和对象存储（公有云和私有云））之间自动移动数据。`ILM` 可降低运营成本，因为更少的管理员可以管理更大规模的存储基础设施。

借助 `SDS`，您可以构建具有以下特征的基础设施解决方案：

*   易于扩展，可使用相对廉价的通用硬件，同时保持世界级的存储管理能力。
*   可部署在 `Amazon Web Services` (`AWS`) 和 IBM Cloud 上。这是一种跨平台解决方案，可在 IBM AIX®、Linux 和 Windows 服务器节点上运行，或混合部署这三种平台。IBM Spectrum Scale 也可用于 IBM Z。
*   作为预打包存储解决方案提供，名为 IBM ESS，包含去集群化 RAID。
*   跨越地理距离和不可靠的 WAN 连接实现全球数据访问。
*   多站点支持，可将本地 IBM Spectrum Scale 集群连接到远程集群，提供更大的管理灵活性和控制力。
*   跨多站点经验证的可靠性，并支持并发硬件和软件升级。
*   先进的协议访问方法，用于在同一全局命名空间下管理文件和对象，从而更高效地利用存储空间并避免数据孤岛。支持的协议包括 `NFS`、`SMB`、`POSIX`、`OpenStack Swift` 和 `S3`。
*   通过 `Hadoop 分布式文件系统` (`HDFS`) 透明特性，实现与 Hadoop 应用程序的无缝集成。
*   经验证的安全功能，确保数据隐私、真实性和可审计性。
*   静态数据的文件级加密和安全擦除。
*   策略驱动的压缩，减小静态数据体积并提高存储效率。
*   可用作容器的持久化存储。
*   包含 GUI，简化存储管理任务并监控系统的多个方面。

图 8.2 展示了 IBM Spectrum Scale：

![](images/Image25860.jpg)

**图 8.2：** IBM Spectrum Scale

IBM Spectrum Scale 常用于银行、金融、医疗、石油天然气和汽车等不同领域的高性能和计算密集型环境。其最常见的用例包括 `人工智能` (`AI`) 和深度学习、大数据分析、内容存储库、私有云和计算集群。它也常用于归档、高速备份和灾难恢复以及 `ILM` 的数据优化和弹性保障。

IBM Spectrum Scale 支持多种部署模型，其中之一是 IBM ESS，这是一种基于现代硬件的实现。IBM ESS 提供 IBM ESS 3000（高密度存储）和 IBM ESS 5000（大容量高性能存储）两种规格。

## Verify Privilege Vault

IBM Security Verify Privilege 提供本地部署和云产品。Verify Privilege Vault（图 8.3）是一种基于云的解决方案，组织无需担心任何硬件或软件要求。不过，IBM Security Verify Privilege On-Premises 需要专用服务器进行安装，并需要 `SQL` 数据库来存储详细信息。根据需求、功能和架构，您的组织可以决定选择哪种产品。本章以 Verify Privilege Vault On-Premises 为例，尽管本文档中的信息可在相关且必要的更改下扩展到云产品。特权访问是通往组织最有价值信息的途径。因此，实施 PAM 已成为重中之重。Verify Privilege Vault 是一款功能全面的 PAM 解决方案，同时提供本地部署和云部署，可帮助您的安全和 IT 运维团队快速、轻松地保护和管理所有类型的特权账户。使用 Verify Privilege Vault，您可以执行以下操作：

*   建立安全保险库。
*   发现特权。
*   保护密码。
*   满足合规要求。
*   控制会话。

Verify Privilege Vault 部署快速、易于使用且可为企业扩展。它与更广泛的 IBM Security 产品组合集成，适用于身份治理和多因素认证等关键用例。图 8.3 展示了 IBM Privilege Vault：

![](images/Image25867.jpg)

**图 8.3：** IBM Privilege Vault

以下列表描述了上图所示的架构：

*   架构左侧表示访问 Verify Privilege Vault 的不同介质。右侧表示高层内部工作原理。
*   Verify Privilege Vault 需要 `SQL` 服务器进行配置和数据管理。您可根据需要配置高可用性设置。
*   Verify Privilege Vault 提供会话启动器，可根据密钥模板中的触发器启动特定应用程序。例如，对于 Windows 平台，尝试访问 Windows 账户密钥时会调用远程桌面连接应用程序。同样，对于 UNIX 或 Linux 平台，使用 UNIX 或 Linux 账户密钥时会触发 `PuTTY` 应用程序。
*   分布式引擎用于远程密码更改和新账户发现。

## 安全影响/隐私顾虑

