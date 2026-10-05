# Differential Calculus

Example 3:

```
$h(x) = \ln(1+e^{2x})$$
$$h'(x) = \frac{1}{1+e^{2x}} \frac{d}{dx}(1+e^{2x})$$
$$h'(x) = \frac{e^{2x}}{1+e^{2x}} \frac{d}{dx}(2x)$$
$$h'(x) = \frac{2e^{2x}}{1+e^{2x}}$
```

There are several additional derivative rules for various functions, such as the trigonometric functions. They are out of scope for the purposes of this book.

# Partial Derivative

Most-world problems use functions of several variables. It is valuable to measure function sensitivity to small changes in the inputs. In finance, the risk of a stock will depend on variables like broad stock market performance (e.g., the S&P 500) and interest rates. A risk manager will be interested in the expected change to the stock price when these variables change by some small quantity.

When we consider a function more than one variable, say $z=f(x,y)=2x+xy+3y$, we can take the derivative with respect to each variable holding the others constant. These derivatives are called *partial derivatives*, and they represent tangent lines in particar directions. The partial derivative notation is slightly different from the single-variable derivative. Let's compute the partial derivative of $z$:

```
$$\frac{\partial z}{\partial x} = 2+y$$
$$$\frac{\partial z}{\partial y} = x+3$$
```

Second-order partial derivatives are computed similarly and denoted

```
$$\frac{\partial^2 z}{\partial x^2}, \frac{\partial^2 z}{\partial x\partial y}, \frac{\partial^2 z}{\partial y^2}$
```

Higher-order derivatives follow analogous notation.
The *gradient* is an important object which holds the partial derivatives of a function at a point. For example, here is the gradient of $z:

```
$$\nabla z(x,y) = \left(\frac{\partial z}{\partial x}(x,y), \frac{\partial z}{\partial y}(x,y)\right)$$$
$\nabla z(x,y) = (2+y, x+3)$
```