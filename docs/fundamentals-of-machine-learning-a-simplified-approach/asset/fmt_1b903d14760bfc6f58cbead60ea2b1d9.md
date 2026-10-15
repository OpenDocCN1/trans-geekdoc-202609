
## 9. Computational Costs of Non-Linear Kernels

Kernel Computation: Non-linear kernels like the RBF kernel can be computationally expensive because they require calculating the similarity between each pair of data points in the feature space. This results in a kernel matrix of size n×nn, which can be computationally prohibitive for large datasets.

Matrix Inversion: In some implementations of SVM (especially for non-linear kernels), matrix inversion is required during training, leading to increased computational time and complexity.

## 10. Limited Support for Online Learning

Batch Learning: SVMs are typically designed for batch learning, where the entire dataset is used for training at once. They are not well-suited for online learning or scenarios where data comes in streams.

No Incremental Learning: Traditional SVM models cannot be updated incrementally with new data. In contrast, models like logistic regression and decision trees can easily adapt to new data without retraining from scratch. This makes SVM less suitable for dynamic, real-time applications.

Exercise

1. Describe in detail all the steps involved in designing a learning system. Discuss the perspective and issues in machine learning.

2. Explain the role of genetic algorithm in knowledge-based technique.

3. Differentiate between Genetic algorithm & traditional algorithm with suitable example.

4. Explain various ANN architectures in detail.

5. Distinguish between supervised learning and Reinforcement learning. Illustrate with an example.

Unit III

DECISION TREE LEARNING

DECISION TREE LEARNING ALGORITHM

The Decision Tree Learning algorithm is a recursive process that divides the dataset into subsets based on a feature that best separates the data points at each step. The goal is to create a model that predicts the target variable by learning simple decision rules inferred from the data features. Below is an overview of the process and steps involved in the Decision Tree learning algorithm.

Steps of the Decision Tree Learning Algorithm

1. Input the Dataset:

The algorithm starts with a dataset consisting of multiple features (attributes) and a target variable (the class label for classification or a continuous variable for regression).

For classification tasks, the target variable is categorical, while for regression tasks, the target variable is continuous.

1. Check for Stopping Conditions:

All samples in the dataset have the same class label: If all samples belong to the same class, the node becomes a leaf node with that class label.

No features remain: If there are no more features to split on (or if the features no longer provide information), the node becomes a leaf node. The class label of the majority of the samples in this subset will be assigned as the label for that node.

Max Depth or Minimum Sample Size: If the decision tree has reached a predefined depth or if there are too few samples in the subset to make further splits, the algorithm stops.

1. Select the Best Feature to Split On:

The algorithm evaluates all available features and selects the one that results in the best split, which is typically based on an impurity measure or a criterion like Gini Impurity, Entropy (Information Gain), or Variance Reduction for regression.

The criteria help measure how well the data is separated after splitting on a particular feature. Some of the most common measures are:

Gini Impurity: Measures the probability of a random sample being incorrectly classified.

![](d2d_images/image024.png)

where Values(A) are the possible values of feature A, and tv​ is the subset of samples in t where feature A=v.

Variance Reduction: In regression tasks, the algorithm selects the feature that minimizes the variance in the target variable after splitting.

1. Split the Dataset:

After selecting the best feature, the dataset is split into subsets based on the values of the chosen feature.

If the feature is continuous, the split could be based on a threshold value (e.g., less than or greater than a certain value). If the feature is categorical, the dataset is split according to the distinct values of that feature.

1. Recursion:

The algorithm then applies the same process recursively to each subset (creating subtrees). For each subset, it checks the stopping conditions, selects the best feature for the next split, and continues until the stopping conditions are met.

1. Assign a Label:

Once the algorithm reaches a leaf node, it assigns a label (class label or regression value) to the node.

*   In classification, the label assigned is the majority class of the samples in that subset.

*   In regression, the label assigned is the average value of the target variable for the samples in that subset.

Decision Tree Learning Algorithm (Pseudocode)

Here’s a general pseudocode representation of the decision tree learning process:

```python
def decision_tree_learning(data, features):
    if stopping_condition(data):
        return create_leaf_node(data)
    best_feature = select_best_feature(data, features)
    tree = create_node(best_feature)
    feature_values = unique_values(best_feature)
    for value in feature_values:
        subset = filter_data(data, best_feature, value)
        subtree = decision_tree_learning(subset, features - {best_feature})
        tree.add_branch(value, subtree)
    return tree
```

Explanation of the Pseudocode:

*   stopping_condition(data): A function that checks if any stopping condition is met (all samples are the same class, no features left, etc.).

*   create_leaf_node(data): Creates a leaf node with the majority class or the average value for regression.

*   select_best_feature(data, features): This function selects the best feature for splitting based on the chosen criterion (e.g., Gini impurity or Information Gain).

*   create_node(best_feature): Creates a decision node that splits on the best feature.

*   unique_values(best_feature): Returns the unique values or thresholds for the feature.

*   filter_data(data, best_feature, value): Filters the dataset based on the value of the selected feature.

*   add_branch(value, subtree): Adds a branch for each possible value of the selected feature.

Pruning the Decision Tree

Once the tree has been fully grown, pruning is used to reduce the size of the tree and improve its generalization ability. There are two types of pruning:

1. Pre-pruning (Early Stopping):

The tree is stopped from growing early based on certain conditions such as:

*   A node has fewer than a predefined minimum number of samples.

*   A node cannot improve the model's accuracy (e.g., Information Gain is too low).

*   The depth of the tree reaches a predefined limit.

1. Post-pruning (Cost-Complexity Pruning):

*   The tree is grown fully, and then branches are removed based on their contribution to improving the model's performance (e.g., based on cross-validation).

*   This is usually done by evaluating the error rate and removing branches that lead to overfitting.

Advantages of Decision Tree Learning

*   Easy to Understand and Interpret: The structure of the tree is easy to visualize, making the model interpretable even for non-technical users.

*   Handles Both Numerical and Categorical Data: Decision Trees can work with both types of data without needing normalization or scaling.

*   Non-Linear Decision Boundaries: Decision Trees can model non-linear relationships between features and the target variable.

*   Automatic Feature Selection: The algorithm automatically selects the most relevant features at each step.

Disadvantages of Decision Tree Learning

*   Overfitting: Decision Trees tend to overfit the data, especially when the tree is deep or the dataset is noisy.

*   Instability: Small changes in the data can lead to a completely different tree.

*   Bias Toward Features with More Levels: Features with many distinct values can dominate the splitting criteria, potentially leading to biased trees.
