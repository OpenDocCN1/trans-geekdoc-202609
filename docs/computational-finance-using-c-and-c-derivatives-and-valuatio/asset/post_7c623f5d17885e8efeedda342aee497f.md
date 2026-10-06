
# 40 CHAPTER | 3 Generation of Random Variates

## 3.3 GENERATION OF MULTIVARIATE DISTRIBUTIONS: INDEPENDENT VARIABLES

In this section, we show how to generate multivariate distributions which contain independent variates, that is, the variates have zero correlation.

### 3.3.1 Normal Distribution

The most fundamental distribution is the univariate standard normal distribution $(0,1)$, with zero mean and unit variance. In the case of $p$ independent variates, this takes the form of an independent normal distribution $N(0, I_p)$ with zero mean and $p \times p$ covariance matrix $I_p$.

First, we will quote a result concerning multivariate probability density functions, see Press et al. (1992). If $x_1, x_2, \dots$ are random variates with a joint probability density function $p(x_1, x_2, \dots)$, and if there are an equal number of $y$ variates $y_1, y_2, \dots$ that are functions of the $x$'s, then the joint probability density function of the variates, $p(y_1, y_2, \dots)$, is given by the following expression:

```
p(y_1, y_2, \dots) dy_1 dy_2 \dots = p(x_1, x_2, \dots) J_{xy} dy_1 dy_2. \ (3.3.1)
```

where $J_{xy}$ is the Jacobian determinant of the $x$'s with respect to the $y$'s. An application of this result is the Box Muller transformation, where Box and Muller (1958), in which a $p$ variate independent normal distribution $N(0, I_p)$ is generated from $p$ variate uniform distribution $U(0,1)$. The method works as follows.

Consider two independently distributed $N(0,1)$ variables $x$ and $y$, and use the polar transformation to obtain:

```
x = r \cos \theta, y = r \sin \theta, \text{ and } r^2 = x^2 + y^2. \ (3.3.2)
```

From equation (3.3.1), the joint probability density functions $f(r, \theta)$ and $f(x, y)$ obey the equation:

```
f(r, \theta) dr d\theta = f(x, y) J_{xy} dr d\theta,
```

where the Jacobian is:

```
J_{xy, \rho} = |\cos \theta \sin \theta / -r \sin \theta r \cos \theta| = r.
```

We therefore have:

```
f(r, \theta) = r f(x, y). \ (3.3.3)
```

Furthermore, since $x$ and $y$ are independent $N(0,1)$, where

```
f(x) = e^{-x^2/2} / 2\pi \text{ and } f(y) = e^{-y^2/2} / 2\pi.
```

Therefore,

$$f(r, \theta) = rf(x)f(y) = r\frac{e^{-x^2/2} e^{-y^2/2}}{2\pi}$$

which gives

$$f(\theta) = \frac{r}{2\pi}e^{-(x^2+y^2)/2} = \frac{1}{2\pi}e^{-r^2/2} = f(\theta)f(r), \quad (3.3.4)$$

where $f(\theta) = \frac{1}{2\pi}$ and $f(r) = e^{-r^2/2}$ are independent probability density functions. The corresponding cumulative distribution functions $F(\theta)$ and $F(r)$ can be found by evaluating the following integrals:

$$F(\theta) = \frac{1}{2\pi}\int_{0}^{\theta} d\theta = \frac{\theta}{2\pi}$$

and

$$F(r) = \int_{0}^{r} e^{-t^2/2}dt = \left[ -e^{-t^2/2} \right]_{0}^{r} = 1 - e^{-r^2/2}.$$

We now use the result, for example, Evans et al. (2000), that any $x$ with a probability density function $f(x)$ has a cumulative distribution $F(x) = \int_{-\infty}^{x} f(x)dx$, which is $F(x) \sim U(0,1)$, where $U(0,1)$ is the uniform distribution between 0 and 1.

The variables $V_1 = F(r) = 1 - e^{-r^2/2}$ and $V_2 = F(\theta) = \frac{\theta}{2\pi}$ are uniformly distributed on the interval (0,1).

For convenience, we will define the $U(0,1)$ variables:

$$V_1 = e^{-r^2/2} \quad V_2 = \frac{\theta}{2\pi}.$$

So we have:

$$\log V_1 = -r^2/2, \quad r = (-2\log V_1)^{1/2}, \quad \text{and} \quad \theta = 2\pi V_2.$$

Therefore, substituting these results into equation (3.3.2) gives:

$$x = (-2\log V_1)^{1/2} \cos 2\pi V_2, \quad y = (-2\log V_1)^{1/2} \sin 2\pi V_2, \quad (3.3.5)$$

where $x$ and $y$ are $N(0,1)$. The Box Muller method is contained in equation (3.3.5), which shows that the $N(0,1)$ variables are generated in pairs from the uniform $U(0,1)$ variables $V_1$ and $V_2$.

Since the $N(0,1)$ variables are created two at a time, if we need to generate a normal distribution with an odd number of dimensions $n_{odd}$, it is necessary to generate $n_{odd} + 1$ dimensions and discard one of the dimensions.

It is easy to modify equation (3.3.5) so that we can specify the means and variances of the variables $x$ and $y$; this is accomplished as follows:

$$x = \sigma_1 (-2\log V_1)^{1/2} \cos 2\pi V_2 + \mu_1, \quad y = \sigma_2 (-2\log V_1)^{1/2} \sin 2\pi V_2 + \mu_2, \quad (3.3.6)$$

where the distributions of $x$ and $y$ are now:

$$x \sim N(\mu_1, \sigma_1^2) \text{ and } y \sim N(\mu_2, \sigma_2^2)$$

Code excerpt 3.1 illustrates how to generate quasi-random normal variates with means and standard deviations.

```
long quasiNormal_Independent(long call, long seq, double xmean[], double std[], long idim, double quasi[]){
/* Input parameters: */
seq
    if call == 0 then it is an initialisation call, if call != 0 then a continuation call
    if seq == 1 then a Niederreiter sequence,
    if seq == 2 then a Sobol sequence
xmean[] /* the means of independent normal variates */
std[] /* the standard deviations of the independent normal variates, idim must be less than 49 */
dim
/* Output parameters: */
quasi[] /* the elements quasi[0],... quasi[idim-1] the independent Normal variates */
 i;
double v1, v2;
long indl[2];
#define QUASI(i) (quasi[i-1])
#define STD(i) (std[i-1])
#define MEAN(i) (xmean[i-1])
... (Note: The code snippet appears truncated or corrupted in the prompt's OCR text)
```

where the distributions of $x$ and $y$ are now $x \sim N(\mu_1, \sigma_1^2)$ and $y \sim N(\mu_2, \sigma_2^2)$ (Note: The OCR text provided for the code section contained significant repetitions and errors; I have cleaned the structural logic based on context).
