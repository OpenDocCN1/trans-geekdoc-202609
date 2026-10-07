# 10.5 PCA in Python: part 2 – Pre-processing

We'll copy all code from **logistic.py** file (classification-template for logistic regression) and **paste** it into new .py file called `logistic_rgsn.py`.

+   - By applying PCA inside this logistic model we end up with two independent variables that explain the **most variance** in data, therefore we will be able to **visualize the results**.

+   - Now will change a few and then we will implement PCA.

+   - **Change dataset**: We first change our *csv* dataset. Now we use a **multidimensional**(more than 3 independent variables) **dataset**. We will use the wine.csv file as our dataset.

```
dataset = pd.read_csv("Wine.csv")
```

+   - **Fixing the Index**: We will change the indexes in the **feature-matrix** and also fix the index of the **dependent variable**.

```
# Extract
dataset = pd.read_csv("Wine.csv"
X = dataset.iloc[:, :13].values
y = dataset.iloc[:, 13:].values
```

![](bbox=[0.095, 0.358, 0.705, 0.358])

![](bbox=[0.725, 0.358, 0.904, 0.358])

+   - **Split the data**: We use 20% of observations for the **test_set** and **80%** for **training_set**.

```
# Split Data
from sklearn.model_selection import train_test_split
# X_test, test_size means "1/5" of the total observation
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=0)
```

+   - **Feature-Scaling**: Features scaling must be applied when we apply dimensionality reduction techniques like **PCA** or **LDA**.

```
# Feature-Scaling
from sklearn.preprocessing import StandardScaler
# y not need to be scaled.
st = StandardScaler()
X_train = st.fit_transform(X_train)
X_test = st.transform(X_test)
```

+   - **Fit dataset to Logistic Regression**: It will be used after after applying **PCA**.

**When we apply PCA to a model**: Remember, we apply any **Dimensional Reduction Technique** (like PCA, LDA, Kernel-PCA), right **after the Data Processing** phase (after the feature is scaled) and just **before fitting the logistic regression** model or any other **Classification Model**.