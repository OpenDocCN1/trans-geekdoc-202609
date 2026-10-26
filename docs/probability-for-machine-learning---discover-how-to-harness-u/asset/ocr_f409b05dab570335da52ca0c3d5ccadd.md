```
Information Gain: 0.117 bits
```

Listing 24.9: Example output from calculating information gain for two splits of a dataset.

# 24.4 Examples of Information Gain in Machine Learning

Perhaps the most popular use of information gain in machine learning is in decision trees. An example is the Iterative Dichotomiser 3 algorithm, or ID3 for short, used to construct a decision tree.

Information gain is precisely the measure used by ID3 to select the best attribute at each step in growing the tree.

> — Page 58, Machine Learning, 1997.

The information gain is calculated for each variable in the dataset. The variable that has the largest information gain is selected to split the dataset. Generally, a larger gain indicates a smaller entropy or less surprise.

Note that minimizing the entropy is equivalent to maximizing the information gain ...

> — Page 547, Machine Learning: A Probabilistic Perspective, 2012.

The process is then repeated on each created group, excluding the variable that was already chosen. This stops once a desired depth to the decision tree is reached or no more splits are possible.

The process of selecting a new attribute and partitioning the training examples is now repeated for each non terminal descendant node, this time using only the training examples associated with that node. Attributes that have been incorporated higher in the tree are excluded, so that any given attribute can appear at most once along any path through the tree.

> — Page 60, Machine Learning, 1997.

Information gain can be used as a split criterion in most modern implementations of decision trees, such as the implementation of the Classification and Regression Tree (CART) algorithm in the scikit-learn Python machine learning library in the DecisionTreeClassifier class for classification. This can be achieved by setting the criterion argument to ‘entropy’ when configuring the model; for example:

```
# example of a decision tree trained with information gain
from sklearn.tree import DecisionTreeClassifier
model = DecisionTreeClassifier(criterion='entropy')
...
```

Listing 24.10: Example of defining a DecisionTreeClassifier classifier to use information gain.