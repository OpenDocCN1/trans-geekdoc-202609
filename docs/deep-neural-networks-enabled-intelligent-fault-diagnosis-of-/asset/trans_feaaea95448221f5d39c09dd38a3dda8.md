

# 基于深度神经网络的机械系统智能故障诊断

比较研究的结果也列在表 3.2 中。根据诊断结果，第一种方法在故障诊断任务中失败。使用未经过预处理的原始振动信号，单隐藏层 BP 网络无法实现分类。对于时域分析，测试中使用的不同特征给出不同的结果，这意味着准确的分类需要人工干预来为故障诊断任务选择合适的特征。与使用未处理数据的 DBN 相比，小波分析提供了相似的结果，但它需要先对信号进行预处理，且结果还取决于提取的特征是否适用于该任务；使用信号频率分布的 DBN 在所有实验中实现了最高的分类率。此外，所提出的基于 DBN 的方法结合了特征学习与分类，提高了故障诊断的效率。这些实验证明该方法是感应电机故障的有效方法。

对于传统的故障诊断，由于原始振动信号始终包含大量的噪声，一个关键步骤是数据处理，以消除噪声并提取分类的相关信息。稳健且有效的特征提取需要高质量的工程经验和专业知识，这往往是挑战性的且难以获得的。与传统的故障诊断方法相比，基于 DBN 的深度学习架构可以自动从输入中学习表示并减少人工工作，从而减少人为因素的影响。

图 3.8 分别显示了 DBN 和 FFT-DBN 模型进行验证实验的详细标签分布。结果表明，FFT-DBN 模型在感应电机故障诊断任务中比 DBN 模型具有更好的分类能力，因为 FFT-DBN 模型只有 1 个分类错误，而 DBN 模型在标签 2、3 和 5 上存在混淆。这说明信号的频率分布适用于 DBN 模型的应用，而 DBN 架构无法很好处理输入数据的时间信息，这可能会影响后续的分类过程。

图 3.9 显示了这两个模型的训练误差和分类率。通过比较，FFT-DBN 模型收敛速度更快，分类率更高。DBN 模型在学习过程中存在波动，这意味着该架构可能不够稳定，无法为分类任务学习准确的模型。

# DBN 架构尺度与深度的影响

在本节中，通过实验研究感应电机应用中分类性能与不同架构之间的关系。研究了同时使用时域信号的 DBN 模型和使用信号频率分布的 FFT-DBN 模型，并展示和讨论了比较结果。

在实验中，考虑了 10 到 100 个以及 100 到 150 个神经元。隐藏层被探索为六层。每组实验重复 50 次，并计算平均分类率作为深度架构的评估指标。分别对 DBN 模型和 FFT-DBN 模型进行了测试，结果如图 3.10 所示。

![](img/f29bba55de4872c43f26af4667e705f2_63_0.png)

![](img/f29bba55de4872c43f26af4667e705f2_63_1.png)

图 3.8 测试数据集的标签分布。(a) 使用时域振动信号的 DBN 模型。(b) 使用频域信号的 FFT-DBN 模型。

![](img/f29bba55de4872c43f26af4667e705f2_64_0.png)

图 3.9 (a) 所提出的 FFT-DBN 模型和 DBN 模型的训练误差和 (b) 分类率。(a) 随 epoch 变化的训练误差和b) 随 epoch 变化的分类率。

从结果来看，DBN 模型对架构的尺度和深度敏感，因为不同网络之间的分类率存在明显差异。具有四个隐藏层的 DBN 架构（图 3.10(a) 中的绿线）具有最佳分类率。仅有一个隐藏层的 DBN 无法精确模拟输入数据，而当隐藏层增加到五层或六层时，分类结果变得不稳定，表明存在过拟合问题。换句话说，训练的模型太复杂，无法对输入建模，导致泛化能力变差。另一方面，当神经元数量小于 100 时，DBN 模型的分类率低于 90%。随着神经元数量增加，分类率

![](img/f29bba55de4872c43f26af4667e705f2_64_1.png)

图 3.10 在 (a) DBN 模型和 (b) FFT-DBN 模型中不同隐藏层和隐藏神经元的不同分类结果。

有所提高；当神经元数量增加到 1000 时，分类率开始下降，表明过多的神经元会导致过拟合，影响模型的分类能力。

与 DBN 模型的分类结果相比，FFT-DBN 模型的结果稳定得多，如图 3.10(b) 所示。随着隐藏神经元的增加，波动很小，但极少数例外外，分类率都在 99% 以上。一个是具有六个隐藏层且每层十个隐藏单元的网络，太窄而无法学习足够的表示；另一个是五个隐藏层每层 1500 个神经元的网络，由于输入数据并不复杂，存在过拟合的可能性。然而，FFT-DBN 模型在各种网络结构中表现良好，准确性和稳定性都很高。

通过比较，使用时域信号的 DBN 模型分类率低于使用频率分布的模型，这意味着 DBN 架构无法处理单元间的关联。时域信息的连接会导致模型不准确。因此，将频率分布作为输入引入 DBN，为感应电机故障诊断提供了良好的解决方案。

# 结论

本文介绍了一种基于 DBN 的深度学习模型，将测量数据的频率分布作为输入用于电机故障诊断。该深度架构使用 RBM 作为构建单元，并采用逐层训练。所提出的方法利用了 DBN 的强大能力，可以对高维数据建模并学习多层表示，减少训练误差并提高分类准确率。通过振动信号进行的实验研究验证了 DBN 模型在特征学习方面的有效性，为自动故障诊断提供了新方法。

# 参考文献

Antonino-Davius, Jose, Selin Aviyente, Elias G. Strangas, and Martin Ria-Guasp. 2013. "Scale Invariant Feature Extraction Algorithm for the Automatic Diagnosis of Rotor Asymmetries in Induction Motors IEEE Transactions on Industrial Informatics 9 (1): 100–8. https://doi.org/10/f4ijrs8

Arel, Derek C. Rose, and Thomas P. Karnkowski. 2010. "Research Deep Machine Learning—A New Frontier in Artificial Intelligence." IEEE Computational Magazine 5 (4): 13–28. https://doi.org/10/cxmtqbb

Bengio, Yoshua. 2009. "Deep Learning Architectures for AI." and Trends in Machine Learning 2 (1): 1–11. https://doi.org/10/tgfnv3

Bengio, Yoshua, Pascal Lamblin, David Popov, and Hugo Larochelle. 2006. "Greedy-wise Training of Deep Networks." In Advances in Neural Information Processing Systems. Vol. 19. MIT Press. https://proceedings.neurips.cc/paper/2006/hash/5da713a690c067105aeb2fae3203405-Abstract.html.

Boashash, Boualem. 2015. Time-Frequency Signal Analysis and Processing: A Comprehensive Reference. Academic Press.

