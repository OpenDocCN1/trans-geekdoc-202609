
## 3.3 Linear regression

In statistics, the term *regression* was coined to define the task of modeling a *dependent* random variable `y`, in terms of a set of random variables `x[1]`, `x[2]`, …, `x[l]`. The former is considered to be the response (output) of a system, which is activated by the latter set of (input) random variables. The input variables will be represented as the components of an equivalent random vector **x**.^([⁶](#fn6))

```
y = θ[0] + θ[1]x[1] + ⋯ + θ[l]x[l] + η = θ[0] + θ^(T)x + η.
```

That is, the model is now linear with respect to the components `ϕ[k](x)`, `k = 1, 2`, of the two-dimensional image `ϕ(x)` of `x`. As a matter of fact, this simple trick is at the heart of a number of nonlinear methods that will be treated later on in the book. No doubt, the procedure can be generalized to any number of functions `ϕ[k](x)`, `k = 1, 2, …, K − 1`, and besides monomials, other types of nonlinear functions can be used, such as exponentials, splines, and wavelets. In spite of the nonlinear nature of the input–output dependence modeling, we still consider this model to be linear, because it retains its linearity with respect to the involved unknown parameters `θ[k]`, `k = 0, 1, …, K − 1` (`K` parameters in total). Although for the rest of the chapter we will adhere to linear functions, in order to keep our discussion simple, everything that will be said applies, also, to this type of nonlinear models, which are known as *generalized linear models*. All that is needed is to replace `x` with `ϕ(x) := [ϕ[1](x), …, ϕ[K−1](x)]^(T) ∈ ℝ^(K−1)`.

In the sequel, we will present two examples in order to demonstrate the use of parametric modeling. These examples are generic and can represent a wide class of problems.
