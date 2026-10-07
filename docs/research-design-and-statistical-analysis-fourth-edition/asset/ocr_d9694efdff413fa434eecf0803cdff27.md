# RULE 2. The expectation of a constant is the constant:

$E(C) = C$

If several events have the same numerical value C, their average value will equal C.

# RULE 3. $E$ follows the distributive law and acts just like a multiplier. For example,

$E(X + Y) = E(X) + E(Y)$

To prove this, we begin with the definition of $E(X + Y)$:

```
$E(X + Y) = \sum_{x} \sum_{y} (x + y)p(x,y)$
```

when the expression on the right indicates that each possible value of $X + Y$ is multiplied by its joint probability, and these products are then summed. Distributing this expression, we obtain

```
$E(X + Y) = \sum_{x} \sum_{y} xp(x,y) + \sum_{x} \sum_{y} yp(x,y)\n= \sum_{x} x \sum_{y} p(x,y) + \sum_{y} y \sum_{x} p(x,y)\n= \sum_{x} xp(x) + \sum_{y} yp(y) = E(X) + E(Y)$
```

A special case of this expression occurs when one variable is replaced by a constant; then

$E(Y + C) = E(Y) + E(C) = E(Y) + C$

This equation allows us to assert that

$E(Y - \mu) = 0$

because

$E(Y - \mu) = E(Y) - \mu = \mu - \mu = 0$

Another application of Rule 3

```
$E(X + Y)^2 = E(X)^2 + E(Y)^2 + 2E(XY)$
```

This leads to a proof of the statement in Chapter 2 that the variance of $Y$, $E(Y - \mu)^2$, equals $E(Y^2) - \mu^2$: