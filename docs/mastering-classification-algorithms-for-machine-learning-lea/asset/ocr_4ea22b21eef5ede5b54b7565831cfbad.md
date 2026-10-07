The package imblearn (or imbalanced learn). Usually, you would need to install thenpackage in your environment:

```
!pip install imblearn
```

Once the imblearn package is successfully installed, we can useRandomOverSampler.

We need to pass all the values of the independent variable(s) (available in X-
train in our case) and the dependent variable (available in y_train in our case).
RandomOverSampler has the method fit() to fit the data, and the method resample()
to create random samples for the data, and the method fit_resample() to fit the
data and create the samples. The method fit_resample() is used here. The resultant
dataset after over-sampling is stored in the variables XO and yO:

```
from imblearn.over_sampling import RandomOverSampler
```

```
oversample = RandomOverSampler(random_state = 42)
X0, y0 = oversample.fit_resample(X_train, y_train)
print("Number of samples for each label after oversampling\n", y0.value_
counts())
print("nShape of X after oversampling = ", XO.shape)
```

Number of samples for each label after oversampling

+   * 7 1358
* 0 1358
* 1 1358
* 10 1358
* 5 1358
* 9 1358
* 8 1358
* 6 1358
* 2 1358
* 3 1358
* 4 1358
* 13 1358

```
Name: Segment, dtype: int64
```

```
Shape of X after oversampling = (16296, 3)
```