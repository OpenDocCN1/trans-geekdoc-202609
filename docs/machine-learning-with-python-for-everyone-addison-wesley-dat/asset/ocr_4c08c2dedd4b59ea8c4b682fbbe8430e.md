Out[10]:

-0.014016723490578809

Shazam. Did you miss it? I'll do it one more time.

```
In [11]:

print(base_r2_sklearn)
print(1 - (sse_base_preds / sse_mean_test))
```

-0.014016723490579253
-0.014016723490578809

sklearn's R² is specifically calculating its base model—the mean model—from the true values we are testing against. We are not comparing the performance of my_model.fit(train) and mean_model.fit(train). With sklearn's R², we are comparing my_model.fit(train) with mean_model.fit(test) and evaluating them against test. Since that's counterintuitive, let's draw it out the long way:

```
In [12]:

#
# WARNING! Don't try this at home, boys and girls!
# We are fitting on the *test* set... to mimic the behavior
# of sklearn R^2.
#
testbase = dummy.DummyRegressor(strategy='mean')
testbase.fit(diabetes_test_ftrs, diabetes_test_tgt)
testbase_preds = testbase.predict(diabetes_test_ftrs)
testbase_mse = metrics.mean_squared_error(testbase_preds, diabetes_test_tgt)

models = [neighbors.KNeighborsRegressor(n_neighbors=3), linear_model.LinearRegression()]
results = co.defaultdict(dict)
for m in models:
    preds = (m.fit(diabetes_train_ftrs, diabetes_train_tgt)
             .predict(diabetes_test_ftrs))
    mse = metrics.mean_squared_error(preds, diabetes_test_tgt)
    r2 = metrics.r2_score(diabetes_test_tgt, preds)
    results[get_model_name(m)]['R^2'] = r2
    results[get_model_name(m)]['MSE'] = mse

print(testbase_mse)
```