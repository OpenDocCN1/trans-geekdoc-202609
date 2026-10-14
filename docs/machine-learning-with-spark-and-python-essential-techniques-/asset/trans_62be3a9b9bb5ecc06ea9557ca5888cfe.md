

> ```
> __author__ = 'mike-bowles'
> 
> from Read_Fcns import list_read_wine
> import numpy a np
> from sklearn import datasets, linear_model
> from math import sqrt
> import matplotlib.pyplot as plt
> 
> #read data into iterable
> names, xList, labels = list_read_wine()
> 
> #Normalize columns in x and labels
> nrows = len(xList)
> ncols = len(xList[0])
> 
> #read wine data into lists
> names, xList, labels = list_read_wine()
> 
> #Normalize features
> xScaler = StandardScaler() 
> xNormalized = xScaler.fit_transform(xList)
> nrows, ncols = xNormalized.shape
> 
> #Normalize labels
> labelScaler = StandardScaler()
> labelNormalized = labelScaler.fit_transform(np.array(labels).reshape( \
>                   [-1,1]))
> 
> #Build cross-validation loop to determine best coefficient values.
> 
> #number of cross validation folds
> nxval = 10
> 
> #number of steps and step size
> nSteps = 350
> stepSize = 0.004
> 
> #initialize accumulator for errors
> mean_sq_err = np.zeros([nSteps,1])
> 
> for ixval in range(nxval):
>     #Define test and training index sets
>     idxTest = [a for a in range(nrows) if a%nxval == ixval]
>     idxTrain = [a for a in range(nrows) if a%nxval != ixval]
> 
>     #Define test and training attribute and label sets
>     xTrain = xNormalized[idxTrain, :] 
>     xTest = xNormalized[idxTest] 
>     labelTrain = labelNormalized[idxTrain] 
>     labelTest = labelNormalized[idxTest] 
> 
>     #Train LARS regression on Training Data
>     nrowsTrain = len(idxTrain)
>     nrowsTest = len(idxTest)
> 
>     #initialize a vector of coefficients beta
>     beta = np.zeros([ncols, 1])
>   
>   for iStep in range(nSteps):
>       #calculate residuals
>       residuals = labelTrain - np.dot(xTrain, beta)
> 
>       #correlation between attribute columns and residual
>       corr = np.mean(xTrain * residuals, axis=0) 
> 
>       #locate feature w largest magnitude correlation with residuals
>       iStar = np.argmax(np.abs(corr))
>       corrStar = corr[iStar]
>   
>       #update coefficients 
>       beta[iStar] += stepSize * corrStar / abs(corrStar)
>     
>       #calculate out of sample squared errors
>       err = labelTest - np.dot(xTest, beta)
>       mean_sq_err[iStep,0] += np.mean(err*err) / float(nxval)
>     
> cvCurve = mean_sq_err
> 
> minPt = np.argmin(cvCurve)
> minMse = cvCurve[minPt]
> print("Minimum Mean Square Error", minMse)
> print("Index of Minimum Mean Square Error", minPt)
> 
> xaxis = range(len(cvCurve))
> plt.plot(xaxis, cvCurve)
> 
> plt.xlabel("Steps Taken")
> plt.ylabel(("Mean Square Error"))
> #plt.savefig('larsWineCV.png', dpi=500)
> plt.show() 
> ```

### 用于模型选择的 Python 代码中的交叉验证机制化

[清单 4.2](#c04.xhtml#c04-fea-0003) 中的代码开头与 [清单 4.1](#c04.xhtml#c04-fea-0001) 中的代码类似。差异在循环 `nxval` 次的交叉验证循环处变得清晰。在本例中 `nxval = 10`，但也可以设置为其他值。关于使用多少折的权衡在于：折数较少意味着你在较少的数据上进行训练。如果你采用 5 折，则每次训练都会留出 20% 的数据。如果你采用 10 折，则只留出 10%。正如你在 [第 3 章](#c03.xhtml) 中所见，在较少数据上训练会导致算法所能达到的准确率下降。然而，折数越多意味着需要更多次地遍历训练过程。就训练所需的时钟或日历时间而言，这可能会很繁琐。

在交叉验证循环之前，初始化了一个误差列表。该误差列表将包含 LARS 算法演进过程中每一步的误差列表。它将累积所有 10 个交叉验证折中每一步的误差。在交叉验证循环内部，你将看到训练集和测试集的定义。除非有特殊原因，我通常使用取模函数来定义这些集合。例如，有时你可能需要进行所谓的*分层抽样*。假设你正试图在不平衡的数据上构建分类器，因此某个类别的样本非常少。你希望训练集能代表完整的数据集。你可能需要按类别隔离数据，以便类别在样本内和样本外数据中都有代表。

你可能更倾向于使用随机函数来定义训练集和测试集。你需要注意数据集中是否存在任何模式，这些模式会与抽样过程产生不利的相互作用（即观测值不可交换）。例如，如果数据是在工作周内每天采集的，那么结合五折交叉验证使用取模函数可能会导致一个集合包含所有的周一，另一个包含所有的周二，依此类推。

### 在每个交叉验证折上累积误差并评估结果

一旦定义了训练集和测试集以及一些常量，LARS 算法的迭代就开始了。这与 [清单 4.1](#c04.xhtml#c04-fea-0001) 中定义的过程非常相似，但有两个重要的区别。首先，算法的基本迭代是在训练集上而非完整数据集上进行的；其次，在每次迭代的每一步以及每个交叉验证折中，当前的 `β` 值会与测试属性和测试标签一起用于确定该步骤在测试集上的误差。你将在交叉验证循环底部看到该计算。每次更新 `β` 时，都会将其应用于测试数据，并将误差累积到“error”中相应的列表中。然后对 error 中的每个列表进行平方和求平均，这是一件简单的事。这将生成一条在所有 10 个交叉验证折上平均的每次迭代的均方误差（MSE）曲线。

你可能会担心测试数据是否被正确使用。时刻警惕测试数据泄露到训练过程中始终很重要。有许多方法会让人误以为自己没有违反这一必要性。在本例中，你会注意到测试数据未用于 `β` 增量的计算。那里只使用了训练数据。

### 模型选择和训练序列的实际考量

LARS 迭代步数与 MSE 的曲线如 [图 4.4](#c04.xhtml#c04-fig-0012) 所示。这条曲线呈现出一种相当常见的模式。它在整个范围内或多或少单调递减。严格来说，正如程序相关打印输出所示，它在 311 步左右确实有一个最小值点。但图表显示该最小值相当平缓，不够尖锐。在某些情况下，这条曲线会在某处有一个尖锐的最小值，并在最小值的左右两侧显著上升。你利用交叉验证的结果来决定 LARS 生成的 350 个解中哪一个应用于预测。在本例中，最小值位于第 311 步。第 311 组 `β` 将是用于部署的系数。当对部署哪个最佳解存在歧义时，通常最好部署更保守的解。对于惩罚回归，更保守意味着系数值更小的那个。按照惯例，样本外性能通常将复杂度较低的模型描绘在左侧，复杂度较高的模型描绘在右侧。复杂度较低的模型具有更好的泛化误差；即它们在新数据上的表现更可预测。更保守的模型将是样本外性能图中更靠左侧的那个。

