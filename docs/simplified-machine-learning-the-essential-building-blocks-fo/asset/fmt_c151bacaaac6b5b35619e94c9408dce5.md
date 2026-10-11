
# Classification And Regression Trees (CART)

Classification And Regression Trees (CART) is a widely used algorithm for building decision trees. It can be applied to both classification and regression tasks. The main idea of the CART algorithm is to recursively split the dataset into subsets based on the values of input features, such that the resulting subsets are as pure as possible. In classification, purity refers to having subsets where most data points belong to a single class, and in regression, it means having subsets with similar target values. The algorithm works as follows:

1.  **Feature selection**: CART selects the best feature and the best-split point to maximize the purity of the resulting subsets. It uses criteria like Gini impurity for classification and Mean Squared Error (MSE) for regression.
2.  **Splitting**: The dataset is split into two subsets based on the selected feature and split point.
3.  **Recursion**: The algorithm recursively applies the same process to each subset until a stopping criterion is met. This might be a maximum tree depth, a minimum number of data points in a node, or a predefined purity level.
4.  **Leaf node prediction**: When a stopping criterion is reached, a leaf node is created. In a classification task, the majority class in the node is assigned as the predicted class. In a regression task, the average of the target values in the node is assigned as the predicted value.
5.  **Pruning**: After the tree is constructed, it may be pruned to avoid overfitting. Pruning involves removing branches that do not significantly improve the tree's performance.

The CART algorithm can create binary trees (nodes have at most two children) or multiway trees (nodes have more than two children). It constructs the tree based on the principle of minimizing impurity or error at each split. [Code 4.4](#ch04.xhtml#cd4-4) presents how to build a decision tree using the CART algorithm:

## Code 4.4: Python code for CART

```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn.datasets import make_classification
from sklearn.tree import DecisionTreeClassifier, export_text
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score

# Generate a synthetic dataset for illustration
X, y = make_classification(n_samples=100, n_features=2, n_informative=2, n_redundant=0, random_state=42)

# Split the dataset into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Create a CART classifier
cart_classifier = DecisionTreeClassifier(random_state=42)

# Fit the classifier on the training data
cart_classifier.fit(X_train, y_train)

# Make predictions on the test data
y_pred = cart_classifier.predict(X_test)

# Evaluate the accuracy of the classifier
accuracy = accuracy_score(y_test, y_pred)
print(f'Accuracy: {accuracy:.2f}')

# Display the tree structure
tree_rules = export_text(cart_classifier, feature_names=['Feature 1', 'Feature 2'])
print("Decision Tree Rules:")
print(tree_rules)
```

Refer to [Figure 4.7](#ch04.xhtml#fig4-7) for the output of the code:

![](images/4.7.png)

Figure 4.7: Output of code 4.4

In this code, a synthetic dataset is generated using `make_classification`. The dataset is split into training and testing sets. A CART classifier is created using `DecisionTreeClassifier`. The classifier is trained on the training data and evaluated on the test data.

# Split algorithm based on information theory

The Iterative Dichotomiser 3 (ID3) algorithm is a tree induction algorithm based on information theory. It is used to construct decision trees for classification tasks. The primary idea behind ID3 is to select the features and splits that maximize the information gain or reduce uncertainty at each node of the tree.

## ID3 algorithm

An overview of the ID3 algorithm is given as follows:

*   **Entropy**: The ID3 algorithm uses a measure called entropy (H) to quantify the uncertainty or impurity of a dataset. In classification tasks, entropy is used to measure the disorder or randomness of class labels. The entropy of a dataset D with respect to a binary classification task (for example, yes/no) is defined as:

    `H(D) = -p(yes) * log2(p(yes)) - p(no) * log2(p(no))`

    Here, `p(yes)` is the proportion of positive (yes) examples in the dataset, and `p(no)` is the proportion of negative (no) examples.

*   **Information Gain (IG)**: Information gain measures the reduction in entropy achieved by partitioning the data based on a specific feature. The ID3 algorithm selects the feature that maximizes information gain at each node. The information gain for a feature F is calculated as follows:

    `IG(D, F) = H(D) - Σ((|Di| / |D|) * H(Di))`

    *   `IG(D, F)` is the information gain achieved by splitting on feature F.
    *   `|Di|` is the number of examples in the dataset that take the value Fi for feature F.
    *   `|D|` is the total number of examples in the dataset.
    *   `H(Di)` is the entropy of the subset of data for which feature F has the value Fi.

*   **Tree construction**: The ID3 algorithm recursively partitions the dataset based on the feature that maximizes information gain. The dataset is split into subsets, each corresponding to a unique value of the selected feature. The process continues until one of the stopping criteria is met, such as all examples in a node belonging to the same class or reaching a pre-defined depth limit.

*   **Leaf node labeling**: When a stopping criterion is met, a leaf node is created. The majority class label of the examples in that node is assigned as the predicted class label for that node.

*   **Attribute selection**: The algorithm selects attributes (features) to split on based on information gain, and attributes are not reused within the same path from the root to a leaf node. As a result, the constructed tree can be deeper and narrower compared to other tree induction algorithms.

It is important to note that while ID3 is a foundational algorithm for decision tree construction, it has some limitations, including its binary splits and sensitivity to small datasets. Variants like the C4.5 and C5.0 algorithms address some of these limitations and are widely used in practice. Additionally, modern tree induction algorithms like CART and Random Forests offer more flexibility and can be used for both classification and regression tasks.

Creating a full implementation of the ID3 algorithm for decision tree construction from scratch can be quite complex. However, we can provide a simplified Python example to illustrate the key concepts. This example assumes a binary classification task with categorical features. The dataset is manually defined, and no pruning is applied as presented in [Code 4.5](#ch04.xhtml#cd4-5):

## Code 4.5: Python code for Split algorithm using IDT3

```python
import math

# Define a toy dataset (features and labels)
data = [
    {'outlook': 'sunny', 'temperature': 'hot', 'humidity': 'high', 'windy': False, 'play_tennis': False},
    {'outlook': 'sunny', 'temperature': 'hot', 'humidity': 'high', 'windy': True, 'play_tennis': False},
    {'outlook': 'overcast', 'temperature': 'hot', 'humidity': 'high', 'windy': False, 'play_tennis': True},
    {'outlook': 'rainy', 'temperature': 'mild', 'humidity': 'high', 'windy': False, 'play_tennis': True},
    # ... (more data points)
]

# Function to calculate entropy
def calculate_entropy(data):
    num_data = len(data)
    label_counts = {}
    for record in data:
        label = record['play_tennis']
        if label not in label_counts:
            label_counts[label] = 0
        label_counts[label] += 1
    entropy = 0.0
    for label in label_counts:
        prob = label_counts[label] / num_data
        entropy -= prob * math.log(prob, 2)
    return entropy

# Function to split the dataset based on a feature
def split_dataset(data, feature):
    subsets = {}
    for record in data:
        value = record[feature]
        if value not in subsets:
```
