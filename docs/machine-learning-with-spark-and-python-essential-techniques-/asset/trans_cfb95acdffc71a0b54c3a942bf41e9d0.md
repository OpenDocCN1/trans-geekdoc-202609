

[Listing 6-5](#c06.xhtml#c06-fea-0005) 展示了装袋法算法在预测葡萄酒质量任务中的应用。葡萄酒示例演示了与你在合成数据中看到的相同原则。这些原则在 [Figures 6.15](#c06.xhtml#c06-fig-0015) 到 [6.17](#c06.xhtml#c06-fig-0017) 中体现得最为明显，这些图表来自于使用不同参数设置运行 [Listing 6-4](#c06.xhtml#c06-fea-0004) 的结果。

### [Listing 6-5](#c06.xhtml#R_c06-fea-0005)：使用装袋法预测葡萄酒质量——wineBagging.py

```
__author__ = 'mike-bowles'

import numpy as np
from sklearn import tree
from sklearn.tree import DecisionTreeRegressor
from numpy.random import choice
from math import sqrt
import matplotlib.pyplot as plt

from Read_Fcns import list_read_wine

# 将数据读入可迭代对象
names, xList, labels = list_read_wine()
xArray = np.array(xList)
yArray = np.array(labels)

nrows = len(xList)
ncols = len(xList[0])


# 取固定测试集，占样本的 30%
indices = list(range(nrows))
nSample = int(nrows * 0.30)
idxTest = choice(indices, nSample, replace=False)
idxTrain = [idx for idx in indices if not(idx in idxTest)]

# 定义测试集和训练集的属性及标签集
xTrain = xArray[idxTrain]
xTest = xArray[idxTest]
yTrain = yArray[idxTrain]
yTest = yArray[idxTest]
idx_Train = list(range(len(xTrain)))

# 在训练数据的随机子集上训练一系列模型
# 将模型收集在列表中，并检查随着列表增长组合模型的误差

# 要生成的最大模型数量
numTreesMax = 100

# 树的深度 - 通常取较高值
treeDepth = 12

# 初始化一个列表以保存模型
modelList = []
predList = []

# 随机装袋法要抽取的样本数量
nBagSamples = int(len(xTrain) * 0.5)
  
for iTrees in range(numTreesMax):
    idxBag = choice(range(len(xTrain)), nBagSamples, replace=True)
    xTrainBag = xTrain[idxBag]
    yTrainBag = yTrain[idxBag]

    modelList.append(DecisionTreeRegressor(max_depth=treeDepth))
    modelList[-1].fit(xTrainBag, yTrainBag)

    # 使用最新模型进行预测并添加到预测列表中
    latestPrediction = modelList[-1].predict(xTest)
    predList.append(latestPrediction)


# 从前 "n" 个模型构建累积预测
# 从前 "n" 个模型构建累积预测
rmse = []
allPredictions = []

for iModels in range(len(modelList)):
    
    prediction_i = np.zeros_like(predList[0]) 
    for i in range(iModels): 
        prediction_i += predList[i] / float(iModels + 1)

    allPredictions.append(prediction_i)
    errors = yTest - prediction_i
    rmse.append(sqrt(np.average(errors * errors)))


nModels = [i + 1 for i in range(numTreesMax)]


plt.plot(nModels,rmse)
plt.axis('tight')
plt.xlabel('Number of Tree Models in Ensemble')
plt.ylabel('Root Mean Squared Error')
plt.ylim((0.0, max(rmse)))
plt.title('RMS Error vs Ensemble Size - Depth = ' + str(treeDepth))
plt.savefig('bagging_wine_' + str(treeDepth) + '.png', dpi=500)
plt.show()

print('With Tree Depth = ', treeDepth)
print('With Number of Trees = ', numTreesMax)
print('Minimum RMSE = ', min(rmse))

Printed Output: 

With Tree Depth = 1
With Number of Trees = 30
Minimum RMSE = 0.7440534935904853
  
With Tree Depth = 5
With Number of Trees = 30
Minimum RMSE = 0.6540549863025144

With Tree Depth = 12
With Number of Trees = 100
Minimum RMSE = 0.5727542363996668 
```

![Figure 6.15: Predicting wine quality with Bagging on depth 1 trees](images/c06f015.png)

**[Figure 6.15](#c06.xhtml#R_c06-fig-0015)：** 在深度为 1 的树上使用装袋法预测葡萄酒质量

![Figure 6.16: Predicting wine quality with Bagging on depth 5 trees](images/c06f016.png)

**[Figure 6.16](#c06.xhtml#R_c06-fig-0016)：** 在深度为 5 的树上使用装袋法预测葡萄酒质量

![Figure 6.17: Predicting wine quality with Bagging on depth 12 trees](images/c06f017.png)

**[Figure 6.17](#c06.xhtml#R_c06-fig-0017)：** 在深度为 12 的树上使用装袋法预测葡萄酒质量

[Figure 6.15](#c06.xhtml#c06-fig-0015) 展示了随着装袋集成中包含的树越来越多，MSE 是如何变化的。在葡萄酒质量数据上，树桩（深度为 1 的树）的集成相比单棵树，其 MSE 几乎没有改善。葡萄酒数据上缺乏改善的情况比合成数据上要显著得多。这可能有几个原因。一种可能是葡萄酒质量数据边缘处的误差比合成数据更显著。另一种可能是变量间的交互作用在葡萄酒数据中更为重要。

合成数据只有一个变量，因此不存在变量间的交互作用。葡萄酒数据有多个属性，因此属性组合在一起可能比其单独贡献之和更重要。如果你走路绊倒了，那可能不重要。如果你在悬崖边缘行走，那可能也不重要。但如果你在悬崖边缘行走时绊倒了，那可能就很重要了。这两个条件需要结合起来考虑。深度为 1 的树只能考虑单个属性，因此无法解释变量之间的强交互作用。

### 装袋法需要树的深度来保证性能

[Figure 6.16](#c06.xhtml#c06-fig-0016) 展示了当树的深度均为 5 时，MSE 如何随树的数量变化。装袋集成随着树的增加显示出明显的改善。由此产生的性能远好于装袋深度为 1 的树。这种改善表明，或许更大的树深度会带来进一步的改善。

[Figure 6.17](#c06.xhtml#c06-fig-0017) 展示了当树的深度为 12 时，装袋集成中 MSE 与树数量的关系。除了使用更深的树之外，集成运行了 100 棵树而不是 30 棵，以更好地了解通过为装袋集成训练更多树可以获得多少性能改进。[Figure 6.17](#c06.xhtml#c06-fig-0017) 显示了三次运行中最低的 MSE。

### 装袋法总结

现在你已经看到了一个集成方法的初步示例。装袋法清晰地展示了集成方法通用的两层层次结构。严格来说，装袋法是定义一系列由基学习器求解的子问题，然后对其预测进行平均的高层算法。构成装袋集成的各个单独问题，是通过对原始训练数据进行随机自助采样（bootstrap sampling）得到的。装袋法降低了单个二叉树表现出的方差。为了使装袋法正常工作，装袋集成中的树需要生长到足够的深度。

装袋法作为集成方法的一个良好入门，因为它相对容易理解，且相对容易演示其方差降低特性。接下来介绍的两种算法是梯度提升和随机森林。它们采用不同的方法构建集成，并表现出比装袋法某些优势。我认识的大多数当前从业者首先使用梯度提升或随机森林，并不经常使用装袋法。

## 梯度提升

