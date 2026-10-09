g(x + \mathbf{x\!d}) = 5 * (x + \mathbf{x\!d})^2 + 4 * (x + \mathbf{x\!d}) + 1 =
(5.67)

5 * (x^2 + 2 * x + \mathbf{x\!d} + (\mathbf{x\!d})^2) + 4 * x + 4 * (\mathbf{x\!d}) + 1
(5.68)

However by definition $\mathbf{(d \; \; ^{2})} = 0$ and therefore that term vanishes.
Rearranging the terms:

$$(5 * x^2 + 4 * x + 1) + (10 * x + 4)\mathbf{x\!d} \quad \quad \quad \quad \quad (5.69)$$

But since $g (x ) = (5 * x^{2} + 4 * x + 1)$ then:

$$g(x + \mathbf{x\!d}) = g(x) + g^{\prime}(x)\mathbf{x\!d} \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad (5.70)$$

+   3  Evaluating the function $g (x)$ at $x = 5$ using $DN$ we get:

$$
\begin{array}{l}
g(x = 4) = (5 * 5^{2} + 4 * 5 + 1) + (10 * 5 + 4)\mathbf{x\!d} = \\
\quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad 146 + (54)\mathbf{x\!d}
\end{array} 
\quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad (5.71)
$$

+   4  The code snippe t in 5.18 implements the function using Autograd .

```
```
1  import autograd.numpy as np
2  from autograd import grad
3  x = np. array([5.0], dtype=float)
4  def f1 (x):
5      return 5* x**2 + 4* x + 1
6  grad_f1 = grad(f1)
7  print (f1(x)) #> 146.0
8  print (grad_f1(x)) #> 54.0
```
```

![](bbox=[0.42, 0.64, 0.58, 0.67])

# ### 5.3.14 Forward mode AD