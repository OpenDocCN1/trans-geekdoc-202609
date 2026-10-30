will just separate out our train data from the merged data and then add features. The following is the process for the train data:

```
x = df_tot[:size_train]
x=add_features(x)
print (x.shape)
x.head()
```

![](bbox=[0.11, 0.29, 0.88, 0.43])

Figure 7.37: Raw Train Data after transformation then separating from merge data

In the preceding screenshot, you can see the shape of the train data changed to (1453,225) after transformation. After that, we checked the Null values in our data train which is zero for all columns.

```
logSalesPrice=raw_data['SalePrice']
x.reset_index(drop=True, inplace=True
x.insert(loc=0, column='SalePrice', value=logSalesPrice)
x.head()
```