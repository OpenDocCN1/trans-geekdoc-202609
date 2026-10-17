
请看一下玻璃数据的标签。您会看到标签由整数玻璃类型组成。每一行都有一个整数，反映与该行化学测量值相关的玻璃类型。这正是 `sklearn` 逻辑回归包所需的形式：单列，包含每个不同类别的唯一标识符。

特征经过了归一化处理，但正如上一节中的 `glmnet` 代码一样，逻辑回归使用标签的方式不会从归一化中获益。

图 5.10 显示了每个玻璃类别的交叉验证误差作为惩罚参数 `C` 的函数。对于这个 `sklearn` 逻辑回归包，惩罚参数不同于我们在其他地方见到的。它是常规惩罚参数的倒数。`C` 从左向右变大。较大的 `C` 值对应于对惩罚的权重较小。正则化参数 `C` 的最佳值因玻璃类型而异。选择能为您的问题提供最佳整体性能的值。这将取决于您对每个类别性能的重视程度。

![图 5.10：使用惩罚线性回归进行玻璃分类的误分类错误率](img/c05f010.png)

**图 5.10** (#c05.xhtml#R_c05-fig-0010)：使用惩罚线性回归进行玻璃分类的误分类错误率

图 5.10 显示了误分类错误率与惩罚参数递减步数的关系图。图中显示，与图左侧边缘最简单的模型相比，在最小值处有显著改进。表现最差的类别准确率约为 70%，即错误率约为 30%。您可以尝试基扩展来改进结果。在接下来介绍集成方法的章节中，您将看到其他一些方法。

## 使用 PySpark 进行线性回归和分类

本节将重现您已经见过的几个问题，但将使用 `PySpark`，这意味着您将看到的代码示例可以在数百或数千个处理器上同时运行。这将使您能够在海量数据集上构建模型。本节将通过各种示例，向您展示如何使用 `PySpark` mllib 包解决回归、二分类和多分类问题。您将看到各种您已经熟悉的算法和分析技术：惩罚回归、变量归一化、交叉验证等。

`PySpark` 的一些计算序列乍看之下可能有点奇怪。由于 `PySpark` 旨在处理分布在多台机器上的数据，它使用可以一次处理一行数据的数据转换，无论数据存储和处理在何处。您将看到其运作方式，稍加练习，这些操作就会成为您熟悉的工具。

本节将展示四个问题：预测葡萄酒口感、将声纳目标分类为岩石或地雷、预测鲍鱼壳的年轮数、以及根据化学成分识别玻璃类型。选择这些问题是为了演练 `PySpark` 中您需要了解的几个特性。我们将在深入每个问题时讨论每个问题所突出的特性。

### 使用 PySpark 预测葡萄酒口感

第 3 章“在海量数据集上使用 PySpark 训练惩罚回归模型”一节中介绍了使用 `PySpark` 解决葡萄酒口感预测问题。本节将增加在构建模型前归一化变量的功能，以便利用系数指示变量重要性。第 3 章中该节的目的是展示 `PySpark` 代码的简洁性及其与 `sklearn` Python 代码的相似性。本节将讨论 `PySpark` 代码中的每个操作。清单 5-8 显示了使用归一化特征预测葡萄酒口感的代码。

#### 清单 5-8：使用 PySpark 惩罚回归确定葡萄酒口味预测中的变量重要性——wine_variable_importance:spark.py

```
__author__ = 'mike_bowles'

##### 导入 sparksession 
from pyspark.sql import SparkSession
from pyspark.ml.feature import VectorAssembler
from pyspark.ml.regression import LinearRegression
import matplotlib.pyplot as plt
from pyspark.ml.feature import StandardScaler
import pandas as pd
from pandas import DataFrame
from Read_Fcns import pd_read_wine

spark = SparkSession.builder.appName("regress_wine_data").getOrCreate()

##### 将鲍鱼数据作为 pandas 数据框读入并创建 Spark 数据框。
wine_df = pd_read_wine()

##### 为葡萄酒数据创建 spark 数据框
wine_sp_df = spark.createDataFrame(wine_df)
print('Column Names for initial data frame\n', wine_sp_df.columns, 
       '\n\n')

vectorAssembler = VectorAssembler(inputCols = ['fixed acidity', \
    'volatile acidity', 'citric acid', 'residual sugar', 'chlorides', \
    'free sulfur dioxide', 'total sulfur dioxide', 'density', 'pH', \
                    'sulphates', 'alcohol'], outputCol = 'features')
v_wine_df = vectorAssembler.transform(wine_sp_df)
  
##### 对特征调用 StandardScaler
scaler = StandardScaler(inputCol="features", 
     outputCol="scaledFeatures")
scalerModel = scaler.fit(v_wine_df)

##### 将每个特征归一化为单位标准差。
scaledData = scalerModel.transform(v_wine_df)

##### scaledData 包含单个原始特征以及
##### 原始特征和缩放特征的向量化版本
scaledData.show()

vwine_df = scaledData.select(['scaledFeatures', 'quality'])

splits = vwine_df.randomSplit([0.66, 0.34])
xTrain_sp = splits[0]
xTest_sp = splits[1]

##### alpha 列表 从大到小，以及用于存储结果的空列表
alphaList = [0.1**i for i in [0,1, 2, 3, 4, 5, 6]]
wt_list = []
intercept_list = []
rmsError = []

for alph in alphaList:
    wine_ridge_sp = LinearRegression(featuresCol = "scaledFeatures", \
        labelCol='quality', maxIter=100, regParam=alph, \
        elasticNetParam=0.0)
    wine_ridge_sp_model = wine_ridge_sp.fit(xTrain_sp)
    test_result = wine_ridge_sp_model.evaluate(xTest_sp)
    
    rmsError.append(test_result.rootMeanSquaredError)
    coef = wine_ridge_sp_model.coefficients.toArray()
    wt_list.append(coef)
    intercept_list.append(wine_ridge_sp_model.intercept)

print('{:18}'.format("RMS Error"), "alpha") 
for i in range(len(rmsError)):
    print(rmsError[i], alphaList[i])

##### 根据表现最佳的 alpha (index=2) 的系数幅度对属性排序

len_coef = len(wt_list[0])
ordered_idx = sorted(zip(range(len_coef), wt_list[2]), key=lambda x:
                       -abs(x[1]))
print('\n\nAttributes ordered by coef magnitude----------')
[print(wine_sp_df.columns) for (a,b) in ordered_idx]
 
 
##### 绘制样本外误差与 alpha 的曲线
x = range(len(rmsError))
plt.plot(x, rmsError, 'k')
plt.xlabel('-log(alpha)')
plt.ylabel('Error (RMS)')
plt.savefig('linear_regression_w_spark.png', dpi=500)
plt.show()

打印输出： 
Column names for initial data frame
 ['fixed acidity', 'volatile acidity', 'citric acid', 'residual sugar',
'chlorides', 'free sulfur dioxide', 'total sulfur dioxide', 'density',
'pH', 'sulphates', 'alcohol', 'quality']

Column names for transformed data set
[fixed acidity, volatile acidity, citric acid, residual sugar,
chlorides, free sulfur dioxide, total sulfur dioxide, density,
pH, sulphates, alcohol, quality, features, scaledFeatures]

Note: Printout of data frame can be seen by running Ch5 code notebook 
in this book's code repo

RMS Error          alpha
0.6464799847389207 1.0
0.6173125740380354 0.1
0.6174096728881342 0.010000000000000002
0.6178333051859206 0.0010000000000000002
0.6178884012227639 0.00010000000000000002
0.6178940680418457 1.0000000000000003e-05
0.617894636333235 1.0000000000000004e-06

Attributes ordered by coef magnitude----------
alcohol
volatile acidity
sulphates
total sulfur dioxide
chlorides
pH
free sulfur dioxide
density
citric acid
residual sugar
fixed acidity 
```

该过程的第一步是启动一个 `SparkSession`。该会话被命名为 "`regress_wine_data`"。第二步是将数据集读入 pandas 数据框，然后将其转换为 PySpark 数据框。回想一下，数据框是一个矩形数据数组，类似于矩阵，不同之处在于特定的数据框列可能与另一列不是相同的数据类型。数据框列可以是字符串变量，例如岩石与矿石数据中的标签列，其中标签为 `M` 和 `R` 分别表示矿石或岩石。在矩阵中，变量都是同一类型，通常是实数。数据框对于处理统计数据非常有用，因为数据集很少全是实数。Python 和 PySpark 都引入了数据框正是出于这个原因。

PySpark 代码中的下一个操作是 `VectorAssembler`。这需要一些解释。PySpark 采用的前提是：机器学习问题的输入示例可以被描述为一个实值特征的行向量和一个关联的标签。对于葡萄酒数据，特征都是实数，因此它们自然符合这一前提，而标签都是单个实数口味评分。标签也符合该前提。您可能会想到鲍鱼数据，其中性别属性取值为 `M`、`F` 和 `I`，或者您见过的标签不是实数的分类问题。后面的章节将展示如何转换这些情况以符合这一前提。

通常，您用于训练模型的数据可能来自一个大得多的数据框中的几列。因此，第一步是组装将用于预测的实数向量。对于葡萄酒数据，这就像将所需特征列的列标题放入一个字符串变量列表中一样简单。这就是您在 `VectorAssembler` 函数调用中看到的内容。变量 `inputCols` 被设置为特征名称列表。`VectorAssembler` 中的 `outputCol` 变量被设置为您选择的名称，用于命名将作为特征矩阵的行向量列。您将经常看到输出名称“features”。从概念上讲，PySpark 将跟踪一个名为 `features` 的行向量列。后面的示例将向您展示这些列条目的一些样本（即特征矩阵的样本行）。

现在 `VectorAssembler` 已定义，下一步是将此转换应用于原始数据框并将其分配给新数据框。新数据框将与旧数据框几乎相同，只是会添加一个名为 `features` 的新列。

下一步是标准化特征。这需要几个步骤。首先是实例化一个 `StandardScaler()` 函数（在代码中命名为 `scaler`）并定义输入和输出列。输入列是 `features`，即之前定义的行向量列。第二步是在 `VectorAssembler` 之后对数据集调用 `scaler.fit()`，以便有一个 `features` 列可供操作。`fit()` 函数会将 `features` 列中的每个单独特征转换为零均值、单位方差。在第 2 章的清单 2.11 中，你已经看到归一化操作需要遍历每一列来确定其均值和标准差，然后减去均值并除以标准差。`fit()` 函数计算均值和标准差，而 `transform()` 函数执行减法和除法运算。这些操作的结果显示在清单 5-8 的输出部分。最终 `scaledData` 数据帧的列标题显示了 `features` 和 `scaledFeatures` 列。显示的输出不包含任何实际的特征值。输出过于繁杂，无法以页面格式打印。你可以通过运行 Jupyter Notebook 生成输出，该 Notebook 可在本书的代码仓库中找到。

现在数据已标准化，拟合 ElasticNet 惩罚线性模型的其余过程相当直接：首先定义训练-测试集划分，然后选择一系列惩罚参数。惩罚参数作为 0.1 的幂次生成。ElasticNet 参数选为 0.0，这给出了岭回归。运行完流程后，样本外 MSE 表表明索引为 2 的惩罚参数是最佳选择。（注意，由于随机训练-测试划分的不同，该值会略有波动。）所有系数都已存储，因此使用索引 2 对应的系数集对特征进行排序并打印结果（图 5.11）。

![图 5.11：PySpark 模型性能与正则化参数的关系](img/c05f011.png)

**图 5.11**：PySpark 模型性能与正则化参数的关系

本示例中模型构建过程的总体流程应该很熟悉，类似于你迄今为止看到的 Python 示例。新元素是使用 PySpark 执行这些熟悉操作的机制和语法。此处的示例实现了特征标准化，部分原因是这是一个你可能想要使用的过程，部分是为了说明在 PySpark 中对数据执行一系列转换的过程是如何工作的。下一节将介绍我们的基本二分类示例：岩石与地雷。

### 使用 PySpark 进行逻辑回归：岩石与地雷

本节将介绍一个与上一节非常相似的过程。它将包括用于生成 `features` 列的 `VectorAssembler` 等。会有几个不同之处。它将使用 `LogisticRegression` 包而不是 `LinearRegression` 包。它将使用 `StringIndexer` 将岩石与地雷问题中的 `M` 和 `R` 转换为 PySpark `LogisticRegression` 所需的分类标签。最后，此处的代码将使用 PySpark Pipeline 框架来完成所需的转换序列。在前一个示例中，转换是一次应用一步，命名生成的数据帧，然后用于下一步。这可能会变得有些重复。Pipeline 框架使流程更加整洁。

第一步与之前相同：启动 PySpark 会话，将数据读入 pandas 数据帧，将其转换为 PySpark 数据帧，并生成一个列名列表，这些列名将作为特征传递给 `VectorAssembler`。然后是 `StringIndexer`。

`StringIndexer` 作用于标签列 `V60`。它将 `M` 和 `R` 转换为 0 和 1。`StringIndexer` 作用于字符串值。它确定有多少个唯一值，并从 0 开始为数量最多的值分配索引编号，然后按数量从多到少的顺序继续向下分配。在本例中，两个类别的样本量相同。

使用 Pipeline 框架需要定义一系列定义步骤顺序的“阶段”。这些阶段累积在一个列表中。列表中的第一个操作是 `StringIndexer` 的实例化，在清单 5-9 中称为 `label_string_idx`。第二个是 `VectorAssembler` 的实例化，它组装了特征列 `V0` 到 `V59`。

接下来，创建 `pipeline` 作为 `Pipeline` 类的实例。对其应用 `fit()` 以学习字符串索引。如果包含标准化，那也将作为 fit 过程的一部分完成。拟合后的模型称为 `pipelineModel`，然后用于转换输入数据。为最终数据帧选择的列以模式形式打印，打印输出显示了来自字符串索引器的标签、向量化特征以及为简洁起见被截断的原始变量。你可以通过运行本书代码仓库中的 Jupyter Notebook 获取完整列表。
