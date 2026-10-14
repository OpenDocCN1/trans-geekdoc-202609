
程序硬编码了在交叉验证中产生最佳结果的 α 值。代码中的版本是使用归一化属性和标签训练出的最佳 alpha。将其中任意一个改为非归一化都会改变相应的最佳 α 值。将 Y 改为非归一化会使其按 1.2 的因子变化，该因子源于将标准差归一化为 1.0（如前文在归一化与非归一化标签的 MSE 差异背景下所讨论的）。硬编码的 α 值用于识别对应于最佳交叉验证结果的系数向量。

### 基展开：通过从旧变量创建新变量来提升性能

[第 4 章](#c04.xhtml) 讨论了以旧属性函数的形式添加新属性。这样做的目的是查看是否能提升性能。[清单 5-3](#c05.xhtml#c05-fea-0004) 展示了如何向葡萄酒数据中添加两个新属性。

#### 清单 5-3：使用样本外误差评估预测葡萄酒质量的新属性——wineExpandedLassoCV.py

```
__author__ = 'mike-bowles'

from Read_Fcns import list_read_wine
import numpy as np
from sklearn.preprocessing import StandardScaler
from sklearn import datasets, linear_model
from sklearn.linear_model import LassoCV
from math import sqrt
import matplotlib.pyplot as plt

# read data into iterable
names, xList, labels = list_read_wine()

# append two new attributes - square of last term (alcohol) and product
# of alcohol and volatile acidity
for i in range(len(xList)):
    alcElt = xList[i][-1]
    volAcid = xList[i][1]
    temp = list(xList[i])
    temp.append(alcElt*alcElt)
    temp.append(alcElt*volAcid)
    xList[i] = list(temp)

# check the new dimensions
print('New number of attributes   ', len(xList[0]))

#add new names to variable list
names.append("alco^2")
names.append("alco*volAcid")
  
# Normalize columns in x and labels
# Note: be careful about normalization.  Some penalized regression 
# packages include it
# and some don't.

xScaler = StandardScaler()
xNormalized = xScaler.fit_transform(xList)

# Normalize labels
yScaler = StandardScaler()
yNormalized = yScaler.fit_transform(np.array(labels).reshape([
         -1,1])).reshape([-1])

#normalized lables
Y = np.array(yNormalized)

#Normalized Xs
X = np.array(xNormalized)

#Call LassoCV from sklearn.linear_model
wineModel = LassoCV(cv=10).fit(X, Y)

# Display results

plt.figure()
plt.plot(wineModel.alphas_, wineModel.mse_path_, ':')
plt.plot(wineModel.alphas_, wineModel.mse_path_.mean(axis=-1),
         label='Average MSE Across Folds', linewidth=2)
plt.axvline(wineModel.alpha_, linestyle='--',
            label='CV Estimate of Best alpha')
plt.semilogx()
plt.legend()
ax = plt.gca()
ax.invert_xaxis()
plt.xlabel('alpha')
plt.ylabel('Mean Square Error')
plt.axis('tight')
plt.savefig('wineExpandedLassoCV.png', dpi=500)
plt.show()

#print out the value of alpha that minimizes the Cv-error
print("alpha Value that Minimizes CV Error  ",wineModel.alpha_)
print("Minimum MSE  ", min(wineModel.mse_path_.mean(axis=-1)))

Printed Output:
New number of attributes    13

alpha Value that Minimizes CV Error   0.020612103466917726
Minimum MSE   0.6666999823938234 
```

关键步骤发生在读取属性并将其转换为浮点数之后。十几行代码获取每一行属性，提取出对应酒精度和挥发性酸度度量的两个变量，然后追加*酒精度的平方*和*酒精度乘以挥发性酸度的乘积*。之所以选择这些变量，是因为从在解中更重要的变量入手是合理的。彻底寻找可能的改进可能包括多次尝试顶层变量的组合。

结果表明，添加这些新变量略微降低了性能。稍微搜索一下可能会合成出一些能产生有用差异的新变量。你可以为这个例子绘制系数曲线，看看新变量是否在最优解中替换了任何重要的旧变量。该信息可能会引导你用这些新的合成变量代替旧变量。

[图 5.4](#c05.xhtml#c05-fig-0004) 显示了使用扩展属性集训练的 Lasso 的交叉验证误差曲线。交叉验证曲线的特性与未进行基展开时的曲线没有实质性差异。

![图 5.4：使用扩展特征集在葡萄酒质量数据上训练的 Lasso 交叉验证误差曲线](images/c05f004.png)

**图 5.4**：使用扩展特征集在葡萄酒质量数据上训练的 Lasso 交叉验证误差曲线

本节演示了在结果为实数的问题（回归问题）上使用惩罚回归方法。下一节展示在结果为双值的问题上使用惩罚线性回归方法。代码将类似于本节所见，一些技术（如基展开）可用于分类问题。主要区别在于分类问题的性能评分方式。

## 二分类：使用惩罚线性回归检测未爆地雷

[第 4 章](#c04.xhtml) 讨论了如何将惩罚线性回归用于分类问题，并为岩石与地雷问题建立了流程。本节详细介绍了如何使用惩罚线性回归方法解决二分类问题。本节结合了 Python 的 `ElasticNet` 包。你可能还记得在 [第 4 章](#c04.xhtml) 中，`ElasticNet` 包含一个更通用的惩罚函数，该函数将 Lasso 和岭回归惩罚函数作为特例。这使得可以观察分类器性能如何随惩罚函数的变化而变化。解决问题的步骤如下：

1.  将二分类问题转化为回归问题。通过在类别结果取两个值之一时分配 0.0，取另一个值时分配 1.0，构建一个实数标签的结果向量。

2.  执行交叉验证。交叉验证变得稍微复杂一些，因为你需要为每一折计算一个误差量。Scikit-learn 有一些方便的工具来简化这些计算。

第一步（在 [第 4 章](#c04.xhtml) 中概述）是通过用实数标签替换分类标签，将二分类问题转化为回归问题。岩石与地雷问题本质上是利用声纳建立一个系统来检测海底的未爆地雷。你可能还记得在 [第 2 章](#c02.xhtml) 的数据探索中，该数据集包含从岩石和金属圆柱体（形状像地雷）返回的信号的数字化版本。目标是建立一个预测系统，能够处理数字化信号，正确识别物体是岩石还是地雷。数据集包含 208 个实验。其中 111 个是地雷，97 个是岩石。数据集宽 60 列。前 60 列包含数字化的声纳回波。最后一列包含 M 或 R，取决于物体是岩石还是地雷。这 60 列数字是该问题的属性。回归问题也需要数字标签。[第 4 章](#c04.xhtml) 中概述的一种方法是通过给两种情况中的一种分配数字 1，另一种分配 0 来构建数字标签列。[清单 5-4](#c05.xhtml#c05-fea-0005) 初始化一个名为 `labels` 的空列表，并为每一行 M 追加 1.0，为每一行 R 追加 0.0。
