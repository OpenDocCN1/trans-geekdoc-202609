# Glossary (Continued)

DF($t, T$) the discount factor between times $t$ and $T$, where $T \geqslant t$. The price of a nondefaultable zero coupon bond which matures at time $T$ is the expected value of DF($t, T$). In this book we assume that interest rates are deterministic and thus DF($t, T$) is the value of a nondefaultable zero coupon bond maturing at $T$

DF($t, T$) the discount factor (including the possibility of default) between times $t$ and $T$, where $T \geqslant t$: DF($t, T$) = S(t)DF($t, T$). The price of a defaultable zero coupon bond matures at time $T$ is the expected value of DF($t, T$). In this book we assume that interest rates are deterministic and thus DF($t, T$) is the value of a defaultable zero coupon bond maturing at $T$

$F(t, T_1, T_2)$ the forward rate at times $T_1$ and $T_2$ where $T_2 \geqslant T_1$ and $T_1 \geqslant t$

$L(T_1, T_2)$ the simply compounded spot rate between times $T_1$ and $T_2$, where $T_2 \geqslant T_1$

$log(x)$ the natural logarithm of $x$ a normal distribution, with mean $a$ and variance $b$

$dW$, a normal variate (sampled at time $t$) from the distribution $N(0, dt)$, where $dt$ a specified time interval e.g. $dx = \mu dt +dW_t$

$dZ_t$ a normal variate (sampled at time $t$) from the distribution $N(0, 1)$. Note: the default $\psi = \sqrt{dt}dZ_t$ has the same distribution as $dW_t$

IID independently and identically distributed

$U(a, b)$ the uniform distribution, with lower limit $a$ and upper limit $b$

$|x|$ the absolute value of the variable $x$

PDF the probability density function of a given distribution

$x \wedge y$ the minimum of $x$ and $y$, that is, $min(x, y)$

$S(t, T)$ the survival probability between time $t$ and $T$, $T > t$

$||A - B|$ the distance between two matrices with the same dimensions. If $A$ and $B$ both have $n$ rows and $m$ columns then this distance is:

```
sum_{i=1}^n \sum_{j=1}^m [A_{i,j} - B_{i,j}]^2$$
```

where $A_{i,j}$ and $B_{i,j}$ refer to the element in the $i$th row and $j$th column