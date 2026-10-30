```
data['TotalSF'] = data['TotalBsmtSF'] + data['1stFlrSF'] +
 data['2ndFlrSF'] + data['GrLivArea'] + data['GarageArea']
# Combine the bathrooms
data['Bathrooms'] = data['FullBath'] + data['HalfBath']* 0.5
# Combine Year built, Garage Year Built and Year Remod
# (with a coeff 0.5 since it's less correlated to Year Built than the
Garage year built).
```

```
data['YearMean'] = data['YearBuilt'] + data['YearRemodAdd'] * 0.5 +
data['GarageYrBlt']
return data
```

Now, we have loaded the test dataset without the target columns and here we have pre-processed together with the train data.

```
# We don't need the Id column so we save it
df_train_id = raw_data['Id']
df_test_id = test_data['Id']
raw_data.drop("Id", axis=1, inplace=True)
test_data.drop("Id", axis=1, inplace=True)
```

```
# same transformation to the train / test datasets to avoid irregularities
size_train = len(raw_data.index)
size_test = len(test_data.index)
print((size_train),(size_test))
```

(1453, 81) (1459, 80)

Figure 7.35: Raw Data /Test Data shape