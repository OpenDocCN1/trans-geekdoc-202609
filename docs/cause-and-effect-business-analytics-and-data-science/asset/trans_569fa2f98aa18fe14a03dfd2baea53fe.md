
![图10.5 时间序列有向无环图。 (节点与其父节点之间最近的关系用黑色箭头表示；灰色箭头在更早时期镜像这些关系。) ⏎](images/fig10_5.jpg)

图10.5 时间序列有向无环图。 (节点与其父节点之间最近的关系用黑色箭头表示；灰色箭头在更早时期镜像这些关系。) [⏎](#chapter10.xhtml#b10fig10_5)

## 10.5 格兰杰因果关系的问题

格兰杰因果关系的检验只有在满足若干基本条件时才具有说服力。所考虑的序列需要是连续的，因此该技术不适用于例如二元变量。变量与其滞后值之间的关系必须是线性的。时间段需要是离散的；滞后阶数理想情况下应已知；序列必须是平稳的；不应存在测量误差；并且 `VAR` 应是完整的，即包含所有相关变量。

这些条件非常严格，因此不足为奇的是它们很少甚至从未同时成立。这解释了 [Shojaie 和 Fox (2022)](#chapter10.xhtml#ref10_10) 在其对格兰杰因果关系的综述中提出的观点，即“虽然有限且通常无法提供关于因果效应的信息，但格兰杰因果关系的概念可以为随时间观察到的随机变量之间的相互作用提供有用的见解”（第5页）。

## 10.6 商业与金融应用

虽然在宏观经济学中已有许多此类技术应用，例如尝试确定 `consumption` 是否格兰杰导致 `GDP`，或反之（例如，[Wen 2007](#chapter10.xhtml#ref10_12)），但在商业中的应用较少，但绝非闻所未闻。例如，[Banerjee 和 Siddhanta (2015)](#chapter10.xhtml#ref10_1) 试图厘清印度个人护理行业企业营销支出与利润之间的“因果”关系，使用2001年第二季度至2011年第一季度的季度数据。用通俗的语言来说，他们想知道营销支出是否能提高利润。虽然似乎显而易见因果关系从营销支出流向利润，但也可能更高的利润使企业能够增加营销支出，在这种情况下（格兰杰）因果关系可能流向相反方向。

Banerjee 和 Siddhanta 首先检验平稳性，发现两个序列——`ln(profit)` 和 `ln(spending on marketing)` ——是非平稳的，但差分序列是平稳的。他们随后使用 `AIC` 准则来确定 `VAR` 的最佳滞后长度，发现为九个季度。这很重要，因为营销支出可能对利润产生滞后效应——事实上，现在增加营销支出可能会在短期内降低利润，但在一年或两年后提升利润。

他们的下一步是检验这两个序列是否协整，如果包含这两个（和滞后项）变量的水平回归的残差是平稳的，则为协整。事实证明它们是平稳的，因此协整方程的误差需要纳入 `VAR` 中，这在技术上现在是一个向量误差修正（`VEC`）模型。他们的最后一步是检验格兰杰因果关系。他们发现无法拒绝利润不驱动营销支出的原假设，但拒绝了营销支出不驱动利润的原假设。换句话说，营销支出格兰杰导致利润（滞后一年半到两年），但反之不成立。

另一个例子是了解竞争企业的广告模式。例如，在针对电信行业的一项咨询项目中使用每周广告支出数据时，我们研究过一家公司的广告支出是否会被其主要竞争对手跟进，或反之。如果前者成立，例如，这种洞察使公司能够更全面地调整或“优化”广告支出，同时考虑竞争对手的反应。

## 10.7 媒体组合建模

更一般地说，时间序列数据在 `MMM` 中被广泛使用。其思想是量化不同媒体的营销支出等措施对销售额或利润等绩效指标的影响。标准技术是回归，它“用于从观察数据中推断因果关系” ([Sun 等 2017](#chapter10.xhtml#ref10_11))，尽管正如我们所见，回归只能衡量关联，而非因果。

媒体组合模型通常使用每周或每月数据，时间跨度很少超过五年；较旧的数据可能反映了不同的市场结构。这使得数据集很小，除非有区域信息，在这种情况下分析可以在次国家层面进行，并受益于更大的样本，这反过来可能带来更高的精度。即便如此，这些模型通常过度拟合，因为分析人员在寻找强拟合（“追逐 `R`”）和高统计显著性（“p-hacking”）方面承受着压力。

媒体组合模型的一个常见弱点是缺乏竞争对手的活动支出信息。[Haughton 等 (2014)](#chapter10.xhtml#ref10_4) 展示了有时可以通过应用 `Hidden Markov Chain` 来推断竞争对手是否在进行营销活动。在他们对向医生营销药品的研究中，[Haughton 等 (2014)](#chapter10.xhtml#ref10_4) 首先使用回归方法，然后构建有向无环图（`DAG`），如 [第5章](#chapter5.xhtml) 所述。但他们也指出，他们的数据未纳入自相关效应，而自相关效应是试图识别格兰杰因果关系的核心。

## 参考文献

* Banerjee, Neelotpaul, and Somroop Siddhanta. 2015. “对营销传播支出对企业盈利能力影响的实证研究：来自印度的证据”。 Global Business Review, 16(4): 609–622. [⏎](#chapter10.xhtml#b10ref10_1)
* Enders, W. 2010. 应用计量经济学时间序列, 3rd edition. Hoboken, NJ: John Wiley & Sons. [⏎](#chapter10.xhtml#b10ref10_2)
* Gujarati, Damodar N., and Dawn Porter. 2009. 基础计量经济学, 5th edition. Boston, MA: McGraw-Hill Irwin. [⏎](#chapter10.xhtml#b10ref10_3)
* Haughton, Dominique, Guangying Hua, Danny Jin, John Lin, Qizhi Wei, and Changan Zhang. 2014. “利用隐马尔可夫链推断未知竞争对手营销活动”. Journal of Direct, Data and Digital Marketing Practice, 15: 276–287. [⏎](#chapter10.xhtml#b10ref10_4)
* Johnston, John. 1972. 计量经济学方法, 2nd edition. New York, NY: McGraw-Hill. [⏎](#chapter10.xhtml#b10ref10_5)
* MacKay, Alexander, and Nathan Miller. 2024. “估计供给和需求模型：工具与协方差限制”. Working Paper 19-051, Harvard Business School. [⏎](#chapter10.xhtml#b10ref10_6)
* Ozcicek, Omeer, and W. Douglas McMillin. 1999. “向量自回归模型中的滞后长度选择：对称与非对称滞后”. Applied Economics, 31: 517–524. [⏎](#chapter10.xhtml#b10ref10_7)
* Palshikar, Girish Keshav, Manoj Ape, Sushodhan Vaishampayan, and Akshada Shinde. 2023. 时间序列中的因果关系：简短综述. In Satyasai Jagannath Nanda, and Rajendra Prasad Yadav (eds.), Data Science and Intelligent Computing Techniques, India: SCRS, 723–748. [⏎](#chapter10.xhtml#b10ref10_8)
* Runge, Jakob, Andreas Gerhardus, Gherardo Varando, Veronika Eyring, and Gustau Camps-Valls. 2023. “时间序列的因果推断”. Nature Reviews Earth & Environment, 4: 487–505. [⏎](#chapter10.xhtml#b10ref10_9)
* Shojaie, Ali, and Emily B. Fox. 2022. “格兰杰因果关系：综述与最新进展”. Annu Rev Stat Appl, 9(1): 289–319. [⏎](#chapter10.xhtml#b10ref10_10)
* Sun, Yunting, Yueqing Wang, Yuzue Jin, David Chan, and Jim Koehler. 2017. 地理层级贝叶斯分层媒体组合建模. Google Inc, Mountain View, CA. [⏎](#chapter10.xhtml#b10ref10_11)
