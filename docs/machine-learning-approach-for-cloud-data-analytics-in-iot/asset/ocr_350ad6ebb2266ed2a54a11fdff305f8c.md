![](bbox=[0.13, 0.1, 0.89, 0.18])

**Figure 3.3** General framework of proposed model for predictive data analytics.

are basic algorithms for any predictive model. Boosting algorithms trains a model in a sequential and gradual manner. These algorithms perform both classification and regression. Boosting algorithms basically aim to identify weak learners which further can be improvised so as it turns to be a strong learner. Gradient boosting and AdaBoost are the two popularly used boosting algorithms. These two boosting algorithms basically differ in identification of weak learners. Weak learners are identified based on error rate. Error rate depends on the parameters to be optimized. For instance, if a model tries to predict sales, then error rate will be difference in predicted sale and actual sale.

Random forest regression may also be employed for prediction problems as it performs classification and regression. Random forest regression employs some classification criteria to classify data. Thereafter, qualities of this split are measured using mean squared error or mean absolute error. It employs the concept of averaging to improve accuracy of prediction.

Authors in the chapter propose usage of bootstrap aggregating ML algorithm also referred to as bagging algorithm. Bagging algorithm aims to improve efficiency and accuracy of ML algorithms by reducing the variance. Usage of bagging algorithm advocates achievement of efficient and accurate predictive model. The accuracy of proposed model increases rapidly over time.

# ## 3.4.1 Case Study

For the sake of illustration of implementation of AI in retail industry, authors in the chapter consider a case study. Similarly, authors have taken a dataset pertaining to a retail store. This dataset comprises of observation for duration of 4 years from 2011 to 2015. This dataset has been taken from kaggle (https://www.kaggle.com/jr2ngb/superstore-dataseturname: jr2ngb). The considered dataset has 16 variables. Out of these 16 features, 10 are categorical features, 5 are numerical features, and 1 is date feature as follows.