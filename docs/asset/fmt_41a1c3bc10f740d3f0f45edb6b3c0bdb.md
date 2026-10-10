
## BaggingClassifier

在 sklearn 中，`BaggingClassifier` 类用于实现分类的 Bagging 集成模型。表 6.1 列出了 `BaggingClassifier` 类的关键参数：

| 参数 | 解释 |
| --- | --- |
| estimator | Bagging Classifier 类使用的估计器。默认情况下，估计器是决策树分类（DecisionTreeClassifier）。此参数需要作为估计器类的一个实例提供。 |
| n_estimators | 要创建的估计器实例的数量。这意味着 Bagging Classifier 将使用估计器类创建数量与 n_estimators 值相等的模型，并从提供的数据集中创建 n_estimators 数量的数据集。在 Scikit-Learn 的某些版本中，该参数可能以 `base_estimator` 的形式存在。 |
| bootstrap | 这是一个布尔值参数，取值为 True 或 False。如果 `bootstrap` 参数的值设置为 True，则进行有放回抽样。如果 `bootstrap` 参数的值设置为 False，则进行不放回抽样。 |
| max_samples | 为每个估计器实例需要提供从原始数据集中提取的最大数据点数。 |
| oob_score | 这是一个布尔值参数，取值为 True 或 False。该参数仅在 `bootstrap` 参数设置为 True 时有效。当其设置为 True 时，将使用袋外（out-of-bag）数据点来检查泛化误差。 |

表 6.1：BaggingClassifier 的参数

在下面的代码中，我们看到如何使用 Scikit-Learn 包中的 BaggingClassifier：

```python
from sklearn.ensemble import BaggingClassifier
```

```python
from sklearn.tree import DecisionTreeClassifier
```

```python
baggingClf = BaggingClassifier(estimator=DecisionTreeClassifier(), n_estimators = 1000, bootstrap=True, max_samples=500, oob_score=True)
```

## StackingClassifier

在 sklearn.ensemble 中，`StackingClassifier` 类用于实现分类的 Stacking 集成模型。StackingClassifier 类有两个关键参数。第一个关键参数是 `estimators`，它接收一个不同分类器的列表用于构建基模型。第二个关键参数是 `final_estimator`，它接收用于构建元模型的类。

`StackingClassifier` 的另一个重要参数是 passthrough。它接收一个布尔值（即，我们将此参数设置为 True 或 False）。当 `passthrough` 设置为 False 时，`StackingClassifier` 使用基模型的预测结果作为构建元模型的输入。当 `passthrough` 设置为 True 时，`StackingClassifier` 将使用基模型的预测结果和原始数据集来构建元模型，如下代码所示：

```python
from sklearn.ensemble import StackingClassifier
...
```

```python
from sklearn.naive_bayes import MultinomialNB
from sklearn.neighbors import KNeighborsClassifier
from sklearn.tree import DecisionTreeClassifier
from sklearn.linear_model import LogisticRegression
```

```python
...
nbCls = MultinomialNB()
knnCls = KNeighborsClassifier()
dtCls = DecisionTreeClassifier()
lrCls = LogisticRegression()
```

```python
...
stackingClf = StackingClassifier(estimators=[('nb', nbCls), ('knn', knnCls), ('dt', dtCls)], final_estimator=lrCls)
...
```

## 使用 Bagging 算法构建语音情感分析模型

情感分析在许多行业中被广泛使用。提供在线服务的公司使用情感分析来分析客户反馈。在临床调查中，它用于预测患者的状态。人力资源部门将其用于离职预测等应用。在保险行业，情感分析有更多其他用例。

情感分析通常在文本数据上进行。这是自然语言处理（NLP）的一个领域。该领域通过分析不同的单词来确定情感。我们将对语音进行情感分析，在语音中，音高、语调、语速、音量等方面被分析以确定表达的情感。

使用机器学习进行情感分析的领域仍处于起步阶段，一些可靠的数据集用于构建模型。我们可以通过提供更高质量的数据来改进模型。

## 关于数据集

正如本章所述，用于情感分析的数据集从 Kaggle 获取。数据集的第一个来源是多伦多大学（University of Toronto），第二个来源是里森音视频数据库（Ryerson Audio-Visual Database）。

### TESS 数据集

TESS 数据集包含 2880 个文件，每个文件都包含一段录音。200 个目标词由两位女演员在“Say the word ______”的短语中读出，并录制了七种不同的情感（愤怒、厌恶、恐惧、快乐、惊讶、悲伤和中性）。两位女演员的英语均为母语，拥有大学学历，并接受过音乐训练。听学测试显示两者的阈值都在正常范围内。

- 1 https://borealisdata.com/dataset.xhtml?persistentid=do:10.5683/SP2/E82MF
- 2 https://zenodo.org/record/1188976#Y_RMYuxBzA1

### Ravdess 数据集

Ravdess 数据集包含 2880 个文件，每个文件都包含一段录音。200 个目标词由两位女演员在“Say the word ______”的短语中读出，并录制了七种不同的情感（愤怒、厌恶、恐惧、快乐、惊讶、悲伤和中性）。两位女演员的英语均为母语，拥有大学学历，并接受过音乐训练。听学测试显示两者的阈值都在正常范围内。

# 掌握机器学习中的分类算法

一旦加载了数据集，就可以使用以下代码播放音频文件：

```python
import IPython.display as ipd
sampleAudio1 = ravdessFiles[0]
ipd.Audio(sampleAudio1)
<IPython.lib.display.Audio object>
sampleAudio2 = tessFiles[100]
ipd.Audio(sampleAudio2)
<IPython.lib.display.Audio object>
```

运行此代码时将出现一个音频播放器，如图 6.5 所示。点击音频片段上的开始按钮后，音频片段将如接下来所示播放：

![](img/11af2c4c7dddfed06ed008516c0c6dfb_193_0.png)

> 图 6.5：由 IPython 库提供的音频播放器

从数据集中，我们需要首先建立数据分布。数据分布是构建良好模型的关键方面。我们知道数据包含 8 种不同情绪的音频片段。我们需要检查数据集中每种情绪的音频文件数量是相似还是不同。如果每种情绪的音频文件数量相似，我们就说数据集是平衡的。否则，该数据集被称为不平衡的。

如果数据集是平衡的，模型将对每种情绪赋予几乎相等的权重。如果不是，模型可能会偏向音频片段较多的情绪。拥有平衡的集合有助于构建良好的分类模型。

我们首先确定每种情绪有多少个音频片段。在这里，音频片段中表达的情绪是我们的标签。我们将告诉机器特定的音频片段表达了特定的情绪。根据提供给机器的这些知识，预计机器将学习如何确定提供给机器的新音频片段所表达的情绪。

每个音频片段相关的情绪都编码在音频片段的文件名中。以下代码从文件名中提取与情绪相关的文本并将其与音频片段关联。请注意，TESS 文件和 Ravdess 文件的命名规范是不同的。此外，注意变量 `tessFiles` 和 `ravdessFiles` 所有音频片段文件的完整路径：

```python
emotionsInTessFiles = [fileName.split("//
```

我们现在知道 TESS 和 Ravdess 文件中可用的情绪：

```python
print('Audio Clips of Emotions available in Tess Files:',
set(emotionsInTessFiles))
```

```python
print('Audio Clips of Emotions available in Ravdess Files:',
set(emotionsInRavdessFiles))
```

Tess 文件中可用的情绪片段：{'disgust', 'neutral', 'fear', 'angry', 'sad', 'happy', 'surprised'}

Ravdess 文件中可用的情绪片段：{'disgust', 'neutral', 'fear', 'angry', 'sad', 'happy', 'surprised'}

注意，我们没有冷静（calm）这种情绪的样本。我们无法从使用此数据集构建的模型中确定“冷静”这种情绪。

接下来，让我们统计两个数据集中每种情绪有多少音频片段：

```python
import pandas as pd
```

```python
print('Number of Audio Clips available for each Emotion in the Tess Files')
dfessEmotions = pd.DataFrame(emotionsInTessFiles, columns = ['Emotion'])
dTessCount = dfTessEmotions.value_counts().reset_index(name = 'count')
```

```python
dfTessCount
```

Tess 文件中每种情绪的音频片段数量

| Emotion | count |
|---|---|---|
| 0 | disgust | 391 |
| 1 | surprised | 387 |
| 2 | happy | 383 |
| 3 | angry | 382 |
| 4 | fear | 379 |
| 5 | sad | 379 |
| 6 | neutral | 378 |

```python
print('Number of Audio Clips available for each Emotion in the Rav Files')
dRavdessEmotions = pd.DataFrame(emotionsInRavdessFiles, columns = ['Emotion'])
dRavdessCount = dRavdessEmotions.value_counts().reset_index(name = 'count')
```

Ravdess 文件中每种情绪的音频片段数量

| Emotion | count |
|---|---|---|
| 0 | sad | 183 |
| 1 | fear | 182 |
| 2 | surprised | 182 |
| 3 | disgust | 180 |
| 4 | angry | 179 |
| 5 | happy | 174 |
| 6 | neutral | 88 |

```python
print('Number of Audio Clips available for each Emotion in both the Tess and Rav Files combined together')
dfCombined = dfTessEmotions.append(dRavdessEmotions)
dfCombinedCount = dfCombined.value_counts().reset_index(name = 'count')
```

# dfCombinedCount

Tess 和 Rav 文件 文件合并后每种情绪的音频片段数量

| Emotion | count |
|---|---|---|
| 0 | disgust | 571 |
| 1 | surprised | 569 |
| 2 | sad | 562 |
| 3 | angry | 561 |
| 4 | fear | 561 |
| 5 | happy | 557 |
| 6 | neutral | 466 |

当我们通过合并 TESS 和 Ravdess 数据集构建模型时，让我们看看合并集中不同情绪的音频片段分布情况：

```python
from matplotlib import pyplot as plt
import seaborn as sb
sb.barplot(x = dfCombinedCount['Emotion'], y = dfCombinedCount['count'])
plt.show()
```

![](img/11af2c4c7dddfed06ed008516c0c6dfb_196_0.png)

**图 6.6：** 合并集的绪分布

# 音频信号可视化

我们看到除了中性（neutral）外，所有情绪的文件数量几乎相同。我们可以认为该数据集是平衡的。现在我们将可视化音频文件中的音频信号。为了做到这一点，我们将使用 librosa 库。在大多数情况下，可能需要安装 librosa 库。使用以下代码在你的机器上安装 librosa。要安装 librosa 库，你需要至少 0.53 版本的 numba（这是撰写本章时的情况）。检查你的机器上是否安装了适当版本的 numba。以下代码将在你的机器上安装 librosa：

```bash
!pip install numba
!pip install librosa
```
