In other words, an RF is just a bagged tree ensemble with an additional layer of randomness produced by selecting a random subset of candidate splitters prior to partitioning the data at every node in every tree—extremely randomized trees (Section 7.8.4), take this randomization a step further in an attempt to reduce variance even more. Let \( m_{try} \le p \) be the number of candidate splitters selected at random from the entire set of \( p \) features prior to each split in each tree. Setting \( m_{try} << p \) can often dramatically improve performance compared to bagged decision trees; note that setting \( m_{try} = p \) will results in an ordinary bagged tree ensemble.

That's it. That's essentially the difference between an ordinary bagged tree ensemble and an RF.

The general steps for constructing a traditional RF are given in Algorithm 7.1 (compare this to Algorithm 5.1).

The recommended default values for \( m_{try} \) (the number of features randomly sampled before each split) and \( n_{min} \) (the minimum size of any terminal node) depend on the type of outcome:

+   - For classification, the typical defaults are \( m_{try} = \lfloor \sqrt{p} \rfloor \), where \( p \) is the number of features, and \( n_{min} = 1 \).

+   - For regression, the typical defaults are \( m_{try} = \lfloor p/3 \rfloor \) and \( n_{min} = 5 \).

These default values may vary slightly from one implementation to another. Note that \( \lfloor x \rfloor \) is just \( x \) rounded down to the nearest integer. As we'll see in Section 7.4, generalization performance is typically most sensitive to the value of \( m_{try} \), but the default is usually in the ballpark, and the tuning space for \( m_{try} \) is simple since \( m_{try} \in \{1, 2, \dots, p\} \), where \( p \) is the total number of available features.

Traditionally, CART was used for the base learners in an RF, but any decision tree algorithm will work (e.g., GUIDE or CTree); I'll use CTree in Section 7.2.3 to build an RF from scratch. Also, the traditional RF algorithm used the Gini splitting criterion (2.1) for classification and the SSE splitting criterion (2.6) for regression. However, many other splitting criteria can be used to great affect. For example, Ishwaran et al. [2008] proposed several splitting rules more appropriate for right-censored outcomes, including a log-rank splitting rule that splits nodes by maximization of the log-rank test statistic; see also Segal [1988], LeBlanc and Crowley [1992].

# 7.2.1 Voting and probability estimation

The voting scheme for classification outlined in step 4) of Algorithms 5.1 and 7.1 is called hard voting. In hard voting, each base learner casts a direct vote on the class label, and a majority vote (binary outcome) or plurality