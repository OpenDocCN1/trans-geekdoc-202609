one or more independent variables that can be continuous as well as categorical. Like the way, we implemented Linear Regression with the help of sklearn, Now, we shall implement Logistic Regression

# Step 1

```
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.linear_model import LogisticRegression as SKLR
```

# Step 2

+   1. Creating dataset with 1000 rows and 2 columns
+   2. Plotting the dataset with the help of the matplotlib library.

```
mean_01 = [0,0]
cov_01 = [[2,0.2], [0.2,1]]
mean_02 = [3,1]
cov_02 = [[1.5,-0.2], [-0.2,2]]
dist_01 = np.random.multivariate_normal(mean_01, cov_01, 500)
dist_02 = np.random.multivariate_normal(mean_02, cov_02, 500)
print(dist_01.shape, dist_02.shape)
(500, 2) (500, 2)
plt.figure()
plt.scatter(dist_01[:,0], dist_01[:,1], color='red')
plt.scatter(dist_02[:,0], dist_02[:,1], color='green')
plt.show()
```

![](bbox=[0.26, 0.71, 0.77, 0.92])