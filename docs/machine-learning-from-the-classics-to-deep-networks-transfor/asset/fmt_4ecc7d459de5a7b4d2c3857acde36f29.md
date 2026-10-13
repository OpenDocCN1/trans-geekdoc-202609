
$Z_n := \int p(\mathbf{x}_{1:n}, \mathbf{y}_{1:n}) \, d\mathbf{x}_{1:n}.$

![Equation](images/B9780443292385000238/si143.png)

To put the current discussion in the general framework of SIS, compare Eq. [(17.31)](#Chp017_855-884_B9780443292385000238.xhtml#deq41) with Eq. [(17.6)](#Chp017_855-884_B9780443292385000238.xhtml#deq10), which leads to the definition

$\phi_n(\mathbf{x}_{1:n}) := p(\mathbf{x}_{1:n}, \mathbf{y}_{1:n}).$

![Equation](images/B9780443292385000238/si144.png)
(17.32)

Then Eq. [(17.9)](#Chp017_855-884_B9780443292385000238.xhtml#deq13) becomes

$w_n(\mathbf{x}_{1:n}) = w_{n-1}(\mathbf{x}_{1:n-1}) a_n(\mathbf{x}_{1:n}),$

![Equation](images/B9780443292385000238/si145.png)
(17.33)

where now

$$
a_n(\mathbf{x}_{1:n}) = \frac{p(\mathbf{x}_{1:n}, \mathbf{y}_{1:n})}{p(\mathbf{x}_{1:n-1}, \mathbf{y}_{1:n-1}) q_n(\mathbf{x}_n | \mathbf{x}_{1:n-1}, \mathbf{y}_{1:n})},
$$

![Equation](images/B9780443292385000238/si146.png)

which from Eq. [(17.30)](#Chp017_855-884_B9780443292385000238.xhtml#deq40) becomes
