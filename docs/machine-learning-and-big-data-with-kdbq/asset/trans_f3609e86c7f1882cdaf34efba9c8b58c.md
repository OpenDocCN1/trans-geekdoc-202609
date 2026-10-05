

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

```
(matEx mmu eigenvectors[0])eigenvalues[0]
```
0.1980295 -0.6931033 -0.6931033 -2.6477e-09
```
(matEx mmu eigenvectors[1])eigenvalues[1]
```
0.2357023 -0.2357023 0.942809 3.527864e-09
```
(matEx mmu eigenvectors[2])eigenvalues[2]
```
0.9074425 -0.1814885 0.362977 0.108891
```
(matEx mmu eigenvectors[3])eigenvalues[3]
```
1 -1.777885e-08 0.06545e-08 -2.063043e-10

事实上，特征向量是在数值精度范围内恢复的。我们为什么没有将特征向量与其恢复的值进行比较呢？

最后，我们将函数封装在一个数值套件中，它接受矩阵并返回按降序排列的特征向量列表以及对应的特征值列表。这些值封装在字典中：

```
.quantQ.mat.eigenSystem:[matt]
// -- 输入矩阵
// 设置默认桶
bucket:(`matrix' maxCounts$thresholdZero()![mat;
  0000;10e-10]);
// 求解特征值
bucket:quantQ.mat.algoQR()/[[continue]];bucket);
// 提取特征值
eigenvalues:quantQ.mat.extractEigenQR[bucket];
// 求解特征向量
evectors::quantQ.mat.eigenIteration[mat;;e-10;10000] each
  -- 特征值;
// 输出桶
:(eigenvalues`eigenvectors)!(eigenvalues;eigenvectors));
```

最后，我们得到了矩阵特征系统的完整解：

```
flip .quantQ.mat.eigenSystem[matEx]
```

| eigenvalues | eigenvectors | |
| :--- | :--- | :--- |
| 8 | 0.1980295 | -0.6931033 | 3.884289e-009 |
| 3 | 0.2357022 | -0.2357023 | 0.9428091 | -5.808747e-017 |
| 2 | 0.9074425 | -0.1814885 | 0.362977 | 0.1088931 |
| 1 | 1 | -1.252761e-099 | 2.44023e-010 | 8.945528e-010 |

# 特征系统与 PCA 341

我们鼓励读者查看提供的函数并提出泛化建议。改进所提供算法的明显地方在于我们在拥有精确特征值的情况下对其进行了扰动。更合适的解决方案是直接使用精确的特征值。当存在退化特征值时，算法无法完美工作。这是一个可以改进的地方。

# 16.4 数据矩阵与主成分分析

主成分分析 (PCA) 是一种广泛的统计技术，它将一组数据转换为一个新的正交基，使得新基的方向根据其对整体矩阵的方差贡献进行排序。这是由 Pearson (1901) 引入的。在本节中，我们考虑一个 $p$ 维的特征向量，其中每个特征被观测了 $n$ 次。令 $n \times p$ 的数据矩阵为 $X$。首先，我们讨论数据矩阵及其属性，然后利用这些发现引入 PCA。

# 16.4.1 数据矩阵

通常情况下，数据矩阵 $X$ 是矩形的——不一定是方阵。正如我们在之前的段落中看到的，特征值对于矩形矩阵是没有定义的。因此我们有另一个密切相关的：奇异值。对于矩形矩阵 $X$，左右奇异值分别是矩阵 $X^TX$ 和 $XX^T$ 特征值的平方根。这些特征值的特征向量分别被称为右向量和左向量。如果 $X$ 是数据矩阵，这些矩阵 $X^TX$ 和 $XX^T$ 在统计学上究竟意味着什么？

