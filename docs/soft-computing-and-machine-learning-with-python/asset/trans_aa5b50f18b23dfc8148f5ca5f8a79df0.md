

corpus.append(s, type=p)

```python
classifier = KNN()
for document in corpus:
    classifier.train(document)
print classifier.classify('sweet') # yields 'WIN'
print classifier.classify('stupid') # yields 'FAIL'd'
```

**图 2：** 用于 Twitter 消息训练的 k-NN 分类器示例源码。

# 案例研究

作为一个案例研究，我们使用 PATTERN 创建了一个荷兰语情感词汇（De Smedt and Daleemans, 2012）。我们挖掘了荷兰语书籍评论，并提取了频率最高的 1,000 个形容词。这些词被手动标注了积极性、消性和主观性评分。然后，我们使用分布扩展扩大了词汇。从 TWNC 语料库（Orelman et al., 2007）中，我们提取了频率最高的名词以及位于这些名词之前的词。这产生了一个包含 5,750 个形容词向量的向量空间，名词作为特征。对于每个标注的形容词，我们计算了 k-NN 并将其得分继承给邻近的形容词。该词汇被封装在 PATTERN 2.3 中。

# 文档

PATTERN 附带示例和单元测试。文档包含快速概述、安装说明，以及每个模块的包含 API 引用、用例示例和科学原理讨论的详细页面。该文档假设用户没有先验知识，除非具有 Python 编程背景。单元测试套件包含了一组用于测试准确性的语料库，例如 POLARITY DATA SET V2.0（Pang and Lee, 2004）。

# 源码

PATTERN 使用纯 Python 编写，这意味着我们为了开发速度和可读性牺牲了性能（即较慢的聚类算法）。该包运行在所有平台上，且没有依赖项（在使用 LSA 时使用 NumPy 外外）。源码附有开发者注释。它托管在 GitHub (github.com) 上，并使用 Git 版本控制系统。欢迎贡献。

源码在 BSD 许可证下发布，因此它可以被整合到专有产品中，或与其他开源包结合使用，如 SCRAPY（挖掘）、NLTK（自然语言处理）、PYBRAIN 和 PYML（机器学习）以及 NETWORKX（网络分析）。我们提供了一个指向 MBSP FOR PYTHON（De Smedt et al., 2010）的接口，这是一个基于 TIMBL 机器学习软件构建的健壮的基于内存的浅层解析器。PATTERN 解析器和 MBSP 的 API 是相同的。

# 致谢

开发资金由安特卫普大学的工业研究基金（IOF）资助。

# 参考文献

- 1. David Arthur and Sergei Vassvilitkii. k-means++: the advantages of careful seeding. Proceedingsof the Eighteenth Annual ACM-SIAM Symposium on Discrete Algorithms, pages 1027–1035, 2007.
- 2. Mathieu Bastian, Sebastian Heymann, and Mathieu Jacomy. Gephi: An open source software exploring and manipulating networks. Proceedings of the Third International ICWSM Conference, 2009.
- 3. Steven Bird, Ewan Klein, and Edward Lopez. Natural Language Processing with Python. O’ReillyMedia, 2009.
- 4. Ulrik Brandes. A faster algorithm for betweenness centrality. The Journal of Mathematical Sociology, 25(2):166–177, 2001.
- 5. Eric Brill. A simple rule-based part of speech tagger. Proceedings of the Third Conference on Applied Natural Language Processing, pages 152–155, 1992.
- 6. Chih-Chung Chang and Chih-Jen Li. LIBSVM: a library for support vector machines. ACM Transactions on Intelligent Systems and Technology, 2(3), 2011.
- 7. Damian Conway. An algorithmic approach to english pluralization. Proceedings of the Second Annual Perl Conference, 1998.
- 8. Tom De Smedt and Walter Daelemans. Vreseljk mooi! (terribly beautiful): A subjectivity lexicon for dutch adjectives. Proceedings of the 8th Language Resources and Evaluation Conference (LREC’12), pages 3568–3572, 2012.
- 9. Tom De Smedt, Vincent Van Asch, and Walter Daelemans. Memory-based shallow parser for python. CLIPS Technical Report Series, 2, 2010.
- 10. Janez Demsar, Ba Zupan, Gregor Leon, and Tom Curk: From experimental machine learning to interactive data mining. Knowledge Discovery in Databases, 3202:537–539, 2004.
- 11. Charles Elkan. Using the triangle inequality to accelerate k-means. Proceedings of the Twentieth International Conference on Machine Learning, pages 147–153, 2003.
- 12. Christiane Fellbaum. WordNet: An Electronic Lexical Database. MIT Press, Cambridge, 1998.
- 13. Jeroen Geertzen. Jeroen geertzen :: software & demos : Brill-nl, June 2010. URL http://cosmion.net/jeron/software/brill\_pos.
- 14. Aric Hagberg, Daniel Schult, and Pieter Swart. Exploring network structure, dynamics, and function using networkx. Proceedings of the 7th Python in Science Conference, pages 11–15, 2008.
- 15. Adam Kilgarrff, Structured prediction for practitioners as well as researchers, in Python. Computational Linguistics, 29(3):333–347, 2003.
- 16. Roeland Ordel, Structured prediction for practitioners as well as researchers, in Python. Computational Linguistics ELRA Newsletter, 12:3–4, 2007.
- 17. Bo Pang and Lillian Lee. Sentiment analysis using summarization. Proceedings of the ACL, 271–278, 2004.
- 18. Tom Schaul, Justin Bayer, Daan Wierstra, Frank Sehne, and Jurgen Schmidhuber. Machine Learning Research, 743–746, 2010.

# 第 10 章
# PYSTRUCT - 在 Python 中学习结构化预测

Andreas C. Müller 和 Sven Behnke
德国波恩，计算机科学学院，第 VI 部门

# 摘要

结构化预测方法已成为许多机器学习应用的核心工具。尽管有越来越多的算法被开发出来，但可用的实现较少。

PyStruct 旨在为从业者和研究人员提供标准预测方法的通用实现。它用 Python 编写，并借鉴了科学社区的范式。

**关键词：** 结构化预测，结构向量机，条件随机场，Python

> *引用:** A. C. Müller, S. Behnke, "PyStruct - Learning Structured Prediction in Python", Journal of Machine Research, 15 (Jun), pp. 2055–2060, 2014.

**版权：** ©2014 作者及 Journal of Machine Research。本文根据 Creative Commons Attribution 3.0 许可开放

# 引言

近年来，结构化预测方法的研究非常丰富，并应用于语言处理和计算机视觉等领域。遗憾的是，公开的实现很少——许多应用是非免费的 (2009)。

PyStruct 旨在用高级 Python 提供一个高质量的实现和易于使用的接口。这使得从业者能够高效地测试一系列模型，使研究人员能够更容易地与基准进行比较（相比目前的实现）。PyStruct 使用 BSD 许可，允许修改和分发代码。通过采用科学社区建立的范式并重用常用的 scikit 库 (Pedregosa et al., 2011) 的接口，PyStruct 可以用于现有项目。在线文档和示例帮助新用户理解结构化预测背后的抽象。

# 结构化预测与软件实现

结构化预测可以定义为通过化输入 x 与可能的标签 y 之间的兼容性来做出预测 f(x) (Nowozin and Lampert, 2011)。大多数方法使用线性标签，导致：

f(x) = arg \max_{y \in Y} \theta^T \Psi(x, y).

在这里，y 是结构化标签，$\Psi$ 是 x 和 y 的联合特征函数，$\theta$ 是模型参数。结构化意味着 y 比单个输出标签复杂，例如句子中的单词或图像每个像素的标签。学习结构化预测意味着从训练数据学习参数 $\theta$。

使用上述公式，学习可以分解为三个子问题：

- 1. 对 $\theta$ 优化目标函数。
- 2. 在联合特征函数 $\Psi$ 中编码问题结构。

