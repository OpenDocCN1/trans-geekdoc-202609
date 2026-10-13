
where the expectation is taken with respect to the conditional probability of `y` given the value of `x`, or in other words, `p(y|x)`.

We will show that the optimal estimator is the mean value of `y`, or

```
f(x) = E[y|x] (3.48)
```

**Proof**

We have

```
E[(y - f(x))²] = E[(y - E[y|x] + E[y|x] - f(x))²]
             = E[(y - E[y|x])²] + E[(E[y|x] - f(x))²] + 2E[(y - E[y|x])(E[y|x] - f(x))]
```

where the dependence of the expectation on `x` has been omitted for notational convenience. It is readily seen that the last (product) term on the right-hand side is zero, hence, we are left with the following:
