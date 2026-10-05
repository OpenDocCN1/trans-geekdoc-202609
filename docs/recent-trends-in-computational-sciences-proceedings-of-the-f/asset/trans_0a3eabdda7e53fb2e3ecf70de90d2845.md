

## 3.2 提出的解决方案

用户可能会花费大量时间在数百部甚至数部动漫中翻找，却无法发现自己感兴趣的内容。我们的目标是填补现有研究的空白，并构建一个根据观众的偏好和需求推荐动漫的系统，从而提供更好的流媒体体验，并增加收入和投入时长。在这项工作中，系统可以通过多种方式实现。我们打算解决的是基于流行度的推荐系统，以及基于 KNN 的协同过滤。

## 3.3 数据集描述

我们使用了两个数据集。第一个是 Anime（动漫），第二个是 Rating（评分）。这两个数据集是从 Kaggle 网站收集的。该数据收集包含了 73,516 名用户对 12,299 部动漫的选择。该集合中的评分是这些选择的汇总。第一个动漫数据集有 12299 行和 7 列。第二个评分数据集有 781376 行和 3 列。每个用户都可能对其进行评分并将其添加到完成列表中。Anime.csv 和 Rating。

下一步是数据预处理，这是一种清洗原始数据并使其适用于分类模型的技术。这将使得数据易于被机器解析，并进一步提高结果的质量。现实世界的数据极易出现不一致、噪声或缺失数据。如果将数据挖掘算法应用于此类数据集，它们将无法获得高质量的结果，因为它们无法有效识别模式。因此，数据预处理是在应用任何算法之前提高数据质量的关键步骤。

## 3.4 算法

### 3.4.1 基于流行度的

这是一种推荐系统，根据流行度或目前客户中最热门、最受欢迎的内容进行运行，并立即向他们推广 [6]。例如，如果一个产品被大多数人经常购买，例如，系统将学习到它是最流行的，并将其推广给每个新加入的用户，从而增加新用户也购买它的可能性。

### 3.4.2 基于协同的过滤

可能有很多人对用户想要的产品进行评分。这些人的评分与用户之间的这种可比的趋势是协同过滤的基础 [5]。协同过滤的基础是根据具有相似兴趣的人的品味进行产品推荐。

### 3.4.3 用于协同过滤的 K 近邻算法

KNN 是一种可以解决分类和回归问题的算法 [14]。根据提供的距离度量（如余弦相似度、欧几里得距离、Jaccard 相似度、闵owski 距离或自定义距离度量），K 近邻确定与单个实例最相似的 k 个对象。

在我们的模型中，我们采用了余弦相似度来发现 K 近邻 [19]。

## 4 结果与讨论

本节总结了获取相似动漫和评分的策略结果。

## 4.1 流行度算法

图 2 显示了根据用户给出的排名前 15 的热门节目。在下方的图中，Y 轴代表不同的动漫，X 轴上的对应流行度分从 0-10。

根据我们的推荐系统，我们根据人们评分获得了最热门的 15 部动漫。绘制了表 2，包含名称（Name）、平均评分（Average Ratings）和基于 15 部最热门动漫的得分（Score）。

表 2. 十五最热门的节目。

| 名称 (Name) | 平均评分 (Average Ratings) | 得分 (Score) |
|---|---|---|
| Fullmetal Alchemist Brotherhood | 9.26 | 9.1292697 |
| SteinsGate | 9.17 | 9.62223918 |
| Clannad After Story | 9.06 | 8.89006859 |
| Code Geass Hangaku no Lelouch R | 8.98 | 8.843128568 |
| Hunter x Hunter 2011 | 9.13 | 8.626378505 |
| Sen to Chihiro no Kamikushi | 8.93 | 8.76503438 |
| Code Geass Hangaku no Lelouch | 8.83 | 8.714967667 |
| Shigatumi kimi no Uso | 8.92 | 8.663781234 |
| Death Note | 8.71 | 8.636635884 |
| One Punch Man | 8.82 | 8.634727359 |

### 4.1.1 KNN

我们使用 KNN 得到了以下结果。表 3 表示了基于给定的动漫 i（即 Anime 0）推荐的前 5 部动漫（相似类型/评分）。这对于根据特定品味对动漫进行分类是有效的。

表 3. 基于 Anime 0 推荐的前 5 部动漫。

| Anime0 | Anime1 | Anime2 | Anime3 | Anime4 | Anime5 |
|---|---|---|---|---|---|---|
| Choisui | Princess Tutu Recaps | Paizuri Cheerld vs Sakunyu Oendan | 09 Recgyord | Pere-Pero Teacher | Please Me | Osaru no Sankiuchi Boukuse n Xmen |
| Gekigre r 3 Movie | Ookiku Furutta but spell | | Gundam Build Fighters Try Idol Wars Jetsu TV | Avengers Confident at Black Widow to Punisher | Koishima Miyu OVA Onake Ashita to | |

## 4.2 基于协同的过滤

可能有很多人对用户想要的产品进行评分。这些人的评分与用户之间的这种可比的趋势是协同过滤的基础 [5]。协同过滤的基础是根据具有相似兴趣的人的品味进行产品推荐。

图 2 显示了根据用户给出的排名前 15 的热门节目。在下方的图中，Y 轴代表不同的动漫，X 轴上的对应流行度分从 0-10。

根据我们的推荐系统，我们根据人们评分获得了最热门的 15 部动漫。绘制了表 2，包含名称（Name）、平均评分（Average Ratings）和基于 15 部最热门动漫的得分（Score）。

![](img/a3f8e852e0ee65e28c95ad0821783b1.png)

## 4.3 KNN

KNN 是一种可以解决分类和回归问题的算法 [14]。根据提供的距离度量（如余弦相似度、欧几里得距离、Jaccard 相似度、闵owski 距离或自定义距离度量），K 近邻确定与单个实例最相似的 k 个对象。

在我们的模型中，我们采用了余弦相似度来发现 K 近邻 [19]。

## 5 结论与未来工作

动漫是一个巨大的娱乐类别，包含各种类型和主题，以吸引大量的观众。动漫行业拥有 430 家公司。为了解决这个问题，我们将个性化推荐变成了一项艰巨的任务。经过深入思考，通过我们的算法对客户的各种兴趣得到了结果。基于识别、内容和记忆的协同过滤技术都已使用。在线公司现在必须通过提供定制的建议、内容和服务来帮助客户。混合模型在考虑用户的浏览记录时产生。实时系统需要极高的精度。某种机器学习算法可以帮助这些系统。我们希望检查其他算法，看看它们是否有助于进一步提高精度。

# REFERENCES

+   [1] Tiwari, Anand Shanker, Ajay Kumar, and Asim Gopal Rahman. “Book Recommendation System Based on Combining Features of Content Based Filtering, Collaborative Filtering and Association Rule Mining.” In 2014 IEEE International Advanced Computing Conference (IACC), pp. 500–503. IEEE,2014.
[2] Saadati, Mojdeh, Seyed Shihab, and Mohammed Shiqur Rahman. “Movie Recommender Systems: Implementation and Performance Evaluation.” arXiv preprint:1909.12749 (2019).

