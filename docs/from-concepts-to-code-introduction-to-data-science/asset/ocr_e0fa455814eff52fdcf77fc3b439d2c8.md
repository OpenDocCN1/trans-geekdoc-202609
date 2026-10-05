# Which student did better?

The student in class 1 scored at the mean, while the student in class 2 performed remarkably better. To make a fair comparison, we standardize the scores by computing z-scores using $z = (x - \mu)/\sigma$. A grade of 90 in class 1 equates to a z-score of $(90 - 90)/2 = 0$, while the grade in class 2 is equivalent to a z-score of $(90 - 75)/2 = 7.5$. Note that a z-score of 7.5 is extremely high, recalling 99.7% of the time, a standard normally distributed random variable will have a z-score between -3 and 3.

In this example, we have one value from each class. In data science, we often standardize one or more columns of data, where each column is a variable. This places each value on a similar scale and retains outliers. The function StandardScaler() can be used to standardize one or more columns. Here is a code example for illustration:

```
from sklearn.preprocessing import StandardScaler
import numpy as np

# create an array with four rows and two columns (variables)
data = np.array([[4, 4], [6, 0], [0, 2], [1, 1]])

# set up the scaler
scaler = StandardScaler()

# compute the z-scores
scaled_data = scaler.fit_transform(data)

print(data)
print(scaled_data)
```

OUT:
[[4 4]
[6 0]
[0 2]
[1 1]]

[[0.52414242 1.52127766]
 [1.36277029 -1.18321596]
 [-1.53111332 0.16903085]
 [-0.73379939 -0.50709255]]

By default, the scaler computes the mean and standard deviation of each column and produces the z-scores. For this data, each column has values in a range of [-3, 3], which is common for a variable with a standard normal