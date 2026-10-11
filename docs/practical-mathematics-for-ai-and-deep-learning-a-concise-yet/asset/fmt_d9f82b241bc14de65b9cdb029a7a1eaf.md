
**Figure 3.3:** *Theorems for continuous functions.* ***(Left)*** *Here `u` ∈ `(f(a), f(b))`. We found a point `c` ∈ `[a,b]` such that `f(c) = u`.* ***(Right)*** *`f(a) < 0` and `f(b) > 0` so we found a point `c` ∈ `[a, b]` such that `f(c) = 0`*

# Derivative of a function

Derivative of a function at a point represents the rate of change of the function at that point. The process of finding the derivative is called *differentiation*.

**Definition**: *Right-derivative* of a function `f` at `x_0` where `x_0` is a point in the domain of the function is defined as the rate at which the function changes in the right proximity of the point `x_0`. The *rate of change* is the ratio of the change in function value for a small change in the value of `x` towards the right side of `x_0` in the axis, say `x_0 + h`, where `h` (>0) is small. The rate of change is given by:

```
(f(x_0 + h) - f(x_0)) / h
```

This ratio represents the slope of the secant line, as shown in *[Figure 3.4](#c03.xhtml#fig3_4)*:

![](images/Figure-3.4.jpg)

**Figure 3.4:** *Derivatives and tangent*

As `h` becomes very small, this secant line tends to become a tangent line at `x_0`. The slope of this tangent line to the graph of the function at the point `(x_0, f(x_0))` is the right derivative of the function `f` at `x_0` and is formally written as:

```
f'_+(x_0) = lim_{h->0+} (f(x_0 + h) - f(x_0)) / h
```

Let’s call this `x_0 + h` as `x_0 + h` is in the right side of `x_0`. Similarly, we can define the left derivative `f'_-(x_0)` as:

```
f'_-(x_0) = lim_{h->0+} (f(x_0) - f(x_0 - h)) / h
```

for any point `x_0 - h` is the left side of `x_0` in the axis.

The *function f is differentiable* at `x_0` if and only if `f` has both a right-hand derivative and a left-hand derivative at `x_0`, and these derivatives are equal. This means the plot of the function is smooth in proximity of `x_0`, that is, if you take a very small segment of the function in the proximity of `x_0`, you can approximate it by a small line segment. That is the reason why differentiable functions are also called smooth functions. Now, if the function is differentiable, we can rewrite derivative as a symmetric difference quotient:

```
f'(x_0) = lim_{h->0} (f(x_0 + h) - f(x_0 - h)) / (2h)
```

**Example**: (Power function) The derivative of the power function `f(x) = x^n` can be calculated using the general derivative equation:

```
f'(x) = lim_{h->0} ((x+h)^n - x^n) / h
```
```
= n x^{n-1}
```

Using the definition of derivative, we can calculate the derivatives of most of the common mathematical functions like trigonometric, logarithmic, exponential. However, in practice, we will encounter many functions that are made up of sums, products, and composition of these functions, like `f(x) = log(2 + sin(x))`. To compute the derivative of such complicated functions, we use the following rules of derivatives:

1.  Derivative is linear operator:

    ```
    (a f(x) + b g(x))' = a f'(x) + b g'(x)
    ```

2.  Product rule of derivative:

    ```
    (f(x) g(x))' = f'(x) g(x) + f(x) g'(x)
    ```

3.  Chain rule of derivative (for function compositions):

    ```
    (f(g(x)))' = f'(g(x)) g'(x)
    ```

**Example**: The sigmoid function is defined as:

```
\sigma(x) = 1 / (1 + e^{-x})
```

Let `u = 1 + e^{-x}` and `y = 1/u`. Therefore, `\sigma(x) = y`. Applying chain rule:

```
d\sigma/dx = dy/du * du/dx = (-1/u^2) * (-e^{-x}) = e^{-x} / (1 + e^{-x})^2
```

Therefore, `\sigma'(x) = \sigma(x) (1 - \sigma(x))`

**Example**: The *tanh* function is defined as:

```
\tanh(x) = (e^x - e^{-x}) / (e^x + e^{-x})
```

Applying product rule and chain rule of derivatives the derivative of tanh can be found as follows:

```
\tanh'(x) = 1 - \tanh^2(x)
```
```
= \text{sech}^2(x)
```

These derivatives are computed for any arbitrary point in the domain of `f`, and we can visualize their plots in *[Figure 3.5](#c03.xhtml#fig3_5)*:

![](images/Figure-3.5.jpg)

**Figure 3.5:** *Derivatives as a function*

Next, we state few useful theorems for differentiable functions.

**Theorem**: A differentiable function is continuous but not conversely.

**Example**: Let `f(x) = |x|`. At `x=0`, Also, `f` is continuous at `x=0`

```
f'_+(0) = 1 and f'_-(0) = -1
```

As `f'_+(0) != f'_-(0)`, f is not differentiable at `x=0`. Differentiability implies smoothness. At `x=0`, there is a sharp corner in the `|x|` plot. Change of direction by 90 degrees. Hence, geometrically, we can see the non-differentiability of `|x|` at 0, so the continuity of a function does not always guarantee differentiability.

**Mean value theorem (Lagrange)**: Let `f` be continuous on `[a, b]` and differentiable at every point in `(a, b)`. Then, there exists at least one point `c \in (a, b)` such that:

```
f'(c) = (f(b) - f(a)) / (b - a)
```

**Rolle’s theorem:** Let `f` be continuous on `[a, b]` and differentiable at every point in `(a, b)`. If `f(a) = f(b)` then, there exists at least one point `c \in (a, b)` such that `f'(c) = 0`.

*[Figure 3.6](#c03.xhtml#fig3_6)* depicts these two theorems pictorially:

![](images/Figure-3.6.jpg)

**Figure 3.6:** ***Theorems on derivative:(Left)*** *The slope of the secant line from f(a)to f(b) is given by `(f(b) - f(a)) / (b - a)` and the tangent at `c` is parallel to this secant line.* ***(Right)*** *As f(a)=f(b) the function must turn at some point and at that point, the derivative is 0.*

# Higher Order derivatives

The derivative of a function `f` is itself a function. We represent it by `f'(x)`. Let `f(x) = x^3`. Then, `f'(x) = 3x^2`. So, we can compute the derivative of the derivative function:

```
f''(x) = 6x
```

This is called the *second order derivative*. Hence, for this function, we have `f'''(x) = 6`. Derivative function can be computed any number of times to obtain *n^(th)* order derivative. This is depicted with the following notation:

```
f^{(n)}(x)
```

Refer to the following figure:

![](images/Figure-3.7.jpg)

**Figure 3.7:** *Higher order derivatives*

There are many applications of higher order derivatives like approximating functions and finding maximum or minimum values attained by a bounded function. We will briefly look at the Taylor series expansion of a function using higher order derivatives.

# Taylor series expansion

If a real valued function satisfies the following conditions:

*   The function should be differentiable any number of times
*   The function should be defined at the given point a

Then,

```
f(x) = f(a) + f'(a)(x-a) + f''(a)(x-a)^2/2! + f'''(a)(x-a)^3/3! + ...
```

This is called the *Taylor series expansion* of the function `f` at the point `a`. It’s an infinite series, that is, the number of terms in this series is infinite and is represented more formally with summation notation, as follows:

```
f(x) = \sum_{n=0}^{\infty} f^{(n)}(a) (x-a)^n / n!
```

Now, if we take `x` sufficiently close to the point `a`, then the higher degree terms of the polynomial `(x-a)^n` for `n > 2` become negligibly small and can be ignored.

In general, for any point `x`, we can approximate `f(x)` using a finite number of terms. Suppose `f` is differentiable `n` times in the neighbourhood of `a`; we can consider the Taylor polynomial with `n` terms only. There will be an error in this approximation proportional to the distance of `x` from `a` and is given by `R_n(x) = f^{(n+1)}(c) (x-a)^{n+1} / (n+1)!`, where `c` is some point between `a` and `x`. This is called *Lagrange form of remainder*. The second order Taylor’s polynomial with Lagrange form of remainder is given by:

```
f(x) = f(a) + f'(a)(x-a) + f''(c)(x-a)^2 / 2
```

**Example**: `f(x) = e^x` and let `a = 0`. For `x` in neighborhood of 0:

```
e^x = 1 + x + x^2/2! + x^3/3! + ...
```

Or `e^x \approx 1 + x + x^2/2`
