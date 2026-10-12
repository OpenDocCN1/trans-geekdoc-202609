
## 数学推导与收敛性分析

$$
\frac{1}{T + 1}\sum\limits_{t = 0}^{T}\mathbb{E}\lbrack{\lVert\nabla F(w^{t})\rVert}^{2}\rbrack \leqslant \frac{2}{\eta(T + 1)}D_{0} + \frac{(1 - L\eta + 2L^{2}\eta^{2})\beta^{2}}{L^{2}\eta^{2}}{\widehat{\sigma}}^{2} \leqslant \frac{2\lbrack F(w^{0}) - F^{\star}\rbrack}{\eta(T + 1)} + \frac{\lVert v^{0}\rVert^{2}}{(T + 1)} + \frac{\sigma_{- 1}^{2}}{2L^{2}\eta^{2}(T + 1)} + \frac{\beta^{2}{\widehat{\sigma}}^{2}}{L^{2}\eta^{2}}.
$$

![Image](img/si391.png)

最后，我们选择 $\eta := \frac{1}{L{(T + 1)}^{1/3}} \leqslant \frac{1}{L}$![Image](img/si392.png)，$\sigma_{- 1} := \frac{1}{{(T + 1)}^{1/3}}$![Image](img/si393.png)，和 $\beta := \mathcal{O}\left( \frac{1}{{(T + 1)}^{2/3}} \right)$![Image](img/si394.png) 使得 ${(1 - \beta)}^{2} \leqslant 1 - \frac{2L^{2}\eta^{2}}{1 - L\eta + 2L^{2}\eta^{2}}$![Image](img/si389.png)（这样的 $\beta$ 总是存在的）。此外，最后的估计表明

$$
\frac{1}{T + 1}\sum\limits_{t = 0}^{T}\mathbb{E}\lbrack{\lVert\nabla F(w^{t})\rVert}^{2}\rbrack = \mathcal{O}\left( \frac{1}{{(T + 1)}^{2/3}} \right),
$$

![Image](img/si395.png)

正如文献 [\[66\]](#Chp001_3-28_B9780443190377000089_split_002.xhtml#br0330) 所证明的。

我们通过使用递归估计 (1.26) 来分析三种 SGD 方案（包括方差缩减方法）的收敛性，展示了我们的方法。我们相信这种方法可用于分析其他变体，包括 SVRG 和 SARAH。

## 1.4 结束语

我们回顾了构成梯度下降法及其变体的几个主要组成部分，包括确定性和随机性方法，范围涵盖从凸问题到非凸问题。我们提供了一个简单且统一的收敛分析框架，该框架依赖于在文献中常用的最基本结构假设下的基本递归估计。虽然这种方法可应用于分析多种方法，但我们仅在几个著名方案上进行了演示。请注意，我们并未提出任何新算法，而是利用简单的递归估计统一了收敛分析。然而，我们相信这种方法可以延伸至本章所做工作之外。以下研究课题引起了我们的兴趣。

首先，是否仍可将我们的分析应用于加速方差缩减随机梯度类方法？也许可以借鉴近期工作 [\[15\]](#Chp001_3-28_B9780443190377000089_split_002.xhtml#br0075) 的思想来实现。

其次，如何将我们的框架扩展以研究分布式系统和联邦学习中的其他优化方法？我们强调，这些领域中的许多算法可视为随机[区块-]坐标方法。因此，向坐标方法和洗牌方法的扩展前景广阔且仍是开放问题。

第三，是否可能将我们的分析扩展并适应于异步基于梯度的算法？我们认为，只要延迟有界，这种扩展就是可能的。然而，需要修改递归表达式以捕捉延迟更新，从而在递归不等式中产生额外的误差项。

最后，我们的方法可用于分析极小极大和变分不等式问题算法的收敛性，这些问题最近获得了极大的关注 [\[19, 65\]](#Chp001_3-28_B9780443190377000089_split_002.xhtml#br0325)。

## 参考文献

*   [1] H.H. Bauschke, P. Combettes, *Convex Analysis and Monotone Operators Theory in Hilbert Spaces*. 2nd edition Springer; 2017.

*   [2] A. Ben-Tal, A. Nemirovski, *Lectures on Modern Convex Optimization: Analysis, Algorithms, and Engineering Applications, vol. 3*. SIAM; 2001.

*   [3] D.P. Bertsekas, *Nonlinear Programming*. 2nd edition Athena Scientific; 1999.

*   [4] J. Bolte, A. Daniilidis, A. Lewis, The Łojasiewicz inequality for nonsmooth subanalytic functions with applications to subgradient dynamical systems, *SIAM J. Optim.* 2007;17(4):1205–1223.

*   [5] L. Bottou, F.E. Curtis, J. Nocedal, Optimization methods for large-scale machine learning, *SIAM Rev.* 2018;60(2):223–311.

*   [6] Léon Bottou, Online learning and stochastic approximations, David Saad, ed. *Online Learning in Neural Networks*. New York, NY, USA: Cambridge University Press; 1998:9–42.

*   [7] S. Boyd, L. Vandenberghe, *Convex Optimization*. Cambridge: University Press; 2004.

*   [8] S. Boyd, L. Xiao, A. Mutapcic, *Subgradient methods*. [Tech. Report. EE392o] Stanford University; 2003.

*   [9] Sébastien Bubeck, Theory of convex optimization for machine learning, *Lecture Notes*. Princeton University; 2014.

*   [10] P. Combettes, J.-C. Pesquet, Signal recovery by proximal forward-backward splitting, *Fixed-Point Algorithms for Inverse Problems in Science and Engineering*. Springer; 2011:185–212.

*   [11] A.R. Conn, N. Gould, P.L. Toint, *Trust-Region Methods*. MPS/SIAM Series on Optimization. Philadelphia, USA: SIAM; 2000.

*   [12] A. Cutkosky, F. Orabona, Momentum-based variance reduction in non-convex SGD, *Advances in Neural Information Processing Systems*. 2019:15210–15219.

*   [13] A. Defazio, F. Bach, S. Lacoste-Julien, SAGA: 一种支持非强凸复合目标的快速增量梯度法，*神经信息处理系统进展 (NIPS)*。2014:1646–1654。

*   [14] M. Van Dijk, L.M. Nguyen, P.H. Nguyen, D.T. Phan, 凸目标函数的刻画及 SGD 的最优期望收敛率，2019，第 6392–6400 页。

*   [15] D. Driggs, M.J. Ehrhardt, C.-B. Schönlieb, 加速方差缩减随机梯度法，*数学规划*。2022:1–45。

*   [16] D. Drusvyatskiy, A. Lewis, 误差界、二次增长与近端方法的线性收敛，*运筹学数学*。2018;43(3):919–948。

*   [17] J. Duchi, E. Hazan, Y. Singer, 适用于在线学习和随机优化的自适应次梯度法，*机器学习研究期刊*。2011;12:2121–2159。

*   [18] I. Ekeland, T. Turnbull, *无限维优化与凸性*。芝加哥大学出版社；1983。

*   [19] F. Facchinei, J.-S. Pang, *有限维变分不等式与互补问题，第 1–2 卷*。Springer；2003。

*   [20] O. Fercoq, Z. Qu, 基于粗略强凸性估计的加速梯度法重启，预印本 [arXiv:1609.07358](http://www.arxiv.org/abs/1609.07358)；2016 第 1–23 页。

*   [21] A.V. Fiacco, G.P. McCormick, *非线性规划：序列无约束极小化技术*。工业与应用数学学会；1987。

*   [22] R. Fletcher, *优化实用方法*。第 2 版 切切斯特：Wiley；1987。

*   [23] R. Fletcher, S. Leyffer, 无惩罚函数的非线性规划，*数学规划*。2002;91:239–269。

*   [24] R. Ge, F. Huang, C. Jin, Y. Yuan, 逃离鞍点——用于张量分解的在线随机梯度，*学习理论会议*。2015:797–842。

*   [25] S. Ghadimi, G. Lan, 非凸随机规划的随机一阶和零阶方法，*SIAM J. Optim.* 2013;23(4):2341–2368。

*   [26] P. Giselsson, S. Boyd, 快速梯度法中的单调性与重启，*IEEE 决策与控制会议*。*美国洛杉矶*。2014 年 12 月:5058–5063。

*   [27] I. Goodfellow, Y. Bengio, A. Courville, *深度学习，第 1 卷*。剑桥：MIT Press；2016。

*   [28] Trevor Hastie, Robert Tibshirani, Jerome Friedman, *统计学习基础：数据挖掘、推断与预测*。第 2 版 Springer 统计学系列。2009。

*   [29] R. Johnson, T. Zhang, 利用预测方差缩减加速随机梯度下降，*神经信息处理系统进展 (NIPS)*。2013:315–323。

*   [30] H. Karimi, J. Nutini, M. Schmidt, Polyak–Łojasiewicz 条件下梯度法和近端梯度法的线性收敛，P. Frasconi, N. Landwehr, G. Manco, J. Vreeken 编。*数据库中的机器学习与知识发现*。Cham: Springer；2016:795–811。

*   [31] C.T. Kelley, *优化迭代法，第 18 卷*。美国费城：SIAM；1999。

*   [32] D.P. Kingma, J. Ba ADAM，一种随机优化方法，*第 3 届国际学习表征会议论文集 (ICLR)*。2014 abs/1412.6980。

*   [33] D. Kovalev, S. Horvath, P. Richtarik, 别再钻圈子套了，去掉那些循环：没有外层循环的 SVRG 和 Katyusha 更好，*算法学习理论*。PMLR；2020:451–467。

*   [34] G. Lan, *面向机器学习的一阶与随机优化方法*。Springer；2020。

*   [35] S. Lee, D. Kim, 适用于光滑结构非凸-非凹极大极小问题的快速额外梯度法，*第三十五届神经信息处理系统会议 (NeurIPs2021)*。2021。

*   [36] B. Li, M. Ma, G.B. Giannakis, 关于 SARAH 及其后续方法的收敛性，技术报告，ArXiv 预印本 [arXiv:1906.02351](http://www.arxiv.org/abs/1906.02351)；2019。

*   [37] I. Loshchilov, F. Hutter, SGDR：带热重启的随机梯度下降，*国际学习表征会议*。2016。

*   [38] D.G. Luenberger, Y. Ye, *线性与非线性规划*。Springer；2007。

*   [39] Z.-Q. Luo, P. Tseng, 误差界与可行下降法收敛分析：一种通用方法，*运筹学年刊*。1993;46(1):157–178。

*   [40] B.S. Mordukhovich, *变分分析与广义微分：第 I 和 II 卷*。第 330 卷 Springer；2006。

*   [41] E. Moulay, V. Léchappé, F. Plestan, 符号梯度下降算法的性质，*信息科学*。2019;492:29–39。

*   [42] I. Necoara, Y. Nesterov, F. Glineur, 非强凸优化一阶方法的线性收敛，*数学规划*。2016:1–39。

*   [43] A. Nemirovskii, D. Yudin, *优化中的问题复杂性与方法效率*。Wiley；1983。

*   [44] Y. Nesterov, 一种收敛速率为 $\mathcal{O}(1/k^{2})$![Image](img/si396.png) 的无约束凸极小化问题求解方法，*苏联科学院报告* 1983;269:543–547 译为苏联数学报告。

*   [45] Y. Nesterov, *凸优化入门讲座：基础课程*。应用优化。Kluwer Academic Publishers；2004；第 87 卷。

*   [46] Y. Nesterov, 非光滑函数的光滑极小化，*数学规划*。2005;103(1):127–152。

*   [47] Y. Nesterov, 凸优化问题的通用梯度法，*数学规划*。2015;152(1-2):381–404。

*   [48] L.M. Nguyen, J. Liu, K. Scheinberg, M. Takáč, SARAH：一种利用随机递归梯度解决机器学习问题的新方法，*第 34 届国际机器学习会议论文集*。2017:2613–2621。

*   [49] J. Nocedal, S.J. Wright, *数值优化*。第 2 版 Springer 运筹学与金融工程系列。Springer；2006。

*   [50] B. O'Donoghue, E. Candes, 加速梯度方案的自适应重启，*计算数学基础*。2015;15:715–732。

*   [51] N. Parikh, S. Boyd, 近端算法，*优化趋势基础*。2013;1(3):123–231。

*   [52] H.N. Pham, M.L. Nguyen, T.D. Phan, Q. Tran-Dinh, ProxSARAH：随机合成非凸优化的高效算法框架，*机器学习研究期刊*。2020;21:1–48。

*   [53] E. Polak, *Computational Methods in Optimization: A Unified Approach*. New York: Academic Press; 1971.
