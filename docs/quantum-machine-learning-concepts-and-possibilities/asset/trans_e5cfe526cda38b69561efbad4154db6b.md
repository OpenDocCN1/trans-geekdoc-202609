

表 1.1. 经典机器学习与量子机器学习术语的对应关系。经典模型在向量和实值函数上运行，而量子模型则使用参数化电路和观测量来操纵量子态。

| 经典机器学习 | 量子机器学习 |
|---|---|
| 数据 | 量子态 |
| 模型 | 参数化电路 |
| 特征映射 | 数据编码 |
| 损失函数 | 观测量 |
| 训练 | 优化 |

相比之下，无监督学习寻求在没有显式标签的情况下，通过识别聚类、降维或学习生成式表示来揭示数据中隐藏的结构。在两种设定中，泛化、过拟合和正则化的概念对于理解模型在未见数据上的性能上都是至关重要的。这些挑战的出现是因为学习者必须在灵活性和归纳偏差之间取得平衡——选择一个足够丰富以捕捉相关模式，但又有足够的约束以避免拟合噪声。

训练过程通常被建模为一个优化问题。代价函数（或损失函数）量化了模型预测与预期结果之间的差异，并使用梯度下降或其变体等优化算法迭代地调整模型参数。在深度学习中，假设类通常是具有数百万参数的高度非线性、分层函数组合。请参见表 1.1 中经典机器学习与量子机器学习术语的对应关系。考虑到此类模型的复杂性，经验证据表明，只要优化后的景观良好且模型容量足够，它们在大规模数据集上训练时可以表现得非常好。

当我们探索用于学习的量子模型时，这些基础思想将在贯书中反复出现。许多概念——如模型选择、泛化和优化——都适用于量子领域，但必须根据量子约束进行重新考虑，例如测量诱导的噪声、电路深度限制以及量子态制备和推理的概率性质。量子机器学习（QML）的挑战与前景在于识别经典框架中的哪些元素可以被量子机制增强或替换，并理解这种替换何时能产生实际收益。

## 1.5 量子机器学习分类

量子机器学习涵盖了广泛的算法策略，这些策略由数据与所用模型之间的相互作用塑造。其核心在于量子资源在分类、采样或生成建模等任务中是否优于经典方法。然而，并非所有机器学习算法都以相同的方式与量子力学接触。量子力学的利用程度不仅取决于算法是否在量子设备上运行，还取决于输入数据的性质。

一些量子机器学习方法旨在完全处理经典数据，将量子电路作为具有优势表达或可训练性的模型。另一些为量子原生任务设计的，例如从物理系统产生的量子态中学习。还有一些介于之间，使用经典输入但依赖子程序（如状态估计或核计算）来加速学习过程的特定部分。这种多样性导致需要一个统一的框架来区分机器学习的不同模式。为了对这些进行分类，以下分类根据两个正交标准提出了机器学习方法：学习的数据类型和执行学习的模型类型。这种分类不仅为读者提供了领域的地图，还强调了每种方法的假设、局限性和机会。

## 机器学习方法分类

机器学习算法可以根据两个特征进行粗分类：数据的性质和模型。

| 数据类型 | 模型类型 | 示例案例 |
|---|---|---|
| 经典 | 经典 | 标准 SVM、CNN、高斯混合、梯度提升 |
| 量子 | 量子 | 变分分类器、量子核方法、在经典数据集上训练的量子电路 |
| 量子 | 经典 | 影子层析、量子测量数据分类、量子传感器输出的经典后处理 |
| 量子 | 量子 | 全量子生成模型、量子自动编码器、量子态确定、量子增强测量 |

备注：

- 经典数据 + 量子模型类别最适用于使用混合量子经典算法的应用。
- 量子数据 + 量子模型适用于量子原生任务，例如量子纠错、状态分类或纠缠传感器网络。
- 某些算法（例如 QAN）根据生成器、判别器和数据编码的结构跨越多个类别。

本章通过概述动机、范围和书籍结构，为探索量子机器学习奠定了基础。我们介绍了驱动该领域的核心问题：量子计算如何在计算效率、模型表达或数据表示方面增强或重新学习任务。为了引导读者，我们回顾了量子计算和经典机器学习的关键原理，识别了指导后续章节的概念相似之处和差异。

本章的一个关键部分是根据输入数据和模型的性质对机器学习方法进行分类，这种分类为读者提供了一幅概念地图，帮助其在统一框架内定位各种算法、技术和应用。

在本章结束时，读者应该准备好应对量子与经典范式之间的交互，理解编码选择的重要性，并欣赏机器学习工作流的高级设计空间。书的剩余部分将在此基础上构建，从对量子原语和经典学习理论的详细检查开始，逐步迈向先进模型和领域的开放挑战。

## 参考文献

- [1] Biamonte J, Wittek P, Pancotti N, Rebentrost P, Wiebe N and Lloyd S 2017 Quantum machine learning Nature 549 195–202
- [2] Montano A 2016 Quantum algorithms: an overview npi Quantum Inf. 2 150233
- [3] Grover L K 1996 A fast quantum mechanical algorithm for database search Proc. 28th Annual ACM Symp. on Computing pp 212–219
- [4] Shor P W 1997 Polynomial-time algorithms for prime factorization and discrete logarithms on a quantum computer SIAM J. Comput. 26 1484–509
- [5] Cross A W, Smith G and Grolmal J 2015 Quantum learning robust against noise noise Phys. Rev. 92 012327
- [6] Rist D, da Silva M P, Ryan C A, Cross W A, Cócoles D, Smolin J A, Gambetta J M, Chow J M and Johnson B R 2017 Demonstration of quantum advantage in machine learning any Quantum Inf. 3 16
- [7] Tucanasalam S and de Wolf R 2017 Guest column: A survey of quantum learning theory ACM SIGACT News 48 41–67
- [8] Servideo R A and Gottler S J 2004 Equalities and separations between quantum and classical learnability SIAM J. Comput. 33 1067–92
- [9] Bernstein E and Vazirani U 1997 Quantum complexity theory SIAM J. Comput. 26 1411–73
- [10] Aci A and Servideo R 2007 Quantum algorithms for learning and testing quantum Quantum Inf. Process. 6 323–48
- [11] Havlíček V, Cócoles A D, Temme K, Harrow A W, Kandala A, Chow J M and Gambetta J M 2019 Supervised learning with quantum-enhanced feature spaces Nature 567 209–12
- [12] Schuld M and Killoran N 2019 Quantum machine learning in Hilbert spaces Phys. Rev. Lett. 122 040504

