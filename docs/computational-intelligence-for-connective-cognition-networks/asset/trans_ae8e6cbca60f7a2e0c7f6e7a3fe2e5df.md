

## 动机

大多数研究人员专注于分析新闻文章的标题以创建假新闻模型，例如 [[66](#ch18.xhtml#r269)–[68](#ch18.xhtml#r271)]。一些用于构建假新闻检测模型的数据集（如 LIAR 数据集 [[69](#ch18.xhtml#r272)]）在数据集中不同时包含新闻文章的标题和内容。该数据集仅包含从文章标题和内容中提取的声明。我们认为新闻内容可以为假新闻检测提供重要信息。因此，在本 RQ 中，我们致力于分析标题和内容对检测假新闻的重要性。本 RQ 的结果可以帮助我们了解新闻的哪一部分在假新闻检测中更为重要。

## 方法

为回答此 RQ，我们构建了 `FNDetector` 模型的三个变体：`FNDetector (title)`、`FNDetector (content)` 和 `FNDetector (title+content)`。`FNDetector (title)` 模型仅使用新闻文章的标题进行训练。`FNDetector (content)` 使用新闻文章的内容进行训练。`FNDetector (title+content)` 同时使用新闻文章的标题和内容进行训练，即本工作提出的原始 `FNDetector` 模型。我们使用 `RF` 和 `LSTM` 两种分类器训练所有这些变体，从而创建了总共六个 `FNDetector` 模型变体。

## 结果

[表 8.13](#ch18.xhtml#t25)、[8.14](#ch18.xhtml#t26) 和 [8.15](#ch18.xhtml#t27) 展示了使用 `RF` 和 `LSTM` 分类器的本 RQ 结果。[图 8.12](#ch18.xhtml#f56) 和 [8.13](#ch18.xhtml#f57) 分别展示了 `FNDetector[RF]` 和 `FNDetector[LSTM]` 模型不同变体之间的性能对比。[表 8.13](#ch18.xhtml#t25) 显示，使用 `FNDetector[RF] (title)` 模型的准确率和 F 值分别为 70.6% 和 72.7%。`FNDetector[LSTM] (title)` 的准确率和 F 值分别为 74.5% 和 76.4%。我们从 [表 8.16](#ch18.xhtml#t28) 观察到，与使用“标题”训练模型相比，使用新闻文章的“内容”时 `FNDetector[RF]` 模型的性能有所提升。与 `FNDetector[RF] (title)` 模型相比，使用 `FNDetector[RF] (content)` 的准确率提升了 11.8%，F 值提升了 10.3%。对于 `LSTM` 分类�器，我们观察到当使用新闻文章的“内容”训练分类器时，准确率和 F 值均有所下降（请参阅 [表 8.17](#ch18.xhtml#t29)）。

![Figure 8.12 Comparison between FNDetector models in random forest classifier with title, content and title+content. T: Title, C: Content.](html/images/9781032942346_C008_012.jpg)

**图 8.12** 随机森林分类器中 FNDetector 模型在标题、内容和标题+内容下的对比。T：标题，C：内容。[⏎](#ch18.xhtml#f56b)

![Figure 8.13 Comparison between FNDetector models in LSTM classifier with title, content and title+content. T: Title, C: Content.](html/images/9781032942346_C008_013.jpg)

**图 8.13** LSTM 分类器中 FNDetector 模型在标题、内容和标题+内容下的对比。T：标题，C：内容。[⏎](#ch18.xhtml#f57b)

**表 8.13** FNDetector 模型使用从新闻文章标题提取的特征的性能[⏎](#ch18.xhtml#t25b)

| 方法 | 准确率 | 精确率 | 召回率 | F 值 |
| --- | --- | --- | --- | --- |
| FNDetector[RF] (title) | 70.6% | 69.0% | 76.9% | 72.7% |
| FNDetector[LSTM] (title) | 74.5% | 75.0% | 77.8% | 76.4% |

**表 8.14** FNDetector 模型使用从新闻文章内容提取的特征的性能[⏎](#ch18.xhtml#t26b)

| 方法 | 准确率 | 精确率 | 召回率 | F 值 |
| --- | --- | --- | --- | --- |
| FNDetector[RF] (content) | 82.4% | 91.7% | 75.9% | 83.0% |
| FNDetector[LSTM] (content) | 58.8% | 87.5% | 25.9% | 40.0% |

**表 8.15** FNDetector 模型使用从文章标题和内容同时提取的特征的性能[⏎](#ch18.xhtml#t27b)

| 方法 | 准确率 | 精确率 | 召回率 | F 值 |
| --- | --- | --- | --- | --- |
| FNDetector[RF] (title + content) | 88.2% | 85.2% | 92.0% | 88.5% |
| FNDetector[LSTM] (title + content) | 78.4% | 75.0% | 88.9% | 81.4% |

**表 8.16** FNDetector[RF] (title+content) 的改进[⏎](#ch18.xhtml#t28b)

| | 准确率提升 | F 值提升 |
| --- | --- | --- |
| FNDetector[RF] (title) | 17.6% | 15.8% |
| FNDetector[RF] (content) | 5.8% | 5.5% |

**表 8.17** FNDetector[LSTM] (title+content) 的改进[⏎](#ch18.xhtml#t29b)

| | 准确率提升 | F 值提升 |
| --- | --- | --- |
| FNDetector[LSTM] (title) | 3.9% | 5.0% |
| FNDetector[LSTM] (content) | 19.6% | 41.4% |

我们注意到，当同时使用新闻文章的标题和内容训练模型时，模型性能得到增强（请参阅 [表 8.15](#ch18.xhtml#t27)、[图 8.12](#ch18.xhtml#f56) 和 [8.13](#ch18.xhtml#f57)）。这也是本工作提出的原始 `FNDetector` 模型。[图 8.12](#ch18.xhtml#f56) 和 [8.13](#ch18.xhtml#f57) 分别展示了 `FNDetector[RF]` 和 `FNDetector[LSTM]` 模型三个变体性能的对比。我们注意到 `FNDetector[RF]` 和 `FNDetector[LSTM]` 模型的性能均有提升。使用 `FNDetector[RF] (title + content)`，与 `FNDetector[RF] (title)` 相比准确率提升了 17.6%，与 `FNDetector[RF] (content)` 相比提升了 5.8%。类似地，使用 `FNDetector[LSTM] (title+content)`，与 `FNDetector[LSTM] (title)` 相比准确率提升了 3.93%，与 `FNDetector[LSTM] (content)` 相比提升了 19.63%。这些改进也在 [表 8.16](#ch18.xhtml#t28) 和 [8.17](#ch18.xhtml#t29) 中展示。结果表明，新闻文章的标题和内容在假新闻检测中都很重要。对于 `FNDetector[RF]` 和 `FNDetector[LSTM]`，我们观察到当同时使用标题和内容训练模型时，预测准确率显著提高。

## RQ 4：在 FNDetector 模型中，哪些特征对于检测假新闻更为重要？

### 动机

我们使用 32 个特征来训练 `FNDetector` 模型。这些特征属于不同领域，具有不同类型，即基于语言的特征（语法和词汇特征）、基于情感的特征、命名实体识别特征和文本特征。`FNDetector` 模型在准确率和 F 值上均显著优于基线分类器。通过分析逐步增加特征类别时 `FNDetector` 模型的性能，可以深入了解不同特征类别的重要性。

### 方法

为回答此 RQ，我们进行了两类实验。首先，我们创建了四个 `FNDetector` 模型变体（针对 `RF` 和 `LSTM` 两种分类器），并逐步增加特征以观察每个特征类别对 `FNDetector` 模型性能的影响。我们创建了以下变体：

*   `FNDetector[A]^(F[S])`：使用基于情感的特征训练的 `FNDetector` 模型。
*   `FNDetector[A]^(F[S] + F[L])`：使用基于情感和基于语言的特征训练的 `FNDetector` 模型。
*   `FNDetector[A]^(F[S] + F[L] + F[N])`：使用基于情感、基于语言和基于 NER 的特征训练的 `FNDetector` 模型。
*   `FNDetector[A]^(F[S] + F[L] + F[N] + F[T])`：使用所有 32 个提取特征训练的 `FNDetector` 模型。

