```
numeric_features = raw_data.dtypes[raw_data.dtypes != 'object'].index
for feature in numeric_features:
try:
outs = detect_outliers(raw_data[feature], raw_data['SalePrice'],top=5,
plot=False)
except:
continue
all_outliers.extend(outs)
```

```
print(Counter(all_outliers).most_common())
for i in outliers:
if i in all_outliers:
print(i)
```

![](bbox=[0.12, 0.5, 0.92, 0.64])

# *Figure 7.32: Outlier Index Count Dictionary*

```
Outliers_table=raw_data.loc[outliers]
Outliers_table=Outliers_table[cols_out]
Outliers_table
```