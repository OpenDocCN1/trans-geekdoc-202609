

这种效果在只能通过使用来评判的产品（例如电影）上更为显著，而在仅凭看图片或阅读描述就能轻易评判的产品（例如智能手机）上则较弱。

此外，推荐系统的有效性还会因用户评论而得到补充。这类推荐系统使用产品收到的用户评论，这就是为什么你在购买产品后常常会收到多条邀请，要求你对产品进行评价。评论中的星级评分和书面部分使用的术语有助于改变推荐系统的行为，从而更好地诱导他人进行购买。

推荐系统最初是作为处理信息过载的一种手段而出现的。施乐帕罗奥尔托研究中心于 1992 年构建了第一个推荐系统。该系统名为 Tapestry，用于处理研究中心研究人员收到的日益增多的电子邮件。协同过滤的概念由此诞生（通过利用偏好相似性来从用户那里学习），随后 GroupLens 项目将其扩展到新闻选择和电影推荐（即 MovieLens 项目，你在本章中使用的数据来自该项目）。

当亚马逊等电子商务领域的巨头开始采用推荐系统时，这一理念进入主流并在电子商务领域广泛传播。Netflix 则通过将推荐系统作为业务工具进行推广，并赞助一项改进其推荐系统的竞赛（`https://en.wikipedia.org/wiki/Netflix_Prize`），该竞赛涉及多个团队并持续了相当长的时间。结果是一种创新的推荐技术，它使用 SVD 和受限玻尔兹曼机。

然而，推荐系统并不仅限于推广产品。自 2002 年以来，一种新型的互联网服务应运而生：例如 Friendster、Myspace、Facebook 和 LinkedIn 等社交网络。这些服务促进用户之间的链接交换，并分享帖子、图片和视频等信息。此外，谷歌等搜索引擎积累了用户响应信息，以提供更个性化的服务，并了解如何更好地匹配用户在响应查询时的需求（`https://en.wikipedia.org/wiki/RankBrain`）。

推荐在引导人们日常生活方面已变得如此普遍，以至于专家们现在担心其对我们独立决策能力和自由感知世界的影响。你可以在 `https://en.wikipedia.org/wiki/Filter_bubble` 的文章中阅读关于这一担忧的内容。推荐系统的历史是机器努力了解我们的思想和心灵，使我们的生活更加便捷，并促进其创建者业务发展的历史。

## 下载评分数据

获取高质量的评分数据可能很困难。本章后面，你将使用 MovieLens 数据集来了解 SVD 如何帮助你创建电影推荐。不过，你还可以使用其他数据库。以下部分将介绍 MovieLens 数据集以及 MSWeb 中包含的数据日志——这两者在尝试推荐系统时都效果不错。

### 筛选 MovieLens 数据集

MovieLens 网站（`https://movielens.org/`）旨在帮助你找到可能喜欢的电影。毕竟，在数以百万计的电影中，找到新的且有趣的电影可能需要你不愿花费的时间。该系统的工作方式是要求你输入你已知电影的评分。然后，MovieLens 网站会根据你的评分为你提供推荐。简而言之，你的评分教会算法寻找什么，然后网站将此算法应用于整个数据集。

你可以在 `http://files.grouplens.org/datasets/movielens/ml-1m.zip` 获取本节使用的 MovieLens 数据集。这个网站有趣的地方在于，你可以根据想要如何与数据集交互来下载全部或部分数据集。你可以找到以下大小的下载：

*   1,000 名用户对 1,700 部电影的 100,000 条评分
*   6,000 名用户对 4,000 部电影的 100 万条评分
*   72,000 名用户对 10,000 部电影的 1,000 万条评分和 100,000 个标签应用
*   138,000 名用户对 27,000 部电影的 2,000 万条评分和 465,000 个标签应用
*   MovieLens 的最新数据集，提供小型或完整版本（撰写本文时，完整版本包含 230,000 名用户对 27,000 部电影的 21,000,000 条评分和 470,000 个标签应用；其规模还在增加。）

这个数据集为你提供了一个机会，使用监督和无监督技术处理用户生成的数据。大型数据集带来了只有大数据才能解决的特殊挑战。你可以在 [第 8 章](#c08.xhtml) 中找到一些关于使用监督和无监督技术的入门信息。第一步是获取数据集，并使用以下代码将其放置在正确的文件夹中：

```
import urllib.request
import os.path
import zipfile
DirName = "ml-1m"
Filename = "ml-1m.zip"
if not os.path.exists(DirName):
    url = "http://files.grouplens.org/datasets/" \
          "movielens/"
    # This step may take a few minutes to download
    # the data.
    urllib.request.urlretrieve(url + Filename, Filename)
    # This step will extract the data for you and
    # place it in the correct directory.
    with zipfile.ZipFile(Filename, 'r') as zip_ref:
        zip_ref.extractall()
```

如果你查看 `ml-1m` 文件夹，你会看到三个 `.dat` 文件：`movies.dat`、`ratings.dat` 和 `users.dat`。要将 MovieLens 数据集作为一个整体来处理，你必须将这三个文件合并为一个 pandas `DataFrame`，如下所示：

```
import pandas as pd
from scipy.sparse import csr_matrix
users = pd.read_table('ml-1m/users.dat', sep='::', header=None, names=['user_id', 'gender', 'age', 'occupation', 'zip'], engine='python')
ratings = pd.read_table('ml-1m/ratings.dat', sep='::', header=None, names=['user_id', 'movie_id', 'rating', 'timestamp'], engine='python')
movies = pd.read_table('ml-1m/movies.dat', sep='::', header=None, names=['movie_id', 'title', 'genres'], engine='python')
MovieLens = pd.merge(pd.merge(ratings, users), movies)
```

要查看生成的评论数量，你只需使用 `print(MovieLens)`。[图 19-1](#c19.xhtml#c19-fig-0001) 显示了你可以期望看到的内容。

![FIGURE 19-1: The output shows 1,000,209 cases and 10 features.](images/9781119724018-fg1901.png)

[FIGURE 19-1:](#c19.xhtml#rc19-fig-0001) The output shows 1,000,209 cases and 10 features.

现在你有了一个可用的单一数据集，你可能想确定人们是如何投票的。在这种情况下，你对评分进行计数，如下所示：

```
MovieLens.set_index(["title", "rating"]).count(level="rating")["user_id"]
```

输出显示评分分布不均匀；人们更有可能给出 3、4 或 5 的评分：

```
rating1 561742 1075573 2611974 3489715 226310
```

评分数据中，各级别评分数量的差异经常发生：评分数据往往偏向正面数据，因为用户倾向于购买或观看他们认为会喜欢的东西。失望主要会导致负面评分，因为期望未得到满足。你也可以使用以下代码来报告每个用户平均评分了多少部电影，以及每部电影被多少用户评分：

```
IndUsers = MovieLens.set_index(["movie_id", "user_id"]).count(level="user_id")["title"]
print("Average movie reviews per user: ", IndUsers.mean())
IndMovies = MovieLens.set_index(["user_id", "title"]).count(level="title")["movie_id"]
print("\nNumber of Reviews Per Movie\n")
print(IndMovies)
```

