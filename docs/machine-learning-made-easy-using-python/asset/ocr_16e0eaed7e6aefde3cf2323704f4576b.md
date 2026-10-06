# Normalization

Normalization is used to rescale each row of data to have a length of 1. It is mainly useful in Sparse dataset where we have lots of zeros. There are two types of normalization process namely L1 and L2. With the L1 method, all the values in each row will sum upto 1. We can demonstrate the same using the Normalizer class and it’s transform method. To use the L1 method specify ‘l1’ in the norm parameter of the class

```
[3]: import pandas
from sklearn import preprocessing
dt = pandas.read_csv('trees.csv')
ar = dt.values
Mm = preprocessing.Normalizer(norm='l1')
nm_ar = Nm.transform(ar)
print(nm_ar[:5])
# Sum of the rows
for i in [0,1,2,3,4]:
    print(sum(nm_ar[i]))
```

| 0.1116071 0.0926393 0.78125 0.11495536 |
| 0.02328289 0.10116141 0.75669383 0.11990687 |
| 0.03592414 0.10352441 0.74117647 0.12 |
| 0.03887269 0.10204082 0.69970845 0.15937804 |
| 0.04329004 0.09264869 0.7012987 0.16277056 |
| 1.0 |
| 1.0 |
| 1.0 |
| 0.99999999999999 |
| 1.0 |

We created the Nm object of the Normalizer class with the normalizing method as l1 in the norm parameter while inicialization and normalized our ar data values with the transform method of the Normalizer class and stored it in nm_ar variable. Then we printed the 5 rows of the normalized data values

We also created a loop to print the sum of each row of the normalized data i.e. 1(except for the 4th row i.e. 0.99). Note that we didn’t perform any rounding-off