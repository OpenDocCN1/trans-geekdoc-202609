```
3. # Encode categorical features
4. for col in cat_col:
5.     le = preprocessing.LabelEncoder()
6.     data[col] = le.fit_transform(data[col])
7.
8. data['Loan_Status'] = le.fit_transform(data['Loan_Status'])
```

Now, you will build an ML model using a random forest classifier and will store the trained models in a pickle object. Here, you can use other ML algorithms and different ML techniques, like GridSearchCV, to improve accuracy. Here, you will build a baseline ML model.

```
1. # Model building
2. X = data[['Gender', 'Married', 'TotalIncome', 'LoanAmount','Credit_History']]
3. y = data['Loan_Status']
4. features = X.columns.tolist()
5.
6. model = RandomForestClassifier(max_depth=4, random_state = 10)
7.
8. model.fit(X, y)
9.
10. # save the model
11. pickle_model = open("trained_model/model_rf.pkl", mode = "wb")
12. pickle.dump(model, pickle_model)
13. pickle_model.close()
14.
15. # Load the trained model
16. pickle_model = open('trained_model/model_rf.pkl', 'rb')
17. model_rf = pickle.load(pickle_model)
18.
19. prediction = model_rf.predict([[1, 1, 6000, 150, 0]])
20. print(prediction)
```