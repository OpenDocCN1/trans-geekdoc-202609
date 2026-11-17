learning algorithm SVM is appropriate. This approach performs admirably in both high- and low-dimensional spaces. Drawing a line or plane is necessary to divide the data points. This technique works well for prediction, text categorization, and pattern recognition. We employ it in our proposed strategy to classify the supplied set of emails into two classes: spam and ham, because of its rapid functioning nature. Drawing a proper hyperplane that yields a maximal margin allows for this separation.

The multinomial model Naïve Bayes classifier is constructed for the training dataset, which classifies emails as either spam or ham. The MNB classifier is capable of efficiently classifying text. The word counts or word frequencies are the input required for this MNB classifier.

The Gaussian Naïve Bayes model is then constructed for the training dataset. The provided email set is once more divided into spam and ham categories. The continuous values for each class are dispersed using a Gaussian distribution. Take note that continuous data is used by this classifier. Once more, test data are categorised as spam or ham using the pre-built Gaussian Naïve Bayes model.

The Bernoulli Naïve Bayes algorithm is the next classifier, which functions similarly to multinomial Naïve Bayes. The predictors are used as Boolean variables by the Bernoulli method, which is the only difference. Put differently, the parameter values are either yes or no, and we go on to the class variable prediction.

The training dataset is used to build the classifier model using the Bernoulli Naïve Bayes algorithm. To classify emails in the test dataset, the same model is also used. There is also a comparison between the four classifiers’ accuracy levels. SVMs are shown to provide the best degree of accuracy.

# 2.4 Results and Discussions

# 2.4.1 Machine Learning Algorithms with RBSA and SBFS Algorithms

Eighty percentage of the training dataset has been considered for building classification models using all the four classifiers. Once the model is built