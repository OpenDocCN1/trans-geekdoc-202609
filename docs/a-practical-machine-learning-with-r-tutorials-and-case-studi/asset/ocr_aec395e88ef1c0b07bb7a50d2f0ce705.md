# 10.3 Decision Trees

observations from the parent node into the child nodes. For example, Sex, Age, or Fare.

2) The splitting value is relevant for continuous variables. For example, when the splitting variable is Age, we have to decide on the passenger's age that determines if an observation is moved to the left or the right child node (13 years or older for VES in our case; see Figure 10.1).

To find the best splitting variable with the best splitting value, the Optimizer compares all combinations of splitting variables and splitting values.4

# What criterion determines if a splitting variable/value combination is good?

The Decision Tree algorithm from the r package uses Gini Impurity as a criterion for classification problems. Other measures that can be set Information Gain and Chi-Square.5 Here we focus on Gini Impurity.6

The Titanic passengers were different in many ways. Some of their differences (e.g., their Sex) were crucial for survival, while others were less important. When we split a parent node (for instance, the root node) into two child nodes, we want the two nodes to be as different as possible regarding survival proportions. Ideally, we would like to get one child node with a survival proportion of 100% and the other with 0%. In that case containing one group of survivors and another group of non-survivors, Gini Impurity would be somewhat at the lowest level for both child nodes.

Let us follow this unrealistic path by assuming that all men on the Titanic died and all women survived. A decision rule of Sex=male would create two pure nodes containing only non-survivors and the other containing only survivors. GiniImpurity should be 0 for both pure child nodes.

Gini Impurity for an individual node is defined by the product of the proportions for the observation between two different classes (P_{Surv} and P_{NonSurv}), multiplied by two. In one case:7

```
$G^{Imp} = 2P_{Surv}P_{NonSurv}$. (10.1)
```

In our example we create two pure child nodes, Equation (10.1) shows the

4There are a few shortcuts that avoid all variables of a variable as splitting values, which these secures the scope of this book.

5See Sharna (2020) for an intuitive description of the different standards.

6Singh (2021) provides an intuitive introduction about Gini Impurity.

7Gini Impurity is calculated for an individual node and estimates "..." the probability that two entities taken at random from the dataset of interest (with replacement) represent (...) different types*(Wikipedia contributors (2023b).