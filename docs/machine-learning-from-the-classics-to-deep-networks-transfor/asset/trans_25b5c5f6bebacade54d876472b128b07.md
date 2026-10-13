

$C(G): = \mathbb{E}_{p_{r}(\mathbf{x})}\ \left\lbrack \ln\frac{p_{r}(\mathbf{x})}{p_{r}(\mathbf{x}) + p_{g}(\mathbf{x})} \right\rbrack + \mathbb{E}_{p_{g}(\mathbf{x})}\ \left\lbrack \ln\frac{p_{g}(\mathbf{x})}{p_{r}(\mathbf{x}) + p_{g}(\mathbf{x})} \right\rbrack,$

![Equation](images/B9780443292385000251/si86.png)(19.14)

其中上式是 $p_{g}$ 的函数。回顾 KL 散度的定义（第 [2.5.2](#Chp002_19-64_B9780443292385000081.xhtml) 节和 [12.7](#Chp012_583-634_B9780443292385000184.xhtml) 节），公式 [(19.14)](#Chp019_997-1102_B9780443292385000251.xhtml#deq26) 可紧凑地重写为

$C(G) = \text{KL}(p_{r}||p_{r} + p_{g}) + \text{KL}(p_{g}||p_{r} + p_{g}),$

![Equation](images/B9780443292385000251/si87.png)

正如我们所知，KL 散度关于其参数*不对称*。除以 2 进行归一化，并考虑到 KL 散度的定义，上式可轻松重写为

$C(G) = - \ln 4 + \text{KL}\left( p_{r}||\frac{p_{r} + p_{g}}{2} \right) + \text{KL}\left( p_{g}||\frac{p_{r} + p_{g}}{2} \right),$

![Equation](images/B9780443292385000251/si88.png)

或

