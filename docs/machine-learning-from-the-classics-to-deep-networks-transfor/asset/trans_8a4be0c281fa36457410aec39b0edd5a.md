
$$
\min_{\{\theta_i, u_i\}_{i=1}^l} \quad (\mathbf{y} - X\mathbf{\theta})^T(\mathbf{y} - X\mathbf{\theta}) + \lambda\sum_{i=1}^l u_i, \quad \text{s.t.} \quad \left\{ \begin{aligned} & -u_i \leq \theta_i \leq u_i, \\ & u_i \geq 0, \end{aligned} \quad i = 1,2,\ldots,l \right.
$$

![Equation](images/B9780443292385000159/si53.png)

这可以通过任何标准凸优化方法（例如 [14,101]）来求解。开发 LASSO 任务算法之所以成为激烈研究活动的中心，是因为重点在于利用该任务的特定性质来获得*高效*算法，特别是在 *l* 非常大的情况下，这在实践中经常发生。

为了更好地洞察 LASSO 所得解的性质，让我们假设回归变量相互正交且范数为单位，因此 $X^T X = I$。

![Equation](images/B9780443292385000159/si54.png)

输入矩阵的正交性有助于解耦坐标，并产生 *l* 个一维问题，这些问题可以用解析方法求解。对于这种情况，LS 估计变为

$$
\widehat{\mathbf{\theta}}_{\text{LS}} = (X^T X)^{-1} X^T \mathbf{y} = X^T \mathbf{y},
$$

![Equation](images/B9780443292385000159/si55.png)

而岭回归给出

$$
\widehat{\mathbf{\theta}}_R = \frac{1}{1 + \lambda} \widehat{\mathbf{\theta}}_{\text{LS}},
$$

![Equation](images/B9780443292385000159/si56.png) (9.9)

即 LS 估计的每个分量仅仅是按*相同*因子 $\frac{1}{1 + \lambda}$ 进行收缩；

![Equation](images/B9780443292385000159/si57.png)

另见第 [6.5](#Chp006_249-291_B9780443292385000123.xhtml) 节。
