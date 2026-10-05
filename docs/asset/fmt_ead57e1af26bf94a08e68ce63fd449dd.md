
在这里使用了默认的距离和连接方法。我们可以指定距离度量，如`Euclidean`和`Manhattan`距离，以及完全连接和`ward`方法。

## 层次聚类算法的优点

- 易于实现
- 生成类的层次结构，有助于我们决定聚类的数量

## 层次聚类算法的缺点

- 受离群值影响
- 受初始种子值影响
- 难以扩展

## 基于模型的聚类

我们可以使用`mclust`包构建基于模型的聚类。它使用极大似然估计法，利用贝叶斯信息准则（`BIC`）寻找最佳模型和聚类数量。

## 基于模型的聚类算法的优点

- 基于统计的聚类算法，有助于我们从聚类中得出推断
- 易于找到聚类数量
- 良好地处理离群值

## 基于模型的聚类算法的缺点

- 当样本点较少时，`BIC`分可能不可用

## 参考文献

- Likas, A., Vlassis, N., & Verbeek, J. J. (2003). The global k-means clustering algorithm. Pattern recognition, 36(2), 451-461.
- Rani¹, Y., & Rohil, H. (2013). A study of hierarchical clustering algorithm. ter S & on Te SIT, 2, 113.
- Zhong, S., & Ghosh, J. (2003). A unified framework for model-based clustering. The Journal of Machine Learning Research, 4, 1001-1037.
- Yu, M., Jieyan, Y., Jiajia, Z., & Xinzhou, C. (2021). Intelligent Detection of Network Coverage Problems Based on the Clustering Algorithm. In Signal and Information Processing, Networking and Computers (pp. 1010-1018). Springer, Singapore.
- Sinaga, K. P., & Yang, M. S. (2020). Unsupervised K-means clustering algorithm. IEEE Access, 8, 80716-8027.

句子需要被拆分为有意义的组件，如单词。空格或标点符号有助于我们将句子分词为单词。

## 词干提取 (Stemming)

词干提取有助于我们保留单词的词根。它有助于移除句子中具有相同词根的重复单词。

## 词性还原 (Lemmatizing)

它与词干提取相似，不同之处在于移除单词的形式变化时会将含义相似的词连接起来。

## 停用词移除 (Stop words removal)

停用词移除在预处理中起着重要作用，因为它移除了文档中频繁出现的如‘a’‘the’‘and’等停用词。

## 词性标注 (POS)

词性标注帮助我们标记句子中的词性，如名词、动词和形容词。词性标注在自然语言处理（NLP）和情感分析任务中起着重要作用。

## 分块 (Chunking)

分块是在句子标记级别完成的，通过将标记分组为相似的块或句法上相关的标记。

## 文本数据分析

文本数据分析涉及计算文档相关的指标、统计学、监督学习和无监督机器学习算法、自然语言处理技术以及情感分析技术。

### 文档相关指标

在分析开始阶段，我们需要计算以下指标，如词频 (TF)、逆文档频率 (IDF) 和词频矩阵 (TDM)。

### 词频矩阵 (TDM)

词频矩阵是文本语料库中文档的矩阵表示。在这里，列级包含文档，行级包含词。词权重可以通过二值权重（0 或 1）来衡量，即词是否出现在该文档中。

### 词频 (TF)

词频是特定文档中单词出现的频率。

### 逆文档频率 (IDF)

逆文档频率为不常见的单词（如‘a’和‘the’）分配较低权重。

### 词频-逆文档频率 (TF-IDF)

词频-逆文档频率为不常见的单词分配更高的权重。

## 统计建模 (Statistical Modeling)

文本挖掘中的统计建模涉及使用统计概率概念和分布。在分析阶段考虑了以下方面：

- 句子由单词序列组成。
- 通过联合概率获取下一个单词的概率。
- 计算整个句子的概率。

我们将使用语言模型，如`Unigram`和`N-gram`模型生成单词的概率分布。这里`Unigram`模型假设单词是独立的。马尔可夫模型帮助我们建模，它假设未来状态取决于当前状态而非过去状态。隐马尔可夫模型是马尔可夫模型的扩展，包含了观测到的从状态`i`到状态`j`的转移概率。

使用拉普拉斯和加法平滑技术将帮助我们调整单词序列中的概率。

## 监督机器学习算法

监督机器学习算法帮助我们将文本分类或分类到给定的主题或类别。垃圾邮件过滤是一个很好的示例。文本分类可以通过基于规则的方法完成，使用语言规则对输入的文本进行分类。这种方法具有挑战性。与基于规则的分类系统相比，监督机器学习系统不需要关于领域的完整知识，但它通过数据学习来提高分类准确率。可以使用支持向量机（SVM）和朴素贝叶（Naïve Bayes）等监督机器学习算法处理数据集。

## 无监督机器学习算法

无监督机器学习算法帮助我们分组或寻找文档之间的关联。可以使用 K 均值（K-means）划分算法或层次聚类算法对文档进行分组。例如，我们可以对具有相似主题的科学文章或具有相同疾病条件的患者记录分组。

## 主题建模 (Topic Modeling)

主题建模使用隐狄利克分布 (LDA) 等技术为文档集分配主题。LDA 首先生成主题下的单词概率模型，然后检查输入的文档并根据生成的概率模型分配主题。

## 情感分析 (Sentiment analysis)

情感分析帮助我们从给定的文本数据集中提取隐藏情感。情感分析对于分析产品、酒店或服务的评论非常有用。根据文本上下文，评论可以分类为积极、中性或消极。

## 文本数据的图形表示

提取的文本可以使用词云（Word Cloud）工具可视化。它以图形形式表示数据集中的词簇，其中出现频率最高的单词表示其在数据集中的重要性。

## 文本挖掘示例

让我们使用监督和无监督机器学习算法对示例数据集进行分类和聚类。我们还将基于示例数据集进行情感分析。

考虑一个假设的产品评论数据集，其中包含对产品的评论，每条评论将被视为分析的文档。在这里，我们提取了评论并将其存储在单个文本文件中。在实时应用中，使用 API 或网络爬取方法会更好。

### 通过 API 提取 Twitter 推文

以下代码帮助我们如何使用 Twitter API 提取推文。要从 Twitter 获取推文，用户需要拥有 Twitter 账号并注册 API 请求，注册后我们将获得以下密钥：

- Consumer key
- Consumer secret key

我们需要安装`rtweet`包并与其他所需的包一起定义它。

我们需要在以下代码中输入这些：

```
![](img/file97.png)
```

我们将获得 Twitter 的确认。现在我们可以使用以下代码搜索 Twitter 并获取所需的推文到我们的 R 环境。

```
![](img/file98.png)
```

这些可以进一步处理。

### 网络爬虫 (Web scraping)

我们可以通过网络爬取方法从在线网站提取文本。我们需要安装`rvest`和`xml2`包来执行网络爬取。

以下代码帮助我们从网站提取数据。在这里我们将使用`read_html()`和`html_nodes()`分别读取和提取 html 标签。要提取这些标签内部的内容，我们需要使用`html_text()`函数。

```
![](img/file99.png)
```

### 产品评论示例

现在我们从存储在工作目录文本文件中的假设产品评论示例数据集开始。

```
![](img/file100.png)
```

我们将使用 TM 包来执行文本挖掘过程。

我们将从文本文件中创建语料库并将其表示在向量空间中。下一步，我们将使用`tm`包中的`tm_map`函数通过移除停用词、标点符号、数字和空格对文档进行预处理。

在这里，为了分析目的，我们将每个句子转换成了单个文档。现在我们将构建词项-文档矩阵 (TDM)。

下面给出了最终 TDM 的几行：

我们将使用`wordcloud`包对文本进行可视化。

## 文本分类示例 – 监督性机器学习算法

现在我们将使用下方链接中的公开数据集，该数据集包含产品评论，并将评论分类为`label1`和`label2`（`label1-positive`和`label2-negative`），用支持向量机 (SVM) 算法对评论进行分类。

https://github.com/necronet/RML-101/blob/master/svm_textclassification/corpus.csv

我们将定义构建 SVM 模型所需的包，并读取 Excel 文件的内容。

我们将为构建 SVM 模型定义训练和测试数据集。

我们将`LABEL`变量定义为因子 (factor)，并在 SVM 模型中使用它。

模型的摘要如下：

我们可以通过混淆矩阵检查预测准确率。

这里的准确率少于 0.53，这可能是由于数据集的原因。我们可以使用`ROCR`包绘制 ROC 曲线。

得到的如下 ROC 曲线所示：

## 文本分类 – 非监督性机器学习算法

我们可以使用无监督性机器学习算法，通过凝聚聚类 (Agglomerative clustering) 技术对评论进行分组或聚类。我们将使用相同的产品评论数据，但会移除标签，仅选取 50 条评论进行分析。

我们将像以前一样借助`tm`包的`tm_map`函数对数据进行预处理。得到如下文档-词项矩阵，其中行表示文档，列表示语料库中的单词。

我们将使用`hclust`函数定义距离度量并构建层次模型，同时绘制聚类图 (dendogram)，该图提供了所考虑评论之间关联关系的图形化表示。它展示了哪些评论是相似的，或者说客户给出的评论。

## 情感分析示例

我们可以通过`syuzhet`包提取隐藏的情绪。我们将使用包含 50 条评论的产品评论集。我们将使用`get_nrc_sentiment`函数获取情感并计算诸如“愤怒”、“喜悦”、“正面”和“负面”等情感得分。同样的内容将以图形形式呈现。

## 参考文献

- Aggarwal, C. C., & Zhai, C. (Eds.). (2012). Mining text data. Springer Science & Business Media.
- Hotho, A., Nürnberger, A., & Paa, G. (2005, May). A brief survey of text mining. In Forum (Vol. 20, No 1, pp. 19-62).
- Berry, M. W., & Kogan, J. (2010). Text mining. Applications and Theory. West Sussex, PO19, John & Sons.
- Cheng, M. Y., Kuso, D., & Gosno, R. (2020). Text mining-based classification using hybrid machine learning. Automation in Construction, 118, 10265.
- Ju, Z., Wang, J., & Zhu, F. (2011, May). Named entity recognition from biomedical text using SVM. In 5th international conference on bioinformatics and biomedical engineering (pp. 1-4).
- Agnihotri, D., Verma, K., & Tripathi, P. (2014, April). Pattern and cluster mining on text data. In 4th International Conference on Systems and Network Technologies (pp. 428-432).
- Vijayani, S., Ilamathi, J., & Nithya, M. (2015). Preprocessing techniques for text mining-an overview. International Journal of Computer Science & Communication, 5(1), 7-16.
- Kadhim, A. I., Cheah, N., & Ahamed, H. (2014, December). Text document preprocessing and dimension reduction techniques for text clustering. In 4th International on Artificial Intelligence with Applications in Engineering (pp. 69-73).
- Grabner, D., Zanker, M., Flied, G., & Fuchs, M. (2012, January). Classification of customer reviews based on sentiment analysis. In (pp. 460-470).
- https://cran.r.project.org/package=tm
- https://cran.r.project.org/package=xlsx
- https://cran.r.project.org/package=rvest
- https://cran.r.project.org/package=cluster
- https://cran.r.project.org/package=xml2
- https://cran.r.project.org/package=xlsx
- https://cran.r.project.org/package=e171
- https://cran.r.project.org/package=caret
- https://cran.r.project.org/package=ROCR
- https://cran.r.project.org/package=syuzhet

## 第 10 章：图像处理

图像处理和分类可以通过`keras`包在 R 中完成。深度学习模型被广泛用于。原始图像需要转换为数组，包含图像 ID、高度和宽度。

- https://tensorflow.rstudio.com/guide/keras/
- https://cran.r.project.org/package=keras
- Mishra, N. K., & Celebi, M. E. (2016). An overview of melanoma detection in dermoscopy images using image processing and machine learning. arXiv preprint arXiv:1601.07843.
- Pandey, R., Naik, S., & Marfatia, R. (2013). Image processing and machine learning for automated fruit grading system: A technical review. International Journal of Computer Applications, 81(16), 29-39.

## 参考文献

- Lézoray, O., Charrier, C., Cardot, H., & Lefèvre, S. (2008). 图像处理中的机器学习。
- Jagadev, P., & Virani, H. G. (2017, May). 使用图像处理和机器学习检测白血病及其类型。见 2017 年国际电子与信息趋势会议 (ICEI) (pp. 522-526)。IEEE。
