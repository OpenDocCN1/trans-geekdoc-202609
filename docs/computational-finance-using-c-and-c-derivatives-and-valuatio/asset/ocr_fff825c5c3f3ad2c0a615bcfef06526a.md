# 324 APPENDIX | C Standard Statistical Results

Moment generating function of a linear function of a random variable x

If the random variable $y$ is defined as $y = ax+b$, then the moment generating function of $y$, $M_y(t)$ is defined as follows:

```
$M_y(t) = M_{ax+b}(t) = E[e^{ty}] = E[e^{t(ax+bt)}] = e^{bt}E[e^{tx}].
```

Therefore,

```
$M_y(t) = e^{bt}M_x(at). (C.5.3)
```

Moment generating function of a linear combination of random variables

Let $z = x + y$ where $x$ and $y$ are independent random variables then

```
$M_z(t) = E[e^{tz}] = E[e^{t(x+y)}] = E[e^{tx}e^{ty}].
```

Since $x$ and $y$ are independent,

```
$E[e^{tx}e^{ty}] = E[e^{tx}]E[e^{ty}] = M_x(t)M_y(t).
```

More generally, if $s_n = \sum_{i=1}^n x_i$ where $x_i, i = 1, \dots, n$ are independent variables, then

```
$M_{s_n}(t) = \prod_{i=1}^n M_{x_i}(t). (C.5.4)
```

If $x_i, i = 1, \dots, n$ are IID, then we have

```
$M_{s_n}(t) = E\left[\exp\left(t\sum_{i=1}^n x_iight)ight]^n = \left(E[e^{tx}]ight)^n = (M_x(t))^n. (C.5.5)
```