
# Maxima and Minima in Machine Learning

In ML, maxima and minima are essential for optimization, determining where a function (e.g., loss or objective function) is at its peak.

For nonlinear functions, the highest peak or the maximum value refers to the `maxima`, and the lowest peak or the lowest value refers to the `minima`. Put differently, the point `x` at which the derivative of a function is 0 is defined as the maxima or the minima.

Maxima and minima are the points where the value of the function remains constant: i.e., the change rate is 0.

The concepts of maxima and minima can be global or local, to indicate whether the peak applies to the entire domain of the function (global) or only to a specific neighborhood around a point (local).

More formally, a function `f(x)` has a local minima at `x = a` if there exists an interval `(a - h, a + h)`, where `h > 0`, such that `f(a) ≤ f(x)` for all `x` in that interval.

[Figure A.8](#a02.xhtml#c0-fig-8) visually illustrates these concepts, assuming the function is limited to a domain of positive real numbers `x > 0`.

![FIGURE A.8 Maxima and minima visualizations, for Bold italic x greater than 0. (Bold italic f of bold italic x equals bold italic e to the power of minus bold italic x, multiplied by sine of 3 bold italic x).](images/cappf008.png)

[FIGURE A.8](#a02.xhtml#rc0-fig-8) Maxima and minima visualizations, for `x > 0` (`f(x) = e^(-x) * sin(3x)`).

## Partial Derivatives

In multivariable calculus, a `partial derivative` measures the rate of change of a function with respect to one variable, while keeping all other variables constant. This is essential in ML for optimizing functions involving multiple parameters, like loss functions.

More formally, for a multivariable function `f(x₁, ..., xₙ)`,

```
∂f/∂xᵢ = lim(Δxᵢ→0) [f(x₁, x₂, ..., xᵢ + Δxᵢ, ..., xₙ) - f(x₁, x₂, ..., xᵢ, ..., xₙ)] / Δxᵢ
```

For example, for `f(x₁, x₂) = x₁² + x₂²`,

```
∂f/∂x₁ = 2x₁,  ∂f/∂x₂ = 2x₂
```

Partial derivatives form the components of the gradient, which is key in optimization.

## Gradient

The `gradient` of a function is a vector containing all its partial derivatives. It points in the direction of the steepest ascent of the function.

More formally, for a multivariable function `f(x₁, ..., xₙ)`,
