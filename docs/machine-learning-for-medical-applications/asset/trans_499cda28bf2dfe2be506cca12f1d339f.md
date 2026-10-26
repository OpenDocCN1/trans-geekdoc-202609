

可以通过识别彼此不同的离群点，克服不同数据流所固有的框架限制。

多模态网络中的融合可以发生在三个主要层面：早期融合、中间融合和晚期融合。早期融合直接对来自不同模态的原始信号执行数据融合，使网络能够接收集成输入。中间融合结合从各个模态中提取的特征，因此能够让网络学习模态间的关系，同时保留模态内的特征。图 15 展示了晚期融合如何通过结合独立训练模型的输出，实现简单且相对不受限制的架构解决方案。近年来的注意力机制和基于图的架构等发展，进一步提升了区分各模态贡献的能力。

广为人知的多模态融合方法基于混合神经架构。例如，CNN 处理图形数据，而 RNN 处理序列数据。为此，特定模态的模型会在融合层连接起来，以学习同步表示。在融合框架中，VAE 和 GAN 也被用于生成和重构多模态网络，进而有助于提升复杂场景下的检测性能。

## 7 结论

本章全面讨论了用于扫描视觉信息有效异常检测的最先进机器学习模型及其组合。通过结合监督学习、无监督学习和强化学习方法，本研究充分应对了异常检测所面临的一些长期挑战，例如处理高维数据和不平衡数据集的能力下降。对包含 CNN、RNN、GAN 和 VAE 的混合模型进行介绍，展示了这些框架的应用如何提高异常检测的准确率，并减少所需的计算量。值得关注的发展领域包括特征提取技术、可靠的集成方法，以及利用多种形式的数据来改善异常检测。本文还讨论了实施所建议方法时涉及的问题和关注点，包括可扩展性、可解释性，以及在相关领域中的灵活性，尤其是在诊断医学、数字安全和制造业领域。这些方法能够改善检测结果，并使该框架具备实际应用价值；不同类型细粒度异常的高召回率和高精确率也证明了这一点。

## 参考文献

- [1] Haleem, A., Javaid, M., Singh, R. P., & Suman, R.（2022）。医疗 4.0 技术：特征、能力与应用。Internet of Things and Cyber-Physical Systems，2，12–30。
- [2] Wang, D., Zhang, C., Chen, W., Yang, H., Zhang, M., & Lau, A. P. T.（2022）。基于机器学习的光网络故障管理综述。Science China Information Sciences，65(11)，211302。
- [3] Taha, A., & Hadi, A. S.（2019）。分类数据的异常检测方法：综述。ACM Computing Surveys (CSUR)，52(2)，1–35。
- [4] Train, K. E.（2009）。离散选择模拟方法。Cambridge University Press。
- [5] Paleyes, A., Urma, R. G., & Lawrence, N. D.（2022）。机器学习部署中的挑战：案例研究综述。ACM Computing Surveys，55(6)，1–29。
- [6] Patcha, A., & Park, J. M.（2007）。异常检测技术概述：现有解决方案与最新技术趋势。Computer Networks，51(12)，3448–3470。
- [7] Chen, C. P., & Zhang, C. Y.（2014）。数据密集型应用、挑战、技术与科技：大数据综述。Information Sciences，275，314–347。
- [8] Zhao, Z. Q., Zheng, P., Xu, S. T., & Wu, X.（2019）。基于深度学习的目标检测：综述。IEEE Transactions on Neural Networks and Learning Systems，30(11)，3212–3232。
- [9] MacLeod, N., & Kolska Horwitz, L.（2020）。用于检验小样本形态变异模式的机器学习策略：灰狼（Canis lupus）颅骨的性二态性。BMC Biology，18，1–26。
- [10] Mikkelsen, B.（2005）。发展工作与研究方法：实践者新指南。Sage。
- [11] Kumar, R., & Agrawal, N.（2023）。基于边缘–雾–云架构框架的多维工业物联网（IIoT）数据分析：当前状态与研究挑战综述。Journal of Industrial Information Integration，100504。
- [12] Usama, M., Qadir, J., Raza, A., Arif, H., Yau, K. L. A., Elkhatib, Y., . . . & Al-Fuqaha, A.（2019）。面向网络的无监督机器学习：技术、应用与研究挑战。IEEE Access，7，65579–65615。
- [13] Ma, X., Wu, J., Xue, S., Yang, J., Zhou, C., Sheng, Q. Z., . . . & Akoglu, L.（2021）。基于深度学习的图异常检测综合综述。IEEE Transactions on Knowledge and Data Engineering，35(12)，12012–12038。
- [14] Simanek, J., Kubelka, V., & Reinstein, M.（2015）。通过异常检测改进多模态数据融合。Autonomous Robots，39(2)，139–154。
- [15] Fernando, T., Gammulle, H., Denman, S., Sridharan, S., & Fookes, C.（2021）。用于医学异常检测的深度学习——综述。ACM Computing Surveys (CSUR)，54(7)，1–37。
- [16] Carbonneau, M. A., Cheplygina, V., Granger, E., & Gagnon, G.（2018）。多示例学习：问题特征与应用综述。Pattern Recognition，77，329–353。
- [17] Alloghani, M., Al-Jumeily, D., Mustafina, J., Hussain, A., & Aljaaf, A. J.（2020）。面向数据科学的监督式和无监督式机器学习算法系统综述。Supervised and Unsupervised Learning for Data Science，3–21。
- [18] Hastie, T., Tibshirani, R., Friedman, J., Hastie, T., Tibshirani, R., & Friedman, J.（2009）。无监督学习。The Elements of Statistical Learning: Data Mining, Inference, and Prediction，485–585。
- [19] Osisanwo, F. Y., Akinsola, J. E. T., Awoleye, O., Hinmikaiye, J. O., Olakanmi, O., & Akinjobi, J.（2017）。监督式机器学习算法：分类与比较。International Journal of Computer Trends and Technology (IJCTT)，48(3)，128–138。
- [20] Elkan, C., & Noto, K.（2008 年 8 月）。仅利用正类数据和无标签数据学习分类器。发表于第 14 届 ACM SIGKDD 国际知识发现与数据挖掘会议论文集，（第 213–220 页）。
- [21] Steinwart, I., Hush, D., & Scovel, C.（2005）。异常检测的分类框架。Journal of Machine Learning Research，6(2)。
- [22] Chalapathy, R., & Chawla, S.（2019）。用于异常检测的深度学习：综述。arXiv 预印本 arXiv:1901.03407。
- [23] Karimi, D., Dou, H., Warfield, S. K., & Gholipour, A.（2020）。带噪声标签的深度学习：探索医学图像分析中的技术与补救措施。Medical Image Analysis，65，101759。
- [24] Riboni, D., Bettini, C., Civitarese, G., Janjua, Z. H., & Helaoui, R.（2016）。SmartFABER：识别细粒度异常行为，以早期检测轻度认知障碍。Artificial Intelligence in Medicine，67，57–74。
- [25] Goldstein, M., & Uchida, S.（2016）。多变量数据无监督异常检测算法的比较评估。PloS One，11(4)，e0152173。

P. Krishnamoorthy、V.R. Kavitha、A. Aalan Babu、D. Shobana 和 G. Kumaran

## 提升疾病检测与诊断敏感性的 AI 增强型诊断材料

**摘要：**人工智能（AI）的应用改变了疾病诊断过程，因为它能够与诊断材料融合，从而提高医疗实践中的敏感性和精确度。在本章中，作者介绍了 AI 辅助诊断技术，重点关注其在提高疾病识别准确性和生产效率方面带来的重大变化。我们将深入探讨其中一些关键突破领域，例如实时数据分析、生物传感器和其他先进的 AI 制造算法。本章高度关注 AI 在应对重要问题方面的作用，包括提高诊断敏感性、增强大数据处理能力以及实现实时监测。此外，本文还讨论了 AI 在诊断领域现存及新兴的伦理问题和研究前景，涉及数据隐私、算法偏差与数据偏差，以及相关政策。本文对 AI 的各个方面进行了研究和评述，面向希望了解并挖掘 AI 潜力的学者、相关领域专业人士和政策制定者，旨在推动 AI 成为可靠的医疗解决方案和更优的诊断工具。

**关键词：**人工智能，诊断敏感性，生物传感器，机器学习，数据隐私，实时监测

**P. Krishnamoorthy**，CSE 系，SASI 科技与工程学院，Tadepalligudem，West Godavari 534101，安得拉邦，电子邮箱：krishnaseo0206@gmail.com

**V.R. Kavitha**，计算机科学与商业系统系，R.M.K. 工程学院，RSM Nagar，Kavaraipettai 601206，电子邮箱：vr.kavitha.cs@gmail.com

**A. Aalan Babu**，CSE 系，Vel Tech Rangarajan 博士 Sagunthala 科学与技术研发学院，Avadi，Chennai，电子邮箱：aalanbabu@gmail.com

**D. Shobana**，机电一体化系，Rajalakshmi 工程学院，Chennai，电子邮箱：shobana.d@rajalakshmi.edu.in

**G. Kumaran**，计算机科学与工程系，Saveetha 工程学院，Saveetha 医学与技术科学研究院，Saveetha 大学，Chennai 602105，泰米尔纳德邦，印度，电子邮箱：gkumarantrk@gmail.com

https://doi.org/10.1515/9783112205198-007

