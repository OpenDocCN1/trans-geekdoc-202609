

## Box–Muller 方法

$J(x,y;r,\phi) = \left\lbrack \begin{array}{ll} {\frac{\partial g_{x}}{\partial r}\ } & \frac{\partial g_{x}}{\partial\phi} \\ {\frac{\partial g_{y}}{\partial r}\ } & \frac{\partial g_{y}}{\partial\phi} \\ \end{array} \right\rbrack$

为简化起见，我们假设每个 $(r,\phi)$ 值对应一个 $(x,y)$ 值。现在让我们看看如何通过分别从均匀分布和指数分布中为 $\phi$ 和 $r$ 抽取样本，来生成高斯分布 $p(x) = \mathcal{N}(x|0, 1)$ 的样本；回顾 [示例 14.1](#Chp014_717-754_B9780443292385000202.xhtml#enun0015)，我们描述了一种从指数分布生成样本的技术。

令 $r$ 服从指数分布，

$$p_{r}(r) = \frac{1}{2}\exp\left( - \frac{r}{2} \right),\quad r \geqslant 0,$$

令 $\phi$ 服从均匀分布 $\mathcal{U}(0, 1)$，

$$p_{\phi}(\phi) = \left\{ \begin{matrix} {\frac{1}{2\pi},\ } & {\quad 0 \leqslant \phi \leqslant 2\pi,} \\ {0,\ } & {\quad\text{否则},} \\ \end{matrix} \right.$$

并假设它们相互独立，即

$$p_{r,\phi}(r,\phi) = p_{r}(r)p_{\phi}(\phi).$$

按如下方式生成两个新的随机变量：

$$x = \sqrt{r}\cos\phi,$$

$$y = \sqrt{r}\sin\phi.$$

