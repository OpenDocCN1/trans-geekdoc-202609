
然而，序数编码不适用于类别之间不存在自然顺序的分类变量。例如，对于红色、蓝色和绿色等颜色差异，使用序数编码可能导致误表示。如果类别之间的关系不是线性的，应用序数编码可能会导致机器学习模型做出错误的推断。

### 示例
如果您有一个分类变量 `quality`，其类别为 "low"、"medium" 和 "high"，序数编码可能会分别分配值 1、2 和 3，表示 "high" 被认为比 "medium" 质量更高。

### 示例
输入: `["Low", "Medium", "High"]`
输出: `[0, 1, 2]`

### Python 中的示例
```
from sklearn.preprocessing import OrdinalEncoder

# Ordinal encoding
ordinal_data = ['Low', 'Medium', 'High']
encoder = OrdinalEncoder(categories=[['Low', 'Medium', 'High']])
encoded_data = encoder.fit_transform([[cat] for cat in ordinal_data])
print(encoded_data)
```

## 12.4.5 各类编码技术的比较
| 编码技术 | 描述 | 优点 | 缺点 | 用例 |
| --- | --- | --- | --- | --- |
| One-Hot Encoding | 将每个类别转换为二进制列（0 或 1）。 | - 无序数假设。 - 在处理许多特征的机器学习算法中效果良好。 | - 对于高基数特征会显著增加维度。 | 无序数关系的分类变量。 |
| Label Encoding | 为每个类别分配唯一的整数。 | - 简单易实现。 - 保持数据紧凑。 | - 暗示序数关系，可能误导某些模型。 | 如随机森林之类的树基算法。 |
| Frequency Encoding | 用数据集中出现的频率替换类别。 | - 保持数据紧凑。 - 反映类别分布。 | - 可能失去可解释性。 - 如果频率与目标不相关则用处不大。 | 大型分类数据集。 |
| Ordinal Encoding | 根据类别的自然顺序分配整数。 | - 保留序数关系。 - 简单易实现。 | - 需要正确排序类别。 - 如果顺序无意义可能误导模型。 | 具有有意义顺序的分类变量。 |
| Target Encoding | 用每个类别的目标变量均值替换类别。 | - 编码了与目标的关系信息。 - 降低维度。 | - 若处理不当易导致数据泄漏。 - 在小数据集中可能过拟合。 | 预测建模任务。 |
| Binary Encoding | 使用比独热编码更少的列将类别转换为二进制格式。 | - 相比独热编码降低维度。 - 处理高基数更好。 | - 编码列的解释可能具有挑战性。 | 高基数分类数据。 |
| Hashing Encoding | 使用哈希函数将类别映射为整数，通常具有固定数量的输出列。 | - 无论基数如何输出大小固定。 - 对大型数据集高效。 | - 可能发生哈希冲突。 - 失去可解释性。 | 大规模数据预处理管道。 |

**要点：**
- `One-Hot Encoding` 是名义数据的首选方法，但在高基数变量上应避免使用，因为会导致维度爆炸。
- `Label Encoding` 对树基模型效果良好，但不适合对序数关系敏感的模型，如线性回归。
- `Target Encoding` 对预测任务非常有效，但必须谨慎处理以避免数据泄漏。
- `Frequency Encoding` 和 `Binary Encoding` 适用于需要最小化维度的高基数数据集。
- `Hashing Encoding` 对流数据或非常大的数据集有用，但牺牲了可解释性。

根据数据的性质、机器学习算法和具体问题要求选择编码技术。

## 12.4.6 处理缺失或复杂类别
为了有效处理缺失的分类数据，一种方法是使用占位符（如 "Unknown"）或该类别中最频繁的值来替换缺失值。这种方法确保数据集保持完整，可用于分析或建模，而不会引入显著的偏差或错误。

另一种有用的技术是目标编码，它涉及用每个类别对应的目标变量均值替换类别。目标编码在预测建模中特别有益，因为它保留了分类变量与目标变量之间的关系，使模型能够有效利用此信息。

### 示例
```
# Target encoding
target_mean = df.groupby('Feature1')['Target'].mean()
df['Target_Encoded'] = df['Feature1'].map(target_mean)
```

# 12.5 数据转换和编码的应用
标准化通常用于支持向量机（`SVM`）和逻辑回归等算法中，有助于将所有特征带到共同的尺度。另一方面，`One-Hot Encoding` 对于决策树和线性回归等算法理想，这些算法需要以数值格式表示分类特征而不引入任何序数关系。对数变换对于减少数据集中的偏斜很有用，尤其是在财务数据或计数中，使分布更适合分析和建模。

### 最佳实践
为了确保有效的数据预处理，重要的是通过分析特征的分布和性质来理解数据。使用 `Scikit-learn` 管道可以通过将转换和编码步骤组合成单个管道来简化流程，使工作流程更高效且可重复。避免数据泄漏也很重要，这意味着在模型训练期间转换应仅使用训练数据执行。最后，测试多种方法是一种良好的实践，以尝试不同的转换和编码来确定最适合您模型的方案。

总之，数据转换和编码是准备原始数据以进行分析和建模的基本预处理步骤。通过选择适当的转换和编码方法，数据可以正确格式化、无偏见并针对机器学习算法进行定制。这最终增强了模型的性能，并确保数据被有效使用以得出有意义的见解。

# 12.6 实战：使用 pandas 预处理数据
数据预处理几乎是每个数据分析或机器学习工作流程中的重要步骤。`Pandas` 是一个强大的 Python 库，可促进高效的数据处理和准备。本教程涵盖了常见的预处理任务，例如管理缺失值、转换数据和编码分类特征，所有这些使用 `pandas` 都变得更简单高效。

### 加载数据
`Pandas` 使从 CSV、Excel 和数据库等各种来源加载数据变得容易。

#### 示例
```
import pandas as pd

# Load CSV data
df = pd.read_csv("data.csv")
print(df.head())
```

### 处理缺失值
#### 识别缺失数据
使用 `isnull()` 方法检测缺失值。
```
print(df.isnull())  # Boolean mask
print(df.isnull().sum())  # Count of missing values per column
```

#### 删除缺失值
使用 `dropna()` 删除包含缺失数据的行或列。
```
df_cleaned = df.dropna()  # Drop rows with missing values
df_cleaned = df.dropna(axis=1)  # Drop columns with missing values
```

#### 插补缺失值
使用 `fillna()` 用默认值或计算值替换缺失值。
```
df['Column1'].fillna(df['Column1'].mean(), inplace=True)  # Fill with mean
df['Column2'].fillna("Unknown", inplace=True)  # Fill with a placeholder
```

### 数据转换
缩放数据
