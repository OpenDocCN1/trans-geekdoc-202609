can detect boundaries in nonlinear domains. kNN is a simple model that uses the neighbors for classification. The abovementioned strengths are combined to make a powerful ensemble classification method. The ensemble classification produces an accuracy of 88.52%. The study proves that integrating multiple models can be achieved in powerful, reliable models.

The detection of disease in a patient needs more powerful medical devices, which sometimes come at a high price, and this makes many small hospitals difficult to purchase. The use of machine learning models can detect disease without the need for powerful devices. However, these machine learning models face another problem called the class imbalance problem. A class imbalance problem is one where the number of instances in one class is relatively greater than the number of instances in another class in the training set. This problem reduces the ability of a machine learning classification model to identify patterns in the dataset. The use of ensemble learning overcomes the class imbalance problem and outlier detection [7].

AlJame et al. [8] use XGBoost as an ensemble learning approach. The missing values in the dataset are imputed using the kNN method, the outliers are fixed using the isolation forest method. The number of instances in the positive and negative classes in the dataset of 5,644 instances is 5,085 and 559, which indicates that the dataset is a pure imbalance dataset. The SMOTE method is used to create a new balanced dataset with an equal number of instances in both classes. The proposed ensemble method, XGBoost, outputs an accuracy of 99.9%. The authors compared their work with the other works in their literature and concluded with promising results.

Senthilkumar and Prabhusundhar [9] use a recursive feature elimination technique to improve classification performance. The imbalanced dataset is converted to a proper dataset with an even number of instances in all classes using the modified SMOTE method. Many classification models were used by the authors, and they found that XGBoost is the one that produces the best results with an accuracy of 95.6%.

# 3 Background

In this section, we briefly talk about the four methods of ensembling used in classification, which are bagging, boosting, voting, and stacking.

# 3.1 Voting

The voting-based ensemble method is the simplest way to combine multiple models to create a powerful single model [10]. The output of different classifiers is used for aggregation to reach a consensus prediction [11]. There are two types of voting known as hard voting and soft voting [12].