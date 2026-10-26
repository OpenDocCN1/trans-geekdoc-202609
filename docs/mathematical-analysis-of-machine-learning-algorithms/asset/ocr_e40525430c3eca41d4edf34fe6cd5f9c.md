of such functions. More generally, we may consider approximate ERM, which returns $\hat{f}$, so that

$$\widehat{\operatorname{err}}_{S_n}(\hat{f}) \leq \epsilon' \tag{3.1}$$

for some accuracy $\epsilon' > 0$.

Next we show that by using union bound and Hoeffding’s inequality, we can obtain a sample complexity bound for PAC learning analysis.

# ### 3.2 Analysis of PAC Learning

In the analysis of the ERM learner, we are interested in bounding the difference of the test error $\operatorname{err}_D(\hat{f})$ and the optimal test error $\operatorname{err}_D(f_*)$, using a decomposition. Note that although, in the realizable PAC learning setting, $\operatorname{err}_D(f_*) = 0$, in the more general case considered in later sections, the optimal test error may be nonzero. The following decomposition can be applied both to the realizable PAC learning setting and the more general situation where $\operatorname{err}_D(f_*) \neq 0$.

$$\begin{aligned}
\operatorname{err}_D(\hat{f})-\operatorname{err}_D(f_*)
&= \underbrace{\left[\operatorname{err}_D(\hat{f})-\widehat{\operatorname{err}}_{S_n}(\hat{f})\right]}_{A}
+ \underbrace{\left[\widehat{\operatorname{err}}_{S_n}(\hat{f})-\widehat{\operatorname{err}}_{S_n}(f_*)\right]}_{B}
+ \underbrace{\left[\widehat{\operatorname{err}}_{S_n}(f_*)-\operatorname{err}_D(f_*)\right]}_{C} \\
&\leq \underbrace{\sup_{f\in\mathcal{F}}\left[\operatorname{err}_D(f)-\widehat{\operatorname{err}}_{S_n}(f)\right]}_{A'} + 0 + \underbrace{\left[\widehat{\operatorname{err}}_{S_n}(f_*)-\operatorname{err}_D(f_*)\right]}_{C'} \\
&\leq 2\sup_{f\in\mathcal{F}}\left|\operatorname{err}_D(f)-\widehat{\operatorname{err}}_{S_n}(f)\right|.
\end{aligned}$$

In decomposition, the key idea is to bound the test error in term of the training error. The inequality $B \leq 0$ follows from the fact that ERM achieves the smallest training error. The inequality $A \leq A'$ follows from $\hat{f} \in \mathcal{F}$. The quantity $C$ can be bounded using the probability inequalities of Chapter 2. The quantity $A'$ or $A''$ requires that the convergence of empirical mean to the true mean holds for all $f \in \mathcal{F}$. Such a convergence result is referred to as uniform convergence, and probability inequalities of Chapter 2 are not immediately applicable.

The key mathematical tool to analyze uniform convergence is the union bound, described in Proposition 3.5. In this book, we employ one-sided uniform convergence $A'$, and the quantity $C$ will be analyzed separately. The bounding of $C$ is relatively simple, and it doesn’t require uniform convergence because $f_*$ is a fixed function. The one-sided analysis makes it easier to handle probability inequalities that may have different forms in the case of underestimating the true mean versus overestimating the true mean (e.g. this happens with multiplicative Chernoff bounds). However, we note that in the literature, much of the existing analysis considers the two-sided uniform convergence quantity $A''$ for the sake of simplicity.