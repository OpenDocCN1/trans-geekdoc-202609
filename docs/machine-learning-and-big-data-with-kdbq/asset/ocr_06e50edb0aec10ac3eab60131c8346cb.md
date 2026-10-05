# Basic Overview of Statistics

observed pairs of the variables disagree while 1 states for perfect agreement. The definition of the Somers’ D is based on the notion of concordance. We say that two pairs (x₁, y₁) and (x₂, y₂) are concordant if the ranks of both elements agree, i.e., x₁ > x₂ and y₁ > y₂ or, x₁ < x₂ and y₁ < y₂. If the ranks disagree, i.e. x₁ < x₂ and y₁ > y₂, or x₁ > x₂ and y₁ < y₂, we say that two pairs are discordant. If there is equality, x₁ = x₂ or y₁ = y₂, we say that such pairs are neither concordant nor discordant.

Let us arrange samples into pairs, i.e. if we denote pair (x₁, y₁), (x₂, y₂), ..., (xₙ, yₙ). Further, consider all possible pairs of pairs, i.e. (1, 2), (1, 3), ..., (N-1, N). There are N(N-1)/2 combinations. Denote the number of concordant pairs out of all pairs as N_C and the number of discordant pairs as N_D.

First, let us define Kendall’ τ rank correlation:

```
$$\tau(X, Y) = \frac{N_C - N_D}{N(N-1)/2}$$
```

Kendall’s τ is ∈ [-1, 1].

Meaning of τ(X,X) is a measure of pairs within X with unequal numbers. We can define Somers’ D(Y;X) as:

```
$D(Y;X) = \frac{\tau(X,Y)}{\tau(X,X)}$
```

where the definition says that D(Y;X) is the difference in the number of concordant and discordant pairs by the number of unequal pairs in X. The role of normalisation is for the case of mass points in the distribution of X. For a continuously distributed variable which does not have “δ” function in its distribution, Somers’ D and Kendall’s τ rank coincide. The difference between the two is mainly for discrete observations.

Kendall’s τ rank correlation is symmetric when Somers’ D is asymmetric due to the normalisation factor. This is apparent for the case when one of the variables has mass points while the other is continuously distributed. The distributions with mass points are a particular focus when Somers’ D is being used.

There is a further simplified formula for the case Y is discrete and X is binary. In such a case, Somers’ D can be expressed:

```
$D(Y;X) = \frac{N_C - N_D}{N_C + N_D + N_T}$
```

where N_T is the number of neither concordant nor discordant pairs with yᵢ = yⱼ while xᵢ ≠ xⱼ.

Somers’ D is used for regression where the dependent variable is binary or discrete while the independent variable can be of any type. Alternatively, Somers’ D can be used to evaluate the performance of classification models, i.e. to assign the degree of association between model and true values.