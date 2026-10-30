# 7.5.3 Feature Transformation

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