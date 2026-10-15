
train`_`test`_`split : 这是 sklearn.model`_`selection 模块中的一个函数，用于将数据集划分为训练集和测试集。X`_`train 和 y`_`train 用于训练模型，X`_`test 和 y`_`test 用于在未见数据上评估模型的性能。

Components of the Function Call :

X: 这是特征矩阵（输入变量）。它包含独立变量或预测器。

y: 这是目标向量（输出变量）。它包含因变量或响应变量。

test`_`size=0.2: 该参数指定要包含在测试集中的数据集比例。这里，0.2 表示 20% 的数据将用于测试，剩余 80% 用于训练。

random`_`state=0: 该参数控制在将数据划分前对数据进行洗牌的操作。传入整数可确保分割的可重复性，即每次使用相同的 random`_`state 值运行代码时，数据划分结果相同。

Output of the Function Call :

X`_`train: 这是特征矩阵的训练子集。包含 X 中 80% 的行。

X`_`test: 这是特征矩阵的测试子集。包含 X 中剩余的 20% 的行。

y`_`train: 这是目标向量的训练子集。包含与 X`_`train 中行对应的 y 中 80% 的行。

y`_`test: 这是目标向量的测试子集。包含与 X`_`test 中行对应的 y 中 20% 的行。

通过使用 test`_`size=0.2，我们确保 20% 的数据被保留用于测试，这有助于评估模型在新数据上的泛化能力。random`_`state 确保数据划分是可重复的，从而在多次运行代码时保持结果一致。

# Training the model

Figure 2-33  说明了如何使用 X`_`train 和 y`_`train 数据集训练机器学习模型。执行结果表明模型已成功训练。

![](OEBPS/image_rsrc52Z.jpg)

Figure 2-33 .

# Code Explanation

lr = LinearRegression()

这一行创建 LinearRegression 类的实例并将其赋值给变量 lr。

实例 lr 将用于将模型拟合到训练数据并进行预测。

lr.fit(X`_`train, y`_`train)

fit: 该方法在训练数据上训练线性回归模型。

X`_`train: 训练数据的特征矩阵，包含独立变量。

y`_`train: 训练数据的目标向量，包含因变量。

运行此代码后，lr 实例包含已训练好的线性回归模型，可通过 predict 方法对新数据进行预测。

# Predicting with the test data

Figure 2-34  展示了如何使用已训练好的模型 (lr) 和测试数据 (X`_`test) 进行预测。

![](OEBPS/image_rsrc530.jpg)

Figure 2-34

# Code Explanation

y`_`pred = lr.predict(X`_`test) :

此代码使用已训练好的线性回归模型 (lr) 对测试数据 (X`_`test) 的因变量值进行预测。预测结果存储在变量 y`_`pred 中。

predict 方法将在训练阶段学习到的关系应用于测试数据，生成这些预测，从而提供模型在未见数据上的性能估计。

# Model Evaluation

在训练机器学习模型后，通过检查 R² 分数来评估其性能是很重要的。R² 分数表示模型在训练数据上的拟合程度，如 Figure 2-35 所示。

![](OEBPS/image_rsrc531.jpg)

Figure 2-35.

# Code Explanation

r2`_`score(y`_`test, y`_`pred)

R² 分数，也称为决定系数，用于衡量模型预测值与实际值之间的匹配程度。

y`_`test: 测试数据集中因变量的实际观测值。这是我们试图预测的真实输出。

y`_`pred: 训练好的模型对测试数据集 (X`_`test) 生成的因变量预测值。

# Model Result Interpretation

输出 0.7999876970680433 表示大约 80% 的因变量 (y`_`test) 的变异可以通过训练好的模型利用独立变量 (X`_`test) 来预测。  

这表明模型拟合良好，因为模型解释了大部分变异。

# Let’s make a prediction

Figure 2-36  展示了如何使用已训练的机器学习模型进行预测。我们需要提供以下特征进行预测：sex , smoker , region , age , BMI , and number of children，这些特征与训练时使用的特征相同。这些特征作为输入传递给 predict 方法，模型据此返回基于这些特征的预测目标变量值。

![](OEBPS/image_rsrc532.jpg)

Figure 2-36.

# Support Vector Regression

Support Vector Regression (SVR) 是一种高度有效且灵活的机器学习方法，常用于解决各种回归问题。其独特的设计使其能够通过确定最佳回归线来管理复杂的回归任务，该回归线准确反映输入变量和输出变量之间的关系。

使用以下链接下载数据集：[Insurance Dataset](https://www.google.com/url?q=https://www.kaggle.com/datasets/awaiskaggler/insurance-csv&sa=D&source=editors&ust=1720099681753988&usg=AOvVaw1qEmRxFcDWzY9jJAm9EsET) 。源代码在此：[Support Vector Regression](https://www.google.com/url?q=https://github.com/anyasorc/appliedml/blob/main/Medical_Insurance_Multiple_Linear_Reg.ipynb&sa=D&source=editors&ust=1720099681754452&usg=AOvVaw2p0VIxTh5aYts45SQmqlOd)  

# Import Libraries

Figure 2-37  展示了所有导入的必需库。

![](OEBPS/image_rsrc533.jpg)

Figure 2-37.

Import and View Data

Figure 2-38   展示了数据的导入和查看过程，如下所示。

![](OEBPS/image_rsrc534.jpg)

Figure 2-38.

# Calculating the frequency of unique values in a DataFrame column named 'region'.

代码 df.region.value`_`counts()  计算 DataFrame df 中 'region' 列的每个唯一值的频率，并显示每个 region 出现的次数。'smokers' 列的处理方式相同，如 Figure 2-39 所示。

![](OEBPS/image_rsrc535.jpg)

Figure 2-39.

# Check for missing values

代码 df.isna().sum() 是一系列方法的组合，用于计算 DataFrame df 中每列的缺失值（NaN）总数，如 Figure 2-40 所示。

![](OEBPS/image_rsrc536.jpg)

Figure 2-40.

# Assign values to X and y

X = df.iloc`[:, :-1]`.values:

此行选择 df 中的所有行和除最后一列外的所有列，并将结果转换为 NumPy 数组。 resulting array X 通常包含特征或预测器，如 Figure 2-41 所示。

y = df.iloc`[:, -1]`.values:

此行选择 df 中的所有行和仅最后一列，并将结果转换为 NumPy 数组。 resulting array y 通常包含目标或响应变量，如 Figure 2-41 所示。

![](OEBPS/image_rsrc529.jpg)

Figure 2-41

# View data in X

在新的代码单元中输入 X 并运行代码，可以查看 X 中赋值的数据，如 Figure 2-42 所示。y 也可以同理处理。

![](OEBPS/image_rsrc52T.jpg)

Figure 2-42 . 我已标记列及其对应的索引位置：第一列 Age 在索引位置 0；第二列 Sex 在索引位置 1；第三列 BMI 在索引位置 2；第四列 Number of Children 在索引位置 3；第五列 Smoker 在索引位置 4；第六列 Region 在索引位置 5。

# Addressing missing values (NaN)
