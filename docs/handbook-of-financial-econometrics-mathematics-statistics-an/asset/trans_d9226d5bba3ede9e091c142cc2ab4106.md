
其中 $F_1(\cdot)$ 和 $F_2(\cdot)$ 分别是 alpha $t$ 比率的两个经验累积分布函数（CDF），一个来自数据，一个来自模型。该度量考察的是两个 CDF 之间的最大垂直距离。第二个替代度量是克拉默–冯·米塞斯距离，

$$D_{\mathrm{CvM}}=E_x\{[F_1(x)-F_2(x)]^2\}, \tag{108.9}$$

它考察的是均方距离。

为了实施这些替代度量，我们将来自原始数据和模型的 alpha $t$ 比率观测值合并，对这些值排序，并在每个离散点上计算两个 CDF。结果见附录，与使用原始度量得到的结果类似。

### 108.6.3 alpha 是否与主动管理相关？

多项研究表明，更主动的基金往往拥有更大的 alpha（例如，Cremers 和 Petajisto 2009；Titman 和 Tiu 2011；Amihud 和 Goyenko 2013；Ferson 和 Mo 2016）。特别是，因子模型回归 $R$ 方较低的基金被发现具有较大的 alpha。我们检验了因子模型 $R$ 方与估计 alpha 之间的相关性，发现共同基金样本中的相关系数为 −0.015，对冲基金样本中为 −0.111。上述模拟的分布混合并未体现这一关系。

我们修改模拟，使得 alpha 与主动管理之间的横截面关系得以体现，这种关系由提供 alpha 的因子模型回归中的 $R$ 方来衡量。我们按因子模型 $R$ 方对基金排序，并根据模拟中任意时点的 π-比例确定组规模，将基金分为三组，先将好的 alpha 分配给低 $R$ 方组，将差的 alpha 分配给高 $R$ 方组。因此，这种方法在 alpha 与主动管理之间建立了一种由因子模型 $R$ 方衡量的关系。

结果汇总在表 108E.4 的 D 组中。我们发现这一修改提高了拟合优度统计量。拟合最佳的 alpha 参数更靠近分布的尾部。在左尾中，差 alpha 向左移动了大约四分之一个百分点。好 alpha 的估计和好对冲基金的比例与原始设计中的结果相似。估计具有更悲观差 alpha 的对冲基金比例更低，而零 alpha 对冲基金的比例增加到 30–44%，当检验水平为 10% 时，这是一个显著为正的比例。BSW 估计值与原设计中的结果相似。结果表明，将高 $R$ 方对冲基金相对较差的表现纳入模型可以提高模型的拟合度。这一结果或许并不令人意外，但它确实表明，未来的模拟估计工作可能会从构建其他基金特征与绩效组之间的关联中获益。

### 108.6.4 替代 alpha

虽然 Fama 和 French（1996）三因子模型在基金业绩评估中比在资产定价中争议更少，但我们仍有必要问一下，结果是否对使用不同的 alpha 模型敏感。我们检验了共同基金的两种替代模型：一种因子较少，另一种因子较多。第一种是资本资产定价模型（Sharpe, 1964），只有一个市场因子；第二种是 Carhart（1997）模型，增加了一个动量因子。对于对冲基金样本，我们在主表中使用 Fung 和 Hsieh（2001, 2004）的多因子模型，并尝试使用 Fama 和 French 三因子模型作为稳健性检验。使用替代 alpha 的结果类似，部分结果报告在网络附录中。

### 108.6.5 收益平滑

收益平滑往往会减小基金收益的标准误，通过降低估计的 beta 而增大 alpha，并且可能对对冲基金很重要（例如，Asness 等，2001）。我们通过使用 Scholes–Williams（1977）估计值替代 beta 和 alpha 的估计值来处理收益平滑。在这里，我们在绩效回归中纳入因子的当前值和滞后值，beta 是当期因子和滞后因子系数之和。首先需要检查的是对原始数据中 alpha 的 t 比率的影响。结果展示在网络附录中。使用 Scholes–Williams beta 对 alpha t 比率分布的影响很小，因此我们不再进一步研究这个问题。

## 108.7 结论

我们以 Barras、Scaillet 和 Wermers（BSW，2010）的共同基金分类方法为基础。我们同时估计总体中好基金、零 alpha 基金和差基金的占比，以及这三个组别的 alpha 位置。我们修改了 BSW 的错误发现率框架，以允许不完美的检验功效和混淆情况，即检验可能将好基金判定为差基金，反之亦然。我们展示了如何将该模型作为关于基金横截面的先验信息来预测基金业绩。

我们将我们的方法应用于美国主动股票型共同基金样本和 TASS 对冲基金样本。估计有较大比例的对冲基金具有正 alpha 或负 alpha。对于共同基金，仅包含零 alpha 和负 alpha 的模型最能拟合数据。共同基金和对冲基金在高 alpha 组中都呈现出业绩随时间下降的趋势，而低 alpha 组的业绩未显示出趋势。

我们通过对模拟过程进行参数自举模拟来研究估计量的有限样本表现。我们从解析上和通过模拟均表明，当零 alpha 基金的真实比例较小时，经典的 FDR 方法会找到过多的零 alpha 基金，从而找到过少的好基金和差基金。我们的方法在提高异常业绩基金的检出率方面提供了更好的功效。

我们基于模拟的经验标准误表明，好基金和差基金占比周围的置信区间很宽。在使用对冲基金的例子中，经典 FDR 方法给出的零 alpha 基金占比的二倍标准误置信带为（11.0%，15.8%）。然而，在调整了标准误中的有限样本偏差后，置信带变为（21.1%，99.1%）。尽管精度不高，但我们可以用我们的估计量在统计上确信样本中存在正 alpha 和负 alpha 的对冲基金。共同基金则是另一回事，没有证据表明存在正 alpha，但有强有力的证据表明存在负 alpha。

我们的结果推动了未来的研究。例如，我们的一项稳健性检验表明，通过将基金业绩组与其他基金特征关联，可能可以获得更精确的推断。Chen、Cliff 和 Zhao（2017）在这方面提出了一些分析，进一步研究这一想法似乎是必要的。另一个思路是寻找更精确的业绩度量。我们使用标准因子模型的 alpha 来阐述我们的方法，但我们的方法也可以应用于其他基金业绩度量，例如基于持仓的度量（如 Daniel 等，1997）、随机贴现因子 alpha（Farnsworth 等，2002；Ferson、Henry 和 Kisgen，2006）、增加值度量（Berk 和 van Binsbergen，2015）以及总 alpha（Pástor、Stambaugh 和 Taylor，2015）。这些度量在衡量基金业绩方面各自都已被证明有其吸引力。

## 参考文献

Amihud, Y. and Goyenko, R. (2013). Mutual Fund R² as a Predictor of Performance. Review of Financial Studies 26, 667-694.

Ardia, D. and Boudt, K. (2018). The Peer Performance Ratios of Hedge Funds. Journal of Banking and Finance 87, 351-368.

Asness, C., Krail, R. and Liew, J. (2001). Do Hedge Funds Hedge? Journal of Portfolio Management 28, 6-19.

Avramov, D. and Wermers, R. (2006). Investing in Mutual Funds when Returns are Predictable. Journal of Financial Economics 81, 339-377.

Bajgrowicz, P. and Scaillet, O. (2012). Technical Trading Revisited: False Discoveries, Persistence Tests, and Transactions Cost. Journal of Financial Economics 106, 473-491.

Bajgrowicz, P., Scaillet, O. and Treccani, A. (2016). Jumps in High-Frequency Data: Spurious Detections, Dynamics, and News. Management Science 62, 2198-2217.

Baks, K., Metrick, A. and Wachter, J. (2001). Should Investors Avoid all Actively Managed Mutual Funds? A Study in Bayesian Performance Evaluation. Journal of Finance 56, 45-85.

Barras, L., Scaillet, O. and Wermers, R. (2010). False Discoveries in Mutual Fund Performance: Measuring Luck in Estimated Alphas. Journal of Finance 65, 179-216.

Barras, L., Scaillet, O. and Wermers, R. (2010). Internet Appendix to: “False Discoveries in Mutual Fund Performance: Measuring Luck in Estimated Alphas.” Journal of Finance 65, 179-216.

Berk, J. and Green, R. (2004). Mutual Fund Flows and Performance in Rational Markets. Journal of Political Economy 112, 1269-1295.

Berk, J. and van Binsbergen, J.H. (2015). Measuring Skill in the Mutual Fund Industry. Journal of Financial Economics 118, 1-20.

Brown, S.J. (1979). Optimal Portfolio Choice Under Uncertainty: A Bayesian Approach. In Bawa, V.S., Brown, S.J. and Klein, R.W. (Eds.), Estimation Risk and Optimal Portfolio Choice. North-Holland, Amsterdam, pp. 109-144.

Carhart, M.M. (1997). On Persistence in Mutual Fund Performance. Journal of Finance 52, 57-82.

Chen, Y., Cliff, M. and Zhao, H. (2017). Hedge Funds: The Good, the Bad, and the Lucky. Journal of Financial and Quantitative Analysis 52, 1081-1109.

Cremers, M. and Petajisto, A. (2009). How Active is Your Mutual Fund Manager? A New Measure that Predicts Performance. Review of Financial Studies 22, 3329-3365.

Criton, G. and Scaillet, O. (2014). Hedge Fund Managers: Luck and Dynamic Assessment. Bankers, Markets & Investors 129, 1-15.

Cuthbertson, K., Nitzsche, D. and O’Sullivan, N. (2012). False Discoveries in UK Mutual Fund Performance. European Financial Management 19, 444-463.

Daniel, K., Grinblatt, M., Titman, S. and Wermers, R. (1997). Measuring Mutual Fund Performance with Characteristic-Based Benchmarks. Journal of Finance 52, 1035-1058.

Das, S.R. (2013). Data Science: Theories, Models, Algorithms and Analytics, A Web Book.

Dewaele, B., Pirotte, H., Tuchschmid, N. and Wallerstein, E. (2011). Assessing the Performance of Funds of Hedge Funds. Working Paper, Solvay Brussels School.

Efron, B. and Tibshirani, R.J. (1993). An Introduction to the Bootstrap. Chapman & Hall.

Elton, E.J., Gruber, M.J. and Blake, C.R. (2001). A First Look at the Accuracy of the CRSP Mutual Fund Database and A Comparison of the CRSP and Morningstar Mutual Fund Databases. Journal of Finance 56, 2415-2430.

Evans, R.B. (2010). Mutual Fund Incubation. Journal of Finance 65, 1581-1611.
