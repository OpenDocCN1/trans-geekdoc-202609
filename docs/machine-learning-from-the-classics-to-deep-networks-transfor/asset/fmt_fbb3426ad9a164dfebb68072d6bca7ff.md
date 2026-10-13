
$f( \cdot ) = \sum\limits_{n = 1}^{N}\theta_{n}\kappa( \cdot ,\mathbf{x}_{n}).$

![Equation](images/B9780443292385000172/si189.png)(11.19)

In practice, the use of a bias term (which does not enter in the regularization) turns out to improve performance. First, it enlarges the class of functions in which the solution is searched and potentially leads to better performance. Moreover, due to the penalization imposed by the regularizing term, $\Omega(\|f\|^2)$, the minimizer pushes the values which the function takes at the training points to smaller values. The existence of $b$ tries to “absorb” some of this action (see, for example, [112]).

### Remarks 11.2

*   We will use the expansion in Eq. [(11.17)](#Chp011_519-582_B9780443292385000172.xhtml#deq65) in a number of cases. However, it is interesting to apply this expansion to the RKHS of the bandlimited functions and see what comes out. Assume that the available samples from a function $f$ are $f(n)$, $n = 1, 2, \dots, N$ (assuming the case of normalized sampling period $x_s = 1$). Then according to the representer theorem, we can write the following approximation:

$f(x) \approx \sum\limits_{n = 1}^{N}\theta_{n}\text{sinc}(x - n).$

![Equation](images/B9780443292385000172/si193.png)(11.20)

*   Taking into account the orthonormality of the $\text{sinc}(\cdot - n)$ functions, we get $\theta_n = f(n)$, $n = 1, 2, \dots, N$. However, note that in contrast to Eq. [(11.14)](#Chp011_519-582_B9780443292385000172.xhtml#deq46), which is exact, Eq. [(11.20)](#Chp011_519-582_B9780443292385000172.xhtml#deq71) is only an approximation. On the other hand, Eq. [(11.20)](#Chp011_519-582_B9780443292385000172.xhtml#deq71) can be used even if the obtained samples are contaminated by noise.

### 11.6.1 Semiparametric representer theorem

The use of the bias term is also theoretically justified by the generalization of the representer theorem [103]. The essence of this theorem is to expand the solution into two parts, i.e., one that lies in an RKHS $\mathbb{H}$ and another that is given as a linear combination of a set of preselected functions.

### Theorem 11.3

Let us assume that in addition to the assumptions adopted in [Theorem 11.2](#Chp011_519-582_B9780443292385000172.xhtml#enun0050), we are given the set of real-valued functions

$\psi_m: \mathcal{X} \mapsto \mathbb{R},\quad m = 1, 2, \dots, M,$

![Equation](images/B9780443292385000172/si196.png)

with the property that the $N \times M$ matrix with elements $\psi_m(\mathbf{x}_n)$, $n = 1, 2, \dots, N$, $m = 1, 2, \dots, M$, has rank $M$. Then any
