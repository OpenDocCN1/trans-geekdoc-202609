# 346 | Blockchain and Distributed Ledgers: Mathematics, Technology, and Economics

The corresponding optimal values ($x^*, y^*, \Omega^*$) are

```
$x^* = \sqrt{P}, y^* = \frac{1}{\sqrt{P}}, \Omega^* = \left(\sqrt{P}-1\right)^2 N. \quad (10.68)
```

This equation shows that a constant product collateral pool cannot be exhausted. At every stage, the values of $TN_1$ and $TN_2$, held in the portfolio are equal to $\sqrt{PN}$, Since the value of both tokens in the portfolio has equal, the implied optimal value of $TN_2$ expressed in terms of $TN_1$ is $P^*=x*/P$, as a consequence of arbitrage. The value of the arbitrated portfolio is $\pi^*=2\sqrt{PN}$, while the buy-and-hold portfolio value is $(P+1)N$. The difference is given by

```
$\omega = (P+1)N - 2\sqrt{PN}. \quad (10.69)
```

The percentage loss of the realized portfolio compared to the buy-and-hold portfolio is

```
$\lambda = 1 - \frac{2\sqrt{P}}{(P+1)} = \frac{(\sqrt{P}-1)^2}{(P+1)}. \quad (10.70)
```

For the mixed ruleget, the arbitrageur's profit for $P > 1$ has the form:

```
$\Omega(x) = (P(1-y_a(x)) - (x-1))N, \quad (10.71)
```

with the optimum achieved at $x_a^*, y_a^*, \Omega_a^*$, such that

```
$y_a^*(x_a^*) = \frac{1}{P}, u_a^*(x_a^*) = x_a^*, \Omega_a^* = (P(1-y_a^*) - (x_a^*-1))N. \quad (10.72)
```

We find $x_a^*$ via the Newton-Raphson method starting with a suitable $x_a^{(0)}$:

```
$x_a^{(n+1)} = x_a^{(n)} - \frac{y_a'^{(n)}}{y_a''^{(n)} + 1/P}. \quad (10.73)
```

Since the Newton-Raphson method has quadratic convergence, we can choose 10 iterations and set $x_a^* = x_a^{(10)}$. The value of the arbitrated portfolio is

```
$$\pi^* = x_a^* + Py_a(x_a^*). \quad (10.74)
```