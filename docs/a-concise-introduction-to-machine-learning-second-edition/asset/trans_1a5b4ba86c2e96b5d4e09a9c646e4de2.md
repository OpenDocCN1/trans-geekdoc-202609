
为了对 **D** 求导，我们利用迹的循环投影性质重写联合对数似然期望的表达式：

```
$$\mathcal{L} = -\frac{1}{2} \sum_{n=1}^{N} [(K + D) \log(|\mathbf{D}|) + \text{tr}(\mathbb{E}[\mathbf{u}_n\mathbf{u}_n^T]) + \left[(\mathbf{v}_n - \mu)^T 2(\mathbf{v}_n - \mu)\mathbb{E}[\mathbf{u}_n]^T W^T \mathbb{E}[\mathbf{u}_n\mathbf{u}_n^T]W D^{-1}\right)]$$
```

通过这种方法推导出 A.2.4、A.2.7 和 A.2.10 中的公式。因此对 **D** 的导数为：

```
$$\frac{\partial}{\partial D}\mathcal{L} = -\frac{1}{2} \sum_{n=1}^{N} \frac{1}{|\mathbf{D}|} \mathbf{D}^{-1} \text{diag}( (\mathbf{v}_n - \mu)^T (\mathbf{v}_n - \mu)) - 2(\mathbf{v}_n - \mu)\mathbb{E}[\mathbf{u}_n]^T W^T \mathbb{E}[\mathbf{u}_n\mathbf{u}_n^T]W^T D^{-1}$$
```

将此式置于零，从左右两边乘以 **D** 并解出 **D**，得到以下公式：

```
$$\mathbf{D}_{new} = \text{diag} \left( \frac{1}{N} \sum_{n=1}^{N} (\mathbf{v}_n - \mu)(\mathbf{v}_n - \mu)^T - \frac{1}{N} \sum_{n=1}^{N} (\mathbf{v}_n - \mu)\mathbb{E}[\mathbf{u}_n]^T W^T + \frac{1}{N} W \sum_{n=1}^{N} \mathbb{E}[\mathbf{u}_n\mathbf{u}_n^T] W^T \right)$$
```

在插入 **$D_{new}$** 时，通常会使用已经更新的 **$W_{new}$**。当将 (7.13) 插入行左侧时，对于 $n=1, \dots, N$ 的和 $\mathbb{E}[\mathbf{u}_n\mathbf{u}_n^T]$ 与其逆逆抵消，最后一行与上方合并。更新公式为：

```
$$\mathbf{D}_{new} = \frac{1}{N} \sum_{n=1}^{N} \text{diag} ((\mathbf{v}_n - \mu)(\mathbf{v}_n - \mu - \mathbf{W}_{new}\mathbb{E}[\mathbf{u}_n])^T)$$
```

这可以看作 (7.12) 的 $D$ 维版本。这取决于 M 步。

这些更新通过 E 步中计算的期望间接地依赖于之前的 **D** 和 **W**。为此，隐变量 **$\mathbf{u}$** 的条件概率分布 $\pi(\mathbf{u}|\mathbf{v})$ 的方差为：

```
$$\mu_{\mathbf{u}|\mathbf{v}} = (\mathbf{W}^T \mathbf{D}^{-1} \mathbf{W} + \mathbf{I})^{-1}$$
```

均值为：

```
$$\mu_{\mathbf{u}|\mathbf{v}} = \sum_{\mathbf{u}} \mathbf{u}^T \mathbf{D}^{-1} \mathbf{W} + \mathbf{I},$$
```

它依赖于 **v**。因此，构成 E 步的两个计算为：

```
$$E[u_n] = \sum_{u_iv}W^T D^{-1}(v_n - \mu)$$
```

并使用 (2.10)：

```
$$E[u_nu_n^T] = \sum_{u_iv} + E[u_n]E[u_n]^T$$
```

# 7.5 核主成分分析

之前的章节假设数据样本通过 (7.2) 中定义的**线性**映射与低维空间中的隐变量相关。从几何角度上看，这意味着数据集接近于一个平面、直线或超平面，如图 7.5 和 7.6 所示。然而，在许多实际应用中，这一假设是不切实际的。

数据样本靠近一个*K 维流形*。球面是一个二维流形。地平论论者们屈从于一种印象，即局部上地球是一个代表平面的球体。然而，从全局来看，它并非如此，因为沿着一个方向连续旅行将回到起点。图 7.7a 给出了一个靠近单位球面的数据示例。颜色较浅的点位于球面表面之外。

可以选择一个映射 $\phi: \mathbb{R}^D \to \mathbb{R}^D$ 到一个高维空间，使得数据集随后与*K 维子空间*中的隐变量相关联。在图 7.7 中，数据集首先被映射到四维空间，其中第四分量是其他三个分量的平方和。由于数据集近似位于球面上，对于所有数据样本，第四分量将接近于 1。因此数据集位于一个超平面上。在找到前两个主成分后，将数据集投影到由这两个主成分形成的平面上。如图 7.7b 所示。因此数据集在顶部或底部分组，可以沿着一个主成分进行分离。

然而，与 5.2 节中的核技巧（kernel trick）一样，避免了显式执行映射。相反，所有计算步骤使用*核函数*或*核* $k: \mathbb{R}^D \times \mathbb{R}^D \to \mathbb{R}$，其定义为：

```
$$k(x,y) = \phi(x)^T\phi(y).$$
```

设 **E** 为 $N \times N$ 矩阵，每个元素为向量 $\mathbf{a} = (a_1, \dots, a_N)$，使得样本的均值为零：

```
$$\mathbf{a}^T(\mathbf{I} - \frac{1}{N}\mathbf{E}) = (a_1^T - \frac{1}{N}\sum_{n=1}^N a_n, \dots, a_N^T - \frac{1}{N}\sum_{n=1}^N a_n).$$
```

其中 $\phi(v_1),\dots, \phi(v_N) \in \mathbb{R}^D$ 是映射 $\phi$ 下的图像。设 $\Phi$ 为 $D \times N$ 矩阵，其列为 $\phi(v_1),\dots, \phi(v_N)$，称为*预图像*（pre-images）。

回顾主成分分析计算数据样本的协方差矩阵 $\Sigma$。在此范围内，对于 $\Phi$ 的每一行，我们减去均值。该矩阵的列是平移后的图像，即 $\Phi(I - \frac{1}{N}\mathbf{E})$ 的第 $n$ 列的转置。这可以写为：

```
$$\Sigma = \frac{1}{N} \sum_{n=1}^N \Phi(I - \frac{1}{N}\mathbf{E})e_n e_n^T (I - \Phi^T$$
```

其中 $e_n$ 是单位向量，除了第 $n$ 列外所有元素均为 0。从右侧乘以 $e_n$ 选出了 $\Phi(I - \frac{1}{N}\mathbf{E})$ 的第 $n$ 列。对所有 $n=1, \dots$ 求和 $e_n e_n^T$ 得到单位矩阵。此外，矩阵 $I - \frac{1}{N}\mathbf{E}$ 是*幂等的*，这意味着它的任何幂都是其本身，因为 $\mathbf{E}^2 = \mathbf{E}$：

```
$(I - \frac{1}{N}\mathbf{E})(I - \frac{1}{N}\mathbf{E}) = I - \frac{2}{N}\mathbf{E} + \frac{1}{N^2}\mathbf{E}^2 = I - \frac{1}{N}\mathbf{E}.$$
```

因此，协方差矩阵可以表示为：

```
$$\Sigma = \frac{1}{N} \Phi(I - \frac{1}{N}\mathbf{E})\Phi^T.$$
```

寻找 $\Sigma$ 最大的 $K$ 个特征值 $\lambda_k$ 以及对应的特征向量 $\mathbf{w}_k, k=1, \dots, K$。利用上述 $\Sigma$ 的表达式，这些向量满足：

```
$$\Phi(I - \frac{1}{N}\mathbf{E})\Phi^T\mathbf{w}_k = N\lambda_k\mathbf{w}_k$$
```

从左侧乘以 $(I - \frac{1}{N}\mathbf{E})\Phi^T$ 并利用 $I - \frac{1}{N}\mathbf{E}$ 的幂等性，变为：

```
$(I - \frac{1}{N}\mathbf{E})\Phi^T\Phi(I - \frac{1}{N}\mathbf{E})\mathbf{w}_k = N\lambda_k(I - \frac{1}{N}\mathbf{E})\mathbf{w}_k.$$
```

在此，向量

```
$$\mathbf{w}_k = (I - \frac{1}{N}\mathbf{E})\mathbf{w}_k \quad (7.14)$$
```

是 $(I - \frac{1}{N}\mathbf{E})$ 对称矩阵 $\mathbf{\Phi}^T\mathbf{\Phi}(I - \frac{1}{N}\mathbf{E})$ 的特征向量，特征值为 $\lambda_k = N\lambda_k$。注意，由于 $I - \frac{1}{N}\mathbf{E}$ 是幂等的，我们有 $(I - \frac{1}{N}\mathbf{E})\mathbf{w}_k = \mathbf{w}_k$。因此，和的组件简化为 $\mathbf{w}_k$ 的 $(i, j)$ 项，即内积：

```
$$\phi(v_i)^T\phi(v_j) = k(v_i, v_j).$$
```

**K = $\mathbf{\Phi}^T\mathbf{\Phi}$ 是*核矩阵*。*核主成分分析*通过 (7.14) 计算 $(I - \frac{1}{N}\mathbf{E})\Phi^T\mathbf{\Phi}(I - \frac{1}{N}\mathbf{E})$ 的特征值 $N\lambda_k$ 和特征向量 $\mathbf{w}_k$。将 (7.14) 从左侧乘以 $1/N$，得到：

```
$$\mathbf{w}_k = \frac{1}{N}\Phi(I - \frac{1}{N}\mathbf{E})\Phi^T\mathbf{w}_k = \lambda_k\mathbf{w}_k.$$
```

因此，$\mathbf{w}_k$ 是图像 $\phi(v_1),\dots, \phi(v_N)$ 的线性组合：

```
$$\mathbf{w}_k = \frac{1}{N}\sum_{n=1}^N \mathbf{w}_n\phi(v_n),$
```

$\mathbf{w}_n, n=1, \dots, N$ 是 $\mathbf{w}_k$ 的系数。在实践中，从不这种计算，因为我们只感兴趣用由主成分形成的基表示任何数据点 $v$，即投影的值：

```
$$\mathbf{w}_k^T\phi(v) = \frac{1}{N\lambda_k}\mathbf{\Phi}^T\phi(v) = \frac{1}{N\lambda_k}\phi(v_1)^T\phi(v) \dots \ \phi(v_N)^T\phi(v)$$
```

```
$$\mathbf{w}_k = \frac{1}{N\lambda_k}k(v_1, v_k) \dots \ k(v_N, v_k)$$
```

还需要指定 $\mathbf{w}_k$ 的长度。主成分的长度为 1，这转化为对 $\mathbf{w}_k$ 长度的条件：

```
$$\1 = \mathbf{w}_k^T\mathbf{w}_k = \frac{1}{(N\lambda_k)^2}\mathbf{w}_k^T\mathbf{\Phi}^T\mathbf{\Phi}\mathbf{w}_k,$$
```
