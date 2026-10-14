
> ```
> __author__ = 'mike_bowles'
> 
> from math import sqrt, fabs, exp
> import matplotlib.pyplot as plt
> from sklearn.model_selection import train_test_split
> from sklearn.ensemble import RandomForestClassifier
> from sklearn.metrics import roc_auc_score, roc_curve
> import numpy as np
> 
> # 从 UCI 数据仓库读取数据
> xList, labels = list_read_rvm()
> 
> # x 矩阵中的行数和列数
> nrows = len(xList)
> ncols = len(xList[1])
> 
> # 将 x 和 y 转换为 numpy 数组并生成列名
> X = np.array(xList)
> y = np.array(labels)
> rocksVMinesNames = np.array(['V' + str(i) for i in range(ncols)])
> 
> # x 矩阵中的行数和列数
> nrows = len(X)
> ncols = len(X[1])
> 
> # 划分为训练集和测试集
> xTrain, xTest, yTrain, yTest = train_test_split(X, y, test_size=0.30, random_state=531)
> 
> # 定义分类器
> depth = None
> maxFeat = 8 # 尝试调整
> 
> num_iterations = 50 # 每次训练 10 棵额外的树，共 50 次
> trees_per_iteration
> rocksVMinesRFModel = RandomForestClassifier(n_estimators=
> trees_per_iteration,  
>                         max_depth=depth, 
>                         max_features=maxFeat,
>                         oob_score=False, 
>                         random_state=531, 
>                         warm_start=True)
> 
> auc = [] # 累积 AUC 分数
> 
> for iters in range(num_iterations):
>   
>     rocksVMinesRFModel.fit(xTrain,yTrain)
>     rocksVMinesRFModel.n_estimators += trees_per_iteration
> 
>     # 在测试集上累积 AUC
>     prediction = rocksVMinesRFModel.predict_proba(xTest)
>     aucCalc = roc_auc_score(yTest, prediction[:,1:2])
>     auc.append(aucCalc)
> 
> print("AUC" )
> print(auc[-1])
> 
> 
> # 绘制训练和测试误差与集成中树的数量的关系图
> num_trees = [i * trees_per_iteration for i in range(num_iterations)]
> plt.plot(num_trees, auc)
> plt.xlabel('集成中树的数量')
> plt.ylabel('ROC 曲线下面积 - AUC')
> plt.title('随机森林的 AUC 性能')
> #plt.ylim([0.0, 1.1*max(mseOob)])
> plt.savefig('rvm_rf_auc_performance_v_num_trees.png', dpi=500)
> plt.show()
> 
> # 绘制特征重要性
> featureImportance = rocksVMinesRFModel.feature_importances_
> 
> # 按最大重要性归一化
> featureImportance = featureImportance / featureImportance.max()
> 
> # 绘制前 30 个重要特征
> idxSorted = np.argsort(featureImportance)[30:60]
> idxTemp = np.argsort(featureImportance)[::-1]
> print(idxTemp)
> barPos = np.arange(idxSorted.shape[0]) + .5
> plt.barh(barPos, featureImportance[idxSorted], align='center')
> plt.yticks(barPos, rocksVMinesNames[idxSorted])
> plt.xlabel('变量重要性')
> plt.title('随机森林的变量重要性')
> plt.savefig('RVM_variable_importance_rf.png', dpi=500)
> plt.show() 
> 
> # 绘制最佳版本的 ROC 曲线
> fpr, tpr, thresh = roc_curve(yTest, list(prediction[:,1:2]))
> ctClass = [i*0.01 for i in range(101)]
> 
> plt.plot(fpr, tpr, linewidth=2)
> plt.plot(ctClass, ctClass, linestyle=':')
> plt.xlabel('假正率')
> plt.ylabel('真正率')
> plt.title('随机森林岩石与地雷 ROC 曲线')
> plt.savefig('rocksVMines_roc_rf.png', dpi=500)
> plt.show()
> 
> # 选取一些阈值并计算最佳预测的混淆矩阵
> # 注意 GBM 预测值不在 (0, 1) 范围内
> # 在第 25、50 和 75 百分位处选取阈值
> idx25 = int(len(thresh) * 0.25)
> idx50 = int(len(thresh) * 0.50)
> idx75 = int(len(thresh) * 0.75)
> 
> # 计算总点数、总正例和总负例
> totalPts = len(yTest)
> P = sum(yTest)
> N = totalPts - P
> 
> print('')
> print('不同阈值的混淆矩阵')
> 
> 打印输出：
> AUC
> 0.9452332657200812
> 
> 不同阈值的混淆矩阵
> 
> 阈值 =    0.724
> TP =  0.3492063492063492 FP =  0.015873015873015872
> FN =  0.19047619047619047 TN =  0.4444444444444444
> 
> 阈值 =    0.63
> TP =  0.4603174603174603 FP =  0.031746031746031744
> FN =  0.07936507936507936 TN =  0.42857142857142855
> 
> 阈值 =    0.516
> TP =  0.5079365079365079 FP =  0.15873015873015872
> FN =  0.031746031746031744 TN =  0.30158730158730157 
> ```

### 确定随机森林分类器的性能

图 7.11 展示了 AUC 与树的数量的关系图。该图看起来与你之前见过的涉及均方误差或误分类误差的图是**倒置**的。对于均方误差和误分类误差，越小越好。对于 AUC，1.0 是完美的，0.5 是完全糟糕的。因此，对于 AUC，越大越好，你要寻找的不是图中的**谷底**，而是**峰值**。图 7.11 显示峰值出现在图的左侧。然而，由于随机森林仅减少方差而不会过拟合，该峰值可归因于随机波动。正如本章前面的一些回归问题一样，最佳模型选择是包含所有树的模型，其性能对应曲线最右侧的点。

![图 7.11：岩石与地雷模型中随机森林的变量重要性估计](img/c07f011.png)

**图 7.11**：岩石与地雷模型中随机森林的变量重要性估计

![图 7.12：岩石与地雷模型中随机森林的变量重要性估计](img/c07f012.png)

**图 7.12**：岩石与地雷模型中随机森林的变量重要性估计

图 7.12 绘制了随机森林地雷探测器中最重要的 30 个变量的重要性。地雷探测问题中的不同属性对应声纳信号的不同频率，因此对应不同的波长。如果让你为这个问题设计机器学习，你的下一步可能是确定这些变量对应的波长，并将这些波长与测试集和训练集中岩石和地雷的特征尺寸进行比较。这能帮助你建立对模型的信心和理解。

图 7.13 展示了随机森林实现的 ROC 曲线。模型获得了非常高的 AUC，ROC 曲线相应地也非常好。它虽然没有完全贴合左上角，但非常接近。

![图 7.13：随机森林岩石与地雷模型的接收者操作特征曲线 (ROC)](img/c07f013.png)

**图 7.13**：随机森林岩石与地雷模型的接收者操作特征曲线 (ROC)

## 使用 Python 集成方法解决多类分类问题

`XGBoost` 中的梯度提升和随机森林包以及 Python `sklearn` 库都能构建二分类和多类分类模型。这两类模型之间存在一些自然的差异。一是标签（`y`）取更多的值。梯度提升和随机森林包的讨论描述了指定标签的方式。对于具有 `nClass` 个不同类别的分类问题，标签取从 0 到 `nClass – 1` 的整数值。类别数量的另一种体现是各种预测方法的输出。预测类别的预测方法生成与标签相同的整数值。预测概率的方法生成 `nClass` 个可能类别的概率。

另一个明显不同的领域是性能指标的指定。误分类误差仍然适用，你将看到示例代码使用它来衡量样本外性能。当类别超过两个时，AUC 的使用变得更加复杂，权衡不同错误类型也变得更具挑战性。

### 处理类别不平衡

本节代码将使用“使用 Python 梯度提升检测未爆地雷”和“构建随机森林模型检测未爆地雷”两节中应用的分类器，但需要针对玻璃数据进行调整。一个重要的区别是玻璃数据是不平衡的。“不平衡”意味着某些类别的样本数量明显多于其他类别。你将在代码清单中看到每种玻璃类型的样本数量。有些类型的样本相对较多（70 多个），而有些类型的玻璃代表性不足。其中有一种类型仅有 9 个样本。

类别不平衡有时会导致问题，因为对代表性不足的类别进行随机采样，可能导致样本中的比例与原始数据中的比例截然不同。例如，玻璃数据中某一类别仅有 9 个样本。如果你想进行 10 折交叉验证，其中一个测试折叠将没有该类别的样本。为避免这些问题，代码采用了一种称为*分层采样*的过程。在此情况下，这意味着数据根据标签进行分离（分层），然后对每个组进行采样，以在每个类别内获得训练集和测试集。随后，将特定类别的训练集合并为一个训练集，其各类别比例与原始数据完全匹配。下一节中的梯度提升代码通过使用 `sklearn` 的 `StratifiedKFold` 包来实现这一点。随机森林代码则展示了如何自行构建分层。

### 使用梯度提升对玻璃进行分类

Listing 7-7 使用 `XGBoost` 构建模型对玻璃进行分类。这是一个多类分类问题。Listing 7-7 中的代码还展示了如何从多个不同的参数组合中构建网格搜索以寻找最佳参数值。网格搜索的基本思路是为若干参数选择一些值，然后遍历所有可能的组合以找到最佳组合。代码使用一个名为 `grid_dict` 的字典来存放被调整的参数。每个参数名作为键，字典为每个键保存一个值列表。随后，一个 `for` 循环遍历所有可能的值组合列表。代码展示了如何使用 Python 的 `itertools` 包从列表字典中生成组合列表。

随着网格搜索迭代的进行，当发现表现更好的参数组合时，对应最佳性能的参数值会被更新。随后，使用最佳参数集重新训练模型，并打印训练性能和测试性能。Listing 7-7 中演示的过程将帮助你自动化寻找最适合你问题的最佳模型的过程。

#### Listing 7-7：构建梯度提升模型以区分不同类型的玻璃——glass_gbm.py
