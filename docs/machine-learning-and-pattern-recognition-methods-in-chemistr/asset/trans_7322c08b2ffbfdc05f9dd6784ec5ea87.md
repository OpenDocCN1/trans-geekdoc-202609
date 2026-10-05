

# 化学中的机器学习与模式识别方法

在这些模型中，模型复杂度与泛化能力之间存在权衡。通过解决帕累托优化问题，他们尝试以最大化泛化能力的方式来选择模型超参数。

## 2.4 癌症亚型分类

造血系统是免疫系统细胞中的一种恶性肿瘤。Park、Batbaatar、Piao、Theera-Umpon 和 Ryu (2021) 使用自动编码器模型来寻找显著特征，并为造血性癌症分类构建预测模型。他们还使用了过采样方法 SMOTE（Chawla, Boyer, Hall, & Kegelter, 2002）来解决数据集不平衡的难题。该研究的另一个优势是使用了 SHAP（Lundberg & Lee, 2017）方法来解释预测模型，并解释了种癌症亚型的主要基因和蛋白质。数据集是 2457 名患有造血性癌症患者的基因表达数据，分为五个亚型。他们在代价函数中汇总了变分自动编码器的重构误差和分类损失，并使用了多种机器学习分类器（例如 ANN、RF、KNN、SVM）。观察表明，自动编码器在降维方面的性能优于 PCA 和 NMF。

## 2.5 光谱成像中的降维

光谱学方法已成为化学、药学和生物学中一种主导且高效的方法。该领域的新实验可以产生数百 GB 的数据，因此，其分析需要强大的算法。大多数分析此类数据的方法都从降维步骤开始。线性方法已被用于减小此类数据的大小，但使用非线性方法有助于在此过程中减少信息。Thomas、Race、Steven、Gilmore 和 Bunch (2016) 使用自动编码器将超过 165,000 个像素和 7000 多个光谱通道减少到更少的本质特征。为了避免对训练数据产生过拟合，他们采用了标准的 L2 权重正则化。他们将其应用于小鼠脑数据，编码器表现出的性能高于 PCA 和 NMF。

## 2.6 帕金森病进展识别

帕金病是一种影响运动的渐进性神经系统疾病。症状逐渐开始，有时仅为单手出现明显的震抖。震抖很常见，该疾病还会导致运动僵硬或速度减慢。

# 生成模型中的自动编码器 135

统一帕金森病评分量表 (UPDRS) 分四部分。每部分包含多个单独评分的得分，0 表示正常或无问题，1 表示轻微问题，2 表示轻度问题，3 表示中度问题，4 表示严重问题。这些分总计以指示疾病的严重程度，199 分最严重（完全残疾），0 分表示无残疾。

Kazak (2019) 使用了一个包含 42 名确诊为早期帕金森病患者的 5875 条记录的数据集：28 名男性和 14 名女性（每位患者约 200 条记录）。每个观测值通过以下变量描述：患者编号、年龄、性别、自基线招募日期起的时间间隔、基于生物医学测量的 16 个语音属性以及用于跟踪症状进展的统一帕金森病评分量表 (UPDRS) 分。结果显示，这种方法比传统的线性方法更有效。

# 参考文献

- Bengyo, Y., Ducharme, R., Vincent, P., & Janvin, C. (2003). A neural probabilistic language model. The Journal of Machine Learning Research, J, 1137–1155.
- Bilal, M., Ullah, M., & Ullah, H. (2019). Chemometric data analysis with autoencoder neural network. Electronic Imaging, 2019(1), 671–679.
- Blaschke, T., Oliveira, M., Engqvist, O., Bajarath, J., & Chen, H. (2018). Application of generative autoencoder for molecular design. Molecular Informatics, 17.
- Chawla, N. V., Bowyer, K., Hall, L., & Kegelter, W. (2002). SMOTE: Synthetic minority oversampling technique. Journal of Artificial Intelligence, 16, 321–357.
- Chung, J., Gulture, C., Cho, K., & Bengio, Y. (2014). Empirical evaluation of gated recurrent networks. arXiv:1412.3535.
- Fukushima, K., & Miyake, S. (2022). Neocognitron: A self-organizing mechanism for visual perception.
- Gómez, R., Hernández-Lobato, D., Sánchez, B., et al. (2018). Deep learning for molecular design. ACS Science, 2678–2776.
- Goodfellow, I., Bengio, Y., & Courville, A. (2016). Deep learning. MIT Press.
- Hinton, G. E., Osind, R., & Williams, R. (2006). Reducing the dimensionality of data with stacked denoising autoencoders. Neural Networks, 191.
- Hochreiter, S., & Schmiduber, J. (1997). Long short-term memory. Neural Computation, 9(8), 1735–1780.
- Jin, W., Mahmoud, P., & Welling, M. (2016). Unsupervised-feature extraction. International Conference on Machine Learning, 32, 1398–1407.
- Kazak, D. (2019). Variational inference for Parkinson's disease. Universidade de Lisboa.
- Kingma, D., & Welling, M. (2013). Stochastic propagation in deep generative models. arXiv:1312.6194.
- LeCun, Y., Bottou, L., & Haffner, P. (1998). Backpropagation applied to handwritten digit recognition. Proceedings of the IEEE, 86(11), 27.
- LeCun, Y., Bengio, Y., & Bengio, G. (2015). Deep learning. Nature.
- Lundberg, M., & Lee, S-I. (2017). An unified approach to interpreting predictions. Proceedings of the 31st International Conference on Neural Information Systems, 4768–4777.
- Magzani, A., Frey, B. (2011). Sparse autoencoders. CS294 Lecture Notes.
- Olshausian, A., & Field, Y. (1997). Sparse coding with overcomplete basis. Vision Research, 37(3), 3311–3325.
- Rasmussen, C., & Williams, R. (2005). Gaussian processes for machine learning. Cambridge, MA: MIT Press.
- Rezende, D., Mohamed, S., & Wierstra, D. (2014). Variational inference in deep generative models. Deep learning workshop.
- Schuster, M., & Palival, K. (1997). Bidirectional recurrent neural networks. In NIPS, 69–106.
- Sutever, I., Vinyals, O., & Lee, Q. Q. (2014). Sequence to sequence learning with neural networks. Advances in Neural Information Processing Systems, 3104–3112.
- Snoek, J., Larochelle, H., & Adams, R. (2012). Bayesian optimization of machine learning algorithms. Advances in Neural Information Processing Systems.
- Soulie, F. F., Gallinari, P., Lecun, Y., & Theria, S. (1987). Evaluation of network architectures on learning tasks. NYU.
- Williams, R., & Zipser, D. (1989). A learning algorithm for continually running recurrent neural networks. Neural Computation, 270–280.

