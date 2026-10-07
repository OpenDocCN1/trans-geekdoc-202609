
该过程在文献中被称为 $k$-聚类。让我们使用以下内容实现原型方法：每个观测值由 $(x_1, x_2, f)$ 组成，其中 $x_i \in [0, 1]$，$i = 1, 2$，且依赖变量定义为

$f = I_{(x_1^2+x_2^2\le1)}.$

其中 $I$ 是指示函数，当参数为真时取值，否则为0。因此我们得到了依赖变量，用于分类点是否位于位于点且半径为1的圆内。这种数据可以如下生成：

```
tableKNN([], x1:10000;x2:10000);
tableKNN: update f:(x1*x1)+(x2*x2)
```

生成了 10000 个点。我们可以使用以下“技巧”来说明数据：

```
select x1,x2_0:x2 from tableKNN where f=0
select x1,x2_1:x2 from tableKNN where f=1
```

可以使用散点图进行展示。图 21 显示了结果，单位圆内的所有点为深灰色，其余点为浅灰色。

# 最近邻

![最近邻](img/97f75811280bdf85683d4c69d94242_449_0.png)

图 21.1 真实簇散点图

## 426 机器学习

```
18
tableX:update distVect..quant.knn.distanceLX[centerX;;2]
// 从 tableSub 翻转中心；
// 排序
tableX:distVect xasc tableX;
// 选择邻域，包括中心点本身
tableX[til k+1];
// 计算邻域的平均值
// 从 tableX 执行平均值中心;
[tableSub;k;iterations];
[tableSub;k;iterations]; each exec centre from tableOut;
// 通过设置新中心来更新 tableOut
update centre:new from tableOut
[table;k:R;iterations]; each valuesf
tableGlobalOut;
;
```

这是之前在 `distanceLX` 中实现的 L2 距离函数。该函数也为最层循环的并行化做了准备，在该循环中，每个应用于依赖变量的所有单元上。

我们可以运行一个 R=6 的示例；使用 k=12 个最近邻居找到中心，且每个搜索迭代 1000 次。

```
resultKNN::quantQ.knn.prototypeKNN[tableKNN;12;6;1000];
resultKNN
```

| f | centreID | count |
|--- |--- |--- |
| 0.325196 0.303876 | 1 | 1 |
| 0.734341 0.650928 | 1 | 2 |
| 0.119721 0.614183 | 1 | 3 |
| 0.679257 0.063369 | 1 | 4 |
| 0.220286 0.732153 | 1 | 5 |
| 0.320573 0.732157 | 1 | 6 |
| 0.826389 0.821746 | 0 | 1 |
| 0.984329 0.675186 | 0 | 2 |
| 0.912804 0.723958 | 0 | 3 |
| 0.524162 0.918754 | 0 | 4 |
| 0.945173 0.885824 | 0 | 5 |
| 0.975616 0.737235 | 0 | 6 |

可以通过使用以下内容形成的表格散点图获取图形输出：

```
(select x1:centre[;], x2_centre[;] from resultKNN where f=0)
(select x1:centre[;], x2_centre[;] from resultKNN where f=1)
[] x1:0.01*til 100; x2_boundary=sqrt[1-(0.01*til 100)] exp 2)
```

我们显式地在边界上生成了点，因此我们可以看到中心点被识别的位置。qPad 的图形输出可以在图 2.12 所示，其中包含了使用 `prototypeKNN` 函数训练的中心点。黑色点对应 f=0 的情况，灰色点对应 f=1。

# 最近邻居

![](img/97f7581128bd0bdf85683d4c69d94242_451_0.png)

**图 21.2** 黑色和灰色点图是由 `.quantQ.knn.prototypeKNN` 函数识别的每个类的原型

训练后的点不足以作为所选两个区域可靠且准确的原型。这可以通过增加原型的数量来解决。让我们说明原型在样本外测试中的表现。我们创建一个函数，根据点与训练中心点的接近程度为该点分配类别。

```
.quantQ.knn.getPrototypeKNN:[[tablesCentre;point;
// 包含训练中心点的表格，包含变量
centre and f
// point -- 用于分类的数组
// 点与中心点接近程度的表格
tablesCentre:distVec xasc update distVec:.quantQ.knn.distanceLX[
-> point;2]
flip centre from tablesCentre;
// 最近中心点的类别
first exec from tablesCentreX;
```

此外，我们可以像这样测试它：

```
.quantQ.knn.getPrototypeKNN;resultKNN;.2 .3
```

为了查看训练后的原型中心如何分类区域，我们对整个空间 [0,1]×[0,1] 执行了以下扫描。

```
tableSweep:([] points:((0.01*til 100) cross (0.01*til 100));
```

## 428 机器学习

为每个点分配类别，

```
tableSweep:: update fTrained; .quantQ.knn.getPrototypeKNN[resultKNN]; each
-- points 来自 tableSweep
```

并描绘表格：

```
tableSweepPlot:(select x1:points[:0], x2_k0:points[:1] from tableSweep
-- where fTrained=0)
(select x1:points[:0], x2_k1:points[:1] from tableSweep
-- where fTrained=1);
```

该方法是通用的，可以用于任意数量的类别。图 21.3 描述了 `tableSweep` 的散点图。训练原型的精度确实类似于原始形状。该形状可以从获得的表中看出：

| fTrained | fTrue | count |
|---|---|---|
| 0 | 0 | 817 |
| 0 | 1 | 389 |
| 1 | 0 | 234 |
| 1 | 1 | 756 |

我们看到分配正确类别的准确率为 93%，考虑到这一点这并不坏，考虑到我们在整个空间中识别了准确性![](img/97f7581128bd0bdf85683d4c69d94242_451_0.png)

**图 21.3** 黑色和灰色点图是由 `.quantQ.knn.prototypeKNN` 函数识别的每个类的原型

# 最近邻居

让我们考虑如下格式的数据集：

`tableFunction:([] coord1:"f($);coord2:"f($);coord3:"f($);...; val:"f($));`

其中，我们考虑了 $n$ 个独立变量 `coord` 和一个因变量 `val`。我们进一步假设因变量已使用归一化技术进行了处理。基于邻居的特征选择构建如下：

首先，我们定义加权 L2 范数 $|x-x'|_w$ 为：

```
.quantQ.knn.weightedL2norm:[x;y;weight]
// x, y -- n 维数组（特征空间中的两个点）
// weight -- n 维权重数组
// t wsum weight*(x-y);
;
```

其中 $x, y$ 是两个长度相同为 $n$ 的向量，该函数返回 $|x-y|_w$。

我们在点 $y$ 的邻域坐标中实现该函数的定位值，其中邻域根据其与点 $y$ 的接近程度使用加权 L2 范数进行加权：

```
.quantQ.knnMeanFunction:[coordX;coordY;weights;beta]
// coordX -- n 维数组（用于进行回归的点）
// coordY -- kn n 数组，k 个 n 维数组的观测值
// value -- n 维因变量数组
// weights -- n 维权重数组
// beta -- 算法参数
// 返回基于 MSE 的代码
:(1%sum exp neg (1%beta) * .quantQ.weightedL2norm[coordX;weights]
-- each coordY)*sum
valueY*exp neg (1%beta)* .quantQ.knnL2norm[coordX;weights]
-- each coordY);
;
```

为了实现该算法，我们必须实现五个构成算法基础的特殊函数。首先，我们实现误差函数 $e(w)$，它是加权估计器与无偏估计器均方误差的负。该函数的参数与之前的 `KNNMeanFunction` 相同。

```
.quantQ.knnError:[coordX;coordY;value;beta]
// coordX -- n 维数组（用于进行回归的点）
// coordY -- kn n 数组，k 个 n 维数组的观测值
// value -- n 维因变量数组
// weights -- n 维权重数组
// beta -- 算法参数
// 返回局部点的误差
// neg 0.5*t*t:(quantQ.knn.KNNMeanFunction[coordX;coordY;value;weights;
-- beta)-
.quantQ.kNNNMeanFunction[coordX;coordY;value](count weight)*1;
-- beta]);
;
```

让我们分别定义一个 $a$ 函数和一个 $u$ 函数：

```
.quantQ.knn.aFunc:([coordX;coordXB;coordXbb;beta;weights])
// coordX, coordXB, 和 coordXbb -- n 维数组（三个点）
// weights -- n 维权重数组
// 算法参数
// 返回 aFunc
// exp neg ((quantQ.knn.weightedL2norm([coordX;coordXB;weights]+
// quantQ.knn.weightedL2norm(coordX;coordXbb;weights])%beta);
```

```
.quantQ.knn.uFunc:([coordX;coordXB;coordXbb;weights])
// coordX, coordXB, 和 coordXbb -- n 维数组（三个点）
// weight -- n 维权重数组
// 返回 uFunc
:weights*(t:t:(coordX-coordX))+(u:(coordX-coordX)));
```

我们可以继续处理梯度函数的梯度 $\nabla_{\hat{\mu}}(x)$：

```
.quantQ.knn.gradFunc:([coordX;coordY;beta;weights]) each
// coordX -- k x n 数组
// coordY -- kn n 数组，k 个 n 维数组的观测值
// value -- n 维因变量数组
// weights -- n 维权重数组
// beta -- 算法参数
// ...
```

```
:(1%sum exp neg (1%beta) * .quantQ.weightedL2norm[coordX;weights]
-- each coordY)*sum
valueY*exp neg (1%beta)* .quantQ.knnL2norm[coordX;weights]
-- each coordY);
;
```

# 最近邻居

三个特征的权重分别为 `coord1:1.122086`, `coord2:1.209277` 和 `coord3:1.036502`。第二个特征权重最高，表明其重要性最大，而第三个特征的重要性最低。这符合底层的数据结构。

让我们描述权重的演变过程：

```select
select cnt, w1:weight[0], w2:weight[1], w3:weight[2] from kNNLab
```

图 21.4 展示了随着迭代次数的增加，对应三个特征的权重演变情况。三条线分别是 `coord1`（浅灰色线）、`coord2`（黑色线）和 `coord3`（深灰色线）。该图显示三个权重之间的差异在绝对值上增大。这些值在任何程度上都没有饱和，系统仍在演化中。权重并不被强制归一化，我们感兴趣的值是权重之间的相对差异。

该练习可以进一步扩展到更复杂的问题。研究权重的演变也很有趣。由于我们在每次迭代中只使用数据集的一个部分（随机部分），因此权重是随机的。值得考虑在每个迭代步骤中对权重进行重归一化，例如固定 ||w||=1。这样就可以利用权重的绝对值来评估不同问题中特征的重要性。

对于读者，展示的练习。图 21.5 展示了 10,000 步迭代后，对应三个特征的三个权重的演变情况。三条线分别是 `coord1`（浅灰色线）、`coord2`（黑色线）和 `coord3`（深灰色线）。与图 21.4 相比，当前图的权重已归一化为 ||w||=1，其中归一化是事后完成。动力学

![](img/97f7581128bd0bdf85683d4c69d242_459.png)

**图 21.4** 三个特征 `coord1`（浅灰色线）、`coord2`（黑色线）和 `coord3`（深灰色）的权重随迭代次数的演变

![](img/97f7581128bd0bdf85683d4c69d242_460.png)

**图 21.5** 三个特征 `coord1`（浅灰色线）、`coord2`（黑色线）和 `coord3`（深灰色）的归一化权重随迭代次数的演变，10,000 个权重在运行约 1000 次后变得更加稳定。第三个特征的权重于 0，而另外两个特征的权重不为零，均按其重要性排序。该图建议向一种算法扩展，只要权重达到 0 的特征就继续迭代。

# 神经网络

本章的重点是神经网络。本章涵盖了许多相关方法和技术，是机器学习增长最快的领域之一。在本章中，我们的目的是让读者相信神经网络可以很好。我们将用几行代码实现一个基于神经网络的分类器和回归器，并成功地应用于实践。

我们并不声称其是解决复杂问题的首选语言。深度网络、卷积网络或长短期记忆（LSTM）都可以编程，但它们的实现需要大量时间。这超出了我们书的范围，我们将其留给未来。神经网络的术语源于它们的原始目的：模拟人类脑的功能。该模型是微观的，显式地模拟每个神经元信号如何跨越网络传播；此外，它赋予了神经网络某种风味。

## 引言
