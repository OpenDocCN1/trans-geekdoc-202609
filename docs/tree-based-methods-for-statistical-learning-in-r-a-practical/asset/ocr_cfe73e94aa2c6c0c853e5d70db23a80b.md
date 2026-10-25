re-encoded, like in linear regression or neural networks. Trees are also invariant to monotone transformations of the predictors; that is, they only care about the rank order of the values of each ordered feature. For example, there's no need to apply logarithmic or square root transformations to any of the features like you might in a linear model.

**Automatic variable selection.** CART selects variables and splits one step at a time (“...like a carpenter that makes stairs”); hence the quote at the beginning of the chapter. If a variable cannot meaningfully partition the data into homogeneous subgroups, it will not likely be selected as a primary splitter. If it does, it’ll likely get snipped off during the pruning phase.

**Trees can naturally handle missing data.** As discussed in Section 2.7, CART can naturally avoid many of the problems caused by missing data by using surrogate splits (i.e., back up splitters that can be used whenever missing values are encountered during prediction).

**Trees are completely nonparametric.** CART is fully nonparametric. It does not require any distributional assumptions, and the user does not have to specify any parametric form for the model, like in linear regression. It can also automatically handle nonlinear relationships (although it tends be quite biased since it uses step function to approximate potentially smooth surfaces) and interactions.

# ## 2.10.2 Disadvantages of CART

**Large trees are difficult to interpret.** Large tree diagrams, like the ones in Figure 2.23 (p. 97), can be difficult to interpret and are probably not very useful to the end user. Fortunately, various interpretibility techniques, like variable importance plots and PDPs, can help alleviate this problem. Such techniques are the topic of Chapter 6.

**CART's splitting algorithm is quite greedy.** CART makes splits that are locally optimal. That is, the algorithm does not look through all possible tree structures to globally optimize some performance metric; that would be unfeasible, even for a small number of features. Instead, the algorithm recursively partitions the data by looking for the next best split at each stage. This is analogous to the difference between _forward-stepwise selection_ and _best-subset selection_. Greedy algorithms use a more constrained search and tend to have lower variance but often pay the price in bias. Chapters 5–8 discuss several strategies for breaking the bias-variance-tradeoff by combining many decision trees together.

**Splits lower on the tree are less accurate.** Data is essentially taken away after each split, making splits further down the tree less accurate (and noisy) compared to splits near the root node. This is part of the reason why binary