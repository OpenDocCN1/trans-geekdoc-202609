
我们看到，映射 $\phi$ 永远不需要求值，只需要最大化目标函数的核 $k$ 即可：

```
$L(\alpha) = \sum_{n=1}^{N} \alpha_n - \frac{1}{2}\sum_{i=1}^{N}\sum_{j=1}^{N} \alpha_i \alpha_j c_{ij} \, (1 + k(\mathbf{v}_i, \mathbf{v}_j))$$
```

受限于 $\alpha_i \ge 0, i = 1, \dots, N$。分类根据以下内容的符号进行：

```
$-b + \sum_{n=1}^{N} \alpha_n c_n \phi(\mathbf{v}_n)^T \mathbf{v} = -b + \sum_{n=1}^{N} \alpha_n c_n k(\mathbf{v}_n, \mathbf{v})$
```

核技巧可以应用于所有的线性分类方法，以分离非线性可的数据。所有方法都减少了核函数 $k$ 的计算。

核函数推导自高维内积。在上一章中，我们将内积视为样本之间关系的度量。例如，一个新样本的分类取决于它与一组支持向量的加权内积的相关性是否比另一组更高。核函数提供了一个描述两个样本之间关系的数值。

这类描述样本的函数并不一定非要推导自高维内积。此类函数适用于我们目的的充分必要条件是：对于任意 $N$ 和任意样本 $\{\mathbf{x}_1, \dots, \mathbf{x}_N\}$，$(m,n)$ 元素等于 $k(\mathbf{x}_m, \mathbf{x}_n)$ 的 $N \times N$ 矩阵 **K** 是*正定的*。这意味着对于所有 $\mathbf{v}$，$\mathbf{v}^T K \mathbf{v} \ge 0$。该矩阵被称为 *Gram 矩阵*或 *Gramian矩阵*。对于正数 $c$，常数函数 $k(\mathbf{x}, \mathbf{y}) = c$ 是有效核，那么对于任何 $\mathbf{v} = (\mathbf{v}_1, \dots, \mathbf{v}_N)$：

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

**如果 A** 是一个对称的、正半定的 $M \times M$ 矩阵，那么由定义的函数

$k(\mathbf{x}, \mathbf{y}) = \mathbf{x}^T \mathbf{y}$

是一个有效核函数，在这种情况下：

```
$$\mathbf{v}^T \mathbf{K} \mathbf{v} = \sum_{m,n}^N v_m \mathbf{x}_m^T \mathbf{A} \mathbf{x}_n = \left(\ \sum_{m=1}^N v_m \mathbf{x}_m \right)^T \mathbf{A} \left( \sum_{n=1}^N v_n \mathbf{x}_n \right)$$
```

同样地，如果 $f: \mathbb{R}^M \to \mathbb{R}$ 是任意函数，且 $k: \mathbb{R}^M \times \mathbb{R}^M \to \mathbb{R}$ 是有效核，那么：

```
$$\sum_{m,n}^N k(\mathbf{x}_m, \mathbf{x}_n) v_m v_n = \mathbf{w}^T \mathbf{w} \geq 0, \eqno (5.1)$$
```

 $w=(f(\mathbf{x}_1), \dots, f(\mathbf{x}_N)^T$。因此，由 $f(\mathbf{x})f(\mathbf{y})$ 定义的函数是有效核。

乘以一个正常数和两个有效核仍然是核。设 $\{\mathbf{x}_1, \dots, \mathbf{x}_N\}$ 是任意集合。设 $\mathbf{K}$ 表示核的 Gram 矩阵。由于 Gram 矩阵是对称且正半定的，它们的 $(m,n)$ 元素由

```
$$\sum_{i=1}^N A_{mi} \quad \text{and} \quad \sum_{j=1}^N B_{mj}$$
```

分别给出。对于任意向量 $\mathbf{v} = (v_1, \dots, v_N)^T$：

```
$$\mathbf{v}^T K \mathbf{v} = \sum_{m,n}^N v_m K_{mn} v_n = \sum_{m=1}^N v_m \dots \text{ (此处省略推导过程)}$$
```

这里 $\mathbf{K}$ 是正半定的，且核的乘积是核。从这里我们可以推导出，如果 $p$ 是一个具有非负系数的多项式，当 $k(\mathbf{x}, \mathbf{y})$ 是有效核时，则 $p(k(\mathbf{x}, \mathbf{y}))$ 是有效核。由于正半定性对于所有点 $x_1, \dots, x_N$ 成立，因此 $k(\mathbf{x}, \mathbf{y})$ 是有效核。$\exp(k(\mathbf{x}, \mathbf{y}))$ 也是有效核，因为它是一个正系数的多项式。

由于正半定性对于所有点 $x_1, \dots, x_N$ 成立，因此 $k(\mathbf{x}, \mathbf{y})$ 是有效核。$\exp(k(\mathbf{x}, \mathbf{y}))$ 的示例包括：

- **线性**：$k(\mathbf{x}, \mathbf{y}) = \mathbf{x}^T \mathbf{y}$
- **二次**：$k(\mathbf{x}, \mathbf{y}) = (\mathbf{x}^T \mathbf{y})^2$ 
- **多项式**：$k(\mathbf{x}, \mathbf{y}) = (\mathbf{x}^T \mathbf{y} + c)^d$
- **Sigmoid**：$k(\mathbf{x}, \mathbf{y}) = \tanh(\frac{\mathbf{x}^T\mathbf{y} + c}{a})$
- **高斯 (RBF)**：$k(\mathbf{x}, \mathbf{y}) = \exp \left(-\frac{|\mathbf{x} - \mathbf{y}\|^2}{2\theta^2}\right)$

