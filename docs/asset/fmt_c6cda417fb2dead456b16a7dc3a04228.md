
随着信息分析和移动计算的发展，这种方法已经准备好产生许多合理且便捷的规范和业务。此外，在机器学习、数据处理、人工智能以及其他先进技术的辅助下，健康规划系统可能会在不断演变的健康规划系统中作为创新源共同发挥至关重要的作用。本项目展示了由信息分析和移动计算辅助的战略性健康规划系统，其由信息资产层、信息管理层和服务层组成。本项目还介绍了一些支持该主题的代表性应用，这些应用已被验证或能够提供许多战略性、技能性和个性化的健康规划服务 [4]。

尽管本项目展示了一个由信息分析和计算辅助的战略性健康规划综合系统，但在未来的工作中，我们寻求纳入更多先进的技术，如心理特征计算、深度学习和有效计算，以提高服务标准和用户专业水平。训练、评估并检查模型以根据一组食材预测菜肴。预测负面公式——药物相互作用的概率以支持预期的应对；最后开发一个移动应用程序作为构建推荐系统的革命，该系统考虑用户偏好，最大化地提高食物中健康化合物的质量，并最小化地减少不健康成分。（例如，不要区分同一机构的不同部门）[14]

## 参考文献

- [1] [膳餐计划对食物选择、饮食质量和体重的影响发表于 Int J Behav Nutr Phys Act，作者 missionary Ducrot, Carline Méjean https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2528891_emeal_planning
- [2] [SmartDiet: 用于开发健康饮食的个人饮食权威，作者 Tim A, Samantha H. https://www.researchgate.net/publication/3221030630_SmartDiet_A_personal_diet_consultant_for_healthy_meal_planning
- [3] [通过优化自然启发的多目标饮食劣势推荐健康膳餐计划，作者 Connor J.K. https://journals.sagepage.com/doi/full/10.1177/1460458220976719
- [4] [建立膳餐/计划/设计(计划) *（主计划、证据、分析、链接）– Tom Hardy https://www.thinkrsrd.com/wp-content/uploads/2016/12/MEAL-Mendomic.pdf
- [5] Kanguto T., Mount D. M., Netanyahu N. S., Piatko C. D., Silvermin R., and Wu A. Y., "一种经济的 k-means 聚类算法：分析与实现., IEEE Trans. Pattern Anal. Mach., vol. 24, no. 7, pp. 881–92, Jul. 2002.
- [6] 营养信息 https://developer.nutrition.com/decouple-2
- [7] Tensorflow https://www.tensorflow.org/resource-learn-ml
- [8] 运动 https://developers.google.com/maps/documentation/home-workouts
- [9] W. Xu, J. He, and Y. Shu, "用于自编码器的深度学习用于健康预测," 见于 Proc. IEEE Symp. Sec Comput. Intell. (SSCI), Dec. 2020, pp. 42–49.
- [10] Firebase https://firebase.google.com/docs/getstarted?sAFp Tensorflow https://github.com/lutzeoer-
- [11] Deng, L., Hinton, G., and Kingsbury B., "用于识别和连接方面的新型深度神经网络：方面视图," 见于 Proc. Int. Conf. Acoust. Signal processing, 8569–8603.
- [12] 指南 https://developers.google.com/cooking/2150/comfort-food
- [13] Singh, S., Kumari, K., Rogathan, S., Raj K. D.; Anusha, N.; Sumizarchi A. 使用人工神经网络垃圾分类。HELIT 2017, 7, 2053–2058.
- [14] Ranada, P. 为什么菲律宾是世界第三塑料垃圾地。Rappler 博客。2015年10月6日检索。
- [15] Sousa, J.; Rebelo, A.; Cardoso, J. 使用深度学习自动垃圾分类。2019 IEEE 视觉通信与网络 (WYC), 2019, pp.43–48.
- [16] Biricanoglu, C.; Atay, M.; Besir, F.; Genç, O.; Kizrak, A. Recyclilent: 使用深度神经网络智能垃圾分类。2018 智能系统与应用 (INSTA)。IEEE, 2018, pp.1–7.
- [17] Yang, M.; Chung, G. 可回收状态垃圾分类，CS229 项目报告 2016, 2016.
- [18] Lucas, D.G.C. 来自尺度不变关键点的独特图像特征。计算机视觉杂志 2004, 60, 91–110.
- [19] Krizhevsky, A.; Sutskever, I.; Hinton, G. 深度学习 2012, 60, 91–110。（注：原文为 Krizhevsky, A.; Sutskever, I.; Hinton, G. Deep Learning 2012, 60, 91–110。）

在一维卷积块之后，深度卷积神经网络中包含三个全连接层。从每个一维卷积块开始，通过汇总所有传感器的输出对数据进行扁直化（图 5）。数据被连接成单个向量，并传输到由 32 个单元组成的全连接神经层。这 32 个单元均使用 `ReLU` 激活函数。子层由 16 个单元组成，第二层位于第一层之后。输出层是网络的最后一层，对于二分类压力检测等应用，它由一个单一隐藏单元组成，并利用 `sigmoid` 函数来激活层函数。[2]

![](img/a35f8e852e0ee65e528c95ad0821783b_185_0.png)

图 5。所提出的深度维度卷积神经网络结构图。

![](img/a35f8e852e0ee65e528c95ad0821783b_185_1.png)

图 6 展示了从云端服务器获取和估计 ECG 数据的结构，采集数据后，通过蓝牙辅助传输到移动终端，并将实时显示。`HRV` 信号由 `DL` 架构进行验证和解释。如果神经网络层的输出检测到心房颤动（`AF`），将立即通知心脏医生。发现 `HRV` 迹图疑为额外心跳或 ECG 心律，将以得出结论。随后，可以使用通俗易懂的术语向患者告知诊断结果。

## 2 1-D 生物医学信号处理

在计算和比较作为时间序列函数的生物医学信号时，必须遵循预定义的步骤。惯常的前端是使用感应器子系统采集信号。前放大器作为缓冲器用于相邻子系统，以对链中的信号进行预处理。下一阶段是过滤，紧邻其的是模拟数字转换（`A/D`）阶段。最后阶段包括去除伪影、检测并解释这些事件以及提取特征。[4]

### 信号采集

| 换能器 | 前置放大器 | 滤波器/放大器 | A/D 转换 |
|---|---|---|--|
| 模式识别、分类、诊断信息 | 事件分析 - 特征提取 | 事件检测 | 去伪影 |

### 信号分析 信号处理

图 7。生物医学信号处理。

测量、识别参数和表征生物信号的初始步骤是以图像或时间序列的形式获取诊断数据，这些数据包含有关底层过程的相关信息。模拟信号通常会被放大和过滤，然后转换为数字格式以使用数字方法进行处理。随后可以应用滤波、平滑、特征提取和分类等信号处理技术来进一步分析生物信号。采集数据的准确性以及后续处理步骤对于获得可靠的诊断信息至关重要。因此，仔细设计、实施和验证这些步骤具有重要意义。生物信号的测量、参数识别和表征对一系列医学和生物应用具有重要意义，包括临床诊断、医学成像、生理监测和反馈。

信号处理通常使用软件算法在数字数据上进行，但在某些情况下，模拟信号处理也是必要的。噪声是测量系统中不可避免的因素，并会限制医疗设备的性能。使用了多种信号处理技术来最大限度地减少测量中的噪声。生物医学测量受到多种变异性的影响，包括环境噪声或干扰、换能器伪影、电子噪声和生理变异。生理变异性是因为检测到的生物医学信号可能会受到研究对象以外生物因素的影响。环境噪声可以源于体内部和外部。用于说明使用自适应降噪技术性的常用示例是胎儿心电图测量。在这种情况下，所需的信号往往会被母体 ECG 遮盖，后者产生了噪声。传统的降噪技术可以部分有效，但由于环境噪声源未知，自适应技术在过滤掉意外噪声方面通常表现更好。[4]

## 3 模型

人工神经网络本质上是从经验中学习的模型。`ANN` 模型在模式识别问题中非常有用，因为它们可以模拟复杂函数且易于使用。[6]

![](img/a35f8e852e0ee65e528c95ad0821783b_187_0.png)

图 8。深度学习模型流程。

为了评估婴儿表情检测的准确性，利用了 `VOC2007` 指标（Everingham 等人，2010）。`VOC2007` 指标主要为检测和分类任务设计。平均精度（`Average Precision`）表示检测准确性，均平均精度（`mean Average Precision`）显示输入七种表情的性能。为每个数据集计算错误表情变化频率（`FEC`）以保持输出的一致性。错误术语替换是指术语从一帧到下一相邻帧的变化，这与地面真值（`ground truth`）所示的交换不符。错误术语替换可能由于表情的错误分类和边界框错误的检测而发生。除了计算错误表情变化频率（`FEC`）外，还引入了降低率来分析时间稳定性。[7] 这种分析仅适用于使用所提时间一致性 R-CNN 的系统。此处 Ho 代表未进行时间分析的情况下错误变化的发生频率，而 F 表示未经过时间处理的错误表情计数。[7]

## 4 文献综述

| 序号 | 作者-年份 | 评估算法 | 结果 |
|---|---|---|--|
| [1] | 模式识别、分类、诊断信息 | 事件分析 - 特征提取 | 事件检测 | 去伪影 |
| [2] | Russell Li & Zhandong Liu 2020年12月30日 | 深度卷积 | 深度卷积网络能够 |
| | | 多层感知器 | |
| [3] | Bambang Tutuko 等 2021年7月14日 | 卷积神经网络 | 深度学习模型检测 AF 的评估结果在 0.02 秒样本点具有高准确性。准确性为 98.94%；灵敏度和特异性均为 98.7%。 |
| [4] | Alexandros Karagiannis 等 2011年8月23日 | 经验分解 | 该算法能够估计 ECG 数据中的高斯噪声水平并提供 95% 置信区间。这对于评估信号质量以及识别可能影响分析或诊断准确性的干扰或噪声源有用 |
| [5] | YUE SUN 等 2019 | 卷积神经网络 | 模型在来自 24 个婴儿的 6534 和 10300 帧视频数据集上通过双折交叉验证实现了 91% 的高总体准确率。此外，模型准确检测舒适的率为 90%，检测不适的率为 92%。这是前景的，表明该模型可能有助于准确检测和区分婴儿的舒适与不适 |
| [6] | S.E. Barajas-Montiel 等 2005年11月28-30日 | 神经网络和支持向量机 | 该研究评估了神经网络（NN）和支持向量机（SVM）在分类婴儿疼痛和饥饿哭声方面的性能。结果表明，集成在疼痛和疼痛哭分类上达到了 96.41% 的准确率，而 SVM 集成的准确率为 85.16%。对于饥饿和无分类，NN 集成达到了 78.61% 的准确率。似乎 SVM 集成在每次循环的正确分类上有 2% 到 3% 的波动。总体而言，研究表明 NN 在此方面表现优于 SVM |
| [7] | Cheng Li 等 2021年1月 | Faster RCNN 和 H | 高平均精度表明系统能够准确地在临床和日常环境中分类不同表情并检测不适。这表明该系统可能对医疗和其他领域的各种应用具有用途 |

# 裁剪部分

# 更改速度

![](img/a35f8e852e0ee65e528c95ad0821783b_189_0.png)

![](img/a35f8e852e0ee65e528c95ad0821783b_189_1.png)

# 注入噪声

# 频率掩码

![](img/a35f8e852e0ee65e528c95ad0821783b_189_2.png)

![](img/a35f8e852e0ee65e528c95ad0821783b_189_3.png)

图 9。婴儿哭信号的音频数据增强。

## 结论

总之，我们可以理解利用 1D 深度学习策略开发生物医学信号的不同视角的重要性以及需要进行的研究。

## 参考文献

- [1] Analyticsvidhya - https://www.analyticsvidhya.com/blog/2021/07/artificial-neural-network-simplified-with-i-d-ec-biomedical-data/
- [2] Li, R. R., Liu, Z. Stress Detection Using Deep Neural Networks, BMC Med Inform Decis Mak 20 (Suppl 11), 285 (2020). DOI: 10.1188/s12911-020-01029-4
- [3] Takeda, B., Nurmainis, S., Todoras, A.E. et al. AfFibNet: An Implementation of Atrial Fibrillation with Convolutional Neural Network, BMC Med Inform Decis Mak 2f, 216 (2021). DOI: 10.1186/s12911-021-01571-1
- [4] Karagannis, Alexandros & Constantinou, Philip & Vouyiouakas, Demosthenes. (2021). Time Series Processing and Analysis Methods: The Case of Empirical Mode Decomposition DOI: 10.5772/20972096
- [5] Yao Sun, Caifeng Shan, Tao Tan, Tong Tong Tong, Wenjin Wang, Arash Pourhtertian, H N N de Wave Detecting Discomfort in Infants Through Facial Expressions, (2019), DOI 10.1388/13361/ab55b3
- [6] S. E. Barrios-Montiel, Arash & C. E. Reyes-Garcia, Identifying Pain and Hunger in Infant Cry with Classifiers En Ensembles International Conference on Computational Intelligence for Modelling, Control and Automation and International Conference on Intelligent Agents. Web Technologies and Internet Commerce (CIMCA-IAWTC'06), 2005, pp. 770–775, DOI: 10.1109/CIMCA.2005.1631561.
- [7] Li, Cheng & Pourhtertian, Arash & Onzenooft, L., & With, Peter. (2021). Automated Infant Monitoring Based on R-CNN and HMM 553–560. 10.5220/010299605530560.

![](img/a35f8e852e0ee65e528c95ad0821783b_190_0.png)

# 人工智能驱动的应用

![](img/a35f8e852e0ee65e528c95ad0821783b_192_0.png)

# 使用区块链技术的农业领域革命

Abdul Taleem, K. Paramesha & M.G. Vinay

计算机科学与工程系，Vidyvardhaka 工程学院，Mys, Karnataka

摘要：近年来，区块链技术引起了广泛关注。在无信任背景下引入区块链智能合约使得去中心化应用的实现，这是今年关注的原因之一。随着智能合约被越来越广泛的使用，研究人员已经调查了多种缓解攻击和规避违反的方法，例如记录漏洞；然而，这些方法在捕捉区块链和用户行为方面不足。农业逐渐成为一个具有全球影响的重要行业。对天气和土壤状况的实时监测以及食品质量的提高推动了生态和经济趋势。本研究探索了利用智能合约技术进行农耕的迷人概念，以生产更好的农产品，以及更好的供应链和物流，从而为各方带来多种优势。通过使用数值和分类数据，通过面部表情检测婴儿的不适。 关键词：区块链、可追溯性、智能合约、以太坊 # 引言

近年来，区块链技术引起了广泛关注。在无信任背景下引入区块链智能合约使得去中心化应用的实现，这是今年关注的原因之一。随着智能合约被越来越广泛的使用，研究人员已经调查了多种缓解攻击和规避违反的方法，例如记录漏洞；然而，这些方法在捕捉区块链和用户行为方面不足。农业逐渐成为一个具有全球影响的重要行业。对天气和土壤状况的实时监测以及食品质量的提高推动了生态和经济趋势。本研究探索了利用智能合约技术进行农耕的迷人概念，以生产更好的农产品，以及更好的供应链和物流，从而为各方带来多种优势。通过使用数值和分类数据，通过面部表情检测婴儿的不适。 关键词：区块链、可追溯性、智能合约、以太坊

关于 1D 深度学习策略开发生物医学信号的不同视角的重要性以及需要进行的研究。

## 2 文献综述
