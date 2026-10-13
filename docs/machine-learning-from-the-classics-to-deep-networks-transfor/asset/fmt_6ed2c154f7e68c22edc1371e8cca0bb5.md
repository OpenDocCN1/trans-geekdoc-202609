
![Figure 11.13 The (0,1)-loss (dotted red), the hinge loss (full red), and the squared error (dotted black) functions tuned to pass through the (0,1) point for comparison. For the hinge loss, the value ρ = 1 was selected. Also, for the hinge and (0,1)-loss functions τ = yf(x), and for the squared error one, τ = y − f(x).](images/B9780443292385000172/gr013.jpg)

**Figure 11.13** The (0,1)-loss (dotted red), the hinge loss (full red), and the squared error (dotted black) functions tuned to pass through the (0,1) point for comparison. For the hinge loss, the value `ρ` = 1 was selected. Also, for the hinge and (0,1)-loss functions `τ` = `yf(x)`, and for the squared error one, `τ` = `y` − `f(x)`.

We will constrain ourselves to linear discriminant functions, residing in some RKHS, of the form

`f(x) = θ₀ + ⟨θ, ϕ(x)⟩`

where, by definition,

`ϕ(x) := κ(⋅, x)`

is the feature map. However, for the same reasons discussed in Section [11.8.1](#Chp011_519-582_B9780443292385000172.xhtml#s0080), we will cast the task as a linear one in the input space, `ℝˡ`, and at the final stage the kernel information will be “implanted” using the kernel trick.

The goal of designing a linear classifier now becomes equivalent to minimizing the cost

```
J(θ, θ₀) = ½‖θ‖² + C ∑ₙ₌₁ᴺ Lᵨ(yₙ, θᵀxₙ + θ₀)
```
(11.60)

Alternatively, employing slack variables, and following a similar reasoning as in Section [11.8.1](#Chp011_519-582_B9780443292385000172.xhtml#s0080), minimizing Eq. [(11.60)](#Chp011_519-582_B9780443292385000172.xhtml#deq143) becomes equivalent to

```
minimize with respect to θ, θ₀, ξ  J(θ, ξ) = ½‖θ‖² + C ∑ₙ₌₁ᴺ ξₙ
```
(11.61)

subject to `yₙ(θᵀxₙ + θ₀) ≥ ρ − ξₙ`
(11.62)
