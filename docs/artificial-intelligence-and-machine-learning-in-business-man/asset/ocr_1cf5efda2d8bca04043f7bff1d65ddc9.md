# Employee Churn Management Using AI

the performance of the model or X_test is the unseen data which helps us to know the accuracy and performance of the model.

There is no strict convention of how much data will go for training and how much will go for testing.

```
x_train, x_test, y_train, y_test - train_test_split(X_scaled, y, test_size=0.25, random_state=1)
```

In our case we have taken 75% of the data for training and 25% of data for testing. Now it's the time for model building using different Machine Learning algorithms.

# 11.3.2 MODEL BUILDING

# K Nearest Neighbour

KNN is a nonparametric regulated learning calculation that makes the model structure from the given dataset. In KNN, k is a number that chooses the number of closest neighbours are utilized to get the best outcome to the dataset. Let 'a' is point mark is to be anticipated first, we need to discover the K nearest point close to 'a'. At that point, it forms a specific class closest information [4]. The different classes can be formed on several available algorithms such as Euclidean separation, Hamming separation, Manhattan separation etc. Finding the best k for the informational index is a difficult undertaking. For informational collection k esteem is unique. In any case, some supposition says k esteem is an odd number that is very important. We can say that the accuracy of k is the controlling parameter for the issue. Examination that in the event that we take k as a lesser number, at that point might prompt overfitting; choosing proper k value is very otherwise it will have a greater effect on the real forest [5]. In the event that we take a bigger estimation of k, at that point it k. We can locate the ideal estimation by playing out our procedure on the informational collection by utilizing diverse k. The k esteem gives the best outcome will be that for specific informational collection.

After applying the KNN we tested the training data and achieved accuracy of 0.96888623210952, but when we tested the model with the unseen data (the test data set which are already prepared before the model creation), we got accuracy of 0.95266666666667.

Next, we applied hyperparameter tuning techniques to improve the performance of the model. For that used GridSearchCV which is in Sklearn module. It gives us a set of parameters which can give us better accuracy. After getting a best set of parameters we again trained the model with these best parameters and it with trained dataset and got an accuracy of 0.9799093252733576 which is more than previous set of parameters which was used before. Now we tested the model again with unseen data which gives us an accuracy of 0.95866666666666667 which is also better than previous.

Hence, after hyperparameter tuning we got slightly high accuracy without that.