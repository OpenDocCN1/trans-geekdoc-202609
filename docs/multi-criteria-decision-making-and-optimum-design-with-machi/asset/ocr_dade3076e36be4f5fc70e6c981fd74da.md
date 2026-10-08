# Appendix B: Combining SVR-NSGA II

```
import numpy as np
from sklearn.svm import SVR
import matplotlib.pyplot as plt
import pandas
from pymoo.model.problem import Problem
from pymoo.algorithms.nsga2 import NSGA2
from pymoo.optimize import minimize
from pymoo.visualization.scatter import Scatter
from platypus NSGAII, Problem
# step 1: Load data from a csv file
df = pandas.read_csv('C:/research/data.csv')
# step 2: Separate input features and variables
ra = np.array(['Ra'])
f = np.array(df['F'])
x = df.drop('Ra', axis=1)
x = x.drop('F', axis=1)
X1 = np.array(x)
# step 3: Create and train the SVR model
svr1 = SVR(kernel='rbf', C=1e3, gamma=0.1,
epsilon=.01)
svr2 = SVR(kernel='rbf', C=1e1, gamma=0.1,
epsilon=.01)
svr1.fit(X1)
svr2.fit(X1)
# step 4: Test the trained model
rap = svr1.predict(X1)
fp = svr2.predict(X1)
class MyProblem(Problem):
    def __init__(self):
        super().__init__(n_var=5,
        n_obj=2,
        n_const=0,
        xl=np.array([1.0, 50.0, 0.1, 60.0, 0.02]),
xu=np.array([6.0, 150.0, 0.9, 240.0, 0.1]),
        elementwise_evaluation=True)
```