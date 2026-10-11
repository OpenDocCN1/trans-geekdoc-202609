

![Image](OEBPS/images/B9780443190377000089/si382.png)

为简单起见，我们选择所有参数均为常数。令 $D\_{t}: = F(w^{t}) - F^{\\star} + \\frac{\\eta(1 - L\\eta)}{2}{\\| v^{t - 1}\\|}^{2} + \\frac{(c - \\eta)}{2}\\sigma\_{t - 1}^{2}$![Image](OEBPS/images/B9780443190377000089/si383.png)，并施加以下条件：

2*L*²*η*²*c*(1 − *β*)² ≤ *η*(1 − *L**η*) and *c*(1 − *β*)² ≤ *c* − *η*.

![Image](OEBPS/images/B9780443190377000089/si384.png)(1.30)

然后，最后的估计得出

$\\mathbb{E}\\lbrack D\_{t + 1}|\\mathcal{F}\_{t}\\rbrack + \\underset{\\Delta\_{t}}{\\underset{︸}{\\frac{\\eta}{2}{\\|\\nabla F(w^{t})\\|}^{2}}} \\leqslant D\_{t} + \\underset{E\_{t}}{\\underset{︸}{c\\beta^{2}{\\widehat{\\sigma}}^{2}}},$

![Image](OEBPS/images/B9780443190377000089/si385.png)

这正是 [(1.26)](#Chp001_3-28_B9780443190377000089_split_002.xhtml#deq41) 式，其中 *ω*[*t*] = 1![Image](OEBPS/images/B9780443190377000089/si202.png)。

假设我们选择 $\\eta \\in (0,\\frac{1}{L})$![Image](OEBPS/images/B9780443190377000089/si386.png) 和 *c* > 0![Image](OEBPS/images/B9780443190377000089/si58_u1.png) 使得 2*L*²*η*²(*c* − *η*) = *η*(1 − *L**η*)![Image](OEBPS/images/B9780443190377000089/si387.png)，从而得到 $c: = \\frac{1 - L\\eta}{2L^{2}\\eta} + \\eta = \\frac{1 - L\\eta + 2L^{2}\\eta^{2}}{2L^{2}\\eta}$![Image](OEBPS/images/B9780443190377000089/si388.png)。此外，${(1 - \\beta)}^{2} \\leqslant 1 - \\frac{2L^{2}\\eta^{2}}{1 - L\\eta + 2L^{2}\\eta^{2}}$![Image](OEBPS/images/B9780443190377000089/si389.png)。那么，[(1.30)](#Chp001_3-28_B9780443190377000089_split_002.xhtml#deq57) 式的两个条件均以等式成立。在这种情况下，我们得到 $\\mathbb{E}\\lbrack D\_{t + 1}|\\mathcal{F}\_{t}\\rbrack + \\frac{\\eta}{2}{\\|\\nabla F(w^{t})\\|}^{2} \\leqslant D\_{t} + \\frac{(1 - L\\eta + 2L^{2}\\eta^{2})\\beta^{2}}{2L^{2}\\eta}{\\widehat{\\sigma}}^{2}$![Image](OEBPS/images/B9780443190377000089/si390.png)。这个不等式意味着

$\\frac{1}{T + 1}\\sum\\limits\_{t = 0}^{T}\\mathbb{E}\\lbrack{\\|\\nabla F(w^{t})\\|}^{2}\\rbrack \\leqslant \\frac{2}{\\eta(T + 1)}D\_{0} + \\frac{(1 - L\\eta + 2L^{2}\\eta^{2})\\beta^{2}}{L^{2}\\eta^{2}}{\\widehat{\\sigma}}^{2} \\leqslant \\frac{2\\lbrack F(w^{0}) - F^{\\star}\\rbrack}{\\eta(T + 1)} + \\frac{{\\| v^{0}\\|}^{2}}{(T + 1)} + \\frac{\\sigma\_{- 1}^{2}}{2L^{2}\\eta^{2}(T + 1)} + \\frac{\\beta^{2}{\\widehat{\\sigma}}^{2}}{L^{2}\\eta^{2}}.$

![Image](OEBPS/images/B9780443190377000089/si391.png)

最后，我们选择 $\\eta: = \\frac{1}{L{(T + 1)}^{1/3}} \\leqslant \\frac{1}{L}$![Image](OEBPS/images/B9780443190377000089/si392.png)，$\\sigma\_{- 1}: = \\frac{1}{{(T + 1)}^{1/3}}$![Image](OEBPS/images/B9780443190377000089/si393.png)，和 $\\beta: = \\mathcal{O}\\left( \\frac{1}{{(T + 1)}^{2/3}} \\right)$![Image](OEBPS/images/B9780443190377000089/si394.png) 使得 ${(1 - \\beta)}^{2} \\leqslant 1 - \\frac{2L^{2}\\eta^{2}}{1 - L\\eta + 2L^{2}\\eta^{2}}$![Image](OEBPS/images/B9780443190377000089/si389.png)（这样的 *β* 总是存在的）。此外，最后的估计表明

$\\frac{1}{T + 1}\\sum\\limits\_{t = 0}^{T}\\mathbb{E}\\lbrack{\\|\\nabla F(w^{t})\\|}^{2}\\rbrack = \\mathcal{O}\\left( \\frac{1}{{(T + 1)}^{2/3}} \\right),$

![Image](OEBPS/images/B9780443190377000089/si395.png)

正如文献 [\[66\]](#Chp001_3-28_B9780443190377000089_split_002.xhtml#br0330) 所证明的。

我们通过使用递归估计 [(1.26)](#Chp001_3-28_B9780443190377000089_split_002.xhtml#deq41) 来分析三种 SGD 方案（包括方差缩减方法）的收敛性，展示了我们的方法。我们相信这种方法可用于分析其他变体，包括 SVRG 和 SARAH。

## 1.4 结束语

我们回顾了构成梯度下降法及其变体的几个主要组成部分，包括确定性和随机性方法，范围涵盖从凸问题到非凸问题。我们提供了一个简单且统一的收敛分析框架，该框架依赖于在文献中常用的最基本结构假设下的基本递归估计。虽然这种方法可应用于分析多种方法，但我们仅在几个著名方案上进行了演示。请注意，我们并未提出任何新算法，而是利用简单的递归估计统一了收敛分析。然而，我们相信这种方法可以延伸至本章所做工作之外。以下研究课题引起了我们的兴趣。首先，是否仍可将我们的分析应用于加速方差缩减随机梯度类方法？也许可以借鉴近期工作 [\[15\]](#Chp001_3-28_B9780443190377000089_split_002.xhtml#br0075) 的思想来实现。其次，如何将我们的框架扩展以研究分布式系统和联邦学习中的其他优化方法？我们强调，这些领域中的许多算法可视为随机[区块-]坐标方法。因此，向坐标方法和洗牌方法的扩展前景广阔且仍是开放问题。第三，是否可能将我们的分析扩展并适应于异步基于梯度的算法？我们认为，只要延迟有界，这种扩展就是可能的。然而，需要修改递归表达式以捕捉延迟更新，从而在递归不等式中产生额外的误差项。最后，我们的方法可用于分析极小极大和变分不等式问题算法的收敛性，这些问题最近获得了极大的关注 [\[19](#Chp001_3-28_B9780443190377000089_split_002.xhtml#br0095),[65\]](#Chp001_3-28_B9780443190377000089_split_002.xhtml#br0325)。

## 参考文献

*   \[1\] H.H. Bauschke, P. Combettes, *Convex Analysis and Monotone Operators Theory in Hilbert Spaces*. 2nd edition Springer; 2017.

*   [\[2\]](#Chp001_3-28_B9780443190377000089_split_000.xhtml#cs0010_2) A. Ben-Tal, A. Nemirovski, *Lectures on Modern Convex Optimization: Analysis, Algorithms, and Engineering Applications, vol. 3*. SIAM; 2001.

*   [\[3\]](#Chp001_3-28_B9780443190377000089_split_001.xhtml#cs0085_1) D.P. Bertsekas, *Nonlinear Programming*. 2nd edition Athena Scientific; 1999.

*   [\[4\]](#Chp001_3-28_B9780443190377000089_split_001.xhtml#cf0290) J. Bolte, A. Daniilidis, A. Lewis, The Łojasiewicz inequality for nonsmooth subanalytic functions with applications to subgradient dynamical systems, *SIAM J. Optim.* 2007;17(4):1205–1223.

*   

*   [\[5\]](#Chp001_3-28_B9780443190377000089_split_001.xhtml#cs0110_1) L. Bottou, F.E. Curtis, J. Nocedal, Optimization methods for large-scale machine learning, *SIAM Rev.* 2018;60(2):223–311.

*   [\[6\]](#Chp001_3-28_B9780443190377000089_split_001.xhtml#cs0110_2) Léon Bottou, Online learning and stochastic approximations, David Saad, ed. *Online Learning in Neural Networks*. New York, NY, USA: Cambridge University Press; 1998:9–42.

*   \[7\] S. Boyd, L. Vandenberghe, *Convex Optimization*. Cambridge: University Press; 2004.

*   [\[8\]](#Chp001_3-28_B9780443190377000089_split_001.xhtml#cf0365) S. Boyd, L. Xiao, A. Mutapcic, *Subgradient methods*. \[Tech. Report. EE392o\] Stanford University; 2003.

*   [\[9\]](#Chp001_3-28_B9780443190377000089_split_000.xhtml#cs0015_1) Sébastien Bubeck, Theory of convex optimization for machine learning, *Lecture Notes*. Princeton University; 2014.

*   [\[10\]](#Chp001_3-28_B9780443190377000089_split_000.xhtml#cs0015_1) P. Combettes, J.-C. Pesquet, Signal recovery by proximal forward-backward splitting, *Fixed-Point Algorithms for Inverse Problems in Science and Engineering*. Springer; 2011:185–212.

*   \[11\] A.R. Conn, N. Gould, P.L. Toint, *Trust-Region Methods*. MPS/SIAM Series on Optimization. Philadelphia, USA: SIAM; 2000.

*   [\[12\]](#Chp001_3-28_B9780443190377000089_split_000.xhtml#cs0045_1) A. Cutkosky, F. Orabona, Momentum-based variance reduction in non-convex SGD, *Advances in Neural Information Processing Systems*. 2019:15210–15219.

