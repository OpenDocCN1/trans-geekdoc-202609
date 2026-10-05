# CHAPTER 1 INTRODUCTION

An **Instance** is a row in the dataset. Other names for 'instance' are: (data) point, example, observation. An instance consists of the feature values $x^{(i)}$ and, if known, the target outcome $y_i$.

The **Features** are the inputs for prediction or classification. A feature is a column in the dataset. Throughout the book, features are assumed to be interpretable, meaning it is easy to understand what they mean, like the temperature on a given day or the height of a person. The interpretability of the features is a big assumption. But if it is hard to understand the input features, it is even harder to understand what the model does. The matrix with all features is called X and $x^{(i)}$ for a single instance. The vector of a single feature for all instances is $x_j$ and the value for the feature $j$ and instance $i$ is $x_j^{(i)}.$

The **Target** is the information the machine learns to predict. In mathematical formulas, the target is usually called $y$ or $y_i$ for a single instance.

A **Machine Learning Task** is the combination of a dataset with features and a target. Depending on the type of the target, the task can be for example classification, regression, survival analysis, outlier detection.

The **Prediction** is what the machine learning model “guesses” what the target value should be based on the given features. In this book, the model prediction is denoted by $f(x^{(i)})$ or $y$.