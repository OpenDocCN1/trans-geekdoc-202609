

# 数据平衡

我们可以根据数据集中记录的标签值，将其划分为不同的组或类别。例如，新闻类别数据集中的每个类别（如 `sports`、`politics`、`entertainment` 和 `community`）都可能包含多条记录。同样，在讽刺检测数据集中，我们可以将记录分类为 `sarcastic`（讽刺）或 `non-sarcastic`（非讽刺）。通常，不同类别的数量并不相同。学习算法可以处理一定程度的类别分布差异（例如 2:3）；然而，当差异变得极端时（例如 1:99），问题就出现了。我们将具有极度偏斜类别分布的数据集称为**不平衡数据集**。

让我们尝试理解在二分类场景下，学习算法在类别不平衡条件下是如何工作的，此时模型会为每个类别分配一个权重。数据集中拥有大量记录的类别被称为**多数类**，而另一个则是**少数类**。如果处理不当，多数类的大量样本可能会影响模型的预测能力。在极端情况下，模型会通过不给少数类分配任何权重，从而学会完全忽略少数类。我们可以通过一种称为**混淆矩阵**的评估指标来检测分类模型的这种偏斜行为。处理不平衡数据集有多种方法；让我们逐一了解。

## I. 移除低频数据记录

此技术仅适用于数据集包含多个类别，且无需特定类别必须存在即可解决手头问题的情况。例如，服装合身度数据集只有三个类别：`small`、`fit` 和 `large`，它们对于解决尺码推荐问题都是必不可少的。而在新闻类别数据集中，我们有许多可用的类别，如 `sports`、`politics`、`entertainment`、`fashion`、`medicine` 和 `community`。解决新闻类别检测问题并不严格要求某个特定类别必须存在。

应对极端偏斜的一个直接方法是从数据集中移除极低频类别的记录。我们也可以考虑采取另一种途径，即丢弃高频类别的记录以匹配低频类别的比例；然而，这可能会大幅缩减数据集的规模。前一种方法在此处显得更合理，因为它保持了数据量，并有助于模型可靠地进行分类。

在从 HuffPost 提取的新闻类别数据集中，我们进行了初步的**探索性数据分析 (EDA)**。我们发现有几个类别下列出的文章少于 500 篇。为了平衡数据集，我们仅移除了它们，并观察到分类模型的性能有所提升。

```python
import json
from collections import defaultdict

category_count = defaultdict(int)

for record in data:
    category_count[record['category']] += 1

filtered_data = []

for record in data:
    if category_count[record['category']] >= 500:
        filtered_data.append(record)

output_file = open('./News_Category_Dataset.json', 'w', encoding='utf-8')

for record in filtered_data:
    output_file.write(json.dumps(record) + '\n')

output_file.close()
```

## II. 随机采样数据记录

采样是处理不平衡数据集的一种广泛流行且简单的方法。该技术涉及从数据集中的丰富类别中随机采样记录以消除偏斜，这一过程通常称为**随机欠采样**。作为替代方案，我们也可以通过有放回地随机采样来增加低频类别的记录，这被称为**随机过采样**。

在讽刺检测数据集中，我们从 TheOnion 提取了讽刺标题，从 HuffPost 提取了真实新闻标题。统计数据显示，非讽刺新闻标题（约 20 万条）远多于讽刺标题（约 1.1 万条）。为了消除这种偏斜，我们使用了欠采样技术：从非讽刺数据中随机采样了约 1.5 万条标题。重要的是要注意，我们并不总是旨在让类别达到 1:1 的比例；如前所述，轻微的偏斜（如 2:3）可以被学习算法有效处理。

```python
data = deepcopy(sarcastic_data)

random.shuffle(non_sarcastic_data)

for i in range(0, 15000):
    hh = preprocess_headline(non_sarcastic_data[i]['headline'])
    if len(hh.split()) > 1:
        temp = dict()
        temp['is_sarcastic'] = 0
        temp['headline'] = hh
        temp['article_link'] = non_sarcastic_data[i]['link']
```

