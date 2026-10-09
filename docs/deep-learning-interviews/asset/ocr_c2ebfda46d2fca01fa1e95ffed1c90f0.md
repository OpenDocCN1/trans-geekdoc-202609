# 4.3.4 	 Classification and Information Gain

# **SOL-86 🖋 CH.SOL- 4.20.**

*The three most widely used methods are:*

+   1.

$$\textit{Entropy}\left(t\right)=-\sum_{i=0}^{c-1} p(i|t) \log _{2} p(i|t). \tag{4.23}$$

+   2.

$$\text{Gini}(t)=1-\sum_{i=0}^{c-1}[p(i|t)]. \tag{4.24}$$

+   3.

$$\textit{Classification error}\left(t\right)=1-\max _{i}\left[p(i|t)\right]. \tag{4.25}$$

# **SOL-87 🖋 CH.SOL- 4.21.**

*In a decision tree, the attribute by which we choose to split is the one with **[maximum]** information gain .*

# **SOL-88 🖋 CH.SOL- 4.22.**

*TBD*

# **SOL-89 🖋 CH.SOL- 4.23.**

+   *1 	 *Information gain is the expected reduction in entropy caused by partitioning values in a dataset according to a given attribute .*

+   *2 	 *A decision tree learning algorithm chooses the next attribute to partition the currently selected node, by first computing the information gain from.*