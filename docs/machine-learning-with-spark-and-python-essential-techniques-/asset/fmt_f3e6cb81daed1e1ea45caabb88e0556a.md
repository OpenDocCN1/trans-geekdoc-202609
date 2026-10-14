
### 梯度提升模型的预测与属性值关系

[Figure 6.19](#c06.xhtml#c06-fig-0019) 展示了三个梯度提升模型的预测值与属性值的关系——一个仅训练一棵树，一个训练 15 棵树，一个训练 30 棵树。仅包含单棵树的模型看起来像是决策树入门部分所见树模型的简化版。正如所述，它确实是一棵在标签上训练的深度为 1 的树，然后乘以 `0.1`——即 `eps` 的值。使用 10 棵树构建的模型变得更有趣。该模型很好地近似了正确答案——图中 45 度的直线。包含 10 棵树的模型正确预测了大约一半的范围，并将左右两侧预测为常数。包含 30 棵树的模型在整个数据边缘处进一步接近良好的近似。这与装袋法使用树桩时表现出的行为截然不同。

![Figure 6.19: Gradient boosting predictions versus attribute value problem—eps = 0.1, treeDepth = 1](images/c06f019.png)

**Figure 6.19** ([#c06.xhtml#R_c06-fig-0019](#c06.xhtml#R_c06-fig-0019)): Gradient boosting predictions versus attribute value problem—eps = 0.1, treeDepth = 1

装袋法无法超越使用浅层树为彼此差别不大的问题构建预测时固有的偏差误差。梯度提升以相同方式开始，但随着它开始减少数据中间的误差，它开始更多地关注出错的区域。这将分裂点移动到了有错误的区域。这一过程无需增加树深度即可得出良好的近似。

改变控制训练的参数会发生什么？[Figures 6.20](#c06.xhtml#c06-fig-0020) 和 [6.21](#c06.xhtml#c06-fig-0021) 展示了如果树深度为 5 时图景如何变化。[Figure 6.20](#c06.xhtml#c06-fig-0020) 中的 MSE 图显示，随着树的数量增加，MSE 平滑下降，趋势相似。训练 30 棵深度为 5 的树后，MSE 值非常接近完美（0.01）——比深度为 1 的树更低。该图未显示的是训练时间。树的每一层训练时间大致相同。在每一层，都必须比较所有可能的分裂点的 MSE。一棵深度为 5 的树所需时间是五棵深度为 1 的树的五倍。公平的比较应是：深度为 1 的树训练 150 棵后达到的误差，与深度为 5 的树训练 30 棵后的误差相比。

![Figure 6.20: MSE versus number of trees for synthetic problem—eps = 0.1, treeDepth = 5](images/c06f020.png)

**Figure 6.20** ([#c06.xhtml#R_c06-fig-0020](#c06.xhtml#R_c06-fig-0020)): MSE versus number of trees for synthetic problem—eps = 0.1, treeDepth = 5

![Figure 6.21: Gradient boosting predictions versus attribute value problem—eps = 0.1, treeDepth = 5](images/c06f021.png)

**Figure 6.21** ([#c06.xhtml#R_c06-fig-0021](#c06.xhtml#R_c06-fig-0021)): Gradient boosting predictions versus attribute value problem—eps = 0.1, treeDepth = 5

[Figure 6.21](#c06.xhtml#c06-fig-0021) 明显反映了用于构建梯度提升集成的更深层树。即使是基于单棵树的第一次预测，也显示出属性整个范围内的一些结构。基于 15 棵树和 30 棵树的模型在数据边缘处仍表现出较高的误差水平。

[Figures 6.22](#c06.xhtml#c06-fig-0022) 和 [6.23](#c06.xhtml#c06-fig-0023) 展示了随着步长参数 `eps` 增加时发生的情况。[Figure 6.22](#c06.xhtml#c06-fig-0022) 显示了步长参数（此处命名为 `eps`）过大时的典型行为。MSE 与树数量的图表急剧下降，但随后在右侧再次上升。最小值位于图表左侧，靠近三分之一处。你需要调整 `eps`，使最小值位于或接近图表的右边缘。这通常能获得更好的性能。

作为属性函数的预测图显示，与使用 `eps=0.1` 的两个版本相比，其偏离正确 45% 线的尖峰波动更多。总体而言，深度为 1 的树版本表现最佳。看起来训练更多树可能会改善深度为 1 模型在边缘处的性能，从而为梯度提升得出最佳答案。

![Figure 6.22: MSE versus number of trees for synthetic problem—eps = 0.3, treeDepth = 5](images/c06f022.png)

**Figure 6.22** ([#c06.xhtml#R_c06-fig-0022](#c06.xhtml#R_c06-fig-0022)): MSE versus number of trees for synthetic problem—eps = 0.3, treeDepth = 5

![Figure 6.23: Gradient boosting predictions versus attribute value problem—eps = 0.3, treeDepth = 5](images/c06f023.png)

**Figure 6.23** ([#c06.xhtml#R_c06-fig-0023](#c06.xhtml#R_c06-fig-0023)): Gradient boosting predictions versus attribute value problem—eps = 0.3, treeDepth = 5

### 多变量问题上的梯度提升

[Listing 6-7](#c06.xhtml#c06-fea-0007) 展示了将梯度提升应用于预测葡萄酒质量的任务。除使用葡萄酒数据集作为输入外，[Listing 6-7](#c06.xhtml#c06-fea-0007) 中的代码与用于简单合成数据集的代码非常相似。

#### Listing 6-7 ([#c06.xhtml#R_c06-fea-0007](#c06.xhtml#R_c06-fea-0007)): Gradient Boosting for Predicting Wine Quality—wineGBM.py

```python
__author__ = 'mike-bowles'

import numpy as np
from sklearn import tree
from sklearn.tree import DecisionTreeRegressor
from numpy.random import choice
from math import sqrt
import matplotlib.pyplot as plt

#read data into iterable
from Read_Fcns import list_read_wine

#read data into iterable
names, xList, labels = list_read_wine()
xArray = np.array(xList)
yArray = np.array(labels)

nrows = len(xList)
ncols = len(xList[0])

#take fixed test set 30% of sample
indices = list(range(nrows))
nSample = int(nrows * 0.30)
idxTest = choice(indices, nSample, replace=False)
idxTrain = [idx for idx in indices if not(idx in idxTest)]

#Define test and training attribute and label sets
xTrain = xArray[idxTrain]
xTest = xArray[idxTest]
yTrain = yArray[idxTrain]
yTest = yArray[idxTest]
idx_Train = list(range(len(xTrain)))

#train a series of models on random subsets of the training data
#collect models in a list and check error of composite as list grows

#maximum number of models to generate
numTreesMax = 100

#tree depth - typically at the high end
treeDepth = 3

#initialize a list to hold models
modelList = []
predList = []
eps = 0.1

#initialize residuals to be the labels y
residuals = list(yTrain)
   
for iTrees in range(numTreesMax):

    modelList.append(DecisionTreeRegressor(max_depth=treeDepth))
    modelList[-1].fit(xTrain, residuals)

    #make prediction with latest model and add to list of predictions
    latestInSamplePrediction = modelList[-1].predict(xTrain)

    #use new predictions to update residuals
    residuals -= eps * latestInSamplePrediction
    
    latestOutSamplePrediction = modelList[-1].predict(xTest)
    predList.append(latestOutSamplePrediction)


#build cumulative prediction from first "n" models
rmse = []
allPredictions = []
for iModels in range(len(modelList)):

    #add the first "iModels" of the predictions and multiply by eps
    prediction_i = np.zeros_like(predList[0]) 
    for i in range(iModels): 
        prediction_i += predList[i] * eps

    allPredictions.append(prediction_i)
    errors = yTest - prediction_i
    rmse.append(sqrt(np.average(errors * errors)))


nModels = [i + 1 for i in range(len(modelList))]

plt.plot(nModels,rmse)
plt.axis('tight')
plt.xlabel('Number of Trees in Ensemble')
plt.ylabel('Root Mean Squared Error')
plt.title('Error vs Ensemble Size for GBM')
plt.savefig('gbm_wine_error_vs_nTrees.png', dpi=500)
plt.ylim((0.0, max(rmse)))
plt.show()

print('Minimum RMSE = ', min(rmse))

Printed Output:
Minimum RMSE =  0.603455179638897 
```
