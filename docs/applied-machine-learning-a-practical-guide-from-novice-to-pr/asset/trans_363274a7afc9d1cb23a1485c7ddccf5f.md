
-   [核心参数 `kernel='rbf'`：该参数指定算法使用的核函数类型。`'rbf'` 代表径向基函数（Radial Basis Function），是一种常用于处理特征与目标变量之间非线性关系的核。RBF 核会将输入特征映射到更高维空间，从而在该空间中可以找到线性分离，使其能够有效捕获复杂模式。]

![](OEBPS/image_rsrc53E.jpg)

-   [fit(X_train, y_train)：该方法用于使用训练数据训练 SVR 模型。`X_train` 包含输入特征，`y_train` 包含对应的目标值。  

    在拟合过程中，SVR 算法通过寻找最佳超平面（或决策边界），在指定的容差（epsilon-insensitive 区间）内使数据最佳拟合，从而学习输入特征与目标变量之间的关系。]

![](OEBPS/image_rsrc53F.jpg)

# 使用测试数据进行预测

Figure 2-49  下面的图示了如何使用已训练好的模型（回归器）和测试数据（X_test）进行预测。

![](OEBPS/image_rsrc53F.jpg)

Figure 2-49.

# 代码说明

![](OEBPS/image_rsrc53G.jpg)

-   [sc_X.transform(X_test)：将与训练数据 X_train 相同的标准化过程应用于测试数据 X_test。  

    `sc_X` 是一个 `StandardScaler` 实例，之前已在 X_train 上拟合。这样可以确保 X_test 使用与训练数据相同的均值和标准差进行标准化，使特征保持相同的尺度。]

![](OEBPS/image_rsrc53H.jpg)

-   [regressor.predict(...)：使用已训练好的 SVR 模型对标准化后的测试数据进行预测。  

    这一步的输出是一个一维数组，包含预测的目标值，但这些预测仍然处于训练时使用的标准化尺度。]

![](OEBPS/image_rsrc53J.jpg)

-   [.reshape(-1, 1)：将预测值数组 reshape 为二维数组，列数为 1。`-1` 参数会自动推断行数，基于数组长度。  

    这种 reshaping 是必要的，因为 `StandardScaler` 的 `inverse_transform` 方法要求输入为二维数组。]

![](OEBPS/image_rsrc53K.jpg)

-   [sc_y.inverse_transform(...)：将标准化后的预测值转换回目标变量 y 的原始尺度。  

    `sc_y` 是一个 `StandardScaler` 实例，之前已在 y_train 上拟合。`inverse_transform` 方法撤销标准化，将标准化后的值恢复到原始尺度。]

![](OEBPS/image_rsrc53M.jpg)

-   [最终结果 y_pred 是一个数组，包含针对 X_test 的预测目标值，已转换回 y 的原始尺度。]

# 模型评估

训练机器学习模型后，评估其性能非常重要，常用指标是 R² 分数（R² score）。R² 分数反映了模型在训练数据上的拟合程度，如 Figure 2-50 所示。

![](OEBPS/image_rsrc53N.jpg)

Figure 2-50.

# 代码说明

![](OEBPS/image_rsrc53P.jpg)

-   [r2_score 是 scikit-learn 库 `sklearn.metrics` 模块中的函数。  

    它用于通过计算决定系数（R-squared，R²）来评估回归模型的性能。]

-   [y_test 表示测试数据集的真实目标值，即模型试图预测的实际值。]

-   [y_pred 表示回归模型为测试数据集生成的预测目标值。]

# 模型结果解释

R² 值为 0.8869590298175918，约为 88.70%，这表明 SVR 模型表现非常出色，能够捕获目标变量的大部分变异。

这表明模型对给定的回归问题有效且准确，能够基于输入特征提供可靠的预测。

# 让我们进行预测

Figure 2-51  下面的图示了使用已训练机器学习模型进行预测的过程。预测时需要提供以下特征：sex、smoker、region、age、BMI、children 数量，这些特征与模型训练时使用的特征相同。

这些特征作为输入传递给 predict 方法，模型据此返回基于这些特征的预测目标变量值。

![](OEBPS/image_rsrc53R.jpg)

Figure 2-51.

# 决策树回归

决策树回归是一种强大且广泛使用的机器学习技术，用于解决回归问题。其简洁性、可解释性以及捕获复杂关系的能力，使其在需要精确数值预测的各种领域中成为有价值的工具。

使用以下链接下载数据集：[保险数据集](https://www.google.com/url?q=https://www.kaggle.com/datasets/awaiskaggler/insurance-csv&sa=D&source=editors&ust=1720099681775664&usg=AOvVaw1E2aDWzbH0fM19H9MRpxm9) 。源代码在此：[决策树回归](https://www.google.com/url?q=https://github.com/anyasorc/appliedml/blob/main/Master_Class_Decision_Tree_Medical_Insurance%2520\(1\).ipynb&sa=D&source=editors&ust=1720099681776132&usg=AOvVaw24p7irzhaxnJ2mjY2KLZfZ) 

# 导入库

Figure 2-52  显示了所有必要的导入库。

![](OEBPS/image_rsrc53S.jpg)

Figure 2-52.

# 导入并查看数据

Figure 2-53  展示了如何导入并查看数据。

![](OEBPS/image_rsrc53T.jpg)

Figure 2-53.

# 计算 'region' 列中唯一值的频率

代码 `df.region.value_counts()` 计算 DataFrame `df` 中 `region` 列每个唯一值的出现次数，显示每个地区出现的次数。同样，也可以对 `smoker` 特征使用该方法，如 Figure 2-54 所示。

![](OEBPS/image_rsrc53U.jpg)

Figure 2-54.

# 检查缺失值

代码 `df.isna().sum()` 是一系列方法的组合，用于计算 DataFrame `df` 每列的缺失值（NaN）总数，如 Figure 2-55 所示。

![](OEBPS/image_rsrc53V.jpg)

Figure 2-55.

# 为 X 和 y 赋值

-   [X = df.iloc[:, :-1].values：该行选取 DataFrame `df` 的所有行和除最后一列之外的所有列，并将结果转换为 NumPy 数组。得到的数组 X 通常包含特征或预测器，如 Figure 2-56 所示。]

-   [y = df.iloc[:, -1].values：该行选取 DataFrame `df` 的所有行和仅最后一列，并将结果转换为 NumPy 数组。得到的数组 y 通常包含目标或响应变量，如 Figure 2-56 所示。]

![](OEBPS/image_rsrc529.jpg)

Figure 2-56.

# 查看 X 中的数据

在新建代码单元格中输入并运行 `X` 以查看分配给 X 的数据，如 Figure 2-57 所示。y 也可以同理查看。

![](OEBPS/image_rsrc52T.jpg)Figure 2-57: 我已为列标记其对应的索引位置：第一列 Age 位于索引 0；第二列 Sex 位于索引 1；第三列 BMI 位于索引 2；第四列 Number of Children 位于索引 3；第五列 Smoker 位于索引 4；第六列 Region 位于索引 5。

# 处理缺失值（NaN）

处理缺失值对于数值特征/列是相关的，如 Figure 2-58 所示。我们选择了索引位置为 0、2、3 的特征/列，即 Age、BMI 和 Number of Children，如 Figure 2-57 所示。

![](OEBPS/image_rsrc53W.jpg)

Figure 2-58. `X[:, [0, 2, 3]]` 表示“选择所有行和索引位置 0、2、3 的列”。因此，`X[:, [0, 2, 3]]` 有效提取 Age、BMI 和 Number of Children 列的所有行。

在确定数值列后，我们将使用 `SimpleImputer` 类计算每列的均值，并用这些均值替换缺失值，如 Figure 2-59 所示。

![](OEBPS/image_rsrc52V.jpg)

Figure 2-59.
