First PC will explain 37% of the variance. 2nd PC will explain 19% of the variance.
So if we take two PCs they will explain 37 + 19 = 56% of the variance.

For 3D visualization, if we take the three PCs that will explain 37 + 19 + 11 = 67%

+   We chose the first two PCs because we get 2D visualization of the result
- Explaining 56% of variance is pretty good to make a classification out of.

Now we edit above PCA code-segmentation and replace n_components with
n_components = 2

```
from sklearn.decomposition import PCA
# dcm_pca = PCA(n_components=None)
dcm_pca = PCA(n_components=2)
X_train = dcm_pca.fit_transform(X_train)
X_test = dcm_pca.transform(X_test)
explind_variance_ = dcm_pca.explained_variance_ratio_
```

Then the pca object dcm_pca will return-2 most independent variables
(represents 2 PCs). And X_train and X_test will be transformed into 2D-matrices
from 3D-matrices.

![](bbox=[0.598, 0.353, 0.804, 0.683])

+   These first two PCs are going to be the two new independent
variables of our dataset (originally) we had 13 independent variables).

+   When we have a look at X_train and X_test right now
contains only two independent variables that are of the top
principal components which explain the most variance.

Since these returned independent variables are already scaled, we're ready
to fit the logistic regression model and visualize its results in 2D.

# 10.7 PCA in Python: part 4 - Logistic & Visualize the result

We are ready to fit a logistic regression model to classify new wines and tell in which segment of customers they belong to. At the
time we will predict the results and evaluate the performance using the confusion matrix.

So basically all things are pre-coded, we just execute the following:

```
# fit sklearn.linear_model import LogisticRegression # Import class
# instead of "regressor" we use "classifier"
classifier = LogisticRegression(random_state=0) # we create object
classifier.fit(X_train, y_train) # fit the dataset

# Predict
y_pred = classifier.predict(X_test)

# Making the confusion matrix use the function "confusion_matrix"
# In class letters, functions are small letters
from sklearn.metrics import confusion_matrix
cm = confusion_matrix(y_true, y_pred) # y_pred= Predicted value
parameters of cm: true *. Real values; y_pred: Predicted value
```