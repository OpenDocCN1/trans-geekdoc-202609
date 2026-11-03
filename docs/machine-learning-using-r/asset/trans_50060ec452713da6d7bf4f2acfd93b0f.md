
使用 `init_model` 进行预测可以通过使用 `predict` 函数并传递 `train_dt` 或 `test_dt` 以及参数 `s` 来实现，该参数取预测时使用的 `lambda` 值。我们还将传递参数 `type = response`，它将报告 (`Y` = 1) 的条件概率。我们将以默认截断值 0.50 将此概率转换为 `class`。要直接报告 `class`，我们可以传递 `type = class`。

![](images/page275-02.png)![](images/page276-01.png)![](images/page277-01.png)

### 7.9.4 分类模型 – 使用 Caret 的逻辑回归

我们将使用 `train` 函数的 `tuneLength` 参数来微调 `ElasticNet` 模型。有关 `tuneLength` 的详细信息，请参阅 [第 7.7.3 节](#15_Chapter07.xhtml#sec7.7.3)。

当 `tuneLength=10` 时，对于每个 `alpha`，将评估 10 个 `lambda` 值。因此，总共将构建 100 个模型。

![](images/page277-02.png)![](images/page278-01.png)![](images/page279-01.png)

`ElasticNet` 模型的模型系数如下：

![](images/page280-01.png)

对 `train_dt` 的预测如下：

![](images/page280-02.png)![](images/page281-01.png)

对 `test_dt` 的预测如下：

![](images/page281-02.png)![](images/page282-01.png)

我们已经看到了使用 `glmnet` 方法解决回归以及分类问题。

### Summary

在本章中，我们学习了

**1.** 通过定义成本函数并使用优化算法最小化成本函数来构建模型。

**2.** 实现 GD 算法以优化基于回归的模型的成本函数。

**3.** 偏差与方差权衡以及如何使用正则化避免模型过拟合。

**4.** 高级回归模型，如 `LASSO`、`ridge` 和 `ElasticNet` 模型。

**5.** 使用 `glmnet` 包构建机器学习模型（回归以及分类）。

**6.** 使用 `caret` 包构建机器学习模型（回归以及分类）。

### Exercise

数据集 `SAheart.data` 取自以下链接：

[http://www-stat.stanford.edu/~tibs/ElemStatLearn/datasets/SAheart.data](http://www-stat.stanford.edu/~tibs/ElemStatLearn/datasets/SAheart.data)

数据集 `SAheartrateData.txt` 包含南非西开普省心脏病高风险地区男性的记录。每例冠心病约有两例对照。许多冠心病阳性男性在冠心病事件后接受了降压治疗和其他降低危险因素的项目。在某些情况下，测量是在这些治疗后进行的。这些数据取自 Rousseauw 等人 (1983) 在 *South African Medical Journal* 中描述的更大数据集。它是一个制表符分隔的文件（.csv）并包含以下列：

• `sbp` – 收缩压

• `tobacco` – 累计烟草（kg）

• `ldl` – 低密度脂蛋白胆固醇

• `adipos ity`

• `famhist` – 心脏病家族史（存在，缺席）

• `typea` – A 型行为

• `obesity`

• `alcohol` – 当前酒精消费

• `age` – 发病年龄

• `chd` – 响应，冠心病

`chd` = 1 和 `chd` = 0 将分别称为 `chd` 和 `no chd` 病例。

**1.** 找出数据集中 `chd` 和 `no chd` 可用的病例数。使用条形图绘制结果，其中 `X` 为 chd 或 no chd，`Y` 给出每个组中的样本计数。

**2.** 使用 `caret` 构建 `lasso` 逻辑回归模型。使用 `K`\-折交叉验证（`K` = 5）并使用 ROC AUC 分数报告最佳模型。

**3.** 使用 `caret` `glmnet` 方法构建 `ridge` 逻辑回归模型。使用 `K`\-折交叉验证（`K` = 5）并使用 ROC AUC 分数报告最佳模型。

**4.** 使用 `caret` 构建 `ElasticNet` 逻辑回归模型。使用 `train()` 的 `tuneLength` 参数微调模型并使用 ROC AUC 分数报告最佳模型。

**5.** 使用 `glmnet` 包构建 `lasso` 逻辑回归模型。使用 K 折交叉验证（`K` = 5）报告最佳模型。比较并描述该模型的结果与第 2 题中获得的模型。

**6.** 使用 `glmnet` 包构建 `ridge` 逻辑回归模型。使用 `K`\-折交叉验证（`K` = 5）报告最佳模型。比较并描述该模型的结果与第 3 题中获得的模型。

**7.** 使用 `glmnet` 包构建 `ElasticNet` 逻辑回归模型。使用 `K`\-折交叉验证（`K` = 5）报告最佳模型。比较并描述该模型的结果与第 4 题中获得的模型。

### Bibliography

**1.** Anon (2018), *“Glmnet：如何选择 Lambda 和 Alpha”*，网址：[https://stats.stackexchange.com/questions/357190/glmnet-how-to-select-lambda-and-alpha](https://stats.stackexchange.com/questions/357190/glmnet-how-to-select-lambda-and-alpha)，于 2021 年 5 月 10 日访问。

**2.** Friedman J and Hastie T, *“通过坐标下降的广义线性模型的正则化路径”*，网址：[https://web.stanford.edu/~hastie/Papers/glmnet](https://web.stanford.edu/~hastie/Papers/glmnet)，于 2021 年 1 月 21 日访问。

**3.** Friedman J, Hastie T, and Tibshirani R (2008), “通过坐标下降的广义线性模型的正则化路径”，*Journal of Statistical Software*，33(1)，1–22。

**4.** Hastie T and Qian J (2014), *“Glmnet and Vignette”*，网址：[https://web.stanford.edu/~hastie/glmnet/glmnet_alpha.html](https://web.stanford.edu/~hastie/glmnet/glmnet_alpha.html)，于 2021 年 1 月 21 日访问。

**5.** Hastie T, Qian J and Kenneth Tay (2021), “An *Introduction to Glmnet”*，网址：[https://glmnet.stanford.edu/articles/glmnet.html](https://glmnet.stanford.edu/articles/glmnet.html)，于 2021 年 5 月 10 日访问。

**6.** Malviya D (2020), *“Machine Learning”*，网址：[https://www.kaggle.com/deepprabhamalviya/ml-day8](https://www.kaggle.com/deepprabhamalviya/ml-day8)，于 2021 年 5 月 10 日访问。

**7.** Mitchell T M (2006), “The Discipline of Machine Learning”，Carnegie Mellon University Report (CMU-ML-06-108)，可获得于 [https://www.cs.cmu.edu/~tom/pubs/MachineLearning.pdf](https://www.cs.cmu.edu/~tom/pubs/MachineLearning.pdf)，于 2021 年 8 月 2 日访问。

**8.** Pradhan M and Kumar U D (2019), *“Machine Learning Using Python”*，Wiley，Indian Institute of Management，Bangalore。

**9.** Simon N, Friedman J, and Hastie T (2013), “A Blockwise Descent Algorithm for Group-Penalised Multiresponse and Multinomial Regression”，网址：[https://arxiv.org/abs/1311.6529](https://arxiv.org/abs/1311.6529)，于 2021 年 5 月 10 日访问。

**10.** Simon N, Friedman J, Hastie T, and Tibshirani T (2011), “通过坐标下降的 Cox 比例风险模型的正则化路径”，*Journal of Statistical Software*，39(5)，1–13。

**11.** Tibshirani R, Bien J, Friedman J, Hastie T, Simon N, Taylor J, Tibshirani R J (2010), “Strong Rules for Discarding Predictors in Lasso-type Problems”，Journal of the Royal Statistical Society: Series B *(Statistical Methodology)*，74(2)，245–266。

________________________

[¹](#15_Chapter07.xhtml#ch7-fn1)[https://web.stanford.edu/~hastie/glmnet/glmnet_alpha.html](https://web.stanford.edu/~hastie/glmnet/glmnet_alpha.html)

[²](#15_Chapter07.xhtml#ch7-fn2)[https://web.stanford.edu/~hastie/Papers/glmnet.pdf](https://web.stanford.edu/~hastie/Papers/glmnet.pdf)

## 集成方法

## 8

*人人都知其道，少有人行之。*

**—菩提达摩**

学习目标

阅读本章后，你将能够：

• 学习集成方法背后的数学原理。

• 学习开发诸如 `Random Forest`、`Gradient boosting machine` 和 `Xtreme boosting` 等集成技术。

• 学习使用集成方法生成 `variable importance`（`feature importance`）。

• 理解机器学习算法中的 `hyper-parameters` 以及如何搜索最佳 `hyper-parameters`。

### 8.1 | 概述

