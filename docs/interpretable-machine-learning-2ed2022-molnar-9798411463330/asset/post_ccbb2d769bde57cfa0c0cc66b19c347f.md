
# CHAPTER 7 GLOBAL MODEL-AGNOSTIC METHODS

```
$\hat{f}(x) = \sum_{S\in{1..p\}} \hat{f}_S(x_S)$
```

In the formula, $x_s$ is the vector of features in the index set $S$. And each subset $S$ represents a functional component, for example a main effect if $S$ contains only one feature, or an interaction if $|S| > 1$.

How many components are in the above formula? The answer boils down to how many possible subsets $S$ of the features $1,...,p$ we can form. And these are $\sum_{i=0}^p \binom{p}{i} = 2^p$ possible subsets! If for use 10 components, we can define the decomposition into 1024 components: 1 intercept, 10 main effects, 92-way interaction terms, 720 3-way interaction terms, and with each additional feature, the number of components doubles. Clearly, for most functions, it is not feasible to compute all components. Another reason NOT to compute all is components with $|S| > 2$ are difficult to visualize and interpret.

## 7.4.3 How to Compute the Components II

So far I have avoided talking about how the components are defined and computed. The only constraints we have implicitly talked about were the number and dimensionality of the components, and that the sum of components should yield the original function. But without further constraints on what the components should be, they are not unique. This means we could shift effects between main effects and interactions, lower-order interactions (few features) and higher-order interactions (more features). In the example at the beginning of the chapter we could set both main effects to zero, and add their effects to the interaction effect.

Here is an more extreme example that illustrates the need for constraints on components. Suppose you have a 3-dimensional function. It does not really matter what this function looks like, but with the following decomposition will **always** work: $f_0$ is $0.12$, $\tilde{f}_1(x_1) = 2-x_1 +$ number of shoes you use. $f_2, f_3, f_{1,2}, f_{1,3}$ are all zero. To make this trick work, I define $\tilde{f}_{1,2,3}(x_1,x_2,x_3)=f(x)-\sum_{S\in{1..p}} \tilde{f}_S(x_S)$. So the interaction term containing all features simply sucks up all the remaining effects, which by definition always works, in the sense that the sum of all components gives us the original prediction. This decomposition would be very useful and misleading if you were to present this as the interpretation of your model.

The ambiguity can be avoided by specifying further constraints or specific methods for computing the components. In this chapter, we will discuss three methods that approach the functional decomposition in different ways:

- (Generalized) Functional ANOVA
- Accumulated Local Effects
- Statistical regression models

## 7.4 Functional Decomposition

## 7.4.4 Functional ANOVA

Functional ANOVA was proposed by Hooker (2004)$^{19}$. A requirement for this approach is that the prediction function $\hat{f}$ is square integrable. With any functional decomposition, the functional ANOVA decomposes the function into components:

```
\hat{f}(x) = \sum_{S\subseteq\{1,...,p\}} \hat{f}_S(x_S)
```

Hooker (2004) defines each component with the following formula:

```
\hat{f}_S(x) = \int_{X_{-S}} \left(\hat{f}(x) - \sum_{V\subseteq S} \hat{f}_V(x)\right) dX_{-S}
```

Okay, let us take this thing apart. We can rewrite the component as:

```
\tilde{f}_S(x) = \int_{X_{-S}} (\hat{f}(x)) dX_{-S} - \int_{X_{-S}} \left(\sum_{V\subseteq S} \hat{f}_V(x)\right) dX_{-S}
```

On the left side is the integral over the prediction function with respect to the features excluded from the set $S$, denoted with $-S$. For example, if we compute the 2-way interaction component for 2 and 3, we would integrate over features 1. The integral can also be viewed as the expected value of the prediction function with respect to $X_{-S}$, assuming that all features follow a uniform distribution from their minimum to their maximum. From this interval, we subtract all components with subsets $S$. This subtraction removes the effect of all lower-order effects and centers the effect. For $S=\{1,2\}$, we subtract the effects of both $f_1$ and $f_2$, as well as the intercept $f_0$. The occurrence of these lower-order effects makes the formula recursive: we have to go through subsets to the intercept and compute all components. For the intercept $f_0$, the subset is the empty $\emptyset$ and therefore $-S$ contains all features:

```
\hat{f}_0(x) = \int_{X} \hat{f}(x)dX
```

This is simply the prediction function integrated over all features. Now that $f_0$, we can compute $f_1$ (and equivalently $f_2$):

```
\hat{f}_1(x) = \int_{X_{-S}} (\hat{f}(x) - \hat{f}_0) dX_{-S}
```

> 19 Hooker, Giles. "Discovering additive structure in black box functions." Proceedings of the tenth ACM SIGKDD international conference on Knowledge discovery and data mining (2004).

To finish the calculation for the component $\hat{f}_{1,2}$, we can put everything together:

$$\hat{f}_{1,2}(x) = \int_{X_{3,4}}(\hat{f}(x) - \hat{f}_0(x) - \hat{f}_1(x) - \hat{f}_2(x)) dX_{3,4}$$

This example shows how higher-order effect is defined by integrating over other features, but also by removing all the lower-order effects that subsets of the feature set we are interested in. Hooker (2004) has shown that this definition of functional components satisfies these desirable axioms:

- Zero Means: $\int \hat{f}_S(x)dX = 0$ for each $S \neq \emptyset$.
- Orthogonality: $\int \hat{f}_S(x)\hat{f}_V(x)dX = 0$ for $S \neq V$
- Variance Decomposition: $\int \hat{f}(x)^2 dX$, $\sigma^2(\hat{f}) = \sum_{S \subseteq \{1,\dots,p\}} \sigma_S^2(\hat{f}_S)$

The means axiom implies that all effects or interactions are centered around area. As a consequence, an interpretation at a point $x$ is relative to the center prediction and not the absolute prediction.

The orthogonality axiom implies components do not share information. For example, the first-order effect of feature $X_1$ and the interaction term of $X_1$ and $X_2$ are not correlated. Because of orthogonality, all components are “pure” in the sense that they do not mix effects. It makes a lot of sense that the component for, say, feature $X_4$ should be independent of the interaction term between features $X_1$ and $X_2$. The more interesting consequence arises for orthogonality of hierarchical components, where one component contains features of another, the main effect of feature. In contrast, a two-dimensional partial dependence plot for $X_1$ and $X_2$ would contain four effects: the intercept, the two main effects of $X_1$ and $X_2$ and the interaction between them. The functional ANOVA component for $\hat{f}_{1,2}(x_1,x_2)$ contains only the pure interaction.

Variance decomposition allows us to divide the variance of the function $\hat{f}$ among the components, and guarantees that it adds up the total variance of the function in the end. The variance decomposition property can also explain why the method is called “functional ANOVA”. In statistics, ANOVA stands for Analysis Of Variance. ANOVA refers to a collection of methods that analyze differences in the mean of a target variable. ANOVA works by dividing the variance and attributing it to the variables. Functional ANOVA can therefore be seen as an extension to any function.

Problems arise with the functional ANOVA when features are correlated. As a solution, the generalized functional ANOVA has been proposed.

## 7.4.5 Generalized Functional ANOVA for Dependent Features

Similar to most interpretation techniques based on sampling data (such as the PDP), the functional ANOVA can produce misleading results when features are correlated. If we integrate over the uniform distribution, when reality features are dependent, we create a new dataset that deviates from the joint distribution and extrapolates to unlikely combinations of feature values.

Hooker (2007) $20$ proposed the generalized functional ANOVA, a decomposition that works for dependent features. It is a generalization of the functional ANOVA we encountered earlier, which means the functional ANOVA is a special case of the generalized functional ANOVA. The components are defined as projections of onto the space of adaptive functions:

```
$\hat{f}_S(x_S) = \text{argmin}_{g_S \in L^2(\mathbb{R}^S), S \subset P} \int \left( \hat{f}(x) - \sum_{S \subset P} g_S(x_S) \right)^2 w(x)dx.$
```

Instead of orthogonality, the components satisfy a hierarchical orthogonality condition:

```
$\hat{f}_S(x_S) | S \subset U : \int \hat{f}_S(x_S)\hat{f}_U(x_U)w(x)dx = 0$
```

Hierarchical orthogonality differs from orthogonality. For two feature sets S and U, neither of which is the subset of the other (e.g. $S=\{1,2\}$ and $U=\{2,3\}$), the components $\hat{f}_S$ and $\hat{f}_U$ are not orthogonal for the decomposition to be hierarchically orthogonal. All components for all subsets of S must be orthogonal to $\hat{f}_S$.

> $20$ Hooker, Giles. "Generalized functional ANOVA diagnostics for high-dimensional functions of dependent variables." Journal of Computational and Graphical Statistics 16.3 (2007): 709-732.
