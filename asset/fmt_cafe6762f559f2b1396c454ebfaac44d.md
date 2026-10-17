
## A. Logistic regression

Logistic regression 是一种主要用于分类问题的机器学习算法，基于概率预测分析 (Rymarczyk et al., 2019)。值得注意的是，LR 模型的代价函数比线性回归更为复杂。该代价函数，通常称为“Sigmoid 函数”或“Logistic 函数”，取代了线性函数。由于逻辑回归的基本前提，代价函数的输出范围天然限制在 `[0, 1]` 区间。这一限制源于逻辑回归本质上模型事件发生的概率，线性函数无法捕捉其细微特征。

## B. Decision tree

决策树是代表数据分类模型的常用方法 (Jijo and Abdulazeez, 2021)。决策树在机器学习、图像处理和模式识别等多个领域都具有多功能性，其核心任务是分类，因此在数据挖掘领域被广泛用作分类器。这些决策树由相互连接的节点和分支组成，每个节点表示离散分类类别中的属性集合，每条分支代表节点对应的可能取值。决策树因其能够快速准确地处理大规模数据集而受到广泛青睐。

## C. Random forest

随机森林是一种监督学习技术，在机器学习领域展现出显著成功，能够处理分类和预测等多种任务。其独特之处在于它像一个由多个决策树组成的团队协作解决问题。它不依赖单一决策树，而是结合许多树的结果，每棵树在不同的数据子集上训练。这种协作方式提高了准确性。树的数量越多，性能越好，错误率越低 (Dabiri et al., 2022; Gera et al., 2021)。

## D. LightGBM

LightGBM 是一种基于树的学习算法的梯度提升框架 (Tang et al., 2020)。它因分布式高效的设计而拥有诸多优势，如训练时间加快、内存占用更少，支持多 GPU 和分布式学习。LightGBM 能够处理大量数据并提供更高的精度。

## V. Methodology

如 Figure 7.1 所示，所提方法在第一阶段从 GitHub 仓库 [`github.com/gabbygab1233/Crop-Recommender/blob/main/Crop_recommendation.csv`](https://github.com/gabbygab1233/Crop-Recommender/blob/main/Crop_recommendation.csv) 获取用于拟议方法的数据集。该数据集结合了印度农业部门收集的降雨、气候和肥料数据。Table 7.1 展示了所用特征的描述。数据集包含 8 个特征和 2200 条记录。

Table 7.1 Feature description

| Attribute | Attribute description |
| --- | --- |
| `Nitrogen` | 土壤中氮含量的比例 |
| `Phosphorus` | 土壤中磷含量的比例 |
| `Potassium` | 土壤中钾含量的比例 |
| `Rainfall` | 降雨量 (mm) |
| `Humidity` | 相对湿度 (%) |
| `pH level` | 土壤 pH 值 |
| `Temperature` | 温度 (摄氏度) |

对收集的原始数据进行准备，以使其适合构建机器学习模型，这是创建机器学习模型的第一步和最关键的一步。数据来源各异，往往不够清洁。数据必须在进行任何操作之前进行清洗和格式化。数据预处理对于此目的至关重要。

## VI. Results

Table 7.2 显示了用于开发作物推荐系统的机器学习方法的性能，包括 LR、DT、RF 和 LightGBM。所使用的算法通过精确率、召回率、F1 分数和支持度等评估指标进行了评估。

### Precision

它指示模型执行的准确预测的百分比。它具体评估分类器正确区分正例或负例的能力。精确率（Precision）是通过将准确预测的正例数除以所有预测的总数（包括正确和错误的分类）来计算得出。

$$Precision = \frac{TP}{TP + FP}$$

### Recall

它表示模型成功识别出的正例的百分比。它量化分类器有效定位所有属于指定目标类别的实例的能力。召回率（Recall）通过将目标类别的正确预测数除以所有预测的总数（包括准确和不准确的分类）来计算。

$$Recall: \frac{TP}{TP + FN}$$

### F1-score

它表示准确的正预测所占的比例。该指标由精确率（Precision）和召回率（Recall）结合计算得出，范围从 1.0（最佳表现）到 0.0（最差表现）。由于 F1-score 同时考虑精确率和召回率，它比单纯的准确率更具信息性。在评估和比较分类器模型时，建议使用 F1-score 的加权平均值，而不是仅依赖整体准确率。

$$F1 - score = \frac{2 \ast Precision \cdot Recall}{Prectsion + Recall}$$

### Support

它指实际数据集中特定类别的出现频率。它是衡量训练数据分布是否均匀或不均匀的指标。支持（Support）的差异可能暗示分类器报告的指标可能不够可靠。需要注意的是，Support 在不同模型中保持一致，其主要作用是辅助分析测试方法。

## VII. Discussion

农业部门在推动国家经济发展方面发挥着关键作用。为提升该部门的盈利能力和生产力，有必要探索创新解决方案。本文在研究论文中介绍了一种基于机器学习技术的作物推荐系统。该系统旨在帮助农民根据土壤属性和天气条件的复杂交互，做出准确的作物品种选择决策。

## VIII. Conclusion

本研究论文介绍了一种面向农民的作物推荐系统，旨在通过预测分析帮助农民做出最佳作物选择。该系统考虑了关键参数，包括土壤特性（NPK 含量、pH 值和湿度）以及气象因素（温度和降雨量）。在开发该系统时，采用了机器学习方法，包括 LR（逻辑回归）、DT（决策树）、RF（随机森林）以及 LightGBM。这些算法均在收集的数据集上进行了应用。数据集在预处理后呈现正态分布，几乎没有异常值，相关分析在预处理步骤之后完成。LightGBM 和 RF 在各类算法中表现出最高的准确率。展望未来，通过持续更新数据集，使系统与农业条件的演变保持同步，可进一步提升系统性能；此外，系统的范围还可以扩展以纳入作物病害检测功能，从而帮助农民在农业领域实现更大收益。

## References

- Chavva, Mr Konda Reddy. India at a glance. n.d. [`www.fao.org/india/fao-in-india/india-at-a-glance/en/`](https://www.fao.org) (accessed june 15, 2023).

- Gera, T., Singh, J., Mehbodniya, A., Webber, J. L., Shabaz, M., and Thakur, D. (2021). Dominant feature selection and machine learning-based hybrid approach to analyze android ransomware. Sec. Comm. Netw., 2021, 1–22.

- Affarirs, M. O. H. NCRB on data portal. [Online]. Available: [`data.gov.in/search?title=suicide`](https://data.gov.in).

- Pande, Shilpa Mangesh, Prem Kumar Ramesh, Anmol Anmol, B. R., Aishwarya, Karuna Rohilla, and Kumar Shaurya. (2021). Crop recommender system using machine learning approach. In 2021 5th international conference on computing methodologies and communication (ICCMC), 1066–1071. IEEE.

- António Monteiro, S. S. P. G. (2021). Precision agriculture for crop and livestock. MDPI/Animals, 1–18.

- Meshram, Vishal, Kailas Patil, Vidula Meshram, Dinesh Hanchate, and S. D. Ramkteke. (2021). Machine learning in agriculture domain: A state-of-art survey. Artificial Intelligence in the Life Sciences, 1, 1–11. doi: [`doi.org/10.1016/j.ailsci.2021.10001`](https://doi.org/10.1016/j.ailsci.2021.10001).

- Sharma, Pinkashia, and Jaiteg Singh. (2018). Machine learning based effort estimation using standardization. In 2018 International Conference on Computing, Power and Communication Technologies (GUCON), 716–720. IEEE.

- Pudumalar, S., E. Ramanujam, R. Harine Rajashree, C. Kavya, T. Kiruthika, and J. Nisha. (2017). Crop recommendation system for precision agriculture. In 2016 Eighth International Conference on Advanced Computing (ICoAC), 32–36. IEEE.

- Jijo, B. T. and Abdulazeez, A. M. (2021). Classification based on decision tree algorithm for machine learning. J. Appl. Sci. Technol. Trends, 02(1), 20–28.

- Rymarczyk, T., Kozlowski, E., Klosowski, G., and Niderla, K. (2019). Logistic regression for machine learning in process tomography. Sensors, 1–19.

- Dabiri, Hamed, Visar Farhangi, Mohammad Javad Moradi, Mehdi Zadehmohamad, and Moses Karakouzian. (2022). Applications of Decision Tree and Random Forest as Tree-Based Machine Learning Techniques for Analyzing the Ultimate Strain of Spliced and Non-Spliced Reinforcement Bars. Applied Sciences. 12(10), 4851. 1–13 doi: [`doi.org/10.3390/app12104851`](https://doi.org/10.3390/app12104851).

- Tang, Mingzhu, Qi Zhao, Steven X. Ding, Huawei Wu, Linlin Li, Wen Long, and Bin Huang. (2020). An improved lightGBM algorithm for online fault detection of wind turbine gearboxes. Energies, 13(4): 807. 1–16. doi: [`doi.org/10.3390/en13040807`](https://doi.org/10.3390/en13040807).

- Raja, S. Kanaga Suba, R. Rishi, E. Sundaresan, and V. Srijit. (2017). Demand based crop recommender system for farmers. In 2017 IEEE Technological Innovations in ICT for Agriculture and Rural Development (TIAR), 194–199. IEEE. doi: [`10.1109/TIAR.2017.8273714`](http://dx.doi.org/10.1109/TIAR.2017.8273714).

- Doshi, Zeel, Subhash Nadkarni, Rashi Agrawal, and Neepa Shah. (2018). AgroConsultant: intelligent crop recommendation system using machine learning algorithms. In 2018 Fourth International Conference on Computing Communication Control and Automation (ICCUBEA), 1–6. IEEE. doi: [`10.1109/ICCUBEA.2018.8697349`](http://dx.doi.org/10.1109/ICCUBEA.2018.8697349).

- Kulkarni, Nidhi H., G. N. Srinivasan, B. M. Sagar, and N. K. Cauvery. (2018). Improving crop productivity through a crop recommendation system using ensembling technique. In 2018 3rd International Conference on Computational Systems and Information Technology for Sustainable Solutions (CSITSS), 114–119. IEEE. doi: [`10.1109/CSITSS.2018.876879`](http://dx.doi.org/10.1109/CSITSS.2018.876879).

- Priyadharshini, A., Swapneel Chakraborty, Aayush Kumar, and Omen Rajendra Pooniwala. (2021). Intelligent crop recommendation system using machine learning. In 2021 5th international conference on computing methodologies and communication (ICCMC), 843–848. IEEE. doi: [`10.1109/ICCMC51019.2021.941837`](http://dx.doi.org/10.1109/ICCMC51019.2021.941837).

## 8 环境与可持续发展：ChatGPT 的视角

Priyanka Bhaskar^(⁸)

DOI: [10.1201/9781003471059-8](https://dx.doi.org/10.1201/9781003471059-8)

### 摘要

**人工智能（AI）与可持续发展是两面一体的硬币。AI 是可持续发展斗争的可靠盟友，引领我们走向更美好的未来。AI 通过分析大规模数据集，为可再生能源、资源管理和生态友好型决策提供支持。然而，AI 模型的能源消耗和碳足迹以及 AI 与可持续发展的关系日益受到审视。本文研究了 AI 模型的环境影响，重点讨论 ChatGPT，并强调可持续 AI 发展的必要性。最近的研究表明，AI 模型的创建与使用对全球碳足迹产生了显著影响，涉及能源、水和碳排放。鉴于其巨大的计算需求，ChatGPT 对环境造成了负面影响。为解决这一矛盾，可持续 AI 发展必须得到推进。模型压缩、量化和知识蒸馏可提升 AI 的能源效率。使用可再生能源以及制定和执行 AI 模型能源效率要求同样至关重要。通过采用可持续 AI 发展方法，ChatGPT 及类似模型可以实现环保。在此背景下，本研究的目标是通过分析现有关于人工智能模型环境影响的报告和研究，分析 AI 工具（特别是 ChatGPT）的使用对可持续性和环境保护的影响。**

**学术界、开发者、政治家、机构和组织必须协同工作，制定节能高效 AI 算法、可再生能源使用以及负责任部署的规则与框架。本文结论指出，AI 模型的能源消耗和碳足迹必须被理解并加以减少。通过推广可持续实践，AI 社区可以推动更具环保意识和负责任的 AI 发展，从而实现符合全球可持续发展目标的更绿色未来。**

**关键词：人工智能、AI 语言模型、ChatGPT、环境影响、碳足迹、水足迹、温室气体排放、能源消耗、可持续性、缓解措施**

### I. 引言

不可否认，人工智能（AI）已经在改变世界，并将继续如此。尽管 AI 有潜在的积极影响，但社会也可能因其而受害。ChatGPT 是由 Open AI 开发的大型语言模型，是一种显著的 AI 模型，已获得广泛应用。2023 年全球 AI 市场规模为 2000 亿美元，预计到 2030 年将增长近 9 倍，达到 1850 亿美元（statista.com）。由于其卓越的自然语言处理（NLP）能力，ChatGPT 引起了广泛关注，毫无疑问简化了人们的生活。但 ChatGPT 也有代价，正如任何值得珍视的事物都有代价。构建和训练这一 AI 系统所需的能源会带来相当大的负面环境成本，如产生大量碳排放和水足迹，这些往往被忽视。
