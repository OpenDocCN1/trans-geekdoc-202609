
你想为每个模式定义一个桶（bucket），在峰值之间放置边界。无论你使用分位数还是众数，你都需要提前分析你的想法的分布，就像我们之前为了归一化 `housing_median_age` 列提前测量均值和标准差一样。

## 分类特征

对于像 `ocean_proximity` 这样的分类特征，有几种选择。如果它已经表示为类别 ID（即从 0 到最大 ID 的整数），那么你可以使用 `categorical_column_with_identity()` 函数（指定最大 ID）。如果不是，且你知道所有可能类别的列表，你可以使用 `categorical_column_with_vocabulary_list()`：

```
ocean_prox_vocab = ['IE OCEAN', 'INLAND', 'ISLAND', 'NEAR BAY', 'NEAR OCEAN']
ocean_proximity = tf.feature_column.categorical_column_with_vocabulary_list(
    'ocean_proximity', ocean_prox_vocab)
```

如果你希望让 TensorFlow 从文件中加载词汇表，可以调用 `categorical_column_with_vocabulary_file()`。如你所期的，这两个函数将简单地将每个类别映射到其在词汇表中的索引（例如，NEAR BAY 将映射到 3），未知类别将映射到 -1。

对于具有大型词汇表的分类列（例如邮政编码、城市、单词、产品、用户等），获取所有可能类别的完整列表可能并不方便，或者类别的添加或删除过于频繁，导致使用索引不可靠。在这种情况下，你可能倾向于使用 `categorical_column_with_hash_bucket()`。如果数据集中有一个“城市”特征，我们可以这样对其编码：

```
city_hash = tf.feature_column.categorical_column_with_hash_bucket(
    'city', hash_bucket_size=1000)
```

此特征将为每个类别（即每个城市）计算一个哈希值，对哈希桶的数量（`hash_bucket_size`）取模。你必须将桶的数量设置得足够以避免过多的冲突（即不同的类别落在同一个桶中），但设置得越高，使用的内存就越多（通过嵌入表，我们稍后将看到）。

## 交叉分类特征

如果你认为两个（或多个）分类特征共同使用时更有意义，那么你可以创建一个交叉列（crossed column）。例如，假设人们特别喜欢位于内陆的老房子和靠近海洋的新房子，那么为 `housing_median_age` 特征创建一个桶化列，并将其与 `ocean_proximity` 列交叉可能会有所帮助。桶化列将根据 `hash_bucket_size` 取模，并结合它交叉的接近度组合，这将赋予它交叉类别 ID。然后，你可以选择只在模型中使用此此交叉列，也可以同时包含单个列。

```
bucketized_age = tf.feature_column.bucketized_column(
housing_median_age, boundaries=[-0., -0.5, 0., 0.5, 1.]]) # age 已经过缩放
age_and_ocean_proximity = tf.feature_column.crossed_column(
[bucketized_age, ocean_proximity], hash_bucket_size=100)
```

用于交叉列的另一个常见情况是将纬度和经度交叉成单个分类特征：通过为每个维度设置 20 个桶开始，然后将这些桶化特征交叉成位置列。这将在加利福尼亚创建一个 20x20 的网格，网格中的每个单元格将对应一个类别：

```
latitude = tf.feature_column.numeric_column("latitude")
longitude = tf.feature_column.numeric_column("longitude")
bucketized_latitude = tf.feature_column.bucketized_column(
latitude, boundaries=list(range(20)))
bucketized_longitude = tf.feature_column.bucketized_column(
longitude, boundaries=list(range(20)))
# ...（此处省略）
```

## 使用 One-Hot 编码分类特征

无论选择什么，它都必须输入神经网络。编码分类特征有两种方法：one-hot 或嵌入（embeddings）。对于第一个选项，简单使用：

```
ocean_proximity_hot = tf.feature_column.indicator_column(ocean_proximity)
```

经验法则，如果类别少于 10，通常使用 one-hot。如果类别大于 50，嵌入通常是更好的。在 10 到 50 之间，你可能想尝试两种方法。

## 使用嵌入编码分类特征

嵌入是一个表示类别的可训练密集向量。默认情况下，嵌入是随机初始化的，例如，“NEAR BAY”类别可能表示为 `[0.131, 0.890]`，而“NEAR OCEAN”类别可能由另一个随机向量如 `[0.631, 0.791]` 表示。由于这些嵌入是可训练的，会在训练过程中逐渐改进，梯度下降会将它们移动到靠近“INLAND”类别。事实上，表示越好，神经网络越容易做出准确预测。这被称为表示学习。

## 词嵌入

嵌入通常不仅对当前任务有用，而且这些相同的嵌入也可以成功地复用于其他任务。最常见的例子是嵌入（即单个单词的嵌入）；当你处理自然语言处理任务时，使用预训练的嵌入通常比自己训练更好。使用向量表示单词的想法可以追溯到20世纪60年代，并且已有许多复杂的技术被用于生成有效的向量，包括使用神经网络，这在2013年真正兴起，当时 Tomás Mikolov 和Google的其他研究人员发表了一种论文，描述了如何使用深度神经网络学习词嵌入，速度快于之前的尝试。这使得他们能够在大型文本语料库上学习嵌入：他们训练了一个深度神经网络来预测给定单词附近的单词。这使他们获得了惊人的嵌入。例如，同义词具有非常接近的嵌入，语义相关的单词（如法国、西班牙、意大利等）最终聚集在一起。但词嵌入还围绕空间中有意义的轴进行组织。这里有一个著名的例子：如果你计算 `King – Woman`（加上并减去这些单词的嵌入向量），那么结果将非常接近 `Queen` 的嵌入。换句话说，词嵌入编码了概念！同样，你可以计算 `Madrid – Spain – France`，结果显然非常接近 `Paris`，这似乎表明首都的概念也被编码在嵌入中。
