
# 对 `dli01` 节点的操作

| root | 停止两个节点带有 Spark 的 IBM Spectrum Conductor： |
| :--- | :--- |
| | `source /opt/ibm/spectrumcomputing/profile.platform` |
| | `egosh service stop all` |
| | `egosh shutdown all` |

| egoadmin | 添加 DLI 权限： |
| :--- | :--- |
| | `eoconfig setitlement entitlement_file_dli.dat` |

| egoadmin | 启用 HA 功能： |
| :--- | :--- |
| | `source /opt/ibm/spectrumcomputing/profile.platform` |
| | `eoconfig mhost /shares/cws_share \|\|` |

# 对 `dli02` 节点的操作

| egoadmin | 启用 HA 功能： |
| :--- | :--- |
| | `source /opt/ibm/spectrumcomputing/profile.platform` |
| | `eoconfig mhost /shares/cws_share \|` |

| root | 刷新环境变量并启动两个节点带有 Spark 的 IBM Spectrum Conductor： |
| :--- | :--- |
| | `source /opt/ibm/spectrumcomputing/profile.platform` |
| | `egosh ego start all` |

| root | 运行 `init 0` 以模拟 `dli02` 崩溃。 |
| :--- | :--- |

| root | 检查集群状态和 DLI 服务。 |
| :--- | :--- |

| root | 启动 `dli02` 并启动服务。 |
| :--- | :--- |

# 安装计算节点的步骤

完成两个管理节点的安装和测试后，在计算节点上安装 DLI，如表 6-3 所示。

**表 6-3 计算节点安装步骤**

| 用户 | 操作 |
| :--- | :--- |
| root | 安装操作系统、GPU 驱动程序和 IBM PowerAI。 |
| root | 安装 IBM Spectrum Conductor Spark。 |
| egoadmin | 加入现有集群。 |
| root | 启动带有 Spark 的 IBM Spectrum Conductor 服务。 |
| root | 安装 DL 框架和 DLI 需要的开源软件。 |
| root | 安装 DLI。 |
| root | 检查集群状态： |

```
root@dli03# epoch resource list
NAME status swp ut it pg rim r15s rim15m
dli02.*d ok 56K 167M 366 1% 0.0 0.3 0.1 0.2 1
dli03.*d ok 516 167M 40G 9% 5 0.0 2.0 4.0 1
dli04.*d ok 56K 167M 366 1% 5 0.0 0.6 0.8 1

root@dli03# epoch resource list -m
IBM EGO current host : dli01.com
Candidate(master) : dli01.com,dli02.com
```

# 启用带有 Spark 的 IBM Spectrum Conductor 以监控 GPU 资源

在编写时，必须运行一个脚本来启用带有 Spark 的 IBM Spectrum Conductor 监控 GPU 资源。示例 6-2 显示了一个使用的命令。

```
#source /opt/ibm/spectrumcomputing/profile.platform
#/opt/ibm/spectrumcomputing/conductors/2.2/etc/gpuconfig.sh enable --quiet
-u Admin
```

登录 IBM Spectrum Computing 管理控制台，请参阅第 77 页的“如何登录 IBM Spectrum Computing 管理控制台”。

# 创建资源组

要创建资源组，请完成以下步骤：

1. 点击**资源 (Resources)** -> **资源规划 (Resource Planning)** -> **资源组 (Resource Groups)**。图 6-17 显示默认资源组配置。

![图 6-17 资源组窗口](img/f6f95defc8b3406a94b2807_181_0.png)

或者，可以通过运行命令获取相同的信息，如示例 6-3 所示。

**示例 6-3：从命令行查看资源组**

```
root@dli01:"# egosh resourcegroup view ComputeHosts

Name        : ComputeHosts
Description : 
Type        : Dynamic
ResReq      : select(img)
SlotExpr    :
HOSTS       : 1

SLOTS       FREE       ALLOCATED
4           0

Resource List : dli03.com

root@dli01:"# egosh resourcegroup view ManagementHosts

Name        : ManagementHosts
Description : 
```

```
Type : Dynamic
ResReq : select(mg)
SlotExpr :
HOSTS : 2

SLOTS FREE ALLOCATED
64 43 21
```

Resource List : `dli02.com` `dli01.com`

2. 从下拉列表中选择“创建资源组”(Create a Resource Group)，并为此新资源组设置参数，如第 170 页的图 6-18 所示。

# 资源组

`icluster` > 创建资源组

识别您的资源组 (*)

资源组名称：

![资源组名称输入框](img/f6f95defc8b3406a94b2807_183_0.png)

描述：

每个主机的槽数

- 每个主机的槽数：
- 每个主机的 CPU 数
- 高级公式：

资源选择方法：动态 (requirements)

成员主机显示

![成员主机显示](img/f6f95defc8b3406a94b2807_183_1.png)

成员主机（在当前集群中找到）

成员主机摘要：Hosts: 1 CPUs: 4 此组总槽数：0 检查重叠

过滤标准：`select(img)`。找到：1/3

| 主机名称 | 类型 | 模型 | CPU | CPU 因子 | 最大内存 | 最大交换 | 温度 | 此组总槽数 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `dli03` | `LINUXP64LE` | `PPC64LE` | 4 | 12.0% | 61352 | 167 | 40896.00 | 0 |

* 必填字段

![必填字段标记](img/f6f95defc8b3406a94b18_2.png)

**图 6-18 为 GPU 组设置参数**

注意：`ngpus` 值将槽数设置为物理 GPU 适配器。如果有多个任务共享 GPU 适配器的需求，可以使用适当的倍数定义字段，例如 `ngpus2`。也可以从命令行创建相同的资源组，如示例 6-4 所示。

**示例 6-4：从命令行查看 GPU 组**

```
root@dli01:~# egosh resourcegroup list
NAME                HOSTS  SLOTS  FREE  ALLOCATED
gpu_rg              1      1     0
ComputeHosts       1      4     0
InternalResourceGroup 3      30    21
ManagementHosts    2      64     43
```

# 创建 Spark 实例组

创建 GPU 资源组后，通过以下步骤创建 SIG：

1. 选择**负载 (Workload)** → **Spark** → **实例组 (Instance Groups)**，如图 6-19 所示。

![图 6-19 创建 Spark 实例组：1](img/f6f95defc8b3406a94b2807_184_0.png)

2. 点击**新建 (New)** → **模板 (Template)**，如图 6-20 所示。

![图 6-20 创建 Spark 实例组：2](img/f6f95defc8b3406a94b2807_185_0.png)

3. 在模板窗口中，有一个名为 `dli-template` 的现有模板，如图 6-21 所示。

![图 6-21 创建 Spark 实例组：3](img/f6f95defc8b3406a94b2807_185.png)

4. 完成此新 SIG 的所需参数，如表 6-4 所示。

**表 6-4 SIG 参数**

| 参数 | 值 |
| :--- | :--- |
| 实例组名称 | `SIG` |
| Spark 部署目录 | `/opt/SIG` |
| JAVA_HOME | `/usr/lib/jvm/java-1.8` |
| HA 恢复目录 | `/shares/sig` |
| Spark 执行器 (槽数) | `gpu_rg` |

图 6-22、第 174 页和第 175 页显示了这些 SIG 的配置窗口。

![图 6-22 SIG 配置窗口](img/f6f95defc8b3406a94b2807_186_0.png)

**图 6-23 设置 `JAVA_HOME` 变量**

注意：如果用户想要启用笔记本工具，请选择图 6-22 所示的三个选项之一。

![图 6-23 笔记本工具选项](img/f6f95defc8b3406a94b2807_187_0.png)

**图 6-24 创建 SIG**

注意：`JAVA_HOME` 的所需值取决于安装的实际环境。

174 IBM PowerAI：在 Power 服务器上深度学习

# 资源组和计划

选择为实例组提供资源的资源组或计划。

| | |
| :--- | :--- |
| Spark 驱动程序 | `ComputeHosts` |
| Spark 执行器 (CPU 槽数) | `ComputeHosts` |
| Spark 执行器 (GPU 槽数) | `gpu_rg` |
| Spark 调度服务 | |
| 批量主服务 | `ComputeHosts` |
| | 使用云主机工厂启用云扩展，以便实例组可以从云提供计算主机 |

显示成员主机

![成员主机显示](img/f6f95defc8b3406a94b2807_183_1.png)

**图 6-24 为 SIG 分配 GPU 资源**

5. 点击**创建并部署实例组**(Create and Deploy Instance Group) 并继续启动此 SIG 服务。当此 SIG 成功创建时，状态显示为“已启动”，如图 6-25 所示。

![图 6-25 检查 SIG 状态](img/f6f95defc8b3406a94b2807_188_0.png)

提供的 OCR 文本似乎是日志类的状态信息与来自名为《IBM PowerAI: Deep Learning own（在 IBM Power 服务器上释放深度学习）一书的技术文档的混合体。根据提供的内容，我对文本进行了清理，合并了页面，并按照您的要求进行了格式化。

```
- elk-ela* STARTED 258 /Managed d101.d 1 RUN 624
- plc* STARTED 243 d102.d 1 RUN 654
- elk-shi* STARTED 283 /Managed d101.d 1 RUN 644
- /Cluster*Intern*d101.d 1 RUN 657
- d102.d 1 RUN 655
- elk-ind* STARTED 281 /Managed d101.d 1 RUN 656
- d103.d 1 RUN 640
- derbybd /Managed d101.d 1 RUN 652
- elk-ela* STARTED 259 d102.d 1 RUN 623
- /Managed*
- IT50-SI* STARTED 307 /ITS50-SI* d103.d 1 RUN 700
- IT50-SI* STARTED 308 /ITS50-SI*Computed103.d 3 RUN 701
- 3 RUN 702
- mongood* STARTED 244 /Managed d101.d 1 RUN 630
- d1mao-o* STARTED 245 /Managed d101.d 1 RUN 631
- redis* STARTED 246 /Managed d101.d 1 RUN 632
- ldpd* STARTED 247 /Managed d101.d 1 RUN 633
- d1mao-m* STARTED 251 /Managed d101.d 1 RUN 634
- REST* STARTED 248 /Managed d101.d 1 RUN 635
- HostFac* /Managed*
- RS* STARTED 249 /Managed d101.d 1 RUN 629
- ascd* STARTED 250 /Cluster*d101.d 1 RUN 636
- ExecPro* STARTED 251 d102.d 1 RUN 651
- d103.d 3 RUN 562
- Service* STARTED 252 /Managed d101.d 1 RUN 645
- WebServ* STARTED 255 /Managed d101.d 1 RUN 646
- d102.d 1 RUN 639
- SparkCl* STARTED 280 /Cluster*Intern*d101.d 2 RUN 650
- d103.d 1 RUN 638
```

与 SIG `ITS50-SIG-sparkss` 和 `ITS50-SIG-sparkss` 相关的两个服务。

## 6.5 工作负载正在运行时主节点崩溃

在 SIG 启动后，通过 LI 图形界面启动一个深度学习（DL）工作负载，例如导入数据集或训练模型。

关于如何使用 LI 进行深度学习项目的更多信息，请参见第 212 页的 6.8，“用例：使用带有深度学习 Caffe Cisco-10 网络”。

在这种情况下，计算节点正在运行一个工作负载，此时主节点崩溃，但工作负载继续运行。带有 Spark 和 DLI 服务的 IBM Spectrum Conductor 由 `dl02` 接管，可以在那里继续监控和管理工作负载。访问网站更改为 `https://dl02.dli.com:8443`。

> 注意：运行时，DLI HA 不提供浮动服务 IP。

176 IBM PowerAI: 在 IBM Power 服务器上释放深度学习

图 6-26 展示了 DLI HA 接管过程。

![图 6-26 故障转移场景说明](img/f6f95c5defc8b3406a94a86b8d202807_190_0.png)

`dli01`（主节点），`dli02`（备用主节点），`dli03` 计算节点，服务正在接管……接管期间工作负载继续运行，`/Shares/cws_share` `/Shares/dli_userdata` `/Shares/sig_share`

## 如何登录 IBM Spectrum Computing 管理控制台

本节介绍了如何登录 IBM Spectrum Computing 管理控制台。

### 在笔记本电脑上编辑 `/etc/hosts`

您使用 FQDN（完全限定域名）访问 DLI，因此您必须在 `hosts` 文件中添加 IP 和主机名解析。如果您使用 Windows 笔记本电脑，文件位于 `C:\Windows\System32\drivers\etc` 目录下。如果你使用 Mac 笔记本电脑，文件位于 `/etc` 目录。无论哪种情况，向 `/etc/hosts` 文件添加一行，如示例 6-6 所示。

**示例 6-6 客户端中的 `/etc/hosts` 文件配置**

```
172.16.51.96 dli01.dli.com
172.16.51.97 dli02.dli.com
172.16.51.98 dli03.dli.com
```

## 获取访问 DLI 的证书

有两种方法获取访问 DLI 的证书：

### 手动添加异常

您必须为以下六个端口添加异常：`5000`、`5001`、`8443`、`8543`、`8643` 和 `9243`。例如，如果使用 Firefox 浏览器，输入 `https://dli01.dli.com:8443` 并回车，浏览器会显示安全无效。点击“添加异常”，如图 6-27 所示。然后弹出一个窗口提示您确认，如第 179 页的图 6-28 所示。

![图 6-27 异常窗口：1](img/f6f95c5defc8b3406a94a86b8d202807_191_0.png)

![图 6-28 异常窗口：2](img/f6f95c5defc8b3406a94a86b8d202807_192_0.png)

### 获取证书导入浏览器

从管理主机的 `/opt/ibm/spectrumcomputing/security/cacert.pem` 下载证书。然后打开 Firefox 并完成以下步骤：

1. 点击**工具（Tools）** -> **高级（Advanced）**。
2. 点击**机构（Authorities）**选项卡并**导入（Import）**。
3. 浏览到保存证书的位置并选择它。

第 6 章 IBM Spectrum Conductor 深度学习 179

4. 当提示信任 CA 时，确保选择此 CA 以识别网站并点击**确定**。您可以查看证书，如图 6-29 所示。

![图 6-29 查看证书](img/f6f95c5defc8b3406a94a86b8d202807_193_0.png)

5. 重启浏览器。

## 登录 IBM Spectrum Computing 管理控制台

图 6-30 显示 IBM Spectrum Computing 管理控制台的登录窗口。默认用户名密码为 `Admin`。

![图 6-30 IBM Spectrum Computing 管理控制台登录窗口](img/f6f95c5defc8b3406a94a86b8d202807_193_1.png)
