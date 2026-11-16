# 8.2.2.3.2 LASSO Regression

A form of standardized regression that complements a penalty to the model for large coefficients, efficiently driving fewer significant feature coefficients to zero. This technique is beneficial in linear models and is frequently favored when handling highly correlated features.

# 8.2.2.3.3 Tree-Based Methods (e.g., Random Forests)

Random forests and other collective tree-based methods rank features on their influence in minimizing impurity in the model. These methods are reliable and capable to handle both linear and non-linear relationships between target and features (Guyon & Elisseeff, 2003; Tibshirani, 1996).

Using a blend of univariate and multivariate methods can improve model performance by primarily filtering unrelated features and then refining the selection by investigating interactions, producing a more robust feature set for training machine learning models.

# 8.2.3 HYBRIDIZED MULTI-FEATURE SELECTION

Hybridized multi-feature selection is a progressive feature selection technique in machine learning that influences the strengths of multiple techniques to improve the feature subset and advance model performance. This approach combines methods such as wrapper, filter, and embedded techniques to provide a more thorough and effective feature selection process. Hybridized selection is particularly valuable in multifaceted datasets where a single method might not cover all relevant patterns.

# 8.2.3.1 Key Components of Hybridized Multi-Feature Selection

# 8.2.3.1.1 Combining Techniques

A hybrid approach integrates numerous feature selection approaches to improve the feature set. For example, combining a filter method like a wrapper technique like recursive feature elimination (RFE) with correlation-based feature selection can assist in removing unrelated features based on correlation, then further reduce the set based on model performance. This layered selection approach takes benefit of the speed and efficiency of filter methods for initial filtering and the accuracy of wrapper methods for more sophisticated selection (Liu & Yu, 2005).

# 8.2.3.1.2 Consensus Approach

Features are selected by combining outcomes from multiple feature selection techniques, creating a consensus set in this method. Different consensus approaches include the following:

# 8.2.3.1.2.1 Voting

This strategy includes choosing features that are often identified as significant across diverse methods. Features that appear recurrently across wrapper, filter, and embedded techniques are considered reliable and robust, as they consistently display significance irrespective of the selection approach. Voting is a simple method to build a reliable feature subset, particularly when combining varied techniques (Saey et al., 2007).