
$$\frac{1}{2}\sigma^{-2}\mathbf{u}^T(\mathbf{W}^T\mathbf{W} + \sigma^2\mathbf{I})\mathbf{u}$$

因此 $p(\mathbf{u})$ 的协方差矩阵为：

$$\Sigma_{\mathbf{u},\mathbf{v}} = \sigma^2(\mathbf{W}^T\mathbf{W} + \sigma^2\mathbf{I}), \quad (7.6)$$

它与 $\mathbf{v}$ 无关。$\mathbf{u}$ 的线性项为：

$$\frac{1}{2}\mathbf{u}^T\Sigma_{\mathbf{u},\mathbf{v}}^{-1} = \mathbf{u}^T\sigma^{-2}\mathbf{W}^T(\mathbf{v}-\mu).$$

这需要等于零。因此，条件分布的均值为：

$$\mu_{\mathbf{u},\mathbf{v}} = \Sigma_{\mathbf{u},\mathbf{v}}^{-1}(\mathbf{v}-\mu) = (\sigma^2\mathbf{W}^T\mathbf{W} + \sigma^2\mathbf{I})^{-1}\mathbf{W}^T(\mathbf{v}-\mu), \quad (7.7),$$

它依赖于 $\mathbf{v}$。期望极大化（EM）算法计算数据似然对数关于隐变量 $\mathbf{u}_1, \dots, \mathbf{u}_N$ 条件概率的期望。数据似然的对数似然对数为：

$$\mathcal{L} = \log \prod_{n=1}^N p(\mathbf{v}_n, \mathbf{u}_n) = \frac{1}{2}\sum_{n=1}^N ((K+D)\log(2\pi) + D\log(\sigma^2) + \mathbf{u}_n^T\mathbf{u}_n - \sigma^{-2}\mathbf{u}_n^T\mathbf{W}^T(\mathbf{v}_n-\mu) - 2\mathbf{u}_n^T\mathbf{W}^T\mathbf{W}\mathbf{u}_n).$$

当对隐变量取期望时，我们有：

$$E[\mathbf{u}_n] = \mu_{\mathbf{u},\mathbf{v}}, \quad (7.8)$$

为了找到 $\mathbf{u}_n$ 与自身内积的期望，我们利用迹（trace）的循环移位性质以及计算迹和期望的操作可以交换的事：

$$E[\mathbf{u}_n^T\mathbf{u}_n] = E[\text{tr}(\mathbf{u}_n\mathbf{u}_n^T)] = \text{tr}(E[\mathbf{u}_n\mathbf{u}_n^T]).$$

类似地，

$$E[\mathbf{u}_n^T\mathbf{W}^T\mathbf{W}\mathbf{u}_n] = E[\text{tr}(\mathbf{u}_n^T\mathbf{W}^T\mathbf{W}\mathbf{u}_n)] = \text{tr}(\mathbf{W}^T\mathbf{W}E[\mathbf{u}_n\mathbf{u}_n^T]).$$

然后可以使用 (2.10) 计算：

$$\mathbb{E}[\mathbf{u}_n \mathbf{u}_n^T] = \mathbf{\Sigma}_{\mathbf{u}_n} + \mathbb{E}[\mathbf{u}_n]\mathbb{E}[\mathbf{u}_n]^T = \mathbf{\Sigma}_{\mathbf{u}_n} + \mu_{\mathbf{u}_n}\mu_{\mathbf{u}_n}^T. \quad (7.9)$$

因此，联合数据似然对数的期望为：

$$\mathcal{L} = \frac{1}{2} \sum_{n=1}^N [(K+D) \log(2\pi) + D \log(\sigma^2) + \text{tr}(\mathbb{E}[\mathbf{u}_n \mathbf{u}_n^T]\mathbf{W}^T\mathbf{W}) - \sigma^{-2}\|\mathbf{v}_n - \mu\|^2 + 2\mathbb{E}[\mathbf{u}_n]^T\mathbf{W}^T(\text{此处})]$$

现在，利用迹的循环性质、A.6 和 A.9 中的公式以及 $\mathbb{E}[\mathbf{u}_n \mathbf{u}_n^T]$ 的对称性，对 $\mathbf{W}$ 求导得到：

$$\frac{\partial\mathcal{L}}{\partial\mathbf{W}} = \frac{1}{2} \sum_{n=1}^N [-2\sigma^{-2}(\mathbf{v}_n - \mu)\mathbb{E}[\mathbf{u}_n]^T + 2\mathbb{E}[\mathbf{u}_n \mathbf{u}_n^T]]$$

将此置为零得到 $\mathbf{W}$ 的更新：

$$\mathbf{W}_{new} = \left(\sum_{n=1}^N (\mathbf{v}_n - \mu)\mathbb{E}[\mathbf{u}_n]^T\right) \left(\sum_{n=1}^N \mathbb{E}[\mathbf{u}_n \mathbf{u}_n^T]\right)^{-1} \quad (7.10)$$

注意这个更新公式通过 (7.6) 和 (7.7) 中的条件均值和协方差矩阵依赖于 $\mathbf{W}$。另一方面，对 $\sigma^2$ 求导得到：

$$\frac{\partial\mathcal{L}}{\partial\sigma^2} = -\frac{1}{2} \sum_{n=1}^N \frac{1}{\sigma^2} (\|\mathbf{v}_n - \mu\|^2 - 2\sigma^{-2}\mathbb{E}[\mathbf{u}_n]^T\mathbf{W}^T(\mathbf{v}_n - \mu) + 2\text{tr}(\mathbf{W}^T\mathbf{W}\mathbb{E}[\mathbf{u}_n \mathbf{u}_n^T]))$$

$\sigma^2$ 的更新公式如下：

$$\sigma_{new}^2 = \frac{1}{ND}\sum_{n=1}^N [\|\mathbf{v}_n - \mu\|^2 - 2\sigma^{-2}\mathbb{E}[\mathbf{u}_n]^T\mathbf{W}^T(\mathbf{v}_n - \mu) + 2\text{tr}(\mathbf{W}^T\mathbf{W}\mathbb{E}[\mathbf{u}_n \mathbf{u}_n^T])] \quad (7.11)$$

在更新 $\sigma^2$ 时，通常使用已经更新的值 $\mathbf{W}_{new}$。使用 (7.9)，更新可以写为：

$$\sigma_{new}^2 = \frac{1}{ND}\sum_{n=1}^N [\|\mathbf{v}_n - \mu\|^2 - 2\sigma^{-2}\mathbb{E}[\mathbf{u}_n]^T\mathbf{W}_{new}^T(\mathbf{v}_n - \mu) + 2\text{tr}(\mathbf{W}_{new}^T\mathbf{W}_{new}\mathbf{\Sigma}_{\mathbf{u}_n} \dots)] \dots$$

这可以被解释为衡量 $\mathbb{E}[\mathbf{u}_n]$ 在 $\mathbf{W}_{new}$ 映射下有多接近样本 $\mathbf{v}_n - \mu$，以及 $\mathbf{W}_{new}^T$ 多接近条件协方差矩阵的逆（即精度矩阵）。

另一种解释是：由于迹的和等于迹的和，我们可以在迹内部使用。使用 (7.10) 的 $\mathbf{W}_{new}$，和会与其逆抵消。进一步，利用迹的循环移位性质和方矩阵的迹为标量的事实，公式简化为：

$$\sigma_{new}^2 = \frac{1}{N}\sum_{n=1}^{N} \|\mathbf{v}_n - \mathbf{W}_{new}\mathbb{E}[\mathbf{u}_n]\|^2 \quad (7.12) $$

## 7.4 因子分析

因此，噪声差是 $\mathbf{v}_n - \mu$ 与差值 $\mathbf{v}_n - \mathbf{W}_{new}\mathbb{E}[\mathbf{u}_n]$ 的平均内积，并经过维度 $D$ 的缩放。它衡量了平均 $\mathbf{W}_{new}\mathbb{E}[\mathbf{u}_n]$ 多接近 $\mathbf{u}_n$ 在 $\mathbf{W}_{new}$ 列列跨空间上的正交投影。

这些关于 $\mathbf{W}_{new}$ 和 $\sigma_{new}^2$ 的公式构成了期望极大化算法的 M 步。它们的长度为 $N$，其中 M 步中的每个元素可以在 $O(KD)$ 次操作内计算。M 步的整体复杂度为 $O(KND)$。

E 步使用 (7.7) 和 (7.8) 计算 $E[\mathbf{u}_n]$，使用 (7.6) 和 (7.9) 计算 $E[\mathbf{u}_n \mathbf{u}_n^T]$。E 步计算矩阵的逆，但该矩阵的大小为 $K \times K$，因此是 $O(K^2)$。计算矩阵本身需要 $O(KD)$。如果找到了逆，计算 $E[\mathbf{u}_n]$ 需要 $O(KD)$，计算 $E[\mathbf{u}_n \mathbf{u}_n^T]$ 需要 $O(KD)$，其中 $K \leq D$。这些需要为 $n=1, \dots, N$ 计算，因此 E 步的复杂度为 $O(KND)$。然而，E 步可以对每个数据点并行进行，因为 $E[\mathbf{u}_n]$ 和 $E[\mathbf{u}_n \mathbf{u}_n^T]$ 是独立计算的。

虽然期望极大化算法是一个迭代过程，但如果 $K \ll D$，迭代次数会显著减少。与直接极大化对数似然（复杂度为 $O(ND^2)$）相比，这会影响时间。

到目前为止在本节中，$K$ 是选定的而不是由数据确定的。Minka (2000) 采用了主成分分析的贝叶斯处理来确定 $K$。

到目前为止噪声被建模为所有方向都是平等的。更合适的模型是让噪声方差为对角矩阵 $\mathbf{D}$，以便每个方向可以单独处理。$\mathbf{D}$ 的对角元素被称为*唯一性*（uniqueness），而 $\mathbf{W}$ 的列被称为*因子负载*（factor loadings）。

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

## 7.5 核主成分分析

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
