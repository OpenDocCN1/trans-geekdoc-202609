
决策树是监督学习的一种。我们需要对数据进行拆分。它包含`root node`（根节点）、`decision node`（决策节点）和`leaf node`（叶节点）。`root node`是起点。`Branches`（分支）代表决策。`Leaf node`是最终结果。

我们可以使用`caret`、`rpart`、`rpart.plot`和`party`包来构建树。我们需要定义以下：

![](img/file5.png)

同样的....................................

![](img/file5.png)[](media/file15.png)

## 我们导入数据

我们使用`xlsx`包以 excel 格式导入数据。

![](img/file16.png)

以下是：的前几行：

![](img/file17.png)

## 决策树 – 分类问题

我们将使用决策树算法根据`satisfied`字段对数据集进行分类。它将帮助我们分类哪些人可能是某类。我们需要将数据集分为训练集和测试集。

![](img/file18.png)

我们将使用`caret`的`train`函数来构建决策树。我们将打印模型及其摘要。

![](img/file19.png)[](media/file20.png)

这里我们使用`rattle`包来绘制决策树。

![](img/file21.png)

这里的准确率是`49%`，可能由于数据集的性质较低。

![](img/file22.png)[](media/file23.png)

我们可以使用`predict`函数来预测测试集的类别。

![](img/file24.png)[](media/file25.png)[](media/file5.png)

## 决策树 - 回归问题

我们也可以使用回归树通过预测变量或特征来预测因变量的值。我们也可以使用`rpart`包来实现预测和绘图。

![](img/file26.png)[](media/file5.png)[](media/file27.png)[](media/file28.png)

下方以决策树的形式绘制了相同的。

![](img/file29.png)

我们可以通过使用`dplyr`包和`select`语句留出`pamount`变量创建一个新的测试集来重新运行模型。

![](img/file30.png)

## 决策树算法的优点

- 易于构建
- 决策树构建快速
- 决策树模型易于解释
- 可用于二分类和分类问题

## 决策树算法的缺点

- 受过拟合问题影响
- 随着分类变量级别的增加可能会增加偏差

为了提高准确性并避免过拟合，使用了`Pruning`、`Bagging`和`Boosting`方法，细节所示。

## 剪枝

剪枝切掉决策树中不提供价值信息的节点，允许我们减少由于过拟合问题导致的误差。

## Bagging

Bagging 过程涉及从数据集中创建 Bootstrap 样本，然后为每个样本创建树。每棵树根据标签对样本数据集进行分类。票数较高的类别被视为最终结果。

## 提升法 (Boosting)

从单树开始并识别错误的分类。然后通过调整权重来改进错误的分类，这一过程顺序持续进行，直到错误分类减少到最低。这种方法有助于减少弱模型之间的高偏差。

## 参考文献

- Brijain, M., Patel, R., Kushik, M. R., & Rana, K. (2014). 用于分类的决策树算法综述.
- Yang, J., Zhang, N. N., LI, J., LIU, Y. M., & LIANG, M. H. (2010). 决策树算法的研究与应用. Computer Technology and Development, 2.
- Singh, S., & Gupta, P. (2014). ID3, cart and C4. 5 决策树算法: a survey. International Journal of Advanced Information Science and Technology (IJAIST), 27(27), 97-103.
- Zhong, Y. (2016, August). 基于决策树的案例分析. In 2016 7th IEEE international conference on software engineering and service science (ICSESS) (pp. 142-147). IEEE.
- Zhang, Y., & Cao, J. (2016). 大数据分析的决策树算法. Computer Science, 43(S1), 374-379.
- Zhou, H., Zhang, J., Zhou, Y., Guo, X., & Ma, Y. (2021). 基于特征权决策树特征选择算法. Expert Systems with Applications, 164, 113842.
- Hernández, V. A. S., Monroy, R., Medina-Pérez, M. A., Loyola-González, O., & Herrera, F. (2021). 决策树诱导的实用教程：候选划分的评估指标与机会. ACM Computing Surveys (CSUR), 54(1), 1-38.
- https://cran.r-project.org/package=caret
- https://cran.r-project.org/package=xlsx
- https://cran.r-project.org/package=rpart
- https://cran.r-project.org/package=rpart.plot
- https://cran.r-project.org/package=dpylr

# 第 4 章：随机森林算法

![](img/file0.png)

随机森林是决策树算法的扩展，基于装袋（bagging）概念，其中使用自助采样（bootstrap sample）构建许多树，自助采样是一种有放回的随机采样方法。

随机森林是一种装袋技术，从随机样本中选择随机特征，使得树之间相互独立。每棵树根据标签对数据集进行分类，这被视为对特定类别的投票。票数最多的类别被视为最终结果。它减少了复杂模型中的高方差。

随机森林算法使用袋外（OOB）误差估计来验证所构建的模型。随机森林仅使用训练数据集的自助样本，而不是使用训练数据集中的所有数据或所有行。袋外误差是根据模型构建过程中被留下的自助样本计算的。

我们可以使用与决策树算法示例中相同的假设客户数据集。该文件可以从作者网站 www.vinaitheerthan.com/book.php 下载。

我们将使用`RandomForest`包来构建模型。我们需要使用`library`语句定义所需的包，如`RandomForest`、`xlsx`和`party`。

![](img/file5.png)![](img/file31.png)

我们将像上一章一样，使用`xlsx`包以 Excel 的形式导入数据。

![](img/file32.png)![](img/file33.png)

以下是数据集的前几行。

## 随机森林 – 分类问题

我们将使用随机森林树算法根据“satisfied”（满意）字段对数据集进行分类。它将帮助我们根据特征分类哪些人可能是满意的（分类问题）。

我们需要将数据集分为训练集和测试集。

![](img/file34.png)

我们将使用`RandomForest`包中的`RandomForest`函数来构建模型并打印模型摘要。

![](img/file35.png)[](media/file5.png)[](media/file36.png)

这里的 OOB 误差率估计为 49.57%，它是从训练集中留下的自助样本计算得。

`VarimpPlot`函数提供了每个特征在分类预测变量中的重要性。

![](img/file37.png)

在这里，`pamount`、`pid`和`dom`特征在 MDA 和 MDG 两种方法中都在重要特征列表的前端。

在这里，`pamount`是`qty`和`price`的派生变量。我们可以使用`dplyr`包和`select`语句通过排除`pamount`变量创建一个新的测试数据集来重新运行模型。

![](img/file38.png)

我们可以使用`predict`来预测测试集。

![](img/file39.png)

以下输出。

![](img/file40.png)[](media/file41.png)

## 随机森林 – 回归问题

我们可以将随机森林用于回归。我们将使用`RandomForest`包中的`RandomForest`函数来构建模型并打印模型摘要。

![](img/file42.png)[](media/file43.png)[](media/file44.png)

在这里，`pamount`是`qty`和`price`的派生变量。我们可以使用`dplyr`包和`select`语句通过排除`pamount`变量创建一个新的测试数据集来重新运行模型。

![](img/file45.png)[](media/file5.png)

`VARIMPPLOT`函数提供了每个特征在分类预测变量中的重要性。

![](img/file46.png)

我们可以使用`predict`来预测测试集。

![](img/file47.png)

![](img/file48.png)[](media/file49.png)

## 随机算法的优点

- 随机森林算法解决了过拟合问题
- 可以同时构建分类和回归
- 不受异常值影响

## 随机森林的缺点

- 树的数量过多导致算法变慢
- 森林模型复杂难以理解

## 参考文献

- Biau, G., & Scornet, E. (2016). 随机森林导论. Test, 25(2), 197-227.
- Svetnik, V., Liaw, A., Tong, C., Culberson, J., Sheridan, R., & Feuston, B. P. (2003). 随机森林: 一种用于分类和回归的工具. Journal of chemical information and computer sciences, 43(6), 1947-1958.
- Schonlau, M., & Zou, R. Y. (2020). 用于机器学习的随机森林算法. The Stata Journal, 20(1), 3-29.
- Yao, D., Zhan, X., Zhan, X., Kwoh, C. K., Li, P., & Wang, J. (2020). 基于随机森林的预测新型 lncRNA-疾病关联的计算模型. BMC bioinformatics, 21, 1-18.
- Gholizadeh, M., Jamei, M., Ahmadianfar, I., & Pourrajab, R. (2020). 使用随机森林 (RF) 方法预测纳米流粘度. Chemometrics and Intelligent Laboratory Systems, 201, 104010.
- Babar, B., Luppino, L. T., Boström, T., & Anfinsen, S. N. (2020). 随机回归改进高纬度太阳辐射制. Solar Energy, 198, 81-92.
- Speiser, J. L., Miller, M. E., Tooze, J., & Ip, E. (2019). 用于分类预测建模的随机森林变量选择方法的比较. Expert systems with applications, 134, 93-101.
- Probst, P., & Boulesteix, A. L. (2017). 是否需要调优随机森林树的数量. J. Mach. Learn. Res., 18(1), 6673-6690.
- Mishra, S., Tadesse, Y., Dash, A., Jena, L., & Ranjan, P. (2021). 使用随机森林分类器进行甲状腺疾病分析。Intelligent and Cloud Computing (pp. 385-390). Springer, Singapore.
- Kandhoul, N., Dhurandher, S. K., & Woungang, I. (2021). 基于随机森林分类器的机会物联网网络安全可靠路由。International Journal of Communication Systems, 34(1), e4646.
- Vakharia, V., Vaishnani, S., & Thakker, H. (2021). 使用随机森林分类器预测电器能量。Recent Advances in Mechanical Engineering (pp. 405-410). Springer, Singapore.
- https://cran.r-project.org/package=caret
- https://cran.r-project.org/package=xlsx
- https://cran.r-project.org/package=rpart
- https://cran.r-project.org/package=rpart.plot
- https://cran.r-project.org/package=party

# 第 5 章：支持向量机算法

![](img/file0.png)

支持向量机（SVM）算法旨在找到一个超平面来区分数据集中的类别，同时化类别之间的间隔。支持向量是那些靠近超平面的样本观测值。超平面可以是线性的，也可以是非线性的。

SVM 算法的核函数帮助我们将非线性数据集转换到高维空间，然后使用不同的核函数（如线性、非线性、径向基函数和 Sigmoid）通过线性方程来划分空间。

我们将使用心脏病患者的生存数据集来构建 SVM 模型（`survival.xlsx`）。该文件可以从作者网站 www.vinaitheerthan.com/book.php 下载。

我们可以使用`e1071`和`caret`等包来构建 SVM 模型。

我们需要使用`library`语句定义所需的包，如`e1071`和`xlsx`。

![](img/file50.png)![](img/file5.png)

我们将像上一章中一样，使用`xlsx`包以 Excel 格式导入数据。

![](img/file51.png)![](img/file52.png)

以下是数据集的前几行。

## SVM - 分类问题

![](img/file53.png)

我们将使用 SVM 根据`Diseasestatus`字段对数据集进行分类。它将帮助我们根据特征分类谁可能存活（分类问题）。

![](img/file5.png)![](img/file54.png)

我们可以使用`TUNE`函数通过不同的成本参数值来调优模型。

![](img/file55.png)![](img/file5.png)![](img/file56.png)

从上面的 TUNE 摘要中，我们可以推断出值为 0.1 的成本提供了最佳模型。

我们可以使用`predict`函数预测测试数据集并计算预测准确率。我们将使用成本为 15 的第一个模型进行预测。

![](img/file57.png)![](img/file5.png)

得到的输出如下：

![](img/file58.png)![](img/file5.png)

这里的准确率为 50.8%，由于假设数据集的性质，准确率可能较低。

![](img/file59.png)

我们可以借助`ROCR`包和`prediction`函数绘制接收者操作曲线（ROC）。

以下是根据假阳性率和真阳性率得到的曲线。

![](img/file60.png)

## SVM 的优点

- SVM 适用于高维数据集
- 它对文本、数字和图像等不同类型的数据效果良好
- 提供了独特的解决方案

## 随机森林算法的缺点

- 处理大型数据集时耗时间更多
- 最终模型可能难以理解

## 参考文献

- Wang, L (Ed.). (2005). 支持向量机：理论与应用 (Vol. 177). Springer Science & Business Media.
- Xie, W., She, Y., & Guo, Q. (2021). 基于改进 SVM 算法的平衡二决策树多分类研究。Scientific Programming, 2021.
- Suthaharan, S. (2016). 支持向量机。In Machine learning (pp. 385-390). Springer, Singapore.

# 第 6 章：朴叶贝叶斯

![](img/file0.png)

朴叶贝叶斯基于贝叶斯原理，并假设给定的特征之间相互独立。我们将使用心脏病患者的生存数据集来构建 SVM 模型。该文件可以从作者网站 www.vinaitheerthan.com/book.php 下载。

我们可以使用`e1071`、`naivebayes`和`caret`等包来构建 SVM 模型。

我们需要使用`library`语句定义所需的包，如`e1071`和`xlsx`。

![](img/file61.png)![](img/file5.png)

我们将像上一章中一样，使用`xlsx`包以 Excel 格式导入数据。

![](img/file5.png)![](img/file62.png)![](img/file5.png)

下表提供了数据集的前几行。为了分析，我们将从原始数据中删除`patientid`。

![](img/file63.png)

## 朴叶贝叶斯 - 分类问题

我们将使用朴叶贝叶斯算法根据`Diseasestatus`字段对数据集进行分类。它将帮助我们根据特征分类谁可能存活（分类问题）。
