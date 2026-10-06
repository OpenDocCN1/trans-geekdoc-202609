# 7.5 Specialization to Interval-Valued Inputs

**Table 7.1** Maximal values of problem (7.16)

| Case | Maximal value |
|--- |--- |
| (I), (1) | $\max\{\underline{a}, b-ar{a}\}$ |
| (I), (2) | 0 |
| (I), (3), (i) | $\underline{b}-ar{a}$ |
| (I), (3), (ii) | $\underline{a}-ar{b}$ |
| (II), (1) | $\underline{b}-ar{a}$ |
| (II), (2) | $\underline{a}-ar{b}$ |

**Table 7.2** Constraint distances in the proof of Theorem 7.4 (c)

| Case | $d_c\{[\underline{a}, ar{a}], [\underline{b}, ar{b}]\}$ |
|--- |--- |
| (I), (1) | $\max\{\underline{a}, b-ar{a}\} = \max\{\underline{a}-b, \underline{a}-ar{b}\}$ |
| (I), (2) | $\max\{b-\underline{a}, ar{b}\} = \max\{\underline{a}-b, \underline{a}-ar{b}\}$ |
| (I), (3), (i) | $\max\{\underline{a}, b-ar{a}\} = \max\{\underline{a}-b, \underline{a}-ar{b}\}$ |
| (I), (3), (ii) | $\max\{\underline{a}, b-ar{a}\} = \max\{\underline{a}-b, \underline{a}-ar{b}\}$ |
| (II), (1) | $\max\{b-\underline{a}, ar{b}\} = \max\{\underline{a}-b, \underline{a}-ar{b}\}$ |
| (II), (2) | $\max\{b-\underline{a}, ar{b}\} = \max\{\underline{a}-b, \underline{a}-ar{b}\}$ |

Similarly, we determine the maximum value of the problem

```
$sup_{x\in[underline{b}, \bar{b}]} \max\{0, a-x\} + \max\{0, x-\bar{b}\} = \max_{x\in[underline{b}, \bar{b}]} \max\{0, a-x\} + \max\{0, x-\bar{b}\}\$
```

by renaming. For the cases already mentioned, the results can be found in Table 7.1. To determine the constraint distance, we must now insert all the results into the formula

> $d_c\{[\underline{a}, \bar{a}], [\underline{b}, \bar{b}]\} = \max_{x\in[\underline{a}, \bar{a}]} \max\{0, \underline{b}-x\} + \max\{0, x-\bar{b}\} = \max_{x\in[\underline{b}, \bar{b}]} \max\{0, a-x\} + \max\{0, x-\bar{b}\}\$

In each case considered, the value of the constraint distance is given in Table 7.2. In this way, the assertion in (c) is proven.

In the case of compact intervals in $\mathbb{R}$, the Hausdorff and constraint distance coincide according to Theorem 7.4. And for the intervals, which additionally contain 0, the radial distance is also equal to these two distances. This shows that the radial and constraint distances play out their advantages only in more complex situations.