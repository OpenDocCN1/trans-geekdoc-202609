

![](img/c6c76bf52016db7e78a5e30d4766ef81_66_0.png)

图 2.21：由于元素限制，**x** 可能位置的单纯形。

当 $\alpha_1 = \dots = \alpha_K$ 时，该分布被称为*对称狄利克雷分布*或*平坦狄利克雷分布*。后者的命名具有误导性，因为只有当所有浓度参数都取值为1时，它才是平坦的。此时，狄利克雷分布变为单纯形上的均匀分布。在这种情况下，

```
$$\text{Dir}(\mathbf{x}) = \frac{\Gamma(K)}{\Gamma(1)\cdots\Gamma(1)} \prod_{k=1}^K x_k^{0}=(K-1)!$$
```

这是单纯形体积的倒数。对于 $K=3$，2单纯形的体积为 1/2。

我们在[图 2.22]中看到，对于 $\alpha=(5,5)^T$，概率质量集中在中心；而对于 $\alpha=(5,2)^T$，它集中在具有最小浓度参数的角的对侧边缘。对于 $\alpha=(5,2)^T$，概率质量集中在浓度参数最大的角上。

当其中一个浓度参数 $\alpha_i$ 小于1时，概率密度函数将在相应的边缘 $x_k=0$ 处趋于无穷大。对于[图 2.22]，这对于 $\alpha=(0,8,0,2)^T$ 是可见的，但对于 $\alpha=(0,8,0,2)^T$ 则几乎可见。

[列表 2.1]提供了一个计算狄利克雷分布概率密度函数的实现。

我们分别计算 **x** 分分的期望。设

```
$$\alpha_0=\sum_{k=1}^K \alpha_k$$
```

```matlab
function y = dirpdf(x,a)
% Dirichlet概率密度函数.
% y = dirpdf(x,a) 返回浓度参数为行向量 a 的
% 利克雷概率密度函数
% x 的每行必须具有相同数量的列
% 且为一个或更少。y 是一个列向量，具有与
% x 的行数相同的元素。

if n ~= 2
error('需要正好两个参数。');
end

[ra,ca] = size(a);
[rx,cx] = size(x);

if ra ~=1
error('第二个参数需要是一个行向量。');
end

if any(cx<0)
error('第二个参数需要为正。');
end

if ca == cx+1
% 创建 x 的最后一列
x(i,cx+1) = 1 - sum(x,2);
cx = cx+1;
end

if ca~cx
error('列数不匹配');
end

% 寻找总和不为1或
% 元素超出范围的 x 行。
xOut = sum(x,2)>1 | any(x<0)|(x>1),2);
xIn = ~xOut;

% 初始化为零。
% 由于伽马函数增长很快，使用其
% 对数更安全。这种实现避免了下溢或溢出。
y(xIn) = prod(exp(log(x(InIn,:))-1)).exp(gammaln(sum(a(1,:), 2))...
-sum(gammaln(a(1,:)), 2));
y(xOut) = NaN;
```

列表 2.1：MATLAB 中的狄利克雷概率密度函数。Python 请访问 https://github.com/ACFaul/Probability-Likelihood-Python/

![](img/c6c76bf52016db7e78a5e30d4766ef81_68_0.png)

![](img/c6c76bf52016db7e78a5e30d4766ef81_68_1.png)

![](img/c6c76bf52016db7e78a5e30d4766ef81_68_2.png)

图 2.22：不同 $\alpha$ 值的狄利克雷概率密度函数。

注意积分是在单纯形上进行的

```
$$\mathbb{E}[x_j] = \int x_j \text{Dir}(x|\alpha)dx = \frac{\Gamma(\alpha_0)}{\Gamma(\alpha_1)\cdots\Gamma(\alpha_K)} x_j^{\alpha_j} \prod_{k\neq j}^K x_k^{\alpha_k-1}dx$$
$$= \frac{\Gamma(\alpha_0)}{\Gamma(\alpha_1)\cdots\Gamma(\alpha_{j-1})\Gamma(\alpha_{j+1})\cdots\Gamma(\alpha_K)} \Gamma(\alpha_j+1)$$
$$= \int \text{Dir}(x|\alpha_1,\dots,\alpha_{j-1},\alpha_j,\alpha_{j+1},\dots,\alpha_K)dx$$
$$= \frac{\alpha_j}{\alpha_0}$$
```

其中我们使用了伽马函数在 2.14 中给出的性质，以及任何概率密度函数在其范围内的积分均为 1 的事实。方差由给出

```
var[x_j] = \frac{\alpha_j(\alpha_0 - \alpha_j)}{\alpha_0^2(\alpha_0 +1)}
```

而 $j \neq k$ 的协方差为

```
cov[x_j, x_k] = \frac{-\alpha_j\alpha_k}{\alpha_0^2(\alpha_0 +1)}
```

正如我们之前在分类分布中看到的 true，这种影响是负的，因为由于 $\alpha$ 的限制，如果一个分量增加，另一个必须减少。观察图 2.22，我们看到浓度参数 $\alpha_k$ 对其和 $\alpha_0$ 的相对大小决定了大部分概率质量集中在单纯形内的位置。因此，在某些文献中，狄利克雷分布给出为 $\alpha$，

```
$$\alpha = \alpha_0 = \sum_{k=1}^K \alpha_k,$$
$$\mu = \left(\frac{\alpha_1}{\alpha_0}, \dots, \frac{\alpha_K}{\alpha_0}\right)^T\quad (2.16)$$
```

在这种情况下，$\alpha$ 被称为（单个）浓度参数，其中 $\mu$ 是基分布。我们已经看到，如果 $\alpha=1$，狄利克雷分布是均匀的。这意味着所有分布 $\chi$ 都是等概率的。如果 $\alpha$ 趋于无穷大，分布将变得在均匀分布附近出现尖峰。

