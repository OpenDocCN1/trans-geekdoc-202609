
For example, `g(x) = -x`, `f(x) = e^x`, then `f ∘ g(x) = f(g(x)) = e^(-x)`. Another example is `g(x) = e^x`, `f(x) = x²`, then `f ∘ g(x) = f(g(x)) = (e^x)²`. The calculation code of the composite function is as follows:

```
y = np.exp(x)**2
```

The function curve of `e^(-x)`, `e^(x²)` is shown in the figure:

![](EPUB/media/file223.png)

Figure 1-23 Curves of functions `e^(-x)` and `e^(x²)`

The sigmoid function $\sigma(x) = \frac{1}{1 + e^{-x}}$ is one of the commonly used functions in machine learning (deep learning). It can be regarded as the quotient of two constant functions 1 and the function `1 + e^(-x)`. The function `1 + e^(-x)` can be regarded as the sum of the constant function 1 and the function `e^(-x)`. The function `e^(-x)` can be regarded as a composite function of functions `e^z` and `z = -x`. `-x` can be regarded as the product of the constant function -1 and x. The process of constructing this complex function from simple elementary functions through four arithmetic and compound operations is shown in Figure 1-24:

![](EPUB/media/file224.png)

Figure 1-24 The composite process of sigmoid function $\sigma(x) = \frac{1}{1 + e^{-x}}$

The following code plots the `σ(x)` function curve:

```
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline

x = np.arange(-7, 7, 0.1)
y = 1 / (1 + np.exp(-x))
plt.plot(x, y)

plt.legend(['\frac{1}{1+e^{-x}}'])
plt.xlabel('x')
plt.ylabel('y')
plt.show()
```

![](EPUB/media/file16.png "fig:")

Figure 1-25 The curve of the function `σ(x)`

It can be seen that the value of the function is in the `[0,1]` interval, and the function value `f(x)` increases with the increase of `x`, that is, the function is **increasing**. If there must be `f(x[1]) < f(x[2])` for any two numbers `x[1] < x[2]` in a certain interval I of the independent variable, it is said that the function is strictly increasing. Likewise, the function decrement can be similarly defined.

The value of the `σ(x)` function at `x = 0` is $\frac{1}{1 + e^{-x}} = 1/2 = 0.5$. When `x` tends to positive infinity, that is, `x → ∞`, `e^(-x)` is close to 0, that is, `e^(-x) → 0`, so $\frac{1}{1 + e^{-x}}$ is close to `1/(1 + 0) = 1`. Conversely, when `x → -∞`, `e^(-x) → ∞`, so $\frac{1}{1 + e^{-x}}$ is close to `1/(1 + ∞) = 0`. In order to describe the behavior of a variable tending to a certain quantity, such as `x` tending to 0 or infinity, people put forward the concept of limit.

### 1.3.3 Limits, derivatives

#### 1. The limit of the sequence

The sequence is a sequence of ordered numbers, such as `(1, 2, 3, 4)`, `(1, 1/2, 1/3, ⋯, 1/n, ⋯)`. The element format in the sequence is called **Number of Items**. A finite number of items is called a finite sequence, and an infinite number of items is called an infinite sequence. A sequence is also a function, which is a mapping from a subset of natural numbers to a set of values, that is, its independent variable is a natural number, and its dependent variable is a value. Usually, a sequence refers to an infinite sequence, which can be written as:

`a[1], a[2], a[3], ⋯, a[n], ⋯`

The limit describes an infinite approximation, such as an infinite sequence `{1, 1/2, 1/3, ⋯, 1/n, ⋯}`. When `n` continues to increase, the corresponding number of the sequence such as `1/n` will become smaller and smaller, getting closer and closer to the value 0, that is, infinitely approaching 0 or this sequence will gradually converge to 0 as `n` increases infinitely. This 0 is called the **limit** of this sequence. The so-called infinite approximation means that as long as `n` is sufficiently large, the distance between `1/n` and its limit value 0 is sufficiently small. In other words, for an arbitrarily small number such as `ϵ = 0.001`, an `n` can always be found so that the distance between all numbers in the sequence after the `n`th item and the limit is smaller than this `ϵ`. For example, after `n=1000` items, `|1/n - 0| < ϵ`.

For another example, it can be proved that the limit of the sequence `{3 - 1, 3 - 1/2, 3 - 1/3, ⋯, 3 - 1/n, ⋯}` is 3.

Usually, the notation `lim` represents the limit:

$\lim\limits_{n \rightarrow \infty}{1/n} = 0$

This formula represents the number sequence on the left. When `n` tends to infinity (`n → ∞`), its limit value is 0.

A sequence may not have a limit; if there is a limit, then the limit must be unique.

#### 2. Limit and continuity of function

Similarly, the limit $\lim\limits_{x \rightarrow x_{0}}f(x)$ of the function `f(x)` at a certain point `x[0]` can be defined, which means that when `x` is sufficiently close to `x[0]`, `f(x)` will be sufficiently close to this limit. For example:

$\lim\limits_{x \rightarrow 3}x^{2} = 9$

It means that when the independent variable `x` is sufficiently close to 3, the value of the dependent variable `f(x)` will be sufficiently close to 9, that is, the limit of `f(x)` is 9. For example, there is a set of independent variable sequence `{3 - 1, 3 - 1/2, 3 - 1/3, ⋯}` that is close to 3, and the `f(x)` value sequence `{(3 - 1)², (3 - 1/2)², (3 - 1/3)², ⋯}` is 9.

If the limit value of the function at `x[0]` exists and is equal to the function value at `x[0]`, i.e., $\lim\limits_{x \rightarrow x_{0}}f(x) = f(x_{0})$, then the function is said to be **continuous** at this point `x[0]`. Intuitively speaking, the curve corresponding to `f(x)` is not broken at `x[0]`.

As shown in Figure 1-26, `f(x) = x²` is continuous at any independent variable `x`, which means that the function curve is continuous without disconnection, so the whole function is **continuous**. The function `f(x) = |x|` is also continuous everywhere. And `f(x) = sign(x)` defined below is discontinuous at `x = 0`.

$f(x) = \text{sign}(x) = \left\{ \begin{matrix} {1,} & {x > 0} \\ {0,} & {x==0} \\ {-1,} & {x < 0} \\ \end{matrix} \right.$

![](EPUB/media/file225.png)

Figure 1-26 Curves of function `x²`, `|x|`, `sign(x)`

Let `Δx[0] = x - x[0]`, `Δf(x[0]) = f(x) - f(x[0])`, then $\lim\limits_{x \rightarrow x_{0}}f(x) = f(x_{0})$ can be expressed as: $\lim\limits_{\Delta x_{0} \rightarrow 0}\Delta f(x_{0}) = 0$. The continuous meaning of the function in the independent variable `x[0]` is that when `Δx[0]` tends to 0, `Δf(x[0])` also tends to 0. That is, `Δf(x[0])` tends to 0 as `Δx[0]` tends to 0.

#### 3. Derivatives of functions

The continuity of the function `y = f(x)` at a certain point `x` refers to whether the dependent variable `y = f(x)` changes continuously with the continuous transformation of the independent variable near this point. Sometimes it is necessary to further examine how quickly the dependent variable changes with the independent variable. For example, `t` is used to represent time, and `s` is used to represent the distance traveled by a moving object. Obviously, `s` changes continuously with `t`, and it will not suddenly jump from a certain point to another at a certain moment point. For moving objects, sometimes we are more concerned about the speed of the object's movement, that is, the speed of the movement. The average movement speed during this period can be expressed by the distance traveled in the same point of time, such as from time `t[0]` to time `t[0] + Δt`, the distance traveled in this time period `t[0] + Δt - t[0]` is `s(t[0] + Δt) - s(t[0])`, and their ratio represents the average movement speed during this period:

$\frac{s(t_{0} + \Delta t) - s(t_{0})}{t_{0} + \Delta t - t_{0}} = \frac{s(t_{0} + \Delta t) - s(t_{0})}{\Delta t}$
