
然而，我们可以将矩阵 `R` 分解为两个矩阵 `M` 和 `U` 的乘积。具体来说，`M` 是 `1000×100` 的矩阵，其行代表电影，列代表特征；`U` 是 `100×2000` 的矩阵，其行代表特征，列代表用户。`M` 和 `U` 兼容，因为它们的乘积维度为 `(1000×100) × (100×2000)`，结果是一个 `1000×2000` 维的矩阵，这也是矩阵 `R` 的维度。此外，`M*U` 的行和列内容与矩阵 `R` 的行和列内容相匹配。

下一节将描述一种新的推荐系统类型，随后介绍本章 earlier 提到的两种主要推荐系统类型。

## 基于内容的推荐系统

基于内容的推荐系统的前提很简单：如果你喜欢某个项目，你很可能也喜欢“相似”的项目。在很容易确定每个项目的上下文或属性的情况下，基于项目相似度的推荐通常效果良好。例如，推荐同类型的电影、书籍、歌曲或餐厅。

基于内容的推荐系统分为两大类：(1) 仅分析内容描述的技术；(2) 构建用户画像和项目画像的技术。这两类技术在下面的子节中分别讨论。

### 仅分析内容描述

该技术类似于基于项目的协同过滤：系统推荐与用户标记为“喜欢”的已知项目相似的内容。该技术的优势包括：

*   如果描述有意义，可避免“新项目问题”

*   可利用语义信息和推断

*   更易创建透明的系统

该技术也有以下缺点：

*   倾向于过度专业化

*   会推荐与用户已消费相似的项目

*   容易形成“滤波泡沫”

### 构建用户画像和项目画像

一种创建用户画像的技术利用用户之前交互过的项目描述或属性，以推荐相似项目。该技术仅依赖用户的历史选择。该技术能够避免冷启动问题，并且对于文本类项目（如文章、新闻、书籍）使用也简单。

## 协同过滤算法

协同过滤的前提可以通过以下简单示例说明。假设人物 `A` 喜欢项目 `1`、`2`、`3`，而人物 `B` 喜欢项目 `2`、`3`、`4`。可以看出，`A` 和 `B` 的兴趣相似，因此我们推断 `A` 会喜欢项目 `4`（因为 `B` 喜欢），同时 `B` 会喜欢 `A` 喜欢的项目。

具体例子：你去餐厅后，向服务员（或同伴）询问推荐，这就是协同过滤的一个例子。

关于协同过滤算法的几点注意事项：

*   算法完全基于历史行为。

*   与上下文无关。

*   独立于其他任何信息。

*   这是一个常用算法。

### 用户-用户协同过滤

该技术通过查找与给定用户相似的客户，找出他们喜欢的产品，然后向给定用户推荐这些产品。这是一种非常有效的算法，但也消耗大量时间和资源，因为必须计算 `每一对` 客户的相似性。在非常大的平台上，若缺乏强大的可并行化系统，实现该算法非常困难。

### 项目-项目协同过滤

该技术与用户-用户协同过滤类似，主要区别在于：

`find item lookalike instead of customer look alike`

-   [类似于用户购买的商品向客户推荐相似商品（当构建相似度矩阵时）](https://wiki.example.org/feynmans_learning_method)的技术比用户-用户协同过滤更省资源。事实上，对于新用户，项目-项目算法的耗时远低于用户-用户协同，因为我们不需要计算所有用户之间的相似度。在商品数量固定的情况下，项目-项目相似度矩阵随时间保持不变。如有需要，可参考附录 `A` 中关于各种距离度量的讨论。

### `Recommender System with Surprise`

`Surprise` 是基于 `Sklearn` 的简单 Python 推荐系统引擎，其缩写为 simple Python recommendation system engine。`Surprise` 是一个开源 Python 库，用于构建和分析推荐系统。

`Surprise` 提供内置数据集、预测算法、降维（`PCA` 和 `SVD`）以及多种指标，如 `MAE`、`RMSE` 等。访问其主页可了解其特性和代码示例：`[`surpriselib.com`](https://surpriselib.com)`

## `Recommender Systems and Reinforcement Learning (Optional)`

正如您已学过的，传统推荐系统通常涉及协同过滤或基于内容的系统。实现推荐系统的另一种方法是强化学习。在深入细节之前，我们先简要介绍强化学习的高层次描述。

### `Basic Reinforcement Learning in Five Minutes`

强化学习涉及一个“代理人”在随机或确定性方式中在各种状态之间移动，以最大化其预期未来奖励。每个状态都有一个奖励值，可能为正、零或负。找到最优路径通常需要进行大量、大量的迭代。*请记住以下要点：代理人（即学习者）并不知道必须采取哪些动作以及按什么顺序执行；代理人必须自行发现这些动作。*

另一个重要点：*在一般情况下，贪婪算法在强化学习任务中会失败，因此采用一种称为“ε 贪婪”算法的泛化方法。* 该方法涉及以下变量：

*   初始状态 `S`

*   变量 `epsilon`，初始值为 `1`

*   变量 `rnd`，为 `0` 到 `1` 之间的随机生成数

*   `Q` 表，其行为是状态行和动作列

如果 `rnd` 小于 `epsilon`，则在当前状态下选择一个随机动作 `A`（该动作针对当前状态已定义）；否则，选择 `Q(S,A)` 值最大的动作。无论哪种情况，选定的动作 `A` 会交给环境（可视为“ oracle”），该环境返回新状态、奖励和布尔“done”标志，其中“done”标志在当前回合（或游戏）结束时为 `true`。下面是一段示例代码，用于根据当前动作确定新状态，其中变量 `env` 是“ oracle”：

```python
import gym  # 初始化状态、动作、epsilon、rnd、done、total_reward
# state = 当前状态
# 其他细节省略
while done == False:
    # 根据 ε 贪婪算法确定一个 **action**：
    # 细节省略...
    # 获取下一个状态和奖励：
    next_state, reward, done, _ = env.step(action)
    # 将当前状态设置为新状态：
    state = next_state
    total_reward += reward
```

上述代码位于循环内部，意味着会在顺序中选择多个动作，以到达不同的状态。

每当生成 `rnd` 的值时，`epsilon` 会从 `1` 递减到一个小数（通常为 `0.1`）。因此，在多次迭代中，随机选择的动作（称为“探索”）数量减少，而贪婪式选择的动作（称为“利用”）数量增加。

如果 `epsilon` 是常数 `0`，则算法仅为贪婪算法，后者实际上是 ε 贪婪算法的特例。相反，如果 `epsilon` 是常数 `1`，则算法仅涉及随机选择，这没有任何实际价值。思考后，ε 贪婪算法在巧妙而优雅地结合随机选择与确定性选择方面表现出色。

强化学习中一个广为人知的技术是 `q-learning`（即“质量”学习），它使用二维矩阵（即“Q 表”），行为是状态行和动作列。矩阵单元是 `(state, action)` 对，初始化为 `0`。每次循环（包含 ε 贪婪算法）结束后，当前选定的 `(state, action)` 对会根据新奖励值进行更新，代理人转移到新选定的状态。

然而，`Q` 表适用于状态和动作数量固定的场景，例如涉及迷宫或在矩形网格中导航的任务。对于像超级马里奥这类游戏，每当马里奥在屏幕上移动时，新出现的像素集合被视为新状态。因此，状态数量被视为连续而非离散。

然而，与将每个新状态追加到 `Q` 表不同，我们使用称为深度 Q 学习（`DQN`）的方法，它将状态作为神经网络的输入，输出层为可能的动作集合。神经网络通过反向误差传播进行训练，输出层中概率最高的动作被选中。

另一种情况是，状态数量和动作数量均为连续。例如，考虑一个移动车辆：状态是连续的，动作（如转动方向盘）也是连续的。存在一些深度强化学习算法，如软 actor critic（`SAC`）和双延迟 `DDPG`（`TD3`），用于解决此类任务。

另一个细节：几乎所有强化学习任务都可以建模为马尔可夫决策过程（`MDP`），`MDP` 基于马尔可夫链，后者是一种带有概率的有向边缘的不可判定有限自动机（`NFA`），其出边概率之和为 `1`。确实，强化学习中存在许多概念和算法，包括：

*   代理人

*   环境

*   状态

*   状态转移

*   动作（及概率）

*   折扣因子

*   折扣未来奖励

*   马尔可夫链

*   `MDP`

*   在线政策与离线政策

*   基于模型与无模型

*   `Q-learning`

*   贝尔曼方程

*   政策梯度算法

*   深度强化学习算法

您可以在网上找到大量讨论上述主题的文章，并查看深度强化学习算法的代码示例。

### `What is RecSim?`

`RecSim` 是一个基于强化学习（`RL`）的开源平台，用于创建协同交互式推荐器（`CIRs`）的模拟。回顾前一节，`RL` 涉及代理人、状态集合以及每个状态关联的动作集，这些动作使得状态之间能够转换。此外，某些任务使用 ε 贪婪算法选择一个状态，该状态交给环境（“ oracle”），环境返回新状态、奖励以及布尔“done”标志。

与之相比，`RecSim` 代理人与环境交互，环境由用户模型、文档模型和用户选择模型组成。在 `RecSim` 中，状态可以表示为内容，动作是下一个最佳内容，用户满意度代表奖励。此外，可以使用向量嵌入来表示内容。简而言之，`RL` 使得推荐系统能够向用户推荐新内容，而该内容独立于之前的推荐。 

事实上，这些新建议可能包含对他们有吸引力的随机内容。这种方法为用户提供了发现以前可能并不感兴趣的新兴趣的机会：毕竟，人们的兴趣可以（也确实）随时间而改变。确实，基于强化学习的模型会随着用户兴趣的变化而不断学习和演变。这部分关于推荐系统的章节到此结束。如果您对推荐系统的最新趋势感兴趣，请访问以下链接：

`[`aws.amazon.com/blogs/media/whats-new-in-recommender-systems/`](https://aws.amazon.com/blogs/media/whats-new-in-recommender-systems/)`

下一节讨论情感分析，并附有一个使用 `NLTK` 进行情感分析的 Python 代码示例。

## 什么是情感分析？

情感分析的目的是判断某人对某主题、文档的上下文，或一系列文档的态度。在每种情况下，情感分析判断输入文本是表达出积极、消极还是中性情感。

在高层次上，情感分析涉及自然语言处理的多个处理步骤，随后是模型训练。第一阶段对文本进行处理，使得在准备训练模型时，我们已经知道模型需要的输入变量。模型学习根据这些变量判断一段文本的情感。

情感分析也可以是二元分类任务，涉及积极和消极情感。情感分析可在许多情境下进行，其中包括：

*   对特定产品的在线情感

*   分析电影、书籍和餐厅的评论

*   客户支持中心记录的问题

正如您在第 `3` 章节中学到的，人类语言非常灵活，能够表达：

*   正负情感的混合

*   嘲讽及其细微差别

*   俚语（负面词汇也可能表示正面）

此外，语言本质上是模糊的，因为我们的情感可以传达嘲讽、讽刺和双关，这些都给 `NLP` 带来挑战。

进行情感分析的主要有两种方式：基于规则的方法（较老且力度较小）和机器学习技术。

基于规则的方法很简单：统计文档中积极词和消极词的数量，数量较大的那一方决定文档的情感。

然而，基于规则的情感分析方法存在缺陷：该方法只关注单个词，而不考虑上下文。例如，基于 `token` 的算法会对“The concert last night was the bomb.” 这样的句子生成高度负面的评分。

机器学习方法则使用分类模型（可从多种算法中选择），在标记的正、负和中性情感数据集上进行训练。可以将这三种情感赋值为 `1`、`-1` 和 `0`，或者赋值范围为 `[-1,1]`。后者中，`-1` 表示最负面情感，`+1` 表示最正面情感。

作为练习，请尝试为以下句子赋予数值情感：

1. “Our plan was not without merit” 与 “Our plan has merit” 意义相近。

2. “I like the pizza toppings, but I do not like the crust.”

3. “The only thing worse than being talked about, is not being talked about” (Oscar Wilde).

4. “Everything is funny, as long as it’s happening to somebody else” (Will Rogers).

5. “When ignorance is bliss, ‘tis folly to be wise” (William Shakespeare).

6. “Good judgment is the result of experience and experience the result of bad judgement” (Mark Twain).

下面是对前面列表中句子的观察。例如 `#1` 包含两个意义相近的句子，但前者接近“双重否定”，是更具挑战性的 `NLP` 情感分析任务。根据所用的 `Python` 库，第二句更有可能获得更高的积极情感评分。

示例 `#2` 既有积极也有消极情感：整句话的数值情感是多少？如果计算 `+1`（积极）和 `-1`（消极）的平均值，结果为 `0`，这表明整体情感为中性。尽管整体情感可能被认为是中性，但句子的两个部分并不中性。

示例 `#3` 可能被视为一种简洁而讽刺的观察，一些人可能认为它也带有一丝哀愁。该句表达了“`B` 比 `A` 更差”的情感形式，暗示 `A` 本身是负面的，但并未明确表达。

示例 `#4` 是一种普遍为真的话，包含正负事件，但不使用任何负面词汇，如 “not”、“bad”、“worse” 等。

示例 `#5` 是威廉·莎士比亚的一句著名引语，常被误译为 “ignorance is bliss”，完整引语含义截然不同。词 “ignorance” 和 “folly” 都表达负面情感。

示例 `#6` 听起来矛盾，直到你获得足够的经验和智慧才能理解其含义。句子中只有 “good” 和 “bad” 这两个词表达情感。后文将提供一个 `Python` 代码示例，对上述句子进行情感分析。

### 用于情感分析的有用工具

以下列表提供了情感分析工具的各种功能，可能适合您的 `NLP` 需求：

*   IBM Watson Tone Analyzer

*   OpenText

*   Talkwalker

*   Rapidminer

*   Social Mention

*   Textblob

*   Vader

请在线搜索这些情感分析工具的文档，以确定哪些工具适合您的任务。

### 方面情感分析

`Aspect-based` 情感分析是比普通情感分析更高级的技术：后者仅检测整体语料的情感，而前者分析每段文本，识别各个方面及其对应的情感。

例如，普通情感分析可能判定一条评论为负面，而方面情感分析可能发现该顾客对某产品的电池续航不满意。因此，方面情感分析能够提供更细粒度的语料分析，这在处理基于文本的客户反馈时至重要。

需要注意的是，方面情感分析既可以提取情感（即对特定方面的积极或消极看法），也可以提取方面（即当前关注的项目）。

例如，`Algorithmia` 提供免费的 API 端点，无需自行部署或管理服务器和基础设施即可调用多种算法。

另一个机器学习工具包是 `Apache OpenNLP`，它提供分词、句子分割、词性标注、实体抽取、 `chunking`、解析以及核心 `ference` 解析等基础 `NLP` 功能。

### 深度学习与情感分析

循环神经网络（`RNN`）和长短期记忆网络（`LSTM`）等深度学习模型可以与 `NLP` 语义分析相结合，例如在推特中判断情感：

`https://ieeexplore.ieee.org/stamp/stamp.jsp? arnumber=8244338`

您也可以将 `RNN` 与情感分析相结合，如这里所述：

`[`blog.openai.com/unsupervised-sentiment-neuron/`](https://blog.openai.com/unsupervised-sentiment-neuron/)`

`https://github.com/openai/generating-reviews-discovering-sentiment`

There are several details to keep in mind. First, distributed word vector techniques have been shown to outperform `BoW` models (as you would probably surmise). Second, the paragraph vector algorithm preserves word order information and produces state-of-the-art results. This algorithm performs better because vector averaging and clustering lose the word order. Third, it’s worthwhile to acquaint yourself with the transformer architecture and `BERT`-based models that are discussed in Chapter `11` before you decide to use `RNNs` or `LSTMs` for sentiment analysis.

## `Sentiment Analysis with Naïve Bayes`

Listing `9.3` displays the contents of `nb_sentiment.py` that illustrates how to perform sentiment analysis with `NLTK`.

***`LISTING 9.3: nb_sentiment.py`***
