
# 021 IEEE 国际图像处理会议 (ICIP) ｜｜ Man-Recon：用于流形学习的 Man-Recon

## 摘要

深度学习在监督的情况下可以提取丰富的表示。对于许多任务，由于需要高水平的领域专家知识（例如地震解释中），标注数据需要付出大量的时间和金钱成本。无监督学习可以识别出对解释者学习最有价值的样本，从而提高效率。我们提出了一种基于流形学习的方法，用于联合识别并训练与无监督任务中学习到的流形最不相似的样本。我们在两个地震数据集（荷兰 F3 调查数据）上验证了所提方法的有效性，实现了 0.773 的最高交并比（IoU）值。

**索引术语—** 深度学习、主动学习、自动编码器、解释、流形

## 1. 引言与相关工作

由于能够从原始数据中学习深层表示，深度学习在计算机视觉和图像处理领域取得了突破性进展。相比之下，地震解释需要专家来配置机器学习算法。对于模型要使用基于深度学习的方法学习有效表示，对大量标注数据的需求是许多实际应用（如医学数据集、地下成像和许多其他应用）中的瓶颈。

话虽如此，通常存在一个较小的训练样本子集，可以维持整个数据在表示空间中的努力 [1]。使用识别出的子集训练样本的DL模型在未见测试用例上的性能优于随机选择的较少训练样本。这是因为主动学习是基于 [2]。人类专家（也称为先知者，Oracle）在第一个循环中标记少数训练样本。在随后的每个循环中，该方法会根据预定义的标准（例如不确定性）在未标记数据集中识别并由专家标记一小部分样本，以向机器学习模型增加最丰富的信息 [2]。

我们在工作中提出了一种基于使用自动编码器学习流形的主动学习方法。自动编码器学习一种可以重建其输入的模型流形。它们的设计使得它们只能从其学习的分布中重建数据，这从回归映射到简单映射。通过这种方法，我们通过对基于输入样本的重建误差分布进行阈值处理，学习用于数据集异常检测的流形。

主动学习算法的挑战在于识别与预存训练样本最不相似的样本。这些训练样本最可能为学习模型提供关于其不确定数据的最丰富信息。

最重要的应用之一是是用于能源和矿产资源的地球地下成像。具体而言，我们关注迁移地震体数据上的地球地下地层分割任务 [6], [7]。该任务需要标注数据，而这些数据通常是不可用的。因此，目标是为所提问题寻找良好的拟合。我们提出了一种特定的编码器-解码器架构，使用相同的潜在空间进行重建和地震地层分割。

在本文中，我们介绍了流形学习的方法及其在地球地下成像和能源资源中的应用。重建误差也将是网络在分割上表现差的部分。识别此类训练样本与随机采样或以其他任意方式采样的相同数量剖面相比，将提高整体的泛化能力。据我们所知，通过将所提工作与基准主动学习方法以及其他此类地下成像和医学诊断的其他数据采样策略进行比较，验证了这一点。我们将讨论限制在此地震解释任务中。简而言之，我们在工作中的主要贡献有三点：

- 提出了一种基于深度自动编码器流形学习的新型主动学习方法；
- 使用用于监督和无监督任务的共享表示学习框架，学习具有高重建误差的分割信息丰富样本；
- 通过与地震体领域的其他标准方法对比，验证了所提工作的有效性。

## 2. 方法

图1展示了主动学习设置的概述。解释者（Oracle）指定了特定数量的主动学习循环N。在每个循环中，解释者在数据体中随机选择一个剖面，将其地层提供给网络。通过最小化由重建误差和交叉熵损失组成的目标函数对网络进行300个epoch训练：

```
\hat{y}_j, \hat{x}_j = D_{\theta}(E_{\phi}(x_j)), j = 1, ..., |D_{train}|.
```

```
L_{reco} = \sum_{j=1}^{|D_{train}|} ||\hat{x}_j - x_j||^2,
```

```
L_{CE} = \sum_{j=1}^{|D_{train}|} CE(y_j, \hat{y}_j)
```

其中`D_{train}`是训练集中所有活动样本和标签对，`D_{\phi}`和`D_{\theta}`分别是具有参数`\phi`和`\theta`的编码器和解码器网络，`x_j`和`y_j`分别为第`j`个训练用的剖面和标签图像，`\hat{y}_j`和`\hat{x}_j`分别为重建和预测标签。然后通过优化重建和交叉熵损失项的加权和求解最优模型。

### 2.2 架构

工作中使用的网络架构使用了具有收缩和扩张路径的卷积自动编码器。收缩路径中的每个块由减少激活值的卷积层组成。相反，扩张路径由转置卷积后的卷积层组成。转置卷积用于将激活上采样2倍。总体，层使用大小为3的填充以确保维度一致性。网络的输入是一个完整的剖面。网络输出相应的预测标签。

### 2.3 训练细节

**算法1：用于地震地层的主动学习**

1. 从`D_{out}`中采样`x_j`。
2. 构建初始训练数据`D_{train} = {x_j, y_j}`。
3. 对于`i=1`到`N`：
   - 获取所有`x \in D_{out}`的重建误差。
   - 选择误差最大的剖面`x_j = \arg\max`。
   - 构建训练集`D_{train} \cup {x_j, y_j}`。
   - 预测`x \in D_{out}`的标签。

![](img/766fb7f81122e8d898202e3a8c3d3113_3_0.png)

图 2：所提方法、随机采样法和基于熵方法的每周期平均交并系数（mOU）。

本报告中的方法通过在每个周期内采样最少代表性的交测线来达到最佳效果。这是因为在每个周期中，网络被强制学习与训练集差异最大的样本，以搜索对所学自动编码器流形性能的实验。

最后，图3a和3b展示了两个不同活动周期下数据集中交测线的重建误差剖面和交叉熵剖面（高亮部分）。请注意，只有在具有地面真值（在本情况下为真实值）时才能观察到潜变量，而前者适用于没有地面真值的情景。有趣的是，如图所示，交叉熵误差剖面最终决定了与重建误差剖面相关的性能。例如，在交测线500附近有一个峰值，大约在另一个处也有一个峰值。这表明网络尝试为重建和分割任务学习相似的表示，因此在某一个任务中表现较差的训练样本在另一个任务中也可能表现。

## 4. 结论

![](img/766fb7f81122e8d898202e3a8c3d3113_3_1.png)

图 3：两个重建误差剖面及其相应的熵误差剖面图。

本文描述了一种主动学习方案，用于在对手动分割的数据集进行解释任务时识别出最具信息量的样本。在初始和已标记的交测线上，针对重建（无监督）和分割（有监督）任务联合训练了一个编码器-解码器架构。网络用于对训练实例进行推理，以获得重建误差剖面。随后对对应误差最大的训练示例进行标记，并添加到数据集中用于下一个训练周期。其底层假设是，由于网络的共享表示，该样本提供了关于分割任务数据集最丰富的信息。通过与文献中的其他标准采样方法进行比较，验证了该方法的有效性。所提方法在完整数据集上达到了0.773的最高mOU值，优于其他方法。

## 5. 参考文献

[1] Angelos Katharopoulos and Francois Fleuret, “Not all samples are created equal: Deep learning with importance sampling,” in Proceedings of the 35th International Conference on Machine Learning, Jennifer Dy and Andreas Krause, Eds., Stockholm, Sweden, 10-15 Jul 2018, vol. 80 of Proceedings of Machine Learning Research, pp. 2525–2534, PMLR.

[2] Burr Settles, “Active learning literature survey,” Tech. Rep., 2010.

[3] Francisco J. Martínez-Manuel, Andres Ortiz, Juan-Manuel Gomez, Javier Ramirez, and Diego Castillo-Bares, “Studying the manifold structure of alzheimer’s: A deep learning approach using convolutional autoencoders,” IEEE Journal of Biomedical and Health Informatics, vol. 24, no. 1, pp. 17–26, Jan. 2020.

[4] Gukyong Kwon, Mohit Prabhushankar, Dogacan Temel, and Ghassan AlRegib, “Backpropagated gradient representations for anomaly detection,” in Proceedings of the European Conference on Computer Vision (ECCV), 2020.

[5] Feng Qian, Miao Yin, Xiao-Yang Liu, Jun-Wang Gan, Cai Lu, and Guang-Min Hu, “Unsupervised seismic facies analysis via deep autoencoders,” GEOPHYSICS, vol. 83, no. 3, pp. 5–18, 2018.

[6] Zayed AlRegib, Patricia Michalowicz, Motafar Alaraj, and Ghassan AlRegib, “A machine-learning benchmark for facies classification,” Interpretation, vol. 7, no. 3, pp. SE15–SE187, Aug. 2019.

[7] Ming Liu, Michael Jeremy, Weichang Li, and Philippe Nivelet, “Seismic facies classification using unsupervised neural networks and semisupervised generative adversarial networks,” GEOPHYSICS, vol. 85, no. 4, pp. O047–O058, 2020.

[8] Vladimir Putsky and Chris Elders, “Unsupervised seismic facies classification using deep autoencoder,” arXiv:1802.01995, 2020.

[9] Adam Pascale, Sam Gross, Francesco Massa, Adam Lerer, James Bradley, Gregory Chaney, Trevor Kileen, Zeming Lin, Natalia Gelsmacher, Luis Antiga, Alban Delman, Andreas Kopt, Eddie Yang, Zhang Devlin, Benoit Steiner, Lu Fang, Jung-jie Bai, and Soumith Chilaankurthy, “Pytorch: An adaptive programming style, high-performance deep learning,” in Advances in Neural Information Processing Systems 32, H. Wallach, H. Larochelle, A. Beygelzmer, F. d’Alché, E. Fox, and R. Garnet, Eds., pp. 8024–8035. Curran Associates, Inc., 2019.

[10] Diederik P. Kingma and Jimmy Ba, “Adam: A method for stochastic optimization,” arXiv:1412.6980, 2017.
