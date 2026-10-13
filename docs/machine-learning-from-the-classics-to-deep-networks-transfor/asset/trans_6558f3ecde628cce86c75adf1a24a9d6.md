

$$
\mathcal{L}\left( y,f(\mathbf{x}) \right) = \begin{cases} 
\epsilon|y - f(\mathbf{x})| - \frac{\epsilon^{2}}{2}, & \quad\text{if}\quad|y - f(\mathbf{x})| > \epsilon, \\ 
\frac{1}{2}|y - f(\mathbf{x})|^{2}, & \quad\text{if}\quad|y - f(\mathbf{x})| \leqslant \epsilon, 
\end{cases}
$$

![Equation](images/B9780443292385000172/si226.png)

对于某个参数 $\epsilon$。这被称为 Huber 损失函数，如 [图 11.10](#Chp011_519-582_B9780443292385000172.xhtml#f0055) 所示。一种可以近似 Huber 损失函数的损失函数，正如我们将看到的，它具有一些良好的计算特性，即所谓的*线性 $\epsilon$* 不敏感损失函数，定义如下（另见第 [8](#Chp008_343-416_B9780443292385000147.xhtml) 章）

$$
\mathcal{L}\left( y,f(\mathbf{x}) \right) = \begin{cases} 
|y - f(\mathbf{x})| - \epsilon, & \quad\text{if}\quad|y - f(\mathbf{x})| > \epsilon, \\ 
0, & \quad\text{if}\quad|y - f(\mathbf{x})| \leqslant \epsilon, 
\end{cases}
$$

![Equation](images/B9780443292385000172/si227.png) (11.28)

如 [图 11.10](#Chp011_519-582_B9780443292385000172.xhtml#f0055) 所示。注意当 $\epsilon = 0$ 时，它与绝对值损失函数一致，并且对于 $\epsilon < 1$ 的小值，它接近 Huber 损失。另一个版本是*二次 $\epsilon$* 不敏感损失函数，定义如下

