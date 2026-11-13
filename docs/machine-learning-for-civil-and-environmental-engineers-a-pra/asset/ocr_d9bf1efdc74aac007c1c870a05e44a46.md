#We can use shap.approximate_interactions to guess which features
#May interact with maximum exposure temperature

```
inds = shap.approximate_interactions("PP fiber quantity (kg/m3)", shap_values, x_test)
```

#Make plots colored by each of the top three possible interacting features

#Explainer = shap.Explainer(xgbc)

```
xgb_binary_shap_values = explainer(x_test)
expected_value = explainer.expected_value
print("The expected value is ", expected_value)
shap_values_p = explainer.shap_values(x_test) [1]
shap.decision_plot(expected_value, shap_values_p, x_test)
```

The expected value is  -1.0156575

![](bbox=[0.09, 0.38, 0.76, 0.76])

```
test_objects = [x_test.iloc[0:17], x_test.iloc[191:192]]
for float in test_objects:
print ('Probability of class 1 = {:.4f}'.format(xgbc.predict_proba(float)[0][1]))
print ('Formula raw prediction = {:.4f}'.format(xgbc.predict(float)[0]))
print ('\n')
```