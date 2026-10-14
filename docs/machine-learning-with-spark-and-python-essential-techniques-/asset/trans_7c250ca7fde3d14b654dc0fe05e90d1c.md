

#### [清单 5.10](#c05.xhtml#R_c05-fea-0011)：独热编码分类特征：鲍鱼数据——`abalone_data_spark.py`

```python
__author__ = 'mike_bowles'

# 导入 sparksession 
from pyspark.sql import SparkSession
from pyspark.ml.feature import VectorAssembler
from pyspark.ml.regression import LinearRegression
import matplotlib.pyplot as plt
from pyspark.ml.feature import StandardScaler
from pyspark.ml.feature import OneHotEncoderEstimator, StringIndexer, VectorAssembler
from pyspark.ml import Pipeline
import pandas as pd
from pandas import DataFrame
from Read_Fcns import pd_read_abalone
from pyspark.ml.evaluation import RegressionEvaluator

spark = SparkSession.builder.appName("abalone_regression").getOrCreate()

# 将鲍鱼数据读取为 pandas 数据框并创建 Spark 数据框。
abalone_df = pd_read_abalone()
abalone_sp_df = spark.createDataFrame(abalone_df)
print('Column Names', abalone_df.columns, '\n\n')

cols = abalone_sp_df.columns
abalone_sp_df.printSchema()

numeric_cols = ['Length', 'Diameter', 'Height', 'Whole weight', 
               'Shucked weight', 'Viscera weight', 'Shell weight']     

stringIndexer = StringIndexer(inputCol="Sex", outputCol="SexIndex")
encoder = OneHotEncoderEstimator(inputCols=[stringIndexer.getOutputCol()], outputCols=["SexClassVec"])
stages = [stringIndexer, encoder]

assembler_inputs = ["SexClassVec"] + numeric_cols 

assembler = VectorAssembler(inputCols=assembler_inputs, outputCol="features")
stages += [assembler]

pipeline = Pipeline(stages=stages)
pipelineModel = pipeline.fit(abalone_sp_df)
df = pipelineModel.transform(abalone_sp_df)
selectedCols = ['features'] + cols
df = df.select(selectedCols)
df.printSchema()

pd.DataFrame(df.take(4), columns=df.columns).transpose()

train, test = df.randomSplit([0.7, 0.3], seed=2018)
print("Training Dataset Count: ", train.count())
print("Test Dataset Count: ", test.count())

lr = LinearRegression(featuresCol='features', labelCol='Rings', maxIter=10, regParam=0.003, elasticNetParam=0.8)
lr_model = lr.fit(train)
print("Coefficients: ", lr_model.coefficients)
print("Intercept: ", lr_model.intercept)

trainingSummary = lr_model.summary
print("RMSE: ", trainingSummary.rootMeanSquaredError)
print("R Squared on training data:", trainingSummary.r2)

lr_predictions = lr_model.transform(test)
lr_predictions.select("prediction", "Rings", "features").show(5)

from pyspark.ml.evaluation import RegressionEvaluator
lr_evaluator = RegressionEvaluator(predictionCol="prediction", labelCol="Rings", metricName="r2")
print("R Squared on test data:" , lr_evaluator.evaluate(lr_predictions))

打印输出：
Column Names Index(['Sex', 'Length', 'Diameter', 'Height',  
'Whole weight', 'Shucked weight', 'Viscera weight', 'Shell weight', 
'Rings'], dtype='object') 

root
 |-- Sex: string (nullable = true)
 |-- Length: double (nullable = true)
 |-- Diameter: double (nullable = true)
 |-- Height: double (nullable = true)
 |-- Whole weight: double (nullable = true)
 |-- Shucked weight: double (nullable = true)
 |-- Viscera weight: double (nullable = true)
 |-- Shell weight: double (nullable = true)
 |-- Rings: long (nullable = true)
 
root
 |-- features: vector (nullable = true)
 |-- Sex: string (nullable = true)
 |-- Length: double (nullable = true)
 |-- Diameter: double (nullable = true)
 |-- Height: double (nullable = true)
 |-- Whole weight: double (nullable = true)
 |-- Shucked weight: double (nullable = true)
 |-- Viscera weight: double (nullable = true)
 |-- Shell weight: double (nullable = true)
 |-- Rings: long (nullable = true)

features     ---row of attribute vectors - run notebook for more
                0       1       2       3
Sex             M       M       F       M
Length          0.455   0.35    0.53    0.44
Diameter        0.365   0.265   0.42    0.365
Height          0.095   0.09    0.135   0.125
Whole weight    0.514   0.2255  0.677   0.516
Shucked weight  0.2245  0.0995  0.2565  0.2155
Viscera weight  0.101   0.0485  0.1415  0.114
Shell weight    0.15    0.07    0.21    0.155
Rings           15      7       9       10

Training Dataset Count: 2924
Test Dataset Count: 1253

Coefficients:  [-0.306360840416938, -1.5588226677602282,
 2.9172381109536025, 4.568071822665666, 32.918696234090376,-
0.09751444851762599, -7.477249822177075, -4.238501196414483,
 12.00722955259035]
Intercept:  3.2080030819683936
RMSE:  2.2246864543509055
R Squared on training data: 0.5023819644971068
 
+-----------------+-----+--------------------+
|       prediction|Rings|            features|
+-----------------+-----+--------------------+
|8.126455982607062|    6|[0.0,0.0,0.345,0....|
|8.301277100910529|    5|[0.0,0.0,0.36,0.2...|
|9.238211710278332|   12|[0.0,0.0,0.415,0....|
|9.930756998402277|    9|[0.0,0.0,0.445,0....|
|9.987207321370438|    9|[0.0,0.0,0.45,0.3...|
+-----------------+-----+--------------------+
only showing top 5 rows
R Squared on test data = 0.424898 
```

## 使用元参数优化的多类逻辑回归

本节介绍几个新要素。其中之一是使用字符串索引器转换多类问题中的标签。另一个是将 PySpark 逻辑回归用于多类问题。这些都是基于你已见内容的适度延伸。另一个新要素是使用参数网格搜索来确定元参数（如 ElasticNet 参数和正则化参数）的最佳值。

该多类问题的基本编码（[清单 5-11](#c05.xhtml#c05-fea-0012)）与 [清单 5-9](#c05.xhtml#c05-fea-0010) 中二分类问题的编码看起来相同。它适用于标签在单列中表示的情况，该列指示由字符串索引器分配给它们的编号。

参数搜索通过使用 `CrossValidator` 和 `ParameterGridBuilder` 来完成。代码展示了如何为正则化参数和 ElasticNet 参数提供待搜索的值。最后，读出由交叉验证结果确定的最佳值。搜索确实带来了改进。

#### [清单 5.11](#c05.xhtml#R_c05-fea-0012)：构建并优化用于玻璃分类的 PySpark 模型的代码——`glass_log_regress_spark.py`

