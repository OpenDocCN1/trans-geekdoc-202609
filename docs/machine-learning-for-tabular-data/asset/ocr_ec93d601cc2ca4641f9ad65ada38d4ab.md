# CHAPTER 2 Exploring tabular datasets

| Classifies if the example is original or synthetic | Computes the ROC AUC score for the classification |

The area under the receiver (ROC) curve, also known as the area under the curve (AUC), is a metric used to evaluate the performance of a machine learning algorithm in a binary classification problem. It measures the algorithm's ability to distinguish between positive and negative instances based on the predicted probabilities assigned to each observation. A score of 1 indicates a perfect classifier, while a score of 0.5 suggests a model that performs no better than guessing. You can learn more about this metric by consulting https://mlu.github.io/roc-auc/, from Machine Learning Repository, an education initiative to teach machine learning.

In this case, the ROC AUC is approximately 0.567, which indicates that the synthetic data is nearly indistinguishable from the original data.

In the next section, we will complete our overview of tabular data by exploring a dataset retrieved from the UCI Machine Learning Repository and Kaggle Datasets. Many of the problems quoted in the previous paragraphs will be spotted as we analyze the data, and remedies will be implemented.

# 2.9 Exploratory data analysis

Assembling the data into a data matrix by rows and columns is just the starting point of a longer process. The data is then examined, explored, transformed, and finally fed into a model. Studying and exploring data are crucial stages of the process because they give an idea of what you might have missed in the assembling phase and what can be done for your specific predictive model. Exploratory data analysis (EDA) is often associated more with the feature engineering phase—more in the case of using classical machine learning approaches. Usually, EDA is almost completely ignored when using deep learning. We want to stress that EDA shouldn't be limited to helping create features. It is an process of exploration to discover how the data can be used at its best.

EDA has a statistical flavor since it was suggested by one of the most prominent statisticians of the 20th century, John W. Tukey. In his 1977 masterpiece, Exploratory Data Analysis. In his work, Tukey claimed that statistical work does not come from simply modeling and hypothesis testing based on theoretical assumptions. According to Tukey, data means of EDA can also tell you what is possible in scientific and engineering problems and hint you at the best ways to curate your data. There are no predefined blueprints for an EDA. Still, smart usage of statistical description and tests and