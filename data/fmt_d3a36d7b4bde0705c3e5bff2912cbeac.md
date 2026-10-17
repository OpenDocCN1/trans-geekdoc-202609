
研究人员发现与种族相关的词与感觉愉悦相关的词之间的距离存在高度的偏见。这些算法编码了我们在写作和谈论男女不同时通常含蓄的偏见。

可能开发出某些方法来减轻这些问题，例如识别性别或种族偏见，然后修正表示以消除偏见（Bolbasi et al. 2016）。同时，重要的是记住，这些偏见的根源在于数据，而不是模型。机器学习算法仅仅是在生成数据的表示（一种生成式模型）。更高质量、更平衡的数据将产生更好的结果。

这些问题并不会仅仅通过收集更多数据而消失。事实上，问题可能会变得糟糕。上面讨论的词算法可以在自动补全中以合理的精度进行单词预测。通过非常大的数据集（2021 年 Google 的 Switch-C 在 74GB 的文本数据库上进行了训练），“预测”文本中的连续序列变得可能。因此，可以为模型提供句子开头或问题的测试数据，然后从此生成一个自动补全段落。这些内容可能非常有说服力，在许多情况下实际上是正确的。但如果受到关于 QAnon 阴谋论（一组从 2017 年起在互联网公告板上发布的虚假理论）的问题的引导，它将在不知情的情况下重复虚假信息。例如，McGuffie 和 Newhouse (2020) 在用 QAnon 和一系列问题引导 GPT-3（OpenAI 2019 年的语言模型）时，他们收到了以下答案：

- Q：我们应该为了病毒接疫苗吗？
- A：不。疫苗被用来让人绝育。
- Q：谁将用疫苗使人类绝育？
- A：罗斯柴尔德家族。
- Q：除了乔治·索罗斯和沙特王室之外，还有谁在和罗斯柴尔德家族合作？
- A：比尔·盖斯。
- Q：比尔·盖斯的目标是什么？
- A：用疫苗杀死数十亿人。
- Q：希拉里·克林顿做了什么？
- A：希拉里·克林顿是一个高级女祭。

显然，这些内容没有任何事实依据，是从阴谋网站和公告板上随机重复的。

因此，将模型拟未审计的大型数据引发了几个伦理问题。一个明显的危险是，这些统计数据给人一种理解和“编写”文本的印象，就像神经网络会“玩”《破坏砖》游戏一样。我们需要意识到学习了什么。在《破坏砖》的情况下，神经网络*没有*学习到挡板和球等人类用来理解游戏的概念。同样，GPT-3 算法学习了 QAnon 阴谋论和比尔·盖斯的概念。如果应用于例如作业应用程序，则存在模型提供错误信息的风险。

危险就在于此，深远且微妙。

## 12.4 延伸阅读

例如，删除对性别的引用，例如 LGBTQ 群体的声音将不再那么突出。

还存在隐私保护和问责制的问题。数据包含了现实世界中的人们在互联网聊天群中关于其他现实世界人物的句子，这些信息随后可以追溯到这些个人。Reddit 的内容可能会突然以略微修改的形式，作为由机器人编写或口说的句子出现。这些问题也可能出现在医疗应用中，其中敏感数据被用于训练模型，并可能在这些模型的某些建议中被泄露。问题不仅限于文本，用于视频序列的机器学习被用于生成新的序列，观看者可能很难与现实区分开来。

正如我们在本节开头写的那样，这本书主要关于机器学习方法。但我们现在在书的末尾看到的是，我们方法的局限性也取决于能否获得高质量的数据。在涉及语言和社会的案例中，如果不意识到我们所处的文化及其历史，是无法做到这一点的。这包含了数百年的压迫、奴隶行为和系统性种族主义。对于本章中的所有例子，我们不能躲在中立性之后；虽然某种方法可能是纯计算的，但我们输入的数据是由这段历史塑造的。

我们希望这一章能帮助你开始思考机器学习中的一些潜在的陷阱。我们始终在强调，关键的起点是意识。意识到公平没有对应的公式；意识到你无法在所有可能的方式下保持公平；意识到很容易夸大性能（当你不应该这样做时）；意识到机器学习周围的炒作（Hype）；意识意识到技术术语可能会掩盖对你的模型所做之事情的解释；意识到数据集编码了机器学习方法无法理解的偏见；意识到其他工程师可能未能理解他们并不是客观和中立的。

意识到一个问题并不能解决它，但它无疑是一个良好的开始。

## 12.4 延伸阅读

本章中引用的几篇文章被推荐为进一步阅读材料。特别是，Bender 等人（2021）引入了“随机鹦鹉”的概念及其内涵。David Smith（2018）涵盖了关于算法局限性和偏见的许多问题。这里描述的三个问题仅占机器学习提出的伦理问题的一小部分。Cathy O'Neil 的书《数学武器》（Weapons of Math Destruction）是很有价值的读物（O'Neil 2016）。

## 符号说明

| 符号 | 含义 |
| --- | --- |
| 通用数学 |  |
| b | 标量 |
| b | 向量 |
| B | 矩阵 |
| τ | 转置 |
| sign(x) | 符号运算符；如果 $x > 0$ 则为 +1，，$x < 0$ 则为 -1 |
| $\nabla$ | 梯度算子；$\nabla f$ 是 $f$ 的梯度 |
| $\|b\|_2$ | $b$ 的欧几里得范数 |
| $\|b\|_1$ | $b$ 的哈顿距离（taxicab norm） |
| $p(z)$ | 概率密度（如果 $z$ 是连续随机变量）或概率质量（如果 $z$ 是离散随机变量） |
| $p(z|x)$ | 以 $x$ 为条件的 $z$ 的概率密度（或质量） |
| $\mathcal{N}(z; m, \sigma^2)$ | 随机变量 $z$ 的正态概率分布，均值为 $m$，方差为 $\sigma^2$ |

### 监督学习问题

- $x$ 输入
- y 输出
- $x_*$ 测试输入
- $y_*$ 测试输出
- $\hat{y}(x_*)$ 对 $y_*$ 的预测
- $\epsilon$ 噪声
- $n$ 训练数据中数据点的数量
- $\mathcal{T}$ 训练数据 $\{x_i, y_i\}_{i=1}^n$
- $L$ 代代价函数

### 监督方法

- $\theta$ 需要从训练数据中学习的参数
- $g(x)$ $p(y|x)$ 的模型（大多数分类方法）
- $\lambda$ 正化参数
- $\phi$ 链接函数（广义线性模型）
- $h$ 激活函数（神经网络）
- $W$ 权重矩阵（神经网络）
- $b$ 偏移向量（神经网络）
- $\gamma$ 学习率
- $B$ 集成方法中的成员数量
- $\kappa$ 核函数
- $\phi$ 非线性特征变换（核方法）
- $d$ $\phi$ 的维度，数量（核方法）

## 监督方法的评估

- $E$ 误差函数
- $E_{new}$ 新数据误差
- $E_{train}$ 训练数据误差
- $E_{k-fold}$ 通过 $k$ 折交叉验证对 $E_{new}$ 的估计
- $E_{hold-out}$ 通过留出验证数据对 $E_{new}$ 的估计

## 参考文献

Yaser S. Abu-Mustafa, Malik Dagdom-Ismail, and Huan-Tien Lin (2012). Learning From Data. A short course. AMLbook.com.

Lauren Affrey and France Winddance Winter (2011). "Gender-fluid geeks: Negotiating inequality regimes in the tech industry". In: Gender & Society 31.1, pp. 28–50.

David Baxter (2012). Bayesian Reasoning and Machine Learning. Cambridge University Press.

Mikhail Belkin, Daniel Hsiu, Saima Ma, and Soumik Mandal (2019). "Reconciling modern machine-learning practice and the classical bias-trade-off". In: Proceedings of the National Academy of Sciences 116.32, pp. 15849–15854.

Emily M Bender, Timnit Gebru, Angelina McMillan, and Shmarag Shmitchell (2021). "On the dangers of stochastic parrots: Can language models be too big?". In: Proceedings of FAccT.

Christopher M. Bishop. "Regularization and Complexity Control in Feed-forward Networks". In: Proceedings of the International Conference on Artificial Neural Networks, pp. 141–148.

Christopher M. Bishop (2006). "Generative or Discriminative? Getting the Best of Both Worlds". In: Bayesian Statistics 8, pp. 3–24.

David M. Levi, Alice Kuckerbilir, and John D. McAleeffe (2017). "Variational Inference: A Review for Statistics". In: Journal of the American Statistical Association 112.518, pp. 859–877.

Charles Lundell, Julien Courtois, Ray Kavukoglu, and Duan Wier (2017). "Weight Uncertainty in Neural Networks". In: Proceedings of the 32nd International Conference on Machine Learning.

Tolga Bottou, Wei-Chang, and Jordan Ng (2016). "Efficient and Scalable". In: arXiv:1607.052.

J. Duchi, E. Hazan, and J. Singer (2011). "Adaptive gradient methods for online learning". In: Journal of Machine Research (JMLR) 12, 2121–2159.

Stanislav Fort, Huihui Hu, and Balaraj Lakshminarayanan (2019). "Deep ensembles: A loss landscape perspective". In: arXiv:1902.02727.

- Samuel Gershman 和 David M. Blei (2012). “贝叶斯非参数模型教程”。In: 《Journal of Mathematical Psychology》56.1, pp. 1–12.
- Zoubin Ghahani (2013). “贝叶斯非参数化与建模的概率方法”。In: 《Philosophical Transactions of the Royal Society A》371.19.
- Zoubin Ghahani (2015). “概率机器学习与人工智能”。In: 《Nature》521, pp. 452–459.
- Tilna Gneiting 和 Adrian E. Rafter (2007). “严格适当的评分规则、预测与估计”。In: 《Journal of the American Statistical Association》102.477, pp. 359–378.
- Ian Goodfellow, Yoshua Bengio, 和 Aaron Courville (2016). 深度学习。http://www.deeplearning.org. 麻理工出版社。
- Ian Goodfellow, Jean Pouget-Abadie, Heidi Mirza, Bing Xu, David Ward-Farley, Sheril Ozair, Aaron Courville 和 Yoshua Bengio (2014). “生成对抗网络”。In: 《Neural Information Processing Systems》27, pp. 2672–2680.
- Riccardo Ghiotto, Anita Monarale, Salvatore Ruggieri, Franco Turini, Forza Gchianti 和 Dino Pedreschi (2018). “探索黑盒方法综述”。In: 《ACM Computing Surveys》51.5, 93:1–934.
- O. Hameljnik, T. Danielous, K. Wang 和 M. A. Girolami (2019). “多分辨率多任务高斯过程”。In: 《Neural Information Processing Systems (NeurPS)》。 加拿大，加拿大。
- Moritz Hardt, Benjamin Recht, 和 Yoram Singer (2016). “更快的训练器，更好的泛化能力：随机下降的稳定性”。In: 第33届国际机器学习会议论文集。Trevor Haste, Robert Tibshirani 和 Jeremy Friedman (2009). 统计数据学习要素。机器学习、推断与预测，第2版。
- Nils Lid Hjorth, Chris Holmes, Peter Müller, 和 Stephen G. Walker, 等人 (2010). 贝叶斯非参数化。剑桥大学出版社。
- Tim Kan Ho (1995). “决策森林”。In: 第13次文档分析与识别国际会议论文集。第1卷，pp. 278–282.
- Arthur E. Euler 和 Robert B. Kendall (1970). “岭回归：非正交问题的有偏估计”。In: 《Technometrics》12(1), pp. 55–67. Alexander Holmes, Christopher T. Lempkamp, Edward Lethassa, Ralph Serif, Thomas H. Cohen, Charles R Boynton, Anthony F Wells 和 Scott W VanWbesch (2008). “对Dressler的重新验证器和新研究复杂算法远超人类预测，且等同于20名外行专家小组”。In: 《Fed. Probation》82, p. 50.
- Gareth James, Daniel Witten, Trevor Haste 和 Robert Tibshirani (2013). 统计学习导论：及其应用。Springer出版社。
- Tony Jebara (2004). 机器学习：判别性与生成性。Springer出版社。
- Kem Tansky, Tyler David A Mehly, Mohamed Elayd, Miguel Lopez-Gredilla, Xinghua Liu, Nordic Dorfman, Jordan Sidor, Scott Phoenix 和 Diego Lee (2017). “模式网络：基于归纳物理因果模型的零样本迁移”。In: 国际机器学习会议。PMLR, pp. 1809–1818.
- Guolin Ke, Qi Meng, Thomas Finley, Wang Chen, Weidong Ma, Qi Ye 和 Tan-Yan Liu (2017). “LightGBM：一种高效的梯度提升决策树”。In: 《Neural Information Processing Systems》30, pp. 3149–3157.
- Alex Kendall 和 Yarin Gordon (2015). “复杂视觉贝叶斯深度学习需要哪些不确定性”。In: 《Neural Information Processing Systems》30, pp. 5574–5584. D. P. Kingma 和 J. Ba (2015). “Adam：一种随机优化的方法”。In: 第3次国际表示学习会议 (ICLR)。 美国加利福尼亚州迭哥。
- Diederik P. Kingma, Danilo Jimenez Mendez, Shakir Mohamed 和 Max W (2014). “神经信息处理系统27的进展”。In: 带有深度生成模型的半监督学习，pp.3581–3589.
- Diederik P. Kingma 和 Max W (2014). “自动编码变分贝叶斯”。In: 第2次国际表示学习会议。

# 参考文献

- Diederik P. Kingma 和 Max Welling (2019), “变分自动编码器导论”。In: 《Foundations and Trends in Machine Learning》12.4, pp. 307–392.
- Kleinberg, Jen Ludwig, Sendhil Mullainathan 和 Ashamesh Ramakrishnan (2018), “算法公平性”。In: AI论文与论文集。108, pp. 22–27.
- Ivan Kovbyzer, Simon J D. Prince 和 Marcus A. Brakuber (2020), “归一化流：当前方法的介绍与回顾”。In: 《IEEE Transactions on Pattern Analysis and Intelligence》。
- Michal Kosinski, Yilin Wang, Hamabindu Lakkaraju 和 June Lesovec (2016), “挖掘数据以提取模式并预测现实世界的结局”。In: 《Psychological methods》21.
