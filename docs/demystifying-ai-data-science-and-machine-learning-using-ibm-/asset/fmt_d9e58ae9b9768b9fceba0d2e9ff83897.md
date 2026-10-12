
## Limitations of Decision Trees

*   **Overfitting**: Decision trees are sensitive to overfitting, especially when the tree is deep and complex.
*   **Instability and variance**: Small changes in the data can lead to significantly different tree structures, which results in high variance in the predictions.
*   **Bias toward dominant classes**: In classification models with imbalanced datasets, decision trees may be biased toward the majority class, which leads to suboptimal performance in minority classes.
*   **Difficulty handling numeric outliers**: Decision trees are sensitive to the scale of continuous variables, and outliers can have a disproportionate influence on the tree's structure and predictions.
*   **Global optimum vs. local optimum**: The greedy nature of the decision tree algorithm may lead to suboptimal splits at individual nodes, even though they contribute to the overall best split.
*   **Lack of coefficients**: Unlike regression, the output of a decision tree model does not provide coefficients for evaluating the effects of predictors on the target variable. These effects must be evaluated through the tree structure and the probability values, which could be challenging to understand.

Despite their limitations, decision trees remain a valuable and widely used machine learning method, especially for data mining projects that require interpretability, handling nonlinear relationships, and dealing with both categorical and continuous variables. However, to address some of the drawbacks, techniques like pruning, ensemble methods, and careful hyperparameter tuning are often applied to improve the model performance.

## Tree Pruning

![Figure 8.9](images/ufig8_9.jpg)

282. Pruning is a crucial step in ensuring a decision tree model has good predictive power. Pruning involves removing redundant subtrees and replacing them with leaf nodes. Large trees with many branches and layers can lead to overfitting, which occurs when the model performs well on training data but poorly on new data. Additionally, large trees are difficult to interpret and understand. These trees often use the same predictors to construct the hierarchy, repeatedly splitting nodes to create numerous branches in an attempt to improve model fit. However, this process can result in overly complex trees that only fit the training data, leading to overfitting.

Pruning helps to prevent overfitting by simplifying the tree, making it more generalized to new datasets, without sacrificing model accuracy. Furthermore, a pruned tree is easier to understand and interpret. [Figure 8.2](#chapter8.xhtml#fig8_2) illustrates the process of decision tree pruning.

![FIGURE 8.2 Decision tree pruning. Return to text.](images/fig8_2.jpg)

FIGURE 8.2 Decision tree pruning. [Return to text.](#chapter8.xhtml#b8fig8_2)

The process of tree pruning consists of six steps:

1.  **Growing the full tree**: The first step is to grow the decision tree to its maximum depth or until a stopping criterion is met. During this stage, the algorithm recursively partitions the data and creates branches and nodes based on a chosen splitting criterion.
2.  **Evaluating node importance**: After growing the full tree, assess the importance of each node in improving model performance. Nodes that contribute little to predictive accuracy or are not statistically significant are candidates for pruning.
3.  **Cost-complexity pruning**: Cost-complexity pruning, also known as minimal cost-complexity pruning, is a popular pruning method. It introduces a complexity parameter (alpha) that balances model accuracy and complexity. The algorithm evaluates the impact of removing each node and calculates a cost-complexity score for the subtree rooted at that node.
4.  283. **Selecting the optimal pruning level**: The algorithm iteratively prunes nodes with the smallest cost-complexity score while evaluating model performance on a validation set. Pruning continues until further reductions result in a significant drop in predictive performance. The optimal pruning level corresponds to the subtree that provides the best balance between accuracy and simplicity.
5.  **Pruning the tree**: Once the optimal pruning level is determined, the tree is pruned by removing nodes and branches corresponding to subtrees above the selected level. The resulting pruned tree is a simplified version of the full tree.

Pruning helps control overfitting by reducing the complexity of the decision tree, thereby improving its predictive power. It also enhances model interpretability by providing a more concise representation of the decision-making process. However, pruning is a data-driven process, and the optimal pruning level may vary depending on the specific dataset. Regular validation is essential to determine the best pruning strategy for each model.

### Types of Decision Tree Pruning

Decision tree pruning can be classified into two types: pre-pruning and post-pruning.

*   **Pre-pruning** (also known as the Early Stopping Rule): Pre-pruning prevents the growth of a tree beyond a specific size or depth based on certain measures like the Gini index or entropy. In this method, the tree-building process is halted when a pruning condition is met at a node. If the condition is satisfied, the subtree is pruned by replacing the decision node with a leaf node. Otherwise, the tree continues to grow. Pre-pruning is faster and more efficient, as it prevents the creation of overly complex subtrees that may overfit the training data. However, pre-pruning can stop the tree's growth prematurely based on the stopping condition.
*   **Post-pruning**: In post-pruning, the entire tree is grown first, and then subtrees are pruned from the bottom-up. Starting from the bottom decision nodes, measures such as Gini impurity or information gain are used to decide whether to keep a decision node or replace it with a leaf node.

#### Manual vs. Automatic Pruning

*   **Manual pruning**: Manual pruning is generally not recommended for data mining projects because it relies on the researcher's judgment, which can introduce bias. Manual pruning also requires a clear justification for removing a subtree, which may not always be evident. For example, how do we know which branches are redundant to remove, and how do we justify that decision? Mistakes in manual pruning can lead to poorer model fit or render the tree ineffective. While manual pruning may be feasible for simple trees, it is impractical for large trees with many nodes and branches. It also defeats the purpose of mining large datasets.
*   **Automatic pruning**: The recommended approach is automatic pruning. This involves setting specific criteria for tree development and subtree selection, allowing the software to perform pruning based on those configurations. Typically, you define how the software should select and assess subtrees and whether to apply cross-validation. The software then uses search algorithms to find the best tree that meets these criteria and requirements.

## Different Types of Decision Trees

![Figure 8.10](images/ufig8_10.jpg)

284. As demonstrated in the previous example, **how a node is split** is crucial to developing a good decision tree model. In data mining, decision trees are derived from data, not from common sense or business rules. Therefore, having valid splitting rules is essential to producing a decision tree model with strong predictive power. Splitting algorithms allow us to categorize different types of decision trees.

Over time, many types of decision tree algorithms have been developed. In this book, I introduce four tree algorithms that are widely used in data science and data mining projects:

*   **CART**
*   **Chi-Squared Automatic Interaction Detection (CHAID)**
*   **C5.0**
*   **QUEST**
