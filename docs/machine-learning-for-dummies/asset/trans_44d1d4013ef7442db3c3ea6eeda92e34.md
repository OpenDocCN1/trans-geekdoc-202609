

如果你的数据包含关于隐藏原因或主题的提示和线索，SVD 可以将它们整合起来，为你提供恰当的答案和洞察。当你的数据由像下面列表中那样有趣的信息片段组成时，这一点尤其正确：

*   **文档中的文本暗示了想法和有意义的类别：** 正如你可以通过阅读博客和新闻组来决定讨论话题一样，SVD 也可以帮助你推断文档组的有意义分类，或每个文档中正在撰写的具体主题。

*   **特定电影或书籍的评论暗示了你的个人偏好和更大的产品类别：** 如果你在评分网站上说你喜欢原版《星际迷航》系列合集，算法可以轻松确定你在其他电影、消费品甚至人格类型方面喜欢什么。

基于 SVD 的一种方法示例是潜在语义索引（LSI），它已被成功用于根据这样一个理念来关联文档和单词：单词虽然不同，但在相似的上下文中放置时往往具有相同的含义。这种分析不仅暗示同义词，还暗示更高层次的分组概念。例如，对一些体育新闻样本进行 LSI 分析可能会仅根据团队名称在相似文章中的共现来对大联盟棒球队进行分组，而无需任何关于什么是棒球队或大联盟的先前知识。

数据缩减的其他有趣应用是关于你可能喜欢购买或了解更多信息的事物的推荐系统。你很可能有很多机会看到推荐系统在运行。在大多数电子商务网站上，登录后，访问一些产品页面，并对产品进行评分或将产品放入电子购物车后，你会看到基于其他客户之前经验的其他购买机会。（如前所述，这种方法称为*协作过滤*。）SVD 可以以更强大的方式实现协作过滤，不仅依赖于单个产品的信息，还依赖于产品在集合中的更广泛信息。例如，协作过滤不仅可以确定你喜欢电影《夺宝奇兵》，还可以确定你通常喜欢所有动作和冒险电影。

你可以基于简单的手段或频率来实现协作推荐，这些手段或频率是根据其他客户购买的物品集合或评分计算的。这种方法即使在供应商很少销售或对用户来说相当新的产品的情况下，也能帮助你可靠地生成推荐。

## 观察 SVD 的实际应用

本章前面的“[执行协作过滤](#c19.xhtml#c19-sec-0009)”部分展示了一种从 MovieLens 数据集进行电影推荐的技术。本部分展示了如何使用 SVD 执行相同的任务。你可以基于简单的手段或频率来实现协作推荐，这些手段或频率是根据其他客户购买的物品集合或评分计算的。这种方法即使在供应商很少销售或对用户来说相当新的产品的情况下，也能帮助你可靠地生成推荐。对于此示例，你使用 MovieLens 网站创建的一个著名数据库，该数据库收集了用户对他们喜欢或不喜欢的电影的评分。此示例依赖于你之前创建的相同 MovieLens `dataframe`，并首先使用以下代码在其上构建电影索引：

```
ratings_mtx_df = MovieLens.pivot_table(values='rating', index='user_id', columns='title', fill_value=0)movie_index = ratings_mtx_df.columns
```

`pandas` 将帮助创建一个数据表，行中包含用户的信息，列中包含电影标题。电影索引将跟踪每一列代表哪部电影。

```
from sklearn.decomposition import TruncatedSVDrecom = TruncatedSVD(n_components=15, random:state=101)R = recom.fit_transform(ratings_mtx_df.values.T)
```

`TruncatedSVD` 类将数据表减少到十个组件。与第 11 章“[解释 SVD 的基础知识](#c11.xhtml#c11-sec-0010)”部分中使用的 SciPy 的 `linalg.svd` 相比，这个类提供了一个更具可扩展性的算法。`TruncatedSVD` 计算由 `n_components` 参数决定的精确形状的结果矩阵（不会计算完整的结果矩阵），从而实现更快的输出和更少的内存使用。

通过计算 `Vh` 矩阵，你可以将不同但相似用户的评分（每个用户的分数由行表示）减少到压缩维度，这些维度重建了一般的品味和偏好。请注意，因为你对 `Vh` 矩阵（列/电影缩减）感兴趣，但算法只为你提供 `U` 矩阵（基于行的分解），所以你需要输入数据表的转置（通过转置，列变为行，你获得 `TruncatedSVD` 输出，即 `Vh` 矩阵）。你现在查找特定电影：

```
movie = 'Star Wars: Episode V \- The Empire Strikes Back (1980)'movie_idx = list(movie_index).index(movie)print("movie index: %i" %movie_idx)print(R[movie_idx])
```

输出指出了《星际大战》一集的索引及其 SVD 坐标：

```
movie index: 3154[184.72254552 -17.77612872 47.33450866 51.4664494 47.92058216 17.65033116 14.3574635 -12.82219207 17.51347857 5.46888807 7.5430805 -0.57117869 -30.74032355 2.4088565 -22.50368497]
```

使用电影标签，你可以找出电影所在的列（在此示例中为列索引 3154）并打印十个组件的值。此序列提供了电影配置文件。你现在尝试获取所有与目标电影评分相似且与其高度相关的电影。一个好的策略是计算所有电影的相关矩阵，获取与你的电影相关的切片，并使用索引找出其中哪些电影标题最相关（其特征是高正相关，例如至少 0.985），如下面的代码所示：

```
import numpy as npcorrelation_matrix = np.corrcoef(R)P = correlation_matrix[movie_idx]print(list(movie_index[(P &gt; 0.985) & (P &lt; 1.0)]))
```

该代码将返回与你的电影最相似的电影名称；它们旨在基于对该电影的偏好提供建议。你的输出可能与所示列表略有不同。（尝试 P 的不同值，例如 0.9，看看你能得到多少部电影。）

```
 ['Star Wars: Episode IV - A New Hope (1977)','Star Wars: Episode V - The Empire Strikes Back (1980)','Star Wars: Episode VI - Return of the Jedi (1983)']
```

《星际大战》粉丝会喜欢《星际大战 IV》和《VI》（当然）。

![Remember](images/remember.png)SVD 将始终找到关联数据中行或列的最佳方式，发现你以前从未想象过的复杂交互或关系。你不需要预先想象任何东西；它完全是一种数据驱动的方法。

Part 6

# The Part of Tens

IN THIS PART …

Get tips for learning from data better

Improve your use of models

Work with data in an ethical manner

Discover packages and libraries you need to add to your toolbox

Chapter 20

# Ten Ways to Improve Your Machine Learning Models

IN THIS CHAPTER

![Bullet](images/check.png)**Creating better models**

![Bullet](images/check.png)**Optimizing the problem environment**

![Bullet](images/check.png)**Developing improved solutions**

![Bullet](images/check.png)**Working with features**

![Bullet](images/check.png)**Offering algorithms more chances to learn**

