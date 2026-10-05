# CHAPTER 7 GLOBAL MODEL-AGNOSTIC METHODS

```
$\hat{f}(x) = \sum_{S\in{1..p\}} \hat{f}_S(x_S)$
```

In the formula, $x_s$ is the vector of features in the index set $S$. And each subset $S$ represents a functional component, for example a main effect if $S$ contains only one feature, or an interaction if $|S| > 1$.

How many components are in the above formula? The answer boils down to how many possible subsets $S$ of the features $1,...,p$ we can form. And these are $\sum_{i=0}^p \binom{p}{i} = 2^p$ possible subsets! If for use 10 components, we can define the decomposition into 1024 components: 1 intercept, 10 main effects, 92-way interaction terms, 720 3-way interaction terms, and with each additional feature, the number of components doubles. Clearly, for most functions, it is not feasible to compute all components. Another reason NOT to compute all is components with $|S| > 2$ are difficult to visualize and interpret.

# ## 7.4.3 How to Compute the Components II

So far I have avoided talking about how the components are defined and computed. The only constraints we have implicitly talked about were the number and dimensionality of the components, and that the sum of components should yield the original function. But without further constraints on what the components should be, they are not unique. This means we could shift effects between main effects and interactions, lower-order interactions (few features) and higher-order interactions (more features). In the example at the beginning of the chapter we could set both main effects to zero, and add their effects to the interaction effect.

Here is an more extreme example that illustrates the need for constraints on components. Suppose you have a 3-dimensional function. It does not really matter what this function looks like, but with the following decomposition will **always** work: $f_0$ is $0.12$, $	ilde{f}_1(x_1) = 2-x_1 +$ number of shoes you use. $f_2, f_3, f_{1,2}, f_{1,3}$ are all zero. To make this trick work, I define $	ilde{f}_{1,2,3}(x_1,x_2,x_3)=f(x)-\sum_{S\in{1..p}} \tilde{f}_S(x_S)$. So the interaction term containing all features simply sucks up all the remaining effects, which by definition always works, in the sense that the sum of all components gives us the original prediction. This decomposition would be very useful and misleading if you were to present this as the interpretation of your model.

The ambiguity can be avoided by specifying further constraints or specific methods for computing the components. In this chapter, we will discuss three methods that approach the functional decomposition in different ways:

+   * (Generalized) Functional ANOVA
* Accumulated Local Effects
* Statistical regression models