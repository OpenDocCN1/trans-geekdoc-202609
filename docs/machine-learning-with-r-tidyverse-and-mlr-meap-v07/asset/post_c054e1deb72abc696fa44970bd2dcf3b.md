
## **SIDEBAR** Generalizing Gini index to any number of classes

In this example we’ve only considered two classes, but the Gini index of a node is easily calculable for problems which have many classes. In that situation the equation for Gini index generalizes to:

$$\mathrm{Gini\ index}=1-\sum_{k=1}^{K}p(\mathrm{class}_k)^2$$

Which is just a fancy way of saying that we calculate $p(\mathrm{class}_k)^2$ for each class from 1 to K (the number of classes), add them all up, and subtract this value from 1.

If you’re interested, the equation for entropy is:

$$\mathrm{entropy}=\sum_{k=1}^{K}-p(\mathrm{class}_k)\times\log_2 p(\mathrm{class}_k)$$

Which is just a fancy way of saying that we calculate $p(\mathrm{class})\times\log_2 p(\mathrm{class})$ for each class from 1 to K (the number of classes) and add them all up (which becomes a subtraction because the first term is negative). As for Gini gain, the information gain is calculated as the entropy of the parent, minus the entropy of the split (which is calculated in exactly the same way as the Gini index for the split).

## 7.1.2 What about continuous, and multi-level categorical predictors?

In this section I’ll show you how the splits are chosen for continuous and categorical predictor variables.

When a predictor variable is dichotomous (has only two levels), it’s quite obvious how to use it for a split: cases with one value go left, and cases with the other value go right. Decision trees can also split the cases using continuous variables, but what value is chosen as the split point? Have a look at the example in figure 7.4. We have cases from three classes, plotted against two continuous variables. The feature space is split into rectangles by each node. At the first node, the cases are split into those with a value of variable 2 above and below 20. The cases which make it to the second node are further split into those with a value of variable 1 above and below 10,000.

But how is the exact split point chosen for a continuous predictor? Well the cases in the training set are arranged in order of the continuous variable, and the Gini gain is evaluated for the mid-point between each adjacent pair of cases. If the greatest Gini gain amongst all predictor variables is one of these mid-points, then this is chosen as the split for that node. This is illustrated in figure 7.5.

Figure 7.5 How the split point is chosen for continuous predictors. Cases (circles) are arranged in order of their value of the continuous predictor. The mid-point between each adjacent pair of cases is considered as a candidate split, and the Gini gain is calculated for each. If one of these splits has the highest Gini gain of any candidate split, it will be used to split the tree at this node.

A similar procedure is used for categorical predictors with more than two levels. First, the Gini index is computed for each level of the predictor (using the proportion of each class that has that value of the predictor). The factor levels are arranged in order of their Gini indices, and the Gini gain is evaluated for a split between each adjacent pair of levels. Take a look at the example in figure 7.6. We have a factor with three levels (A, B, and C), we evaluate the Gini index of each and find their values are such that B < A < C for their Gini indices. Now, we evaluate the Gini gain for the splits B versus A & C, and C versus B & A.

In this way, we can create a binary split from categorical variables with many predictors, without having to try every single combination of level splits (2^(m−1) where m is the number of levels of the variable). If the split B versus A & C is found to have the greatest Gini gain, then cases reaching this node will go down one branch if they have a value of B for this variable, and will go down the other branch if they have a value of A or C.

Figure 7.6 How the split point is chosen for categorical predictors. The Gini index of each factor level is calculated using the proportion of cases from each class with that factor level. The factor levels are arranged in order of their Gini indices and the Gini gain is evaluated for each split between adjacent levels.

## 7.1.3 Hyperparameters of the rpart algorithm

In this section I’ll show you what hyperparameters need to be tuned for the rpart algorithm, what they do, and why we need to tune them in order to get the best performing tree possible.

Decision tree algorithms are described as *greedy*. By greedy, I don’t mean they take an extra helping at the buffet line; I mean that they search for the split that will perform best *at the current node*, rather than the one that will produce the best result globally. For example, a particular split might discriminate the classes best at the current node, but result in poor

These four criteria combined can make for very stringent and complicated stopping criteria. As the values of these criteria cannot be learned directly from the data, they are hyperparameters! What do we do with hyperparameters? Tune them! So when we build a model with rpart, we will tune these stopping criteria to get values that give us the best-performing model.

Recall from chapter 3 that a variable or option that controls how an algorithm learns, but which cannot be learned from the data, is called a hyperparameter.

In this section, you're going to learn how to build a decision tree with rpart, and how to tune its hyperparameters. Imagine you work in public engagement at a wildlife sanctuary. You're tasked with creating an interactive game for children, to teach them about different animal classes. The game asks the children to think of any animal in the sanctuary, and then asks them questions about the physical characteristics of that animal. Based on the responses the child gives, the model should tell the child what class their animal belongs to (mammal, bird, reptile etc.). It’s important your model is general enough that it can be used at other wildlife sanctuaries. Let’s start by loading the mlr and tidyverse packages.

```
library(mlr)
library(tidyverse)
```
