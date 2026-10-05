

# 最近邻居

让我们考虑如下格式的数据集：
tableFunction:([] coord1:"f($);coord2:"f($);coord3:"f($);...; val:"f($));

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
（抱歉，由于长度限制，后续逻辑翻译如下）

```
:(1%sum exp neg (1%beta) * .quantQ.weightedL2norm[coordX;weights]
-- each coordY)*sum
valueY*exp neg (1%beta)* .quantQ.knnL2norm[coordX;weights]
-- each coordY);
;
```

