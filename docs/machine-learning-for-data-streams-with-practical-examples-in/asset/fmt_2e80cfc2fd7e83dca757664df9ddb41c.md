
# The ultra fast forest of trees (UFFT)

The ultra fast forest of trees (UFFT), developed by Gama and Medas [113], generates a forest of binary trees, one for each possible pair of classes. The trees contain a `Naive Bayes` classifier at each node, like `VFDTc`. The main difference from `VFDTc` is in the handling of numeric attributes.

UFFT uses analytical techniques to choose the splitting criteria, and information gain to estimate the merit of each possible splitting test. For multiclass problems, the algorithm builds a binary tree for each possible pair of classes, leading to a forest of trees, that comprises *k*(*k* − 1)/2 classifiers for a *k*-class problem. The analytical method uses a modified form of quadratic discriminant analysis to include different variances on the two classes.

# 6.3.5 Hoeffding Adaptive Tree

The *Hoeffding Adaptive Tree* [33] is an adaptive extension to the Hoeffding Tree that uses `ADWIN` as a change detector and error estimator. It has theoretical guarantees of performance and requires no parameters related to change control. In contrast, `CVFDT` has no theoretical guarantees, and requires several parameters with default values that can be changed by the user, but which are fixed for a given execution. It requires:

1.  **`W`**: The example window size.
2.  **`T[0]`**: Every `T[0]` examples, `CVFDT` traverses the entire decision tree, and checks at each node whether the splitting attribute is still the best. If there is a better splitting attribute, it starts growing an alternate tree rooted at this node, and it splits on the current best attribute according to the statistics at the node.
3.  **`T[1]`**: After an alternate tree is created, the following `T[1]` examples are used to build the alternate tree.
4.  **`T[2]`**: After the arrival of `T[1]` examples, the following `T[2]` examples are used to test the accuracy of the alternate tree. If the alternate tree is more accurate than the current one, `CVFDT` replaces it with this alternate tree (we say that the alternate tree is promoted).

The default values are `W = 50,000`, `T[0] = 10,000`, `T[1] = 9,000`, and `T[2] = 1,000`. We can interpret these figures as the assumptions that often the last 50,000 examples are likely to be relevant, that change is not likely to occur faster than every 10,000 examples, and that 1,000 examples will be sufficient to tell the best among current and candidate trees. These assumptions may or may not be correct for a given data source. Moreover, the stream may change differently at different times, so no single set of values may be best for all the stream.

The main differences of the Hoeffding Adaptive Tree with respect to `CVFDT` are:

*   The alternate trees are created as soon as change is detected, without having to wait for a fixed number of examples to arrive after the change. Furthermore, the more abrupt the change, the faster a new alternate tree will be created.
*   The Hoeffding Adaptive Tree replaces an old tree with the alternate tree as soon as there is evidence that it is more accurate, rather than waiting for another fixed number of examples.

These two effects can be summarized by saying that the Hoeffding Adaptive Tree adapts to the scale of time change in the data, rather than relying on the a priori guesses made by the user.

# 6.4 Handling Numeric Attributes

Handling numeric attributes in a data stream classifier is much more difficult than in a nonstreaming setting. In this section we will review the most popular methods used for *discretization* in decision trees and Naive Bayes algorithms in evolving data streams. We need to examine how to manage the statistics of numeric attributes and how to determine the best splitting points in decision trees.

We start by mentioning the methods in the nonstreaming scenario. There, the main discretization strategies are:

*   **Equal width**: The range of the numeric attribute is divided into a fixed quantity of bins of the same size. The maximum and minimum values are needed to compute the upper and lower values in the bins. This is the simplest method as it does not need to sort the data, but it is vulnerable to the existence of outliers and to skewed distributions.
*   **Equal frequency**: This strategy also uses a fixed number of bins, but each bin contains the same number of elements. For *n* values and *k* bins, the bin weight will be *n/k*, up to rounding. It is well suited for outliers and skewed distributions, but it needs more processing time, as it needs to sort the values.
*   **Fayyad and Irani's method** [98]: This is based on computing the best cut-points using information gain as it is used in decision trees. First, it sorts the data, and then each point between adjacent pairs of values is selected as a split candidate. Using information gain, the best cut-point is selected, and then the procedure continues recursively in each of the parts. A stopping criterion is needed to stop the recursive process. The criterion is based on stopping when intervals become pure, with values of one class only, or when the *minimum description length* principle estimates that dividing the numeric range will not bring any further benefit.

## 6.4.1 VFML

The very fast machine learning (VFML) package of Hulten and Domingos [137] contains a method for handling numeric attributes in `VFDT` and `CVFDT`. Numeric attribute values are summarized by a set of ordered bins. The range of values covered by each bin is fixed at creation time and does not change as more examples are seen. A hidden parameter serves as a limit on the total number of bins allowed—in the VFML implementation this is hard-coded to allow a maximum of 1,000 bins. Initially, for every new unique numeric value seen, a new bin is created. Once the fixed number of bins have been allocated, each subsequent value in the stream updates the counter of the nearest bin.

Essentially, the algorithm summarizes the numeric distribution with a histogram, made up of a maximum of 1,000 bins. The boundaries of the bins are determined by the first 1,000 unique values seen in the stream, and after that the counts of the static bins are incrementally updated.

There are two potential issues with this approach. Clearly, the method is sensitive to data order. If the first 1,000 examples seen in a stream happen to be skewed to one side of the total range of values, then the final summary cannot accurately represent the full range of values.

The other issue is estimating the optimal number of bins. Too few bins will mean the summary is small but inaccurate, whereas too many bins will increase accuracy at the cost of space. In the experimental comparison the maximum number of bins is varied to test this effect.

## 6.4.2 Exhaustive Binary Tree

Gama et al. [111] present this method in their `VFDTc` system. It aims at achieving perfect accuracy at the expense of storage space. The decisions made are the same that a batch method would make, because essentially it is a batch method—no information is discarded other than the order of values.

It works by incrementally constructing a binary tree as values are observed. The path a value follows down the tree depends on whether it is less than, equal to, or greater than the value at a particular node in the tree. The values are implicitly sorted as the tree is constructed, and the number of nodes at each time is the number of distinct values seen. Space saving occurs if the number of distinct values is small.

On the other hand, the structure saves search time versus storing the values in an array as long as the tree is reasonably balanced. In particular, if values arrive in order, then the tree degenerates to a list and no search time is saved.

## 6.4.3 Greenwald and Khanna's Quantile Summaries

The field of database research is also concerned with the problem of summarizing the numeric distribution of a large dataset in a single pass and limited space. The ability to do so can help to optimize queries over massive databases.
