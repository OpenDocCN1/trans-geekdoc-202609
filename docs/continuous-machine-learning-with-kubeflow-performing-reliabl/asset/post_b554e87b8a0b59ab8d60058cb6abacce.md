
The SalePrice skewness is 1.88

![](img/8f8a671916d96b455297952d0f37b96c_447_0.png)

Figure 7.22: Normal Distribution Plot

![](img/8f8a671916d96b455297952d0f37b96c_447_1.png)

Figure 7.23: Probability plot

Therefore, we need to transform it into a more normal distribution, since the linear models will perform better. So, after the Log Transformation, the Normal distribution and P-P plot is as follows:

```
raw_data['SalePrice']=np.log1p(raw_data['SalePrice'])
```

```
skew_distribution(raw_data, 'SalePrice')
```

The SalePrice skewness is 0.12

![](img/8f8a671916d96b455297952d0f37b96c_448_0.png)

Figure 7.24: Normal Distribution Plot

![](img/8f8a671916d96b455297952d0f37b96c_448_1.png)

Figure 7.25: Probability plot

SalePrice is now more Gaussian, and the second plot which represents the probability plot shows that the distribution follows almost a normal distribution.

## 7.5.2.4 Correlation & Scatter Plots

Here, we will plot the correlation to check the relation between the variables and scatter the plots to check the outlier analysis with respect to the dependent feature House price.

```
corr = raw_data.corr()
top_correlation = corr['SalePrice'].sort_values(ascending=False)[:25]
threshold = 0.51
top_corr = corr.index[np.abs(corr["SalePrice"]) > threshold]
```

```
plt.figure(figsize=(10,8))
sns.heatmap(raw_data[top_corr].corr(),annot=True,cmap="RdBu_r")
```

So, the correlation plot will look like the following:

<matplotlib.axes._subplots.AxesSubplot at 0x7f29c57b0c88>

![](img/8f8a671916d96b455297952d0f37b96c_451_0.png)

## Figure 7.26: Top correlation Plot

Now, in the preceding screenshot, we can see that we plotted the top correlated features with the 0.51 threshold value and figured out a few columns which are very important with respect to the dependent columns.

We will find the mean correlation of the top numeric correlated features.

```
for col in top_correlation.index[:15]:
```

```
```python
print('{} - unique values: {} - mean: {:.2f}'.format(col, raw_data[col].unique()[:5], np.mean(raw_data[col])))
```
```

```
```
SalePrice - unique values: [12.24769912 12.10901644 12.31717117 11.84940484 12.4292202 ] - mean: 12.02
OverallQual - unique values: [7 6 8 5 9] - mean: 6.10
GrLivArea - unique values: [1710 1262 1786 1717 2198] - mean: 1515.46
GarageCars - unique values: [2 3 1 0 4] - mean: 1.77
GarageArea - unique values: [548 460 608 642 836] - mean: 472.98
TotalBsmtSF - unique values: [ 856 1262  920  756 1145] - mean: 1057.43
1stFlrSF - unique values: [ 856 1262  920  961 1145] - mean: 1162.63
FullBath - unique values: [2 1 3 0] - mean: 1.57
YearBuilt - unique values: [2003 1976 2001 1915 2000] - mean: 1971.27
YearRemodAdd - unique values: [2003 1976 2002 1970 2000] - mean: 1984.87
GarageYrBlt - unique values: [2003. 1976. 2001. 1998. 2000.] - mean: 1978.51
TotRmsAbvGrd - unique values: [8 6 7 9 5] - mean: 6.52
Fireplaces - unique values: [0 1 2 3] - mean: 0.61
MasVnrArea - unique values: [196. 0. 162. 350. 186.] - mean: 103.69
BsmtFinSF1 - unique values: [706 978 486 216 655] - mean: 443.64
```
```

## Figure 7.27: Correlated Mean wrt. Target feature

So, the following columns are the important columns which we figured out for further analysis through the scatter plot.

```
```python
cols = 'SalePrice GrLivArea GarageArea TotalBsmtSF YearBuilt 1stFlrSF MasVnrArea TotRmsAbvGrd'.split()
with plt.rc_context(rc={'font.size':14}):
fig, ax = plt.subplots(figsize=(16,13), tight_layout=True)
pd.plotting.scatter_matrix(raw_data[cols], ax=ax, diagonal='kde', alpha=0.8)
```
```

![](img/8f8a671916d96b455297952d0f37b96c_453_0.png)

## Figure 7.28: Scatter Plot

These scatter plots will give us some insight into a few outliers, that is, the values which resemble some incoherent/huge values, which will now impact the models. Thus, we will only remove a few of them since these ones are really important. We will remove the principal outliers in the scatter plots of (GrLivArea - GarageArea - TotalBsmtSF - 1stFlrSF - MasVnrArea - TotRmsAbvGrd) vs SalePrice).

## 7.5.2.5 Outlier Detection

Now, we will remove the outliers from our Dataset with Scikit-Learn LocalOutlierFactor Method.

```
def detect_outliers_plots(x, y,name,top=5, plot=True):
lof = LocalOutlierFactor(n_neighbors=40, contamination=0.1)
x_ =np.array(x).reshape(-1,1)
preds = lof.fit_predict(x_)
lof_scr = lof.negative_outlier_factor_
out_idx = pd.Series(lof_scr).sort_values()[:top].index
if plot:
f, ax = plt.subplots(figsize=(9, 6))
plt.scatter(x=x, y=y, c=np.exp(lof_scr), cmap='RdBu')
ax.set(ylabel='SalePrice', xlabel=name)
return out_idx
```

Extract the 8 columns in a separate table and list and drop the null values.

```
outlier_ana_data=raw_data[['SalePrice','GarageArea','TotalBsmtSF',
'YearBuilt','1stFlrSF','MasVnrArea', 'TotRmsAbvGrd', 'GrLivArea']]
outlier_ana_data.dropna(inplace=True)
cols_out = ['GarageArea','TotalBsmtSF',
'YearBuilt','1stFlrSF','MasVnrArea', 'TotRmsAbvGrd', 'GrLivArea']
for i in cols_out:
```

```
outs = detect_outliers_plots(outlier_ana_data[i],
 outlier_ana_data['SalePrice'],i,top=5) #got 1298,523
print(outs)
```

```
Int64Index([540, 515, 1364, 318, 1158], dtype='int64')
Int64Index([1290, 331, 495, 522, 439], dtype='int64')
Int64Index([1429, 802, 800, 282, 762], dtype='int64')
Int64Index([1290, 495, 522, 1018, 1365], dtype='int64')
Int64Index([1017, 1353, 976, 378, 384], dtype='int64')
Int64Index([531, 633, 203, 1094, 612], dtype='int64')
Int64Index([1290, 522, 1176, 688, 531], dtype='int64')
```

## Figure 7.29: Output of Index Outlier

So, it will return the index of all the outliers in those 7 columns.

![](img/8f8a671916d96b455297952d0f37b96c_455_0.png)

## Figure 7.30: Normal Distribution Plot

![](img/8f8a671916d96b455297952d0f37b96c_456_0.png)

## Figure 7.31: Probability plot

We have created a function and called it here to detect the outliers; you can find the code in GitHub, so don’t get confused if you see this method in the following section.

We extracted the most common outliers from the dataset and found out the outliers.

```
outliers = [30, 88, 462, 523, 632, 1298, 1324]
from collections import Counter
all_outliers=[]
```

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

![](img/8f8a671916d96b455297952d0f37b96c_457_0.png)

## *Figure 7.32: Outlier Index Count Dictionary*

```
Outliers_table=raw_data.loc[outliers]
Outliers_table=Outliers_table[cols_out]
Outliers_table
```

|  | GarageArea | TotalBsmtSF | YearBuilt | 1stFlrSF | MasVnrArea | TotRmsAbvGrd | GrLivArea |
|---|---|---|---|---|---|---|---|
| 30 | 250 | 649 | 1920 | 649 | 0.0 | 6 | 1317 |
| 88 | 0 | 1013 | 1915 | 1013 | 0.0 | 6 | 1526 |
| 462 | 360 | 864 | 1965 | 864 | 0.0 | 5 | 864 |
| 523 | 884 | 3138 | 2007 | 3138 | 762.0 | 11 | 4676 |
| 632 | 544 | 1386 | 1977 | 1411 | 209.0 | 6 | 1411 |
| 1298 | 1418 | 6110 | 2008 | 4692 | 796.0 | 12 | 5642 |
| 1324 | 895 | 1795 | 2006 | 1795 | 428.0 | 7 | 1795 |

## Figure 7.33: Outlier Table

Now we will delete the outliers via the index lists.

```
raw_data = raw_data.drop(raw_data.index[outliers])
raw_data.reset_index(drop=True, inplace=True)
raw_data.shape()
```

[23]: (1453, 81)

## Figure 7.34: New Data shape

So, we have removed 7 rows of outliers which were most common.

## 7.5.3 Feature Transformation

Here, group the columns into numerical, categorical, Label Encoder columns, and changing datatype of columns.

```
N= ['GarageYrBlt', 'MasVnrArea','GarageArea',
'GarageCars','BsmtFinSF1', 'BsmtFinSF2', 'BsmtUnfSF','TotalBsmtSF',
'BsmtFullBath', 'BsmtHalfBath','MasVnrArea']
M= ['MSZoning','Electrical','KitchenQual','Exterior1st',
'Exterior2nd','SaleType']
S=['OverallCond','YrSold','MoSold','MSSubClass','GarageCars',
'Fireplaces', 'HalfBath','OverallQual']
L= ['PoolQC','MSSubClass','MasVnrType','Alley','MiscFeature',
'Fence','FireplaceQu','BsmtQual', 'BsmtCond',
'BsmtExposure','BsmtFinType1', 'BsmtFinType2','GarageType',
'GarageFinish', 'GarageQual', 'GarageCond']
cols= ['BsmtExposure', 'BsmtFinType1', 'BsmtFinType2', 'BsmtQual',
'BsmtCond', 'GarageQual', 'GarageCond', 'GarageFinish',
'GarageType',
'FireplaceQu', 'ExterQual', 'ExterCond',
'HeatingQC', 'PoolQC', 'KitchenQual',
'Functional', 'Fence', 'LandSlope',
'LotShape', 'PavedDrive', 'Street', 'Alley', 'CentralAir',
'MSSubClass', 'OverallCond', 'GarageCars', 'YrSold', 'MoSold',
'Fireplaces', 'HalfBath']
```

So, the following **transformation()** function is used for the imputation of the numerical columns:
