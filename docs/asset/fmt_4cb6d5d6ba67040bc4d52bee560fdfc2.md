
图 11.6 说明了从损坏的训练数据集中学到的决策边界。图 11.6(a) 显示了决策边界如何被迫在测试数据上 `f[attack]` = 0.1 时大幅向负侧移动。`ρ` 值设置为 0.67。如图 11.6(b) 所示，`ρ` = 0.76 时学到的决策边界稍好一些。这个实验提醒我们设定 `ρ` 值下界的重要性。当 `ρ` 值太小时，输出中出现假阳性的可能性会更大。在实践中，我们建议 `ρ` 值不大于 0.5。然而，在对抗性攻击可能非常激进的任何领域，较小的 `ρ` 值更受青睐。

![图 11.6 调整决策边界以考虑潜在的对抗性攻击。图中的实线说明了决策边界。(a) Rho 值 = 0.67；(b) Rho 值 = 0.76。](img/fig11_6.jpg)

图 11.6 调整决策边界以考虑潜在的对抗性攻击。图中的实线说明了决策边界。(a) Rho 值 = 0.67；(b) Rho 值 = 0.76。

与其他任何基于核的方法一样，选择初始 `η` 值很重要。较小的 `η` 值可能导致学习模型对训练样本过度敏感。较大的 `η` 值可能导致严重的过拟合。从负面来看，这可能需要交叉验证，增加额外的计算成本。从正面来看，不合适的初始 `η` 值往往会迅速导致非正定特征向量的退化，从而导致求解器过早终止。如果发生这种情况，通常意味着需要更大的 `η` 值。

### 11.5.3 真实数据集上的实验

我们实验中使用的两个真实数据集是：来自 UCI 数据仓库的 `spam base` ([`archive.ics.uci.edu/ml`](http://archive.ics.uci.edu/ml))，以及来自 LibSVM 网站的 `web spam` ([`www.csie.ntu.edu.tw/~cjlin/libsvmtools/datasets/`](http://www.csie.ntu.edu.tw/~cjlin/libsvmtools/datasets/))。

这两个数据集均收集自通常运行在对抗性环境中的应用。

在 `spam base` 数据集中，总共有 4,601 个电子邮件示例，其中 39.4% 是垃圾邮件。每个示例用 57 个属性和一个类标签表示。在我们的实验中，数据集被分成两半，一半用于训练，另一半用于测试。每次运行随机抽取 5% 的训练数据来构建四个学习模型。结果取 10 次随机运行的平均值。表 11.2 显示了四种学习算法的分类错误率。当 `f[attack]` 0.5 时，单类 SVM 输出最佳结果，而我们的对抗性 RVM 算法排名第二，且性能优于 RVM 和 SVM。当 `f[attack]` > 0.5 时，我们的 AD-RVM 优于所有其他算法。

表 11.2 AD-RVM、RVM、SVM 和 1-CLASS SVM 在 spam base 数据集上的分类错误。最佳结果已加粗

| | `f[attack]` |
| --- | --- | --- | --- | --- | --- |
| | 0.1 | 0.3 | 0.5 | 0.7 | 0.9 |
| AD-RVM | 0.3158 | 0.3270 | 0.3368 | **0.3438** | **0.3809** |
| RVM | 0.3875 | 0.3753 | 0.3775 | 0.3899 | 0.3902 |
| SVM | 0.3641 | 0.3751 | 0.3793 | 0.4149 | 0.4079 |
| 1-class SVM | **0.3127** | **0.3147** | **0.3248** | 0.3555 | 0.4011 |

`web spam` 数据集是来自 LibSVM 网站的单元版本。每个示例有 254 个特征。我们进一步将特征数量减少到 50 个。实例总数为 350,000。我们用一半进行训练，另一半进行测试。我们随机选择训练集中 2% 的样本来构建学习模型。结果取 10 次随机运行的平均值，如表 11.3 所示。可以观察到，对抗性 RVM 明显优于其他三个模型。

表 11.3 AD-RVM、RVM、SVM 和 1-CLASS SVM 在 web spam 数据集上的分类错误。最佳结果已加粗

| | `f[attack]` |
| --- | --- | --- | --- | --- | --- |
| | 0.1 | 0.3 | 0.5 | 0.7 | 0.9 |
| AD-RVM | 0.2426 | **0.2926** | **0.3373** | **0.4945** | **0.5866** |
| RVM | **0.2355** | 0.3169 | 0.4541 | 0.5560 | 0.5876 |
| SVM | 0.2725 | 0.4725 | 0.5604 | 0.6061 | 0.6061 |
| One-class SVM | 0.3155 | 0.5625 | 0.5945 | 0.6009 | 0.5997 |

## 11.6 总结与展望

### 数据挖掘任务与对抗学习

当对手通过修改恶意数据以逃避检测来发起攻击时，数据挖掘任务变得更加复杂。主要挑战在于找到一种对不可预测的恶意数据分布不敏感的鲁棒学习模型。在本章中，我们提出了一种用于对抗学习的稀疏相关向量机集成。我们工作的创新之处在于使用个性化的核参数在模型训练期间对潜在的对抗攻击进行建模。我们允许核参数向最小化正类数据似然的方向漂移。这一步骤与学习相关向量机的权重和权重先验交织进行。我们的实证结果表明，此类相关向量机模型的集成对对抗攻击更具鲁棒性。

我们提出了一种稀疏贝叶斯对抗学习模型。该算法设置个体核参数，通过最小化训练集中正实例的对数似然，在特征空间中对对抗攻击进行建模。在这种设置下训练的学习模型对包括极具侵略性攻击在内的各类攻击更具鲁棒性。一个开放性问题是发现一种能同时高效更新核参数和学习参数的方法。该解决方案将有助于在样本空间中找到针对最坏情况攻击的最优学习模型。

## 参考文献

*   **[AUER1998]** P. Auer, N. Cesa-Bianchi, On-Line Learning with Malicious Noise and the Closure Algorithm, Annals of Mathematics and Artificial Intelligence, Volume 23, # 1–2, 1998, 83–99.

*   **[BRÜC2009]** M. Bruckner, T. Scheffer, Nash Equilibria of Static Prediction Games, Advances in Neural Information Processing Systems, MIT Press, 2009.

*   **[BRÜC2011]** M. Bruckner, T. Scheffer, Stackelberg Games for Adversarial Prediction Problems, *Proceedings of the 17th ACM SIGKDD*, ACM, 2011.

*   **[BSHO1999]** N.H. Bshouty, N. Eiron, E. Kushilevitz, PAC Learning with Nasty Noise, Theoretical Computer Science, Volume 288, 1999, 2002.

*   **[DALVI2004]** N. Dalvi, P. Domingos, Mausam, S. Sanghai, D. Verma, Adversarial Classification, *Proceedings of the Tenth ACM SIGKDD*, ACM, 2004, pp. 99–108.

*   **[DEKE2008]** O. Dekel, O. Shamir, Learning to Classify with Missing and Corrupted Features, *Proceedings of the International Conference on Machine Learning*, ACM, 2008, pp. 216–223.

*   **[DEKE2010]** O. Dekel, O. Shamir, L. Xiao, Learning to Classify with Missing and Corrupted Features, Machine Learning, Volume 81, # 2, 2010, 149–178.

*   **[GHAO2003]** L. El Ghaoui, G.R.G. Lanckriet, G. Natsoulis, Robust Classification with Interval Data, EECS Department, Tech. Rep. UCB/CSD-03-1279, UC Berkeley, October 2003.

*   **[GLOB2006]** A. Globerson, S. Roweis, Nightmare at Test Time: Robust Learning by Feature Deletion, *Proceedings of the 23rd ICML*, ACM, 2006, pp. 353–360.

*   **[KANT2011]** M. Kantarcioglu, B. Xi, C. Clifton, Classifier Evaluation and Attribute Selection against Active Adversaries, Data Mining and Knowledge Discovery, Volume 22, January 2011, 291–335.

*   **[KEAR1993]** M. Kearns, M. Li, Learning in the Presence of Malicious Errors, SIAM Journal of Computing, Volume 22, 1993, 807–837.

*   **[LANC2002]** G.R.G. Lanckriet, L.E. Ghaoui, C. Bhattacharyya, M.I. Jordan, A Robust Minimax Approach to Classification, Journal of Machine Learning Research, Volume 3, 2002, 555–582.

*   **[LIU2010]** W. Liu, S. Chawla, Mining Adversarial Patterns via Regularized Loss Minimization, Machine Learning, Volume 81, October 2010, 69–83.

*   **[LOWD2005]** D. Lowd, C. Meek, Adversarial Learning, *Proceedings of the Eleventh ACM SIGKDD International Conference on Knowledge Discovery in Data Mining, Chicago, IL*, August 2005, pp. 641–647.

*   **[TEO2007]** C.H. Teo, A. Globerson, S.T. Roweis, A.J. Smola, Convex Learning with Invariances, Proceedings of the 20th International Conference on Neural Information Processing Systems (NIPS), *Vancouver, Canada*, December 2007, pp. 1489–1496.

*   **[TIPP2001]** M.E. Tipping, Sparse Bayesian Learning and the Relevance Vector Machine, Journal of Machine Learning Research, Volume 1, September 2001, 211–244.

*   **[ZHOU2012a]** Y. Zhou, M. Kantarcioglu, B. Thuraisingham, B. Xi, Adversarial Support Vector Machine Learning, *Proceedings of the 18th ACM SIGKDD*, ACM, 2012, pp. 1059–1067.

*   **[ZHOU2012b]** Y. Zhou, M. Kantarcioglu, B.M. Thuraisingham, Sparse Bayesian Adversarial Learning Using Relevance Vector Machine Ensembles, ICDM 2012, pp. 1206–1211.

# 12 隐私保护决策树

DOI: [10.1201/9781003081845-20](https://doi.org/10.1201/9781003081845-20)

## 12.1 简介

虽然第 10 章和第 11 章侧重于安全感知数据科学，但本章我们将讨论隐私感知数据科学。特别是，我们以决策树为例讨论隐私保护数据挖掘。数据挖掘技术（现已演变为机器学习和数据科学技术）被用于从海量数据中推导模式 [THUR1998]。然而，此类技术可能会提取出先前已知的“金块”。这些“金块”可能会侵犯个人隐私 [THUR2002]。由于与隐私相关的担忧日益增加，已经开发出各种隐私保护数据挖掘技术来解决不同的隐私问题 [THUR2005]。这些技术包括隐私保护关联规则挖掘技术和隐私保护决策树 [AGRA2000, AGGA2004, LIU2009]。隐私保护数据挖掘的理念是对数据进行随机化和/或扰动，然后再进行数据挖掘。这样敏感数据就能保持私密性。图 12.1 说明了隐私保护数据挖掘背后的理念。

![图 12.1 隐私保护数据挖掘。](img/fig12_1.jpg)

图 12.1 隐私保护数据挖掘。

正如第 3 章所述，隐私保护数据挖掘技术通常在各种假设下运行并采用不同的方法。之前的工作主要分为两类：(1) 基于扰动和随机化的方法，以及 (2) 基于安全多方计算的方法。对于基于扰动的方法，数据会被扰动，以便保持敏感数据的私密性。对于随机化方法，会向数据中引入随机值。对于基于安全多方计算的方法，理念是每一方加密其秘密。隐私保护数据挖掘在加密的秘密上进行。最终结果会透露给各方。然而，每一方的秘密仅为该方所知。

早期的扰动和随机化方法包含一个重构原始数据分布的步骤。该领域较新的研究采用不同的数据扭曲方法或修改数据挖掘技术，使其更适合扰动场景。采用加密工具构建数据挖掘模型的安全多方计算方法面临着高昂的通信和计算成本，尤其是在参与计算的参与方数量较大时。

### 保护隐私的决策树分类

在本章中，我们重点关注在隐私保护数据挖掘中广泛使用的扰动方法。它与之前的几种技术不同之处在于，我们直接从扰动数据构建数据挖掘模型，而不试图将通用数据分布重构作为中间步骤。在我们的解决方案中，我们修改数据挖掘算法，使其能直接用于扰动数据。换句话说，我们直接从扰动训练数据集构建原始数据集的分类器。

更确切地说，我们描述了一种修改后的 `C4.5` [QUIN1993] 决策树分类器，它可以处理扰动后的数值连续属性。我们的保护隐私决策树 `C4.5` (`PPDTC4.5`) 分类器使用扰动训练数据，并构建一个可用于对原始或扰动数据集进行分类的决策树模型。我们的实验表明，当用于对原始数据集进行分类时，我们的 `PPDTC4.5` 分类器能获得高度的准确性。我们选择决策树进行此项研究，是因为许多先前的方法都集中在隐私保护关联规则挖掘上。此外，我们在隐私保护决策树方面的努力，是开发决策树隐私感知方法这一更大规模工作的一部分 [LIU2009]。

本章组织结构如下：第 12.2 节 介绍相关工作。第 12.3 节 介绍我们工作中用于度量隐私的隐私度量体系。第 12.4 节 展示决策树的构建。第 12.5 节 描述如何从扰动数据集构建朴素贝叶斯模型。在 第 12.6 节 中，我们详细解释我们的 `PPDTC4.5`。第 12.7 节 展示我们的实验结果。在 第 12.8 节 中，我们通过对未来工作的讨论进行总结。

## 12.2 相关工作与动机

隐私保护数据挖掘的先前工作解决了两个问题。其中之一旨在通过扰动数据值来保护客户隐私 [AGRA2000]。在该方案中，引入随机噪声数据以扭曲敏感值，并利用随机数据的分布生成一个接近原始数据分布但不泄露原始数据值的新数据分布。估计的原始数据分布用于重构数据，并将分类器和关联规则等数据挖掘技术应用于重构后的数据集。后来，该方法的改进基于扭曲数据收紧了对原始值的估计 [AGRA2000]。数据扭曲方法也已应用于布尔值的研究工作中 [DU2003, EVFI2002, RIZV2002]。扰动方法及其隐私保护受到批评，因为某些方法可能从重构步骤中推导出私人信息 [KARG2003]。

不同于 [AGRA2000] 中最初的噪声加法方法，已提出许多独特的扰动方法。一个重要类别是乘法扰动方法。从数据几何属性的角度来看，用随机噪声矩阵乘以原始数据值相当于旋转原始数据矩阵，因此也称为基于旋转的扰动。在 [CHEN2005] 中，作者给出了“旋转不变分类器”的可靠证明，表明某些数据挖掘工具可直接应用于基于旋转扰动的数据。在后来的工作 [LIU2006] 中，Liu 等人提出了乘法随机投影，提供了更强的隐私保护。还有一些其他有趣的技术，如基于凝聚的方法 [AGRA2000]、矩阵分解 [XU2006] 等。正如 [LIU2007] 所指出的，这些近期关于基于扰动方法的研究工作直接将数据挖掘技术应用于扰动数据，跳过了重构步骤。选择合适的数据挖掘技术取决于引入噪声的方法。据我们所知，只有少数工作专注于映射或修改数据挖掘技术以满足扰动数据的需求。
