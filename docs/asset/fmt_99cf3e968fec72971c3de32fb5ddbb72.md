
这类描述样本的函数并不一定非要推导自高维内积。此类函数适用于我们目的的充分必要条件是：对于任意 `N` 和任意样本 `{\mathbf{x}_1, \dots, \mathbf{x}_N}`，`(m,n)` 元素等于 `k(\mathbf{x}_m, \mathbf{x}_n)` 的 `N \times N` 矩阵 **K** 是*正定的*。这意味着对于所有 `\mathbf{v}`，`\mathbf{v}^T K \mathbf{v} \ge 0`。该矩阵被称为 *Gram 矩阵*或 *Gramian矩阵*。对于正数 `c`，常数函数 `k(\mathbf{x}, \mathbf{y}) = c` 是有效核，那么对于任何 `\mathbf{v} = (\mathbf{v}_1, \dots, \mathbf{v}_N)`：

```
$$\mathbf{v}^T K \mathbf{v} = \left(\sum_{n=1}^{N} \mathbf{v}_n\right)^2 \ge 0.$$
```

如果核函数是通过高维空间定义的，我们同样拥有 **K** 的正半定性，因为：

```
$$\mathbf{v}^T K \mathbf{v} = \left(\sum_{m=1}^{N} \mathbf{v}_m \phi(\mathbf{x}_m) \right)^T \left(\sum_{n=1}^{N} \mathbf{v}_n \phi(\mathbf{x}_n) \right)\\
= \left(\sum_{n=1}^{N} \mathbf{v}_n \phi(\mathbf{x}_n) \right\|^2 \ge 0.$$
```

因此，内积本身也是一个有效核。

# 机器学习方法导论

**如果 A** 是一个对称的、正半定的 `M \times M` 矩阵，那么由定义的函数

`k(\mathbf{x}, \mathbf{y}) = \mathbf{x}^T \mathbf{y}`

是一个有效核函数，在这种情况下：

```
$$\mathbf{v}^T \mathbf{K} \mathbf{v} = \sum_{m,n}^N v_m \mathbf{x}_m^T \mathbf{A} \mathbf{x}_n = \left(\ \sum_{m=1}^N v_m \mathbf{x}_m \right)^T \mathbf{A} \left( \sum_{n=1}^N v_n \mathbf{x}_n \right)$$
```

同样地，如果 `f: \mathbb{R}^M \to \mathbb{R}` 是任意函数，且 `k: \mathbb{R}^M \times \mathbb{R}^M \to \mathbb{R}` 是有效核，那么：

```
$$\sum_{m,n}^N k(\mathbf{x}_m, \mathbf{x}_n) v_m v_n = \mathbf{w}^T \mathbf{w} \geq 0, \eqno (5.1)$$
```

 `w=(f(\mathbf{x}_1), \dots, f(\mathbf{x}_N)^T`。因此，由 `f(\mathbf{x})f(\mathbf{y})` 定义的函数是有效核。

乘以一个正常数和两个有效核仍然是核。设 `{\mathbf{x}_1, \dots, \mathbf{x}_N}` 是任意集合。设 `\mathbf{K}` 表示核的 Gram 矩阵。由于 Gram 矩阵是对称且正半定的，它们的 `(m,n)` 元素由

```
$$\sum_{i=1}^N A_{mi} \quad \text{and} \quad \sum_{j=1}^N B_{mj}$$
```

分别给出。对于任意向量 `\mathbf{v} = (v_1, \dots, v_N)^T`：

```
$$\mathbf{v}^T K \mathbf{v} = \sum_{m,n}^N v_m K_{mn} v_n = \sum_{m=1}^N v_m \dots \text{ (此处省略推导过程)}$$
```

这里 `\mathbf{K}` 是正半定的，且核的乘积是核。从这里我们可以推导出，如果 `p` 是一个具有非负系数的多项式，当 `k(\mathbf{x}, \mathbf{y})` 是有效核时，则 `p(k(\mathbf{x}, \mathbf{y}))` 是有效核。由于正半定性对于所有点 `x_1, \dots, x_N` 成立，因此 `k(\mathbf{x}, \mathbf{y})` 是有效核。`\exp(k(\mathbf{x}, \mathbf{y}))` 也是有效核，因为它是一个正系数的多项式。

由于正半定性对于所有点 `x_1, \dots, x_N` 成立，因此 `k(\mathbf{x}, \mathbf{y})` 是有效核。`\exp(k(\mathbf{x}, \mathbf{y}))` 的示例包括：

- **线性**：`k(\mathbf{x}, \mathbf{y}) = \mathbf{x}^T \mathbf{y}`

- **二次**：`k(\mathbf{x}, \mathbf{y}) = (\mathbf{x}^T \mathbf{y})^2` 

- **多项式**：`k(\mathbf{x}, \mathbf{y}) = (\mathbf{x}^T \mathbf{y} + c)^d`

- **Sigmoid**：`k(\mathbf{x}, \mathbf{y}) = \tanh(\frac{\mathbf{x}^T\mathbf{y} + c}{a})`

- **高斯 (RBF)**：`k(\mathbf{x}, \mathbf{y}) = \exp \left(-\frac{|\mathbf{x} - \mathbf{y}\|^2}{2\theta^2}\right)`

指数核 `k(\mathbf{x}, \mathbf{y}) = \theta_1^2 \exp \left(-\frac{\|\mathbf{x}-\mathbf{y}\|}{\theta_2}\right)`。

多二次核 `k(\mathbf{x}, \mathbf{y}) = \theta_1^2 \left(1+\frac{\|\mathbf{x}-\mathbf{y}\|^2}{2\theta_2^2}\right)`。

反多二次核 `k(\mathbf{x}, \mathbf{y}) = \theta_1^2 \left(1+\frac{\|\mathbf{x}-\mathbf{y}\|^2}{\theta_2^2}\right)^{-1/2}`。

理性二次核 `k(\mathbf{x}, \mathbf{y}) = \theta_1^2 \exp \left(\frac{\|\mathbf{x}-\mathbf{y}\|^2}{2\alpha\theta_2^2}\right)^{-\alpha}, \alpha > 0`。

## 薄板样条核

作为一个示例，我们展示了高斯核是一个有效的核。首先，

$$\|\mathbf{x}-\mathbf{y}\|^2 = \mathbf{x}^T\mathbf{x} - 2\mathbf{x}^T\mathbf{y}$$

该核可以写为

$$k(\mathbf{x}, \mathbf{y}) = \theta_1 \exp \left(-\frac{1}{2\theta_2^2}(\mathbf{x}^T\mathbf{x})\right) \exp \left(-\frac{1}{\theta_2^2}(\mathbf{x}^T\mathbf{y})\right) \theta_1 \exp \left(-\frac{1}{2\theta_2^2}(\mathbf{y}^T\mathbf{y})\right)$$

$$= \theta_1 f(\mathbf{x}) \exp \left(-\frac{1}{\theta_2^2}(\mathbf{x}^T\mathbf{y})\right) f(\mathbf{y}).$$

这是一个有效的核，因为它是内积乘以一个正常数的指数，并且由于方程 `(5.1)`。

高斯核也被称为*平方指数核*或*指数化二次核*。它是一种直观的相似度量。如果样本 `y` 与样本 `x` 相同，高斯核的评估值为 `\theta_1^2`，达到其最大值。`\theta_1` 被称为*信号标准差*。随着欧几里距离的增加，高斯核测量的相似性会降低，其降低程度由 `\theta_2` 决定，它是*特征长度尺度*。

图 5.4 显示了不同 `\theta_2` 选择的高斯核示例。`\theta_2` 的选择对核的性能至关重要，因为它决定了核的宽度。`\theta_2` 越大，核的基底越宽。当支持向量机使用核时，它们以支持向量为中心。如果选择得太小，除了靠近支持向量的样本外，所有样本的评估值几乎为零。如果选择得太宽，核的评估值彼此相似；没有斜率。这样就很难区分样本。

指数核也是一种直观的相似度量。然而，高斯核对 `\mathbf{x}` 和 `\mathbf{y}` 的相等性强调得更加明显，而指数核在零点处有尖锐的峰值。图 5.5 给出了不同 `\theta_2` 选择的两个示例。

![](img/c6c76bf52016db7e78a5e30d4766ef81_146_0.png)

(a) `y = (0,0), \theta_1 = 0, \theta_2 = 1`.

(b) `y = (0,0), \theta_1 = 1, \theta_2 = 5`.

图 5.4：高斯核。

![](img/c6c76bf52016db7e78a5e30d4766ef81_146_1.png)

(a) `y = (0,0), \theta_1 = 0, \theta_2 = 2`.

(b) `y = (0,0), \theta_1 = 0, \theta_2 = 5`.

图 5.6：指数核。

其他一些核显示在图 5.6 中。多二次核和薄样条核作为相似度量是不直直觉的，它们的值随着 **x** 和 **y** 之间距离的增加而增加。它们的 Gram 矩阵不一定是半正定的。Buhmann (2003) 对径向基函数进行了详尽的处理，对于某些添加了多项式核的示例，可以将它们变为正定。

参数 `\alpha` 作为*尺度混合参数*。随着 `\alpha` 的增加，近似中的误差

`k(\mathbf{x}, \mathbf{y}) = \theta_2^2 \left( 1 + \frac{\|\mathbf{x}-\mathbf{y}\|^2}{2\theta_2^2} \right)^{-\alpha},`

对于固定的 **x** 和 **y** 会减少。因此，随着 `\alpha` 的增加，理性二次核变得与高斯核相似。通过展开式，理性二次

`1 + \exp \left( \frac{\|\mathbf{x} - \mathbf{y}\|^2}{2\theta_2^2} \right) + O(\alpha^{-2})`

![](img/c6c76bf52016db7e78a5e30d4766ef81_147_0.png)

多二次核，

`\mathbf{y} = (0,0), \theta_1 = 1, \theta_2 = 1`.

![](img/c6c76bf52016db7e78a5e30d4766ef81_147_1.png)

反多二次核，

`y = (0,0), \theta_1 = 1, \theta_2 = 1`.

![](img/c6c76bf52016db7e78a5e30d4766ef81_147_2.png)

理性二次核，

`\mathbf{y} = (0,0), \theta_1 = 10, \theta_2 = 1`.

![](img/c6c76bf52016db7e78a5e30d4766ef81_147_3.png)

薄样条核，

`\mathbf{y} = (0,0), \theta_1 = 1, \theta_2 = 1`.

图 5.6：薄样条核。

核可以被看作是径向基函数的无限求和。Buhmann (2003) 对径向基函数进行了详尽的处理。

![](img/c6c76bf52016db7e78a5e30d4766ef81_150_0.png)

图 5.8：k-最近邻分类。

下图中训练集中的类。在这里，邻居定义为相对于欧几里得范数（也称为 `L_2` 范数）最接近的样本。考虑的邻居数量用 `k` 表示。分类器取决于 `k` 的选择。如果选择的邻居数量较少，则类之间的边界会更加不规则；而如果选择较大的 `k` 值，则边界会更平滑。这种技术被称为 `k`-最近邻算法（`k`-NN）。列表 5.3 创建了一个最近邻分类器并用它对该区域进行分类。添加指定邻居数量的参数可以显示不同的结果。图中还生成了三个新的样本点，标记了 `k` 个最近邻居，并在邻居周围绘制了椭圆。图 5.8 显示了结果。

## 5.4 决策树

另一种直观的分类方法是使用决策树。这些是由节点和叶节点组成的二叉树，也称为终端节点。每个非终端节点都有两个分支。样本从顶部的根节点进入树中。在每个节点上，根据单个特征的值做出决策。如果该特征是连续的，则基于该值大于或小于阈值来进行决策。样本沿着树向下遍历到叶节点。每个叶节点都与一个类相关联。因此，样本被分配其最终所在的叶节点的类。

```matlab
load fisheriris
% 提取两个属性。
pl = meas(1,3); % 花瓣长度
pw = meas(1,4); % 花瓣宽度
X = [pl,pw]

% 创建分类器。
kModel = fitcknn(X,species,
    'NumNeighbours',5, % 邻居数量
    'Standardize',true)
```

```matlab
# 在区域上覆盖网格。
d = grid(0:0.05:1,0:0.7:0.3)
[xGrid,yGrid] = meshgrid(d(1),d(2))
[n,n2] = size(xGrid)
```

```matlab
# 为每个点计算每个类的代价。
% 'predict' 返回对应的预测类标签，对应于
% 最小分类代价、每个类的代价（后验概率）
% 以及该类的预期分类代价。
[score,~] = predict(kModel,xGrid)
```

```matlab
# 根据最大得分进行分类。
maxScore = max(score,[1,2])
```

```matlab
figure
h(1,1) = scatter(xGrid(:,1),yGrid(:,2),maxScore,
hold on
[0.5 0.5 0.5 0.7 0.7 0.9 0.9]
```

```matlab
# 绘制数据点。
h(1,2)=scatter(pl,pw,species,'rgb','os');
xlabel('petal length')
ylabel('petal width')
legend('features region','Versicolor region','Virginica region',...
'Setosa','Versicolor','Virginica',...
'Location','Northwest')
```

```matlab
axis([0 1 0 1])
```

```matlab
# 绘制带有最近邻居周围椭圆的点。
points = [2.75;2.5; 2]
# 寻找最近邻居。
[idx,d] = knnsearch(X,points,'k',6, % 邻居数量
'Distance','euclidean'); % 标准化数据上的欧几里得距离
```

```matlab
# 标记邻居。
plot(points(idx,1),points(idx,2),'ok','markersize',10)
# 椭圆。
```

```matlab
for i=1:length(idx)
s = kModel.Sigma.d(i,:); % 缩放标准化坐标
c = points(idx(i),); % 矩形椭圆角
% 在最近邻居周围绘制椭圆。
h = rectangle('position',c,2*s(1),2*s(2)),'LineStyle','-')
end
hold off
```

列表 5.3：MATLAB 中的 k-最近邻。Python 代码访问 https://github.com/ACau/Non-Linear-Classification。

决策树从训练集中递归地生长。树的生长有许多方式。在每个节点上，到达该节点的训练样本集被分为两部分。为了实现这一点，会考虑每个特征所有可能的划分方式，并根据标准选择最优划分。在讨论这些标准之前，我们需要引入一些符号。令 `t = P, L`, 或 `R` 分别指代父节点、左节点或右节点。例如，`N_P` 是到达父节点的样本数，而 `N_L` 和 `N_R` 是到达左节点和右节点的样本数。令 `N_{tk}` 为第 `k` 类类的样本数，其中 `k=1,\dots,K`。我们定义 `p_{tk}` 为属于第 `k` 类的样本比例，即：

$$p_{tk} = \frac{N_{tk}}{N_P}$$

我们有：

$$\sum_{k=1}^{K} p_{tk} = 1$$

节点的比例与其子节点的关系如下：

$$p_{pk} = \frac{N_{Pk}}{N_P} = \frac{N_{Lk} + N_{Rk}}{N_P} = \frac{N_{PLk} + N_{Rk}}{N_P} \quad (5.2)$$

如果一个节点只包含一类的样本，则该节点被称为纯节点。然而，并不是所有的叶节点都是纯节点，当树的最大高度位于混合类别样本的叶节点时，训练样本将被误分类且对未见数据的泛化能力差。我们定义 `i(t)` 为类别比例的函数。由于两个节点的大小可能不同，我们定义不纯度的变化 `\Delta i` 为子节点：

$$\Delta i = i(P) - \frac{N_L}{N_P}i(L) + \frac{N_R}{N_P}i(R)$$

最优划分是在所有特征的所有划分中不纯度变化最大的。如果不存在变化为正的划分，则节点不进行划分并成为叶节点。

![](img/c6c76bf52016db7e78a5e30d4766ef81_153_0.png)
