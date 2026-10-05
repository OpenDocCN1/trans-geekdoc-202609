# 46 • NETWORK SECURITY AND CRYPTOGRAPHY

$F_x(x)$ and $F_y(y)$ are known as the marginal cumulative distribution functions.

Similarly, the individual probability density functions of the random variables $X$ and $Y$ can be obtained from their joint probability density function. For $X$,

```
$f_x(x) = \frac{dF_x(x)}{dx} \xrightarrow{=} \int_{XY} (x,y)dy \quad (2.36)
```

and $Y$,

```
$f_y(y) = \frac{dF_y(y)}{dy} \xrightarrow{=} \int_{XY} (x,y)dx \quad (2.37)
```

$f_x(x)$ and $f_y(y)$ are known as the marginal probability density functions.

As mentioned earlier, two random variables are independent if the values taken by one do not affect the other. As a result,

```
$P(X \le x, Y \le y) = P(X \le x)P(Y \le y) \quad (2.38)
```

or

```
$F_{XY}(x,y) = F_x(x)F_y(y) \quad (2.39)
```

This condition is equivalent to

```
$f_{XY}(x,y) = f_x(x)f_y(y) \quad (2.40)
```

Thus, two random variables are independent when their joint distribution is the product of their individual marginal distributions (or densities).

Finally, we may extend the concept of conditional probabilities to the case of continuous random variables. The conditional probability density function of $X$ given the event $Y=y$ is

```
$f_X(x|Y=y) = \frac{f_{XY}(x,y)}{f_y(y)} \quad (2.41)
```