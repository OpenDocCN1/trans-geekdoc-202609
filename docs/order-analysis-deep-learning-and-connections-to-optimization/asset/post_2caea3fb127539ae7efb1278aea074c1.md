
# 116 Basics of Deep Learning

is then called quasi-Newton equation or secant equation (cf. [28, 148]). In general, quasi-Newton methods work with update formulas for matrices $B'$ satisfying the quasi-Newton equation (6.11).

Since optimization in deep learning can have millions of variables, it is not practical to work with dense matrices $B'$ (standard quasi-Newton methods cannot be used). As a consequence, we choose a simple class of matrices, as the class of matrices $\lambda I$, where $\lambda > 0$ must be chosen appropriately and $I$ denotes the $(n, n)$ identity matrix. Barzilai and Borwein [12] used the quasi-Newton equation to determine an appropriate step size for the gradient descent method. To obtain a good approximation of Eq. (6.11) for this special class of matrices, we solve the optimization problem

$$\|\lambda I(x^i - x^{i-1}) - (\nabla f(x^i) - \nabla f(x^{i-1}))\|_2^2. \quad (6.12)$$

which can be rewritten as

$$\min_{\lambda>0}(x^i - x^{i-1})^T(\nabla f(x^i) - \nabla f(x^{i-1}))^T[\lambda(x^i - x^{i-1}) - (\nabla f(x^i) - \nabla f(x^{i-1}))].$$

For each minimal $\lambda > 0$, the derivative of the objective function of this optimization problem vanishes, we get

$$0 = (x^i - x^{i-1})^T[\lambda(x^i - x^{i-1}) - (\nabla f(x^i) - \nabla f(x^{i-1}))] + [x^i - x^{i-1})^T(\nabla f(x^i) - \nabla f(x^{i-1}))^T](x^i - x^{i-1})$$
$$=2\tilde{\lambda}(x^i - x^{i-1})^T(x^i - x^{i-1}) - 2(x^i - x^{i-1})^T(\nabla f(x^i) - \nabla f(x^{i-1}))$$

implying

$$\tilde{\lambda} := \frac{(x^i - x^{i-1})^T(\nabla f(x^i) - \nabla f(x^{i-1}))}{(x^i - x^{i-1})^T(x^i - x^{i-1})}.$$$$

It is known from quasi-Newton methods that the iteration reads as follows:

$$x^{i+1} := x^i + (B^i)^{-1}d^i = x^i + \frac{1}{\lambda}d^i.$$

If we set

$$\lambda_i := \frac{1}{\tilde{\lambda}} = \frac{(x^i - x^{i-1})^T(x^i - x^{i-1})}{(x^i - x^{i-1})^T(\nabla f(x^i) - \nabla f(x^{i-1}))}.$$$$

we obtain the Barzilai-Borwein step size rule in line 9 of Algorithm 6.2. This choice of $\lambda_i$ does not guarantee descent in the objective function $f$ (see [117, p. 27]).

## 6.6 Gradient Methods

**Remark 6.4 (Second Barzilai-Borwein Formula)** Beside the formula for $\lambda_j$ in line 9 of Algorithm 6.2, there is another formula by Barzilai and Borwein [12]. It reads

$$\lambda_i := \frac{(x^i - x^{i-1})^\text{T}(\nabla f(x^i) - \nabla f(x^{i-1}))}{(\nabla f(x^i) - \nabla f(x^{i-1}))^\text{T}(\nabla f(x^i) - \nabla f(x^{i-1}))} \quad (6.13)$$

If we consider again the quasi-Newton equation (6.11) but with the class of updates $B'_i := \frac{1}{\lambda}$ for $\lambda > 0$, we can also solve the optimization problem

$$\min_{\lambda>0} \|x^i - x^{i-1}\|^2 - \lambda(\nabla f(x^i) - \nabla f(x^{i-1}))\|_2^2.$$

With similar arguments as Remark 6.3, we can then obtain the formula (6.13). The formula (6.13) can also be used in Algorithm 6.2. However, Dai and Liao [27, line on p. 8] find that the formula (6.13) often performs well in practical computations than the formula in Algorithm 6.2. Occasionally, the $\lambda_i$ in Algorithm 6.2 is the long *BB step size* and $\lambda_i$ in (6.13) is the short *BB step size* (see [65, 718]). It is interesting to note that both formulas do not guarantee a decrease of the objective function values, there does not necessarily have to be a descent [117, 27]].

There is work on extending the step size formula in Algorithm 6.2 (see among others [117, 65]). And there are convergence results under special assumptions on the objective function (see [40] for an early patch on the convergence of gradient methods and [12, 134]).

Using a simple, modified test problem by Barzilai [117], we now discuss features of Algorithm 6.2 in the following example:

**Example 6.3 (Modified Test Problem 2 in [117])** For an arbitrary $n \in \mathbb{N}$, we study the unconstrained optimization

$$\min_{x\in\mathbb{R}^n} f(x) \quad (6.14)$$

with the objective function $f : \mathbb{R}^n \to \mathbb{R}$ defined by

$$f(x) := \sum_{j=1}^n \frac{1}{10}(e^{x_j} - 1)^2 \text{ for } x := (x_1, \dots, x_n) \in \mathbb{R}^n. \quad (6.15)$$

The optimization problem (6.14) is scalable in the dimension $n$. The $j$-th summand (with $j \in \{1, \dots, n\}$) in (6.15) depends on only one variable, $x_j$; in this sense, the variables are decoupled. In contrast to the original test problem 2 by Barzilai [117], here the term "$-1$" is added to avoid that the minimal value of $f$ increases strongly with large dimensions. Every sum in (6.15) is nonnegative and for all $x \in \mathbb{R}^n$ even positive. Consequently, the objective function $f$ has the unique global point $\tilde{x} := (0, 0, \dots, 0) \in \mathbb{R}^n$ with the function value $f(\tilde{x}) = 0$. For $n = 2$, level lines of the objective function $f$ together with the minimal point $\tilde{x}$ are shown in Fig. 6.12. For numerical computations, we use the starting Table 6.2 results for Algorithm 6.2 in Example 6.3

| Number $n$ of variables | Stopping criterion $\epsilon$ | Number $i$ of iterations | $\|\nabla f(x_i)\|_2$ | $f(x_i)$ | CPU time in seconds |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 10 | $10^{-5}$ | 21 | $4.6341 \cdot 10^{-6}$ | $5.1095 \cdot 10^{-11}$ | 0.02 |
| 100 | $10^{-5}$ | 75 | $5.7853 \cdot 10^{-6}$ | $9.9415 \cdot 10^{-12}$ | 0.1 |
| 1,000 | $10^{-5}$ | 255 | $6.6261 \cdot 10^{-6}$ | $1.7014 \cdot 10^{-10}$ | 0.17 |
| 10,000 | $10^{-5}$ | 1,419 | $4.6969 \cdot 10^{-6}$ | $-1.6692 \cdot 10^{-6}$ | 177.59 |
| 100,000 | $10^{-3}$ | 1,110 | $9.9359 \cdot 10^{-4}$ | $-1.634 \cdot 10^{-4}$ | 1,170.18 |

![Fig 6.11](img/e4a2e491dbba0d9f71abf293f149cd5b_126_0.png)
**Fig 6.11** Illustration of a part of the objective function in Example 6.3

![Fig 6.12](img/e4a2e491dbba0d9f71abf293f149cd5b_126_1.png)
**Fig 6.12** Level lines of the objective function $f : \mathbb{R}^2 \to \mathbb{R}$ with $f(x_1, x_2) := \frac{1}{10}(e^{x_1}-1)^2 + \frac{1}{2}(e^{x_2}-1)^2$ for all $(x_1, x_2) \in \mathbb{R}^2$

Fig. 6.13 Descent and ascent of the function values $f(x^i)$ at the iteration points $x^i \in \{1,\dots,21\}$ in Example 6.3 for the special case $n=10$. The function value $f(x^0)$ at the starting vector $x^0$ is also displayed. A semilog scale is used $x^0 := \frac{10}{n}(1,1,\dots,1)$, which depends on the dimension $n$. Table 6.2 shows the numerical results obtained with MATLAB R2021a on an 8-core iMac. The following points are of interest for this test problem: Algorithm 6.2 is quite fast because of its special step size rule. It also works in high dimensions. For ten variables, one gets acceptable results for a reduced tolerance $\epsilon = 10^{-3}$. Even in the case of $n=10$, we generally do not see a descent at each iteration. This is illustrated in Fig. 6.13, which shows the value of the objective function $f$ at 21 iteration points. Ascent may be possible at certain iteration points. This may be useful for problems

**Table 6.3** results for Algorithm 6.2 in Example 6.3 modified by the second Barzilai-wein step formula (6.13)

| Number of variables | Stopping criterion $\epsilon$ | Number $i$ of iterations | $||\nabla f(x_i)||_2$ | $f(x_i)$ | CPU time in seconds |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 10 | $10^{-5}$ | 21 | $6.5241 \cdot 10^{-6}$ | $1.0725 \cdot 10^{-10}$ | 0.02 |
| 100 | $10^{-5}$ | 69 | $4.1689 \cdot 10^{-6}$ | $1.4106 \cdot 10^{-10}$ | 0.07 |
| 1,000 | $10^{-5}$ | 207 | $9.9353 \cdot 10^{-6}$ | $4.8047 \cdot 10^{-10}$ | 0.14 |
| 10,000 | $10^{-5}$ | 1,090 | $9.8901 \cdot 10^{-6}$ | $-1.7204 \cdot 10^{-6}$ | 111.54 |
| 100,000 | $10^{-3}$ | 876 | $8.9076 \cdot 10^{-4}$ | $-1.6088 \cdot 10^{-4}$ | 745.4 |

![Fig 6.13](img/e4a2e491dbba0d9f71abf293f149cd5b_127_0.png)
