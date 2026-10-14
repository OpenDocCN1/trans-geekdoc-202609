
> ```
> __author__ = 'mike_bowles'
> 
> # Import sparksession 
> from pyspark.sql import SparkSession
> from pyspark.ml.feature import VectorAssembler
> from pyspark.ml.classification import LogisticRegression
> import matplotlib.pyplot as plt
> from pyspark.ml import Pipeline
> from pyspark.ml.feature import OneHotEncoder, StringIndexer, VectorAssembler
> import pandas as pd
> from pandas import DataFrame 
> from Read_Fcns import pd_read_glass
> from pyspark.ml.tuning import ParamGridBuilder, CrossValidator
> from pyspark.ml.evaluation import MulticlassClassificationEvaluator
> 
> 
> spark = SparkSession.builder.appName("glass_mc_log_regress").getOrCreate()
> 
> # read glass data into pandas data frame and create spark df
> glass_df = pd_read_glass()
> 
> # Create spark dataframe for glass data
> glass_sp_df = spark.createDataFrame(glass_df)
> 
> cols = glass_sp_df.columns
> print('Column Names', cols, '\n\n')
> 
> glass_sp_df.printSchema()
> 
> pd.DataFrame(glass_sp_df.take(5), columns=glass_sp_df.columns).transpose()
> 
> feature_cols = ['RI', 'Na', 'Mg', 'Al', 'Si', 'K', 'Ca', 'Ba', 'Fe']
> 
> label_stringIdx = StringIndexer(inputCol="Type", outputCol="label")
> assembler = VectorAssembler(inputCols=feature_cols, outputCol='features')
> pipeline = Pipeline(stages=[assembler, label_stringIdx])
> 
> pipelineFit = pipeline.fit(glass_sp_df)
> dataset = pipelineFit.transform(glass_sp_df)
> 
> # have a look at the dataset
> dataset.show(5)
> 
> # train test split
> trainingData, testData = dataset.randomSplit([0.7, 0.3], seed=1011)
> 
> # select model p
> lr = LogisticRegression(maxIter=20, regParam=0.003, elasticNetParam=0.5)
> lrModel = lr.fit(trainingData)
> 
> predictions = lrModel.transform(testData)
> 
> evaluator = MulticlassClassificationEvaluator(predictionCol="prediction")
> print(evaluator.evaluate(predictions))
> 
> # search for best parameter values
> paramGrid = (ParamGridBuilder() 
>              .addGrid(lr.regParam, [0.003, 0.03, 0.3]) 
>              .addGrid(lr.elasticNetParam, [0.0, 0.2, 0.4, 0.6])
>              .build())
> 
> # 5-fold CrossValidator
> cv = CrossValidator(estimator=lr, 
>                     estimatorParamMaps=paramGrid, 
>                     evaluator=evaluator, 
>                     numFolds=5)
> 
> cvModel = cv.fit(trainingData)
> 
> predictions = cvModel.transform(testData)
> # Evaluate best model
> evaluator = MulticlassClassificationEvaluator(predictionCol="prediction")
> print(evaluator.evaluate(predictions))
> 
> print('Best Param (regParam): ', cvModel.bestModel._java_obj.getRegParam())
> print('Best Param (elasticNetParam): ', cvModel.bestModel._java_obj.getElasticNetParam()) 
> ```

本节演示了如何使用 PySpark 解决多类分类问题，并展示了如何使用 `ParamGridBuilder` 和交叉验证来确定元参数的最佳值。

## Summary

本章演示了惩罚回归的使用以及许多用于预测建模的通用工具。本章展示了几种您将经常遇到的不同类型的问题。这些包括回归、二分类和多分类。本章使用体现各种不同风格惩罚回归的 Python 包来完成这些任务。此外，本章还演示了解决您遇到的建模问题所需的几种工具的使用。这些包括将因子变量编码为数值的技术、使用二分类器解决多分类问题的技术，以及扩展线性方法以预测属性与结果之间非线性关系的技术。

本章还演示了多种量化预测模型性能的方法。回归问题最容易量化，因为它们的误差自然可以用实数来表示。分类问题可能更复杂。您看到了分类性能被量化为误分类错误率、接收者操作特征曲线下面积和经济成本。您应该选择最接近以您的实际目标（业务目标、科学目标等）衡量性能的方法。

随后，本章介绍了许多不同的问题设置（多分类、分类变量、回归、分类），并展示了如何使用 PySpark 构建解决方案。此外，本章还涵盖了一系列用于构建模型和评估其性能的工具。您将在 [Chapter 6](#c06.xhtml) 中再次看到许多相同的工具，届时我们将把它们与集成模型一起使用。

## References

1.  P. Cortez, A. Cerdeira, F. Almeida, T. Matos, and J. Reis. (2009). “Modeling Wine Preferences by Data Mining from Physicochemical Properties.” *Decision Support Systems*, Elsevier, 47(4):547–553.

2.  T. Hastie, R. Tibshirani, and J. Friedman. (2009). *The Elements of Statistical Learning: Data Mining, Inference, and Prediction*. 2nd ed. Springer-Verlag, New York.

3.  J. Friedman, T. Hastie, and R. Tibshirani. (2010). “Regularization Paths for Generalized Linear Models via Coordinate Descent.” *Journal of Statistical Software*, 33(1).

4.  K. Bache and M. Lichman. (2013). UCI Machine Learning Repository. Irvine, CA: University of California, School of Information and Computer Science. `http://archive.ics.uci.edu/ml`.

# Chapter 6: Ensemble Methods

集成方法源于这样一个观察：如果模型之间相对独立，多个模型的性能优于单个模型。一个正确率为 55% 的分类器仅属于平庸水平，但如果您拥有 100 个正确率均为 55% 的分类器，它们大多数正确的概率将跃升至 82%。（请自行搜索“cumulative binomial probability”并尝试一些数字。）

获得一组相对独立模型的一种方法是使用不同的机器学习算法。例如，您可以使用支持向量机、线性回归、K 近邻、二叉决策树等构建模型。但很难通过这种方式获得非常长的模型列表。此外，这很繁琐，因为不同模型具有需要单独调整的不同参数，且可能对输入数据有不同要求。因此，模型需要单独编码。这无法满足生成数百或数千个模型的需求（您很快就会这样做）。

因此，集成方法的关键在于开发一种算法方法，生成大量相对独立的模型，然后将它们组合成一个集成。在本章中，您将学习最流行的方法是如何实现这一点的。本章将讲解最流行的集成方法的机制，概述算法的基本结构，并通过 Python 代码演示这些算法，以帮助您深入理解其工作原理。

集成方法采用两层算法层次结构。低层算法称为*基学习器*。基学习器是一种单一的机器学习算法，用于生成将被聚合到集成中的所有模型。本章将主要使用二叉决策树作为基学习器。上层算法操纵基学习器的输入，使其生成的模型相对独立。相同的算法如何生成不同的模型？有几种广泛使用的上层算法。它们被称为*Bagging*、*Boosting* 和*随机森林*。（严格来说，随机森林是上层算法与二叉决策树特定修改的结合体。您将在“[Random Forests](#c06.xhtml#c06-sec-0035)”一节中看到更多详细信息。）
