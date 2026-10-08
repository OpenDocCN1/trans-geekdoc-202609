are an effective technique for many applications, such as customer segmentation, predictions, and fraud detection.

# 8.5.1 Overview of random forests as an ensemble learning approach

Multiple decision trees are randomly trained on subsets of the data using the ensemble learning technique known as random forests, and the votes from each individual tree are then combined to provide the final forecast. This approach reduces variance from an individual tree by introducing a diversity of models that have no correlation with each other. The level of randomness is adjustable and the process is iterative, so the algorithm can hone in on the most predictive variables for a data set [15]. Random forests provide a tremendous boost in accuracy compared to a single decision tree, and are widely used in areas such as recommendation systems and computer vision.

# 8.5.2 Decision tree construction and aggregation in random forests

Decision tree construction in random forests is the process of building individual decision trees that make up the forest. This process begins by randomly selecting observations from the data set to become the “root node” or “decision node.” For each node, the best split point is determined by algorithm and splitting criteria, such as information gain or a Gini index. The next step is to divide the training data into two new child-nodes, each representing a subset of the data. This process continues until each node is pure (all observations belong to the same class) or until all nodes have the same values [16]. Lastly, the algorithm builds the optimal model by pruning away nodes that do not significantly add to the accuracy of the model, and weighing the nodes based on their importance.

In Random forests, the process of aggregation entails integrating the forecasts of the various decision trees that comprise the forest. This is done by averaging the predictions made by the various trees. A consensus prediction is produced as a result of this averaging, and it is thought to be more accurate and less prone to error than predictions produced by a single tree.

# 8.5.3 Random forests algorithm and its variations

The random forests ensemble learning method builds a large number of decision trees during the training phase and outputs the class that represents the mean of the classes (classification) or mean prediction (regression) of the individual trees. Random