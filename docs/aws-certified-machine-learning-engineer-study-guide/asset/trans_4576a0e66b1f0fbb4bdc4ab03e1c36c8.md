
```
import pandas as pd
from sklearn.preprocessing import OneHotEncoder

# 示例数据
data = {'Color': ['White', 'Black', 'Red', 'Blue', 'Green', 'Yellow', 'Pink', 'Brown', 'White', 'Black']}
df = pd.DataFrame(data)

# 初始化 OneHotEncoder
encoder = OneHotEncoder(sparse_output=False)

# 拟合并转换数据
one_hot = encoder.fit_transform(df[['Color']])

# 转换为 DataFrame 以便查看
one_hot_df = pd.DataFrame(one_hot, columns=encoder.get_feature_names_out(['Color']))

# 打印结果
print("原始数据:\n", df)
print("\n独热编码数据:\n", one_hot_df)
```

[图 3.13](#c003.xhtml#c03-fig-13) 展示了该程序产生的结果。

![图 3.13 独热编码。](images/c03f013.png)

[图 3.13](#c003.xhtml#rc03-fig-13) 独热编码。

正如你所见，原始数据集有一个分类特征“Color”，包含 10 个数据点（类别）：White、Black、Red、Blue、Green、Yellow、Pink、Brown、White 和 Black。

独热编码后的数据集已转换为八个数值特征，等于不同颜色的数量：`Color_Black`、`Color_Blue`、`Color_Brown`、`Color_Green`、`Color_Pink`、`Color_Red`、`Color_White` 和 `Color_Yellow`。它们每个都有 10 个数据点。

独热编码是具有少量分类数据的特征以及非树模型 ML 算法（如线性回归、k-NN 和神经网络）的良好选择。这些算法将在下一章中介绍。

### 二进制编码

二进制编码是一种处理分类数据的有效技术，不会像独热编码那样导致特征数据集的维度“爆炸”。其工作原理是将每个类别值转换为对应的二进制数，然后将该二进制数拆分为单独的位作为独立的特征（列）。

可以将二进制编码视为一种压缩独热编码技术所产生特征数量的方法。

在下面的示例中，我们使用了 `category_encoders` 模块中的 `BinaryEncoder` 类对前一个示例中的相同数据集进行二进制编码：

```
import category_encoders as ce
import pandas as pd

# 示例数据
data = {'Color': ['White', 'Black', 'Red', 'Blue', 'Green', 'Yellow', 'Pink', 'Brown', 'White', 'Black']}
df = pd.DataFrame(data)

# 初始化二进制编码器
encoder = ce.BinaryEncoder(cols=['Color'])

# 拟合并转换数据
df_binary_encoded = encoder.fit_transform(df)

# 打印结果
print("原始数据:\n", df)
print("\n二进制编码数据:\n", df_binary_encoded)
```

[图 3.14](#c003.xhtml#c03-fig-14) 显示了此转换的输出。

![图 3.14 二进制编码。](images/c03f014.png)

[图 3.14](#c003.xhtml#rc03-fig-14) 二进制编码。

由于对 10 个非唯一类别进行二进制编码，新数据集只有四个数值特征（而不是八个）。

为什么是四个？因为原始数据集有八个不同的类别，可以使用四位二进制格式表示。请注意，数据点的数量（10）在转换数据时不会改变。

二进制编码最适合解决独热编码的缺点，因为它缓解了为每个唯一类别创建一个新特征而导致的维度“爆炸”。

然而，与独热编码相比，二进制编码可能导致分类数据内的信息丢失，这可能会对模型性能产生负面影响。这是因为二进制编码将分类数据压缩到更少的位中，导致类别之间的区别变得模糊。

### 特征哈希

该技术使用哈希函数将高基数分类数据转换为固定数量的数值特征，你作为 ML 工程师可以自行选择该数量。

特征哈希高效且具有高度可扩展性，因为转换结果是一个固定大小的向量，从而控制了内存使用量。以下是其高层工作原理：

*   **输入特征。** 特征哈希函数接收一个特征值，该值可以是单词、类别或数据中任何其他可识别的属性。
*   **哈希函数应用。** 特征由哈希函数处理，该函数根据特征的值返回一个唯一的整数值（哈希值）。
*   **取模运算（可选）。** 为确保哈希值落在所需范围内（通常是特征向量的大小），哈希值通常对预定义的数字取模。
*   **向量更新。** 计算出的哈希值用作索引，以更新特征向量中对应的元素。

通过利用哈希函数，这种方法能快速转换数据，因此适用于大型数据集。虽然可能发生冲突，但值的聚合通常能减轻其影响，尤其是当哈希桶足够大时。

因此，特征哈希在保留信息和保持计算效率之间取得了平衡。它是以高效且具成本效益的方式对高基数分类数据进行特征工程的绝佳解决方案。

你可以使用 `sklearn.feature_extraction` 模块中的 `FeatureHasher` 类通过此方法对特征进行哈希，如下面的代码片段所示：

```
import pandas as pd
from sklearn.feature_extraction import FeatureHasher

# 示例数据
data = [{'Color': 'White'}, {'Color': 'Black'}, {'Color': 'Red'}, {'Color': 'Blue'}, {'Color': 'Green'}, {'Color': 'Yellow'}, {'Color': 'Pink'}, {'Color': 'Brown'}, {'Color': 'White'}, {'Color': 'Black'}]

# 转换为 DataFrame 以便在转换前查看
df = pd.DataFrame(data)

print("原始数据:")
print(df)

# 初始化 FeatureHasher
hasher = FeatureHasher(n_features=3, input_type='dict')

# 拟合并转换数据
hashed_features = hasher.transform(data)

# 将哈希特征转换为 DataFrame 以便查看
hashed_df = pd.DataFrame(hashed_features.toarray(), columns=[f'feature_{i}' for i in range(hashed_features.shape[1])])

print("\n哈希后的数据:")
print(hashed_df)
```

[图 3.15](#c003.xhtml#c03-fig-15) 显示了该程序生成的哈希特征。

![图 3.15 特征哈希。](images/c03f015.png)

[图 3.15](#c003.xhtml#rc03-fig-15) 特征哈希。

请注意 `FeatureHasher` 类如何应用特征哈希将分类数据（10 个类别）转换为每个类别的固定大小向量。在本示例中，我们在 `FeatureHasher` 类的构造函数中设置了特征数量。该数字已设置为 3。

结果，这 10 个类别已被哈希为 10 个向量。每个向量包含三个整数，对应三个特征中的每一个。

### 时间序列数据的特征工程

时间序列数据在本章开头已介绍，它不同于标准表格数据，因为它是随时间重复采集的，每个连续数据点都依赖于其过去的值。可以将时间序列想象成看电影——每个场景都取决于前面的场景。时间维度在时间序列数据中起着关键作用。

**Amazon SageMaker Data Wrangler** 为时间序列数据处理提供了一个低代码解决方案，能够更快地清理、转换和准备数据。它还使数据科学家能够按照其预测模型的输入格式要求来设计时间序列数据特征。

要对时间序列数据集执行特征工程，我们首先需要了解数据集中存在的模式。Amazon SageMaker Data Wrangler 提供了许多可视化工具，为数据科学家和分析师提供了关于现有模式的宝贵线索，并可帮助你选择建模策略。在了解数据集中存在的模式后，我们就可以开始设计旨在提高预测模型准确性的新特征。
