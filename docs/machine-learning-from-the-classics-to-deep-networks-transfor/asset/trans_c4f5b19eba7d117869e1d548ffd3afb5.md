

$$
\Sigma_{N + 1} = \begin{bmatrix} {\kappa(\mathbf{x},\mathbf{x}) + \sigma_{\eta}^{2},} & {\mathbf{\kappa}^{T}(\mathbf{x})} \\ {\mathbf{\kappa}(\mathbf{x}),} & \Sigma_{N} \end{bmatrix},\quad\mathbf{\kappa}(\mathbf{x}): = {\lbrack\kappa(\mathbf{x},\mathbf{x}_{1}),\ldots,\kappa(\mathbf{x},\mathbf{x}_{N})\rbrack}^{T},
$$

![Equation](images/B9780443292385000196/si668.png)

即，

![Equation](images/B9780443292385000196/fx022.jpg) (13.141)

将公式 [(13.141)](#Chp013_635-716_B9780443292385000196.xhtml#deq235) 与公式 [(11.27)](#Chp011_519-582_B9780443292385000172.xhtml) 进行比较。考虑到 $\Sigma[N] = \mathcal{K}[N] + \sigma[\eta]^2 I$ ![Equation](images/B9780443292385000196/si669.png)，对于适当选择的 $C$ 和 $\sigma[\eta]^2$ ![Equation](images/B9780443292385000196/si146.png)，$\mu[y](\mathbf{x})$ ![Equation](images/B9780443292385000196/si670.png) 与核岭回归得到的 $\hat{y}$ ![Equation](images/B9780443292385000196/si671.png) 相同。然而，现在我们也获得了关于结果估计量相应方差的信息。

此时，回顾第 [12.2.3](#Chp012_583-634_B9780443292385000184.xhtml) 节中参数建模的贝叶斯回归任务很有意思，并要记得对于零均值先验 $p(\mathbf{\theta})$ ![Equation](images/B9780443292385000196/si357.png)，公式 [(12.20)](#Chp012_583-634_B9780443292385000184.xhtml) 中得到的均值与岭回归提供的均值相同，前提是 $\lambda$ 选择得当。

### 备注 13.7

*   从前面的讨论中显而易见，利用高斯过程求解回归任务，是在再生核希尔伯特空间（RKHS）中求解回归任务的贝叶斯答案。这两种方法有一个共同的优势。尽管由所采用的核所隐含的到 RKHS 的底层映射可能存在于高维空间中，但求解任务的复杂度取决于训练点的数量 $N$。与高斯过程相关的复杂度来源是矩阵求逆，其运算量为 $\mathcal{O}(N^3)$ ![Equation](images/B9780443292385000196/si672.png)。

*   [(13.141)](#Chp013_635-716_B9780443292385000196.xhtml#deq235) 中的两个方程均可从第 [12.2.3](#Chp012_583-634_B9780443292385000184.xhtml) 节中涵盖的贝叶斯学习线性情况下推导出的相应方程获得。确实，在公式 [(12.27)](#Chp012_583-634_B9780443292385000184.xhtml) 中设定 $\mathbf{\theta}[0] = 0$ ![Equation](images/B9780443292385000196/si673.png) 并将其与公式 [(12.22)](#Chp012_583-634_B9780443292385000184.xhtml) 结合，我们得到

