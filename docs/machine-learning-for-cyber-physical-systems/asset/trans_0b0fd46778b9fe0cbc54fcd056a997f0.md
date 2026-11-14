

## 4 结论

机器学习算法的计算吞吐量受到底层硬件可用计算能力的限制。DLNN 中的大部分计算能力都由卷积步骤消耗，该步骤基于通用矩阵乘法 (GEMM)。近年来，为了加速机器学习应用中的计算时间，提出了多种针对 GPU 的高度优化 GEMM 实现。通常，这些软件库已针对特定的 GPU 版本和要处理的数据的特定布局进行了优化。

为了获得最大性能，GEMM 算法的内核参数需要针对硬件和学习任务进行专用调优。基于这些假设，我们提出了一种适用于基于 GPU 的 GEMM 算法的两步自动调优方法：第一步，通过使用几种开发的性能指标分析内核源代码，对内核参数搜索空间进行剪枝；第二步，使用一种改进的模拟退火算法，该算法能够快速搜索性能最优的内核参数，同时保持搜索运行时间低于最先进的暴力搜索实现。我们表明，所提出的用于自动调优 MAGMA-GEMM 内核的方法能够实现高性能，并能适应 GPU 硬件和数据布局。我们的结果基于 160 个不同的输入问题得出——与 NVIDIA (cuBLAS) 的最先进的 GEMM 实现相比，在基于 Pascal 的 NVIDIA 加速卡上平均加速比约为 12。本文提出的关键概念可以推广，用于自动调优其他对性能敏感的 GPU 内核的内核参数。

## 5 致谢

该工作在弗劳恩霍夫“认知互联网技术”卓越集群中开发。

## 参考文献

- 1. Theano：基于 Python 的 GPU 深度学习 Bergstra, James 和 Bastien, Frédéric 和 Breuleux, Olivier 和 Lamblin, Pascal 和 Pascanu, Razvan 和 Delalleau, Olivier 和 Desjardins, Guillaume 和 Warde-Farley, David 和 Goodfellow, Ian 和 Bergeron, Arnaud 和其他人，NIPS 2011，BigLearning 工作坊，西班牙格拉纳达
- 2. 针对 Fermi 的 GEMM 自动调优 Jakub Kurzak, Stanimire Tomov, Jack Dongarra 2011
- 3. 使用 GPU 的快速 k 近邻搜索 Vincent Garcia, Eric Debreuve, Michel Barlaud 可于 http://vincentfpgarcia.github.io/kNN-CUDA/ 查阅，访问日期 13.06.2018
- 4. Magma 项目页面 http://icl.cs.utk.edu/magma/ 访问日期 13.06.2018
- 5. 软件自动实证优化及 ATLAS 项目 R. Clint Whaley 和 Antoine Petitet 和 Jack J. Dongarra 2001
- 6. OSKI：自动调优稀疏矩阵内核库 Richard Vuduc 和 James W. Demmel 和 Katherine A. Yelick 2005
- 7. 面向 GPU 的与应用无关的自动调优 Martin TILLMANN 和 Thomas KARCHER 和 Carsten Dachsbacher 和 Walter F. TICHY 2013
- 8. CUDA GPU 的 3-D FFT 库自动调优 Akira Nakada 和 Satoshi Matsuoka 2009
- 9. 基于 GPU 上稀疏矩阵-向量乘法统计信息的性能预测 Ruixing Wang 和 Tongxiang Gu 和 Ming Li 2017
- 10. 面向仿射程序的自动 C 到 CUDA 代码生成 Muthu Manikandan Baskaran 和 J. Ramanujam 和 P. Sadayappan 2010
- 11. 用于生成高性能 CUDA 代码的基于脚本的自动调优编译器系统 MALIK KHAN 和 NUST PROTONU BASU 和 GABE RUDY 和 MARY HALL 和 CHUN CHEN 和 JACQUELINE CHAME 2013
- 12. 用于稠密线性代数调优的 GPU 基准测试 Vasily Volkov, James W. Demmel 2008
- 13. 关于 GPU GEMM 自动调优的备注 Yinam Li1, Jack Dongarra, Stanimire Tomov 2009
- 14. 面向 Fermi 图形处理单元的改进 Magma Gemm Rajib Nath, Stanimire Tomov, Jack Dongarra 2010
- 15. GPU 批量 GEMM 的性能、设计与自动调优 Ahmad Abdelfattah, Azzam Haidar, Stanimire Tomov 和 Jack Dongarra 2016
- 16. GPU 上多变量大小 BLAS 计算批量执行的新 HPC 技术 Ahmad Abdelfattah, Azzam Haidar, Stanimire Tomov 和 Jack Dongarra 2017
- 17. GPU 上的暴力 k 近邻搜索 Shengren Li 和 Nina Amenta 2015
- 18. GPU 上矩阵乘法自动调优以实现能耗最小化的经验 Hartwig Anzt, Blake Haugen1, Jakub Kurzak1 和 Piotr Luszczek 和 Jack Dongarra 2015
- 19. GPU 上稀疏矩阵-向量乘法的模型驱动自动调优 Jee W. Choi, Amik Singh 和 Richard W. Vuduc 2010
- 20. https://www12.informatik.uni-erlangen.de/edu/map/ss08/talks/Best Practices for GPU Programming.ppt，访问日期 26.2.2018 16:21。GPU 编程最佳实践。
- 21. 理解 GPU 上的延迟隐藏，Vasily Volkov，2016
- 22. AARTS, Emile; KORST, Jan. 模拟退火与玻尔兹曼机。1988

**开放获取** 本章根据 Creative Commons 署名 4.0 国际许可证 (http://creativecommons.org/licenses/by/4.0/) 的条款获得许可，只要向原作者(们)和来源适当致谢，提供 Creative Commons 许可证链接并注明是否已更改，即可在任何媒介或格式中使用、共享、改编、分发和复制。

本章中的图像或其他第三方材料包含在本章的 Creative Commons 许可证中，除非材料的致谢行中另有说明。如果材料未包含在本章的 Creative Commons 许可证中，且您的预期用途未获法律法规允许或超出允许范围，则需要直接从版权持有人处获得许可。

![](img/a2f5eed6507498d886a06be86239344b_83_0.png)

## 带有众多工艺变量和质量标准的冲压硬化生产线的工艺控制

Anke Stoll, Norbert Pierschel, Ken Wenzel, 和 Tino Langer

弗劳恩霍夫机床与成形技术研究所 IWU，德国 09126 采姆尼茨赖兴汉纳街 88 号
anke.stoll@iwu.fraunhofer.de

### 摘要

目前，冲压硬化工艺的优化仍然是一项复杂且具有挑战性的任务。本报告描述了将线性回归与最小二乘优化相结合，以调整该工艺的工艺参数，从而提高质量。使用了 FE 仿真程序 AutoForm 来建模相关生产线，并测量了各种工艺和质量参数。所提系统能够根据生产线各步骤的质量估计，自动调整后续工艺步骤的工艺参数。额外的好处是能够在生产过程早期识别可能存在缺陷的零件。基于 1000 次观察的结果，更好地了解了该工艺，未来可将组合回归与优化方法扩展到更复杂的生产线。

### 关键词

线性回归，最小二乘优化，生产线，冲压硬化，工艺控制

## 1 引言

工业 4.0 的目标之一是通过算法、大数据方法和高新技术进行数字化，以优化和定制生产流程 [1]。目前，机器学习 (ML) 方法支持用于故障检测、维护、决策支持和产品质量改进的监控、诊断和(离线)系统优化 [2,3]。ML 领域多种多样，有多种不同的方法可供选择。然而，在制造和其他应用领域，ML 方法的复杂性可能会阻碍其采用，即使许多生产过程的数据采集是可能的，并且充足的数据库可用或可获得。因此，本工作旨在为生产线实施一种简单的 ML 和优化方法。本文从第 2 节讨论与 ML 和工艺控制相关的工作开始，接着在第 3 节介绍方法论，其中包括数据集、数据准备和估计技术的描述。第 4 节描述了分析结果。第 5 节介绍了结论和实际意义的讨论。

