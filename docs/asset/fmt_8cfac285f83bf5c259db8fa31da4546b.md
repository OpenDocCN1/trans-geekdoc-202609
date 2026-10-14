
除以标准差（`σ`）会相对于数据的分布范围缩放数据点。此步骤确保标准化后数据的方差（即标准差的平方）变为 1。

### 缩放

**缩放** 是调整特征范围或分布的通用术语。由于归一化主要关注转换后数据集的范围（将所有特征缩放至 0 到 1），而标准化关注分布（转换后数据集的均值 `μ` 为 0，标准差 `σ` 为 1），您刚学习的这两种技术都属于缩放范畴。

如果您的特征数据不符合正态分布，您需要采用不同于 Z-score 标准化的技术来处理偏态或异常值。考试需要了解的技术如下：

*   **鲁棒缩放。** 鲁棒缩放通过减去中位数来使特征数据集居中，并根据四分位距（IQR）进行缩放。这使其特别适用于包含异常值的数据集，因为它能确保中心趋势和分布范围对异常值具有鲁棒性。因此，这种标准化技术对异常值不敏感，且在处理偏态数据时效果良好。

    您可以使用 `sklearn.preprocessing` 模块中的 `RobustScaler` 类通过此技术缩放特征，如以下示例所示：

    ```python
    import numpy as np
    import pandas as pd
    from sklearn.preprocessing import RobustScaler
    
    # 加载数据集
    data = np.array([[4, 11], [3.8, 12], [4.5, 12.5], [8, 8], [9, 8.5], [9.5, 7.5], [13, 5], [14, 4.7], [13.7, 6], [25, 23]])
    df = pd.DataFrame(data, columns=['Feature1', 'Feature2'])
    
    # 应用 RobustScaler
    scaler = RobustScaler()
    data_scaled = scaler.fit_transform(df)
    
    # 将缩放后的数据转换回 DataFrame 以便查看
    df_scaled = pd.DataFrame(data_scaled, columns=['Feature1', 'Feature2'])
    
    print("原始数据:")
    print(df)
    print("\n 缩放后数据:")
    print(df_scaled)
    ```

    上述代码生成的输出如图 3.12 所示。

    ![图 3.12 鲁棒缩放。](img/c03f012.png)

    图 3.12 鲁棒缩放。

    正如您在图 3.12 中所见，经过鲁棒缩放后，缩放后的数据框对异常值的敏感度低于原始数据框。由于转换的结果，像 `[25, 23]` 这样的异常值不会扭曲您特征的新数据集。

*   **MinMax 缩放。** 这种标准化技术将特征转换到一个固定范围，通常在 0 和 1 之间。该技术保留了特征间的关系，但不解决偏态问题。

    您可以使用 `sklearn.preprocessing` 模块中的 `MinMaxScaler` 类通过此方法缩放特征，如以下代码片段所示：

    ```python
    import numpy as np
    import pandas as pd
    from sklearn.preprocessing import MinMaxScaler
    
    # 示例数据
    data = np.array([[1, 2], [3, 4], [5, 6], [7, 8], [-1, -2], [-3, -4]])
    df = pd.DataFrame(data, columns=['Feature1', 'Feature2'])
    
    # 初始化 MinMaxScaler
    scaler = MinMaxScaler()
    
    # 拟合并转换
    data_scaled = scaler.fit_transform(df)
    df_scaled = pd.DataFrame(data_scaled, columns=['Feature1', 'Feature2'])
    
    # 打印结果
    print("原始数据:\n", df)
    print("\n 缩放后数据:\n", df_scaled)
    ```

*   **MaxAbs 缩放。** MaxAbs 缩放是一种通过将每个特征数据点缩放至其最大绝对值来标准化数据的技术。结果是每个数据点都落在 [−1, 1] 范围内。

    此技术最适合用于标准化稀疏数据集或包含许多 0 数据点的数据集，因为它在保持原始数据分布的同时保留了 0 条目。

    您可以使用 `sklearn.preprocessing` 模块中的 `MaxAbsScaler` 类，通过这种方法缩放特征，如以下代码片段所示：

    ```python
    import numpy as np
    import pandas as pd
    from sklearn.preprocessing import MaxAbsScaler
    
    # Sample data
    data = np.array([[1, 2], [3, 4], [5, 6], [7, 8], [-1, -2], [-3, -4]])
    df = pd.DataFrame(data, columns=['Feature1', 'Feature2'])
    
    # Initialize MaxAbsScaler
    scaler = MaxAbsScaler()
    
    # Fit and Transform
    data_scaled = scaler.fit_transform(df)
    df_scaled = pd.DataFrame(data_scaled, columns=['Feature1', 'Feature2'])
    
    # Print results
    print("Original Data:\n", df)
    print("\nScaled Data:\n", df_scaled)
    ```

#### 幂变换（Box-Cox、Yeo-Johnson）

数据集的方差是标准差的平方（`σ²`）。根据定义，方差始终为正数，用于衡量数据集中数据点的分散程度，告诉您每个点距离均值（`μ`）有多远。从数学上讲，它是与均值之差的平方的平均值。方差高意味着数据点分散在远离均值的位置；方差低意味着它们接近均值。

幂变换有助于稳定方差并使数据更接近正态分布。两种常见类型是 Box-Cox 变换和 Yeo-Johnson 变换。前者仅适用于正数据，而后者可同时处理正数据和负数据。

您可以使用 `sklearn.preprocessing` 模块中的 `PowerTransformer` 类，通过这种方法缩放特征，如以下代码片段所示：

```python
import numpy as np
import pandas as pd
from sklearn.preprocessing import PowerTransformer

# Sample data
data = np.array([[1, 2], [3, 4], [5, 6], [7, 8], [-1, -2], [-3, -4]])
df = pd.DataFrame(data, columns=['Feature1', 'Feature2'])

# Initialize Yeo-Johnson Transformation
pt = PowerTransformer(method='yeo-johnson')

# Fit and Transform
data_scaled = pt.fit_transform(df)
df_scaled = pd.DataFrame(data_scaled, columns=['Feature1', 'Feature2'])

# Print results
print("Original Data:\n", df)
print("\nScaled Data:\n", df_scaled)
```

幂变换通过减少偏度和稳定方差，使您的数据更适合建模，从而产生更稳健、更准确的模型。

#### 对数变换

正如您之前所学，对数变换是一种检测和管理异常值的方法。它作为数值数据的一种特征工程技术，通过减少偏度、限制异常值的影响和增强线性关系来提供帮助。具体方式如下：

*   **减少偏度。** 许多现实世界的数据集呈右偏，意味着大多数数据点聚集在较低值周围，而少数异常值将“尾部”延伸向较高值。常见例子包括收入分布，少数高收入者形成长右尾；或是高难度考试的分数分布，大多数学生得分较低，少数高分者在顶端。应用对数变换可压缩这一尾部，使分布更对称、更接近正态分布，而许多 ML 算法能更好地处理正态分布。

*   **限制异常值的影响。** 高值异常值可能主导并扭曲数值数据的尺度。对数变换降低这些异常值的量级，使其更接近数据主体，而无需直接删除。

*   **增强线性关系。** 对于某些数据，特征与目标变量之间的关系可能是乘法或指数关系，而非线性关系。对数变换可将这些关系线性化，使线性模型更容易捕捉潜在模式。

例如，考虑以下数据集：

```
[x,y] = [[3, 1], [4, 10], [5, 100], [6, 1000]]
```

通过将 `y` 转换为 `log10(y)`，新数据集变为：

```
[x,y] = [[3, 0], [4, 1], [5, 2], [6, 3]]
```

通过将数据转换为对数尺度，变化变得更易管理，数据的整体结构也更清晰。这种变换能显著提升许多模型的性能和准确性。

#### 平方根或立方根

为了处理数值数据集中的高方差（除了前面介绍的幂变换），可考虑使用平方根或立方根变换。特征的平方根和立方根会影响特征分布。然而，这种影响不如对数变换显著。立方根有其自身优势：可应用于包括 0 在内的负值。平方根仅适用于正值和 0。

#### 分箱

分箱（也称为**分桶**）是将数值型连续数据划分为离散区间或“箱”的过程。此技术可简化 ML 模型开发，并使模型对异常值和噪声更稳健。通过分箱，您可将数值数据转换为分类数据。

例如，若您查看汽车数据，可将车辆重量转换为五列：`is_minicompact`、`is_subcompact`、`is_compact`、`is_midsize` 和 `is_large`。

### 分类数据的特征工程

分类数据能捕捉数值数据可能遗漏的数据关系和特征信息。妥善设计的分类特征能显著提升 ML 模型性能。

分类数据的特征工程始于**编码**，即将特征数据从字符串格式转换为数值格式的过程。数值格式可以是整数、整数数组、矩阵，甚至是整数张量。编码的目的是让 ML 算法能解释并使用这些数据作为输入，因为大多数算法只能理解数值。

例如，若您的类别为 White、Black 和 Red，可将这些数据编码为三个向量：`[1, 0, 0]` 代表 White，`[0, 1, 0]` 代表 Black，`[0, 0, 1]` 代表 Red。

#### 标签编码

标签编码——顾名思义——将分类特征的每个类别标记为唯一整数。例如，具有如下值的分类特征“Color”

```
["White", "Black", "Red"]
```

变为

```
[0, 1, 2]
```

虽然简单，但此技术可能给假设数据存在有序关系的算法带来问题，因为它在分类值上强加了序数结构。

此编码技术最适合基于树的 ML 算法，因为这些算法能处理标签编码隐含的序数关系。

#### 独热编码

独热编码将分类特征转换为一组二进制特征，其中每个二进制特征代表一个可能的类别，若该类别存在则值为 1，不存在则为 0。

您可以使用 `sklearn.preprocessing` 模块中的 `OneHotEncoder` 类，通过这种方法对特征进行编码，如以下代码片段所示：

```python
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
print("\n 独热编码数据:\n", one_hot_df)
```

图 3.13 展示了该程序产生的结果。

![图 3.13 独热编码。](img/c03f013.png)

图 3.13 独热编码。

正如你所见，原始数据集有一个分类特征“Color”，包含 10 个数据点（类别）：White、Black、Red、Blue、Green、Yellow、Pink、Brown、White 和 Black。

独热编码后的数据集已转换为八个数值特征，等于不同颜色的数量：`Color_Black`、`Color_Blue`、`Color_Brown`、`Color_Green`、`Color_Pink`、`Color_Red`、`Color_White` 和 `Color_Yellow`。它们每个都有 10 个数据点。

独热编码是具有少量分类数据的特征以及非树模型 ML 算法（如线性回归、k-NN 和神经网络）的良好选择。这些算法将在下一章中介绍。

#### 二进制编码

二进制编码是一种处理分类数据的有效技术，不会像独热编码那样导致特征数据集的维度“爆炸”。其工作原理是将每个类别值转换为对应的二进制数，然后将该二进制数拆分为单独的位作为独立的特征（列）。

可以将二进制编码视为一种压缩独热编码技术所产生特征数量的方法。

在下面的示例中，我们使用了 `category_encoders` 模块中的 `BinaryEncoder` 类对前一个示例中的相同数据集进行二进制编码：

```python
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
print("\n 二进制编码数据:\n", df_binary_encoded)
```

图 3.14 显示了此转换的输出。

![图 3.14 二进制编码。](img/c03f014.png)

图 3.14 二进制编码。

由于对 10 个非唯一类别进行二进制编码，新数据集只有四个数值特征（而不是八个）。

为什么是四个？因为原始数据集有八个不同的类别，可以使用四位二进制格式表示。请注意，数据点的数量（10）在转换数据时不会改变。

二进制编码最适合解决独热编码的缺点，因为它缓解了为每个唯一类别创建一个新特征而导致的维度“爆炸”。

然而，与独热编码相比，二进制编码可能导致分类数据内的信息丢失，这可能会对模型性能产生负面影响。这是因为二进制编码将分类数据压缩到更少的位中，导致类别之间的区别变得模糊。

#### 特征哈希

该技术使用哈希函数将高基数分类数据转换为固定数量的数值特征，你作为 ML 工程师可以自行选择该数量。

特征哈希高效且具有高度可扩展性，因为转换结果是一个固定大小的向量，从而控制了内存使用量。以下是其高层工作原理：

*   **输入特征。** 特征哈希函数接收一个特征值，该值可以是单词、类别或数据中任何其他可识别的属性。

*   **哈希函数应用。** 特征由哈希函数处理，该函数根据特征的值返回一个唯一的整数值（哈希值）。
