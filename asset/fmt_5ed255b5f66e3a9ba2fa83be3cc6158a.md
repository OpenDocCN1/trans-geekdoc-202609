
7. Holland, J. H. (1992). Adaptation in natural and artificial systems: An introductory analysis with applications to biology, control, and artificial intelligence. MIT Press, 1992. Online ISBN: 9780262275552.

8. Sutton, R. S. and Barto, A. G. (2018). Reinforcement learning: An introduction. MIT Press, 2018. ISBN 0262039249, 9780262039246.

9. National Institute of Diabetes and Digestive and Kidney Diseases. (2023). Diabetes Data Set. UCI Machine Learning Repository. [Online]. Available: [`archive.ics.uci.edu/ml/datasets/diabetes`](https://archive.ics.uci.edu). Accessed: [August 5, 2023].

10. Kingma, D. P. and Ba, J. (2014). Adam: A method for stochastic optimization. arXiv preprint arXiv:1412.6980. Cornell University, 1, 1–8. [`doi.org/10.48550/arXiv.1412.6980`](http://dx.doi.org/10.48550/arXiv.1412.6980).

11. Goodfellow, I., Bengio, Y., Courville, A., and Bengio, Y. (2016). Deep learning. 1. MIT Press Cambridge, 2016. ISBN: 9780262035613, pp 800.

12. Vargas, D. V. and López, J. F. (2018). Evolutionary algorithms for hyperparameter optimization in machine learning: A review. J. Mac. Learn. Res., 19(1), 277–308.

13. LeCun, Y., Bengio, Y., and Hinton, G. (2015). Deep learning. Nature, 521(7553), 436–444.

14. Sutskever, I., Martens, J., Dahl, G., and Hinton, G. (2013). On the importance of initialization and momentum in deep learning. Proc. 30th Int. Conf. Int. Conf. Mac. Learn., 28, 1139–1147.

# 10 使用机器学习算法检测 ISP 网络中良性和恶意 DNS 流量

Avinash Singh^(¹⁰)

## 摘要

本文提出了一个工作模型，用于利用数据科学和机器学习（ML）检测互联网服务提供商（ISP）网络流量中真实和伪造的域名系统（DNS）流量。当任何主机访问网络进行 DNS 查询或邮件交换记录时。基于源端口、目的端口、源地址和目的地址，我们使用各种端口镜像技术在一定时间内从路由器端口记录净流量。采用了一种模式，使用每个记录的 DNS 请求数量及其响应。两种机器学习模式 K-最近邻（KNN）、朴素贝叶斯（NB）用于分类目的，并进一步用于预测和分析数据中的行为。我们使用预测来对准确率和训练时间作为性能指标进行分类，以找出哪种算法比另一种更准确。用于训练和测试算法的数据集包含多种恶意和真实端口以进行分类。

**关键词：** DNS, 端口镜像, 净流量, K-最近邻（KNN）, 朴素贝叶斯（NB）

## 1. 引言

每个互联网服务提供商（ISPs）都有自己的 DNS 服务器，为客户端提供名称解析和反向查询服务。DNS 服务器使用端口 `53` 的用户数据报协议（`UDP`）和传输控制协议（`TCP`）来执行其活动。作为 DNS 请求，目标端口为 `53`，源端口为 `1023` 以上的任意端口；对于 DNS 响应，源端口为 `53`，目标端口为 `1023` 以上的任意端口。当两个 DNS 服务器传输其区域文件时，源端口和目标端口均为端口 `53`（`TCP`）。

互联网呈指数级增长，这对所有系统和网络管理员实现信息安全目标——保密性、完整性和可用性——来说是一个巨大的挑战。这就是为什么需要持续的网络监控、分类和安全分析。入侵检测系统（`IDS`）和入侵防御系统（`IPS`）要么基于内容，要么基于行为，无法防御各种攻击 [1, 2, 3 和 4]。

如今，大多数研究人员使用网络流流量来减轻或对抗各种类型的攻击和恶意流量。网络流记录包含可用于各种目的的各种信息，其中一个重要目的是对网络进行安全分析。我们捕获了为期 1 个月的时间段的网络流数据。然后应用数据可视化从数据集中获得某些模式。在应用机器学习（`ML`）模型后，比较了 K-最近邻（`KNN`）和朴素贝叶斯（`NB`）机器学习分类器之间的单独性能以找出准确率 [5, 6, 7 和 8]。

## 2. 问题陈述

为了识别针对 DNS 服务的良性和恶意流量，以提高服务质量、安全性和效率，我们必须分析网络中的模式。流量量、流量类型、流量的源和目标等。

我们的重点是使用数据科学和各种 ML 语言开发一个工作模型，以可视化、分析和预测网络中的流量类型以及这些流量对 ISP 网络的影响。

作为对潜在危险的保险政策。利用一系列供应商提供了一层额外的保护，这是其好处之一。这导致网络具有增强的保护级别，因为可能能够通过由一个供应商提供的由于已知故障而提供的<|message|>安全设备的攻击将无法通过由其他供应商提供的 security 设备。

## 3. 工作流程

我们的工作模型分为三个主要部分——数据收集（网络流）、数据采样和数据分类（Figure 10.1）。

![Figure 10.1: Flow diagram.](img/fig10_1_C.jpg)

Figure 10.1: Flow diagram.

## 4. 用于存储网络流数据（捕获记录）的数据库

这里我们有源地址、目标地址、源端口、目标端口和时间戳的详细信息。我们将这些详细信息存储在 `.csv` 文件（网络流数据集）中并导入 `Jupyter`，并应用一些排序和条件来可视化数据集（Figure 10.2）。

![Figure 10.2: Captured dataset through net flow.](img/fig10_2_B.jpg)

Figure 10.2: Captured dataset through net flow.

首先我们根据时间戳对数据集进行排序，并根据我们的 DNS 服务器（`203.190.128.141` 和 `8.8.8.8`）和 DNS 端口 `53` 应用条件。条件如下 `DNSREQ` -如果源端口大于 `1023` 且目标 IP 等于 DNS 服务器 IP 且目标端口等于 `53`，则为 DNS 请求（`DNSREQ`），如果源 IP 等于 DNS 服务器 IP 且源端口等于 `53` 且目标 IP 等于发送 DNS 请求的 IP，则为 DNS 响应（`DNSRES`）。它在数据集中设置了一个标志。

根据组织日常活动中使用的特定端口，如 https（`443`）、http（`80`）、DNS（`53`）和网络管理员允许的特定服务的自定义端口。我们将其视为良性流量，其余视为恶意流量。因此，为了区分它们，定义了一个函数，其中添加了一个新列，该列将说明发起请求的是否是真实流量还是恶意流量，并且函数定义还计算了存在流量类型的数量和百分比（Figure 10.3）。

![Figure 10.3: Dataset after set flags and traffic type.](img/fig10_3_B.jpg)

Figure 10.3: Dataset after set flags and traffic type.

在此分析之后，是时候对数据进行可视化了，为此导入了 `Matplotlib`，并且我们绘制了端口计数的 top 30 值图表，而不将它们基于恶意或真实流量进行分离。但为了更好地可视化，创建了一个数据透视表，其中所有真实流量端口都与恶意流量端口分开。所有恶意流量端口都合并到一个列中，并制作了一个函数来计算主机请求的端口出现次数。现在使用新表进行可视化，其中只有真实流量端口和一个包含所有恶意流量端口的端口（Figure 10.4, Figure 10.5, Figure 10.6 和 Figure 10.7）。

![Figure 10.4: Visualization of the port address count.](img/fig10_4_C.jpg)

Figure 10.4: Visualization of the port address count.

![Figure 10.5: Visualization of benign and malicious traffic separately.](img/fig10_5_C.jpg)

Figure 10.5: Visualization of benign and malicious traffic separately.

![Figure 10.6: Horizontal bar graph of the benign and malicious traffic ports separately.](img/fig10_6_C.jpg)

Figure 10.6: Horizontal bar graph of the benign and malicious traffic ports separately.

![Figure 10.7: Line plots of the benign and malicious traffic ports separately.](img/fig10_7_C.jpg)

Figure 10.7: Line plots of the benign and malicious traffic ports separately.

## 5. 数据集上的机器学习应用部分

### 5.1 朴素贝叶斯（NB）

朴素贝叶斯分类器是一组基于 `Bayes’ Theorem` 的分类算法。它不是单一算法，而是一系列算法，其中所有算法都共享一个共同原理，即即将被分类的每对特征彼此独立。它是一种简单但出人意料的强大的预测建模算法。该模型由两种可以直接从训练数据计算的概率组成：（1）每个类别的概率；以及（2）给定每个 x 值的每个类别的条件概率。一旦计算完成，概率模型就可以使用贝叶斯定理对新数据进行预测。NB 分类器专门为二元分类问题而设计。它非常容易构建，并且在处理海量数据时在许多情况下优于一些复杂的方法 [9]。

### 5.2 K-最近邻（KNN）

K-nearest neighbor 是 ML 中最基础却至关重要的分类算法之一。它属于监督学习领域，并在模式识别、数据挖掘和入侵检测中得到广泛应用。KNN 算法非常简单且非常有效。KNN 的模型表示为整个训练数据集。对新数据点的预测是通过在整个训练集中搜索 K 个最相似的实例（邻居）并汇总这些 K 个实例的输出变量来完成的。关键在于如何确定数据实例之间的相似性 [10]。

使用这两种算法，我们导入了 `sklearn` 库，通过将数据划分为测试用例和可训练数据来预测恶意流量和良性流量的发生情况，该数据用于预测结果。预测完成后，我们使用了 `sklearn` 库中的指标来确定使用模型对不同测试用例大小获得的结果的准确性。在 `KNN` 中，我们首先保持测试用例大小相同，通过改变预测中的邻居数量来获得最佳准确性。之后我们保持邻居数量相同而改变测试用例大小，以获得不同测试用例大小下的准确性。

在 `Naïve Bayes` 中，首先我们必须将输入形式更改为二进制以实现模型，然后我们只需更改测试用例大小即可获得不同的预测，我们用它来计算模型的准确性。

## 6. Results

在我们将 `Naïve Bayes` 和 `KNN` 应用于数据集后，我们观察到 `KNN` 在预测数据方面比 `Naïve Bayes` 更准确、更精确，关于改变测试用例大小 (Figure 10.8)。

Figure 10.8 Table of accuracies w.r.t changing test case sizes.

| Training data size (in terms of format)  || Classification accuracy(%) |

| --- | --- |

|  || K-nearest neighbor(n=7) || Naïve Bayes |

| 0.10 || 97.45 || 95.23 |

| --- | --- | --- |

| 0.20 || 97.08 || 95.49 |

| 0.30 || 96.60 || 95.83 |

| 0.40 || 97.03 || 95.54 |

| 0.50 || 96.94 || 95.52 |

| 0.60 || 96.81 || 95.52 |

| 0.70 || 96.75 || 95.74 |

| 0.80 || 96.73 || 95.89 |

正如我们从上表中可以观察到的那样，在两种分类器中，`KNN` 比 `Naïve Bayes` 更准确、更精确。

为了更好地可视化获得的结果，比较图见 Figure 10.9。

![Figure 10.9: Comparison plot of the accuracy for the classifiers.](img/fig10_9_C.jpg)

Figure 10.9: Comparison plot of the accuracy for the classifiers.

我们理解了哪种 ML 算法表现最佳，并在数据集中给出了更好的输出。

因此，我们可以说，通过将数据训练到不同测试用例大小的分类器中，可以理解数据集中的真实流量和恶意流量将一直存在，直到采取某些措施防止其进一步被利用。

## 7. Conclusions

随着我们继续推进在本项目中所学到的所有内容，通过将数据科学和 ML 算法应用于实时数据集，我们得出结论，恶意流量的数量少于真实流量，这告诉我们网络和系统管理员制定的 ACL 和过滤规则工作正常，但也需要一些对策措施来降低威胁并增强网络安全。在我们在此模型中使用的众多算法中的两种中，`KNN` 在准确性和精确度方面都优于 `Naïve Bayes`，这表明 `KNN` 中的误报率更少，而在 Bowe 可以从数据集中看到恶意流量主要来自哪些源 IP 和端口，我们现在可以通过更新防火墙协议来调节流量速率。此模型可以进一步用于查找其他服务数据集的恶意和真实流量。

### References

1. Singh, S. K. and Roy, P. K. (2020). Detecting malicious DNS over HTTPS traffic using machine learning. 2020 Int. Conf. Innov. Intel. Informat. Comput. Technol. (3ICT), 1–6, doi: [10.1109/3ICT51146.2020.9312004](http://dx.doi.org/10.1109/3ICT51146.2020.9312004)。

2. Huang, C.-T., Thareja, S., and Shin, Y.-J. (2006). Wavelet-based real time detection of network traffic anomalies. Proc. Securecomm. Workshops, 1, 1–7, doi: [10.1109/SECCOMW.2006.359584](http://dx.doi.org/10.1109/SECCOMW.2006.359584)。

3. Ishibashi, K., Toyono, T., Toyama, K., Ishino, M., Ohshima, H., and Mizukoshi, I. (2005). Detecting mass-mailing worm infected hosts by mining DNS traffic data. Proc. ACM SIGCOMM Workshop Min. Netw. Data, 1, 159–164. [`doi.org/10.1145/1080173.1080175`](http://dx.doi.org/10.1145/1080173.1080175)。

4. Thuraisingham, B. (2003). Data mining and cyber security. Third Int. Conf. Qual. Softw. 2003 Proc., 2, doi: [10.1109/QSIC.2003.1319078](http://dx.doi.org/10.1109/QSIC.2003.1319078)。

5. Joshi, M. R. and Hadi, T. H. (2015). A review of network traffic analysis and prediction techniques. arXiv preprint arXiv:1507.05722. Cornell University, Arxiv, 1, 1–23. [`doi.org/10.48550/arXiv.1507.05722`](http://dx.doi.org/10.48550/arXiv.1507.05722)。
