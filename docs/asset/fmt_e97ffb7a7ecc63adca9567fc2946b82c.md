
> ```
> __author__ = 'mike_bowles'
> 
> from Read_Fcns import list_read_wine
> import numpy as np
> from sklearn import datasets, linear_model
> from math import sqrt
> import matplotlib.pyplot as plt
> 
> def xattrSelect(x, idxSet):
>     #takes X matrix and return subset containing columns in idxSet
>     xOut = []
>     for row in x:
>         xOut.append([row[i] for i in idxSet])
>     return(xOut)
> 
> #read data into iterable
> names, xList,labels = list_read_wine()
> 
> #divide attributes and labels into training and test sets
> indices = range(len(xList))
> xListTest = [xList[i] for i in indices if i%3 == 0 ]
> xListTrain = [xList[i] for i in indices if i%3 != 0 ]
> labelsTest = [labels[i] for i in indices if i%3 == 0]
> labelsTrain = [labels[i] for i in indices if i%3 != 0]
> 
> #build list of attributes one-at-a-time - starting with empty
> attributeList = []
> index = range(len(xList[1]))
> indexSet = set(index)
> indexSeq = []
> oosError = []
>   
> for i in index:
>     attSet = set(attributeList)
>     #attributes not in list already
>     attTrySet = indexSet - attSet
>     #form into list
>     attTry = [ii for ii in attTrySet]
>     errorList = []
>     attTemp = []
>     #try each attribute not in set to see which one gives least oos error
>     for iTry in attTry:
>         attTemp = [] + attributeList
>         attTemp.append(iTry)
>         
>         #use attTemp to form training and testing sub matrices 
>         xTrainTemp = xattrSelect(xListTrain, attTemp)
>         xTestTemp = xattrSelect(xListTest, attTemp)
> 
>         #form into numpy arrays
>         xTrain = np.array(xTrainTemp); yTrain = np.array(labelsTrain)
>         xTest = np.array(xTestTemp); yTest = np.array(labelsTest)
>         
>         #use sci-kit learn linear regression
>         wineQModel = linear_model.LinearRegression()
>         wineQModel.fit(xTrain,yTrain)
>         
>         #use trained model to generate prediction and calculate rmsError
>         rmsError = np.linalg.norm((yTest-wineQModel.predict(xTest)), 2)\
>         /sqrt(len(yTest))
>         errorList.append(rmsError)
>         attTemp = []
> 
>     iBest = np.argmin(errorList)
>     attributeList.append(attTry[iBest])
>     oosError.append(errorList[iBest])
> 
> print("Out of sample error versus attribute set size" )
> print(oosError)
> print("\n" + "Best attribute indices")
> print(attributeList)
> namesList = [names[i] for i in attributeList]
> print("\n" + "Best attribute names")
> print(namesList)
> 
> #Plot error versus number of attributes
> x = range(len(oosError))
> plt.plot(x, oosError, 'k')
> plt.xlabel('Number of Attributes')
> plt.ylabel('Error (RMS)')
> plt.show()
>   
> #Plot histogram of out of sample errors for best number of attributes
> #Identify index corresponding to min value, 
> #retrain with the corresponding attributes
> #Use resulting model to predict against out of sample data.  
> indexBest = oosError.index(min(oosError))
> attributesBest = attributeList[1:(indexBest+1)]
> 
> #Define column-wise subsets of xListTrain and xListTest convert to numpy
> xTrainTemp = xattrSelect(xListTrain, attributesBest)
> xTestTemp = xattrSelect(xListTest, attributesBest)
> xTrain = np.array(xTrainTemp); xTest = np.array(xTestTemp)
> 
> #train and plot error histogram
> wineQModel = linear_model.LinearRegression()
> wineQModel.fit(xTrain,yTrain)
> errorVector = yTest-wineQModel.predict(xTest)
> plt.hist(errorVector)
> plt.xlabel("Bin Boundaries")
> plt.ylabel("Counts")
> plt.show()
> 
> #scatter plot of actual versus predicted
> plt.scatter(wineQModel.predict(xTest), yTest, s=100, alpha=0.10)
> plt.xlabel('Predicted Taste Score')
> plt.ylabel('Actual Taste Score')
> plt.show() 
> ```

前面的代码清单包含一个小函数 `xattrSelect(x, idxSet)`，用于从 X 矩阵（以列表的列表形式）中提取选定的列。然后，它将 X 矩阵和标签向量分割为训练集和测试集。之后，代码遵循前面的算法描述。算法的一次遍历从解中包含的属性子集开始。对于第一次遍历，此子集为空。对于后续遍历，该子集包括在早期遍历中逐个选择的属性。每次遍历选择单个新属性添加到属性子集中。要添加的属性是通过测试每个未包含的属性来选择的，以查看哪一个在添加到子集后产生最佳性能。依次将每个属性添加到属性子集中，并使用普通最小二乘法拟合具有生成的属性子集的线性模型。对于测试的每个属性，都会测量样本外性能。产生最佳均方根（RSS）误差的测试属性将被添加到属性集中，并捕获相关的 RSS 误差。

图 3.13 绘制了作为回归中包含的属性数量函数的 RMSE。误差随属性增加而减少，直到包含 9 个属性时达到最小，之后略有增加。

代码清单 3.4 展示了将前向逐步回归应用于葡萄酒质量数据的数值输出。

![图 3.13：使用前向逐步回归进行葡萄酒质量预测误差](img/c03f013.png)

**图 3.13**：使用前向逐步回归进行葡萄酒质量预测误差

##### 代码清单 3.4：前向逐步回归输出

> ```
> 打印输出：
> 
> 样本外误差与属性集大小的关系
> [0.7234259255116278, 0.6860993152837196, 0.6734365033420278, 
> 0.6677033213897796, 0.6622558568522271, 0.6590004754154625, 
> 0.6572717206143076, 0.65709058062077, 0.6569993096446137, 
> 0.6575818940043473, 0.657390986901134]
> 
> 最佳属性索引
> [10, 1, 9, 4, 6, 8, 5, 3, 2, 7, 0]
> 
> 最佳属性名称
> alcohol, volatile acidity, sulphates, chlorides, total sulfur dioxide, pH, 
> free sulfur dioxide, residual sugar, citric acid, density, fixed acidity 
> ```

第一个列表显示了 RSS 误差。误差减少直到列表中的第 10 个元素，然后再次变大。相关的列索引显示在下一个列表中。最后一个列表给出了相关属性的名称（列标题）。

#### 评估和理解你的预测模型

其他几个图表有助于理解训练算法的性能，并能指出改进其性能的方法。图 3.14 显示了测试集中真实标签与预测标签的散点图。理想情况下，图 3.14 中的所有点都将位于一条 45 度线上——即真实标签和预测标签相等的线。由于真实评分是整数，散点图显示出水平的点行。当真实值只取少量值时，使数据点部分透明很有用，这样深浅可以表明图表某一区域积累了许多点。实际口味评分 5 和 6 重现得相当好。更极端的值则没有被系统很好地预测。一般来说，机器学习算法在数据集边缘处的表现较差。

![图 3.14：使用前向逐步回归生成的实际口味评分与预测值对比](img/c03f014.png)

**图 3.14**：使用前向逐步回归生成的实际口味评分与预测值对比

图 3.15 展示了使用前向逐步回归预测葡萄酒口感评分时的预测误差直方图。有时误差直方图会呈现两个或更多离散的峰值。也许它会在图表的最右侧或最左侧出现一个小峰值。在这种情况下，可能可以找到误差中不同峰值的解释，并通过添加一个新属性来降低预测误差，该属性解释了数据点属于哪一组。

![图 3.15：使用前向逐步回归预测葡萄酒口感的误差直方图](img/c03f015.png)

**图 3.15**：使用前向逐步回归预测葡萄酒口感的误差直方图

你需要注意该输出的几个方面。首先，让我们重述一下这个过程。该过程是训练一族模型（在本例中，是在 X 的列子集上训练的普通线性回归）。这系列模型是参数化的（在本例中，由线性模型中使用的属性数量参数化）。选择用于部署的模型是为了最小化样本外误差。纳入解决方案的属性数量可以称为 `complexity parameter`（复杂度参数）。具有较大复杂度参数的模型拥有更多自由参数，比复杂度较低的模型更容易过拟合数据。

还要注意，属性已根据其预测质量的重要性进行了排序。在列编号列表和相关的属性名称列表中，列表中的第一个是首先被选中的属性，第二个是其次，以此类推。使用的属性会以一个漂亮的有序列表形式输出。这是机器学习技术的一项重要且理想的特性。机器学习任务的早期阶段主要涉及寻找（或构建）用于预测的最佳属性集。拥有按重要性对属性进行排序的技术有助于这一过程。本书中开发的其他算法也将具备这一特性。

最后一个观察点是关于从机器学习技术生成的模型族中挑选模型。模型越复杂，其泛化能力越差。最好倾向于选择复杂度较低的模型。前面的例子表明，第 9 个（最佳）模型和第 10 个模型之间的性能几乎没有下降（第 4 位有效数字发生了变化）。最佳实践是移除那些属性，即使它们在第 4 位有效数字上表现更好，以保持保守策略。

#### 通过惩罚回归系数控制过拟合——岭回归

本节介绍另一种修改普通最小二乘回归的方法，以控制模型复杂度并避免过拟合。该方法作为惩罚线性回归的初步介绍。你将在第 4 章中看到更多相关内容。

普通最小二乘回归旨在寻找标量 $\beta_0$ 和向量 $\beta$，使其满足（参见公式 3.14）。

![公式 3.14：OLS 最小化问题](img/c03-disp-0015.png)

**公式 3.14**：OLS 最小化问题

表达式 `argmin` 意为“使表达式最小化的 $\beta_0$ 和 $\beta$ 的值”。得到的系数 $\beta_0^*, \beta^*$ 即为普通最小二乘解。最佳子集回归和前向逐步回归通过限制使用的属性数量来抑制普通回归。这等同于施加一个约束，即向量 $\beta$ 中的某些条目等于零。另一种方法称为*系数惩罚回归*。系数惩罚回归通过使所有系数变小（而不是使其中一些变为零）来实现相同目的。系数惩罚线性回归的一种版本称为*岭回归*。公式 3.15 展示了岭回归的问题公式化。

![公式 3.15：岭回归最小化问题](img/c03-disp-0016.png)

**公式 3.15**：岭回归最小化问题

公式 3.15 与普通最小二乘法（公式 3.14）的区别在于增加了 $\alpha \beta^T \beta$ 项。$\beta^T \beta$ 项是 $\beta$（系数向量）的欧几里得范数的平方。变量 $\alpha$ 是该问题公式化中的复杂度参数。如果 $\alpha = 0$，问题就变成了普通最小二乘回归。当 $\alpha$ 变大时，$\beta$（系数向量）趋近于零，只有常数项 $\beta_0$ 可用于预测标签 $y_i$。scikit-learn 中提供了岭回归。清单 3.5 展示了使用岭回归解决葡萄酒口感回归问题的代码。

##### 清单 3.5：使用岭回归预测葡萄酒口感——ridgeWine.py
