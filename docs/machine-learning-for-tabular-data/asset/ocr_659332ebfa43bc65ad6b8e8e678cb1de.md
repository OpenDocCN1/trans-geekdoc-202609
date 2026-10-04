# Introducing Scikit-learn

```
from sklearn.preprocessing import StandardScaler
processing = StandardScaler().fit(X)
```

In our example, we instantiate the class necessary for standardizing the data (StandardScaler), and we immediately fit the data itself. Since the .fit method returns the instantiated class for the fitting procedure, you can safely get in return the class with all the learned parameters by combining these two steps. Such an approach will be helpful when building pipelines and training models because it helps you separate the activities that learn something from the actions that apply what they learned to data. This way, you won't mistake mixing information from training and validation data.

Depending on the complexity of the underlying operations and the quantity of provided data, fitting a model or a function processing data may take some time. After the fitting has been complete, many more attributes will become available for you to use afterward, depending on the algorithm used.

For a trained model, you will obtain a vector of responses of predictions based on any data by applying the .predict method. This will work for a classification or a regression problem:

```
X_test = [[-1, 1], [2, -1]]
model.predict(X_test)
```

Suppose you are working on a classification; instead, you must get the probability that a certain class is a correct prediction for a new sample. In this case, you need to use the .predict_proba method, which is available only to certain models:

```
model_predict_proba(X_test)
```

Classes that process data, do not have a .predict method. Still, they use the .transform one, which returns data if the class has been previously instantiated and fitted with some training data for learning the key parameters necessary for the transformation:

```
processing.transform(X)
```

Since the transformation is often applied on the very same data that provided the key parameters, the .fit_transform method, which concatenates the two fit and transform forms, will result in a handy shortcut:

```
processing.fit_transform(X)
```

# 4.1.3 Introduction to Scikit-learn pipelines

You can also wrap a sequence of transformations and then predictions, selectively deciding what to transform and joining different sequences of transformations by using utility functions offered by Scikit-learn, such as