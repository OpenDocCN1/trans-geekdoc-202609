

如果我们考虑 CEO 的价值，给出的薪资约为 600,000，这与真实价值相差甚。因此，我们需要一个比直线更好的模型来拟合数据。

```python
# Polynomial
# y_poly_pred = lin_regressor_2.predict(X) does not work
# (because the linear regressor is not linear)
y_poly_pred = lin_regressor_2.predict(X)
plt.scatter(X, y, color = "red")
plt.title('Truth or bluff Linear Regression')
plt.xlabel('Position Level')
plt.ylabel('Salary')
plt.plot(X, y_poly_pred, color = "green")
```

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_53_0.png)

**注意：** X_poly 配合 lin_regressor_2 使用，不能直接使用 X。原因是 lin_regressor_1 是基于单个特征 X 构建的模型，而 lin_regressor_2 是基于特征 X2 的多项式项构建的模型。

```python
y_poly_pred = lin_regressor_2.predict(X_poly)
```

## 通过增加次数来拟合模型。

**对于 degree=3：** 如果我们将次数改为 3，我们将得到一个更准确的图表，如下所示。**Degree 4：** 因此，我们可以通过增加多项式的次数来获得更准确的结果。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_53_1.png)

### V. 步骤 5：使用线性回归模型预测最终结果：
现在，我们将使用线性回归模型预测最终输出，以判断员工是在说实话还是撒谎。因此，我们将使用 predict() 方法并传递值 6.5。以下是相应的代码：

```python
# Prediction
lin_pred = lin_regressor_1.predict([[6.5]]) # Simple Linear Regression
print(lin_pred)
poly_pred = lin_regressor_2.predict(poly_regressor.fit_transform([[6.5]])) # Poly Linear Regression
print(poly_pred)
```

我们可以看到，多项式回归的预测输出为 [158862.45265153]，这更接近真实值，因此可以说这位员工在说实话。

```python
# --- Import Libraries ---
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
```

```python
# --- Data Preprocessing ---
dataset = pd.read_csv("Position_Salaries.csv")
X = dataset.iloc[:, 1:2].values
# X = dataset.iloc[:, [1]].values is same as above
y = dataset.iloc[:, 2].values
```

```python
# --- Simple Linear model for Reference ---
from sklearn.linear_model import LinearRegression
lin_regressor_1 = LinearRegression() # object for Simple Linear Regression
lin_regressor_1.fit(X, y)
```

```python
# --- Polynomial regressor ---
from sklearn.preprocessing import PolynomialFeatures
# Set the polynomial degree
poly_regressor = PolynomialFeatures(degree=4)
poly_X = poly_regressor.fit_transform(X) # Generates Polynomial Feature-Matrix
lin_regressor_2 = LinearRegression() # object for Polynomial Regression
lin_regressor_2.fit(poly_X, y)
```

```python
# --- Visualize the result ---
# ======= Simple Linear ========
y_pred = lin_regressor_1.predict(X)
plt.scatter(X, y, color = "red")
plt.scatter(X, y_pred, color = "blue")
plt.title("Truth or bluff | Linear Regression")
plt.xlabel("Position level")
plt.ylabel("Salary")
plt.show()
```

```python
# ======= Polynomial ========
# y_poly_pred = lin_regressor_2.predict(X) does not work - Have to use Polynomial Feature-Matrix
y_poly_pred = lin_regressor_2.predict(poly_X)
plt.scatter(X, y, color = "red")
plt.title("Truth or bluff | Linear Regression")
plt.xlabel("Position level")
plt.ylabel("Salary")
plt.plot(X, y_poly_pred, color = "green")
plt.show()
```

```python
# --- Prediction ---
lin_pred = lin_regressor_1.predict([[6.5]]) # Simple Linear Regression
print(lin_pred)
poly_pred = lin_regressor_2.predict(poly_regressor.fit_transform([[6.5]])) # Poly Linear Regression
print(poly_pred)
```

```python
# python prctc_polnm_rgsn.py


## 教师版本

## 多项式回归

# Importing the Libraries
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd

# Importing the dataset
dataset = pd.read_csv('Position_Salaries.csv')
X = dataset.iloc[:, 1].values
y = dataset.iloc[:, -1].values

# Training the Linear Regression model on the whole dataset
from sklearn.linear_model import LinearRegression
lin_reg = LinearRegression()
lin_reg.fit(X, y)

# Training the Polynomial Regression on the whole dataset
from sklearn.preprocessing import PolynomialFeatures
poly_reg = PolynomialFeatures(degree=4)
X_poly = poly_reg.fit_transform(X)
lin_reg_2 = LinearRegression()
lin_reg_2.fit(X_poly, y)

# Visualising the Linear Regression results
plt.scatter(X, y, color='red')
plt.plot(X, lin_reg.predict(X), color='blue')
plt.title('Truth or bluff (Linear Regression)')
plt.xlabel('Position level')
plt.ylabel('Salary')
plt.show()

# Visualising the Polynomial Regression results
plt.scatter(X, y, color='red')
plt.plot(X, lin_reg_2.predict(X_poly), color='blue')
plt.title('Truth or bluff (Polynomial Regression)')
plt.xlabel('Position level')
plt.ylabel('Salary')
plt.show()

# Visualising the Polynomial Regression results (for higher resolution and smoother curve)
X_grid = np.arange(X.min(), X.max(), 0.1)
X_grid = X_grid.reshape((len(X_grid), 1)
plt.scatter(X, y, color='red')
plt.plot(X_grid, lin_reg_2.predict(poly_reg.fit_transform(X_grid)), color='blue')
plt.title('Truth or bluff (Polynomial Regression)')
plt.xlabel('Position level')
plt.ylabel('Salary')
plt.show()

# Predicting a new result with Linear Regression
lin_reg.predict([[6.5]])

# Predicting a new result with Polynomial Regression
lin_reg_2.predict(poly_reg.fit_transform([[6.5]]))

## New Template for Non-Linear Regression
Follow the Instructor version

```python
# Regression Template
# Importing the Libraries
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd

# Importing the dataset
dataset = pd.read_csv('Position_Salaries.csv')
X = dataset.iloc[:, 1:2].values
y = dataset.iloc[:, 2].values

# Splitting the dataset into Training and Test set
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=0)

# Feature Scaling
from sklearn.preprocessing import StandardScaler
sc_X = StandardScaler()
X_train = sc_X.transform(X_train)
X_test = sc_X.transform(X_test)
sc_y = StandardScaler()
y_train = sc_y.transform(y_train.reshape(-1,1))

# Fitting the Regression Model to the dataset
from sklearn.svm import SVR
regressor = SVR(kernel="rbf")
regressor.fit(X_train, y_train)

# Predicting a new result
y_pred = regressor.predict(6.5)

# Visualising the Regression results
plt.scatter(X, y, color='red')
plt.scatter(X, regressor.predict(sc_X.transform(X)), color='blue')
plt.title('Truth or bluff (Regression Model)')
plt.xlabel('Position level')
plt.ylabel('Salary')
plt.show()

# Visualising the Regression results (for higher resolution and smoother curve)
X_grid = np.arange(X.min(), X.max(), 0.1)
X_grid = X_grid.reshape(len(X_grid), 1)
plt.plot(X_grid, regressor.predict(sc_X.transform(X_grid)), color='red')
plt.title('Truth or bluff (Regression Model)')
plt.xlabel('Position level')
plt.ylabel('Salary')
plt.show()
```

## Chapter 2 : Section 4
## Support Vector Regression (SVR)

### 2.4.1 Implementation of SVR in Python

- Data Preparation: We continue with our previous problem of "Bluff Detection"

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# data preprocessing
# Importing the dataset. previous problem of "Bluff Detection"
dataSet = pd.read_csv("Position_Salaries.csv")
X = dataSet.iloc[:, 1].values
y = dataSet.iloc[:, 2].values
```

- Fitting SVR to the dataset: We'll implement SVR from the sklearn library because SVR is actually a vector machine SVM for regression.

```python
# Fitting SVR to the dataset
from sklearn.svm import SVR
regressor = SVR(kernel="rbf")
regressor.fit(X, y)
```

- Choosing kernel: We have many parameters for many ML models. The most important parameter that we need to focus on is the kernel. The kernel is whether you use a linear SVR or a polynomial SVR or Gaussian SVR. 'linear', 'poly', 'rbf', 'sigmoid', 'precomputed' as the most common kernel.

- The one we want to use is the 'rbf' kernel. Why not that? Because our problem is non-linear. The linear kernel would make a linear machine model that would not be appropriate for a nonlinear problem.

- And then we have the choice 'poly' and 'rbf', both these kernels could work for our problem. We're going to choose the most common which is the Gaussian kernel and therefore 'rbf' here.

- Prediction without scaling: In y_pred, we use [[6.5]]. Since Parameter must be 2-D array

```python
y_pred = regressor.predict([[6.5]]) # [[6.5]], since Parameter must be 2-D array
print(y_pred)
```

# Before scaling is applied

