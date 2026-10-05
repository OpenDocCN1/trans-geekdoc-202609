# Functions

shows the intermediary results:

```
where5f is the first item of the x variable,--31f = 5f - 6f xexp 2 and-80f = (5f
- 6f xexp 2) - 7f xexp 2.
```

# 3.2.5.1 EMA: The Exponential Moving Average

Let's see how can be applied to compute this very common iterative func-
tion we want the intermediate results of the time series. Given a vector
x0,x1,...,xi,...,xj...xn and a weight lambda, the EMA at point i is defined as:

```
$EMA_{i}(\lambda) = x_{i-1} \times (1-\lambda) + EMA_{i-1} \times \lambda$
```

where EMA_{0} = x_{0}$.
Given the vector 20 30, and a lambda of 2, the EMA at each point will be

| 10 | / x[0] |
| (10 * 0.8 ) + 20 * 0.2 | / ( x[0] * (1 - lambda) ) + x[1] * lambda |

| 12f |
| (12 * 0.8 ) + 30 * 0.2 | / ( x[1] * (1 - lambda) ) + x[2] * lambda |

15.6

> We can use scan to implement the above iteratively:

```
.quantQ.stats.expma1::[lambda;vector]
/ lambda -- memory
/ vector -- data
{{x;y;z}(x+y)+z}\[ first vector; 1 - lambda; vector * lambda]
};
```

and

```
.quantQ.stats.expma1[0.2;10 20 30]
```

10 12 15.6

Note that, since version 3.1, q has an optimisation which simplifies

```
{{z+y+x}\[x;y;z]}
```

to

```
{x y\z}
```