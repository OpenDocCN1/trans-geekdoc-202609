
通常会同时使用这两种类型的操作。例如，如果您在桶中存储 Web 服务器日志文件，可能希望最初将每个日志文件保存在 `STANDARD` 存储中。当文件达到 90 天时，您可以将其通过 S3 移动到 `STANDARD_IA` 存储。然后，在 `STANDARD_IA` 存储中保存 365 天后，文件将被删除。

按照 Exercise 8.1 的步骤创建您自己的 S3 桶。

## S3 Glacier

S3 Glacier 提供长期归档 infrequently accessed（很少访问）数据的功能，成本极低。您可以上传大量数据以实现长期、耐用的存储，希望永远用不到，但如果需要，它会在那里（在不太可能发生的情况下）。Glacier 保证在给定年份内具有 99.999999999 百分比的耐用性。这正好是 S3 中 `GLACIER` 存储类的相同耐用性水平。

### Archives and Vaults

在 Glacier 中，您存储一个或多个文件在一个 archive 中，archive 是一个信息块。虽然您可以在一个 archive 中存储单个文件，但更常见的做法是将多个文件组合成 `.zip` 或 `.tar` 文件并将其作为 archive 上传。archive 的大小可以从 1 字节到 40 TB 不等。Glacier 将 archives 存储在 vault 中，vault 是一个 region-specific（region 特定）容器（类似于 S3 桶），用于存储 archives。Vault 名称在 region 内必须唯一，但不需要全局唯一。

您可以使用 Glacier 控制台创建和删除 vault，但要上传、下载或删除 archives，必须使用 AWS 命令行接口 (CLI) 或编写自己的代码来通过 AWS 软件开发套件 (SDK) 与 Glacier 交互。此外，还有第三方程序可以让您与 Glacier 交互，例如 CloudBerry Backup (`https://www.cloudberylab.com/backup.aspx`)、FastGlacier (`https://fastglacier.com`) 和 Arq Backup (`https://www.arqbackup.com`)。

### 检索选项

由于 Glacier 设计用于长期归档，它不提供实时访问 archives 的功能。从 Glacier 下载 archive 是一个两步过程，需要先启动一个检索作业，然后在作业完成后下载数据。完成作业的时间取决于您选择的检索选项。有三种检索选项：

**Expedited** 除非在异常高需求期间，expedited 检索通常在 1 到 5 分钟内完成，尽管大于 250 MB 的 archive 可能需要更长时间。在 US East 区域，成本为每 GB `$0.03`。您可以选择购买预配置容量，以确保 expedited 检索及时完成。

**Standard** Standard 检索通常在 3 到 5 小时内完成。这是默认选项。该选项的成本为 US East 区域每 GB `$0.01`。

**Bulk** Bulk 检索是最低成本选项，在 US East 区域的成本为每 GB `$0.0025`，通常在 5 到 12 小时内完成。

## AWS Storage Gateway

AWS Storage Gateway 简化了将现有的本地服务器连接到 AWS 云存储的过程。由于它使用行业标准存储协议，无需在现有服务器上安装特殊软件。相反，您只需在本地部署一个 AWS Storage Gateway 虚拟机并将服务器连接到它。Storage Gateway 处理服务器与 AWS 存储基础设施之间的数据传输。虚拟机可以在 VMware ESXi 或 Microsoft Hyper-V 超融合程序上运行。

AWS Storage Gateway 提供以下三种虚拟机类型，适用于不同的使用场景：

* 文件网关（File gateways）
* 卷网关（Volume gateways）
* 磁带网关（Tape gateways）

### 文件网关

文件网关允许您使用 Network File System (NFS) 和 Server Message Block (SMB) 协议将数据存储在 Amazon S3 中。虽然数据存储在 S3，但它会本地缓存，从而实现低延迟访问。文件网关可以作为普通的本地文件服务器工作。由于数据存储在 S3，您可以利用 S3 的所有功能，包括版本管理、桶策略、生命周期管理、加密和跨区域复制。

### 卷网关

卷网关提供基于 S3 的存储卷，供本地服务器通过 Internet Small Computer System Interface (iSCSI) 协议使用。卷网关支持以下两种配置：

**存储卷** 存储卷会在本地存储所有数据，并异步将其作为 Elastic Block Store (EBS) 快照备份到 S3。存储卷是 1 GB 到 16 TB 大小的良好选择，适合需要 uninterrupted（无间断）访问数据的场景。存储卷大小可从 1 GB 到 16 TB。

**缓存卷** 卷网关将所有数据存储在 S3，仅将频繁使用的子集缓存在本地。缓存卷大小可从 1 GB 到 32 TB。这适合本地存储空间有限的情况。由于仅缓存子集数据，如果与 AWS 的连接中断，某些数据可能无法访问。如果这不可接受，应使用存储卷。两种配置均允许手动或计划进行 EBS 快照。EBS 快照始终存储在 S3 中。您可以将 EBS 快照还原到本地网关存储卷或可挂载到 EC2 实例的 EBS 卷上。

### 磁带网关

磁带网关模拟传统的磁带备份基础设施。它与常见的备份应用程序（如 Veritas Backup Exec、NetBackup、Commvault 和 Microsoft System Center Data Protection Manager）兼容。您只需将备份应用程序配置为通过 iSCSI 连接到磁带网关。在磁带网关上，您可以创建虚拟磁带，每个虚拟磁带的容量在 100 GB 到 2.5 TB 之间。

磁带网关将虚拟磁带存储在由 S3 支持的虚拟磁带库（VTL）中。工作流程如下：当备份软件将数据写入虚拟磁带时，磁带网关会异步将数据上传到 S3。由于备份数据量大且上传耗时，磁带网关会在上传完成前保留数据在缓存存储中。如果需要从虚拟磁带恢复数据，磁带网关会从 S3 支持的 VTL 下载数据并将其存储在其缓存中。

为了实现成本效益高的长期存储，您可以将虚拟磁带从 VTL 移动到由 Glacier 支持的虚拟磁带架（virtual tape shelf），以实现更低成本的长期存储。要恢复存档的虚拟磁带，必须发起一个检索请求，通常需要 3 到 5 小时。检索完成后，虚拟磁带将在 S3 支持的 VTL 中可用，并可传输到磁带网关。

## AWS Snowball

AWS Snowball 是一种设计用于在短时间内在本地站点和 AWS 云之间移动大量数据的硬件设备。Snowball 的常见使用场景包括：

* 将办公室或数据中心的数据迁移到 AWS 云
* 快速将大量数据转移到或从 S3 用于备份或恢复目的
* 向客户和合作伙伴分发大量内容

Snowball 的核心思想是，物理运输大量数据比通过网络传输更快。例如，假设您想将一个 40 TB 的数据库迁移到 AWS，即使通过高速的 1 Gbps 连接，也需要超过 4 天！

但相反，AWS 会按名义费用向您发送一个 Snowball 设备。您只需将文件转移到它上并将其寄回。当 AWS 收到设备后，会将文件从 Snowball 传输到一个或多个 S3 桶中。导入文件到 S3 不会产生任何传输费用，一旦上传，文件即可供其他 AWS 服务使用。

### 硬件规格

最大 80 TB 的 Snowball 设备费用为 $250，可存储高达 72 TB。如果不需要传输这么大的数据量，您可以选择稍小的 50 TB Snowball，费用为 $200，可存储高达 42 TB。Snowball 的 RJ45 和 SFP+ 网络接口支持最高 10 Gbps 的速度，使得在约 2.5 天内将 72 TB 数据传输到设备上！(虽然 10 Gbps 连接在不到一天内即可完成传输，但 Snowball 中的固态硬盘 (SSD) 的写入速度限制了实际传输速率约为 3 Gbps。)

收到 Snowball 后，您可以在 10 天内保留它而无需额外费用。如果超过 10 天，每天将额外收取 $15 的费用。您最多可保留 Snowball 90 天，足够填满设备。

![](img/note.jpg) 您可以使用 Snowball 导出 S3 中的数据，但会按出站 S3 传输费率计费，费用范围在每千兆字节 $0.03 至 $0.05 之间，具体取决于地区。

### 安全

Snowball 采用坚固、防篡改的外壳。它包含可信平台模块 (TPM) 芯片，用于检测对硬件、软件或固件的未经授权修改。每次使用后，AWS 会验证 TPM 是否检测到任何篡改。如果 TPM 检测到篡改或设备出现损坏，AWS 不会从该设备中传输任何数据。

Snowball 采用两层加密。第一层：在您将数据传输到或从 Snowball 时，数据在传输过程中使用 SSL 加密。第二层：Snowball 上的数据始终在静止状态下加密。Snowball 通过要求您仅使用 Snowball 客户端或更高级的 S3 SDK Adapter for Snowball 进行数据传输来强制数据加密。前者无需任何编程知识。两者均在 Linux、macOS 和 Windows 操作系统上运行。

数据使用 AES 256 位加密，由 Snowball 客户端或 S3 SDK Adapter for Snowball 强制执行，确保设备永不存储未加密的数据。为进一步提升安全，AWS 在将 Snowball 发送给另一位客户之前，会依据美国国家标准技术局 (NIST) 在特刊 800-88 中发布的媒体擦除标准，对 Snowball 上的数据进行擦除。

### Snowball Edge

Snowball Edge 类似于 Snowball，但提供更丰富的功能。Snowball Edge 具备与 Snowball 相同的网络连接选项，并增加了 QSFP+ 端口，可实现比 Snowball 更快的网络速度。此外，Snowball 仅设计用于在本地环境与 S3 之间传输大量数据，而 Snowball Edge 除此功能外，还提供：

* 本地存储用于 S3 桶
* 本地运行 EC2 实例和 Lambda 函数的计算能力
* 使用 NFS 版本 3 和 4 协议的文件服务器功能

您可以从三种设备选项中选择，每种都针对不同的应用场景优化：

**存储优化** 该选项提供最高 80 TB 可用存储、24 个 vCPU 以及 32 GB 内存，适用于计算类应用。QSFP+ 网络接口支持最高 40 Gbps。

**计算优化** 该选项提供最高计算能力，拥有 52 个 vCPU 和 208 GB 内存，以及 39.5 TB 可用存储，其中 7.68 TB 专用于计算实例。

**计算优化（带 GPU）** 该选项与计算优化完全相同，唯一区别在于加入了 NVIDIA V100 Tensor Core 图形处理单元 (GPU)，使其特别适合机器学习和高性能计算应用。两种计算优化设备均配备支持最高 100 Gbps 的 QSFP+ 网络接口。

您可以将 5 到 10 台 Snowball Edge 设备集群在一起，构建本地的高可用计算或存储集群，这对于需要本地处理大量数据的情况非常有用。

![](img/note.jpg) Snowball Edge 不支持虚拟私有云 (VPC)。您不能在 Snowball Edge 上运行的 EC2 实例放入 VPC 中，而是在本地网络中为实例分配 IP 地址。

Table 8.2 突出了 Snowball 与 Snowball Edge 之间的主要相似性和差异。

**TABLE 8.2** Snowball 与 Snowball Edge 对比

| Feature | Snowball | Snowball Edge |
| --- | --- | --- |
| Transfer data to and from S3 | Yes | Yes |
| Local EC2 instances | No | Yes |
| Local compute with Lambda | No | Yes |
| File server functionality using NFS | No | Yes |
| Local S3 buckets | No | Yes |

## 摘要

S3 是 AWS 的主要存储服务。尽管 S3 与所有其他 AWS 服务集成，但它与 S3 Glacier 以及计算服务（EC2、Lambda）之间的关系尤为紧密。

为了实现耐用且高度可用的云存储，请使用 S3。您可以通过 bucket policy 将文件设置为私有或公开。如果需要长期存储成本较低、使用频率较低的数据，S3 Glacier 是最佳选择。

在本地存储方面，AWS Storage Gateway 让您通过虚拟机访问数据，该虚拟机会自动与 S3 同步。

将文件传输到或从 S3 的常见方式包括通过 Internet、虚拟私有网络 (VPN) 或 Direct Connect 链路。但对于大量数据，这些方式不切实际，硬件解决方案更为合适。Snowball 是一种坚固、防篡改的设备，AWS 会将其寄送给您。您将文件写入它，寄回后，AWS 会将文件传输到 S3。

另一种硬件选项是 Snowball Edge。它具备与 Snowball 相同的功能，还能作为使用 NFSv3 和 NFSv4 协议的持久本地文件服务器。此外，您还可以在本地运行 EC2 实例或 Lambda 函数。

### 考试要点

**理解 S3 中的持久性与可用性之别。** 持久性是指在一年内丢失对象的可能性；可用性是指在一年内对象可访问的百分比。

**根据成本、合规和可用性需求选择最佳 S3 存储类。** S3 提供六种存储类。`STANDARD` 可用性最高（99.99%），跨至少三个可用区复制对象，且是每 GB 月费用最高的存储类。`ONEZONE_IA` 可用性最低（99.5%），仅在单个可用区存储对象，其每 GB 月费用不到 `STANDARD` 存储类的一半。

**了解将数据导入和导出 S3 的不同选项。** 您可以通过 S3 控制台、AWS CLI 或直接访问对象的 URL 来上传或下载对象。AWS Storage Gateway 让本地服务器使用 iSCSI、NFS、SMB 等行业标准存储协议与 S3 进行数据传输。AWS Snowball 和 Snowball Edge 通过安全的物理方式实现数据向 S3 的导入和导出。

**了解何时使用 bucket policy、用户策略和访问控制列表 (ACL)。** 使用 bucket policy 或 ACL 来授予对象的匿名访问权限，例如希望公开的网页或图片。使用用户策略来授予特定 IAM 主体对对象的访问权限。

# 第 9 章 核心数据库服务

**本章涵盖的 AWS 认证云实践考试目标可能包括，但不限于，以下内容：**

* **领域 3：技术**
* ![images](img/correction.png) 3.1 定义在 AWS 云中部署和运行的方法
* ![images](img/correction.png) 3.3 识别核心 AWS 服务

![images](img/clogo.jpg)

## 介绍

许多应用程序使用数据库来存储、检索和组织数据，因此所选的数据库类型以及其配置对这类数据库驱动应用的性能和可用性有重大影响。

在传统基础设施中，组织通常自行安装和配置数据库服务器。例如，企业可能使用 Microsoft SQL Server 或 Oracle 数据库来存储客户信息。虽然可以在云中构建和运行自有的数据库服务器，但 AWS 提供了另一种——对于许多用户来说更优的——选择：托管数据库服务。

使用托管数据库服务时，您可以通过 AWS 管理控制台或 AWS 命令行界面 (CLI) 来创建数据库。AWS 负责数据库软件的安装和维护，以及数据库备份和复制。

在本章中，您将了解 AWS 提供的以下三种不同的托管数据库服务：

* 关系型数据库服务 (RDS)
* DynamoDB
* Redshift

## 数据库模型

一个数据库可以使用关系型或非关系型模型。您选择的模型取决于您的应用程序如何存储、组织和检索数据。重要的是要理解，应用程序的需求决定了您选择的数据库模型，而不是相反。

大多数关系型和非关系型数据库之间的技术差异超出了本书的范围，但在本章中，您将了解这两者之间的主要区别。

### 关系型数据库

关系型数据库已经存在很长时间，即使您从未创建或维护过一个，您也已经熟悉其基本概念。关系型数据库类似于包含列和行的电子表格。在关系型数据库中，列被称为`attribute`，行被称为`record`。它们都存储在`table`中，一个数据库可以包含多个表。Table 9.1 显示了一个简单的关系型数据库表可能的样子。

**TABLE 9.1** 客户表

| `Customer ID` | `Last Name` | `First Name` | `Last Purchase` |
| --- | --- | --- | --- |
| 1670 | Isaacson | Callan | 08/29/18 |
| 1680 | Ashland | Chessa | 12/15/16 |
| 1690 | Colson | Charlie | 02/20/12 |
| 1700 | Charlotte | Linda | 05/09/17 |

与电子表格一样，关系型数据库表具有定义的列数。数据库表与电子表格的区别在于，关系型数据库表中的每一行必须唯一。确保行唯一性的一种方法是定义主键——一个必须唯一且在每条记录中存在的列。在 Table 9.1 中，主键将是 `Customer ID` 列。

![](img/note.jpg) 主键可以由多个列组成。
