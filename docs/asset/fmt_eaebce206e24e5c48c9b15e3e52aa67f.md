
```
$$\theta_{(i,j)} = \arctan\left(-\frac{a_{(i,i)}}{a_{(i,j)}}\right). (16.17)
```

## 16.2.2 特值的 QR 算法

QR 算法允许我们找到方阵的所有特征值。其工作原理如下：

- 初始化 `$A_0 = A$`。

- 对于 `$k = 0, 1, 2, \dots$`：

- 计算 QR 分解 `$A_k = Q_k R_k$`。

- 设置 `$A_{k+1} = R_k Q_k$`。

`$R_k$` 的对角线元素收敛于 `$A$` 的特征值。

## 特征系统与 PCA

QR 算法有一个明显的缺点：如果矩阵具有复特征值，该方法就会失效。在这种情况下，需要更高级的方法。本节的目的是向读者介绍特征系统。为了涵盖所有可能性，我们不得不花费整本书的主题。

## 16.2.3 逆迭代

假设我们已经掌握了全部实特征值的知识。我们的目标是找到对应的特征向量。我们将关注逆（幂）迭代。以下步骤需要将特征值 `$\lambda'$` 与矩阵关联：

- 计算更新后的向量：`$v_{k+1} = (A-\lambda'I)^{-1}v_k$`。

- 算法以迭代进行，`$k$` 表示迭代步，在 `$k = 0$` 时：

- 通过其范数归一化向量 `$v_{k+1}$`：`$v_{k+1} = v_{k+1}/\|v_{k+1}\|$`。

- 向量 `$v_{k+1}$` 收敛于 `$v'$`。

接下来我们将实现这两种方法。

## 16.3 特征系统计算的实现

我们实现了计算维度为 `$p$` 的实矩阵 `$A$` 的特征值系统的数值过程。首先，我们需要生成一个单位矩阵：

```
.quantQ.mat.diagMatrix:[dim]
// dim -- 对角矩阵的维度
:"f$v/v:til dim
);
```

它的运行结果符合预期：

```
unitMatrix::quantQ.mat.diagMatrix[4];
unitMatrix
```

| 1 0 0 0 |

| 0 1 0 0 |

| 0 0 1 0 |

| 0 0 0 1 |

我们将单位矩阵存储在一个临时变量中，以便进行后续的数值检查。出于好奇，我们来提供一种单位矩阵的另一种实现方式：

```
.quantQ.mat.diagMatrix2:[dimM]
// dimM -- 对角矩阵的维度
:[x;y]t:x:0; t[y]:1.0; t[dimM] each til dimM;
);
```

> 定义与第一个完全相同，正如从以下内容所示：

```
unitMatrix~quantQ.mat.diagMatrix2[4]
```

1b

我们鼓励读者对比并测试上述两种方法的时间，并尝试使用其他动词和/或操作符给出更多的定义。

QR 算法的直观原理基于 Givens 旋转（Givens rotation）。我们实现了一个函数，它接受四个参数：矩阵维度、两个坐标 `$i$` 和 `$j$` 以及旋转角 `$\theta$`，并返回带有 Givens 旋转的矩阵：

```
.quantQ.mat.givensRotation:[dimM;i;j;theta]
// dim1 -- 矩阵维度
// i -- dim 到 dim-1
// j -- dim2 到 dim-1
// theta -- 旋转角
// 单位矩阵
givens:quantQ.mat.diagMatrix[dimM];
// 插入 cos
givens[i;i]:cos[theta];
givens[j;j]:cos[theta];
```

## 特征系统与 PCA 333

```
// 插入 sin
givens[min[(i;j)];max[(i;j)]]=neg[sin[theta]]
givens[max[(i;j)];min[(i;j)]]=sin[theta]
// 旋转矩阵
:givens;
;
```

让我们在 4 维空间中使用 Givens 矩阵，在第 2 轴和第 4 轴跨成的空间内进行 `$\pi/4$` 角的旋转：

```
.quantQ.mat.givensRotation[4;1;3;0.25*acos[-1]]
```

| 1 0 |

| 0 0.7071068 -0.7071068 |

| 0 1 |

| 0 0.7071068 0.7071068 |

矩阵的形式符合预期。让我们用这样一个矩阵来旋转单位矩阵：

```
.quantQ.mat.givensRotation[4;1;3;0.25*acos[-1]] mmu unitMatrix
```

| 1 0 |

| 0 0.7071068 -0.7071068 |

| 0 1 |

| 0 0.7071068 0.7071068 |

旋转后的单位矩阵等于旋转矩阵 `$q$`。该示例也提醒了我们用于两个矩阵相乘的 `mmu` 动词。

### 16.3.1 QR 分解

让我们继续 QR 分解。`QRdecomp` 函数实现了该过程。输入是我们想要分解的矩阵。函数的输出是三个矩阵：原始矩阵、旋转后的矩阵和旋转矩阵。函数本身是一个迭代过程，我们遍历了所有需要设置为零的坐标。我们将迭代保留在主函数内部，没有将其分离。按照定义运行该函数是至关重要的，我们在算法描述中已经强调了这一点。

```
quantQ.mat.QRdecomp:[mat]
// 输入矩阵
// 计算矩阵的维度
dimM:count[mat]
// 需要遍历的坐标列表
coord: range[[dimM;x]] {{x;y] (y;x)}'[t where x<t:reverse til dimM]][dimM]; each til dimM;
// 输入矩阵
inputMat:mat;
// 初始化旋转矩阵
rotMat::quantQ.mat.diagMatrix[dimM]
// 计数器
counter:;
```

### 334 用于迭代过程的四个变量的 bucket 数据科学

我们将 QR 分解函数应用于两个旋转矩阵的乘积。第一个矩阵作用于第 2 和第 4 坐标空间，角度为 `$\pi/4$`，而第二个矩阵作用于第 2 和第 3 坐标空间，角度同样为 `$\pi/4$`。

```
output:quantq.mat.QRdecomp[quantq.mat.givensRotation[4;1;3;0.25*acos
  -> [-1]] mmu...quantq.mat.givensRotation[4;1;0.25*acos[-1]];
```

我们将输出结果保存在一个变量中，其中包含三个矩阵，我们将逐一探索。首先是输入矩阵：

```
output[`matrix`
```

| 1 0 0 |

| 0.5 -0.5 -0.7071068 |

| 0.7071068 0 0 |

| 0.5 -0.5 -0.7071068 |

我们鼓励读者验证此矩阵对应于旋转。函数结果中的第二个矩阵应该是上角矩阵。由于我们使用 Givens 旋转创建了矩阵，结果矩阵将是（上角的）：

```
output[`matrixRotated`
```

![](img/977581128bd0df8568d3c69d424358.png)

## 特征系统与 PCA 335

1 0 0 0

0 1 0 0

0 0 1 0

0 0 0 1

最后，函数返回的最后一个矩阵是旋转矩阵：

```
output[`rotationMatrix`]
```

1 0 0 0

0 0 0.7071068 0.5

0 -0.5 0.7071068 -0.5

该旋转矩阵对应于两次旋转：首先，在第 2 和第 3 坐标跨成的空间内进行 `$-\pi/4$` 角旋转。然后，在第 2 和第 4 空间内进行 `$-\pi/4$` 角旋转。我们可以通过以下方式验证：

```
.quantQ.mat.givensRotation[4;1;neg 0.25*acos[-1]] mmu .quantQ.mat.givensRotation[4;3;neg 0.25*acos[-1]] = output[`rotationMatrix`]
```

验证了 QR 分解的功能。我们使用 QR 分解获取特征值。QR 算法是一个迭代过程，迭代采用 QR 分解并更新矩阵。首先，读取输入的矩阵字典。找到 QR 上三角矩阵和正交矩阵。此外，它包含一个计数器以便控制：

```
.quantQ.iterQR:[bucket]
// bucket 包含矩阵和计数器
// QR 分解
bucketTMP: quantQ.mat.QRdecomp[bucket[`matrix`]]
// 定义 Q 和 R
Q: flip bucketTMP[`rotated`]
R: bucketTMP[`rotationMatrix`]
// 定义新矩阵，与原始矩阵类似
bucket[`matrix`]:R mmu Q;
// 增加计数器
bucket[`counter`]:bucket[`counter`]+1
// 返回 bucket
bucket:
};

1b

让我们定义本章剩余部分使用的示例矩阵。

## 336 数据科学

matExa: (1.0 -2.0 0.0 5.0;0.0 7.0 1.0 5.0;0.0 4.0 4.0;0.0 0.0 2.0)

1 -2 0 5
0 7 1 5
0 4 0
0 0 2

初始化 bucket 以运行函数：

```

bucket(`matrix`-counter(matExa;0));

```

并显式地运行十次迭代：

```

bucket.(quantQ.mat.iterQR/)[10;bucket];

bucket[]

```

得到以下输出：

| 1 1.414216 1.414165 5 |
| 0 8.000803 -2.999828 3.535655 |
| 0 0.0001718623 2.999897 -3.535412 |
| 0 0 2 |

矩阵的形状正接近上角矩阵。主对角线下的元素非常小。我们需要将迭代封装进函数中，`algoQR` 就是这样一个函数，它接受一个包含待分解矩阵、计数器以及两个控制变量的字典：最大迭代次数和数值精度：

```

quantQ mat.algoQR:[bucket]

// bucket --包含矩阵、计数器、最大迭代次数和

// 精度

// QR 分解

bucketTMP: quant.mat.QRdecomp[bucket[matrix]];

// 定义 Q 和 R

Q: flip bucketTMP[matrixRotated];

R: bucket[matrix];

// 定义新矩阵，与原始矩阵类似

bucket[`matrix`]:R manu Q;

// 增加计数器

bucket[counter]:bucket[counter]+1;

// 判断是否继续

// 准则 1：计数

$bucket[counter]<bucket[maxCounts],bucket[`continue]:0b;

// 准则 2：精度

$bucket[thresholdZero]:max abs {{matt;coord] matt[first[coord]], last[

-- coord]]bucket[`matrix];

each raza [[dimM;x] {{x;y); (y;x)}x't where x<reverse til

-- dimM

][dimM] each tail count[bucket[matrix];bucket[`continue]:0b];

bucket;

```

## 特征系统与 PCA 337

函数通过 QR 算法迭代地变换矩阵。迭代停止有两个检查条件。如果迭代次数超过阈值或对角线下的数字处于通用数值精度范围内，算法将停止。

我们初始化输入的 bucket：

```

bucket::('matrix`counter`maxCounts`thresholdZero`continue)!(matExa;0j;10000

j:1e-10));

```

并运行函数，我们感兴趣的是上角矩阵：

```

bucket::quantQ.mat.algoQR/){x[`continue`];bucket;

bucket[`matrix` ]

```

产生的矩阵如下：

| 1 -1.414214 5 |
| 0 8 -3 1.414214 3.535534 |
| 0 .708607e-011 3 -3.535534 |
| 0 0 2 |

对角线下的元素小于精度。我们提供矩阵 matExa 的特征值。最后，我们提供一个程序，从 bucket 中提取特征值并按降序排序：

```

.quantQ.mat.extractEigenQR::[bucket]

// bucket -- algoQR 的结果

// 提取对角线并排序

:desc {x[y,y]}[bucket[`matrix`,] each til count bucket[`matrix`];

;

```

此时特征值正在产生中：

```

eigenvalues::quantQ.mat.extractEigenQR[bucket]

eigenvalues

```

8 3 2 1f

# 338
# 数据科学

并验证我们所使用的矩阵：

```

.quantQ.mat.normL1[matExa]

```

我们定义了 `inverseIteration` 函数，它接受四个参数：矩阵、数值容差和最大迭代次数。我们对迭代算法的实现使用了逆矩阵 `inv`。使用矩阵求逆的问题出现在我们提供了精确特征值的情况下。在这种情况下，矩阵 (A - λI) 是奇异的，无法求逆。

为了克服迭代算法中的奇异性，我们对特征值引入了扰动。因此，当我们获得精确的特征值时，我们会对其进行扭曲，直到获得一个近似解。对于这样的解，迭代算法可以正常工作并继续进行。在每次迭代的开始，我们对每个 `[invMat]` 执行 `([x=0nf)` 或 `(x=0wf)` 或 `(x=-wf)` 检查。扰动是在初始调用时应用的，因为我们并没有暴露于扰动后的值。该函数直接返回特征向量和特征值。

使用 L1 矩阵数对迭代进行归一化。此外，为了防止特征向量因乘法因子 -1 而翻转，我们强制特征向量的第一个元素为正。该函数从一个随机向量开始，其组件独立地从 [-1;1] 上的均匀分布。在迭代结束时，特征向量通过 L2 范归一化为单位模。

该函数读取如下：

```

quantQ.mat.inverseIteration::[mattIn;eigenValue;toler;maxIter]

// mattIn -- 矩阵

// eigenvalue -- 特征值

// toler -- 数值容差

// maxIter -- 最大迭代次数

// 矩阵维度

dimM=: count mattIn;

// 初始起始向量，随机

vecB[1:1]+=dimMat72.0;

// 设置随机向量的元素为正

$0=first vecB; vecB=: neg vecB;

// 准备桶

bucket::([bucket];

bucket::('matrix'vecB`counter*maxIter*continue)!(

  -> mattIn;eigenValue:toler;0;maxIter:1b));

bucket::([bucket];

// 用于逆迭代的矩阵

inMat:bucket['matrix']-bucket['eigenVal]*.quantQ.mat.diagMatrix[

count[bucket['matrix']]);

// 逆迭代方法适用于非奇异矩阵

$0=sum([x=0nf) or (x=0wf) or (x=-wf) each raza inv[invMat];

// 引入随机扰动

bucket['eigenVal]:bucket['eigenVal]+(1e-7)*(neg[1]+first

  -> 7.0).

```

# 特征系统与 PCA 339

```

vecBOLD:bucketI[`vecB`;

vecB: (1.0%)quantQ.mat.normL[t])*t:(invinvMat) mmu vecBOLD;

// 设置随机向量的元素为正

$0:=first vecB; vecB:=neg vecB;

// 放入桶

bucketI[`vecB`]:vecB;

// 增加计数器

bucketI[`counter`]:bucketI[`counter`]+1;

// 关闭迭代

((max[abs(vecB-vecB)])<bucketI[`tolerance`]) or (bucketI[`n->bucketI[`maxter]`];bucketI[`continue`]:0b);

// 在最后一步，归一化到 L=2

$bucketI[`continue`]:0b;bucketI[`vecB`]:bucketI[`vecB`]*(1.0%sqrt

[sum bucketI[`continue`]:bucketI[`vecB`]])

];

];

// 输出桶

bucketI;

})/{[`continue`]:bucketI;

// 特征向量

:bucketI[`vecB`];

```

我们根据上一节中找到的特征值计算特征向量：

```

eigenvectors:quantQ.mat.inverseIteration(matEa;1e-10;10000] each

eigenvalues

```

并修正特征向量：

```

eigenvectors[0]

```
0.1980295 -0.6931033 -0.6931033 -1.059117e-08
```

eigenvectors[1]

```
0.2357023 -0.2357023 0.942809 5.219755e-09
```

eigenvectors[2]

```
0.9074425 -0.1814885 0.362977 0.108891
```

eigenvectors[3]

```
1 -5.400702e-09 2.054183e-08 -1.031521e-10
```

我们可以通过检查特征向量乘以矩阵并除以相应的特征值来验证特征向量。

# 340

# 数据科学
