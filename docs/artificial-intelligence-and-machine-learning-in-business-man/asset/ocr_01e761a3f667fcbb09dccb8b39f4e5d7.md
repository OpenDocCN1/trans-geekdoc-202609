# Artificial Intelligence and Machine Learning in Business Management

```
scalar = StandardScaler()
X_scaled = scalar.fit_transform(X)

X_scaled
array([[-0.93649469, -1.08272529, -1.46286291, ..., -0.17418182,
0.39725083,-0.5545458],
 [0.75281433, 0.84780693, 0.97112292, ..., -0.17418182,
0.39725083,1.04300582],
 [-2.82827906, 0.95755433, 2.59736348, ..., -0.17418182,
0.39725083,1.04300582]]
[[-0.97671363, -1.08272529, -1.46286291, ..., -0.17418182,
0.24361512,-0.55454583],
 [-2.02247906, 1.42043936, ..., -0.17418182,
0.24361512,-0.55454583],
 [-0.97671363, -1.46506989, -1.46286291, ..., -0.17418182,
0.24361512,-0.55454583]])
```

**FIGURE 11.9** Scaled input features.

```
# Import LabelEncoder
# from sklearn import preprocessing
# creatingLabelEncoder
le = preprocessing.LabelEncoder()
# Converting string Labels into numbers.
data['salary'] =le.fit_transform(data['salary'])
data['Departments'] =le.fit_transform(data['Departments'])
```

After converting into normal form, salary contains 3 classes based on →1, medium→2, and high→3. Similarly, departments are divided into 7 classes based on the department names. For model building we need to divide the dataset into 2 parts, i.e., features or independent variable and labels the dependent variable or result. Here the column named “Left” is the output or result of the department part and rest of the columns are independent part. We divided the dataset into two parts X and Y, where X contains independent features and Y contains resultant.

If we notice the dataset, we can see that all the features are not in a single scale, which means all column values have different ranges. So, to get a more accurate model, we need to bring down all the values to the same scale. For this purpose, we need to use the “Standard scaler” of sklearn module, which converts all the column values into the same scale. After scaling, values look like below image: Scaled input features is shown below in Figure 11.9.

# 11.3.1 TRAIN TEST SPLIT

To develop the model, we need the data to feed we divide the entire dataset and Y into two parts, train and test datasets. Train dataset or X_train and Y_train is used for model building or learning for the model and the test or X_test is used for testing