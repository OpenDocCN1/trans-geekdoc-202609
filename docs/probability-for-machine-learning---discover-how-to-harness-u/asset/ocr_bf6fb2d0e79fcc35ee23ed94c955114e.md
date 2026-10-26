This can be stated formally as follows:

$$I(X;Y) = KL(p(X,Y)\|p(X) \times p(Y)) \tag{24.7}$$

Mutual information is always larger than or equal to zero, where the larger the value, the greater the relationship between the two variables. If the calculated result is zero, then the variables are independent. Mutual information is often used as a general form of a correlation coefficient, e.g. a measure of the dependence between random variables. It is also used as an aspect in some machine learning algorithms. A common example is the Independent Component Analysis, or ICA for short, that provides a projection of statistically independent components of a dataset.

# ## 24.6 How Are Information Gain and Mutual Information Related?

Mutual Information and Information Gain are the same thing, although the context or usage of the measure often gives rise to the different names. For example:

+   - Effect of Transforms to a Dataset (*decision trees*): Information Gain.
+   - Dependence Between Variables (*feature selection*): Mutual Information.

Notice the similarity in the way that the mutual information is calculated and the way that information gain is calculated; they are equivalent:

$$I(X;Y) = H(X) - H(X|Y) \tag{24.8}$$

and

$$IG(S,a) = H(S) - H(S|a) \tag{24.9}$$

As such, mutual information is sometimes used as a synonym for information gain. Technically, they calculate the same quantity if applied to the same data. We can understand the relationship between the two as the more the difference in the joint and marginal probability distributions (mutual information), the larger the gain in information (information gain).

# ## 24.7 Further Reading

This section provides more resources on the topic if you are looking to go deeper.

# ### 24.7.1 Books

+   - *Information Theory, Inference, and Learning Algorithms*, 2003.  
+     https://amzn.to/2KfDDF7
+   - *Machine Learning: A Probabilistic Perspective*, 2012.  
+     https://amzn.to/2xKSTCP