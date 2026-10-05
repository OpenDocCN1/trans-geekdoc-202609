

# 结论与未来工作

除了交易员通常进行的技术分析外，已经确定市场趋势对于确定市场状况至关重要。此外，结果也支持了这一点，因为 LSTM 模型展示了 69.32% 的准确率，这对于比特币等金融风险资产的预测来说，是一个非常客观的。最终达到的准确率为 70%，表明该模型在提供的 4 个场景中有 3 个场景能准确给出买卖建议。交易员可以通过 1:2 的风险收益比从本研究中获益高 Alpha 值，并结合技术指标发现发现以产生更佳的交易表现。

这项研究在量化交易领域具有广泛的应用。该研究可用于构建具有多种属性的多模型，从而提高交易的整体准确性和精确度，因为这些模型将提供公众的基础情绪。通过将该模型与各种其他高频交易系统结合，可以实现高频交易。

# 参考文献

- [1] Xinwen Zhang, The Evolution Of Natural Language Processing And Its Impact On AI, Forbes, Nov 2018
- [2] Mixu, NLP for Stock Market Prediction with Reddit Data, 2021
- [3] Toni Pano and Rasha Kashel, A Composite VADER-Based Sentiment Analysis of Bitcoin (BTC), 9 Nov 2020
- [4] O. Sattarov, H. S. Jeong, Oh and J. D. Lee, “Forecasting Bitcoin Price Fluctuation by Twitter Sentiment Analysis”, 2020 International Conference on Information Science and Communications Technologies ICISC 2020, p. 1–4, November 2020.
- [5] D. R. Pant, P. Neupane, A. Pound, A. K. Pokhel and B. K. Lama, “Recurrent Neural Network Based Bitcoin Price Prediction by Twitter Sentiment Analysis”, 2018 IEEE 3rd International Conference on Computing, 2018.
- [6] Harshad M. J. and Owda A. Y., “A Novel Cryptocurrency Price Prediction Using gru LSTM and Bi-LSTM Machine Learning Algorithms”, AI, vol. 2, p. 44, 477–496, 2021, [online] Available: https://www.mdpi.com/2673-6268/2/4/24
- [7] Jaquart P., Dann D. and Weinhardt C., “Short-term Bitcoin Market Prediction Via Machine Learning”, The Journal of Financial and Data Science, vol. 7, p. 45–66, 2021.
- [8] Alessandretti L., ElBahwry A., Aiello L. M. and Bonanchelli A., “Anticipating Cryptocurrency Prices Using Machine Learning”, Complexity, 2018.
- [9] Langare K., “Introduction to cryptocurrencies”, vol. 12, p. 01–08, 2022.
- [10] Koker T. E. and Koutmos D., “Cryptocurrency Trading Using Machine Learning”, Journal of Risk and Financial Management, vol. 13, no. 8, p. 178, 2020.

# 副处理器浮点运算的微架构设计与验证

K. Harshitha, A.S. Hithen, T.A. Jagatha Madappa, B.G. Karthik and Narasimhamoorthy S. Bhat
电子与通信工程系, Vidyvardaka College of Engineering,
Mysuru, India
ORCID ID: 0000-0002-8094-1913

摘要：在微处理器芯片中，可以引入具有特殊用途的电路来执行特定任务或进行数值运算，以减轻主处理器的负担。CPU 可以快速工作。为了充分利用主机 CPU，I/O 职责被分配给其他被称为输入/输出的系统。中央计算机不需要任何输入/输出处理，而是简单地通过输入或输出来执行整个操作。通过将相对简单的子处理器用于耗时的格式化和处理，系统性能得到了提高。我们可以在引擎运行时使用副处理器处理额外工作，因此引擎的使用变得更加高效。同样，即副处理器在在使用复杂应用程序时处理数学部分。浮点运算最早出现在 70 年代的台式电脑中，并于 80 年代和 90 年代流行起来。早期的版本使用 16 位和 8 位软件执行 CPU 运算。当支持处理器支持时，浮点计算可以快速进行。副处理器是计算机辅助设计 (CAD) 以及科学与工程社区的常用单元。一些浮点单元，如 AMD 511、Intel 8232 和Motorola 6881 被视为外设，而另一些则与处理器紧密集成。

关键词：微处理器芯片、特殊用途、耗时、通道 I/O、浮点运算

# 1 引言

副处理器通常被称为大师。副处理器执行常规数学任务，从核心处理器中释放出来并节省其时间。通过卸载主处理器，副处理器从核心 CPU 卸载专门任务，使其运行得更快。副处理器是一个用于辅助主处理器功能的计算机处理器。副处理器是一个用于辅助主处理器功能的计算机处理器。副处理器从核心 CPU 卸载专门任务，通过卸载主处理器使其运行得更快。副处理器是一个用于辅助主处理器功能的计算机处理器。副处理器是一个用于辅助主处理器功能的计算机处理器。副处理器从核心 CPU 卸载专门任务，通过卸载主处理器使其运行得更快。副处理器是一个用于辅助主处理器功能的计算机处理器。副处理器是一个用于辅助主处理器功能的计算机处理器。副处理器从核心 CPU 卸载专门任务，通过卸载主处理器使其运行得更快。副处理器是一个用于辅助主处理器功能的计算机处理器。副处理器是一个用于辅助主处理器功能的计算机处理器。副处理器从核心 CPU 卸载专门任务，通过卸载主处理器使其运行得更快。副处理器是一个用于辅助主处理器功能的计算机处理器。副处理器是一个用于辅助主处理器功能的计算机处理器。副处理器从核心 CPU 卸载专门任务，通过卸载主处理器使其运行得更快。副处理器是一个用于辅助主处理器功能的计算机处理器。副处理器是一个用于辅助主处理器功能的计算机处理器。副处理器从核心 CPU 卸载专门任务，通过卸载主处理器使其运行得更快。副处理器是一个用于辅助主处理器功能的计算机处理器。副处理器是一个用于辅助主处理器功能的计算机处理器。副处理器从核心 CPU 卸载专门任务，通过卸载主处理器使其运行得更快。副处理器是一个用于辅助主处理器功能的计算机处理器。副处理器是一个用于辅助主处理器功能的计算机处理器。副处理器从核心 CPU 卸载专门任务，通过卸载主处理器使其运行得更快。副处理器是一个用于辅助主处理器功能的计算机处理器。副处理器是一个用于辅助主处理器功能的计算机处理器。副处理器从核心 CPU 卸载专门任务，通过卸载主处理器使其运行得更快。副处理器是一个用于辅助主处理器功能的计算机处理器。副处理器是一个用于辅助主处理器功能的计算机处理器。副处理器从核心 CPU 卸载专门任务，通过卸载主处理器使其运行得更快。

![](img/a3f8e852e0ee65e28c95ad0821783b_101.png)

# ## 浮点运算的副处理器卸载

...通过卸载主处理器使其运行得更快。副处理器可以执行特殊任务，如复杂的数学计算和图形显示。这些任务运行得比核心 CPU 快。微处理器的设计方式需要实时工作，以便无延迟地看到所需的输出。如果我们在指令路径中添加浮点运算，会减慢进程。为了减轻主处理器的严苛需求，开发了副处理器，它可以加速系统性能和时间。我们使用工具编写开发项目的 RTL 代码，执行所有必要的算术运算。操作流程如下所示系统架构所示。在成功执行 RTL 代码后，我们将为指定的测试平台验证所有算术运算的输出。

# ## 文献综述

- Metin Ozilben & Mustafa Gok [1] 提出了一种名为“多精度浮点加法器”的设计。本文介绍了一种多精度浮点加法器，它可以执行单次高精度浮点加法或并行多个低精度浮点加法。所提的设计在低精度模式下运行时消除了耗时的格式转换。所提多精度浮点加法器的延迟与标准双精度浮点加法器相同。
- Park 等人 [2] 发表了一篇名为《SFQ 半精度浮点乘法器的设计、实现和芯片速度》的论文。在文中，他们解释了为了克服延迟，提出的大规模重构数据路径（LSRDP）作为单通量量子（SFQ）电路的合适处理器架构。SFQ LSRDP 通过重构 SFQ 网络开关由数千个 SFQ 浮点组成，以实现低功。在本研究中，我们设计并实现了 SFQ LSRDP 的关键组件之一——SFQ 浮点乘法器 (FPM)。
- Hanie Sahel 和 Earl Schwartz lander [3] 开发了“浮点融合加减法单元”，从中提到的浮点加减法单元作为

