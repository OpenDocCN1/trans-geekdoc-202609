allocation, $k _ { i }$.

# **ALGORITHM 17    K-Means**

To cluster observations $\{ \mathbf { x } _ { i } \} _ { i = 1 } ^ { n }$ into $K$ groups, initialize by randomly drawing $k _ { i } \in \{ 1 \ldots K \}$ for each $i$. Then, until convergence:

+   - Estimate the cluster centers

$$\hat { \boldsymbol { \mu } } _ { k } = \overline { { \boldsymbol { x } } } _ { k } = \frac { 1 } { n _ { k } } \sum _ { i : k _ { i } = k } \mathbf { x } _ { i }$$

where $\{ i : k _ { i } = k \}$ are the $n _ { k }$ observations with $k _ { i } = k$.

+   - For each $i$, update $k _ { i }$ to the component with center $\hat { \boldsymbol { \mu } } _ { k }$ closest to $\boldsymbol { x } _ { i }$:

$$k _ { i } = \operatorname { a r g m i n } _ { k } \sum _ { j } \left( \mathbf { x } _ { i j } - \hat { \mu } _ { k j } \right) ^ { 2 }$$

There is one annoying difference between $K$-means and the other deviance minimization algorithms that we have seen thus far: if you run $K$-means multiple times, you can get different answers. This happens because of the random $k _ { i }$ initialization, combined with the fact that the minimization objective is nonconvex. Nonconvexity says that the deviance surface is not a simple cup (e.g., like $x _ { 2 }$) that has one single minimum; rather, it is a lumpy surface that can have multiple "solutions" where the $k _ { i }$ can converge during Algorithm 17. For this reason, it is often recommended that you run $K$-means multiple times from different random starts and use the solution that gives the lowest deviance (lowest sum-squared error around the $\hat { \boldsymbol { \mu } } _ { k }$ centers).

More generally, this sort of indeterminacy should cause you pause: how much can the clusters represent some "true" state of the world if your estimates change every time you run the algorithm? Indeed, this lack of identification is a reason that we tend to caution against interpreting the results of clustering as anything more than useful exploratory or predictive summaries.

To illustrate the procedure, let's look at clustering various (former) European countries by food. We have data on protein consumption by country, in grams per person per day for 25 countries: