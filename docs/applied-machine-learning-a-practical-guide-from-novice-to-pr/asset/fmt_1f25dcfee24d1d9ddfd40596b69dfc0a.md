
ca: Number of major vessels (0-3) colored by fluoroscopy.

thal: Thalassemia (1 = normal; 2 = fixed defect; 3 = reversible defect).

Target: 0 indicates the patient's heart is healthy, while 1 indicates the patient's heart is not healthy.

The hospital hired Ade with the primary responsibility of developing a machine learning model to predict the presence of heart disease in patients. Following this, he will collaborate with the front-end development team to create the XYZ Breast Heart Prediction Model.

Patients will input parameters from their device readings into the portal. The self-diagnosis results will display as 0, indicating no presence of heart disease, or 1, indicating the presence of heart disease. If the outcome is 1, patients will be advised to schedule an appointment with the hospital to consult with a specialist.

Implementing this model will help:

Reduce the pressure on hospital staff by streamlining the diagnostic process.

Manage hospital resources more effectively, ensuring that appointments are evenly distributed among available consultants.

Inform decisions about hiring or engaging additional breast cancer specialists as needed.

Note: accuracy_score is a metric used to evaluate the performance of a classification model. It measures the proportion of correctly classified instances out of the total instances.

You can download the dataset for classification via this link: [Heart Disease](https://www.google.com/url?q=https://www.kaggle.com/datasets/arezaei81/heartcsv&sa=D&source=editors&ust=1720099681834178&usg=AOvVaw2Ogt5nu6dVZIvv1V3Km2mc)  

The dataset 'heart.csv' includes data pertaining to heart issues, with a target class indicating whether a patient is diagnosed with heart disease (1) or not (0). Our objective is to apply various machine learning classification models to the data and select the model with the highest accuracy score.

# Logistic Regression 

Logistic regression is a statistical technique used to solve binary classification problems. In binary classification, the outcome variable is categorical with only two classes. Despite its name, logistic regression is primarily used for classification tasks rather than regression. It is particularly useful when the dependent variable is binary, meaning it can have only two possible outcomes, such as 0 or 1, Yes or No, or True or False.

The source code is available here: [Logistic Regression](https://www.google.com/url?q=https://github.com/anyasorc/appliedml/blob/main/Classification_Logistic_Regression%2520\(1\).ipynb&sa=D&source=editors&ust=1720099681835062&usg=AOvVaw1h_ACip0MOpvZdDW-X_rRp)  

# Import Libraries

Figure 3-1  shows all the imported required libraries

![](OEBPS/image_rsrc54H.jpg)

Figure 3-1.

# Import and View Data

Figure 3-2  shows how data was imported and viewed as seen below.

![](OEBPS/image_rsrc54J.jpg)

Figure 3-2.

# Assign values to X and y

X = df.iloc[:, :-1].values:

This line selects all rows and all columns except the last one from the DataFrame df and converts the result into a NumPy array. The resulting array X typically contains the features or predictors as seen in Figure 3-3 .

y = df.iloc[:, -1].values:

This line selects all rows and only the last column from the DataFrame df and converts the result into a NumPy array. The resulting array y typically contains the target or response variable as seen in Figure 3-3 .

![](OEBPS/image_rsrc54K.jpg)

Figure 3-3.

# Splitting into train and test set

We must divide our dataset into training and testing sets. Employing an 80:20 split, 80% of the data will train the model, and the remaining 20% will assess its performance on unseen data. Figure 3-4  visually demonstrates this process.

![](OEBPS/image_rsrc54M.jpg)

Figure 3-4.

# Standardizing the data

In the context of machine learning, particularly when using algorithms that are sensitive to the scale of the input data, it is common to standardize the data. Standardization transforms the data such that it has a mean of zero and a standard deviation of one. Figure 3-5 illustrates how to implement it.

![](OEBPS/image_rsrc54N.jpg)

Figure 3-5.

# Code Explanation

The code snippet in Figure 3-5  uses the `StandardScaler` class from the `scikit-learn` library to standardize features by removing the mean and scaling to unit variance. This process is essential for many machine learning algorithms to perform optimally. Here's an explanation of each line:

sc = StandardScaler(): This line creates an instance of the `StandardScaler` class. The `StandardScaler` is used to standardize the features of the dataset.

X_train = sc.fit_transform(X_train):

fit_transform: This method first calculates the mean and standard deviation of the `X_train` data (this is the `fit` part).

It then uses these statistics to standardize `X_train` by subtracting the mean and dividing by the standard deviation for each feature (this is the `transform` part).

The result is that `X_train` is now a standardized version of the original training data, where each feature has a mean of 0 and a standard deviation of 1.

X_test = sc.transform(X_test):

transform: This method uses the mean and standard deviation calculated from the `X_train` data to standardize `X_test`.

This ensures that the test data is transformed in the same way as the training data, which is crucial for the consistency of the model's performance.

X_test is now a standardized version of the original test data, following the same scale as `X_train`.

Here's a bit more detail on why standardization is important:

Consistency: It ensures that the training and test data are on the same scale, which is crucial for the performance of many machine learning models.

Algorithm Performance: Algorithms like gradient descent used in logistic regression or neural networks converge faster with standardized data.

Improved Accuracy: Some algorithms, like support vector machines (SVM) and k-nearest neighbors (KNN), are sensitive to the scale of the data and perform better with standardized data.

By using `StandardScaler`, you help ensure that your machine learning model works more effectively and consistently.

# Training the Model

Figure 3-6  illustrates the process of using the X_train and y_train datasets to train the machine learning model. The execution of the training process indicates that the model was successfully trained.

![](OEBPS/image_rsrc54P.jpg)

Figure 3-6.

# Code Explanation

Looking at the code snippet in Figure 3-6  cs = LogisticRegression(random_state=0); cs.fit(X_train, y_train) is used to create and train a logistic regression model using the scikit-learn library in Python.

cs = LogisticRegression(random_state=0) :

LogisticRegression is the class for creating logistic regression models.

cs is the variable that will store the instance of the logistic regression model.

random_state=0 is a parameter that ensures the results are reproducible by setting a seed for the random number generator. This way, you get the same results every time you run the code. If random_state is set to None, the seed is randomly selected, which can lead to different results each time you run the model.

cs.fit(X_train, y_train) :

fit is a method used to train the model.

X_train is the training data containing the features (input variables) that the model will learn from.

y_train is the training data containing the target labels (output variables) that correspond to the features in X_train.

# Predicting with the test data

Figure 3-7  below illustrates how we made predictions using the trained model (cs) and the test data (X_test).

![](OEBPS/image_rsrc54R.jpg)

Figure 3-7.

# Code Explanation

The line y_pred = cs.predict(X_test) is specifically using a logistic regression model (cs) to make predictions on a test dataset (X_test). Here's a detailed explanation tailored to logistic regression:
