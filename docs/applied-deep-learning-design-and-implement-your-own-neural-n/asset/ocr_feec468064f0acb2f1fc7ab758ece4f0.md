# Decision tree

A decision tree is a method of classification, which gives results as flow charts like tree structure where the branch of the tree represents the outcome, and the node represents the value of the attribute. The classes are represented by the tree nodes.

Let us take an example where we have to classify a cat, sparrow, and bat based on their attributes. Figure 1.29 shows the decision tree for our example:

![](bbox=[0.275, 0.254, 0.72, 0.55])

# ID3 algorithm

The main algorithm to build the decision tree is ID3. It follows a greedy, top-down search approach through possible branches. It uses entropy and information gain to build the decision tree.

# Entropy

Entropy is defined as the measure of disorder, uncertainty, or impurity of a dataset. It controls the decision of splitting the data. ID3 algorithm uses entropy to determine the homogeneity of the sample. Mathematically, entropy can be represented as follows:

```
E(S) = \sum_{j=1}^n -P_j log_2 P_j	(1.18)
```

where P_j is the probability of class j in the dataset.

# Information gain

Information gain is the measure of information given by the feature about the class. It is used to construct the decision tree. The decision tree algorithm maximizes