
# Cloud Functions

用户必须为 Cloud Functions 提供代码，以便在事件发生时开始运行，因为 GCP 完全管理软件和基础设施。云事件是指在云计算环境中发生的事件，例如数据库中存储的数据发生变化、存储系统中添加了新文件，甚至新虚拟机的创建都是此类操作的实例。触发器是指您对某个特定事件或一组事件感兴趣的声明。将函数绑定到触发器可让用户捕获事件并对其采取行动。事件数据是在事件触发器导致函数执行时传递给 Cloud Function 的数据：

![](images/Figure_1.31.png)

**Figure 1.31: Cloud Function**

# GCP 计算服务摘要

GCP 计算服务的摘要可见于 [Figure 1.32](#ch01.xhtml#fig1-32)：

![](images/Figure_1.32.png)

**Figure 1.32: Summary Compute Service**

# Compute Engine 创建（VM 实例）

Compute Engine 实例可运行 Google 的公共 Linux 和 Windows Server 镜像以及私有自定义镜像。Docker 容器也可部署在 Container-Optimized OS 公共镜像实例上。用户在创建时需要指定区域、操作系统和机器配置类型（虚拟 CPU 数量和 RAM）。每个 Compute Engine 实例都有一个包含操作系统的小型持久启动磁盘，且可添加更多存储空间。VM 实例默认时间为协调世界时 (UTC)。请按以下步骤创建虚拟机实例：

## 步骤 1：打开 Compute Engine

按 [Figure 1.33](#ch01.xhtml#fig1-33) 所述步骤打开平台的 Compute Engine：

![](images/Figure_1.33.png)

**Figure 1.33: VM Creation**

1. 用户可在搜索框中输入 `Compute Engine`。
2. 或者，用户可在 `Compute` -> `Compute Engine` | `VM instances` 下导航。

## 步骤 2：启用 Compute Engine API

当首次访问资源时，系统会提示用户启用 API，如 [Figure 1.34](#ch01.xhtml#fig1-34) 所示：

![](images/Figure_1.34.png)

**Figure 1.34: VM Creation API enablement**

1. 如果提示启用 API，请启用该 API。

## 步骤 3：VM 实例选择

按 [Figure 1.35](#ch01.xhtml#fig1-35) 所述步骤选择 VM：

![](images/Figure_1.35.png)

**Figure 1.35: VM Creation**

1. 选择 `VM instances`。
2. 点击 `CREATE INSTANCE` 开始创建过程。
3. GCP 提供 `IMPORT VM` 选项用于 Compute Engine 迁移。

## 步骤 4：VM 实例创建

按 [Figure 1.36](#ch01.xhtml#fig1-36) 所述步骤为 VM 实例选择位置和机器类型：

![](images/Figure_1.36.png)

**Figure 1.36: Location, machine selection for VM instance**

1. GCP 提供多种 VM 创建选项，第一种是从头创建 VM。我们将创建一个 `New VM instance`。
2. VM 可从模板创建。用户可创建模板以供将来使用。
3. VM 可从机器镜像创建，机器镜像是存储配置、元数据及其他创建 VM 所需信息的资源。
4. GCP 还提供将现成解决方案部署到 VM 实例的选项。
5. 实例名称由用户指定。
6. 标签为可选项，它们提供键值对以将 VM 分组。
7. 选择区域和可用区。
8. GCP 在机器配置方面提供广泛选项，从 `GENERAL-PURPOSE`、`COMPUTE-OPTIMIZED`、`MEMORY-OPTIMIZED` 到基于 `GPU` 的机型。
9. 在每个机器系列配置下，GCP 提供几个系列机型和机器类型（用于在 CPU 和内存之间选择）。
10. 用户可选择 CPU 平台和 GPU，如果想选择 vCPU 与核心比率及可见核心数。

> **Note:** 尝试选择不同的机器配置并观察预估价格的变化。

## 步骤 5：VM 实例磁盘和容器选择

按 [Figure 1.37](#ch01.xhtml#fig1-37) 所述步骤为实例选择启动磁盘：

![](images/Figure_1.37.png)

**Figure 1.37: Boot disk selection for VM instance**

1. 启用显示工具，启用屏幕录制工具的使用。
2. 通过保持此 VM 内存加密来保护使用中的数据。
3. `Deploy Container` 选项在需要使用容器优化的 OS 镜像将容器部署到 VM 实例时非常有用。
4. 用户可通过点击 `change` 更改操作系统、硬盘大小和类型 (HDD/SSD)。

## 步骤 6：VM 实例创建访问设置

按 [Figure 1.38](#ch01.xhtml#fig1-38) 所述步骤配置访问权限：

![](images/Figure_1.38.png)

**Figure 1.38: access control for VM instance**

1. 选择设置与 VM 实例关联的默认服务账号，或用户可创建服务账号并将其用于 Compute Engine。
2. 用户需选择 VM 的访问方式，可选择 `allow default access`，或 `allow all the APIs` 或仅允许特定 API 访问 VM。
3. 默认情况下，所有互联网流量均被阻断，我们需要启用它们。
4. `networking`、`disks`、`security` 和 `management` 下提供了磁盘保护、预留、网络标签、更改主机名、实例删除时删除或保留启动磁盘等附加选项。
5. 点击 `Create`。

# 访问 VM 实例

虚拟机创建后，将列在 `VM instances` 下，如 [Figure 1.39](#ch01.xhtml#fig1-39) 所示：

![](images/Figure_1.39.png)

**Figure 1.39: VM instance created and listed under VM instances**

1. 点击实例类型查看 VM 详情（包括 VM 的区域、可用区、机器配置、CPU 利用率、内存利用率的负载监控等）。
2. `Internal IP address` 为子网 IP 地址。
3. `External IP address` 用于与外部设备通信。
4. `SSH` 用于连接到 VM。

## 步骤 1：访问 VM

按 [Figure 1.40](#ch01.xhtml#fig1-40) 和 [Figure 1.41](#ch01.xhtml#fig1-41) 所述步骤访问创建的 VM 实例：

![](images/Figure_1.40.png)

**Figure 1.40: Accessing the VM**

1. 点击 `SSH` 选项并选择 `open in browser window`。

新窗口将打开，SSH 密钥将被传输并建立连接，如 [Figure 1.41](#ch01.xhtml#fig1-41) 所示：

![](images/Figure_1.41.png)

**Figure 1.41: Accessing the VM**

在窗口中尝试以下命令：

a. `Hostname`（获取 VM 实例名称）
b. `Lsblk`（获取磁盘信息）
c. `Sudo su –`（检查 root 权限）
d. `Logout`（退出 root 权限）
e. `Cat /etc/os\-release`（查看操作系统详情）
f. `Logout`（关闭连接）

# 删除 VM 实例

按 [Figure 1.42](#ch01.xhtml#fig1-42) 所述步骤删除 VM 实例：

![](images/Figure_1.42.png)

**Figure 1.42: Deletion of VM**

1. 点击三个点并选择 `Delete`。
2. 弹出窗口将请求确认。

> **Note:** 所有计算资源在任何平台上都很昂贵，使用后请务必释放它们。

# BigQuery

任何人都可以使用 BigQuery 在几秒钟内分析 TB 级数据，BigQuery 是 Google Cloud Platform 提供的全托管无服务器数据仓库解决方案。它通过机器学习、地理空间分析和商业智能等内置功能，简化了数据的管理和分析。BigQuery 的无服务器架构利用 SQL 查询为组织提供最紧迫问题的答案，且无需管理底层基础设施。
