```
In [13]: iris_df.head()
Out[13]:
     sepal length (cm)  sepal width (cm)  petal length (cm)  \
0              5.1              3.5              1.4
1              4.9              3.0              1.4
2              4.7              3.2              1.3
3              4.6              3.1              1.5
4              5.0              3.6              1.4

     petal width (cm) species  
0             0.2  setosa  
1             0.2  setosa  
2             0.2  setosa  
3             0.2  setosa  
4             0.2  setosa 
```

# Let's calculate some descriptive statistics for the numerical columns:

lick here to view code image

```
In [14]: pd.set_option('precision', 2)

In [15]: iris_df.describe()
Out[15]:
     sepal length (cm)  sepal width (cm)  petal length  (cm)  \
count           150.00          150.00          150.00
mean              5.84            3.06            3.76
std               0.83            0.44            1.77
min               4.30            2.00            1.00
25%               5.10            2.80            1.60
50%               5.80            3.00            4.35
75%               6.40            3.30            5.10
max               7.90            4.40            6.90

     petal width (cm)
count          150.00
mean             1.20
std              0.76
min              0.10
25%              0.30
50%              1.30
75%              1.80
max              2.50
```

Calling the describe method on the 'species' column confirms that it contains three unique values. Here, we know in advance of working with this data that there are three classes to which the samples belong, though this is not always the case in unsupervised machine learning.