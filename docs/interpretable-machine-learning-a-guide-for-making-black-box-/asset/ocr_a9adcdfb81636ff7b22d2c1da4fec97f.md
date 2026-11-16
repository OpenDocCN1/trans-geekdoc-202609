numerical}}\mathb{b{I}_{\{_{-\{x\_j\neq\{ x\ '_j\}&\text{if \$x\_j$ categorical}\end{cases}\\}

Dividing the distance of a numeric feature \j(j) by (\widehat{R}\_j\)), the observed value range, scales (\delta\_G\)) for all features between 0 and 1.

The Gower distance can handle both numerical and categorical features but does not count how many features were changed. Therefore, we count the number of features in a third objectives (\o\_3\)) using the (\L\_0\)) norm:

|\o\_3(x,x')=||x-x'||_0=|\sum_{\{j=1\}^\{p\}}\mathbb{I}_{\{_{-\{x\ '_j\\neq\ x\_j\}}.\["

By minimizing (\o\_3\)) we aim for our third criteria - sparse feature changes.

The fourth objective (\o\_4\)) reflects that our counterfactuals should have likely feature values/combinations. We can infer how "likely" a data point is using the training data or another dataset. We denote this dataset as (\X^{\wedge}\{obs\}). As an approximation for the likelihood, (\o\_4\)) measures the average Gower distance between x' and the nearest observed data point (\x^{\wedge}\{[1\]}\\backslash\{\X^{\wedge}\{obs\}\)):

|\o\_4(x',\textbf{X}^{\wedge}\{obs\})=\text{frac}\{1\}\{p\}\sum_{\{j=1\}^\{p\}}\{p\})\text{delta\_G}(x'\_j,x^{\wedge}\{[1\]}\_j)]

Compared to Wachter et al., (\L(x,x',y',\X^{\wedge}\{obs\})\)} has no balancing/weighting terms like (\lambda). We do not want to collapse the four objectives (\o\_1\)), (\o\_2\)), (\o\_3\)) and (\o\_4\)) into a single objective by summing them up and weighting them, but we want to optimize all four terms simultaneously.

How can we do that? We use the **Nondominated Sorting Genetic Algorithm**\(^5\) or short NSGA-II. NSGA-II is a nature-inspired algorithm that applies Darwin's law of the "survival of the fittest". We denote the fitness of a counterfactual by its vector of objectives values \(\langle(\o\_1,\o\_2,\o\_3,\o\_4)\rangle\). The lower a counterfactuals four objectives, the "fitter" it is.

The algorithm consists of four steps that are repeated until a stopping criterion is met, for example, a maximum number of iterations/generations. The following figure visualizes the four steps of one generation.

![](bbox=[0.07, 0.56, 0.56, 0.72])

FIGURE 6.2: Visualization of one generation of the NSGA-II algorithm.

In the first generation a group of counterfactual candidates is initialized by randomly changing some of the features compared to our instance x to be explained. Sticking with above's credit example, one counterfactual could suggest to increase the income by \(\hat{} \rightarrow 30,000\) while another one proposes to have no default in the last 5 years and a reduction in age by 10. All other feature values are equal to the values of x. Each candidate is then evaluated using the four objective functions of above. Among them, we randomly select some candidates, where fitter candidates are more likely selected. The candidates are pairwise recombined to produce children that are similar to them by averaging their numerical feature values or by crossing over their categorical features. In addition, we slightly mutate the feature values of the children to explore the whole feature space.