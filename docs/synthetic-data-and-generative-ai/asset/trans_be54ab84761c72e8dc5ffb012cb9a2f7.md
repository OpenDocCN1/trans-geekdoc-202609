
## 9.3 时间序列插值与地理空间温度数据的代码

本节包含时间序列插值和地理空间温度数据集的代码。时间序列版本处理海洋潮汐数据集，以及使用 `MPmath` 库插值高级数学函数（具有复数值和复数参数）。您可以将代码用于您自己的数据集，以及合成用途。此外，我还添加了基于傅里叶级数的多元回归的最少量代码。

### 9.3.1 时间序列插值

该程序处理一维插值方法。代码也在我的 GitHub 仓库中，[此处](https://github.com/VincentGranville/Statistical-Optimization/blob/main/interpol_fourier.py)。参数说明请参见第 [9.1.1](#Chp009_147-168_B9780443218576000138.xhtml#s0015) 和 [9.1.2](#Chp009_147-168_B9780443218576000138.xhtml#s0020) 节。代码可以根据 `mode` 参数插值数学函数或时间序列（按时间排序且具有固定时间增量的观测值数据集）。无论哪种方式，待插值的“对象”（函数或数据）在代码中均由函数 `g` 表示。该程序计算非线性移动平均，以在时间取分数参数时插值 `g(t)` 的值，例如 `t = 1/16, 2/16, 3/16` 等，而该值仅在整数参数下已知。

当 `t` 为整数时，插值与观测值相同。对于数学函数，在某些一般条件下，当节点数量（由变量 `n` 决定）为无限大时，插值也是精确的。实际上，当 `n = 8` 时即可获得非常好的近似值。

参数 `1/16` 在代码中由变量 `incr` 表示。您可以将其更改为 2 的幂的倒数，例如 `1/8, 1/4` 或 `1/2`。其他值（如 `1/7`）可能会导致问题：由于计算机算术，指令 `7*1/7` 或 `9*1/9` 不会返回精确整数；然而，`8*1/8` 会。如果需要，很容易修正此问题。

最后，减少操作数量的一种方法是使用哈希表（Python 中的字典）来存储每次遇到新 `t` 时的 `g(t)` 值。由于移动平均，相同的值 `g(t)` 可能在不同场合被多次计算。哈希表将避免重复计算，并且在计算 Zeta 函数时尤其能节省时间。

![](images/B9780443218576000138/gr006.jpg)

### 9.3.2 地理空间温度数据集

Python 代码 `interpol.py` 也在我的 GitHub 仓库中，[此处](https://github.com/VincentGranville/Statistical-Optimization/blob/main/interpol.py)。函数和参数在第 [9.1.3](#Chp009_147-168_B9780443218576000138.xhtml#s0025) 和 [9.1.4](#Chp009_147-168_B9780443218576000138.xhtml#s0030) 节中描述。应用于芝加哥地区温度的二维网格插值主函数相当简单。数据存储在 `data` 数组中，映射到 `npdata` Numpy 数组。然后将其映射到由 `zgrid` 数组表示的网格上。该网格仅用于生成等高线图。

生成了四份训练集副本（使用 `ppo=4`）。它们可以被视为训练集的四个合成版本，其位置和温度分布与原始训练集完全一致。合成位置存储在数组 `xa` 和 `ya` 中（纬度和经度）；通过插值获得的合成温度存储在数组 `za` 中。

根据设计，在与训练集位置相同的位置上计算的插值是精确的。注意，在插值之前，数据会被转换：它被归一化为零均值和单位方差，这是一种标准做法。最后进行反归一化以生成等高线图。每个插值都是使用可变数量的节点计算的。该数量取决于有多少节点足够接近目标位置。节点是训练集中已知温度的位置。

每个合成位置的节点数存储在 `npt` 数组中。使用 `alpha` 的默认参数值可确保始终至少有一个节点（最近邻）来计算插值。这可能导致远离训练集的位置产生无意义的插值。减小默认 `alpha` 会导致某些未插值的值标记为 `NaN`，这实际上是推荐的做法。未计算的值在 [图 9.4](#Chp009_147-168_B9780443218576000138.xhtml#f0025) 中显示为绿色“+”。

最后，`interpolate` 函数接受的位置 `x`、`y` 可以是单个位置，也可以是位置数组。相应地，返回值 `z`（即温度）可以是单个值，也可以是数组。`audit` 参数在内部用于测试和监控目的。

![](images/B9780443218576000138/gr009.jpg)

### 9.3.3 傅里叶级数回归

此处提供的基本代码旨在说明第 [9.2.3](#Chp009_147-168_B9780443218576000138.xhtml#s0050) 节中的方法论，即使用正弦和余弦样条进行多元回归。这是一段最小可行代码。数据是编造的，且不需要转换器，因为根据构造，观测值对于特征向量已经在 `[-1, 1]` 范围内。代码也在我的 GitHub 仓库中，[此处](https://github.com/VincentGranville/Statistical-Optimization/blob/main/interpol_ortho.py)。查找 `interpol_ortho.py`。

![](images/B9780443218576000138/gr015.jpg)

## 参考文献

*   [[1]](#Chp009_147-168_B9780443218576000138.xhtml#cf0025) G.R. Lawlor, A l'Hospital's rule for multivariable functions, Preprint, pp. 1–13 [arXiv:1209.0363](http://www.arxiv.org/abs/1209.0363); 2013. [[Link]](https://arxiv.org/abs/1209.0363)。
*   [[2]](#Chp009_147-168_B9780443218576000138.xhtml#cf0245) A.R. Osborne, Multidimensional Fourier series, *International Geophysics* 2010;97:115–145. [[Link]](https://www.sciencedirect.com/science/article/abs/pii/S0074614210970071)。
*   [[3]](#Chp009_147-168_B9780443218576000138.xhtml#cf0225) M. Shivanand, et al., Fitting random regression models with Legendre polynomial and B-spline to model the lactation curve for Indian dairy goat of semi-arid tropic, *Journal of Animal Breeding and Genetics* 2022:414–422. [[Link]](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5088414/)。
*   [[4]](#Chp009_147-168_B9780443218576000138.xhtml#cf0240) F. Wang, et al., Bivariate Fourier-series-based prediction of surface residual stress fields using stresses of partial points, *Mathematics and Mechanics of Solids* 2018. [[Link]](https://journals.sagepub.com/doi/10.1177/1081286518763976)。

# 第 10 章：合成表格数据：Copulas 与增强 GANs

## 摘要

在本章中，您将学习如何在 Python 中使用两种流行技术（GAN 和 Copula）创建自己的表格合成数据。一个示例包含真实的保险数据集：使用 Copula，您将能够创建一个替代（合成）数据集，该数据集与训练集中观测值的分布非常吻合，包括所有相关性。另一个示例是糖尿病数据集；目标是预测癌症，背景是监督分类。您将学习如何使用 GAN（生成对抗网络）合成该数据集。我还将讨论数据转换、如何处理缺失数据以及评估合成数据质量的现代工具，并附带插图。有一节重点介绍特征聚类，以减少训练 GAN 模型所需的时间。
