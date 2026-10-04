

158 T. P. Fowder, L. Babooram, M. N-U-D-Ibn Nazir Rosun and M. Indoondonman

线性回归模型可以通过添加多项式项来修改，得到如下的多项式回归模型 [25]:

```
$y = \beta_0 + \beta_1x + \beta_2x^2 + \beta_3x^3 + \dots + \beta_nx^k + \varepsilon \quad (3.15)$
```

其中，

- $y$ - 变量
- $\beta_0$ - 截距
- $k$ - 最高次数
- $\beta_1, \beta_2, \beta_3, \dots, \beta_n$ - 系数
- $x$ - 变量
- $\varepsilon$ - 误差

## 简明示例 5

在这个示例中，六辆汽车的重量和里程数通过二阶（二次）多项式回归相关。记录的数据如表 3.11 所示：

## 表 3.11. 多项式回归-记录数据

| 重量（磅），x | 里程（每加仑里程），y |
|---|---|
| 1835 | 26 |
| 1970 | 31 |
| 2372 | 24 |
| 3086 | 14 |
| 3504 | 18 |
| 4341 | 15 |

可以使用最小二乘法得到回归线，该方法通过求解形式为 $Ma = b$ 的线性方程组来实现 [29]：

```
$$\begin{bmatrix} \sum_{i=1}^{N} x_i & \sum_{i=1}^{N} x_i^2 & \dots & \sum_{i=1}^{N} x_i^k \\ \sum_{i=1}^{N} 1 & \sum_{i=1}^{N} x_i & \dots & \sum_{i=1}^{N} x_i^k \\ \vdots \\ \sum_{i=1}^{N} x_i^k & \sum_{i=1}^{N} x_i^{k+1} & \dots & \sum_{i=1}^{N} x_i^{2k} \end{bmatrix} \begin{bmatrix} \beta_0 \\ \beta_1 \\ \vdots \\ \beta_k \end{bmatrix} = \begin{bmatrix} y_i \\ y_i \\ \vdots \\ y_i \end{bmatrix}$$
```

## 机器学习算法

此示例中的线性方程如下：

```
$$\begin{bmatrix} 6 & 1.71 \times 10^4 & 5.35 \times 10^7 \\ 1.71 \times 10^4 & 5.35 \times 10^7 & 1.81 \times 10^{11} \\ 5.35 \times 10^7 & 1.81 \times 10^{11} & 6.54 \times 10^{14} \end{bmatrix} \beta_0 = \begin{bmatrix} 128 \\ 3.37 \times 10^5 \\ 9.79 \times 10^8 \end{bmatrix}$$
```

然后可以使用行列式计算每个系数，如下：

```
$$\beta_i = \frac{det(M_i)}{det(M)}$$
```

其中，$M_i$ 是通过将矩阵 $M$ 中的第 $i^{th}$ 列替换为列向量 $b$ 构建的。在此处，$M_0, M_1$ 和 $M_2$ 如下：

```
$M_0 = \begin{bmatrix} 128 & 1.71 \times 10^4 & 5.35 \times 10^7 \\ 3.37 \times 10^5 & 5.35 \times 10^7 & 1.81 \times 10^{11} \\ 9.79 \times 10^8 & 1.81 \times 10^{11} & 6.54 \times 10^{14} \end{bmatrix}$
$M_1 = \begin{bmatrix} 6 & 128 \\ 1.71 \times 10^4 & 3.37 \times 10^5 & 5.35 \times 10^7 & 1.81 \times 10^{11} \\ 5.35 \times 10^7 & 9.79 \times 10^8 & 6.54 \times 10^{14} \end{bmatrix}$
$M_2 = \begin{bmatrix} 6 & 128 \\ 1.71 \times 10^4 & 5.35 \times 10^7 \\ 3.37 \times 10^5 & 5.35 \times 10^7 & 1.81 \times 10^{11} & 9.79 \times 10^8 \end{bmatrix}$
```

使用上述矩阵的行列式，系数的计算如下：

```
$\beta_0 = \frac{det(M_0)}{det(M)} = \frac{7.68 \times 10^{21}}{1.77 \times 10^{20}} = 43.33$
$\beta_1 = \frac{det(M_1)}{det(M)} = \frac{-1.73 \times 10^{18}}{1.77 \times 10^{20}} = -0.0098$
$\beta_2 = \frac{det(M_2)}{det(M)} = \frac{1.16 \times 10^{14}}{1.77 \times 10^{20}} = 6.59 \times 10^{-7}$
```

因此多项式模型可以写为：

```
$y = 43.33 - 0.0098x + (6.59 \times 10^{-7})x^2$
```

3000 磅汽车的里程估计如下：

```
$Y = 43.33 - 0.0098(3000) + (6.59 \times 10^{-7})(3000)^2 = 19.86$ MPG
```

160 T. P. Fowdar, L. Babooram, M. N-U-Dbn Nazir Rosun and M. Indoondonman

MATLAB 统计和机器学习工具箱中的 `fitlm` 函数可用于拟合多项式回归。多项式回归函数的语法如下：

```
mdl= fitlm(X,Y,modelspec)
```

函数的输入如下：

- X：预测变量。
- Y：响应变量。
- modelspec：模型规格。对于多项式回归应设置为 'polyijk'，其中 i, j 和 k 取第一、第二和第三预测变量的最高次数。在单预测的情况下，应设置值 i。例如，对于最高次数为 3 的单预测场景使用 'poly3'。然后可以使用 MATLAB 统计和机器学习工具箱中的相同 `predict` 函数来预测测试预测的响应。

下面是简明示例中回归的 MATLAB 仿真。首先将训练数据集加载到 MATLAB 工作区，然后使用列表 3.20 中的代码使用 `fitlm` 函数拟合指定次数的多项式回归模型。

## 列表 3.20. 多项式回归- 定义数据集

| X = [1835 1970 2372 3086 3504 4341]; |
| y = [26 31 24 18 15]; |
| mdl = fitlm(X,Y,poly2); % 拟合多项式回归模型 |

可以使用列表 3.21 中的代码绘制回归线。

## 列表 3.21. 多项式回归- 可视化回归线

| R=[1800:4500]; % 定义回归线的点数组 |
| ypred = predict(mdl,R); % 预测 C 中汽车重量的里程 |
| plot(X,y,'',R,ypred,'-') % 画训练数据集及回归线 |
| xlabel ('Weight') |
| ylabel('Mileage') |
| legend('Data','Regression Line') |

MATLAB 代码生成的多项式回归可视化如图 3.15 所示。可以观察变量与响应之间存在曲线关系。

![](img/2b52fde0e707e8c2f05a10309f8982_172_0.png)

图 3.15. 多项式回归- MATLAB 上的可视化。

3000 磅汽车的里程不是使用列表 3.22 代码预测的训练数据集的一部分。结果输出在 MATLAB 命令行窗口，如图 3.16 所示。仿真结果与简手工计算的结果略有不同，因为后者使用的位数有限。

## 列表 3.22. 多项式回归- 预测里程

```
ynpred = predict(mdl,3000) % 预测 3000 磅汽车的里程
```

162 T. P. Fowdur, L. Babooram, M. N-D-Ibn Nazir Rosun and M. Indoonondonun

```
Command Window
>> PolynomialRegression

ypred =
17.9751
>>
```

图 3.16. 多项式回归- 预测结果。

## 3.4.1.4. 朴贝叶斯

贝叶斯分类器是使用公式 (3.16) 给出的朴贝叶斯概率定理将数据分类相应类别的数据分类器 [31]。朴贝叶斯分类器假设每个特征的值都是相互独立的。与其他数据分类器相比，它们速度较快，因此可以用于实时预测。

$P(B|A) = \frac{P(A \cap B)}{P(A)}$

其中，

- $P(B|A)$ - 在 A 为真时 B 发生的条件概率。
- $P(A|B)$ - 在 B 为真时 A 发生的条件概率。
- $P(A)$ - 事件 A 的概率。
- $P(B)$ - 事件 B 的概率。

