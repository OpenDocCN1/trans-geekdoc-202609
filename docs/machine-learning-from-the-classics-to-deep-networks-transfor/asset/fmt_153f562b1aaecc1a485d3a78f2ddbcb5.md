
## The algorithmic steps

1. **Pick the variable `x`, whose marginal `P(x)` will be computed.**
2. **Divide the tree into as many subtrees as the number of factor nodes to which the variable node `x` is connected.**
3. **For each one of these subtrees, identify the leaf nodes.**

```
$\sum\limits_{\mathbf{x}_{A} \in V_{A}}\psi_{A}(x_{1},\mathbf{x}_{A})\quad = \sum\limits_{x_{2}}\sum\limits_{x_{3}}\sum\limits_{x_{4}}f_{a}(x_{1},x_{2},x_{3},x_{4})\mu_{x_{2}\rightarrow f_{a}}(x_{2})\mu_{x_{3}\rightarrow f_{a}}(x_{3})\mu_{x_{4}\rightarrow f_{a}}(x_{4})\quad = \mu_{f_{a}\rightarrow x_{1}}(x_{1}).$
```

![Equation](images/B9780443292385000214/si299.png)(15.53)

Working similarly for the other two subtrees, `T[G]` and `T[H]`, we finally obtain

```
$P(x_{1}) = \frac{1}{Z}\mu_{f_{a}\rightarrow x_{1}}(x_{1})\mu_{f_{g}\rightarrow x_{1}}(x_{1})\mu_{f_{h}\rightarrow x_{1}}(x_{1}).$
```

![Equation](images/B9780443292385000214/si300.png)(15.54)

Note that each summation can be viewed as a step that “removes” a variable and produces a message. This is the reason that sometimes this procedure is called *variable elimination*. We are now ready to summarize the steps of the algorithm.
