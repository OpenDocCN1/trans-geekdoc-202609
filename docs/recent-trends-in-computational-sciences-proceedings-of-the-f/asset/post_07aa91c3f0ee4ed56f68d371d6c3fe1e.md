
# Customer churn prediction using ensemble learning with neural networks

Kannaiah Karthikeya & Vikram Neerugatti
Department of Computer Science and Engineering, Jain (Deemed to be) University, Bangalore,
Karnataka, India
ORCID ID: 0000-0002-2203-7002

ABSTRACT: Modern-day companies have to keep in mind their immensely large customer base. Their businesses strictly deal with the masses. Companies have to maintain a record of how their product or service is reaching the people. And to know Customer Behavior are going to determine respect to the product or the service provided. This vital piece of information will give understanding about customer's interests aligned with respect to the product or the service provided. Companies have to keep an eye on customers leaving. Churn Rate is a measure vital to understand the growth or fall of a company. Predicting customers who are willing to churn even before they are going to be is quite remarkable. Based on prediction, companies now can target and work better on customers predicted to leave. This prediction suggests an Ensemble Learning Model using Neural Networks. Three models of Neural Networks will share their prediction and the most occurred prediction is selected to be the final prediction. Proposed model scored 84% accuracy which is a decent improvement over individual model.

*Keywords:* customer churn, churn rate, ensemble learning, neural networks & prediction

# 1 INTRODUCTION

Churn depicts turnover of customers. Customers are assets to the growth of companies. Losing an existing customer is a situation that a company should not be in. Getting new customers means a lot of customer acquisition costs. Getting in good with unsatisfied customer by providing valuable service. Customers are a very valuable asset especially to the companies which are customer dependent as the Telecom industry [1]. Customer Churn is a situation where customers are willing to change from services of one company to another [2]. With advancements in big data, customer-centric organizations like banks have faced unexpected challenges and competition [3]. Not only banks but this can be related to any sector that deals with large customers. Organizations from these kinds of sectors usually have a methodology/system to manage customers. Customer relationship management systems play a role in developing and acquiring new customers and also maintaining a healthy relationship with the customers. Churn prediction plays a vital role in this instance as it gives predicted churners on when this management system can work upon and retain the customer.

Data is crucial in churn prediction. When dealing with prediction problems we may think that the more the data the better it is actually relevant to the cause the merit is to solve the problem. Careful inspection of data can filter useful features that have the benefit of being useful in terms of having to be an independent feature dependable for the problem. Usually in this field of customer churn, we have very less data on churners. In this paper, we will see some put related to data. This paper proposes an ensemble learning model using neural networks. This model is used to predict potential churners by taking votes and the most voted solution wins and becomes the final prediction by ensemble model. Our model predicts if a customer churns or not. It is a binary classification problem. The remaining parts of this paper will feature 5 sections. In Section II features Literature Review of relevant work related to customer churn. Section III Section IV, Implementation methodology is given. In Section V, Results will be featured along with commentary. Finally in Section VI, Conclusion and Future Scope have been discussed.

# 2 LITERATURE REVIEW

This section features findings of relevant works carried out by enthusiasts relevant to this problem.

A paper by Sankrawal et al [5] features a multi-layer neural network model. Deep learning techniques have been used on a telecom dataset. Their model scored a accuracy of 80.03%. Their paper describes Customer behavior analysis and features which are to be kept in mind. Analysis draws correlations and helps understanding features.

Seyed Jamal Haddadi et al. [6] This paper uses the concept of time-series DNNs based on customer retention approach. Processed data is featured to Bi-LSTM network model. This proposed model showed significant improvement in comparison to other models over traditional ML techniques. This proposed model scored a promising accuracy of 84%. This paper is useful for using the telecom dataset.

Shisha Bhardwaj et al. [7] features two models for customer churn prediction on the 77.52% accuracy and a second model is Multi-Layer Perceptron (MLP) scores 94.19% accuracy. MLP features three hidden layer architectures with a learning rate of 0.01. Predictive models of this paper are used in consulting market research.

Jasmi Lathee and Vineetha S a paper on customer churn prediction which features a LSTM model and SMOTE processing for an imbalanced dataset. Their model scored an accuracy of 88%. Accuracy found to be better SMOTE technique. Framework provided by the paper is useful for organizations to discover clients who are likely to churn [4]. This paper done by Pushkar Bhuse et al [8] describes various classifiers up to using Random Forest Classifiers. In comparison, Random Forest worked well over other models. Scoring an accuracy Other models are Ridge Classifier, XGBoost, KNN Classifier, Support Vector Classifier (SVC), and Deep Neural Network. This paper is used as telecom dataset.

A comparative study by Pradeep Singh et al [9] explores models used in around ten papers. Their findings show that Random Forest was best in comparison to basic classification models and Importance of feature engineering in helping performance of the model. Amany Zaky et al. [10] attempts a single layer Artificial Neural Network. Bank dataset is used in this paper. The model scored an accuracy 87%. The proposed network is said to be a effective method for bank organizations to maintain bank customers and help retain them, Paper by Aisyah Larasati et al. [11] discusses optimizing the ANN model to predict better. It is found that the churn percentage is 36.4% and an accuracy of 76.38%.

Xuan et al. [12] features a model that combines prediction results and This paper uses a dataset. shows an amazing accuracy of 98.87%.

# 3 PROPOSED MODEL

## 3.1 Neural networks

Neural Networks are inspired by the Human brain. They try to mimic the function of neurons in the human brain. Deep learning is a concept where more than one layer can be constructed. This is because of scope and advancements [11]. This paper introduces three models. First model (MODEL-1) is trained on an unbalanced dataset. The Second (MODEL-2) and third model (MODEL-3) are trained on a balanced dataset. Section has information about how the dataset is balanced. While the Third model is a single layer Neural network. This paper implements neural networks using TensorFlow and Keras library [13,14].

## 3.2 Ensemble learning

Ensemble learning is a machine learning concept dealing with use of multiple learning algorithms. Better models used. In ensemble learning, predictions generated by all constituent models are considered in final decision making. Every model has its own hypothesis to form hopefully a better hypothesis [15]. In this paper, predictions of all three models are considered. As we are dealing with a binary classification problem where decision is either “0” or “1”, we suppose we have two models predicted to be “0” and another model predicted to “1”. As prediction “0” is the most popular vote so “0” will be a prediction. We achieve this system by adding all three predictions and then if the sum is greater than (2 or 3) then “1” will be a prediction. If the sum is either 0 or 1 then prediction is to be “0” means customers will not churn or “1” means customer will churn.

## 3.3 Evaluation

Evaluating models is a process where one can understand how the model is performing. Evaluation measures help us this. This paper uses four measures. These measures are Accuracy(A), Precision(P), Recall(R) and F1-score (F1). You can refer to these measures in this paper [10]. A confusion matrix can be used to help calculate these measures as shown in Table 1.

Table 1. Confusion matrix.

| | Predicted (0) | Predicted (1) |
|---|---|---|
| Actual (0) | True Positive (TP) | False Negative (FN) |
| Actual (1) | False Positive (FP) | True Negative (TN) |
