
# Equation of the Polynomial Regression Model:

- Simple Linear Regression equation:
  y = $b_0 + b_1x$

- Multiple Linear Regression equation:
  y = $b_0 + b_1x_1 + b_2x_2 + b_3x_3 + ... + b_nx$

- Polynomial Regression equation:
  y = $b_0 + b_1x + b_2x^2 + ... + b_nx^n$

> ※ We can clearly say that all equations are Polynomial equations but they differ by the degree of variables. The Simple and Multiple Linear equations are also Polynomial equations with a single degree, and the Polynomial regression equation is Linear with the nth degree. (In mathematics Polynomial equations are nonlinear equations. Here in Regression it does not depend on the variables. If we add a degree to our linear equations, it will be converted into Polynomial Linear equations.)

## 2.3 Implementation of Polynomial Regression using Python

Here we implement the Polynomial Regression using Python. We will understand it by comparing Polynomial Regression model with the Simple Linear Regression model. So first let's understand the problem for we are going to build the model.

### Problem Description: There is a Human Resource company, which is going to hire a new candidate. The candidate has his previous salary 60K per annum, and the HR have to check whether he is telling the truth or bluff. To identify this, we only have a dataset of his previous company in which the salaries of the TOP positions are mentioned with their levels. By checking the dataset, we have found that there is a non-linear relationship between Position levels and the salaries. Our goal is to build a fitting regression model, so HR can hire an honest candidate. Here are the steps to build a model.

| Position | Level(X-variable) | Salary(Y-Variable) |
|---|---|---|
| Business Analyst | 1 | 45000 |
| Junior Consultant | 2 | 50000 |
| Senior Consultant | 3 | 60000 |
| Manager | 4 | 80000 |
| Country Manager | 5 | 110000 |
| Region Manager | 6 | 150000 |
| Partner | 7 | 200000 |
| Senior Partner | 8 | 300000 |
| C-level | 9 | 50000 |
| CEO | 10 | 1000000 |

### Steps for Polynomial Regression: The main steps involved in Polynomial Regression are given below:

- i. Data Pre-processing
ii. Build Linear Regression model and fit it to the dataset
iii. Build Polynomial Regression model and fit it to the dataset
iv. Visualize the result for Linear and Polynomial Regression model.
v. Predicting the output

### Why Linear & Polynomial best? Here, we will build the Linear regression as well as Polynomial Regression to see the results between the predictions. And Polynomial regression model is for reference.

### Step - Data Pre-processing: The data pre-processing step will remain the same as in previous regression models, except for some changes. In the Polynomial Regression model, we will not use feature scaling, and we also will not split our dataset into training and test. It has two reasons:

- ✓ The dataset contains very less information which is not suitable to divide into a test and testing, else our model will not be able to find the correlations between the salaries and levels.
- ✓ In this, we will get accurate predictions for salary, so the model should have enough information.

## Pre-processing step

```python
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

dataset = pd.read_csv("Position_Salaries.csv")
X = dataset.iloc[:,[1]].values # same as above
y = dataset.iloc[:,[2]].values # same as above
```

We will consider only two columns (Salary and Levels). Because "Levels" indicate "Positions".
**Trick to make feature-**: for x-variable, we use parameters as [:,1], because we want 1 index(levels), and include -2 to make it a matrix (we could also use dataset.iloc[:, -1]).

| Index | Position | Level | Salary |
|---|---|---|---|
| 0 | Business Analyst | 1 | 45000 |
| 1 | Junior Consultant | 2 | 50000 |
| 2 | Senior Consultant | 3 | 60000 |
| 3 | Manager | 4 | 80000 |
| 4 | Country Manager | 5 | 110000 |
| 5 | Region Manager | 6 | 150000 |
| 6 | Partner | 7 | 200000 |
| 7 | Senior Partner | 8 | 300000 |
| 8 | C-level | 9 | 50000 |
| 9 | CEO | 10 | 100000 |

Here we will **predict** the output for **level 6.5** because the candidate has **4+ years'** experience as a **regional manager**

```python
# Simple Linear model for Reference
from sklearn.linear_model import LinearRegression
lin_regressor_1 = LinearRegression() # 
```
