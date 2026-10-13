
## 公式与推导

![Equation](images/B9780443292385000238/si69.png) (17.9)

其中

$$a_{k}(\mathbf{x}_{1:k}) := \frac{\phi_{k}(\mathbf{x}_{1:k})}{\phi_{k - 1}(\mathbf{x}_{1:k - 1})q_{k}(\mathbf{x}_{k}|\mathbf{x}_{1:k - 1})}, \quad k = 2,3,\ldots,n.$$

![Equation](images/B9780443292385000238/si70.png) (17.10)

现在提出的问题是如何选择 $q_{n}(\mathbf{x}_{n}|\mathbf{x}_{1:n - 1}),\ n = 2,3,\ldots$ ![Equation](images/B9780443292385000238/si71.png)。一种合理的策略是选择它以最小化权重 $w_{n}(\mathbf{x}_{1:n})$ ![Equation](images/B9780443292385000238/si72.png) 的方差，给定样本 $\mathbf{x}_{1:n - 1}$ ![Equation](images/B9780443292385000238/si73.png)。结果表明，使方差实际上为零的最优值（问题 [17.4](#Chp017_855-884_B9780443292385000238.xhtml#o0045)）由下式给出：

![Equation](images/B9780443292385000238/fx002.jpg) (17.11)

然而，在实践中，通常 $p_{n}(\mathbf{x}_{n}|\mathbf{x}_{1:n - 1})$ ![Equation](images/B9780443292385000238/si74.png) 不易采样，只能满足于采用其某些近似。我们现在准备陈述我们的第一个序贯重要性采样（SIS）算法。

## 算法 17.2：序贯重要性采样

*   选择 $q_{1}(\cdot)$ ![Equation](images/B9780443292385000238/si75.png)，$q_{n}(\cdot|\cdot)$ ![Equation](images/B9780443292385000238/si76.png)，$n = 2,3,\ldots$ ![Equation](images/B9780443292385000238/si77.png)。
*   选择粒子数，$N$。
*   **For** $i = 1,2,\ldots,N$ ![Equation](images/B9780443292385000238/si45.png)，**Do**；初始化 $N$ 个不同的实现/流。
    1.  采样 $\mathbf{x}_{1}^{(i)} \sim q_{1}(\mathbf{x})$ ![Equation](images/B9780443292385000238/si67.png)。

