
> ```
> __author__ = 'mike_bowles'
> 
> from Read_Fcns import list_read_wine
> import numpy as np 
> from sklearn import datasets, linear_model
> from math import sqrt
> import matplotlib.pyplot as plt
> 
> # 将数据读入列表
> names, xList, labels = list_read_wine()
> 
> # 将属性和标签划分为训练集和测试集
> indices = range(len(xList))
> xListTest = [xList[i] for i in indices if i%3 == 0 ]
> xListTrain = [xList[i] for i in indices if i%3 != 0 ]
> labelsTest = [labels[i] for i in indices if i%3 == 0]
> labelsTrain = [labels[i] for i in indices if i%3 != 0]
> 
> xTrain = np.array(xListTrain); yTrain = np.array(labelsTrain)
> xTest = np.array(xListTest); yTest = np.array(labelsTest)
> 
> alphaList = [0.1**i for i in [0,1, 2, 3, 4, 5, 6]]
> 
> rmsError = []
> for alph in alphaList:
>     wineRidgeModel = linear_model.Ridge(alpha=alph)
>     wineRidgeModel.fit(xTrain, yTrain)
>     rmsError.append(np.linalg.norm((yTest-wineRidgeModel.\
>                             predict(xTest)), 2)/sqrt(len(yTest)))
> 
> print('{:18}'.format("RMS Error"), "alpha") 
> for i in range(len(rmsError)):
>     print(rmsError[i], alphaList[i])
> 
> # 绘制样本外误差随 alpha 变化的曲线
> x = range(len(rmsError))
> plt.plot(x, rmsError, 'k')
> plt.xlabel('-log(alpha)')
> plt.ylabel('Error (RMS)')
> plt.show()
> 
> # 为最佳 alpha 值绘制样本外误差直方图
> # 以及实际值与预测值的散点图
> # 找出对应最小值的索引，用对应的 alpha 值重新训练
> # 使用生成的模型对样本外数据进行预测
> indexBest = rmsError.index(min(rmsError))
> alph = alphaList[indexBest]
> wineRidgeModel = linear_model.Ridge(alpha=alph)
> wineRidgeModel.fit(xTrain, yTrain)
> errorVector = yTest-wineRidgeModel.predict(xTest)
> plt.hist(errorVector)
> plt.xlabel("Bin Boundaries")
> plt.ylabel("Counts")
> plt.show() 
> 
> plt.scatter(wineRidgeModel.predict(xTest), yTest, s=100, alpha=0.10)
> plt.xlabel('Predicted Taste Score')
> plt.ylabel('Actual Taste Score')
> plt.show() 
> ```

回想一下，前向逐步回归算法生成了一系列不同的模型——第一个模型包含一个属性，下一个包含两个属性，依此类推，直到最终模型包含所有属性。岭回归的代码也有一系列模型。不同之处在于，岭回归模型序列具有不同的 $\alpha$ 值，而不是不同数量的属性——$\alpha$ 是决定对 $\beta$ 施加惩罚严重程度的参数。$\alpha$ 序列的构建是按 10 的幂次递减的。一般来说，你会希望让它们按指数级递减，而不是按固定增量递减。该范围需要相当宽泛，且可能需要一些实验来确定。

[图 3.16](#c03.xhtml#c03-fig-0031) 绘制了 RMSE 作为岭复杂度参数 $\alpha$ 函数的图表。参数从左侧的最大值排列到右侧的最小值。惯例是将最不复杂的模型显示在图表左侧，最复杂的模型显示在右侧。该图表显示的特性与前向逐步回归大致相同。误差大体相当，但略微倾向于前向逐步回归。

![图 3.16：使用岭回归进行葡萄酒质量预测的误差](images/c03f016.png)

[**图 3.16**](#c03.xhtml#R_c03-fig-0031)：使用岭回归进行葡萄酒质量预测的误差

[清单 3.6](#c03.xhtml#c03-fea-0006) 显示了岭回归的输出。数字表明岭回归的特性与前向逐步回归大致相同。数字略微倾向于前向逐步回归。

#### [清单 3.6](#c03.xhtml#R_c03-fea-0006)：岭回归输出

> ```
> RMS Error alpha
> (0.65957881763424564, 1.0)
> (0.65786109188085928, 0.1)
> (0.65761721446402455, 0.010000000000000002)
> (0.65752164826417536, 0.0010000000000000002)
> (0.65741906801092931, 0.00010000000000000002)
> (0.65739416288512531, 1.0000000000000003e-05)
> (0.65739130871558593, 1.0000000000000004e-06) 
> ```

[图 3.17](#c03.xhtml#c03-fig-0032) 显示了岭回归预测器在葡萄酒口味数据上训练得到的实际口味评分与预测口味评分的散点图。[图 3.18](#c03.xhtml#c03-fig-0033) 显示了预测误差的直方图。

![图 3.17：使用岭回归生成的实际口味评分与预测值对比](images/c03f017.png)

[**图 3.17**](#c03.xhtml#R_c03-fig-0032)：使用岭回归生成的实际口味评分与预测值对比

你可以将同样的通用方法应用于分类问题。“[预测模型性能度量](#c03.xhtml#c03-sec-0010)”一节讨论了几种量化分类器性能的方法。概述的方法包括使用误分类误差、将经济成本与各种预测结果相关联，以及使用 ROC 曲线下面积（AUC）来量化性能。该节使用普通最小二乘回归构建了一个分类器。[清单 3.7](#c03.xhtml#c03-fea-0007) 显示了遵循同一总体计划的 Python 代码。它不使用 OLS，而是使用岭回归作为构建岩石与地雷分类器的回归方法（带有复杂度调节参数），并使用 AUC 作为分类器的性能度量。[清单 3.7](#c03.xhtml#c03-fea-0007) 中的程序与使用岭回归进行葡萄酒口味预测类似。最大的区别在于，该程序将测试数据上的预测值和测试标签作为输入传递给 scikit-learn 包中的 `roc_curve` 程序。这使得计算每次训练过程中的 AUC 变得容易。这些值被累积起来，打印出的值如 [清单 3.8](#c03.xhtml#c03-fea-0008) 所示。

![图 3.18：使用岭回归进行葡萄酒口味预测误差的直方图](images/c03f018.png)

[**图 3.18**](#c03.xhtml#R_c03-fig-0033)：使用岭回归进行葡萄酒口味预测误差的直方图

#### [清单 3.7](#c03.xhtml#R_c03-fea-0007)：使用岭回归进行岩石与地雷分类——classifierRidgeRocksVMines.py
