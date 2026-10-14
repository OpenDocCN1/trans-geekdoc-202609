
[Listing 7-8](#c07.xhtml#c07-fea-0008) 遵循与检测地雷所用代码相似的大纲。在本示例中，采用了一种更手动的方法来处理类别不平衡，以便您可以直观地了解其工作原理。输入数据按类别分离，然后每个类别单独划分为 70:30 的训练集和测试集。接着，各类别的训练集被汇总为一个整体训练集，测试集同理。

#### [Listing 7-8](#c07.xhtml#R_c07-fea-0008)：构建随机森林模型以区分不同玻璃类型——glass\_rf.py

```
__author__ = 'mike_bowles'

from math import sqrt, fabs, exp
import matplotlib.pyplot as plt
from sklearn.metrics import accuracy_score, confusion_matrix, roc_curve
from sklearn.model_selection import train_test_split
from sklearn import ensemble
import numpy as np
from Read_Fcns import list_read_glass

# 读取玻璃数据
names, xNum, labels, yOneVAll = list_read_glass()

glassNames = np.array(['RI', 'Na', 'Mg', 'Al', 'Si', 'K', 'Ca', 'Ba', 'Fe',
                       'Type'])

# x 矩阵的行数和列数
nrows = len(xNum)
ncols = len(xNum[1])

# 标签为 1 到 7 的整数，没有 4 的示例。
# gb 需要从 0 开始的连续整数
newLabels = []
labelSet = set(labels)
labelList = list(labelSet)
labelList.sort()
nlabels = len(labelList)
for l in labels:
    index = labelList.index(l)
    newLabels.append(index)

# 类别分布：
# 旧标签     新标签     样本数量
# 1              0               70
# 2              1               76
# 3              2               17
# 5              3               13
# 6              4               9
# 7              5               29
# 
# 抽取 30% 测试样本可能无法保持总体比例

# 按标签进行分层抽样。
xTemp = [xNum[i] for i in range(nrows) if newLabels[i] == 0]
yTemp = [newLabels[i] for i in range(nrows) if newLabels[i] == 0]
xTrain, xTest, yTrain, yTest = train_test_split(xTemp, yTemp,
test_size=0.30,
                                                random_state=531)
for iLabel in range(1, len(labelList)):
    # 根据标签分离 x 和 y
    xTemp = [xNum[i] for i in range(nrows) if newLabels[i] == iLabel]
    yTemp = [newLabels[i] for i in range(nrows) if newLabels[i] == 
                iLabel]

    # 在分离出的示例子集上形成训练集和测试集
    xTrainTemp, xTestTemp, yTrainTemp, yTestTemp = train_test_split(xTemp, 
                                yTemp, test_size=0.30, random_state=531)

    # 累积
    xTrain = np.append(xTrain, xTrainTemp, axis=0)
    xTest = np.append(xTest, xTestTemp, axis=0)
    yTrain = np.append(yTrain, yTrainTemp, axis=0)
    yTest = np.append(yTest, yTestTemp, axis=0)

num_iterations = 50
trees_per_iteration = 10
depth = None
maxFeat  = 4 # 尝试调整

glassRFModel = ensemble.RandomForestClassifier(
                       n_estimators=trees_per_iteration, 
                       max_depth=depth, 
                       max_features=maxFeat,
                       oob_score=False, 
                       random_state=531, 
                       warm_start=True)    
   
missCLassError = []

for iteration in range(num_iterations):
    
    glassRFModel.fit(xTrain,yTrain)
    glassRFModel.n_estimators += trees_per_iteration
    
    # 在测试集上累积 auc
    prediction = glassRFModel.predict(xTest)
    correct = accuracy_score(yTest, prediction)
  
    missCLassError.append(1.0 - correct)

print("Misclassification Error" )
print(missCLassError[-1])

# 生成混淆矩阵
pList = prediction.tolist()
confusionMat = confusion_matrix(yTest, pList)
print('')
print("Confusion Matrix")
print(confusionMat)

# 绘制集成中树的数量与训练和测试错误的关系图
num_trees = [i * trees_per_iteration for i in range(num_iterations)]
plt.plot(num_trees, missCLassError)
plt.xlabel('Number of Trees in Ensemble')
plt.ylabel('Misclassification Error Rate')
plt.title('Random Forest Classifier Perf on Glass Data')
plt.savefig('rf_glass_perf.png', dpi=500)
#plt.ylim([0.0, 1.1*max(mseOob)])
plt.show()

# 绘制特征重要性
featureImportance = glassRFModel.feature_importances_

# 按最大重要性归一化
featureImportance = featureImportance / featureImportance.max()

# 绘制变量重要性
idxSorted = np.argsort(featureImportance)
barPos = np.arange(idxSorted.shape[0]) + .5
plt.barh(barPos, featureImportance[idxSorted], align='center')
plt.title('RF Variable Importance on Glass Data')
plt.yticks(barPos, glassNames[idxSorted])
plt.xlabel('Relative Variable Importance')
plt.savefig('rf_glass_var_importance.png', dpi=500)
plt.show()


打印输出：
Misclassification Error
0.2272727272727273

Confusion Matrix
[[17  2  1  0  0  1]
 [ 2 18  1  2  0  0]
 [ 2  0  4  0  0  0]
 [ 0  1  0  3  0  0]
 [ 0  1  0  0  2  0]
 [ 0  2  0  0  0  7]] 
```

该代码生成随机森林模型，并绘制训练进度和变量重要性图。它还会打印出一个混淆矩阵，显示预测模型如何处理数据总体中的每个类别。它展示了预测器将每个类别中多少样本映射到正确类别，以及多少映射到错误类别。如果分类器完美无缺，矩阵中不应有非对角线元素。

### 确定随机森林模型在玻璃分类上的性能

[Figure 7.15](#c07.xhtml#c07-fig-0015) 展示了随着集成中包含的树越来越多，随机森林的性能如何提升。曲线通常随树的增加而下降。随着树的增加，改进率逐渐降低。在图表停止的位置，改进已大幅放缓。

![Figure 7.15: The overall performance of random forests](images/c07f015.png)

[**Figure 7.15**](#c07.xhtml#R_c07-fig-0015)：随机森林的整体性能

![Figure 7.16: The relative importance of the variables used by random forest](images/c07f016.png)

[**Figure 7.16**](#c07.xhtml#R_c07-fig-0016)：随机森林所用变量的相对重要性

[Figure 7.16](#c07.xhtml#c07-fig-0016) 是一个条形图，显示了随机森林所用变量的相对重要性。图表显示许多变量的性能大致相当。这种行为不寻常。在许多情况下，变量重要性在前几个变量后就会迅速下降。本问题包含多个同等重要的变量。

## 使用 PySpark 集成包解决回归问题

本节将回顾您在全书中看到的示例，并演示如何使用 PySpark 中可用的集成方法为每个示例构建模型。本节结合了您在[第 5 章](#c05.xhtml)中学到的内容以及您刚刚看到的关于使用集成方法构建模型的内容。在 PySpark 中使用集成方法涉及与您在[第 5 章](#c05.xhtml)中看到的完全相同的数据准备步骤，并使用您在本章中迄今为止学到的相同梯度提升和随机森林算法。PySpark 的梯度提升和随机森林算法具有您之前见过的相同可调参数。一旦数据像在[第 5 章](#c05.xhtml)中那样准备就绪，只需学习一些符号和变量名的细微差别即可。
