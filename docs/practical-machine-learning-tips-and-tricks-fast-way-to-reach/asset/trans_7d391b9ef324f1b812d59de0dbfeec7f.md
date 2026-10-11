

# 算法与优化方法

## 牛顿法求解严格凸函数

**算法 6：用于最小化严格凸函数的牛顿技术**

```text
while (!convergency) do
    Evaluate gk = ∇f(xk)
    Evaluate Hk = ∇²f(xk)
    dk = -Hk⁻¹gk
    Use line search to observe step size ηk along dk
    xk+1 = xk + ηkdk
end
```

## DFP 算法

在 DFP 算法中，$P_k$ 和 $Q_k$ 定义为：

$$P_k = \frac{\delta_k \delta_k^T}{\delta_k^T y_k} \tag{A.10}$$

$$Q_k = -\frac{B_k y_k y_k^T B_k}{y_k^T B_k y_k} \tag{A.11}$$

## 拟牛顿法

### BFGS 算法

由公式 A.5 可导出半牛顿条件如下：
使用 $B_k$ 作为 $H_k$ 的估计，此时半牛顿条件变为：

$$f'(x) - g_k = H_k(x - x_k)$$
$$g_{k-1} - g_k = H_k(x_{k-1} - x_k)$$
$$g_k - g_{k-1} = H_k(x_k - x_{k-1})$$

$$B_{k+1}\delta_k = y_k \tag{A.12}$$

更新准则类似 DFP，但 $P_k$ 和 $Q_k$ 不同。令：

$$g_{k+1} - g_k = H_{k+1}(x_{k+1} - x_k) \quad \text{(半牛顿条件)} \tag{A.7}$$

$$P_k\delta_k = y_k, \quad Q_k\delta_k = -B_k\delta_k$$

则：

$$P_k = \frac{y_k y_k^T}{y_k^T \delta_k} \tag{A.13}$$

$$Q_k = -\frac{B_k \delta_k \delta_k^T B_k}{\delta_k^T B_k \delta_k} \tag{A.14}$$

### Broyden 算法

Broyden 算法是 DFP 和 BFGS 的线性组合。

## 术语表

**特征向量**
> 用于表征单个数据的特征向量。

**损失函数**
> 一种将事件映射为实数的函数，该实数直观地表示与该事件相关的某些“代价”。

**术语表条目**
> 此处编写术语表条目的描述。
> 此处编写术语表条目的描述。
> 此处编写术语表条目的描述。

