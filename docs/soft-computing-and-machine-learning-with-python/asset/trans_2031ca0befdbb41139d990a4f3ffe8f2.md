
基于 Python 的软计算与机器学习

## 参考文献

- D. Ascher, P. F. Dubois, K. Hinsen, J. Hugunin, and T. Oliphant. 一个开源项目：Numerical python。技术报告 UCRL-MA-128569, 洛伦斯利弗国家实验室，2001年9月。

- D. M. Chickering, D. Geiger, and D. Heckerman. 贝叶斯网络的学习是 np-hard。技术报告 MSR-TR-94-17, 微软研究院，1994年11月。

- D. Heckerman. 贝叶斯网络学习教程。《图模型中的学习》，第301–354页。MIT出版社，1998年。

- S. Imoto, T. Higuchi, T. Goto, K. Tashiro, S. Kuhara, and S. Miyano. 结合微阵列和生物学知识通过贝叶斯网络估计基因网络。生物信息学会议，2003。CSB 2003。2003年 IEEE 会议，第104–113页，2003年。

- T. E. Oliphant. 用于科学计算的 Python。《科学与工程计算》，第10–20页，2007年。

- D. Pe'er, A. Regev, G. Elidan, and N. Friedman. 从受扰的表达谱中推断子网络。《生物信息学》，1(1):1–9，2001年。

- K. Sachs, D. Gifford, T. Jaakkola, P. Sorger, and D. Lauffenburg. 细胞信号通路建模的贝叶斯网络方法。《科学 STKE》，2002年。

- C. Yoo, V. Thorsson, and G. F. Cooper. 从实验和观察性 DNA 微阵列数据的混合发现基因调节通路中的因果关系。《Pac 生物计算》，7:498–509，2002年。

## 第 12 章

## SCIKIT-LEARN：Python 中的机器学习

Fabian Pedregosa, Gael Varoaux, Alexandre Gramfort, Vincent Michel, Bertrand Thirion, Olivier Grisel, Mathieu Blondel, Peter Prettenhofer, Ron Weiss, Vincent Dubourg, Jake Vanderplas, Alexandre Passos, David Cournnau, Mathieu Brucher, Matthieu Perrot, and Edouard Duchesnay

- *Parietal, INRIA Saclay Neurospin, Bat 145, CEA Saclay 91119 Gif sur Yvette – 法
- *Nuxeo 20 rue Soleilet 75 020 Paris – 法
- *Kobe University 1-1 Rokkodai, Nada Kobe 657-8501 – 日本
- *Bauhaus-Univers Weimar Bauhaus.str. 11 99421 Weimar – 德国
- *Google Inc 76 Ninth Avenue New York, NY 10011 – 美国
- *Clermont University, IFMA, EA 3867, LaMI BP 10488, 63000 Clermont-Ferrand – 法
- *Astronomy Department University of Washington, Box 351850 Seattle, WA 98195 – 美国
- *IESL Lab UMass Amherst MA 01002 – 美国
- *Enthought 21 J.J. Thompson Avenue Cambridge, CB 3FA – 英国

> 引用：F. Pedregosa, G. Varoaux, A. Gramfort, V. Michel, B. Thirion, O. Grisel, M. Blondel, P. Prettenhöfer, R. Weiss, V. Dubourg, J. Vanderplas, A. Passos, D. Cournapeau, M. Brucher, M. Perrot, E. Duchesnay; “Scikit-learn: Machine Learning in Python”，“机器学习研究期刊》，12 (10月): 2825–2830, 2011年。

版权：© 2011 作者及《机器学习研究期刊》。本文是根据知识共享署名 3.0 许可分发的开放文章

# 基于 Python 的软计算与机器学习

Total SA, CSTJF avenue Larribau 64000 Pau – 法

LNAO Neurospin, Bat 145, Cea Saclay 91191 Gif Yvette – 法

## 摘要

Scikit-learn 是一个 Python 模块，集成了一系列最先进的机器学习算法，适用于中等规模的监督和无监督问题。该软件包侧重于使用通用高级语言，为非专业人士引入机器学习。重点在于易用性、性能、文档和 API 的一致性。它的依赖项极少，并根据简化的 BSD 许可证分发，鼓励其在学术和商业环境中使用。源代码、二进制执行文件和文档可以从 http://scikit-learn.sourceforge.net 下载。

**关键词：** Python，监督学习，无监督学习，模型选择

## 引言

Python 编程语言正在成为最受欢迎的科学计算语言之一。得益于其高层交互式特性以及成熟的科学库生态系统，它是算法开发和探索性数据分析极具吸引力的选择（Dubois, 2007; Milmann and Avizais, 2017）。

Scikit-learn 构建在科学 Python 栈之上：numpy, scipy 和 matplotlib。这些库为高效的数组操作、数值例程和可视化提供了基础。Scikit-learn 为分类、回归、数据预处理、模型选择、降维和流水线提供了多种快速工具。

Scikit-learn 的目标是为机器学习算法提供简单且一致的接口。这是通过遵循几个原则实现的：

- 一致性：所有的估计器都具有相同的接口，便于在算法之间切换并构建流水线。
- 灵活性：该库设计用于各种上下文并与其他工具配合。
- 效率：算法尽可能高效地实现，通常使用 C 或 Cython 提高性能。
- 文档：该库文档详尽，提供了许多示例帮助用户学习。

Scikit-learn 是一个社区驱动的项目。我们欢迎新功能、改进和错误报告的贡献。

Scikit-learn 的核心组件是估计器（estimators）、转换器（transformers）、分类器（classifiers）和回归器。估计器是 Scikit-learn 中最重要的对象。它们遵循一致的接口：
- `fit(X, y)` 在训练数据上训练模型。
- `predict(X)` 在新数据上进行预测。
- `score(X, y)` 评估预测质量。

转换器用于数据转换，例如标准化、编码和降维。它们遵循类似的接口：
- `fit(X, y)` 学习转换参数。
- `transform(X)` 将转换应用到数据。

分类器和回归器用于监督学习的估计器类型。它们遵循与估计器相同的接口，并带有 `predict` 方法。

Scikit-learn 还提供了许多模型选择和评估工具，例如交叉验证、网格搜索和各种指标。这些工具帮助用户为数据找到最佳模型，并确保其良好地泛化到新数据。

## 底层技术

Numpy：Scikit-learn 的基础是 numpy。它提供了处理这些数组的多维对象和函数。

Scipy：Scikit-learn 还使用 scipy 进行许多数值例程，如优化、线性代数和信号处理。

Cython：使用算法thonthon 允许我们编写运行速度类似于 C++ 的 Python 代码。

## 代码设计

通过接口而非继承指定对象：在 Scikit-learn 中，我们不要求对象继承自基类。相反，我们依赖鸭子类型（duck typing）。如果对象具有所需的方法，就可以作为估计器使用。这使得 Scikit-learn 与其他的集成变得更容易。
