# 11.3.3.2 Naïve Bayes Classifier

Bayes’ theorem (also known as Bayes’s rule after Thomas Bayes) links the conditional and marginal probabilities of two random occurrences in probability theory. It’s frequently used to calculate posterior probabilities based on data. The term “Naïve Bayes classifier” refers to a rudimentary probabilistic classification based on Bayes’s theorem [39, 40].

# 11.3.3.2.1 Bayes’s Theorem:

$P(A / B) = \frac{P(B|A) \times P(A)}{P(B)} , where A, B = events$
$P(A|B) = $ probability of occurrence of $A$ given $B$ is true.
$P(B|A) = $ probability of occurrence of $B$ given $A$ is true.
$P(A), P(B) = $ the independent probabilities of $A$ and $B$.

A Naïve Bayes classifier assumes that the presence (or absence) of a particular characteristic of a class has no effect on the presence (or absence) of any other feature. The Naïve Bayes classifier has the benefit of only having a small quantity of training data to estimate the parameters (variable means and variances) required for classification [41, 42].

In this research, the addition of the probabilistic approach of Naïve Bayes in the model enhances the chances of getting predicted data more accurately.

# 11.3.3.3 Decision Tree

A Decision Tree is a graph that illustrates every feasible outcome of a decision using a branching strategy. To resolve those categorization issues, the Decision Tree technique is more powerful. This approach has two steps: creating a tree and applying the tree to the dataset [43, 44].

Here, the Gini Index algorithm [45] among all Decision Tree methods is chosen for this chapter. The Gini Index is a crucial criterion for building decision trees. It is a function that measures how well a decision tree is split. Essentially, it assists us in determining which splitter is optimal so that we can construct a pure decision tree. This measure has a value between 0 and 0.5. The purpose of using Gini impurity is to optimize the split and to develop a better ensemble algorithm using a pure decision tree [46].

# 11.3.3.4 Support Vector Machine

Support Vector Machine is supervised learning used for regression [47] or classification [48]. The Support Vector Machine model is an appropriate