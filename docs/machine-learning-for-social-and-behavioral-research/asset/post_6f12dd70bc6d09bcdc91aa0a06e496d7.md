
## 5 Decision Trees

Decision trees are one of the core algorithms of machine learning, both as an individual algorithm, as well as forming the basis for many more complex algorithms (Chapter 6). Their primary benefit is the level of interpretability afforded by the visually depicted tree structure along with propensity to identify interaction effects without manual specification. We spend the majority of this chapter focused on describing the tree creation process and how to interpret the tree structure, while ending with details on the specific implementations and nuances in application.

## 5.1 Key Terminology

- Decision tree. Also commonly referred to as classification and regression trees, decision trees refer to an algorithm that recursively partitions the predictor space to create a nonlinear mapping from predictors to an outcome. The resultant mapping is then depicted as an interpretable tree structure.
- Partition. The process of dividing the dataset into subgroups based on predictor cutoff values.
- Heterogeneity. In contrast to homogeneity, heterogeneity refers to the existence of between-person variability, namely, assuming that an entire sample represents a singular population is untenable.
- Node. A group of cases in a tree structure. The root node refers to the entire sample that has yet to be partitioned, while the terminal node is the final subgroup at the end of the partitioning process.
- Surrogate split. A split in the decision tree that does not show up in the final tree as it did not produce as much of an improvement in fit as the chosen split, but is used for cases with missingness on the predictor used in the chosen split.
- Pruning. The process of creating a large decision tree, followed by pruning or removing splits to create a smaller, more generalizable tree.
- Variable importance. A summary statistic for how much an individual predictor contributes to explaining variability in the outcome. This is used primarily as a way to understand which predictors are important in algorithms (trees and ensembles; see Chapter 6) that are not as interpretable as linear regression.

## 5.2 Introduction

Decision trees were first introduced in the 1960s by Morgan and Sonquist (1963). However, the use of the method did not capture the attention of the statistics community until 20 years later with the work of Breiman, Friedman, Olshen, and Stone (1984). First termed automatic interaction detection, the purpose of the algorithm was to efficiently identify interactions when the number of predictors was large. In large datasets, the sequential testing of a large number of models and possible combinations of variables quickly decreases the statistical properties of the models (i.e., false positives; Morgan, 2005).

As there are a number of variants to decision tree algorithms, we refer to decision trees as the umbrella methodology, and refer to specific algorithms that fall under this decision trees terminology as such. For instance, the most popular variant of decision trees is classification and regression trees (CART, Breiman et al., 1984). Note that classification and regression trees is also commonly used to refer to decision trees, while CART refers to a specific algorithm.

Decision trees' popularity can be attributed to their easy-to-understand tree structure, that mimics the way that humans make decisions. We elaborate on this further below. To create a tree structure, the predictor space into into all possible unique values. Across these unique values, the algorithm iteratively partitions the dataset to determine an improvement in model fit. This involves placing each observation into one of two groups, of which each member receives the same predicted response. The actual partitioning of the dataset functions differently based on the type of each predictor variable. For quantitative variables, each unique value is tested in order: For example, if predictor values range from 50 to 100, the process is as follows: Everyone with a predictor value equal to 50 versus everyone with a predictor value greater than 50, then everyone with a predictor value equal to 50–51 versus everyone with greater than 51, until every possible successive value is tested in this manner. Given $m$ unique sorted values, this involves testing $m-1$ unique splits. For nominal variables, as there is no ordering to the values, all possible groupings are tested. If there are $m$ categories, this involves testing $2^{m-1}-1$ dichotomous splits. Particularly for predictors with large categories, this can quickly become computationally burdensome.

Predictions derived from the tree structure are then compared to each observation's actual response to error (model misfit). For continuous outcomes, this is generally mean squared error, for categorical it can be accuracy or two alternatives, such as entropy or the gini index. After every possible partition has been tested, and an error is calculated and assigned to this specific partitioning, the split that results in the largest reduction in error is chosen. Effectively, the algorithm has created two datasets: dataset A contains every observation that adheres to one side of the best splitting rule and dataset B contains all observations.

At its core, decision trees are an analytical method for creating subgroups. This assumes that identifying heterogeneity (creating subgroups) with respect to the observations in the sample will explain some portion of the outcome.

### 5.2.1 Example 1

To make the process of creating a tree structure more concrete, we use data from the National Survey on Drug Use and Health, as was detailed in the previous chapter. This dataset was split into a subset to have equal proportions of the suicidalation (last 12 months; SUIC THINK) outcome, as well as selecting categories that received questions about depression. Predictors included variables that measure feelings of worthlessness (worthiness; 1 for Yes), whether depression interfered with work or personal life (interference; 1–5 = extremely), whether symptoms of depression felt every day (dep; 1 = Yes), sex (1 = Female), age, and race. Note that in contrast to the logistic regression analyses, it is not recommended to use dummy code categorical predictors. Instead, these should be treated as nominal, as it is worthwhile to test a one-versus-all scheme for group differences (as opposed to just a comparison to the reference group).

Decision trees first start with a root node, as displayed in Figure 5.1.

FIGURE 5.1. The root node from the NSDUH dataset. No splits have occurred, as every observation is treated as a homogenous sample. "0" refers to the predicted response for each case in the node, 0.49 is the mean of the outcome, and 100% denotes that the entire sample is contained in this node.

![](img/5047f0f064e22688ceb5d0cdfaf3e964_126_0.png)

For classification trees, the prediction for each observation reflects the distribution of both classes, which in our example is 0.49, or 49% 0s. In regression trees, this would be the mean of the outcome. In our example, those with a history of suicide attempts (1) and those without a history (0) are roughly distributed 50–50.

To create a first split, the algorithm tests all possible splits, according to the rules dictated by the predictor types (which is important to check the class of the predictors before creating the tree). This resulted in the following split depicted in Figure 5.2.

FIGURE 5.2. First split in the NSDUH dataset. The split occurs between the values of 0 and 1 worthless.

![](img/5047f0f064e22688ceb5d0cdfaf3e964_127_0.png)

This split occurred between 0 and 1 on worthless, with those having a value of 0 (19% of sample) receiving a predicted probability of suicide attempt of 0.25. Note that this predicted probability is the class proportion in each node (e.g., 25% of the sample in this node has 1s). Similar to logistic regression, decision trees output predicted probabilities, with class assignment dependent on the probability cutoff (generally 0.5). Cases with a worthless value of 1 received a predicted probability of 0.55 (81%) of the sample. Now that we effectively have two subgroups of cases based on trying to partition each subgroup worthless, the algorithm proceeds by trying to partition each subgroup further. This results in the next set of splits is given in Figure 5.3.
