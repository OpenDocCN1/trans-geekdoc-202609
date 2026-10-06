
## 10.3 Decision Trees

- The **root node** contains the training dataset, which is indicated by the label "100%" in the third row of the *root node*. The second label indicates that, sadly, the survival rate was only *0.39* (39%). Since the survival rate is less than 0.5, we would predict that a random passenger (observation) does not survive (Survived = FALSE); see the first label in the *root node*.

- Next, all observations are moved from the *root node* to one of its child *nodes* depending if the *decision rule* *Sex=male* is fulfilled (left child) or not (right child).

Consequently, male observations (passengers) are moved to the left child *node* and female observations to the *right child*. When reading the three labels from the *left child node*, we can see that 64% of the training observations ended up in this node (64% of passengers in the training dataset are male). The survival rate among them was only 0.2 (second label), and therefore, we would predict that an individual passenger does not survive (Survived = FALSE; 0.2 < 0.5).

The *right child node* contains only female observations. From the training data observations, 36% are female. For these female passengers, the survival rate was 0.73. Thus, for an individual female passenger, we would predict that she survives (Survived = TRUE; 0.73 > 0.5).

In summary: After the first split by *Sex*, we can conclude that men's survival chances were 20%, while the survival chances of women were 73%.

- The process does not stop after the split for *Sex*. When you look at the *left child node* below the *root node*, you can see that the male passengers are further split into older nodes (13 years and older; moved to the left *child node*) and younger males (moved to the right *child node*).

Checking the labels in the left child node (*a terminal node*), you can see that 60% of the training observations were male and older than 13 years. The survival rate among them was only 0.17. Therefore, we would predict for an older male who does not survive (Survived = FALSE; 0.17 < 0.5).

Checking the labels of the *right child node* (not a terminal node) below the *Age>=13* decision rule shows that 4% of the training observations were young males, and their survival rate was 0.57. Thus, for an individual young male (if we do not know in which class he traveled), we would predict that he survives (Survived = TRUE) because 0.57 > 0.5.

- After all observations from the training dataset descend through the *Decision Tree*, they end up in one of the six *terminal nodes*. Note that the percentages of training data in the six *terminal nodes* add up to 100% (60% + 3% + 1% + 3% + 14% + 18% ≈ 100%).

We know the survival rate for each *terminal node* based on the training observations that ended up in that node. Therefore, we can predict (Survived = FALSE or Survived = TRUE) for each terminal node (see the first labels of the six terminal nodes).

## Decision Tree Predictions for Binary vs. Continuous Variables

The prediction for a specific node for a binary variable like Survived (TRUE or FALSE) can be derived as follows:

Using all observations from the training dataset that end up in a specific node, the proportion for the last label TRUE. If this proportion is greater than 50%, predict TRUE for any observation that ends up in this node. Otherwise, predict FALSE.

The prediction for a specific node for a continuous variable can be derived as follows:

Calculate the mean for the outcome variable from all training data observations that ended up in a specific node. This is the prediction for an observation's outcome that later ends up in that.

Now that you know how the training data were guided through the tree to one of the terminal nodes, you should be able to interpret the Decision Tree as whole. Try to confirm the following five statements with the Decision Tree in Figure 10.1.

- 1. Adult male passengers 13 years or older, regardless of the class they traveled and the fare they paid, had only a survival rate of 0.17.
- 2. Young male passengers (young than 13 years), regardless of which class they traveled and the fare they paid, had a survival rate of 0.57.
- 3. Young male passengers (young than 13 years) traveling in Third Class had only a survival rate of 0.4 regardless of the fare they paid.
- 4. Female passengers, regardless of age and not considering the class they traveled in or the fare they paid, had a survival rate of 0.73.
- 5. When considering the class female passengers traveled in, we can see female passengers, regardless of age, had a survival rate of 0.95 when they traveled in First or Second Class regardless of the fare they paid.

Note that not decision rules and nodes from the Decision Tree in Figure 10.1 make sense — a weakness of Decision Trees.

For example, if you look at the rule that created the fourth and fifth terminal nodes and the related parent node, you can see that females traveling in Third Class had a lower survival rate when the fare they paid was more than 25 British pounds as compared to otherwise (5% vs. 60%). It makes little sense.

## 10.3 Decision Trees

**Table 10.1 Nine-year boy on Titanic**

| Survived | Sex | Class | Fare |
| :--- | :--- | :--- | :--- |
| TRUE | male | 3 | 9 |
| TRUE | female | 3 | 22.5 |
| FALSE | male | 3 | 27 |
| TRUE | female | 1 | 27.1 |
| TRUE | female | 2 | 38 |
| FALSE | male | 3 | 35 |
| FALSE | male | 3 | 26 |
| TRUE | male | 2 | 53 |

## 10 Tree-Based Models — Bootstrapping Explained

Since we know for each passenger (observation of the testing dataset) if they survived or not, and also what the Decision Tree predicted (see the .pred_class column), we can generate a confusion matrix and also use the metric_set() to calculate the metrics accuracy, sensitivity, and specificity.

```
conf_mat(DataTestWithPred, truth=Survived, estimate=.pred_class)

## Truth
## Prediction TRUE FALSE
TRUE 63 14
FALSE 23 123
```

```
metricSetTitanic=metric_set(accuracy, sensitivity, specificity)
metricSetTitanic(DataTestWithPred, truth=Survived, estimate=.pred_class)

## A title 3 x 3
## ..metric .estimate
<chr> <chr> <dbl>
1 accuracy binary 0.834
2 sensitivity binary 0.733
3 specificity binary 0.898
```

With an overall accuracy of 83%, the prediction results are not bad. The model worked well in predicting passengers that did not survive (negative class: specificity). As you can see, specificity is higher than sensitivity. However, the difference is not big enough to consider the dataset as unbalanced.

This leaves us with one topic that we have not touched so far:

# How the Optimizer determine the decision rules

Decision rules are determined from the top of the Decision Tree down to the bottom. The Optimizer starts with finding the best decision rule for the root node, then moves down to the child nodes and finds the decision rule for each of the child nodes and then for the child nodes of the child nodes. The process stops when either the maximum level with the hyper-parameter level is reached (level=3 in our case) or when splitting a node further no increases the predictive quality.

Decision rules consist of two components:

- 1) The splitting variable. That is, the variable used to split the

> Note Decision rules of the previous level are never reversed, even if this would allow for a better decision rule on the current level. This type of algorithm is called a greedy algorithm.
