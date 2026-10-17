
尽管 3D 空间数据的收集速度不断加快，但用于处理、存档、管理、分发和分析大数据等问题的负担得技术价格却滞后了（Chen, 2009；Evangelinos and Hill, 2008；Liu, 2009 以及 Zhang, 2008；Meng et al., 2010；Onsypayev et al., 2012；Schön et al., 2010；Sugumaran et al., 2011）。在这些变化中，数据集的大小和处理海量信息所需的计算资源现在对于地方用户等来说更大。除了规模之外，数据集的多样性和更新率往往超过了现代空间计算技术的能力（Shekhar et al., 2012；Wang et al., 2009；Yang et al., 2011）。`LiDAR` 等大型数据集的处理可以使用高性能（`HPC`）环境，如集群、网格计算和超级计算机（Simhan and Ramirez (Ostermann et al., 2010）。Shekhar 等人（2012）的一项研究解决了手机轨迹、`GPS` 设备以及下一代交通服务的详细路线地图带来的挑战。这些新挑战包括详细信息、大数据多样性的增长、对多样方法的需求、地理信息的隐私问题以及跨空的空间推理。由于这些变化，研究人员开始寻找开发大规模数据密集型应用程序的特定算法。

云计算的出现为几个现实提供了可能的解决方案，包括改进供应、按需付费模式、降低软件成本、按需提供资源、可扩展性、弹性、无限的存储容量、设备独立性和数据可靠性（Abrham et al., 2009；Watson et al., 2010；Huang et al., 2010；McEovy and Schulze, 2008；Rezgui et al., 2012）Ji 等人概述的大数据问题包括管理平台、分布式文件系统、数据存储以及云环境中的虚拟化。虽然云计算服务现在已用于处理少数大数据集，但 Krishnan 等人（2010）研究了结合云计算和 `MapReduce` 编程来生成 `DEM`。在另一项研究中，Sugumaran 等人（2011）开发了一种使用各种并行计算的云应用程序。

## 3.2 方法论

尽管 `LiDAR` 数据的获取和使用在过去十年中迅速增长，但只有少数国家（如丹麦、芬兰和瑞士）在近期内完成了全国范围内的采集。在美国，地质调查局（`USGS`）作为领先机构，协调多项开发国家数据集的工作。该项目包含三个 `TB` 数据。爱荷华州是完成全州数据收集的州之一。

# 使用云计算环境处理大型 3D 空间数据集

没有足够强大的计算机来处理大区域的数据。此外，当前版本的 `ILP` 仅允许下载原始数据，并未为终端用户提供额外的处理功能，例如创建数字高程模型 `DEM` 以及衍生产品（如坡度、坡向和山体）。为了支持这些功能，利用成本效益的云资源开发并实现了 `CLIPS` 系统。

为了进行处理、验证和校验，使用了来自爱荷华州 `LiDAR` 项目的几块 `LiDAR` 图形数据。由于瓦片的大小随位置而异，因此选择了三个代表不同地形和 `LiDAR` 回波特征的瓦片：一个地形起伏较小的，一个起伏地形，和一个城市区域。对于每项研究，选择了不同数量的瓦片（`3 x 9`，`5 x 5 = 25`）进行处理。每个瓦片的大小在平坦地形为 `90` 到 `370 MB` 不等，起伏地形为 `137` 到 `491 MB`，城市地形为 `181` 到 `355 MB`。通常，使用指定为最后一个波的 `LiDAR` 点来创建地形的数字地形模型（`DTM`，即裸地），而使用第一个波则创建数字表面模型（`DSM`），它包含了树木和建筑等所有特征。在其他情况下，所有回波指的是 `3D LiDAR`，其中多个回波表示某位置的多个高度，例如树冠层中的开口处。在我们的案例中，我们使用了大型回波数据集来测试和验证该方法。

## 3.2.2 CLiPS 设计与实现

本研究开发的 `CLIPS` 总体架构如图 3.3 所示。网络门户使用 `Adobe` 框架以及 `ESRI` 的 `ArcGIS API for Flex` (ESRI, 2012) 实现。`CLIPS` 框架采用三层客户端-服务器技术设计并实现（图 3.3），包含一个支持用户与系统交互的顶层用户界面；一个提供开发、监控和分析等过程管理服务的中间层；以及一个提供数据库管理功能并专门用于数据和服务服务的第三层。客户端界面使用 `Flex` 开发，服务器端使用我们自定义的工具，这些工具由 `LaTools` (LaTools, 2006）等开源产品和其他特定的空间技术构建。

![](img/7c79e82750415aed3dd6b437e48a8d77_59_0.png)

图 3.3 本研究开发的 `CLIPS` 总体架构。

# 大数据

![](img/7c79e82750415aed3dd6b437e48a8d77_60_0.png)

图 3.4 `CLIPS` 用户界面。

## 3.3 结果

项目开发的 `CLIPS` 用户界面如图 3.4 所示。在预处理阶段，用户可以调用数据削减算法（例如顶点精简方法）、裁剪和合并原始数据、启动用户指定的下载工具。顶点精简功能使用户户减少数据量（Orysspayev 等人，2012）。在后处理期间，用户可以选择从不规则三角形网（`TIN`）或点云创建 `DEM`，合并并裁剪 `DEM`，并从 `DEM` 或 `TIN` 派生二次产品（生成等高线，以及坡度和坡向）。

处理界面还允许用户选择项目预定义的计算机基础设施（例如 `EC2` 实例类型：`large`、`XLarge` 和 `double xray`）或针对其特定问题指定处理器配置。表 3.1 提供了这三种实例类型的高级规格。每个实例作为处理器、内存和存储容量的详细规格见 `http://aws.amazon.com/ec2/instance-types/`。为了演示处理流程，下一节提供了一个应用示例。

### 表 3.1

`EC2` 实例类型规格

| | Large | XLarge | 2Xlarge |
|---|---|---|---|
| 内存 (GB) | 7.5 | 15 | 30 |
| 存储 (GB) | 850 | 1690 | 弹性块存储 |
| I/O 性能 | 中等 | 中等 | 高 |
| 平台 | 32 位 | 32 位 | 64 位 |

### 3.3.1 应用示例：使用大型 LiDAR 数据集生成 DEM

在这个示例中，我们演示了 `DEM` 生成过程的全流程，从用户如何从 `CLIPS` 网络门户选择 `LiDAR` 数据，到如何在所使用的商业云计算站点上进行处理（图 3.5）。在典型场景下，用户 (1) 从地图上选择感兴趣区域，(2) 提供 `Amazon Web Services (AWS)` 凭证登录 `AWS` 服务，(3) 选择将使用的 `AWS` 实例类型（计算机资源），(4) 选择首选的处理器类型（例如 `CPU` 或 `GPU`），(5) 指定所需的产品（例如 `TIN`、坡度或等高线），以及 (6) 指定用于处理完成通知的名称和电子邮箱地址（图 3.5）。在用户在客户端侧的用户界面上提供了所需信息后，`LiDAR` 数据将被推送到 `Amazon` 云存储，然后使用用户指定的参数，利用我们在 `EC2` 环境中实现的软件生成 `DEM` 和其他衍生产品。最后，在处理完成后，将向用户发送电子邮件通知，并附上下载链接。

为了测试性能和处理时间，我们使用了 18 种数据集和处理器配置的组合：三种地形数据（平坦、起伏、城市）、瓦片大小（`9` 和 `25`）以及三种 `EC2` 实例类型（`large`、`Xlarge` 和 `double Xlarge`）。图 3.6 描述了不同组合的处理时间。正如预期的，该图显示随着计算机功率

![](img/7c79e82750415aed3dd6b437e48a8d77_61_0.png)

图 3.5 生成 `DEM` 和衍生产品的用户界面。

从 `Xlarge` 增加到 `X2Large`，起伏地形数据比其他两种地形需要更多时间。这些结果清楚表明，城市瓦片消耗的时间比平坦地形更多。

![](img/7c79e82750415aed3dd6b437e48a8d77_62_0.png)

**图 3.6** 本使用的不同计算机资源的时间和性能对比。

处理时间最长的组合是使用最小处理器配置的起伏地形大区块（`5×5`）；合并瓦片并将其转换为 `DEM` 需 `8` 分钟 `12` 秒。然而，作为一种权衡，它是最具成本效益的，处理费用为 `34` 美元。在使用 `EC2` 服务时，任何部分小时都计为一整小时。本研究中各种组合的比较清楚表明，即使使用不同类型的 `25` 瓦片，每个请求也小于小时，处理费用低于 `1` 美元。从 `TREE` 服务器上传数据到云存储的费用低于 `50` 美元。由于涉及成本，我们没有使用 `Amazon` 云设施存储整个州的数据资源，尽管存储成本的下降可能意味着我们可以在不久后再次考虑这一点。在 `Amazon` 云上测试数据的总成本低于 `100` 美元，这对我们任何人来说都是负担得起的。

### 3.3.2 启发式模型开发

基于对不同实例、瓦片大小、地形类型、处理时间和成本的教训，我们开发了两个启发式模型为用户提供一个原型推荐系统：(1) `LiDAR` 数据削减和 (2) 各地形类型的最佳计算机基础设施分配（图 3.5 和 3.7）。

`LiDAR` 数据削减系统使用顶点精简方法来减少 `TIN` 的密度（Oprayev 等人，2012）。顶点精简方法最初由 Schneider 等人 (1992) 提出，反复检查每个顶点对表面模型渲染的显著性。对每个待考虑的顶点根据其定义的三角形数量以及用于精简该顶点的角度阈值进行评估。例如，当六个三角形边的端点，其 `z` 值（高度）与其他顶点有显著差异时。

# 使用云环境处理大型 3D 空间数据集

![](img/7c79e82750415aed3dd6b437e48a8d77_63_0.png)

**图 3.7** 为 `CLIPs` 中的 `LiDAR` 处理开发的启发式模型。

将被保留的边缘末端。另一方面，完美定义了四个三角形且 `z` 值差异极小的顶点是变形的候选对象。

为了开发该启发式模型，我们使用从 `110` 到 `180` 度以 `2` 度为增量的角度范围，评估了平坦和起伏地形的抽稀率。对于每次角度缩减，都与原始 `DEM`（无缩减）一起生成一个 `DEM` 以进行精度估计。这两个 `DEM` 之间的均方根误差（`RMSE`）使用以下公式计算：

```
$RMSE = \sqrt{\sum_{i=1}^{n}(X_{Original,i} - X_{Obtained,i})^2 / n}$
```

其中

$n$ 是栅格中的单元格数量

$X_{Original,i}$ 是原始值

$X_{Obtained,i}$ 是单元格 $i$ 的获取值

图 3.5 显示了对于两种地形类型，`RMSE` 值如何随使用角度的变化而减少。它还显示这有助于用户为其应用找到最佳的推荐选择和可接受的 `RMSE` 值。

第二个推荐系统根据地形类型、愿意投入资金以及希望在云环境中完成任务的速度，为用户提供最佳实例和处理器配置。为了开发该启发式模型，我们使用了来自平坦和起伏地形的 `LiDAR` 数据、云平台上的 `GPU` 和 `CPU` 配置，以及在云端处理数据的预计时间和成本（图 3.7）。我们的目标仍然是帮助新手用户指定合适的计算机配置，使其能够在云端处理 `LiDAR` 数据并在时间与费用之间进行权衡。

## 3.4 结论

我们成功地利用云计算开发并实现了一个基于 Web 的 `LiDAR` 数据处理系统。我们使用 `Amazon` 的 `EC2` 服务测试了三种不同计算机资源配置的 `LiDAR` 数据。对于 `5 x 5` 瓦片，起伏数据集比其他类型花费更多时间，而本研究使用的 `3 x 3` 瓦片中，城市地形的计算强度最高。我们的结果清楚表明，随着计算能力的增加，三种类型的 `LiDAR` 处理时间均有所减少。我们的方法在所研究的配置范围内具有扩展性。然而，研究区域的时间和点密度也是影响 `LiDAR` 数据性能的重要因素。无论实例类型和其他因素如何，总成本都是适中的（小于 `100` 美元）。此外，根据从不同类型的实例、尺寸、地形、处理时间和成本中学到的经验，我们开发了两个用于 `LiDAR` 数据抽的启发式模型。这些方法整合到用户界面中，使新手能够探索云环境中各种类型地形的适当基础设施分配。

# 致谢

本研究在 `Amazon Research` 和 `USGS-AmericaView` 项目的支持下进行。

## 参考文献

Ackermann, F. 1999. Airborne laser scanning-present status and future expectations. IPSRS Journal of Photography and Remote Sensing, 542, 64–67.

Ambercore. 2000. Transport aerial services—A white paper on LiDAR mapping. http://www.ambercore.com/files/TransportWhitePaper.pdf (accessed on May 4, 2011).

Anderson, E. S., Thompson, I., and Austin, S. 2005. LiDAR data and linear interpolator over elevation estimates. International Journal of Remote Sensing, 2618, 3889–3990.

Arnbust, M. F., Gough, R., Joseph, D. A., Katz, K., Konwiski, A., Lee, G., Patterson, D. A., Rabkin, R., Stoica, I., and Zhou, M. 2009. The Clouds: A View of Cloud Computing, Technical Report No. UCB/ECS-2009-28, University of California at Berkeley, California.

Balvasais, E. P. 1999. A comparison between photogrammetry and laser sensing. IPSRS Journal of Photography and Remote Sensing, 52, 83–94.

Campeau, L., and Haas, M. 2003. Light detection and ranging-based terrain—a concept. In Proceedings of the 16th International Technical Meeting of the Satellite Division of the Union, Portland, OR, September 9–12.

Chen, Q. 2009. Improvement of the edge-based method for lidar data. International Journal of Remote Sensing, 304, 1069–1074.

Cui, D., and Zhang, Q. 2010. Massive data processing based on cloud computing model, Computational Science and Optimization, 3rd Annual Conference on Computational Science and Optimization, 347–350.

ESRI. 2012. ArcGIS Server. http://www.esri.com/software/arcgis/arcserver.

Evangelinos, C., and Hill, N. 2008. Cloud computing for scientific applications: Feasibility of running coupled-atmosphere models on Amazon’s EC2, In Proceedings of the 1st Workshop on Cloud Computing and its Applications, Chicago, October 22–23.

Hanh, S., He, J., Joon, H., and Yu, K. 2009. Parallel processing for airborne laser scanning using a PC cluster and virtual grid. Sensors, 94, 2555–2573.

Hodgson, M. E., Jensen, J., Raber, G., Tullis, J., Davis, B., Thompson, G., Schuckman, C. 2005. Evaluation of lidar-derived elevation and terrain slope in off-grid conditions. Photogrammetric Engineering and Remote Sensing, 71–77.

Hodgson, M. E., Jensen, J. R., Schmidt, L., Schill, S., and Davis, B. 2003. Evaluation of LIDAR-derived elevation models in off-grid conditions with USGS Level 1 and Level 2 DEMs. Remote Sensing of Environment, 84, 295–308.

Huang, Q., Yang, C., Ebert, D., Liu, K., and Wu, H. 2010. Cloud computing for geosciences: Deployment of GEOSS on ACM SIGPG: Performance and Distributed Geographic Information Systems, New York, pp. 35–38.

IBM. 2012. Big data to bring to the era. http://www.ibm.com/software/data/bigdata/ (accessed on April 4, 2013).
