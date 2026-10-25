![](bbox=[0.215, 0.085, 0.875, 0.385])

FIGURE 2.8: Potential split points for temperature as a function of gain. The maximum gain occurs at a temperature of 82.5 °F (the dashed vertical line).

For example, suppose we considered splitting on Wind next. Using the same procedures previously described, we would find that the next best partition occurs in the left child node using Wind with a cutpoint of 7.15 (mph). The corresponding tree diagram is displayed on the left side of Figure 2.9. If we stop splitting here, the result is a regression tree in two features. The corresponding prediction function, displayed on the right side of Figure 2.9, is a surface that's constant over each terminal node.

# 2.4 Categorical splits

Up to this point, we've only considered splits for ordered predictors, which have the form x < c vs. x ≥ c, where c is in the domain of x. But what about splits involving nominal categorical features? If x is ordinal (i.e., an ordered category, like low < medium < high), then we can map its ordered categories to the integers 1, 2, ..., J, where J is the number of unique categories, and split as if x were originally numeric. If x is nominal (i.e., the order of the categories has no meaning), then we have to consider all possible ways to split