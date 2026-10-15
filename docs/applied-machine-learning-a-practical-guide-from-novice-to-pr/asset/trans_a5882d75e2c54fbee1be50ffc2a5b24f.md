
预测目标变量：经过转换的特征随后传递给已训练的回归模型 `lr` 的 `lr.predict` 方法，用于预测目标变量。

# 多元线性回归

多元线性回归通过建模依赖变量（也称为目标变量或响应变量）与多个自变量（也称为预测器或特征）之间的关系，扩展了简单线性回归的原理。虽然简单线性回归仅考虑一个预测器，多元线性回归则纳入两个或更多的预测器，从而提供了更全面的分析，说明各种因素如何共同影响依赖变量。

在数据科学中，该方法对于理解和量化多个变量对目标结果的影响至关重要。通过考虑多个预测器，多元线性回归能够实现更准确的预测，并提供对数据中复杂关系的洞察。

使用以下链接下载数据集：[保险数据集](https://www.google.com/url?q=https://www.kaggle.com/datasets/awaiskaggler/insurance-csv&sa=D&source=editors&ust=1720099681734560&usg=AOvVaw3TzaCJRNZGrbHq9PreHILr)。源代码可在此查看：[多元线性回归](https://www.google.com/url?q=https://github.com/anyasorc/appliedml/blob/main/Medical_Insurance_Multiple_Linear_Reg.ipynb&sa=D&source=editors&ust=1720099681734846&usg=AOvVaw0jy2PLIOHE3Kh20p1ZKiiS)

# 导入库

图 2-24 显示了所有必要的导入库。

![](OEBPS/image_rsrc52M.jpg)

图 2-24。

# 导入并查看数据

图 2-25 展示了数据的导入和查看方式，如下所示。

![](OEBPS/image_rsrc52N.jpg)

图 2-25。

# 统计 DataFrame 中 'region' 列唯一值的频率

代码 `df.region.value_counts()` 用于计算 DataFrame `df` 中 `region` 列每个唯一值的频率，显示每个地区出现的次数。如图 2-26 所示，该方法同样适用于 `smoker` 特征。

![](OEBPS/image_rsrc52P.jpg)

图 2-26。

# 检查缺失值

代码 `df.isna().sum()` 是一系列方法的链式调用，用于计算 DataFrame `df` 中每列的缺失值（NaN）总数，如图 2-27 所示。

![](OEBPS/image_rsrc52R.jpg)

图 2-27。

# 为 X 和 y 赋值

`X = df.iloc[:, :-1].values:`

此行选择 DataFrame `df` 的所有行和除最后一列之外的所有列，并将结果转换为 NumPy 数组。得到的数组 `X` 通常包含特征或预测器，如图 2-28 所示。

`y = df.iloc[:, -1].values:`

此行选择 DataFrame `df` 的所有行和仅最后一列，并将结果转换为 NumPy 数组。得到的数组 `y` 通常包含目标或响应变量，如图 2-28 所示。

![](OEBPS/image_rsrc52S.jpg)

图 2-28

# 查看 X 中的数据

在新代码单元中输入 `X` 并运行，即可查看已赋值给 `X` 的数据，如图 2-29 所示。对 `y` 也可如此操作。

![](OEBPS/image_rsrc52T.jpg)

在图 2-29 中，我为列标记了对应的索引位置：第一列 `Age` 位于索引位置 0；第二列 `Sex` 位于索引位置 1；第三列 `BMI` 位于索引位置 2；第四列 `Number of Children` 位于索引位置 3；第五列 `Smoker` 位于索引位置 4；第六列 `Region` 位于索引位置 5。

# 处理缺失值（NaN）

处理缺失值对于数值特征/列是相关的，如图 2-30 所示。我们选择了索引位置为 0、2、3 的特征/列，对应于 `Age`、`BMI` 和 `Number of Children`，如图 2-29 所示。

![](OEBPS/image_rsrc52U.jpg)

图 2-30. `X[:, [0, 2, 3]]` 的含义是“选择所有行和索引位置为 0、2、3 的列”。因此，`X[:, [0, 2, 3]]` 有效提取 `Age`、`BMI` 和 `Number of Children` 列/特征的所有行数据。

在识别出数值列后，我们将使用 `SimpleImputer` 类计算每列的均值，并用这些均值替换缺失值，如图 2-31 所示。

![](OEBPS/image_rsrc52V.jpg)

图 2-31.

# 代码说明

`SimpleImputer(missing_values=np.nan, strategy='mean')`

`missing_values=np.nan`: 该参数指定要 impute（填补）的缺失值由 `np.nan` 表示。

`strategy='mean'`: 该参数指定缺失值应替换为其所在列的均值。

`imp.fit(X[:, [0, 2, 3]])`

`X[:, [0, 2, 3]]`: 从数组 `X` 中选择所有行和索引位置为 0、2、3 的列。这些列为数值型。

`.fit(...)`: 该方法基于非缺失值计算每列的均值，并将这些均值存储以供后续使用。

`np.set_printoptions(precision=2)`

该函数用于配置 NumPy 数组的显示方式。此处将打印输出的精度设置为 2 位小数。

`X[:, [0, 2, 3]] = imp.transform(X[:, [0, 2, 3]])`

`X[:, [0, 2, 3]]`: 再次选择从数组 `X` 中所有行和索引位置为 0、2、3 的列。

`imp.transform(...)`: 该方法将在 `.fit(...)` 步骤中计算的均值替换选定列中的缺失值。

`X[:, [0, 2, 3]] = ...`: 此赋值将更新原始数组 `X` 中的选定列，使其包含已用均值替换缺失值的转换后数据。

# ColumnTransformer 和 OneHotEncoder()

机器学习模型本质上不理解文本或 categorical（类别）值，因此需要将它们转换为模型能够处理的数值表示。这就是为什么我们需要将图 2-29 中索引位置 1（`Sex`）、4（`Smoker`）和 5（`Region`）的类别变量进行转换的原因。为此，我们将使用 `ColumnTransformer` 和 `OneHotEncoder`，如图 2-32 所示。

![](OEBPS/image_rsrc52W.jpg)

图 2-32.

# 代码说明

`ColumnTransformer`: 来自 `sklearn.compose` 模块的类，用于对数据集的不同列应用不同的预处理转换。

`OneHotEncoder`: 来自 `sklearn.preprocessing` 模块的类，用于将类别特征转换为可以供机器学习算法使用的数值格式。

`np`: 通常用于 NumPy 库的别名，用于进行数组操作。

创建 ColumnTransformer 实例

![](OEBPS/image_rsrc52X.jpg)

`ColumnTransformer(...)`:

初始化 `ColumnTransformer` 对象，用于对特定列应用指定的转换。

`transformers=[('encoder', OneHotEncoder(), [1, 4, 5])]`:

`'encoder':` 为该转换器指定的名称，可以是任意字符串。

`OneHotEncoder()`: 指定使用 `OneHotEncoder` 进行转换。

`[1, 4, 5]`: 指定用于转换的列的索引位置列表。此处，索引位置为 1、4、5 的列将被一热编码。

`remainder='passthrough'`:

该参数指定未明确转换的列应如何处理。`passthrough` 表示这些列保持不变，直接包含在输出中。

# 分割训练集和测试集

我们需要使用 80:20 的比例将数据集划分为训练集和测试集。这意味着 80% 的数据用于训练模型，剩余的 20% 用于在未见过的数据上评估模型的性能。图 2-32 描绘了这一过程。

![](OEBPS/image_rsrc52Y.jpg)

图 2-32.

