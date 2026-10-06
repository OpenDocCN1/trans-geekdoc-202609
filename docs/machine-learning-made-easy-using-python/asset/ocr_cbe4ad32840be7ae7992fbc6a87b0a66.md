Now sort them into ascending order on the basis of distance value calculated above

Finally assign a class or values to the point on the basis of the nearest datapoint

![](bbox=[0.185, 0.335, 0.513, 0.558])

# Regression with KNN

We will perform regression with the KNN algorithm to create a model to predict the weight of a person if the height is provided as input, the same problem solved in the Linear regression model (page no. 130)

We can start-off by importing the necessary modules and the dataset height_and_weight.csv

```
import pandas
from sklearn.neighbors import - KNeighborsRegressor
from sklearn.model_selection import - train_test_split
```