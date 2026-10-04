# CHAPTER 5 Decision trees and gradient boosting

```
self.init = self.logit(np.mean(y))
y_pred = self.init * np.ones(X.shape[0])
for k in range(self.n_estimators):
    gradient = self.gradient(self.logit(y), y_pred)
    tree = DecisionRegressor(**self.params)
    tree.fit(X, -gradient)
    self.tree.append(tree)
    y_pred += self.learning_rate * tree.predict(X)
```

Initializes the model with the logit-transformed mean of the target values

```
def predict_proba(self, X):
    y_pred = self.init * np.ones(X.shape[0])
    for tree in self.trees:
        y_pred += self.learning_rate * tree.predict(X)
    return self.sigmoid(y_pred)
```

Fits a decision tree regressor to the negative gradient of the log-odds transformed target

Updates the predicted values using the output of the fitted tree with a learning rate factor

```
def predict(self, X, threshold=0.5):
    proba = self.predict_proba(X)
    return np.where(proba >= threshold, 1, 0)
```

Predicting requires cumulating predictions from all the trees.

As in the gradient descent we have applied to linear models, we are making the process stochastic to avoid being stuck on a suboptimal solution, which is achieved by sampling rows or columns before the training of each decision tree. In addition, we use early stopping to prevent using too many decision sequences and adapting too much to the data. We will develop early stopping in the next chapter.

Now that we have explained the workings of the GradientBoosting class, we can experiment with it. We'll use the Airbnb NYC dataset and begin by dividing it into a training set and a testing set. This will involve creating lists of row indices—one for the training set and one for the testing set—employing the Scikit-learn function train_split (https://mg.bz/pjplz). We instantiate the GradientBoosting class, which requires a learning rate of 0.1 and 300 trees, with a maximum depth of 4 branches and terminal leaves with at least three examples. After transforming the training data, by numeric and categorical features, we fit the model, predict the test set, and evaluate the results.

| Listing 5.7 Testing our gradient boosting class | train_split |

```
from sklearn.model_selection import train_split

train, test = train_split(range(len(data)), test_size=0.2,
random_state=0
```

```
cls = GradientBoosting(n_estimators=300,
                          learning_rate=0.1,
                          max_depth=4,
                          min_samples_leaf=3,
```

Splits the dataset indices into training and testing set using a fixed random seed