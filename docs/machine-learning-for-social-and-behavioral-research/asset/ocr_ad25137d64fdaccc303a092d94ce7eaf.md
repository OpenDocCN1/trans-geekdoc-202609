# Decision Trees

FIGURE 5.6. Terminology for each node.

![](bbox=[0.284, 0.203, 0.715, 0.427])

In the first, the first (topmost) node is termed the *root node*, while each additional node that is then further split is referred to as an *internal node*. Finally, those nodes that are not further split (bottommost) are referred to as *terminal nodes*. We have already described the splitting functions (rules) that dictate where people are placed. Note that there are alternative terminologies used to describe the parts of the tree. One alternative is the use of *parent* and *child* nodes, used in a relative way to describe splitting cases in the parent node that results in two child nodes. Lastly, the terminal nodes also referred to as the *leaves of the tree*

# 5.3.1 Example 2

The process that can be used for decision trees and categorical outputs (classification trees) applies to continuous outcomes (regression trees). To portray this and take it a step further in understanding the mapping between predictor and response, we will use data from the ECLS-K. For this example, we will use math and general knowledge to predict science scores in the eighth grade. To get a better sense of the relation-