
# 参考文献

Khonji, M., Iraqi, Y., & Jones, A. (2013). Phishing detection: A literature survey. *IEEE Communications Surveys and Tutorials*, 15(4), 2091–2121. DOI: [10.1109/SURV.2013.032213.00009](http://dx.doi.org/10.1109/SURV.2013.032213.00009)

Li, Q., Liu, W., Wu, H., Xie, C., & Yang, W. (2020). LSTM based phishing detection for big email data. *IEEE Transactions on Big Data*, 8(1), 278–288. DOI: [10.1109/TBDATA.2020.2978915](http://dx.doi.org/10.1109/TBDATA.2020.2978915)

Rawal, S., Sharma, A., Kumar, S., & Pandey, H. (2017). Phishing detection in e-mails using machine learning. *International Journal of Applied Information Systems*, 12(7), 21–24. DOI: [10.5120/ijais2017451713](http://dx.doi.org/10.5120/ijais2017451713)

Salloum, S., Alshurideh, M., Elnagar, N., & Shaalan, K. (2021). Phishing email detection using natural language processing techniques: A literature survey. *Procedia Computer Science*, 189, 19–28. DOI: [10.1016/j.procs.2021.05.077](http://dx.doi.org/10.1016/j.procs.2021.05.077)

Salloum, S., Alshurideh, M., Elnagar, N., & Shaalan, K. (2022). A systematic literature review on phishing email detection using natural language processing techniques. *IEEE Access : Practical Innovations, Open Solutions*, 10, 65703–65727. DOI: [10.1109/ACCESS.2022.3183083](http://dx.doi.org/10.1109/ACCESS.2022.3183083)

Sanchez, F., & Duan, Z. (2012). A sender-centric approach to detecting phishing emails. In *2012 international conference on cyber security*. IEEE.

Smadi, S., Aslam, N., & Zhang, L. (2018). Detection of online phishing email using dynamic evolving neural network based on reinforcement learning. *Decision Support Systems*, 107, 88–102. DOI: [10.1016/j.dss.2018.01.001](http://dx.doi.org/10.1016/j.dss.2018.01.001)

Unnithan, N. A., . . . (2018). Machine learning based phishing e-mail detection. In *Proceedings of Security-CEN@ Amrita* (pp. 65-69). DOI: [10.1145/3190645.3190652](http://dx.doi.org/10.1145/3190645.3190652)

Verma, R., Shashidhar, N., & Hossain, N. (2012). Detecting phishing emails the natural language way. In *Computer Security–ESORICS 2012: 17th European Symposium on Research in Computer Security, Pisa, Italy, September 10-12, 2012. Proceedings 17* (pp. 824-841). Springer Berlin Heidelberg. DOI: [10.1007/978-3-642-33167-1_47](http://dx.doi.org/10.1007/978-3-642-33167-1_47)

Yang, Z., Chen, Z., Xiao, W., Liu, Q., & Zhang, Y. (2019). Phishing email detection based on hybrid features. IOP Publishing. *IOP Conference Series. Earth and Environmental Science*, 252(4), 042039. DOI: [10.1088/1755-1315/252/4/042051](http://dx.doi.org/10.1088/1755-1315/252/4/042051)

Yasin, A., & Abuhasan, A. (2016). An intelligent classification model for phishing email detection. *arXiv preprint arXiv:1608.02196*.

Zareapoor, M., & Seeja, K. R. (2015). Feature extraction or feature selection for text classification: A case study on phishing email detection. *International Journal of Information Engineering and Electronic Business*, 7(2), 60. DOI: [10.5815/ijieeb.2015.02.08](http://dx.doi.org/10.5815/ijieeb.2015.02.08)

Zhang, N., & Yuan, Y. (2012). Phishing detection using neural network. *CS229 Lecture Notes*, 301. DOI: [10.1145/3180445.3180464](http://dx.doi.org/10.1145/3180445.3180464)

# 基于异常的网络入侵检测系统

基于异常的网络入侵检测系统通过检测网络模式中的偏差来识别潜在威胁。它最初监控正常的网络流量以确定基线，然后以此为基础（而非数据库）来识别偏差。这有助于检测新的和未知的威胁。然而，它也存在一些缺点，例如误报数量增加，且在基线建立方面面临困难。它还消耗大量资源，需要计算资源来持续监控和分析网络流量。

# 利用机器学习构建稳健的 IDS

在减轻传统网络入侵检测系统局限性的同时发挥其优势，对于开发稳健的网络入侵检测系统至关重要。机器学习是实现这一目标的工具。由于机器学习算法是在包含正常和恶意流量的大型数据集上训练的，因此具有改进的模式识别能力，从而有助于减少误报。此外，特征工程技术（Venkatesan, 2023）可用于提高检测准确性。由于机器学习模型可以持续学习，它们能够适应新模式，从而为异常检测建立动态且自适应的基线。机器学习算法旨在处理大型数据集。它们还能更高效地预处理和分析数据，并可并行处理，从而降低计算开销并提高资源效率。

# 应对高容量数据挑战

现有的基于机器学习的网络入侵检测面临超大数据量的问题，这影响了检测准确率和检测率。这可以通过使用特征选择技术（Pudjihartono et al., 2022）来缓解，而不是使用数据中存在的所有特征。这将减少计算过载，缩短检测时间，减少误报数量，并有助于整体提升网络入侵检测系统的性能。此外，对用于该目的的不同机器学习算法进行超参数调优（Kusumaputri & Arifin, 2022），有助于识别哪些算法是最优的。这也有助于选择表现最佳的算法并对它们进行集成。集成是一种利用不同超参数调优后的机器学习算法优势的方法。这有助于构建一个稳健的网络入侵检测系统——即一个在不同场景下都能工作的系统。

# 使用 CICIDS-2017 数据集实施

为了实施所提出的想法，使用了 `CICIDS-2017` （Panigrahi & Borah, 2018）数据集。该数据集包含为期七天观察到的正常和恶意网络模式，因此数据量很大。用于模式识别的各种机器学习算法包括 `Random Forest`、`Decision Tree` 等（将在后文讨论）。`Optuna` 用于超参数调优。最后，模型被集成并进行了测试。

# 章节结构

以下呈现本章的总体结构：

- 本章讨论了在实施所提出想法之前进行的文献综述。这涉及对不同作者提出的类似系统及其局限性的研究。
- 还讨论了方法论，并概述了所提出想法的开发方法、预处理技术、特征选择和模型选择。
- 本章的实施部分提供了系统架构、使用的算法和测试环境。
- 结果与讨论部分展示了获得的结果以及从结果中得出的分析和推断。
- 本章以所提出系统的结论和未来展望作为结尾。
- 关键术语和定义见附录。

# 文献综述

所提出的模型专注于特征选择技术，以提高预测准确性，从而实现对未见攻击的检测。模型使用 `CIC IDS 2017` 数据集进行训练。执行探索性数据分析以观察数据集中的趋势，然后对数据进行预处理，随后采用特征选择技术 `Particle Swarm Optimization`（粒子群优化），然后使用 `RUS` 和 `ADASYN` 采样算法对数据集进行平衡。使用的机器学习算法包括 `K-Nearest Neighbours`、`Random Forest`、`Decision tree`、`Gaussian Naïve Bayes`、`XGBoost`、`Catboost`、`LightGBM`、`Adaboost` 和 `Logistic regression`。这些单独的模型使用 `Optuna` 进行超参数调优并进行集成，以确保在存在外部噪声时的稳健性和稳定性。训练好的集成模型的性能通过三种方式进行评估，并通过改变扰动大小使用稳定性分数验证模型的稳定性。通过添加随机噪声验证模型的鲁棒性。最后，执行了 `5 fold cross validation`（5 折交叉验证）以检查过拟合。

在题为“Machine and Deep Learning Based Comparative Analysis Using Hybrid Approaches for Intrusion Detection System”（基于混合方法的机器学习与深度学习入侵检测系统比较分析）的研究中，A. Rashid、M. J. Siddique 和 S. M. Ahmed 提出了他们的想法，该论文的核心思想基于在 `NSL-KDD` 和 `CIDDS-001` 数据集上对 ML 算法的全面比较分析；推广混合特征选择方法以提高分类器性能。该论文展示了使用机器学习和深度学习方法在 `NSL-KDD` 和 `CIDDS-001` 数据集上对入侵检测系统的比较分析。论文的局限性包括未解决所有现有的网络安全问题；需要未来研究更先进的深度学习方法和最新数据集。

在探索了上述论文后，研究了文中提到的数据集，分析了数据集的优缺点并记录了重要观察结果，决定采用机器学习方法用于所提出的模型，仔细记录了上述论文的局限性，并旨在在所提出的模型中加以修正。这篇论文有助于比较和对比机器学习和深度学习模型。

2024 年，Ramu, C., Rao, T.S. & Rao, E.U.S. 在其题为“Attack Classification in Network Intrusion Detection System Based on Optimization Strategy and Deep Learning Methodology”（基于优化策略和深度学习方法的网络入侵检测系统攻击分类）的论文中，提出了一种创新的元启发式优化和基于深度学习的方法，以提升网络入侵检测系统的性能，取得了优于现有模型的结果。该方法涉及将符号特征转换为布尔值，使用 z-score 进行归一化，并使用 `SMOTE` 和 `RUS` 进行数据平衡，使用扩展的 `Pelican Optimization algorithm (Ex-Pel)`（鹈鹕优化算法）进行特征选择过程以选择最优特征集，使用 `Self-Attention Assisted Weighted Auto Encoder (SAttn_WAE)`（自注意力辅助加权自编码器）模型进行分类以检测攻击。所提出的模型在 `UNSW-NB15` 数据集上显著优于替代方法。局限性包括该研究未解决所提出模型在实际部署中的潜在局限性。

详细研究了这篇论文，并得出了关于所提出模型的重要结论。在上述模型中被证明能产生最佳结果的数据平衡和特征选择技术也被用于所提出的模型。彻底研究了 `UNSW-NB15` 数据集，并在为所提出的模型选择数据集时考虑了其优缺点。

## 基于特征选择的入侵检测系统设计 (2023)

Srinath Venkatesan (2023) 在论文“Design an Intrusion Detection System based on Feature Selection Using ML Algorithms”中提出了一种使用机器学习算法进行入侵检测的模型。该论文对决策树、随机森林和 SVM 等机器学习算法进行了比较研究，以构建高效的入侵检测系统，并得出结论：**随机森林算法在选定特征下表现最佳**。

**局限性**：

- 存在重复记录，可能导致误报结果
- 需要使用不同的 ML 算法和特征选择技术进行进一步研究

该论文记录了特征选择过程后决策树、随机森林和支持向量机等不同分类器算法的响应和预测。这有助于单独分析各种机器学习分类器算法，并进一步研究了文中特征选择方法的优势。

## 面向入侵检测系统的可解释机器学习框架 (2020)

M. Wang, K. Zheng, Y. Yang & X. Wang (2020) 在论文“An Explainable Machine Learning Framework for Intrusion Detection Systems”中提出了一种使用 SHAP 为 IDS 提供解释的框架；这是将 SHAP 方法应用于提高 IDS 透明度的首次尝试。该框架提供局部和全局解释，以提高任何入侵检测系统 (IDS) 的可解释性。

该框架帮助网络安全专家更好地理解 IDS 做出的预测以及不同网络攻击的特征，并允许专家根据不同分类器之间解释的差异来优化 IDS 的结构。

**研究方向**：

- 在 APT 等更复杂的攻击上探索 SHAP 方法
- 不同分类器之间的不同解释也有助于安全专家更好地设计 IDS 的结构

**局限性**：

- SHAP 方法无法实时工作
- 需要在更多数据集上进行实验

该论文主要关注入侵检测系统的透明度，使模型更易理解，并将模型应用于复杂攻击，模型的解释详细且有助于设计更好的 IDS。

## 粒子群优化与入侵检测系统特征选择 (2020)

Kunhare, N., Tiwari, R. & Dhar, J. (2020) 在论文“Particle Swarm Optimization and Feature Selection for Intrusion Detection System”提出了一种方法论，涉及对 NIDS 指标的不同分类器进行比较研究，使用 RF 进行特征选择，使用 PSO 进行优化，灵感来源于群体智能。在 NSL-KDD 数据集上，结合特征选择的粒子群优化方法比其他机器学习算法实现了更好的准确性和性能，且仅使用了 10 个特征，优于在同一数据集上使用特征选择的其他现有算法。

该论文使用的特征选择方法——粒子群优化被用于拟议模型中，该技术已被广泛研究和详细探讨。论文中使用的 NSL-KDD 数据集已被研究，其优缺点被仔细观察并记录以供进一步参考。这是拟议模型的核心论文之一。

## 数据集选择与预处理决策

在回顾文献后得出重要结论：彻底研究了各论文中使用的 NSL-KDD、UNSW-NB15 等数据集以及 KDD-Cup 99 和 CIC IDS 等其他可用数据集，决定使用 **CIC IDS 2017 数据集**。理由如下：

- 这是一个包含真实网络流量数据的最新数据集
- 相比 KDD-Cup 99 和 NSL-KDD 提供了更详细的标注
- 包含 2,830,743 条记录，涵盖与网络攻击相关的各类网络活动

使用 **ADASYN 和 RUS 采样方法**等数据平衡技术解决了 CIC IDS 2017 数据集的类别不平衡问题。

在彻底研究文献中的各种模型并考虑其优缺点后，确定了拟议模型的工作流程。执行了**探索性数据分析 (EDA)**，以从数据集中获得重要见解、详细的可视化和统计摘要，分三步进行：单变量分析、双变量分析和多变量分析。随后在粒子群优化之前进行了独热编码和对数变换等预处理技术，然后应用了不同的分类器算法。为防止对特定类别的偏见，进行了数据平衡，之后应用不同的分类器算法，然后使用 Optuna 对单个模型进行超参数调优，使用软投票进行集成，并使用稳定性评分和交叉验证等测试方法进行测试。

# 方法论
