

Raj S., Ray K. C., and Shankar O., “Development of robust, fast and efficient QRS complex detector: a methodological review”, Aust. Phys. Eng. Sci. Med., (2018 Sept.), 41(3), 581–600.

Raj S. and Ray K.C. A personalized arrhythmia monitoring platform. Scientific Reports, (2018b), 8(11395), 1–11. [a](#bodymatter-007.xhtml#xref_d69967e26293), [b](#bodymatter-007.xhtml#xref_d69967e29163)

Raj S. and Ray K.C. Sparse representation of ECG signals for automated recognition of cardiac arrhythmias. Expert Systems with Applications, (2018c), 105, 49–64. [→](#bodymatter-007.xhtml#xref_d69967e26296)

Raj S. and Ray K.C. A personalized point-of-care platform for real-time ECG monitoring. IEEE Transactions on Consumer Electronics, (2018d), 66(4), 452–460. [→](#bodymatter-007.xhtml#xref_d69967e26300)

Rilling G., Flandrin P., and Goncalves P. On empirical mode decomposition and its algorithms. IEEE-EURASIP Workshop on Nonlinear Signal and Image Processing NSIP, (2003), 3, 8–11. [→](#bodymatter-007.xhtml#xref_d69967e26450)

Saxena S., Kumar V., and Hamde S. Feature extraction from ECG signals using wavelet transforms for disease diagnostics. International Journal of Systems Science, (2002), 33(13), 1073–1085. [→](#bodymatter-007.xhtml#xref_d69967e26287)

Vapnik V. The Nature of Statistical Learning Theory. Springer, (2000). [→](#bodymatter-007.xhtml#xref_d69967e26970)

Weston J. and Watkins C. (1998), Multi-class support vector machines. Technical Report, Citeseer, 1998. [→](#bodymatter-007.xhtml#xref_d69967e26973)

Yegnanarayana B. Artificial Neural Networks. PHI Learning Pvt. Ltd, (2009). [→](#bodymatter-007.xhtml#xref_d69967e26335)

# 8 机器学习方法探索计算智能

Naveenkumar Jayakumar Department of Computer Engineering, Bharati Vidyapeeth (Deemed to Be University) College of Engineering, Pune, India Dhanashri P. Joshi Department of Computer Engineering, Bharati Vidyapeeth (Deemed to Be University) College of Engineering, Pune, India

#### Abstract
受基因和自然特征启发的新概念，如大脑中的神经元结构\[神经网络 (NN)\]，被称为计算智能 (CI)。CI 依赖于三个主要支柱，即 NN、模糊系统和进化计算 (EC)。模糊系统利用自然语言或更具体地说人类使用的语言来表示语言模糊性，并解决近似推理计算中的困难。NN 可以定义为根据人类大脑的结构和工作方式设计的计算模型，可以进行训练并据此执行工作。本章重点关注 EC 以及 EC 在机器学习 (ML) 应用中的各个方面。EC 通过生成、计算和转换不同的可能解决方案，如进化编程、遗传算法、多目标优化和可进化硬件 (EH) 等，为优化问题提供了解决方案。在 ML 和大数据近几年，计算机系统/应用程序正在创建、收集和消耗大量数据。由于如此庞大的数据被用于 ML 功能以及数据需求型应用程序，从存储单元到主机单元的数据传输速率将成为瓶颈。可进化编程和 EH 共同可能是解决上述优化问题的关键。解决方案可以通过使用近数据处理 (NDP) 或原位处理来提供。NDP 允许在原位执行计算密集型应用程序，这意味着在存储单元 (内存/存储) 内或非常接近存储单元。结果可能是 NDP 旨在减少昂贵的数据移动，从而提高性能。NDP 由软件系统加硬件系统的组合构成，源自主机单元 (中央处理单元) 加智能存储系统。智能存储系统具有多个元素，即用于存储的各种磁盘、缓存、前端和后端。现在缓存内存具有大容量，用于临时存储热数据 (频繁使用的数据)。冷数据 (使用频率较低的数据) 被移向前面的存储层。前端旨在连接主机系统和存储系统。后端旨在支持缓存和多个存储磁盘之间的通信。后端的一部分是后端控制器，它管理这些磁盘，具有冗余独立磁盘阵列 (RAID) 的能力，并具有错误查找以及错误校正方法。本章讨论了与 ML 方法兼容的 NDP 的不同架构，以及这些提到的 NDP 架构如何增强 ML 方法的执行。本章重点关注为各种 ML 方法设计的 NDP 的最新研究进展。

关键词：原位处理，近数据处理 (NDP)，智能存储系统，计算智能，

## 8.1 计算智能简介

电子设备能够以远超人类计算能力的速度计算大量不同类型的数据，并且不会像人类那样疲劳。在某些情况下，人类贡献并不完全能够胜任，例如天气预报、健康相关问题的预测、自动防撞系统或需要处理大量数据的类似情况。因此，对计算智能 (CI) 和人工智能的需求正在逐步上升 ([Rattadilok et al., 2014](#bodymatter-008.xhtml#b_9783110648195-008_ref_031))。

那些主要需要实时数据的应用程序主要采用各种传感器以极快的速度创建和收集数据。这类应用程序通常称为物联网 (IoT) 应用程序，它们从研究者的焦点转移到智能数据计算以及在预期时刻从这些数据中发现有用的事实片段。这些有用的信息可能用于管理某些计算、激活各种传感器或控制各种物理设备或支持决策。在实时应用程序中，控制或触发任务的复杂性显著增加。CI 已成功应用于此类大数据或基于 ML 的应用程序。CI 是一个同样受生物特征启发的概念，如神经网络 (NN)。它建立在 EC、模糊系统和 NN 等坚实支柱之上。模糊系统通过利用人类使用的自然语言来塑造语言模糊性，为近似推理问题提供了关键。NN 是一个基于人类大脑结构和功能构建的范式，可以获取知识并据此工作。EC 通过产生、近似计算和转换不同的可能解决方案，为优化问题提供了解决方案。EC 由可进化硬件 (EH)、遗传算法 (GAs)、多目标优化、进化编程等组成。

即使 CI 技术需要一些数据集来提供一致和精确的结果，如系统前景，在 CI 中，预期的示例或情况形成系统，使其能够突出相应数据集中明显的异常，以便为核心实践工作开发的系统能够自主工作。这些发生的锯齿状情况被称为异常。上述异常在事先发现起来很复杂，并且可能对概述合适的训练数据集构成危险。因此，习惯于应对动态问题的 CI 方案必须能够适应条件以及环境变化 ([Rattadilok et al., 2014](#bodymatter-008.xhtml#b_9783110648195-008_ref_031))。

## 8.2 计算智能研究方面

在本节中，描述了一些 CI 关键研究方面。

