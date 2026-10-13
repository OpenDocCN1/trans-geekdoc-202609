
(a) $\hat{\theta}[0] = 0.028$, $\hat{\theta}[1] = 0.226$, $\hat{\theta}[2] = -0.224$; (b) $\hat{\theta}[0] = 0.914$, $\hat{\theta}[1] = 0.325$, $\hat{\theta}[2] = -0.477$.

![Equation](images/B9780443292385000093/si83.png)

for the two cases, respectively. [Figs. 3.4](#Chp003_65-117_B9780443292385000093.xhtml#f0025)A and B show the recovered planes. Observe that in the case of [Fig. 3.4](#Chp003_65-117_B9780443292385000093.xhtml#f0025)A, corresponding to a noise variable of small variance, the obtained plane follows the data points much closer than that of [Fig. 3.4](#Chp003_65-117_B9780443292385000093.xhtml#f0025)B.

### Remarks 3.1

*   The set of points $(\hat{y}[n], x[n1], \dots, x[nl])$, $n = 1, 2, \dots, N$, lie on a *hyperplane* in the $\mathbb{R}^{l+1}$ space. Equivalently, they lie on a hyperplane that crosses the origin and, thus, it is a linear subspace in the extended space $\mathbb{R}^{l+2}$ when one absorbs $\theta[0]$ in $\boldsymbol{\theta}$, as explained previously.
*   Note that the prediction model in Eq. [(3.11)](#Chp003_65-117_B9780443292385000093.xhtml#deq14) could still be used, even if the true system structure does not obey the linear model in Eq. [(3.9)](#Chp003_65-117_B9780443292385000093.xhtml#deq11). For example, the true dependence between $y$ and $\mathbf{x}$ may be a nonlinear one. In such a case, the predictions of $y$ based on the model in Eq. [(3.11)](#Chp003_65-117_B9780443292385000093.xhtml#deq14) may, however, not be satisfactory. It all depends on the deviation of our adopted model from the true structure of the system that generates the data.
*   The prediction performance of the model also depends on the statistical properties of the noise variable. This is an important issue. We will see later on that, depending on the statistical properties of the noise variable, some loss functions and methods may be more suitable than others.
*   The two previous remarks suggest that in order to quantify the performance of an estimator some related criteria are necessary. In Section [3.9](#Chp003_65-117_B9780443292385000093.xhtml#s0065), we will present some theoretical touches that shed light on certain aspects related to the performance of an estimator.

## 3.4 Classification
