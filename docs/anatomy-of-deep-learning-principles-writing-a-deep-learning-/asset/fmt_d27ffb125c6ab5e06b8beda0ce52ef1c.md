
Then the dot product of gradient vector and increment vector can be written in the form of matrix product:

`f(xx + Δ) − f(xx) ≃ ∇f(xx)Δx = Δxx^(T)∇ff(xx)^(T)`

If the gradient is also written as a column vector, the dot product of the gradient vector and the increment vector can be written as a matrix product:

`f(xx + Δ) − f(xx) ≃ ∇f(xx)^(T)Δx = Δxx^(T)∇ff(xx)`

If the independent variable is written in the form of a row vector, and the gradient is written in the form of a column vector, that is:

`xx = (x[1], x[2], ⋯, x[n])`

`Δxx = (Δx[1], Δx[2], ⋯, Δx[n])`

```
∇f f(x x) = (∂f/∂x_1, ∂f/∂x_2, ⋯, ∂f/∂x_n)^T
```

but:

`f(xx + Δ) − f(xx) ≃ Δxx∇f(xx)`

If the gradient `∇[x]ff(xx)`, `f(xx)`, `xx` are all written in row vector form, then:

`f(xx + Δ) − f(xx) ≃ ∇f(xx)Δx^(T) = Δxx∇ff(xx)^(T)`

For a multivariate function `f(xx)`, if the independent variable `xx` is written in the form of a matrix, then `f(xx)` is about `xx` The gradient of , although it is a vector, is sometimes written in the form of a matrix with the same shape as `xx`, so it is easy to know which partial derivative corresponds to which variable, namely:

```
f'(x x) = dy/dx x = [ ∂y/∂x_11  ∂y/∂x_21  ⋯  ∂y/∂x_n1
                      ∂y/∂x_12  ∂y/∂x_22  ⋯  ∂y/∂x_n2
                      ⋮          ⋮          ⋱  ⋮
                      ∂y/∂x_1n  ∂y/∂x_2n  ⋯  ∂y/∂x_nn ]
```

Whether you write gradients, independent variables, and dependent variables as row vectors, column vectors, or matrices depends entirely on which form is more helpful for you to derive related formulas. If `xx` is written in matrix form and the gradient is written in matrix form, it looks more consistent.

### Example 1

For the multivariate function `F(x, y, z) = x + 2y² + 3z³`, there are:

`∇F(x, y, z) = (1, 4y, 9z²)`

The gradient at a specific point (2,3,4) is `(1, 4 * 3, 9 * 4²) = (1, 12, 144)`. Around this point if the independent variable has a small increment `(Δx, Δy, Δz)`, then:

`F(2 + Δx, 3 + Δy, 4 + Δz) − F(2, 3, 4) ≃ 1 * Δx + 12 * Δy + 144 * Δz`

### Example 2

Suppose `y = w[1] * x[1] + w[2] * x[2] + ⋯ + w[n] * x[n] + b`, if `y` is regarded as a function of `w = (w[1], w[2], …, w[n])`, Then `dy/dw = (x_1, x_2, ..., x_n)`; if `y` is regarded as a function of `x = (x[1], x[2], …, x[n])`, then `dy/dx = (w[1], w[2], …, w[n])`; if `y` is regarded as a function of `b`, then `dy/db = 1`.

If `ww` is written as a column vector and `xx` is written as a row vector, then `y = xxww`, if the gradient is written as a row vector, then `∂y/∂xx = ww^T`, `∂y/∂ww = xx`.

If `ww` and `xx` are written in the form of column vectors, and the gradient is written in the form of row vectors, then `y = ww^(T)xx = xx^(T)ww`, then `∂y/∂xx = ww^T`, `∂y/∂ww = xx^T`.

It can be proved that the four algorithms of derivatives and the chain rule are also true for gradients. Let f, g be two real-valued functions from ℝ^(n) to ℝ, then:

#### Linear rule

`(αf + βg)'(x) = ∇(αf + βg)(x) = αf'(x) + βg'(x) = α∇f + β∇g(x)`

#### Product rule

`(fg)'(x) = ∇(fg)(x) = f'(x)g(x) + f(x)g'(x) = g(x)∇f(x) + f∇g(x)`

#### Chain rule

Let g be a real-valued function from ℝ^(n) to ℝ and f be a real-valued function from ℝ to ℝ , for some `xx ∈ ℝ^(n)`, the value of `g(xx)` is `z`, if `xx` is a column vector and the gradient is in the form of a row vector, Then there are:

`(f ∘ g)'(xx) = ∇(f ∘ g)(xx) = f'(z)g'(xx) = f'(z)∇g(xx)`

If `xx` is a row vector and the gradient is in column vector form, then:

`(f ∘ g)'(xx) = ∇(f ∘ g)(xx) = g'(xx)f'(z) = ∇g(xx)f'(z)`

That is, the order of the two different forms of the chain rule is exactly the opposite.

### Example 3

If `g((x_1, x_2)^T) = 3x_1 + 2x_2^3`, `f(z) = z²`, then `(f ∘ g)((x_1, x_2)^T) = (3x_1 + 2x_2^3)^2`. So:

`(f ∘ g)'(xx) = f'(z)∇g(x) = 2z * (3, 6x[2]²) = 2 * (3x[1] + 2x[2]³) * (3, 6x[2]²) = (18x[1] + 12x[2]³, 36x[1]x[2]² + 24x[2]⁵)`

If the variable is a row vector and the gradient is a column vector, `g(x[1], x[2]) = 3x[1] + 2x[2]³`, `f(z) = z²`, then `(f ∘ g)(x[1], x[2]) = (3x[1] + 2x[2]³)²`. So:

```
(f ∘ g)'(x x) = ∇g(x)f'(z) = [ 3
                                 6x_2^2 ] 2z = [ 3
                                                  6x_2^2 ] 2 * (3x_1 + 2x_2^3) = [ 18x_1 + 12x_2^3
                                                                                     36x_1x_2^2 + 24x_2^5 ]
```

### Example 4

Suppose `y`, `ŷ` are 2 vectors in ℝ^(n), you can use the square of their Euclidean distance to define these 2 vectors The error (distance) between, such as using the following formula to express the error `E(y, ŷ)` between two vectors:

```
E(y y, ŷ ŷ) = 1/2 ||y y - ŷ ŷ||_2^2 = 1/2((y_1 - ŷ_1)^2 + (y_2 - ŷ_2)^2 + ⋯ + (y_n - ŷ_n)^2)
```

The gradient of `E(y y, ŷ ŷ)` with respect to `yy` is `(y y - ŷ ŷ)^T`.

### 1.3.7 Derivative of vector-valued function and Jacobian matrix

If there are multiple functions:

```
f_1: x → f_1(x)
f_2: x → f_2(x)
⋮
f_m: x → f_m(x)
```

Then they can be written together in a column vector:

```
f f(x) = [ f_1(x)
           f_2(x)
           ⋮
           f_m(x) ]
```

These combined functions are called **vector-valued functions**. Input a `x`, each function produces a function value `f[i](x)`, these function values constitute the vector on the right side above.

For example, there are 3 functions: `f[1](x) = x²`, `f[2](x) = e^x`, `f[3](x) = ax`, then they constitute a vector-valued function:

```
f f(x) = [ f_1(x)
           f_2(x)
           f_3(x) ] = [ x^2
                        e^x
                        ax ]
```

Enter a value of `x` such as 3, and generate 3 values: `[ 9, e^3, 3a ]^T`

The vector-valued function composed of m univariate functions is a mapping (transformation) of a real number set ℝ to ℝ^(m) `ff(x) : ℝ → ℝ^(m)`. If at a certain point `x`, the derivatives of each function `f[i](x)` with respect to `x` exist, these derivatives are accumulated into a vector, which is called the derivative of the vector-valued function with respect to the independent variable `x`, which can be written as `Dff(x)`:
