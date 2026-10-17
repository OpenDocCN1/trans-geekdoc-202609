
## 也称为带评论者的学习

智能体执行一系列动作，仅在最后获得奖励/惩罚，中间动作无反馈。利用这些有限信息，智能体应学会生成动作以在后续试验中最大化奖励。例如下棋，我们走一系列步骤，最后输赢分晓；因此我们需要弄清是哪些动作导致了该结果，并相应地给予它们信用。

## 样本

一组观测数据。在统计学中，我们区分**总体**和样本。假设我们要研究高中生肥胖情况。总体是所有高中生，但我们不可能观测所有人的体重。相反，我们随机选取一个子集，例如 1,000 名学生，观测他们的体重。这 1,000 个值就是我们的样本。我们分析样本以推断总体。从样本计算出的任何值都是统计量。例如，样本中 1,000 名学生体重的平均值是一个统计量，也是总体均值的一个估计量。

## 智能设备

其感测数据以数字形式表示并对此数据进行某种计算的设备。该设备可能是移动的，也可能是在线的；即它可能具备与其他智能设备、计算机或**云**交换数据的能力。

## 语音识别

通过麦克风捕获的声学信息识别说出的句子。

## 监督学习

一种机器学习类型，模型学会为任何输入生成正确输出。模型使用监督者准备的数据进行训练，监督者可为给定输入提供期望输出。**分类**和**回归**是监督学习的例子。

## 时序差分学习

一组用于**强化学习**的方法，通过将当前动作的优劣值回溯至紧接在它之前的动作来进行学习。一个例子是 **Q-learning** 算法。

## 迁移学习

使用在任务 **A** 上完全或部分训练好的模型来解决任务 **B**。用于**神经网络**时，这对应于将在 **A** 上训练的网络的某些层也用于为 **B** 训练的网络。如果 **A** 和 **B** 是相似任务，且我们对 **A** 的数据比 **B** 多时，这特别有用。

## 验证

通过在训练期间未见过的数据上测试已训练模型，来测试其**泛化**性能。通常在机器学习中，我们留出一部分验证数据，训练后在此数据上测试。该验证准确率是模型日后在实际应用中预期表现的一个估计量。

## 网页抓取

自动浏览网页并从中提取信息的软件。

## 注释

### 前言

1. “围棋大师李世石称因无法战胜 AI 围棋选手而退役。” 韩联社，2019 年 11 月 27 日。 [`en.yna.co.kr/view/AEN20191127004800315`](https://en.yna.co.kr/view/AEN20191127004800315) （访问于 2020 年 1 月 29 日）。

### 第 1 章

1. 这些使用为英文字母和标点符号设计的 ASCII 码。我们今天使用的字符编码方案涵盖了不同语言的不同字母表。

2. 在制造笔记本电脑、音乐播放器和智能手机等便携式电子设备时，可充电锂离子电池的发展至关重要。2019 年诺贝尔化学奖授予了三位使该技术成为可能的研究人员。

3. 仅凭计算能力、存储容量或连接性本身并不产生附加价值，正如人口增加不一定意味着劳动力增加。发展中国家庞大的智能手机数量并不等同于财富。

4. 计算机程序由用于任务的算法和用于所处理信息数字表示的数据结构组成。一本关于计算机编程的开创性书籍的标题就是：*算法 + 数据结构 = 程序*（Wirth 1976）。

### 第 2 章

1. 参见 <https://en.wikipedia.org/wiki/Depreciation>。

2. 这种平滑性假设在图像处理中也经常被使用。例如，当科学家在 2019 年首次捕捉到黑洞图像时，他们使用了事件视界望远镜，它实际上是全球多台望远镜的组合，每台望远镜只能记录一小部分。平滑性约束被用来将这些碎片拼凑在一起以获得完整图像，就像 Kanizsa 三角错觉那样，尽管我们实际看到的只是它的小碎片，我们却能想象出一个完整的大三角形。

3. 关于人工智能的精彩历史，请参见 Nilsson 2009。

4. 关于基于期望值或期望效用的决策可能不是最佳方式的一些现实场景，请参见 Sandel 2012。*帕斯卡的赌注* 是在不应应用期望值计算的领域应用该计算的另一个例子。

### 第 3 章

1. 这里我们讨论的是*光学*字符识别，其输入是图像；还有*笔迹*字符识别，书写是在触控板上进行的。在这种情况下，输入不是图像，而是书写笔尖在触控表面上书写时的 (`x`,`y`) 坐标序列。

2. 假设 `F` 代表流感，`N` 代表流鼻涕。使用贝叶斯法则，我们可以写出在已知某人流鼻涕的条件下，该人患流感的概率：

```
P(F|N) = P(N|F)P(F)/P(N)
```

这里，`P(N|F)` 是反方向的条件概率，即已知患者患有流感的条件下，患者流鼻涕的概率。`P(F)` 是患者患流感的概率，无论他们是否流鼻涕；`P(N)` 是患者流鼻涕的概率，无论他们是否患流感。

3. 有趣的是，在许多科幻电影中，尽管机器人在视觉、语音识别和自主移动方面可能非常先进，但它们仍然继续用无感情的、“机械式的”声音说话。

4. 这是由于孔多塞陪审团定理，该定理指出：在一个通过多数投票做决定的群体中，如果每个投票者以独立概率 `p` 投给正确决定，对于任意 `p` > ½（优于随机猜测），随着投票者数量的增加，多数投票正确的概率趋近于 1。这就是为什么民主优于君主制（孔多塞侯爵支持法国大革命，尽管他后来被视为叛徒并被送进监狱，最终死在狱中），但前提是投票者能够独立形成自己的观点，这也是新闻自由和言论自由等概念发挥作用的地方。

另一个含义是包容差异或对不同背景个体（如移民）持开放态度的国家的优势，因为它们知道差异是多样性的来源，进而是新思想的来源。从历史上看，我们看到无论是艺术创造力还是科学创造力，在长期作为贸易国家并持续与不同文化互动的国家，或欢迎移民的国家中都是最高的。人们常说创造力需要能够“跳出框框思考”；人们越不同，他们的框框重叠得就越少，结识不同的人会扩大一个人的框框。

5. 贝叶斯估计使用概率论中的贝叶斯法则（我们之前见过），以托马斯·贝叶斯（1702–1761）命名，他是一位长老会牧师。在观测数据之前并构成其基础的先验假设的存在，对于这份工作来说本应是自然而然的。

### 第 4 章

1. 请查看 <http://thispersondoesnotexist.com> 了解由 GAN 生成的示例人脸图像。

### 第 7 章

1. 引用自“人权与技术”讨论文件，澳大利亚人权委员会，2019 年 12 月，第 75 页，<https://www.humanrights.gov.au/our-work/rights-and-freedoms/publications/human-rights-and-technology-discussion-paper-2019>。

### 第 8 章

1. 光速约为 300,000 公里/秒，因此穿越 1,000 公里（到数据中心的距离）至少需要 3.33 毫秒。对于电子设备来说，这实际上并不是一个很小的数字。连接从来不是直接的，中间路由设备总会带来延迟；并且请记住，要获得响应，我们首先需要发送查询，所以我们需要将时间翻倍。

2. 更多内容请参见 *Frontiers in Massive Data Analysis*（华盛顿特区：国家科学院出版社，2013 年）。

## 参考文献

Bakshy, E., S. Messing, and L. A. Adamic. 2015. “Exposure to Ideologically Diverse News and Opinion on Facebook.” *Science* 348:1130–1132.

Blei, D. 2012. “Probabilistic Topic Models.” *Communications of the ACM* 55:77–84.

Bohannon, J. 2015. “Fears of an AI Pioneer.” *Science* 349:252.

Börner, K. 2015. *Atlas of Knowledge: Anyone Can Map*. Cambridge, MA: MIT Press.

Brown, N., and T. Sandholm. 2019. “Superhuman AI for Multiplayer Poker.” *Science* 365:885–890.

Buchanan, B. G., and E. H. Shortliffe. 1984. *Rule-Based Expert Systems: The MYCIN Experiments of the Stanford Heuristic Programming Project.* Reading, MA: Addison Wesley.

Eisenstein, J. 2019. *Introduction to Natural Language Processing*. Cambridge, MA: MIT Press.

Favaretto, M., E. De Clercq, and B. S. Elger. 2019. “Big Data and Discrimination: Perils, Promises and Solutions: A Systematic Review.” *Journal of Big Data* 6 (12): 1–27.

Feldman, J. A., and D. H. Ballard. 1982. “Connectionist Models and Their Properties.” *Cognitive Science* 6:205–254.

Fukushima, K. 1980. “Neocognitron: A Self-Organizing Neural Network Model for a Mechanism of Pattern Recognition Unaffected by Shift in Position.” *Biological Cybernetics* 36:93–202.

Gilpin, L. H., D. Bau, B. Z. Yuan, A. Bajwa, M. Specter, and L. Kagal. 2018. “Explaining Explanations: An Overview of Interpretation of Machine Learning.” ArXiv preprint ArXiv:1806.00069.

Goodfellow, I., Y. Bengio, and A. Courville. 2016. *Deep Learning*. Cambridge, MA: MIT Press.

Goodfellow, I. J. , J. Pouget-Abadie , B. Xu, D. Warde-Farley, S. Ozair, A. Courville, and Y. Bengio. 2014. “Generative Adversarial Networks.” ArXiv preprint ArXiv:1406.2661.

Han, J., and M. Kamber. 2011. *Data Mining: Concepts and Techniques*. 3rd ed. San Francisco, CA: Morgan Kaufmann.

Hebb, D. O. 1949. *The Organization of Behavior*. New York: Wiley & Sons.

Hirschberg, J., and C. D. Manning. 2015. “Advances in Natural Language Processing.” *Science* 349:261–266.

Hochreiter, S., and J. Schmidhuber. 1997. “Long Short-Term Memory.” *Neural Computation* 9:1735–1780.

Horvitz, E., and D. Mulligan. 2015. “Data, Privacy, and the Greater Good.” *Science* 349:253–255.

Hubel, D. H. 1995. *Eye, Brain, and Vision*. 2nd ed. New York: W. H. Freeman. http://hubel.med.harvard.edu/index.html.

Jordan, M. I., and T. M. Mitchell. 2015. “Machine Learning: Trends, Perspectives, and Prospects.” *Science* 349:255–260.

Koller, D., and N. Friedman. 2009. *Probabilistic Graphical Models.* Cambridge, MA: MIT Press.

Lazic, N., T. Lu, C. Boutilier, M. Ryu, E. Wong, B. Roy, and G. Imwalle. 2018. “Data Center Cooling using Model-Predictive Control.” In *Proceedings of the 32nd Conference on Neural Information Processing Systems*, 3818–3827.

LeCun, Y., Y. Bengio, and G. Hinton. 2015. “Deep Learning.” *Nature* 521:436–444.

LeCun, Y., B. Boser, J. S. Denker, D. Henderson, R.E. Howard, W. Hubbard, and L. D. Jackel. 1989. “Backpropagation Applied to Handwritten Zip Code Recognition.” *Neural Computation* 1:541–551.

Li, Y. 2019. “Reinforcement Learning Applications.” ArXiv preprint ArXiv:1908.06973.

Liu, T.-Y. 2011. *Learning to Rank for Information Retrieval*. Heidelberg: Springer.

Marr, D. 1982. *Vision: A Computational Investigation into the Human Representation and Processing of Visual Information*. Cambridge, MA: MIT Press.

McCulloch, W., and W. Pitts. 1943. “A Logical Calculus of the Ideas Immanent in Nervous Activity.” *Bulletin of Mathematical Biophysics* 5:115–133.

Mikolov, T., K. Chen, G. Corrado, and J. Dean. 2013. “Efficient Estimation of Word Representations in Vector Space.” ArXiv preprint ArXiv:1301.3781.

Minsky, M. L., and S. A. Papert. 1969. *Perceptrons*. Cambridge, MA: MIT Press.

Mitchell, T. 1997. *Machine Learning*. New York: McGraw Hill.

Mnih, V., K. Kavukçuoğlu, D. Silver, A. Rusu, J. Veness, M. G. Bellemare, A. Graves, et al. 2015. “Human-Level Control through Deep Reinforcement Learning.” *Nature* 518:529–533.

Moravcik, M., M. Schmid, N. Burch, V. Lisý, D. Morrill, N. Bard, T. Davis, et al. 2017. “DeepStack: Expert-Level Artificial Intelligence in Heads-Up No-Limit Poker.” *Science* 356:508–513.

Nilsson, N. J. 2009. *The Quest for Artificial Intelligence: History of Ideas and Achievements.* Cambridge, UK: Cambridge University Press.

Orbanz, P., and Y. W. Teh. 2010. “Bayesian Nonparametric Models.” In *Encyclopedia of Machine Learning*. New York: Springer.

Rosenblatt, F. 1962. *Principles of Neurodynamics*. Washington, DC: Spartan Books.

Rumelhart, D. E., G. E. Hinton, and R. J. Williams. 1986. “Learning Representations by Back-Propagating Errors.” *Nature* 323:533–536.

Rumelhart, D. E., and J. L. McClelland and the PDP Research Group. 1986. *Parallel Distributed Processing: Explorations in the Microstructure of Cognition.* Cambridge, MA: MIT Press.
