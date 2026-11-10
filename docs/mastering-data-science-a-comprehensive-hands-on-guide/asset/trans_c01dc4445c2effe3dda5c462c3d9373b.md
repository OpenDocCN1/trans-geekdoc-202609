
# 数据转换与编码

数据转换和编码是在为分析或机器学习准备数据时必不可少的步骤。这些过程对数据进行标准化、规范化或重新格式化，使其适用于分析工具和模型。在数据科学的背景下，“data encoding”是指将分类数据——例如文本或非数值值——转换为机器学习算法可以处理的数值格式。这种转换是必要的，因为算法只能在数值数据中识别模式和关系，这使得编码成为数据在用于机器学习模型之前的数据预处理管道中的关键步骤。

简而言之，数据编码将分类变量转换为机器学习算法可以处理的数值格式。

目的是使主要处理数值的机器学习算法能够通过将每个类别映射为数值来处理分类数据 such as "gender" (male/female) 或 "color" (red/blue/green)。

## 常见编码技术

- One-hot encoding: 为每个类别创建新的二进制列，其中仅相关类别设为 1，其他为 0。
- Label encoding: 每个唯一类别获得一个唯一的数值，但这仅在类别之间存在固有顺序时才进行（ordinal data）。
- Mean encoding: 用该类别目标变量的平均值替换每个类别。

这是数据准备中的关键步骤之一，以确保机器学习模型正确学习分类数据中的特征。

## 12.4 编码技术

### 12.4.1 One-Hot Encoding

在数据科学中，“one hot encoding”是一种将分类数据——例如颜色（red, green, blue）——转换为机器学习算法可以解释的数值格式的技术。本质上，它将类别转换为二进制列。

该过程为每个唯一类别创建新的二进制列，其中每个数据点只有一个列被标记为“hot”（值为 1），表示该类别的存在。所有其他列保持为 0，表示其缺失。这样，one hot encoding 将分类变量转换为每个类别作为单独二进制特征表示的格式。此方法使机器学习模型能够通过将其编码为数值来处理分类数据。

例如，如果你有一个“color”特征，其类别为“red”、“green”和“blue”，one hot encoding 将创建三个新列：`is_red`、`is_green`和`is_blue`。

示例：

Input: `["Red", "Green", "Blue"]`

Output:
Red  Green  Blue
1    0      0
0    1      0
0    0      1

Example in Python:
```python
from sklearn.preprocessing import OneHotEncoder

# One-hot encode
encoder = OneHotEncoder(sparse=False)
encoded_data = encoder.fit_transform(df[['Feature1']])
print(encoded_data)
```

### 12.4.2 Label Encoding

在数据科学中，Label Encoding 是一种通过为每个不同类别分配唯一整数将分类数据，例如文本标签，转换为数值表示的技术。此方法使机器学习算法能够有效地处理分类特征。Label encoding 提供了一种简单的方法来将分类数据转换为可由仅接受数值输入的模型使用的格式。本质上，它为每个类别分配唯一整数，促进了分类数据在机器学习模型中的使用。

与 Label Encoding 相关的要点：
- 用唯一整数替换分类变量中的每个唯一类别。
- 最适用于类别之间没有固有顺序或等级的标称分类数据。
- Label encoding 应该仅用于具有自然顺序（ordinal data）的分类数据，因为将其应用于无序类别可能会创建误导性的层级，从而混淆模型。对于标称分类数据，one-hot encoding 通常是更好的选择。

示例：

如果有一个特征名为“color”，其类别为“red”、“green”和“blue”，则 Label Encoding 可能分别将其编码为 0、1 和 2。

重要注意事项：Label Encoding 可以应用于序数和标称数据，但必须注意该技术假设类别之间没有内在顺序。当处理具有有意义顺序的序数数据，例如“small”、“medium”和“large”时，这一假设可能存在问题。此外，Label Encoding 在与基于距离的算法一起使用时可能会引起问题，例如 K-Nearest Neighbors (KNN)。Label Encoding 分配的任意数值可能导致算法计算中出现误导性模式，影响结果质量。

示例：

Input: `["Red", "Green", "Blue"]`

Output: `[0, 1, 2]`

Example in Python:
```python
from sklearn.preprocessing import LabelEncoder

# Label encode
encoder = LabelEncoder()
df['Encoded_Color'] = encoder.fit_transform(['Red', 'Green', 'Blue'])
print(df)
```

### 12.4.3 Frequency Encoding

在数据科学中，称为“frequency encoding”的技术涉及用该类别在数据集中的出现频率替换分类变量中的每个类别。本质上，此方法根据类别出现的频率为每个类别分配数值。换句话说，类别被其出现的频率所替代。

也称为“count encoding”，此方法在处理机器学习模型的分类特征时特别有用，其中更频繁的类别往往具有更大的影响。该过程通过计算数据集中每个类别的频率，然后用相应的频率值替换类别来工作。

Frequency encoding 易于实现，并且在类别频率为目标变量提供有用见解时尤其有益。它有助于降低维度，特别是对于基数高的特征。然而，当类别频率对目标变量没有信息价值时，此方法可能无效，并且可能对不平衡的类别分布敏感。

示例：

考虑一个数据集，其中包含一个“city”特征，其类别例如“New York”、“Los Angeles”、“Chicago”和“Miami”。使用 frequency encoding，类别“New York”在数据中出现 20%，将被分配 0.2 的值。同样，“Miami”出现 5% 的时间，将被分配 0.05 的值。此方法根据每个类别出现的频率将分类数据转换为数值。

Example in Python:
```python
# Frequency encoding
df['Category_Frequency'] = df['Feature1'].map(df['Feature1'].value_counts())
print(df)
```

### 12.4.4 Ordinal Encoding

在数据科学中，ordinal encoding 是一种通过为每个类别分配唯一整数同时保留类别之间固有顺序或等级关系，将分类数据转换为数值值的技术。本质上，这意味着为存在明确层级的分类数据分配数值，例如“small”、“medium”和“large”，其中“small”将被分配比“large”更低的值。简而言之，它根据类别的顺序或等级进行编码。

与其它编码技术不同，ordinal encoding 保持了类别之间的自然顺序，当类别的顺序对分析很重要时，这一点至关重要。此编码方法对于具有自然层级或顺序的分类变量特别有用，例如衬衫尺码（small, medium, large）、教育水平（high school, bachelor's, master's）或信用等级（poor, fair, good）。
