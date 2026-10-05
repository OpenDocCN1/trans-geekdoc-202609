# 4.5.4 Advantages

This section discusses the benefits of IF-THEN rules in general.

IF-THEN rules are **easy to interpret**. They are probably the most interpretable of the-interpretable models. This statement only applies if the number of rules is small, the conditions of the rules are short (maximum 3 I would say) and if the rules are organized in a decision list or a non-overlapping decision set.

Decision rules can be **as expressive as decision trees, while being more compact**. Decision trees often also suffer from replicated sub-trees, that is, when the splits in a left and a right child node have the same structure.

The **prediction with IF-THEN rules is fast**, since only a few binary statements need to be checked to determine which rules apply.

Decision rules are **robust** against monotonic transformations of the input features, because only the threshold in changes changes. They are also robust against outliers, since it only matters if a condition applies or not.

IF-THEN rules usually generate sparse models, which means that not many features are included. They **select only the relevant features** for the model. For example, a linear model assigns a weight to every input by default. Features that are irrelevant can simply be ignored by IF-THEN rules.

Simple rules like OneR **can be used as baseline** for more complex algorithms.

# 4.5.5 Disadvantages

This deals with the disadvantages of IF-THEN rules in general.

The research and literature for IF-THEN rules focuses on classification and almost **completely neglects regression**. While you can always divide a continuous target into intervals and turn it into a classification problem, you lose information. In general, approaches are more attractive if you use them for both regression and classification.

Often the **features also have to be categorical**. While numeric features must be categorized if you want to use them. There are many ways to a continuous feature into intervals, but this is not trivial and with many questions without clear answers. How many intervals should the feature be divided into? What is the splitting criteria: Fixed interval lengths, quantiles or people? Categorizing continuous features is a non-trivial issue that is often neglected and people just use the next best method (like I did in the examples).

Many of the order rule-learning algorithms are prone to overfitting. The algorithms presented here all have at least safeguards to prevent overfitting. OneR is limited because it can only use one feature (only problematic if the feature has too many features or if there are many features, which equates to the multiple testing problem), RIPPER does pruning and Bayesian Rule Lists impose a prior distribution on the decision lists.