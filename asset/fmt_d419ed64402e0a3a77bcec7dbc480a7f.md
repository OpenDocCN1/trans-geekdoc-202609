
[1] 简要讨论了云计算系统的基本架构。它们是硬件层、基础设施层和应用层。作者还讨论了网格计算、混合云。[ [2] 作者在 2008 年讨论了[相关内容（原文不全）。][ [3] 作者描述了云计算的演变。[ [4] 作者还描述了其优点和缺点。[ [5] 作者提议了一种具有四个模块的算法。[ [6] 作者讨论了最流行的云平台，如 `OpenStack`、亚马逊云服务（Amazon Web services）。[ [7] 他从普通用户的角度进行了讨论。[ [8] 作者提出了一个部署在 `Firebase` 中的系统，使用 `Maps API` 和 `MySql` 数据库形成一个框架，用于获取医生和患者的实时数据。[ [9] 作者考虑了最流行的云存储服务，如 `Google Drive`, `Dropbox`，并将其实现到具有最大吞吐量和带宽的连接中。

云盘、`Mega` 以及如 `Wuala`、`Horizon` 等私有云服务器。本文针对下载、上行、分块（`Chunking`）、客户端去重等不同维度对这些服务进行了分析和基准测试。整体而言，作者将时间作为基准因素，因为大多数用户在基准统计中不会感知到这一点。到服务器的距离也是一个主要因素，因为延迟可能会随距离而变化。作者得出结论说，在一种测试用例中 `Online` 的结果最佳。在 [10] 中，作者比较了 `Google Drive`、`Microsoft Azure` 等云服务。测量是基于下载、上行、客户端和去重的。在作者产生的所有测试中，其得出了最优结果。在 [11] 中，作者讨论并提供了几个使 `WebRTC` 更具动态性的解决方案。`WebRTC` 是一个开源项目，允许开发者通过 `API`（应用程序编程接口）实现视频和音频通话。在 [12] 中，简而言，作者提出了管理网络拥塞边界的部分解决方案。作者提出了一个处理数据丢包和视频抖动的系统。作者还使用 `Firebase API` 进行身份验证，使用 `RDBMS` 数据库以及与医生进行会议。该系统被开发为 `Android` 应用程序。在 [13] 中，作者讨论了当我们连接两或多台计算机进行对点（`P2P`）直播视频流服务的情况。视频流有两种类型，我们称之为对点（`P2P`）连接。按需直播是同步连接，而按需播放是非同步连接。与传统电视和卫星通道相比，体验质量受到限制。在该通道中，`P2P` 启动时间较长，且通道存在明显的延迟。在 [14] 中，作者建议对 36 名资深医护人员进行调查，涵盖了他们在诊所和通过视频会议中受益的场景。作者最后结论说，在大多数场景下，通过视频通话进行住院的经济价值很高。在 [15] 中，作者提出了一种改进的 `JPEG` 的高效压缩算法。`PSR`（峰值信噪比）使用测试中使用的彩色和灰度图像进行计算。在 [16] 中，作者提出了一个允许高效传输消息（文本+ 文本）和媒体的框架或系统。作者还实现了 [15] 中的 `LRJPEG` 压缩算法，以压缩并跨网络发送图像。该系统利用 `Firebase API` 来验证用户身份并存储信息。在 [17] 中，作者涵盖了一个云框架，它可以在不同规模上合并数据并与云引擎同步。它是一个具有有用设计和支持该系统的特征集成框架。在 [18] 中，详细介绍了云计算如何促进与医疗相关的各种数据类型、存储、分析以及从存储的医疗数据中推断结论。作者还给出了医疗保健领域云计算技术的提议方法和未来。基于云和物联网的系统还充当数据共享的骨干，极大地有助于开发高效的医疗应用引擎。[19] 云系统通过分析数据并使用所提框架工作作为风险预防系统。该系统具有数据处理模块和带有机器学习的数据分析模块，作为决策支持系统工作。[20] 云隐私框架在区块链环境的帮助下工作，确保高安全和重要数据的隐私。[21] 文献综述涵盖了许多云系统和用于存储和共享数据的云平台。但数据需要高效传输，特别是当涉及到图像和视频时。所提工作侧重于图像压缩并将其高效传输到基于云的系统以处理结果并方便地做出决策。论文的下一节讨论了用于构建所提框架的各种类型工具。机构将列在作者姓名下方。

## 3 开发中使用的工具

### 3.1 LRJPEG

一种基于亮度的 `JPEG-LRJPEG` 方法是一种可以帮助我们无损压缩图像的算法。该算法计算 `CR`（压缩率）、`PSNR`（峰值信噪比）和 `MSE`（均方误差）。压缩率（`CR`）是发生压缩的比例或量。计算 `CR` 是为了分析图像大小的变化来分析系统的效率。`PSNR` 和 `MSE` 是用于评估图像压缩质量和性能的两个误差标准。`MSE` 显示了原始图像与压缩图像之间的累积平方误差，而 `PSNR` 显示了峰值误差值。

### 3.2 Firebase

`Firebase` 可以被称为 `BaaS`（后端即服务）。任何 `BaaS` 都能让开发者停止担心管理服务器或后端 `API`。这使得开发者能够专注于改进用户体验。简而言之，`Firebase` 让开发者能够更快地设计和开发应用程序。`Firebase` 提供了许多功能，如身份验证、云函数、数据库、文件存储、云消息。在消息中，所有这些功能都与 `Gmail` 账户集成。当我们实现所有这些功能时，就可以开发并部署一个高效的应用程序。`Firebase` 还为开发者提供了应用程序增长的深度分析和统计。

### 3.3 OpenTok SDK

`OpenTok SDK` 由 `TokBox Inc.` 开发和维护。他们是一家基于 `PaaS`（平台即服务）的公司。`TokBox` 维护的服务器端 `SDK` 和客户端 `SDK` 使我们能够在不关注后端服务器的情况下将实时视频通话集成到应用程序中。`OpenTok` 的 `WebRTC` 支持 `Android`、`Javascript` 和 `IOS`。`OpenTok` 的基本服务由公司免费提供。然而，视频通话等高级功能需要付费。因此，我们正在利用免费服务并对获得的数据进行分析，以检查结果是否理想。下一节讨论了所提系统的架构。

## 4 所提系统的架构

所提系统的架构描绘了系统中存在的关键元素。该系统集成了与医疗和存储相关的各种数据类型、分析以及从存储的医疗数据中推断结论。作者还给出了医疗保健领域云计算技术的提议方法和未来。基于云和物联网的系统还充当数据共享的骨干，极大地有助于开发高效的医疗应用引擎。云系统通过分析数据并使用所提框架工作作为风险预防系统。该系统具有数据处理模块和带有机器学习的数据分析模块，作为决策支持系统。

## 5 所提系统的方法论

系统的工作从急救员模块开始。

### 5.1 急救员模块

在急救车上的急救员将有一个 `Android` 应用程序，使能够与坐在桌前的医生互动。该系统开发为 `Android` 应用程序。在 [13] 中，作者讨论了当我们连接两或多台计算机进行对点（`P2P`）直播视频流服务的情况。视频流有两种类型，我们称之为对点（`P2P`）连接。按需直播是同步连接，而按需播放是非同步连接。与传统电视和卫星通道相比，体验质量受到限制。在该通道中，`P2P` 启动时间较长，且通道存在明显的延迟。

### 5.2 医生端

医生在根据急救员传输的输入判断患者状况也起着至关重要的作用。在医院的医生也将有一个 `Android` 应用程序，访问访问上传的照片。照片将按照上传的时间顺序存储。医生还可以使用视频通话功能与急救员互动。这有助于医生获取患者的视觉信息。

### 5.3 后端/Firebase 和压缩模块

由于时间在患者运输过程中是一个主要因素，系统利用了 `LRJPEG` 图像压缩算法，该算法可以在不丢失清晰度的情况下高效压缩图像，从而使图像能够快速上传到服务器。急救员和医生的登录由 `Firebase` 中的身份验证模块处理。所有用户信息都以层级方式存储在 `Firestore` 中。当数据传输到 `Firebase` 服务器时，几乎没有数据丢失。用户登录信息在存储到服务器之前会通过 `Firebase API` 进行哈希处理，安全性极高。

# 结果与讨论

为了进行测试，首先按照方法论所述创建了一个移动应用程序并将其连接到免费基础引擎。然后执行参数化模块的操作，并收集和测试数据。为了测试压缩功能，随机选择了并加载了图像。下面列出了压缩前后图像大小的统计数据。测试结果结果已绘制在下表1中。

表 1. 随机测试图像压缩前后的结果。

| 图像编号 | 压缩前 | 压缩后 |
| --- | --- | --- |
| 图像 1 | 4.53 MB | 534 KB |
| 图像 2 | 2.62 MB | 175 KB |
| 图像 3 | 2.10 MB | 126 KB |
| 图像 4 | 6.23 MB | 934.5 KB |
| 图像 5 | 8.06 MB | 1.01 MB |
| 图像 6 | 1.45 MB | 233.870 KB |

压缩率的计算公式如下，我们可以看到未压缩图像与压缩图像的比例计算方式：

> $Compression ratio(CR) = \frac{Uncompressed image size}{Compressed image size} (1)$

为了理解比例，下面对所选的各种图像进行了计算：

> $CR \text{ 图像 1 = \frac{4.53 * 1000}{534} = 8.4831 (2)$

> $CR \text{ 图像 2 = \frac{2.62 * 1000}{175} = 14.971 (3)$

> $CR \text{ 图像 3 = \frac{2.10 * 1000}{126} = 16.667 (4)$

> $CR \text{ 图像 4 = \frac{6.23 * 1000}{934.5} = 6.667 (5)$

> $CR \text{ 图像 5 = \frac{8.06}{1.01} = 8.514 (6)$

> $CR \text{ 图像 6 = \frac{1.45 * 1000}{233,870} = 6.202 (7)$

如公式所示，各种图像的压缩率及其传输率让我们理解，压缩在图像上的工作效果非常好，这绝对有助于图像的更快速传输。

图 4 用柱状图显示了所有测试图像的压缩率 (`CR`)。在这里我们可以看到压缩率在 5% ~ 20% 之间波动。上传压缩图像的时间与上传未压缩图像的时间之间差异巨大。考虑到图像质量损失非常小且肉眼无法察觉，对于使用 `OpenTok API` 发布和订阅的流的深度统计数据对开发者也是提供的，这是有助于快速处理数据、图像和视频且无队列限制的主要功能。

## 压缩率 (KB)

![](img/a35f8e852e0ee65e528c95ad0821783b_131_0.png)

图 4. 各种图像的压缩率。

上表的表 2 显示了基于用户交互的使用统计数据。每个账户持有者都有唯一的 `ID`，并可以创建同样用 `ID` 标识的项目，每个用户将拥有他们在应用程序使用的流类型或路由，这些都记录在云端。表 2 的结果获取自云仪表板 `API`，该 `API` 根据使用统计数据改进系统。所提的 `API` 借助图像压缩有助于更快地上传和下载数据，这在远程医疗方法中是非常需要的。因此，该系统是一个交互数据传输的有用框架。

表 2. 来自 `API` 的图像流使用统计数据。

| 账户 ID | 项目 ID | 类型 | 使用量 |
|---|---|---|---|
| 3574702 | 4628262 | 小时 | 0.34166667 |
| 3574702 | 4628262 | 流订阅分钟 | 17.95 |
| 3574702 | 4628262 | 流订阅路由分钟 | 17.95 |
| 3574702 | 4628262 | 会话分钟 | 17.9 |

## 7 结论

疫情和对远程医疗数据传输的需求产生了对数据共享的高效技术或交互式框架的需求。这项工作展示了一个通过 `API` 和压缩技术帮助进行数据共享的框架。该系统使交互的急救人员与现场患者连接起来，以共享数据或向医生进行直播，这有助于院前场景的处置。该系统是数据共享的一站式解决方案，通过在安卓 端和 `Open-tk` 服务器 `API` 上进行的实时实验，该系统提供了一个高效的交互框架来管理直播流视频，其速度与系统压缩框架一样快。实时系统的使用结果表明，它加速了数据共享，将有助于远程医疗和远程咨询。这项工作可以集成到医院管理系统中，通过用户友好的应用程序以及高效的存储和检索系统，非常有效地协助许多困难的院前或医院转运工作。

## 参考文献

- [1] Al-Dharabi, Y., Paraiso, F., Djaralla, N., & Merle, P. (2018). Elasticity in Cloud Computing: State of the Art. IEEE Transactions on Services.
- [2] Birman, K., Chocker, G., & van Renesse, R. (2009). Toward A Cloud Computing Agenda. ACM SIG News. https://doi.org/10.1145/15614.15612
- [3] Russkov, A. (2014). Shared Storage Performance of Cloud Computing: OpenNebula Nebula. In 2014 3rd International Conference on Cloud Networking, CloudNet 2014. https://doi.org/10.1109/CloudNet2014.06007
- [4] Wang, J., Peng, G., Xe, Y., & Fu, J. (2010). Cloud Storage As Infrastructure of Cloud Computing. In Proceedings - 2010 International Conference on Intelligent Computing and Cognitive Informatics, ICICI.
- [5] Prabhavathy, B., Priya, A., & own, K. (2013). Load Balancing Algorithm In 2013 4th International Conference on Cloud Communications, Technologies. https://doi.org/10.1109/tcc2013
- [6] Cimeone, A., Laurent, C., Sernov, V., Debre, C. (2016). Delay Reduced Multimedia Transmission in JPEG Algorithm to Improve Image Compression. WINA, 193–243. https://doi.org/10.1109/WAINA.
- [7] Li, Z., Guo, J., & Liang, C. (2008). A Survey on Peer-to-Peer Video Systems. 1–7.
- [8] Rahat, A., Parsa, I., & Babu, P. (2017). Real time experiment conducted with an android end Open-tk server API, 8–12.
- [9] Bocchi, E., Dario, L., & Mellia, M. (2015). Personal Storage. Transactions on Cloud. https://doi.org/10.1109/tcc.2015
- [10] Esposito, E., Dario, L., & Mellia, M. (2015). 554–764.
- [11] Johnson, A., Yu, S., & Singh, K. (2018). Telehealth Web in an Enterprise Era. 51(4), 48–54. https://doi.org/10.1109/MCOM.2018
- [12] Javad, M., Haleem, A., Raj, R. P., Sultan, S., and Khan, I.H. (2022). Evolutionary Trends in Cloud Computing: Challenges and Barriers.. Int. J. Cogn. Eng., vol. 3, pp. 124–135, Jun, 2022. https://doi.org/10.1016/ijce.2022.06.001.
- [13] Wade V.A., Karnon, A.G., & Heller, J.E. (2010). A Systematic Review of Economic Analyses of Telehealth Services Using Electronic Health Records. Health Research, 10
- [14] Mukhopadhyay, A., Shaj, R. P., & Raj, A. (2018). 2018 International Conference on Advances in Computing, Communications and Informatics, ICACCI 2018. https://doi.org/10.1109/ICACCI2018.85543
- [15] Mukhopadhyay, A., Shaj, R. P., & Raj, A. (2018). ICCACCI2018, 1313–1319. https://doi.org/10.1109/ICACCI2018.85540
- [16] Parekh M. & Saleena B. U. (2015). "Designing a Cloud Based Framework for HealthCare System and Applying Clustering Techniques for Region Wise Diagnosis," Procedia Comput., Vol. 50, pp. 537–542, Jan, 2015.
- [17] Hussein N.W., Hussain H.N. and Humod I.M., (2022), "A Proposed Framework for Healthcare Based on Cloud Computing and IoT Applications," Future. Gen.
计算科学的最新趋势 – Guraraj, Pooja & Flamminini (编)
