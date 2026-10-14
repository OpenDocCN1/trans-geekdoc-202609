
代码从 UCI 数据存储库读取葡萄酒数据集；进行一些处理以将属性、标签和属性名称放入列表中；并按 `RandomForestRegressor` 所需的输入格式将列表转换为 numpy 数组。将这些输入对象设为 numpy 数组形式的一个额外好处是，它允许使用 sklearn 工具 `train_test_split` 来构建输入的训练版本和测试版本。代码将 `random_state` 设置为指定的整数值，而不是让随机数生成器选取一个不可重复的内部值。这样做是为了让你在运行代码时，能得到与此处展示的结果相同的图表和数值。在开发过程中设置 `random_state` 也很方便，因为结果中的随机性可能会掩盖你所做的更改。在实际模型训练期间，你可能想要将 `random_state` 设置为其默认值 `None`。固定 `random_state` 会固定留出集，因此，重复的参数调整和重新训练可能会开始在你的留出集上过度训练。

代码的下一步是定义一个集成规模列表，以生成性能图表，展示性能如何随集成中树的数量变化而变化。为了生成详细的图表，[清单 7-2](#c07.xhtml#c07-fea-0002) 中选择的数字从训练 10 棵树开始，然后获取结果并分批训练更多树。分增量训练使你能看到误差与树数量曲线的形状。这样你就可以衡量最终模型需要多少棵树。[清单 7-2](#c07.xhtml#c07-fea-0002) 中的代码展示了如何使用 `warm_start` 参数，以便在添加新树时累积训练。

#### [清单 7-2](#c07.xhtml#R_c07-fea-0002)：构建随机森林预测葡萄酒质量——wine_rf.py

```
__author__ = 'mike_bowles'

import numpy as np
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestRegressor
from sklearn.metrics import mean_squared_error
import matplotlib.pyplot as plt
from Read_Fcns import list_read_wine
from math import sqrt


# 从 UCI 网站读取葡萄酒质量数据
names, xList, labels = list_read_wine()

nrows = len(xList)
ncols = len(xList[0])

X = np.array(xList)
y = np.array(labels)
wineNames = np.array(names)

# 取固定留出集，占数据行的 30%
xTrain, xTest, yTrain, yTest = train_test_split(X, y, test_size=0.30, 
        random_state=531)

# 针对不同森林规模训练随机森林 - 观察 mse 如何变化
rmseOos = [] 
depth = None  # None - 给出最大深度树，可尝试限制
maxFeat  = 4 # 可尝试调整

num_iterations = 50 # 训练 10 棵额外的树 50 次
trees_per_iteration = 10

wineRFModel = RandomForestRegressor(n_estimators=trees_per_iteration,
                      max_depth=depth, 
                      max_features=maxFeat, 
                      oob_score=False, 
                      random_state=531, 
                      warm_start=True)

for iters in range(num_iterations):
    wineRFModel.fit(xTrain,yTrain)
    wineRFModel.n_estimators += trees_per_iteration
    
    # 累积测试集上的 mse
    prediction = wineRFModel.predict(xTest)
    rmseOos.append(sqrt(mean_squared_error(yTest, prediction)))


print("RMSE" )
print(min(rmseOos))
print(rmseOos[-1])

# 绘制训练和测试误差随集成中树数量变化的曲线
num_trees = [i * trees_per_iteration for i in range(num_iterations)]
plt.plot(num_trees, rmseOos)
plt.xlabel('Number of Trees in Ensemble')
plt.ylabel('Root Mean Squared Error')
plt.title('RF Performance vs Number of Trees')
plt.savefig('wine_rf.png', dpi=500)
plt.show()

# 绘制特征重要性
featureImportance = wineRFModel.feature_importances_

# 按最大重要性归一化
featureImportance = featureImportance / featureImportance.max()
sorted_idx = np.argsort(featureImportance)
barPos = np.arange(sorted_idx.shape[0]) + .5
plt.barh(barPos, featureImportance[sorted_idx], align='center')
plt.yticks(barPos, wineNames[sorted_idx])
plt.xlabel('Variable Importance')
plt.subplots_adjust(left=0.2, right=0.9, top=0.9, bottom=0.1)
plt.title('Relative Importance of Features')
plt.savefig('wine_rf_var_imp.png', dpi=500)
plt.show()
   
打印输出
RMSE
0.5618291717498893
0.5644169041290903 
```

影响训练的大多数参数是在实例化 `RandomForestRegressor` 对象的构造函数中设置的。在这种情况下，对构造函数的调用非常简单。唯一没有保留默认值的参数是 `max_features` 参数。默认值 (`None`) 会导致在树的每个节点都考虑所有特征，这意味着它实际上是在实现装袋法，因为不涉及属性的随机选择。

实例化 `RandomForestRegressor` 对象后，下一步是调用 `fit()` 方法并传入训练集作为参数。完成此操作后，使用测试集的属性调用 `predict()` 方法会生成预测值，这些预测值可以与测试集标签进行比较。清单中的代码使用 sklearn.metrics 函数 `mean_squared_error` 来计算预测误差。生成的均方误差数字被收集在一个列表中，然后绘制出来。[图 7.3](#c07.xhtml#c07-fig-0003) 显示了生成的图表。

![图 7.3：随机森林葡萄酒质量模型的训练和测试性能](images/c07f003.png)

[**图 7.3**](#c07.xhtml#R_c07-fig-0003)：随机森林葡萄酒质量模型的训练和测试性能

均方误差的最小值和最后一个值也会被打印并在 [清单 7-2](#c07.xhtml#c07-fea-0002) 底部复制。请注意，最后一个值比最小值略高。我更倾向于信任最后一个（较高的）值而不是最小值。随机森林通过平均越来越多的某种程度上独立的高方差树来最小化方差。从概念上讲，误差应该单调下降。在它没有单调下降的程度上，这些变化是随机波动。到 [图 7.3](#c07.xhtml#c07-fig-0003) 中图表的末尾，图表已经变得或多或少是平坦的。开始附近的最小值很可能是随机波动，而非可实现的性能。

#### 可视化随机森林回归模型的性能

[图 7.3](#c07.xhtml#c07-fig-0003) 中的曲线展示了随机森林算法的方差减少特性。随着树的增加，误差水平下降，曲线中的统计波动量也随之减少。

随机森林会生成每个变量对预测准确性重要性的估计。[清单 7-2](#c07.xhtml#c07-fea-0002) 提取数据成员 `feature_importances_`，将重要性值重新缩放到 `0` 和 `1` 之间，对生成的重要性值进行排序，然后在条形图中绘制它们。[图 7.4](#c07.xhtml#c07-fig-0004) 显示了该图表。最重要的变量具有 `1.0` 的缩放重要性，是条形图中最顶端的条形。随机森林模型将酒精度排为最重要的特征，将挥发性酸度排为第二重要。这与梯度提升的结果相反，但与你在 [第 5 章](#c05.xhtml) 中看到的惩罚线性回归的结果相同。

## 在 Python 集成模型中融入非数值属性
