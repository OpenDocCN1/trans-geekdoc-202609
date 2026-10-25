As you've already seen, decision trees can naturally handle variables of any type without special encoding, although we did see that a local form of mean/target encoding can be used to reduce the computational burden imposed by nominal categorical splits. Nonetheless, using an encoding strategy, like OHE, can sometimes improve the predictive performance or interpretability of a tree-based model; see Kuhn and Johnson [2013, Sec. 14.7] for a brief discussion on the use of OHE in tree-based methods. Further, some tree-based software, like Scikit-learn's `sklearn.tree` module, require all features to be numeric—forcing users to employ different encoding schemes for categorical features. See Boehmke and Greenwell [2020, Chap. 3] for details on different encoding strategies (with examples in R), and further references.

# ## 2.5 Building a decision tree

In the previous sections, we talked about the basics of splitting a node (i.e., partitioning some subset of the learning sample). Building a CART-like decision tree starts by splitting the root node, and then recursively applying the same splitting procedure to every resulting child node until a saturated tree is obtained (i.e., all terminal nodes are pure) or other stopping criteria are met. In essence, the partitioning stops when at least one of the following conditions are met:

+   - all the terminal nodes are pure;
+   - the specified maximum tree depth has been reached;
+   - the minimum number of observations that must exist in a node in order for a split to be attempted has been reached;
+   - no further splits are able to decrease the overall lack of fit by a specified factor;
+   - and so forth.

This often results in an overly complex tree structure that overfits the learning sample; that is, it has low bias, but high variance.

To illustrate, consider a random sample of size \( N = 500 \), generated from the following sine wave with Gaussian noise:

```
\( Y = \sin(X) + \epsilon, \)
```

where \( X \sim \mathcal{U}(0, 2\pi) \) and \( \epsilon \sim \mathcal{N}(0, \sigma=0.3) \). A scatterplot of the data, along with the true response function, is shown in Figure 2.12.