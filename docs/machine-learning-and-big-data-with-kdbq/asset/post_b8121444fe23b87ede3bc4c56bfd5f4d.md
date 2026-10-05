
# Time Series Econometrics

```python
.quantQ.ts.Y:[y;p]
// y historical data of the endogenous variable (list of floating
// numbers)
// p order of the VAR(p) process
:y;p+tilt y[0]+1-p;
```

The estimator of the VARX(p,q) model is implemented as:

```
.quantQ.varX:[x;y;q;p]
// x historical data of the endogenous variable (list of floating
// numbers)
// y historical data of the endogenous variable (list of floating
// numbers)
// q order of the exogenous process
// p order of the VAR(p) process
z0:quantQ.ts.ZX[x;y;q;p]
:y;p+tilt count y[0])-p mmu flip (z0) mmu inv (flip z0) mmu z0;
```

The estimator of the variance-covariance residual is adjusted to include
the q exogenous variables:

```
.quantQ.ts.covarianceResidual:[x;y;q;p]
// x historical data of the exogenous variable (list of floating
// numbers)
// y historical data of the endogenous variable (list of floating
// numbers)
// q order of exogenous process
// p order of the VAR(p) process
yp0:quantQ.ts.Y[y;p];
z0:quantQ.ts.ZX[x;y;q;p];
T:count y[0];
K:count y;
coef1:(T-(K+p)-1f);
coef*(ymu flip yp0) - ymu flip (z0) mmu inv[z0 mmu flip z0] mmu
- z0 mmu flip yp0;
```

The 1-step and n-step forecasting of the VARX(p,q) model based on the data series y and exogenous series x are given by following two functions:
first, the 1-step forecast of a VARX(p,q) model:

```
.quantQ.ts.estimateX::[x;y;q;p]
// x historical data of the exogenous variable (list of floating
// numbers)
// y historical data of the endogenous variable (list of floating
// numbers)
// q order of exogenous process
// p order of the VAR(p) process
M:quantQ.ts.varX[x;y;q;p];
M:y[;];
v:M y;
k:count y;
m:count x;
```

```python
:v+sum[[[i]M;(1+k+i)+til mmu y[(count y[0])-(1+i)]) each til p+
sum[[[i]M;(1+k*p)+(m+i)+til mmu x[(count x[0])-(1+i)] each til
  q]+
nM;1+(k*p)+(m*q)+til mmu x[0];
```

Second, the n-step forecast of a VARX(p,q) model:

```python
.quantQ.ts.estimateNX:[n;x;y;q]
// n -- positive integer indicating the number of steps of the forecast
// x -- historical data of the exogenous variable (list of floating
  // numbers)
// y -- historical data of the endogenous variable (list of floating
  // numbers)
// p -- order of the VAR(p) process
output:=quantQ.ts.estimateX[x;y;q;p];
[$n>1;
{
  newx:=quantQ.ts.estimateN[(n-1);q;x];
  .quantQ.ts.estimateNX[n-1,newx,y,output;q;p];
};
output];
;
```

# CHAPTER 15

## Fourier Transform

In this chapter, we introduce the implementation of the Fourier Transform, in particular, the discrete Fourier transform (DFT) and illustrate its usage for time analysis. The DFT allows us to transform a time series from a time domain to a frequency domain and understand the periodicity, if any, of the contributing components. In order to be able to introduce the DFT, we first start with complex numbers. After introducing the DFT, we conclude with a bonus section on quaternions and fractals.

### 15.1 COMPLEX NUMBERS

Complex numbers are native to some languages, but this is not the case in Julia, which does not go beyond real numbers. What is a complex number? For a full answer, see Agarwal et al. (2011). In a nutshell, a complex number is a number which can be written as $a + bi$, where $a$ and $b$ are real numbers and $i^2 = -1$. It is the last property of $i$, which distinguishes complex numbers from reals as there is no real number $i$ would satisfy this condition.

Alternatively, we define a complex number $z$ as a linear polynomial in a single indeterminate $x$:

$z = a + bx,$ (15.1)

where additional constraint on $x$ is imposed:

$x^2 + 1 = 0.$ (15.2)

We can treat complex numbers as polynomials. The algebraic operations for complex numbers can be derived from those defined for polynomials. It is convenient to denote the variable $x$ as $i$. An example of a complex number is $1 + i$. The number 1 is the real part of the complex number, and the number $i$ is the imaginary part. The word "imaginary" does not mean that complex numbers are not useful. On the contrary, they prove to be important in physics and mathematics.

From a mathematical perspective, the system of complex numbers is an algebraic extension of reals by an imaginary number $i$. This gives rise to an analogy between complex numbers and polynomials with $i$ and allows the system

### 15.1.1 Properties of Complex Numbers

Complex numbers are represented in two parts: real and an imaginary part. In our implementation, we use a dictionary to represent the two parts. The first key `re` corresponds to the real part while the second key `im` represents the imaginary part. Let us define an example as:

```python
cx1: re`im 0;
cx2: re`im 1;
cx3: re`im[-0.5]+2.0;
```

The first complex `cx1` is equivalent to the real number 1.0, the complex number `cx2` is the pure imaginary number $i$, and the last complex number is a randomly generated one:

| cx3 | |
|---|---|
| re | -0.1072476 |
| im | 0.0170912 |

In the following paragraphs, we define the set of utility functions for operations on complex numbers. The convention is that all the functions are prepended with `.quantQ.complex`. The first algebraic operation is to define adding two numbers. Mathematically, the sum of two complex numbers:

$z1 + z2 = (a1 + b1i) + (a2 + b2i) = (a1 + a2) + (b1 + b2)i.$ (15.3)

We can thereafter simply do:

`cx1 + cx2`

| | |
|---|---|
| re | 1.449117 |
| im | -9.093283 |

Further, we define the complex conjugate of the complex number as:

$z^* = (a + bi)^* = (a - bi). \quad (15.6)$

In the geometric interpretation, the complex conjugate is a reflection around the real axis. Further, the following relationship $z^* = z$ is equivalent to stating that the complex number $z$ is real. We can get the real and imaginary parts:

$a = \frac{z + z^*}{2}, a = \frac{z - z^*}{2i}. \quad (15.7)$

The complex conjugate function is then provided as:

```python
.quantQ.complex.conjugate:@[im;neg]
giving:
.quantQ.complex.conjugate[cx3]
```

| cx3 | |
|---|---|
| re | -0.1072476 |
| im | 0.0170912 |

The geometric interpretation of the complex numbers would require a few functions, in particular, to convert a complex number into polar coordinates:

$z = (a + bi) = re^{i\phi}. \quad (15.8)$

When $r$ is the modulus of the complex number and $\phi$ is the polar angle. When a complex number is interpreted as a vector on the two-dimensional plane originating at (0,0), then $r$ is the length of the vector, and $\phi$ is the angle of the vector with the positive part of the real axis.

The modulus is given as:

$|z| = z * z^* = a^2 + b^2. \quad (15.9)$

In order to obtain the polar angle, we have to employ a trigonometric formula which depends on the complex number itself:

$\phi = \begin{cases} \arctan(\frac{b}{a}) & if a > 0, \arctan(\frac{b}{a}) + \pi & if a < 0 \text{ and } b \geq 0, \arctan(\frac{b}{a}) - \pi & if a < 0 \text{ and } b < 0, \frac{\pi}{2} & if a = 0 \text{ and } b > 0, \-\frac{\pi}{2} & if a = 0 \text{ and } b < 0, \text{not defined} & if a = 0 \text{ and } b = 0, \end{cases} \quad (15.10)$

where $\phi$ is defined within the interval $(-\pi, \pi]$.
