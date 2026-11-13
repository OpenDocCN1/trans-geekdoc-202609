```
1260 rows x 6 columns

#checking how python reads the dataset
#(float64 = numerical numbers)
CFST.dtypes

D     float64
t     float64
L     float64
fy    float64
fc    float64
N     float64
dtype: object
```

```
Statistical_insights=CFST.agg(
{
"D": ["min", "max", "median", "skew", "std", "mean"],
"t": ["min", "max", "median", "skew", "std", "mean"],
"L": ["min", "max", "median", "skew", "std", "mean"],
"fy": ["min", "max", "median", "skew", "std", "mean"],
"fc": ["min", "max", "median", "skew", "std", "mean"]
}
)
```

```
#Agg is a function that is used for aggregating the data using #one or more operations
#The output of this function will demonstrate a summary
#of statistical insights for the parameters of the dataset

print(Statistical_insights)
#This dataset is used for regression model
#which means you are trying to train the model
#to predict a numerical value (compressive strength in this exam#ple)
```

| | D | t | L | fy | fc |
|---|---|---|---|---|---|
| min | 44.500000 | 0.500000 | 152.300000 | 178.300000 | 7.600000 |
| max | 1020.000000 | 16.500000 | 5560.000000 | 853.000000 | 185.900000 |
| median | 129.000000 | 4.000000 | 662.000000 | 324.700000 | 37.400000 |
| skew | 3.720751 | 1.584916 | 2.004010 | 2.167371 | 2.150750 |
| std | 104.833942 | 2.455295 | 1000.293248 | 90.955122 | 30.665316 |
| mean | 158.835238 | 4.276746 | 1055.142222 | 335.676508 | 47.503492 |

```
#Assigning the 'X' variable to use the features
#as a data frame for X
#Dropping the target label
#(it will be reassigned for y variable as a target)

x=CFST.drop(['N'], axis=1)
y=CFST['N']

#Assigning the target label

x_train,x_test,y_train,y_test=train_test_split(x,y
, test_size=0.2
, random_state=200
)

#Splitting the dataset into 80% training set and 20% as a
#testing set
RF=RandomForestRegressor(max_depth = 20,
```