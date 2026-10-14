
# LARS 算法

LARS 算法解决的问题与前面列出的那些略有不同。然而，它生成的解通常与 Lasso 相同，即使存在差异，差异也相对较小。深入研究 LARS 算法的原因在于它与 Lasso 和前向逐步回归关系非常密切，且 LARS 算法易于概述，代码实现也相对紧凑。通过阅读 LARS 的代码，你将理解更通用的 ElasticNet 求解器内部的工作原理。更重要的是，你将看到伴随惩罚回归求解器的各种问题及其变通方法。实现 LARS 算法的代码如 [代码清单 4.1](#c04.xhtml#c04-fea-0001) 所示。

代码主要分为三个部分，此处简要描述，随后将详细讨论：

*   以列表形式读取数据和表头。
*   标准化属性和标签。
*   求解组成解的系数（`β₀*, β*`）。

## 代码清单 4.1：用于预测葡萄酒口感的 LARS 算法——larsWine2.py

```
from Read_Fcns import list_read_wine
import numpy as np
from sklearn import datasets, linear_model
from sklearn.preprocessing import StandardScaler

from math import sqrt
import matplotlib.pyplot as plt

# 将葡萄酒数据读入列表
names, xList, labels = list_read_wine()

# 标准化特征
xScaler = StandardScaler()
xNormalized = xScaler.fit_transform(xList)
nrows, ncols = xNormalized.shape
  
# 标准化标签
labelScaler = StandardScaler()
labelNormalized = labelScaler.fit_transform(np.array(labels).reshape(
          [-1,1]))

# 初始化系数向量 beta
beta = np.zeros([ncols, 1])

# 初始化每一步的 beta 矩阵
betaMat = beta.copy()

# 初始化列表以累积已使用的特征
nzList = []

# 步数和步长
nSteps = 350
stepSize = 0.004

for i in range(1, nSteps):
  
    # 计算残差
    residuals = labelNormalized - np.dot(xNormalized, beta)
    
    # 属性列与残差之间的相关性
    corr = np.mean(xNormalized * residuals, axis=0) 
  
    # 定位与残差相关性幅度最大的特征
    iStar = np.argmax(np.abs(corr))
    corrStar = corr[iStar]
  
    # 增加或减少对应的系数 (beta)
    # 相关性为正则增加，为负则减少
    beta[iStar] += stepSize * corrStar / abs(corrStar)
    betaMat= np.concatenate( (betaMat, beta.copy()), axis=1)

    # 形成非零系数列表并累积新增的系数
    nzBeta = [index for index in range(ncols) if beta[index] != 0.0]
    for q in nzBeta:
        if (q in nzList) == False:
            nzList.append(q)

nameList = [names[nzList[i]] for i in range(len(nzList))]

print(betaMat.shape)
print(nameList)
for i in range(ncols):
    # 绘制每个属性的 beta 值范围
    coefCurve = betaMat[i,:].reshape([-1,])
    xaxis = range(nSteps)
    plt.plot(xaxis, coefCurve) 

plt.xlabel("Steps Taken")
plt.ylabel(("Coefficient Values"))
#plt.savefig('larsWine2.png', dpi=500)
plt.show()

打印输出：
(11, 350)
alcohol, volatile acidity, sulphates, total sulfur dioxide, chlorides,
fixed acidity, pH, free sulfur dioxide, citric acid, residual sugar,
density 
```

第一步是读取表头、属性值和标签。此处使用普通的 Python 列表作为这些数据结构。

第二步是标准化属性。所用的标准化方法与你在 [第 2 章](#c02.xhtml) “通过理解数据来理解问题” 中看到的相同。在 [第 2 章](#c02.xhtml) 中，属性标准化是为了将属性置于可比较的尺度上，以便它们能方便地绘图并充分占据同一尺度。出于大致相同的原因，标准化通常作为惩罚线性回归的第一步。属性需要具有相同的尺度，以便系数值的选择仅基于哪个属性最有用，而非基于哪个属性具有最有利的尺度。作为说明，若距离属性以微米为单位，与以公里为单位的同一属性相比，只需一个非常小的系数就能在标签上产生巨大差异。标准化对于从惩罚回归中获得合理结果至关重要。

LARS 算法的每一步都会按固定量增加其中一个 `β`。如果属性具有不同的尺度，这个固定增量对不同属性意味着不同的事情。此外，更改某个属性的尺度（例如从英里改为英尺）会导致结果不同。基于这些原因，惩罚线性回归包通常使用你在 [第 2 章](#c02.xhtml) 中看到的通用标准化方法进行标准化。它们将数据标准化为零均值（通过减去均值）和单位标准差（通过除以标准差）。包通常会提供不标准化的选项，但我从未听说过不标准化的充分理由。

第三个也是最后一个部分求解 `β₀*, β*`。因为算法在标准化变量上运行，所以不需要截距 `β₀*`。截距通常用于解释标签与加权属性之间的任何差异。因为所有属性都已标准化为零均值，它们之间没有偏移量，因此 `β₀*` 没有任何作用。请注意，初始化了两个与 beta 相关的列表。一个称为 `beta`，其元素数量与属性数量相同——每个属性一个权重。另一个是一个类矩阵的列表的列表，将存放 LARS 算法每一步的 beta 列表。这触及了惩罚线性回归以及现代机器学习算法的一个关键概念。

## LARS 如何生成数百个复杂度各异的模型
