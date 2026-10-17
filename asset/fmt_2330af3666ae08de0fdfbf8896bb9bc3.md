
在表 5.2 中，我们讨论了一些基于云和学习算法的相关工作。

### 5.7 结论

该工作展示了利用自然启发算法和机器学习算法进行资源分配领域的当前最先进工作。比较表明，使用 `ANN`、`RNN` 或随机森林的基于机器学习的算法优于现有的自然启发算法和元启发式算法。该工作展示了各种问题和性能参数。该工作为研究人员提供了云中资源分配领域当前最先进工作的综述。

### 参考文献

1. Peter Mell, and Timothy Grance, "The NIST definition of cloud computing." Sep, 2011. [`csrc.nist.gov/publications/nistpubs/800-145/SP800-145.pdf`](http://csrc.nist.gov/publications/nistpubs/800-145/SP800-145.pdf)

2. Gartner Research, [`www.gartner.com/it-glossary/cloud-computing/`](http://www.gartner.com/it-glossary/cloud-computing/)

3. Reshmi, R., and D. Shanthi Saravanan. "Load prediction using (DoG–ALMS) for resource allocation based on IFP soft computing approach in cloud computing." *Soft Computing* 24, no. 20 (2020): 15307–15315.

4. Akki, Praveena, and V. Vijayarajan. "Energy efficient resource scheduling using optimization based neural network in mobile cloud computing." *Wireless Personal Communications* 114 (2020): 1785–1804.

5. Jeddi, Sima, and Saeed Sharifian. "A hybrid wavelet decomposer and GMDH-ELM ensemble model for network function virtualization workload forecasting in cloud computing." *Applied Soft Computing* 88 (2020): 105940.

6. Chudasama, Vipul, and Madhuri Bhavsar. "A dynamic prediction for elastic resource allocation in hybrid cloud environment." *Scalable Computing: Practice and Experience* 21, no. 4 (2020): 661–672.

7. AbdElminaam, Diaa Salama, Ahmed A. Toony, and Mohamed Taha. "Resource allocation in the cloud environment based on quantum genetic algorithm using Kalman filter with ANFIS." *IJCSNS* 20, no. 10 (2020): 10.

8. Chen, Shengkai, Shuliang Fang, and Renzhong Tang. "An ANN-based approach for real-time scheduling in cloud manufacturing." *Applied Sciences* 10, no. 7 (2020): 2491.

9. Hasan, Md, Md Almamun, and Shawkat Akbar. "An intelligent machine learning and self adaptive resource allocation framework for cloud computing environment." *EAI Endorsed Transactions on Cloud Systems* 6, no. 18 (2020).

10. Kholidy, Hisham A. "An intelligent swarm based prediction approach for predicting cloud computing user resource needs." *Computer Communications* 151 (2020): 133–144.

# 基于机器学习的预测模型

人工智能与机器学习的区别在于：人工智能以智能方式完成任务，而机器学习为机器提供数据使其自我学习。机器学习的扩展版本是深度学习，它利用神经网络和其他方法模拟人脑活动，应用于目标检测、目标识别、语音识别、语言翻译和决策制定。正如 Dey (2016) 在 *machine learning algorithms* [\[10\]](#index_split_002.html#p130) 中所观察到的（图 6.3），机器学习进一步分为三类：监督学习、无监督学习和强化学习。

![Image 46](img/index-113_1.jpg)

**图 6.3** 云中的机器学习方法。

机器学习中的预测模型是指能够利用过去或当前的可用数据提前预测事件发生的模型。神经网络、逻辑回归、随机森林和决策树是应用于云应用以提升现有系统性能的一些机器学习预测模型；例如，正如 Nikravesh 等人 (2017) 在 *autonomic prediction suite* [\[11\]](#index_split_002.html#p130) 中所述（图 6.4），决策融合技术和结构风险最小化被用于云应用中的资源可用性预测。

![Image 47](img/index-114_1.jpg)

![Image 48](img/index-114_2.jpg)

**图 6.4** 预测模型的工作原理。

**图 6.5** 云性能指标。

云计算涉足多个领域，如多云策略、超大规模数据中心、云安全、云备份与检索、基于云的网络服务和无服务器架构。云应用是指部署或开发在云环境中的软件或应用，而非托管在本地环境或机器上。为了提升云应用性能，研究人员随时间开发了大量算法。本章将讨论此类算法及其与现有框架的对比结果（图 6.5）。

投资回报率（ROI）是一种绩效衡量指标，用于评估或比较投资效率。正如 Skilton (2010, p.22) 在 *ROI from cloud computing* [\[12\]](#index_split_002.html#p130) 中所述，ROI 包含云计算 ROI 模型以高效完成此任务；为评估 SaaS 中云应用的性能，存在关键性能指标（KPIs）。KPIs 以云计算与传统 IT 及云计算解决方案为对比目标。正如 Lin (2013) 在 *performance indicator evaluation* [\[13\]](#index_split_002.html#p130) 中所述，云中的主要 KPIs 包括时间、成本、质量和盈利能力或利润率。本文将讨论三个云 KPIs：时间、成本和质量。

三种时间 KPIs 模型在决定 SaaS 中应用性能方面起关键作用：平均响应时间、最大响应时间、响应时间失败率。这三者均属于服务响应时间类型。平均响应时间应最小化，以提供 SaaS 中云应用的增强性能。下一个 KPI 是成本。成本取决于两个因素：获取成本和持续成本。云服务提供商为单项服务提供不同功能并定价是一大挑战。同一云服务提供商可能提供满足不同用户需求的不同 VM。最后一个 KPI 是质量。云服务质量取决于四个属性：相关性、实用性与可计算性、一致性和区分能力。正如 Garg (2013) 在 *future generation computer systems* [\[14\]](#index_split_002.html#p131) 中所述，每个属性在云弹性、准确性、透明度、适用性、可靠性、可用性、吞吐量和效率中均发挥着关键作用。

根据 NIST 定义，云模型具有五个基本特征、三种服务模型和四种部署模型；具体解释如下。

#### 6.1.1 基本特征

根据 NIST 定义，云的五个基本特征如下：

*   On-demand self-service（按需自助服务）。
*   Broad network access（广泛的网络访问）。
*   Resource pooling（资源池化）。
*   Rapid elasticity（快速弹性）。
*   Measured service（可度量服务）。

Source: Based on 'The NIST Definition of Cloud Computing', Special Publication 800-145, NIST, US [\[21\]](#index_split_002.html#p131).

#### 6.1.2 云交付/部署模型

根据 NIST 定义，云模型分为四种模型 [\[21\]](#index_split_002.html#p131)（图 6.6）：

![Image 49](img/index-116_1.jpg)

**图 6.6** 云部署模型。

*   **Public cloud（公有云）**：由第三方提供商提供。所有人均可通过互联网访问。公有云扩展迅速，访问便捷。维护由服务提供商负责。资源共享导致安全性、灵活性和对云环境的控制力降低。例如 `Amazon EC2` 和 `Google App Engine`。
*   **Private cloud（私有云）**：顾名思义，这是一种专用云服务，资源由单个实体或组织独占使用。由于资源不共享，提供高安全性。对云环境具有高灵活性控制权。比公有云昂贵，因为服务和维护须由组织自行负责。例如 `VMware`、`Microsoft`、`KVM` 和 `Xen`。
*   **Hybrid cloud（混合云）**：也称为“两全其美”。结合了公有云和私有云的最佳特性。提供更大灵活性、高安全性、更多功能、更多部署选项，且支持云爆发。成本较高，网络复杂。例如 `IBM`、`HP`、`Vmware`、`vCloud` 和 `eucalyptus`。
*   **Community cloud（社区云）**：集成不同类型的云以实现共同目的。社区云提供高安全性、可靠性和性能。可扩展性有限，成本较高。例如 `SolaS` 和 `VMware`。

#### 6.1.3 云服务/模型类型

正如 Mell (2011) 在 *NIST definition of cloud computing* [\[21\]](#index_split_002.html#p131) 中定义的三种云服务：IaaS、PaaS 和 SaaS，分别侧重于硬件、系统软件和应用（图 6.7）。

![Image 50](img/index-117_1.jpg)

**图 6.7** 云服务控制对比。

*   **Software as a service (SaaS)**：通过互联网按需提供软件应用。用户无需在本地机器安装。用户可通过 Web 浏览器访问软件。用户无法控制应用，只能使用。所有维护和更新由提供商处理。
*   **Platform as a service (PaaS)**：指提供创建、测试、开发和部署产品应用环境的云管理。客户可在给定平台上引入和控制应用。PaaS 包含服务器、数据库、网络和开发工具等管理服务。
*   **Infrastructure as a service (IaaS)**：将整个基础设施作为服务提供，可在互联网上快速扩展，按使用付费。用户可购买、安装、配置和管理自己的产品、应用和软件、操作系统及任何应用，而基础设施由服务提供商管理。

![Image 51](img/index-118_1.jpg)

# 基于机器学习的预测模型

### 6.2 云计算挑战

云计算是一项独立的技术，用于管理资源以及信息的处理与监管。维护透明度、云计算的一致性面临着挑战和困难，且这些挑战日益增加。云计算可能面临资源优化、扩展、安全、维护等问题。

图 6.8 中 Rightscale（2018）的一项调查显示了云计算面临的挑战。

显而易见，云计算安全面临重大挑战，紧随其后的是云计算领域的其他挑战。为了提升云计算的运行效能，必须通过更好的解决方案克服所有这些挑战。

### 6.3 文献综述

### [1]

Raza 等人（2019）提出了一种用于比较分析的机器学习模型，其中讨论了 11 种机器学习分类方法。在其中一种机器学习方法中，应用了 Friedman 检验和 Nemenyi 事后检验，以识别分类器在训练数据集上十折交叉验证期间的性能差异，从而确定所有机器学习方法的最佳参数以获得最优解。SaaS 是云应用中基于应用的服务。

### [2]

Ahmed 等人（2018）提出了一种利用并行粒子群优化的优化模型来提高虚拟机性能的模型。该方法讨论了线性回归和神经网络机器学习方法，以实现虚拟机性能的提升。结果表明，与现有模型相比，所提模型针对基于云计算的高性能计算系统（HCS）中的慢性肾脏病，结果提升了 64%。

### [3]

Kirchoff 等人（2019）提出了监督机器学习工作负载预测技术，在各种云环境和配置下比较了 ARIMA、MLP 和 GRU 三种机器学习方法。获得的结果表明，这三种方法均适合短期预测。ARIMA 需要大量样本才能计算出最优结果，且耗时较长。在使用灵活性、对样本数量的敏感度、执行时间和准确性方面，GRU 在三者中取得了最佳结果。

### [4]

在文献 [4] 中，Esfahani 等人（2015）提出了一种基于知识的自适应调度器，利用定制的决策树算法进行资源分配，以最小化 SLA 违规并最大化利润。与之前的研究工作相比，该方法实现了 38.4% 的成本节约。

### [6]

Borkowski 等人（2016）提出了一种利用 ANN 反向传播机器学习预测模型来预测云资源利用率性能改进的方法。预测模型基于历史数据和真实世界数据集构建。评估结果显示，与简单回归方法相比，该方法提高了准确性。结果表明，对于中位数情况，该方法将预测误差降低了 20%；对于最佳情况，使用所提模型获得的预测误差减少了 89%。

### [7]

Alkalbani 等人（2016）在文献 [7] 中引入了五种监督机器学习预测方法，用于预测 SaaS 在线客户评论的情感。结果显示，使用支持向量机五折交叉验证方法获得了 92.37% 的准确率。与其他模型相比，该方法效果最佳。

### [8]

Tripathy 等人（2020）在文献 [8] 中提出了一种利用机器学习分类器针对 SaaS 进行 SQL 注入攻击检测的方法。使用五个特征时，该方法获得了 99.3% 的检测准确率；使用七个特征配合 AdaBoostClassifier 时，获得了 99.4% 的检测准确率。

### [15]

Sharkh 等人（2020）利用 TU Delft Bitbrains 追踪数据集，通过在数据集上应用机器学习方法，提出了一种新的云性能预测技术。预测的任何改进都会直接影响云客户和提供商的 KPI。线性回归方法针对平均绝对百分比误差磁盘写吞吐量产生了最优结果。支持向量机（SVM）学习方法针对均方根误差、网络接收吞吐量和网络发送吞吐量产生了最优结果，从而改善了云数据中心的云资源调度。

### [17]

Pandita 等人（2020）提出了一种神经网络机器学习故障预测模型方法。采用贝叶斯正则化人工神经网络方法预测应用性能，所提模型在 Google Cloud 选定数据集上获得的结果为 97.6%。

### [18]

Govindraju 等人（2020）提出了一种回归树模型，以获得虚拟机启动时间的性能准确率。使用 OpenStack 测试环境计算所提模型的效率。该模型以 91.81% 的平均准确率预测了虚拟机的启动时间。

### [19]

Shetty 等人（2020）在文献 [19] 中提出了一种针对云环境中医疗数据的监督机器学习预测方法，重点关注两个领域。第一，医疗领域算法的分析。预测模型在准确率、精确率、F1 值和召回率等性能指标上进行测试。计算结果显示，在其他监督机器学习方法中，随机森林预测模型获得了最佳结果。

### [20]

Sergue（2020）在文献 [20] 中提出了一种用于 SaaS 云服务模型的机器学习预测模型，采用线性回归和随机森林方法。对于特定场景，非线性随机森林回归技术获得的结果优于线性回归技术。

### [22]

Madni 等人（2020）提出了一种基于模糊理论和布谷鸟搜索的模糊布谷鸟搜索技术，以解决实时优化问题。在 IaaS 云中，FCS 解决了可靠性感知的资源调度问题。FCS 技术与遗传算法（GA）、蜜蜂算法（HB）和粒子群优化（PSO）进行了比较。结果显示，在故障率方面，FCS 比 GA、HB 和 PSO 产生了好 39.21% 的结果。

### [23]

Chen 等人（2020）提出了一种利用 QoS 预测模型和 PSO 运行时决策算法模型的自适应资源分配方法。使用相同的历史数据，该方法产生了好 15% 的结果。云应用资源分配的有效性提高了约 5–6%。

### [24]

Shahidinejad 等人（2020）提出了一个框架，该框架使用学习自动机作为决策者，将传入的动态工作负载卸载到云服务器上。另一种方法提出了一种边缘服务器供给方法，利用长短期记忆模型估算未来工作负载，并利用强化学习技术做出适当的扩缩容决策。

结果表明，所提出的框架提高了 CPU 利用率，并减少了执行时间和能耗。

### [25]

Hasan 等人 (2020) 提出了一种基于机器学习的自适应资源分配框架，以解决多维云资源中的问题。作者对资源分配框架中的 QoS 预测模型、改进蝙蝠算法 (IBA)、节能模型 (EEM)、改进上校选择算法 (MCSA) 和增强循环神经网络 (ERNN) 机器学习方法进行了比较。

(*续*)

**106** ◾ ML 和优化模型

**内容**

16
