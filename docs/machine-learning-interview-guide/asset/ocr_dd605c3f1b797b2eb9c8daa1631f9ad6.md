# Question 8: Discuss the impact of changing hyperparameters like max depth or min samples per leaf on decision tree performance.

Answer: Changing hyperparameters in decision trees, such as max depth or min samples per leaf, can significantly impact the model's performance by:

+   - **Max depth**:
+     - **Increase**: The trees with more depth might reveal more intricate patterns in the data at the cost of overfitting, which is dangerous for the small training dataset.
+     - **Decrease**: The generalization might be better, but it may also over-simplify the model, which might sacrifice the accuracy.
+   - **Min samples per leaf**:
+     - **Increase**: A higher value respectively results in a higher constraint on the size of the leaves, which may reduce overfitting and increase generality.
+     - **Decrease**: Smaller values can cause overly fine partitions of the data, which contain noise and overfitting the data.

Their values are specific to the targeted dataset and defined by the choice between two extremes that prevent underfitting or overfitting of the model.

# Question 9: Explain the difference between a pre-pruned and post-pruned decision tree.

Answer: In the pre-pruned decision tree, the early stop criteria pause a tree’s construction midway and adds that the use of criterion X does not meet certain conditions. It determines the splitting of a node depending on the maximum depth, minimum instances per terminal node, or