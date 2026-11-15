| Mode | Empty reservoir | | |
|---|---|---|---|
| | Tan and Chopra [17] | Salajegeh et al. [12] | Present work |
| 1 | 4.27 | 4.29 | 4.30 |
| 2 | – | – | 4.58 |
| 3 | – | 6.71 | 6.67 |

# ## 10.4 Arch Dam Optimization

# ### 10.4.1 Mathematical Model and Optimization Variables

In the optimization process, the goal is to minimize the cost of arch dam while satisfying multiple constraints on natural frequencies. The optimization problem can be stated mathematically as follows:

```
Find: X = [x₁, x₂, ..., xₙ]
To minimize: w(X)
Subject to: gᵢ(X) ≤ 0, i = 1, ..., m
Xˡ ≤ X ≤ Xᵘ
```

where X is the vector containing the design variables with n unknowns, w(X) represents the objective function that should be minimized, and gⱼ is the jth constraint from m inequality constraints. Also, in the above equation Xˡ and Xᵘ denote the lower and upper bounds of the design variable vector, respectively.

# ### 10.4.2 Design Variables

The most effective parameters for creating the arch-dam geometry were mentioned in Sect. 10.2. These parameters can be adopted as design variables:

```
X^T = { s β tc₁ ... tcₙ₊₁ rₐ₁ ... rₐₙ₊₁ r_d₁ ... r_dₙ₊₁ }
```

in which the X^T vector may have 3n + 5 components involving shape parameters of the arch dam.