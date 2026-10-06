# 11

# Machine Learning with mlr3

Machine learning (ML) is a broad term that covers a wide range of bioinformatic and data science activities including, regression, classification, and data clustering.

The mlr3 package is an open source ML framework for the R programming language. It is designed to provide a unified and efficient interface for building, evaluating, and comparing ML models. mlr3 is built on top of the mlr package, which is one of the most popular ML packages in R.

mlr3 follows a modular design, which means that different components of the ML process, such as data preprocessing, feature selection, model training, and model evaluation, are separated into individual objects. This design allows for greater flexibility and modularity, enabling users to customize and extend the functionality of the framework. We will look at this framework through consecutive classification and test steps in this chapter.

In this chapter, we will cover the following recipes:

+   - Defining a task and learner to implement k-nearest neighbors (k-NN) in mlr3
- Testing the fit of the model using cross-validation
- Using logistic regression to optimize parameters in a model to classify based on the relative likelihoods of two outcomes
- Classifying using random forest and interpreting it with iml
- Dimension reduction with PCA in ml3 pipelines
- Creating a tSNE and UMAP embedding
- Clustering with k-means and hierarchical clustering