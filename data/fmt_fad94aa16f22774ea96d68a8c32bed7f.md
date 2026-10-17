
*p*(**x**) = exp(**θ**^(*T*)**u**(**x**) − *A*(**θ**))

![Equation](img/si391.png)

### 1. 证明 *A*(**θ**) 生成定义指数族的相应均值参数。

```
\frac{\partial A(\mathbf{\theta})}{\partial\theta_{i}} = \mathbb{E}\left\lbrack u_{i}(\mathbf{x}) \right\rbrack = \mu_{i}.
```

![Equation](img/si392.png)

### 2. 同时，证明 *A*(**θ**) 是一个凸函数。

### 3. **16.15** 证明 *A*(**θ**) 的共轭函数（与指数分布相关联，如问题 16.14 中所示）是相应的负熵函数。此外，如果 **μ** 和 **θ**(**μ**) 是双重耦合的，则

**μ** = 𝔼[**u**(**x**)]

![Equation](img/si394.png)

### 4. 其中 𝔼[·] 是关于 *p*(**x**; **θ**(**μ**)) 的。

![Equation](img/si170.png)

### 5. **16.16** 推导在 HMM 中更新 *γ*(**x**[*n*]) 的递归公式，使其独立于 *β*(**x**[*n*])。

![Equation](img/si262.png)

![Equation](img/si259.png)

### 6. **16.17** 推导一种用于 HMM 模型预测的高效方案，即求得 *p*(**y**[*N* + 1]|*Y*)，其中 *Y* = {**y**[1], **y**[2], …, **y**[*N*]}。

![Equation](img/si396.png)

![Equation](img/si397.png)

### 7. **16.18** 在用于训练 HMM 的前向-后向算法背景下，证明概率 *P*[*k*]、*k* = 1, 2, …, *K* 和 *P*[*ij*]、*i*, *j* = 1, 2, …, *K* 的估计公式。

![Equation](img/si272.png)

![Equation](img/si220.png)

![Equation](img/si226.png)

![Equation](img/si274.png)

### 8. **16.19** 考虑第 15.3.5 节中由局部条件 PDF 定义的高斯贝叶斯网络。

$$
\left. p(x_{i} \middle| \text{Pa}_{i}) = \mathcal{N}\left( x_{i} \middle| \sum\limits_{k:x_{k} \in \text{Pa}_{i}}\theta_{ik}x_{k} + \theta_{i0},\sigma^{2} \right),\quad i = 1,2,\ldots,l. \right.
$$

![Equation](img/si399.png)

#### 1. 假设有一组*N*个观测值，*x**i*，*n* = 1, 2, …, *N*，*i* = 1, 2, …, *l*，并推导参数**θ**的最大似然估计；假设公共方差*σ*²是已知的。

## 参考文献

*   [1] S. Arnborg, D. Cornell, A. Proskurowski, 在 k 树中寻找嵌入的复杂性，*SIAM J. Algebraic Discrete Methods* 1987;8(2):277–284.
*   [2] D. Barber, A.T. Cemgil, 时间序列的图模型，*IEEE Signal Process. Mag.* 2010;27:18–28.
*   [3] D. Barber, *贝叶斯推理与机器学习*。剑桥：剑桥大学出版社；2013.
*   [4] R. Bartolami, H. Bunke, 基于隐马尔可夫模型的集成方法用于离线手写文本行识别，*Pattern Recognit.* 2008;41(11):3452–3460.
*   [5] C.A. Berrou, A. Glavieux, P. Thitimajshima, 接近香农极限的纠错编码与解码：涡轮码，*IEEE 国际通信会议论文集*。*瑞士日内瓦*。1993.
*   [6] L. Christensen, J. Zarsen, 使用变分贝叶斯 EM 算法对区块衰落频率选择性 MIMO 信道进行数据和参数估计，*国际声学、语音与信号处理会议，ICASSP，第 4 卷*。2006:465–468.
*   [7] R.G. Cowell, A.P. Dawid, S.L. Lauritzen, D.J. Spiegehalter, *概率网络与专家系统*。纽约：Springer-Verlag；1999.
*   [8] J. Deller, J. Proakis, J.H.L. Hansen, *语音信号的离散时间处理*。纽约：Macmillan；1993.
*   [9] R. Durbin, S. Eddy, A. Krogh, G. Mitchison, *生物序列分析：蛋白质和核酸的概率模型*。剑桥：剑桥大学出版社；1998.
*   [10] J. Domke, 使用近似边缘推断学习图参数，[arXiv:1301.3193v1 [cs,LG]](http://www.arxiv.org/abs/1301.3193v1)；2013 年 1 月 15 日.
*   [11] Y. Ephraim, D. Malah, B.H. Juang, 关于隐马尔可夫模型在增强噪声语音中的应用，*IEEE Trans. Acoust. Speech Signal Process.* 1989;37(12):1846–1856.
*   [12] P. Fearhead, 针对多重问题的精确高效贝叶斯推断，*Stat. Comput.* 2006;16(2):203–213.
*   [13] N. Friedman, D. Geiger, M. Goldszmidt, 贝叶斯网络分类器，*Mach. Learn.* 1997;29:131–163.
*   [14] K.S. Fu, *句法模式识别及其应用*。新泽西州 Upper Saddle River：Prentice Hall；1982.
*   [15] R.G. Gallager, 低密度奇偶校验码，*IEEE Trans. Inf. Theory* 1968;2:21–28.
*   [16] C. Georgoulakis, S. Theodoridis, 使用隐马尔可夫模型和聚类技术进行盲均衡和半盲均衡，*Signal Process.* 2000;80(9):1795–1805.
*   [17] Z. Ghahramani, M.I. Jordan, 阶乘隐马尔可夫模型，*Mach. Learn.* 1997;29:245–273.
*   [18] Z. Ghahramani, G.E. Hinton, 用于切换状态空间模型的变分学习，*Neural Comput.* 1998;12(4):963–996.
*   [19] R. Greiner, W. Zhou, 逻辑回归的结构扩展：信念网络分类器的判别参数学习，*第 18 届国际人工智能会议论文集*。2002:167–173.
*   [20] D. Grossman, P. Domingos, 通过最大化条件似然学习贝叶斯网络分类器，*第 21 届国际机器学习会议论文集*。*加拿大 Bauff*。2004.
*   [21] Y. Guo, D. Wilkinson, D. Schuurmans, 最大边际贝叶斯网络，*国际人工智能不确定性会议论文集*。2005.
*   [22] D. Heckerman, D. Geiger, M. Chickering, 学习贝叶斯网络：知识与统计数据的结合，*Mach. Learn.* 1995;20:197–243.
*   [23] B. Hu, I. Land, L. Rasmussen, R. Piton, B. Fleury, 一种用于编码 CDMA 联合多用户解码的散度最小化方法，*IEEE J. Sel. Areas Commun.* 2008;26(3):432–445.
*   [24] A. Ihler, J.W. Fisher, P.L. Moses, A.S. Willsky, 用于传感器网络自定位的非参数信念传播，*IEEE J. Sel. Areas Commun.* 2005;23(4):809–819.
*   [25] A. Ihler, D. McAllester, 粒子信念传播，*国际人工智能与统计会议*。2009:256–263.
*   [26] S. Ikeda, T. Tanaka, S.I. Amari, 涡轮码和低密度奇偶校验码的信息几何，*IEEE Trans. Inf. Theory* 2004;50(6):1097–1114.
*   [27] T.S. Jaakola, *图模型中推断与估计的变分方法*。[博士论文] 脑与认知科学系，M.I.T.；1997.
*   [28] T.S. Jaakola, M.I. Jordan, 图模型中概率近似的递归算法，M.C. Mozer, M.I. Jordan, T. Petsche, 编。*神经信息处理系统进展论文集*。*NIPS*。马萨诸塞州剑桥：MIT Press；1997.

## 参考文献

*   [29] T.S. Jaakola, M.I. Jordan, 通过使用混合分布改进均场近似,载 M.I. Jordan 主编, *Learning in Graphical Models* (图形模型中的学习). Cambridge, MA: MIT Press, 1999.
*   [30] T.S. Jaakola, M.I. Jordan, 变分方法与 QMR-DT 数据库, *J. Artif. Intell. Res.* (人工智能研究期刊) 1999;10:291–322.
*   [31] T.S. Jaakola, 变分近似方法教程,载 M. Opper, D. Saad 主编, *Advanced Mean Field Methods: Theory and Practice* (高级均场方法: 理论与实践). Cambridge, MA: MIT Press, 2001, pp. 129–160.
*   [32] F.V. Jensen, *Bayesian Networks and Decision Graphs* (贝叶斯网络与决策图). New York: Springer, 2001.
*   [33] H. Jiang, X. Li, 使用凸优化进行统计模型的参数估计, *IEEE Signal Process. Mag.* (IEEE 信号处理杂志) 2010;27(3):115–127.
*   [34] M.I. Jordan, Z. Ghahramani, T.S. Jaakola, L.K. Saul, 图形模型变分方法导论, *Mach. Learn.* (机器学习) 1999;37:183–233.
*   [35] R.E. Kalman, 线性滤波与预测问题的新方法, *Trans. ASME J. Basic Eng.* (ASME 基础工程期刊汇刊) 1960;82:34–45.
*   [36] G.K. Kaleh, R. Vallet, 线性与非线性信道的联合参数估计与符号检测, *IEEE Trans. Commun.* (IEEE 通信汇刊) 1994;42(7):2406–2414.
*   [37] R. Kikuchi, 协作现象理论, *Phys. Rev.* (物理评论) 1951;81:988–1003.
*   [38] G.E. Kirkelund, C.N. Manchon, L.P.B. Christensen, E. Riegler, MIMO-OFDM 中的联合信道估计与解码的变分消息传递, *Proceedings, IEEE Globecom* (IEEE 全球通信会议论文集), 2010.
*   [39] U. Kjærulff, *Triangulation of Graphs: Algorithms Giving Small Total State Space* (图的三角剖分: 产生较小总状态空间的算法). [Technical Report, R90-09] Denmark: Aalborg University, 1990.
*   [40] A.P. Klapuri, A.J. Eronen, J.T. Astola, 声学音乐信号拍子分析, *IEEE Trans. Audio Speech Lang. Process.* (IEEE 音频、语言与语音处理汇刊) 2006;14(1):342–355.
*   [41] D. Koller, N. Friedman, *Probabilistic Graphical Models: Principles and Techniques* (概率图形模型: 原理与技术). Cambridge, MA: MIT Press, 2009.
*   [42] M. Kolar, L. Song, A. Ahmed, E.P. Xing, 估计时变网络, *Ann. Appl. Stat.* (应用统计学年刊) 2010;4:94–123.
*   [43] J.B. Kruskal, 关于最短生成子树与旅行推销员问题, *Proc. Am. Math. Soc.* (美国数学会会刊) 1956;7:48–50.
*   [44] S.L. Lauritzen, D.J. Spiegelhalter, 图形结构上的概率局部计算及其在专家系统中的应用, *J. R. Stat. Soc. B* (皇家统计学会志 B 系列) 1988;50:157–224.
*   [45] S.L. Lauritzen, *Graphical Models* (图形模型). Oxford: Oxford University Press, 1996.
*   [46] S.E. Levinson, 用于自动语音识别的连续可变持续时间 HMM, *Comput. Speech Lang.* (计算机语音与语言) 1986;1:29–45.
*   [47] D.J.C. MacKay, 基于极稀疏矩阵的优秀纠错码, *IEEE Trans. Inf. Theory* (IEEE 信息论汇刊) 1999;45(2):399–431.
*   [48] Y. Mao, F.R. Kschischang, B. Li, S. Pasupathy, 无线传感器网络链路损耗监测的因子图方法, *J. Sel. Areas Commun.* (IEEE 通信选编/精选通信领域期刊) 2005;23(4):820–829.
*   [49] R.J. McEliece, D.J.C. MacKay, J.F. Cheng, Turbo 解码作为 Pearl 信念传播算法的一个实例, *IEEE J. Sel. Areas Commun.* (IEEE 通信选编期刊) 1998;16(2):140–152.
*   [50] T.P. Minka, 用于近似推理的期望传播, *Proceedings 17th Conference on Uncertainty in Artificial Intelligence* (第 17 届人工智能不确定性会议论文集). San Mateo: Morgan-Kaufmann, 2001, pp. 362–369.
*   [51] T.P. Minka, *Divergence Measures and Message Passing* (散度度量与消息传递). [Technical Report MSR-TR-2005-173] Microsoft Research Cambridge, 2005.
*   [52] K.P. Murphy, T. Weiss, M.J. Jordan, 用于近似推理的回路信念传播: 实证研究, *Proceedings 15th Conference on Uncertainties on Artificial Intelligence* (第 15 届人工智能不确定性会议论文集), 1999.
*   [53] K.P. Murphy, *Machine Learning: A Probabilistic Perspective* (机器学习: 概率视角). Cambridge, MA: MIT Press, 2012.
*   [54] S.H. Nielsen, T.D. Nielsen, 将贝叶斯网络结构适配至非平稳领域, *Int. J. Approx. Reason.* (国际近似推理期刊) 2008;49(2):379–397.
*   [55] S. Nowozin, C.H. Lampert, 计算机视觉中的结构化学习与预测, *Found. Trends Comput. Graph. Vis.* (计算机图形学与视觉基础与趋势) 2011;6:185–365.
*   [56] M. Ostendorf, V. Digalakis, O. Kimball, 从 HMM 到段模型: 语音随机建模的统一视角, *IEEE Trans. Speech Audio Process.* (IEEE 语音与音频处理汇刊) 1996;4(5):360–378.
*   [57] J. Pearl, *Probabilistic Reasoning in Intelligent Systems: Networks of Plausible Inference* (智能系统中的概率推理: 似然推理网络). San Mateo: Morgan-Kaufmann, 1988.
*   [58] F. Pernkopf, J. Bilmes, 贝叶斯网络分类器判别性结构学习的高效启发式算法, *J. Mach. Learn. Res.* (机器学习研究期刊) 2010;11:2323–2360.
