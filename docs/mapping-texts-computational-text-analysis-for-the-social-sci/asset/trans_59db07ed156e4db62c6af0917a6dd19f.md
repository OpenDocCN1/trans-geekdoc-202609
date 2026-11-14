

在美国，美国社会学协会（2021 年）的会员构成在 2020 年为：女性占 53.9%，男性占 44.2%，跨性别或非二元性别者占 1.9%。但是，在 *社会学年度评论* 本卷中，被归类为“女性”和“男性”的作者较少，这表明男性社会学家在主要出版物中可能被过度代表。不过，借鉴**语料库构建**中的经验教训，我们也必须考虑到，*社会学年度评论* 并非典型的学术期刊，因为其作者是受邀撰写的。

现在，假设我们有数万篇文章和数万名作者。考虑到潜在的测量误差，自动化性别标记可能是唯一可行的选择。即便如此，我们也要牢记 Mullen 等人的谨慎提示，并在与社区分享研究结果时务必讨论这些局限性。

## 命名实体识别

有时我们需要知道语料库中的文本在讨论谁或什么。如果我们对自己的文本了解甚多——或者想要查找特定实体的提及——那么或许可以构建一个由实体名称组成的自定义词典，并利用它来识别每篇文本提及这些实体的频率。例如，共和党总统在他们的国情咨文（SOTU）演讲中（反之亦然）提及民主党的频率有多高？我们只需统计国情咨文提及这两个特定两字词组的次数即可。

如果我们对语料库中的文本可能提及的人或组织了解甚少，那么可以使用**命名实体识别（NER）**。NER 标注器输入文本文档，并返回文本中找到的“实体”：例如，人名、组织、地点和日期等。NER 对信息提取问题很有用，也有助于构建词典，因为它可以用来识别语料库中被引用最频繁的人、地、事物等。

命名实体识别在社会科学中的应用日益广泛。我们（Stoltz 和 Taylor，2017）使用 NER 来识别报纸数据中的抗议事件，并在事件内嵌套新闻报道的基础上运行多层模型。Mohr 等人（2013）使用 NER 来定位美国国家安全战略文件中的主要地缘政治行为体。Van de Rijt 等人（2013）在 Lydia 文本分析系统中使用 NER 来模拟报纸中的名人更替，Shor 等人（2015）则使用同一系统来研究媒体报道中随时间变化的性别差距。7

- 本部分需要：
  - tidyverse
  - entity
  - tidytext

> 7 有关 NER 在社会科学中应用的更多示例，请参见 Shor 等人（2014）和 Traag 等人（2015）。有关将 NER 用作进一步分析的预处理策略的讨论，请参见 D'Orazio 等人（2014:230–231）。

接下来，我们将首先从总体上介绍 NER 的工作原理，随后演示如何在 R 中进行 NER 标注。

## 命名实体识别的工作原理

请考虑以下文本（改编自 Mack 2019）。经过正确优化的 NER 标注器应当返回这些“命名实体”及其所属的实体标签，如下所示：

> 《星际迷航：皮卡德》于 2020 年 1 月 [日期/时间] 在 CBS [组织] All Access 上首播，派屈克·斯图尔特 [人物] 再次扮演这位高贵领导者的角色，此举是在《星际迷航：下一代》结束 20 多年之后。新剧预告片显示，皮卡德已在地球 [地点] 的一个葡萄园里退休，但感到格格不入，渴望太空旅行。

在这个例子中，有四种实体标注器，分别用于识别人名、组织名称、日期/时间和地点。这些是常见的实体标签，但具体标签会因所使用的 NER 标注器而异。entity 还提供金额和百分比的标注器。斯坦福 NLP 团队的 CoreNLP 库附带更多标签，包括国籍、宗教，甚至死因（Manning 等人，2014）。

NER 算法“学习”识别实体标签的方式各不相同。它们都依赖训练数据。这些训练数据是已由人类（或一组人类）标注好的句子。例如，“人名”标注器的训练数据大致如下：8

8 训练数据格式必须与所使用的软件匹配。对于 OpenNLP 库，每行必须包含一个带注释的句子（Apache，2020）。

```
The CEO of Apple, <START:person> Tim Cook <END>, unveiled the new iPhone. Mr. <START:person> Cook <END> was joined on the stage by Chief Operating Officer, <START:person> Jeff Williams <END>.
```

训练文件需要包含至少 15,000 个以行分隔的带注释句子（Apache，2020）。

因此，训练文档按句子解析，以换行符分隔，名称是手动标注的。随后，模型会遍历预设的上下文变量——即所谓的“特征集”（Apache，2020）。9 部分上下文变量可能包括：该词是否大写？该词是否紧随“先生”、“女士”或“博士”等头衔之后？

9 NER 模型通常具有预设的上下文变量，但我们可以提供自定义特征集。

10 OpenNLP NER 工具为此使用广义迭代梯度法。

该算法利用带标签词与上下文变量之间的共现关系，为每个变量开发一个权重，以指示该变量与某个类别（这里是“是人”或“不是人”）之间关联的强度。任何 NER 模型的输出都是权重——即每个上下文变量的“重要性”。10

训练好的 NER 模型随后可用于预测新的、未标注文本中的实体类别。11 我们将使用的 NER 模型是**预训练**的。因此，不需要带注释的训练数据。OpenNLP NER 模型似乎是在12 对 318 篇 *华尔街日报* 文章上训练而成，这些文章构成了第六次信息理解会议（MUC-6）的一系列 NLP 评估任务的训练集（Nouvel 等人，2016:61）。

11 在 OpenNLP 中，这是通过最大熵（“maxent”）建模完成的。

12 OpenNLP 的训练数据很难确定。我们从 Joern Kottmann 2010 年在 OpenNLP SourceForge 仓库上的一个讨论帖子中找到了 MUC-6 数据。

## R 中的命名实体

我们将用于命名实体识别的软件包是 entity。13 它是 Apache 软件基金会维护的基于 Java 的 OpenNLP 库的 R “封装器”。14 让我们使用 *星际迷航：皮卡德* 段落作为快速示例（输出在旁注中）：

```
para <- "Star Trek: Picard, which debuted in January 2020 on CBS All Access, saw Patrick Stewart reprise his role as the noble leader more than 20 years after Star Trek: Next Generation ended. The trailer for the new show showed Picard retired at a vineyard on Earth, but feeling out of place and longing for space travel."

person_entity(para)
organization_entity(para)
location_entity(para)
date_entity(para)
```

所有实体均已被识别并正确标记。

让我们使用卡内基梅隆大学政治博客语料库（Eisenstein 和 Xing，2010）中的更大示例进行讲解。这六个政治博客的文章于 2008 年收集。三个来源偏向自由派（*Digby*、*ThinkProgress* 和 *Talking Points Memo*），另外三个是保守派媒体（*American Thinker*、*Hot Air* 和 Michelle Malkin 的博客）。

13 如果 entity 无法从 CRAN 下载，请尝试从维护者的 GitHub 安装：trinker/entity。

14 我们的机器上还需要安装 Java。

```
[1] "Patrick Stewart"
[1] "CBS"
[1] "Earth"
[1] "January 2020"
```

我们将使用 100 篇博客文章的随机样本。将其读入 R 时，我们还会将其分配给一个名称较短的对象以节省空间，但这并非必需。让我们来看一篇较短文章的片段，该文章来自 *Hot Air*：15

15 我们未能找到这篇博客文章的原始作者。

```
data("corpus_cmu_blogs100", package = "textmap.corpora")
blogs <- corpus_cmu_blogs100 # rename it so it's tidier
blogs$text[[46]]
```

[1] "约翰·爱德华兹因与丽埃勒的婚外情在这次党代会上遭到民主党人冷落

