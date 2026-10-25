that **rpart** is extendable^k and several R packages on CRAN extend **rpart** in various ways. For example, **rpartScore** [Galimberti et al., 2012] can be used to build classification trees for ordinal responses within the same CART-like framework, and **rpart.LAD** [Dlugosz, 2020] can be used to fit regression trees based on _least absolute deviation_ [Breiman et al., 1984, Sec. 8.11]. The **treemisc** package provides some utility functions to support **rpart**, for example, to implement pruning based on the 1-SE rule (Section 2.5.2.1). The R package **treevalues** [Neufeld, 2022] can be used to construct confidence intervals and _p_-values for the mean response within a node or the difference in mean response between two nodes in a CART-like regression tree (built using the package **rpart**); see [Neufeld et al., 2021] for details.

CART-like decision trees are implemented in many other open source languages as well. Scikit-learn's **sklearn.tree** module offers extensive decision tree functionality

The following examples illustrate the basic use of **rpart** for building decision trees. We'll confirm the results we computed manually in previous sections as well as construct decision trees for new data sets.

An excellent case study using decision trees in R to identify email spam is provided in Nolan and Lang [2015, Chapter 3].

# ## 2.9.1 Example: Swiss banknotes

In Section 2.2.2, I restricted my attention to just two predictors, top and bottom, and walked through the steps of constructing a two-split tree by hand (i.e., a tree with three terminal nodes). Here, I'll use the **rpart** package to reconstruct the same tree and to confirm my previous split calculations.

By default, **rpart** uses the Gini splitting rule, equal misclassification costs, and the observed class priors^n when building a classification tree; hence, we do not need to set any additional arguments (we'll do that in the next section).

^k As described in the “User Written Split Functions” vignette; see `vignette("usercode"

^l https://github.com/bensadeghi/DecisionTree.jl.

^m Spark has various interfaces, including R and Python; an example using R will be given in Section 7.9.5.

^n Note that the balanced nature of these data is not very realistic, unless roughly half the Swiss banknotes truly are counterfeit. However, without any additional information about the true class priors, there’s not much that can be done here.