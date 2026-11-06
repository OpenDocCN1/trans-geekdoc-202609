
# Decision Tree Split Search

## Bonferroni Correction

Statisticians face a similar problem when they combine the results from multiple statistical tests. As the number of tests increases, the chance of a false positive result likewise increases. To maintain overall confidence in the statistical findings, statisticians inflate the `p-values` of each test by a factor equal to the number of tests being conducted. If an inflated `p-value` shows a significant result, then the significance of the overall results is assured. This type of `p-value` adjustment is known as a `Bonferroni correction`.

Because each split point corresponds to a statistical test, `Bonferroni corrections` are automatically applied to the `logworth` calculations for an input. These corrections, also called `Bonferroni adjustments`, penalize inputs with many split points by reducing the `logworth` of a split by an amount equal to the log of the number of distinct input values. This is equivalent to the `Bonferroni correction` because subtracting this constant from `logworth` is equivalent to multiplying the corresponding `chi-squared` `p-value` by the number of split points. The adjustment enables a fairer comparison of inputs with many and few levels later in the `split-search` algorithm.

## Missing Values Handling

Third, for inputs with missing values, two sets of `Bonferroni-adjusted logworths` are generated. For the first set, cases with missing input values are included in the left branch of the contingency table and `logworths` are calculated. For the second set of `logworths`, missing value cases are moved to the right branch. The best split is then selected from the set of possible splits with the missing values in the left and right branches, respectively.

## Partitioning Process

The partitioning process is repeated for every input in the `training data`. Inputs whose adjusted `logworth` fails to exceed the `threshold` are excluded from consideration.

### Figure A.4.2: Decision Tree Split Search – Repeat the Partitioning Process

![Figure 1.1 Some JMP Help Options](Images/Image877.jpg)

Again, the optimal split for the next input considered is the one that maximizes the `logworth` function for that input.

After you determine the best split for every input, the tree algorithm compares each best split’s corresponding `logworth`. The split with the highest adjusted `logworth` is deemed best.

### Figure A.4.3: Decision Tree Split Search – Partiioning the Training Data using the Best Split Rule

![Figure 1.1 Some JMP Help Options](Images/Image8841.png)

![Figure 1.1 Some JMP Help Options](Images/Image8941.png)

![Figure 1.1 Some JMP Help Options](Images/Image9011.png)

![Figure 1.1 Some JMP Help Options](Images/Image908.png)

The `training data` are partitioned using the best split rule.

The `logworth` of the `x2` split is negative. This might seem surprising, but it results from several adjustments made to the `logworth` calculation. (`The Bonferroni adjustment` was described previously. Another, called the `depth adjustment`, is outlined later in this section.)

The split search continues within each leaf. `Logworths` are compared as before.

### Figure A.4.4: Decision Tree Split Search – Comparing Logworths

![Figure 1.1 Some JMP Help Options](Images/Image9161.png)

![Figure 1.1 Some JMP Help Options](Images/Image9231.png)

Because the significance of secondary and subsequent splits depends on the significance of the previous splits, the algorithm again faces a multiple comparison problem. To compensate for this problem, the algorithm increases the `threshold` by an amount related to the number of splits above the current split. For binary splits, the `threshold` is increased by `log10(2)` `d` ≈ `0.3∙d`, where `d` is the depth of the split on the `decision tree`. This is known as the `depth adjustment`.

By increasing the `threshold` for each depth (or equivalently decreasing the `logworths`), the tree algorithm makes it increasingly easy for an input’s splits to be excluded from consideration.

### Figure A.4.5: Decision Tree Split Search – Creating Partition Rules

![Figure 1.1 Some JMP Help Options](Images/Image9312.png)

![Figure 1.1 Some JMP Help Options](Images/Image9381.png)

The data are partitioned according to the best split, which creates a second partition rule. The process repeats in each leaf until there are no more splits whose adjusted `logworth` exceeds the `depth-adjusted thresholds`. This process completes the `split-search` portion of the tree algorithm.

## Maximal Tree

The resulting partition of the input space is known as the `maximal tree`. Development of the `maximal tree` is based exclusively on statistical measures of split worth on the `training data`. It is likely that the `maximal tree` fails to generalize well on an independent set of `validation data`. The `maximal tree` is the starting place for how complexity of the model will be optimized. Optimizing the complexity of a tree is done through `pruning`, and this is covered in the next section.

# Appendix B: Solutions

## Practice Solutions

Note: Due to the distributed nature of the `SAS Viya` environment, results might not be reproducible. Your results and answers to the questions in the practices could be different from those provided below.

### Chapter 7

#### Building a Decision Tree

1. Build a decision tree using the `Autotune` feature. Add a `Decision Tree` node to the `Lesson 3` `pipeline`, below the `Variable Selection` node. Use the `Autotune` feature. Explore the settings that are made available when `Autotune` is selected.

a. On the `Starter Template` `pipeline`, right-click the `Variable Selection` node and select `Add child node`  `Supervised Learning`  `Decision Tree`.

b. In the properties pane, turn on the `Perform Autotuning` option. The default properties show starting values and ranges that are tried for each property in the `decision tree` model.

c. Right-click the `Decision Tree` node and select `Run`. This process might take few minutes.

d. When the execution is over, right-click the `Decision Tree` node and select `Results`.

e. Examine the `Results` window. Maximize the `Autotune Results` window and notice the different evaluations performed. Restore the `Autotune Results` window.

![Figure 1.1 Some JMP Help Options](Images/Image745.png)

f. Scroll down and maximize the `Output` window. This output shows the set of parameters selected for the final `decision tree` model.

![Figure 1.1 Some JMP Help Options](Images/Image752.png)

g. Click the `Assessment` tab. Scroll down and observe the `Fit Statistics` window. The average squared error for the `Autotune` model is 0.0573 on the `VALIDATE` partition.

![Figure 1.1 Some JMP Help Options](Images/Image7612.png)

2. What criteria were selected for the champion model?

◦ `Split criteria`: `Gain`

◦ `Pruning method`: `Cost Complexity`

◦ `Maximum number of branches`: 2

◦ `Maximum tree depth`: 11

3. How does the autotuned decision tree compare to the other models in the pipeline, particularly to the decision tree model built during the demonstration? Consider the fit statistics average squared error for this comparison.

It performed better than the decision tree built during the demonstration.

### Chapter 8

#### Building a Gradient Boosting Model

1. Build a gradient boosting model using the `Autotune` feature. Add a `Gradient Boosting` node to the `Lesson 3` `pipeline`, below the `Variable Selection` node. Use the `Autotune` feature. Explore the settings that are made available when `Autotune` is selected.

a. On the `Starter Template` `pipeline`, right-click the `Variable Selection` node and select `Add child node`  `Supervised Learning`  `Gradient Boosting`.

b. In the properties pane, turn on the `Perform Autotuning` option. The default properties show starting values and ranges that are tried for each property in the `gradient boosting` model.

c. Right-click the `Gradient Boosting` node and select `Run`. This process might take few minutes.

d. When the execution is over, right-click the `Gradient Boosting` node and select `Results`.

e. Examine the `Results` window. Maximize the `Autotune Results` window and notice the different evaluations performed. Restore the `Autotune Results` window.

![Figure 1.1 Some JMP Help Options](Images/Image769.png)
