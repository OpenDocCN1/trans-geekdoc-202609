![](bbox=[0.08, 0.09, 0.68, 0.33])

Fig. 1.17: The line integral is performed on a line passing through the backprojection point.

Let \( f(\vec{x}) = \delta(\vec{x} - \vec{x}_0) \). The point spread function of the projection/backprojection operator is

\( b(\vec{x}) = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} \frac{\delta\left(\vec{x} - \vec{x}_0 - \widehat{\vec{x}}\right)}{\|\widehat{\vec{x}}\|} d\widehat{\vec{x}} = \frac{1}{\|\vec{x} - \vec{x}_0\|} = \frac{1}{r}. \tag{1.37} \)

**Example 5:** Evaluate \( \int_{-\infty}^{\infty} \delta\left(e^{2(x-3)(x+4)} - 1\right) f(x) dx \).

_Solution_ Let

\( g(x) = e^{2(x-3)(x+4)} - 1. \tag{1.38} \)

Solving \( g(x) = e^{2(x-3)(x+4)} - 1 = 0 \), we obtain the zeros of \( g(x) \) as

\( \lambda_1 = 3 \text{ and } \lambda_2 = -4. \tag{1.39} \)

The derivative of \( g(x) \) is

\( g'(x) = 2[(x-3) + (x+4)]e^{2(x-3)(x+4)} = 2(2x+1)e^{2(x-3)(x+4)}. \tag{1.40} \)

Thus, at the two zeros of \( g(x) \), we have

\( g'(3) = 14 \text{ and } g'(-4) = -14. \tag{1.41} \)