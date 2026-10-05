distribution. Additionally, each column will have a mean of zero and standard
deviation of one. We can compute the means and standard deviations of each
column to check one of the z-scores by "hand.".

```
data.mean(axis=0)
OUT: [2.75 1.75]
```

```
data.std(axis=0)
OUT: [2.384848 1.47901995]
```

The Axis=0 parameter allows for selecting across rows when computing the
statistic. For the parameter of 4, its z-score is then (4-2.75)/2.384848=0.52414242
which matches the scaled data entry.

# 10.2.3 Normalization

Another approach to scaling data is normalization. This approach
squeezes the data into a range which is commonly selected to be [0, 1] or
[-1, U]. Unlike what the name may suggest, this transform has nothing to do
with the normal distribution, and the data does not need to follow a normal
distribution. Outliers are filtered to the lower bound and capped at the upper
bound. This transformation is effective in scaling data, but when the data
is approximately normally distributed, standardization is recommended for
retaining symmetry about the origin and for retaining outliers. The formula
for normalizing data is the following:

$x_{norm} = \frac{x - x_{min}}{x_{max} - x_{min}}$

Here is a code snippet for normalizing the dataset from the previous example.
By default, MinMaxScaler() uses a lower bound of 0 and an upper bound of
1.

```
from sklearn.preprocessing import MinMaxScaler
import numpy as np

# set up the scaler
scaler = MinMaxScaler()

# normalize the data
norm_data = scaler.fit_transform(data)

print(norm_data)
```

OUT: