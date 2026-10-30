data and transform the **add_features** function, and then we will predict.

```
t=pd.read_csv("house_test_final.csv")
t=add_features(t)
t.shape
arr_test = t[t.columns[1:]].values
```

For a large number of predictions, we can split the input data and query the prediction service. **array_split** is convenient to specify how many splits are needed.

```
predictions = []
for arr in np.array_split(arr_test,50):
result = predictor.predict(arr)
result = result.decode("utf-8")
result = result.split(',')
print (arr.shape)
predictions += [float(r) for r in result]
```

Now, we will reverse and transform our log values. We can evaluate our validation dataset as well.

```
pred=np.expm1(predictions)
sub=pd.DataFrame()
sub['id']=df_test_id.values
sub['SalePrice']=pred
sub.head()
```