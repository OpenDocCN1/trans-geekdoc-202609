# CHAPTER 21

# Nearest Neighbours

Nearest neighbours algorithms are popular with data exploration and pattern recognition. In this chapter, we cover the foundation of the nearest neighbours techniques and present three particular algorithms. These methods are by definition model free. We only need to impose mild – or no – assumptions on the data. The outcome is fully derived from the data set itself. The inevitable consequence of this is the blackbox nature of the model. We can barely introduce a narrative for the link between independent and dependent variables without looking into the raw data set.

The nearest neighbour-based algorithms are quite successful in classification problems. They can be used for regression, but the power of the algorithm is not as good as it is with classification. In particular, high-dimensional problems are challenging for nearest neighbour-based regressions. A regression is thus better to run with other methods discussed in this book, such as linear regression (with regularisation), trees/forests, or neural networks.

In this section, we present three specific algorithms based on the principles of nearest neighbours and implement them in q:

+   - k-nearest neighbours classifier
- Prototype clustering
- Feature selection based on the local nearest neighbourhood

# 21.1 k-NEAREST NEIGHBOURS CLASSIFIER

The first method of the machine learning approach we present is the k-nearest neighbours, or KNN, one of the most simple and basic machine learning algorithms. The kNN is a non-parametric method for classification and/or regression of the data. For the object we want to classify or for which we want to regress the characteristic value, we use voting based on the set of objects from the nearest neighbourhood.

The kNN is very simple in terms of no model being inferred from the data, and computation is postponed. Whenever the inference has to be drawn, the entire training set is used, and the neighbour is identified. Therefore, the method itself is intensive in terms of computational resources needed to deal with the full training data set when the problem at hand requires extensive data, both in cross-sectional dimension and number of

419

Machine Learning and Big Data with kdb+/q First Edition. Jan Novotny, Paul A. Bilekorn, Ari Galiotos and Frédéric Délize.
© 2020 Jan Novotny, Paul A. Bilekorn, Ari Galiotos and Frédéric Délize. Published in 2020 by John & Sons, Ltd.