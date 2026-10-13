
$$
\mathcal{W}_{\theta} = \begin{bmatrix} \frac{1}{|\theta_{1}|} & 0 & \cdots & 0 \\ 0 & \frac{1}{|\theta_{2}|} & \cdots & 0 \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \cdots & \frac{1}{|\theta_{l}|} \\ \end{bmatrix},
$$

![Equation](images/B9780443292385000160/si197.png)

其中当 $\theta[i] = 0$ 时，对于某些 $i \in \{1, 2, \dots, l\}$，$\mathcal{W}[\theta]$ 相应的系数被定义为 1。如果 $\mathcal{W}[\theta]$ 是一个常数加权矩阵，即对于某个固定的 $\widetilde{\mathbf{\theta}}$ 有 $\mathcal{W}[\theta] := \mathcal{W}[\tilde{\theta}]$，那么求得最小值

$$
\widehat{\mathbf{\theta}} = {\arg\min}_{\mathbf{\theta} \in \mathbb{R}^{l}}\ \left\| \mathbf{y} - X\mathbf{\theta} \right\|_{2}^{2} + \lambda\mathbf{\theta}^{T}\mathcal{W}_{\widetilde{\theta}}\mathbf{\theta},
$$

![Equation](images/B9780443292385000160/si202.png)

将是直接且类似于岭回归的。在迭代重加权方案中，$\mathcal{W}[\tilde{\theta}]$ 被 $\mathcal{W}[\theta^{(i)}]$ 所取代，后者是利用从前一次迭代获得的参数相应估计值形成的，即 $\widetilde{\mathbf{\theta}} := \mathbf{\theta}^{(i)}$，这与我们之前所做的一样。在后续过程中，每次迭代求解一个加权岭回归任务。
